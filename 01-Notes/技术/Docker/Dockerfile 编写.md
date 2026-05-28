---
date: "2026-05-28"
tags: [Docker, Dockerfile, 构建]
---

# Dockerfile 编写

> Dockerfile = 镜像的"配方"文件。告诉 Docker 如何从零构建你的应用镜像

## 最简示例

```dockerfile
# 基于 Python 3.11 官方镜像
FROM python:3.11

# 设置工作目录
WORKDIR /app

# 复制依赖文件并安装
COPY requirements.txt .
RUN pip install -r requirements.txt

# 复制应用代码
COPY . .

# 声明容器运行时端口
EXPOSE 8000

# 启动命令
CMD ["python", "main.py"]
```

## 核心指令

| 指令 | 用途 | 示例 |
|------|------|------|
| `FROM` | 基础镜像 | `FROM python:3.11-slim` |
| `WORKDIR` | 工作目录 | `WORKDIR /app` |
| `COPY` | 复制文件 | `COPY . /app` |
| `RUN` | 构建时执行命令 | `RUN pip install -r requirements.txt` |
| `CMD` | 容器启动时的默认命令 | `CMD ["python", "app.py"]` |
| `ENTRYPOINT` | 容器入口点 | `ENTRYPOINT ["python"]` |
| `ENV` | 环境变量 | `ENV PORT=8000` |
| `EXPOSE` | 声明端口 | `EXPOSE 8000` |

## 实战：为 FastAPI 项目写 Dockerfile

```dockerfile
FROM python:3.11-slim

WORKDIR /app

# 先复制依赖文件（利用 Docker 缓存层）
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 再复制代码
COPY . .

EXPOSE 8000

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

> 为什么 COPY 要分两步？Docker 每层有缓存。先 COPY requirements.txt → 如果依赖没变，pip install 这层直接用缓存；如果一起 COPY . → 代码改一行就要重新 pip install。

## 多阶段构建（减小镜像体积）

```dockerfile
# 阶段 1：构建
FROM python:3.11 AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --user -r requirements.txt

# 阶段 2：运行（更小的最终镜像）
FROM python:3.11-slim
WORKDIR /app
COPY --from=builder /root/.local /root/.local
COPY . .
ENV PATH=/root/.local/bin:$PATH
CMD ["python", "main.py"]
```

多阶段构建可以把最终镜像从 1GB 压缩到 300MB。

## .dockerignore

```
__pycache__
*.pyc
.env
.git
.venv
*.log
```

和 `.gitignore` 作用类似 — 构建时忽略这些文件，不复制进镜像。

## 面试常问

> 问："CMD 和 ENTRYPOINT 的区别？"
> 答："CMD 定义默认命令，可以被 `docker run` 后面的参数覆盖。ENTRYPOINT 定义容器入口，不会被覆盖，只把额外参数追加进去。常用组合：ENTRYPOINT 指定程序，CMD 指定默认参数。"

← [[Docker 常用命令]] | → [[Docker Compose]]
