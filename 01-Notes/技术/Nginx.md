---
date: "2026-05-28"
tags: [Nginx, Web服务器, 运维]
---

# Nginx

> 高性能 Web 服务器 + 反向代理 + 负载均衡，所有请求的"前台接待员"

## 三个核心用途

### 1. Web 服务器
```nginx
server {
    listen 80;
    root /var/www/html;
    index index.html;
}
```
静态文件（HTML、CSS、JS、图片）→ Nginx 直接返回，极快

### 2. 反向代理
```nginx
location /api/ {
    proxy_pass http://localhost:8000;
}
```
用户 → Nginx → 后端服务 → 返回结果。用户不知道后面有几个服务

### 3. 负载均衡
```nginx
upstream backend {
    server 10.0.1.1:8000;
    server 10.0.1.2:8000;
}
location / {
    proxy_pass http://backend;
}
```
流量大时 Nginx 轮流分发到多台服务器

## 常用命令

```bash
nginx -t                  # 测试配置是否正确
nginx -s reload           # 热重载（不中断服务）
systemctl restart nginx   # 重启
```

## 实际架构

```
用户 → Nginx(80/443) → /api/* → FastAPI(8000)
                      → /     → 静态文件
                      → *.jpg  → 直接返回
```

关联：[[Docker 实战案例]] | [[Linux 系统管理]]
