---
date: "2026-05-28"
tags: [Docker, 命令, 实操]
---

# Docker 常用命令

> 这些是最常用的 20 条命令，覆盖日常 90% 的操作

## 镜像操作

```bash
docker images                    # 列出本地镜像
docker pull python:3.11          # 拉取镜像
docker pull nginx:latest         # 拉取最新版 nginx
docker rmi python:3.11           # 删除镜像
docker build -t myapp:v1.0 .     # 用 Dockerfile 构建镜像
```

## 容器操作

```bash
# 启动容器
docker run -d --name web -p 8080:80 nginx     # 后台运行，端口映射
docker run -it python:3.11 bash                # 交互式进入容器
docker run -v /host/path:/container/path ...   # 挂载数据卷

# 查看容器
docker ps                       # 运行中的容器
docker ps -a                    # 所有容器（含已停止）

# 停止/启动/重启
docker stop web                 # 停止
docker start web                # 启动已存在的容器
docker restart web              # 重启

# 删除
docker rm web                   # 删除容器
docker rm -f web                # 强制删除（运行中也删）
docker container prune          # 删除所有已停止的容器
```

## 常用参数速查

| 参数 | 含义 | 示例 |
|------|------|------|
| `-d` | 后台运行 | `docker run -d nginx` |
| `-p` | 端口映射 | `-p 8080:80` (主机8080 → 容器80) |
| `-v` | 数据卷挂载 | `-v ./data:/app/data` |
| `-e` | 环境变量 | `-e DATABASE_URL=xxx` |
| `--name` | 给容器命名 | `--name my-web` |
| `-it` | 交互模式 | `docker exec -it web bash` |
| `--rm` | 退出后自动删除 | `docker run --rm python:3.11` |

## 调试命令

```bash
docker logs web                 # 查看容器日志
docker logs -f web              # 实时跟踪日志
docker logs --tail 50 web       # 最后 50 行

docker exec -it web bash        # 进入运行中的容器
docker exec web cat /etc/hosts  # 在容器里执行命令

docker inspect web              # 查看容器详细信息（IP、挂载等）
docker stats                    # 查看所有容器资源使用
```

## 清理命令

```bash
docker system prune -a          # 清理所有不用的镜像、容器、网络（常用）
docker volume prune             # 清理不用的数据卷
docker image prune              # 清理无标签的镜像
```

## 常用组合

```bash
# 启动 MySQL，设置 root 密码
docker run -d --name mysql -p 3306:3306 \
  -e MYSQL_ROOT_PASSWORD=123456 \
  mysql:8.0

# 启动 nginx，挂载本地目录
docker run -d --name web -p 80:80 \
  -v ./html:/usr/share/nginx/html \
  nginx

# 进入容器调试
docker exec -it mysql mysql -uroot -p

# 一键停掉所有容器
docker stop $(docker ps -q)
```

← [[Docker 基础概念]] | → [[Dockerfile 编写]]
