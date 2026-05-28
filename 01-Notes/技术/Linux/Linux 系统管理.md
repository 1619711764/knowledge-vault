---
date: "2026-05-28"
tags: [Linux, 系统管理, 命令]
---

# Linux 系统管理

## 进程管理

```bash
ps aux                   # 列出所有进程
ps aux | grep python     # 查找 Python 进程

top                      # 实时进程监控（q 退出）
htop                     # 更好看的 top（需安装）

kill 1234                # 终止进程 PID=1234
kill -9 1234             # 强制终止
pkill -f python          # 按名称终止

jobs                     # 查看后台任务
fg %1                    # 把后台任务 1 调到前台
bg %1                    # 让任务 1 在后台运行
```

`Ctrl+Z` 暂停当前进程 → `bg` 放到后台 → `fg` 拉回前台

## 磁盘和内存

```bash
df -h                    # 磁盘使用情况
du -sh ./dir/            # 目录占用大小
du -h --max-depth=1      # 当前目录下各子目录大小

free -h                  # 内存使用情况
```

## 系统信息

```bash
uname -a                 # 系统信息
lscpu                    # CPU 信息
lsblk                    # 磁盘设备列表
uptime                   # 运行时长 + 负载
who                      # 当前登录用户

dmesg | tail             # 最近的系统日志
journalctl -u nginx      # 查看 nginx 的 systemd 日志
```

## 定时任务

```bash
crontab -l               # 查看当前定时任务
crontab -e               # 编辑定时任务

# 格式：分 时 日 月 周 命令
# 0 2 * * * /backup.sh   每天凌晨 2 点执行备份
```

## 包管理

```bash
# Debian/Ubuntu
apt update && apt upgrade
apt install nginx

# CentOS/RHEL
yum install nginx
```

← [[Linux 文本处理]] | → [[Linux 权限管理]]
