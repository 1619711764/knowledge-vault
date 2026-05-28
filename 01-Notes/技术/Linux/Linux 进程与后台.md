---
date: "2026-05-28"
tags: [Linux, 进程, 命令]
---

# Linux 进程与后台

## 后台运行

```bash
python app.py &         # 直接在后台启动
sleep 100 &             # 后台任务示例

# 运行后自动出现：
# [1] 12345  ← [任务号] PID
```

## 查看后台任务

```bash
jobs                    # 当前 shell 后台任务列表
jobs -l                 # 显示 PID
ps                      # 当前 shell 的进程
ps aux                  # 所有进程
```

## 前后台切换

```bash
Ctrl+Z                  # 暂停当前前台任务
bg %1                   # 让任务 1 在后台继续运行
fg %1                   # 把后台任务 1 拉回前台
```

## 守护进程（长期后台运行）

```bash
nohup python app.py &           # 退出终端后仍运行
nohup python app.py > app.log 2>&1 &

# 用 screen/tmux（推荐）
screen -S myapp                  # 新建命名为 myapp 的 session
python app.py                    # 在里面运行
# Ctrl+A, D                      # 分离（detach）
screen -r myapp                  # 重新连接

# tmux
tmux new -s myapp
# Ctrl+B, D 分离
tmux attach -t myapp
```

## systemd 服务（生产环境）

```bash
systemctl start nginx            # 启动
systemctl stop nginx             # 停止
systemctl restart nginx          # 重启
systemctl status nginx           # 状态
systemctl enable nginx           # 开机自启
systemctl disable nginx          # 取消自启
journalctl -u nginx -f           # 实时日志
```

← [[Linux 压缩打包]] | ↑ [[Linux 常用命令]]
