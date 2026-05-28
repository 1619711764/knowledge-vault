---
date: "2026-05-28"
tags: [Docker, 实战, 部署]
---

# Docker 实战案例

> 用 Docker + Docker Compose 部署一个真实项目：FastAPI + MySQL + Nginx

## 项目结构

```
my-project/
├── app/
│   └── main.py          # FastAPI 应用
├── nginx/
│   └── default.conf      # Nginx 配置
├── requirements.txt
├── Dockerfile
├── docker-compose.yml
└── .dockerignore
```

## Dockerfile

```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

## docker-compose.yml

```yaml
version: "3.8"

services:
  web:
    build: .
    expose:
      - "8000"
    environment:
      - DATABASE_URL=mysql+pymysql://root:password@db:3306/mydb
    depends_on:
      db:
        condition: service_healthy
    restart: always

  db:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: mydb
    volumes:
      - mysql_data:/var/lib/mysql
    healthcheck:
      test: ["CMD", "mysqladmin", "ping", "-h", "localhost"]
      interval: 10s
      retries: 5

  nginx:
    image: nginx:alpine
    ports:
      - "80:80"
    volumes:
      - ./nginx/default.conf:/etc/nginx/conf.d/default.conf
    depends_on:
      - web

volumes:
  mysql_data:
```

## Nginx 配置

`nginx/default.conf`：

```nginx
server {
    listen 80;
    server_name localhost;

    location / {
        proxy_pass http://web:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

## 常用命令

```bash
docker-compose up -d                     # 启动所有服务
docker-compose ps                        # 查看状态
docker-compose logs -f web               # 跟踪日志
docker-compose up -d --build             # 更新代码后重新构建
docker-compose exec db mysql -uroot -p   # 进入数据库
docker-compose down                      # 停止所有服务
```

## 生产 Checklist

- `.env` 不入镜像
- 数据库密码用变量 `${MYSQL_PASSWORD}`
- 不锁 `latest` 标签，固定版本号如 `mysql:8.0.35`
- 设置 `restart: always`
- 非 root 用户运行容器

← [[Docker Compose]] | ↑ [[Docker 学习路线]]
