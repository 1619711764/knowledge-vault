---
date: "2026-05-28"
tags: [Docker, 容器, 基础]
---

# Docker 基础概念

## 一句话理解

> Docker = 轻量级虚拟机。把你的应用 + 它需要的所有环境（Python 版本、依赖包、系统库）打包成一个标准化的"集装箱"，放到任何装了 Docker 的机器上都能直接跑。

## 三个核心概念

### 1. 镜像（Image）

镜像 = **只读的模板**。可以理解为"安装光盘的 ISO 文件"。

```bash
docker images          # 查看本地有哪些镜像
docker pull python:3.11  # 下载 Python 3.11 镜像
```

镜像分层：每个 `RUN` 指令产生一个新层 → 层可以复用，节省磁盘

### 2. 容器（Container）

容器 = **镜像的运行实例**。可以理解为"用 ISO 装好之后正在运行的系统"。

```bash
docker run python:3.11 python -c "print('hello')"  # 运行容器
docker ps                  # 查看正在运行的容器
docker ps -a               # 查看所有容器（含已停止的）
```

### 3. 仓库（Registry）

仓库 = **存放和管理镜像的地方**。Docker Hub 是最大的公共仓库（类似 GitHub 之于代码）。

```bash
docker pull nginx:latest                    # 从 Docker Hub 拉镜像
docker push 1619711764/myapp:v1.0          # 推送到自己的仓库
```

## Docker vs 虚拟机

```
虚拟机                            Docker 容器
────────────────────────        ───────────────────
┌── App A ──┐ ┌── App B ──┐    ┌─ App A ─┐ ┌─ App B ─┐
│ Bin/Libs  │ │ Bin/Libs  │    │ Bin/Libs│ │ Bin/Libs│
├───────────┤ ├───────────┤    ├─────────┤ ├─────────┤
│  Guest OS │ │  Guest OS │    └─────────┘ └─────────┘
├───────────┤ ├───────────┤    ┌─────────────────────┐
│     Hypervisor          │    │     Docker Engine     │
├─────────────────────────┤    ├─────────────────────┤
│       Host OS           │    │       Host OS         │
└─────────────────────────┘    └─────────────────────┘

每个 VM 都有自己的 OS 内核      所有容器共享 Host OS 内核
启动需要分钟                      启动只需要秒
吃内存（每个 GB 级别）            省内存（每个 MB 级别）
```

## 面试话术

> 问："Docker 和虚拟机有什么区别？"
> 答："虚拟机虚拟硬件，每个 VM 有自己的操作系统，资源开销大、启动慢。Docker 用操作系统级虚拟化，容器共享宿主机内核，只隔离应用层，启动秒级，资源开销小。VM 更安全（完全隔离），Docker 更高效（共享内核）。"

## 一张图总结工作流

```
Dockerfile ──build──→ Image ──push──→ Registry (Docker Hub)
                         │
                       run
                         │
                         ▼
                     Container (你的应用在跑)
```

← [[Docker 学习路线]] | → [[Docker 常用命令]]
