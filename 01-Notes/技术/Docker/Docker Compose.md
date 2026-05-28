---
date: "2026-05-28"
tags: [Docker, Compose, 编排]
---

# Docker Compose

> 一个 YAML 文件编排多个容器。比如：Web 服务 + 数据库 + Redis + Nginx，一条命令全部启动

## 为什么需要 Compose

单容器用 `docker run` 就够了。但真实项目通常是这样的：

```
┌──────────┐     ┌──────────┐     ┌──────────┐
│  Nginx   │────→│  FastAPI │────→│  MySQL   │
│  (入口)   │     │  (后端)   │     │  (数据库) │
└──────────┘     └──────────┘     └──────────┘
                         │
                    ┌────▼─────┐
                    │  Redis   │
                    │  (缓存)   │
                    └──────────┘
```

每次手动 `docker run` 四次 + 管理网络？太累。用 Compose 一个文件搞定。

## docker-compose.yml 示例

```yaml
version: "3.8"

services:
  web:
    build: .
    ports:
      - "8000:8000"
    environment:
      - DATABASE_URL=mysql://root:password@db:3306/mydb
    depends_on:
      - db
    volumes:
      - ./app:/app

  db:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: mydb
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql

volumes:
  mysql_data:
```

## 核心命令

```bash
docker-compose up -d              # 启动所有服务（后台运行）
docker-compose down               # 停止并删除所有服务
docker-compose down -v             # 连数据卷一起删
docker-compose logs -f web         # 跟踪 web 服务的日志
docker-compose ps                  # 查看所有服务状态
docker-compose restart web         # 重启某个服务
docker-compose exec web bash       # 进入 web 服务容器
```

## 网络通信

Compose 自动创建网络。服务之间用**服务名**互访：

```yaml
# web 服务里访问数据库：
# 地址写 "db"（服务名），不写 IP
DATABASE_URL=mysql://root:password@db:3306/mydb
```

## depends_on vs 健康检查

```yaml
services:
  web:
    depends_on:
      db:
        condition: service_healthy  # 等 db 真正就绪再启动

  db:
    image: mysql:8.0
    healthcheck:
      test: ["CMD", "mysqladmin", "ping"]
      interval: 5s
      timeout: 3s
      retries: 5
```

`depends_on` 只控制启动顺序，不检查数据库是否就绪。加 `healthcheck` 才能确保 web 启动时数据库已可用。

← [[Dockerfile 编写]] | → [[Docker 实战案例]]
