---
date: "2026-05-28"
tags: [MOC, Docker, 容器, 运维]
---

# Docker 学习路线 — MOC

> Docker 是必学的容器技术：打包、分发、运行应用的环境一键搞定

## 核心理念

> 在你的机器上能跑，为什么在服务器上跑不了？→ Docker 把运行环境和应用一起打包，到处都能跑

## 学习路径

### 第一阶段：理解概念
- [[Docker 基础概念]] — 镜像、容器、仓库是什么，和虚拟机的区别

### 第二阶段：动手操作
- [[Docker 常用命令]] — 拉镜像、启容器、看日志、进容器、删资源

### 第三阶段：构建自己的镜像
- [[Dockerfile 编写]] — 把 Python 项目打包成 Docker 镜像

### 第四阶段：多容器编排
- [[Docker Compose]] — 一个 YAML 文件编排多个容器（如 Web + 数据库）

### 第五阶段：实战
- [[Docker 实战案例]] — 用 Docker 部署 FastAPI + MySQL + Nginx

## 和现有知识的关系

- Docker 容器本身就是一个迷你 [[Linux 常用命令|Linux 环境]]
- [[Dockerfile 编写]] 里大量用到 [[Linux 文件操作|Linux 命令]]
- 部署项目时 = Docker 拉镜像 + [[Linux 系统管理|systemd/systemctl]] 管理服务
- 日志查看 = `docker logs` + [[AI 日志解析]] + [[正则表达式实战]]
