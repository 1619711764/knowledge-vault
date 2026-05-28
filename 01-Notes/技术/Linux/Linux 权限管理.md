---
date: "2026-05-28"
tags: [Linux, 权限, 命令]
---

# Linux 权限管理

## 权限模型

```bash
ls -l file.txt
# -rwxr-xr-x 1 user group 1024 May 28 10:00 file.txt
#  └┬┘└─┬─┘└─┬─┘
#   │   │    └── 其他人的权限 (r-x)
#   │   └─────── 所属组的权限 (r-x)
#   └─────────── 所有者的权限 (rwx)
```

| 符号 | 含义 | 数字 |
|------|------|------|
| `r` | 读 | 4 |
| `w` | 写 | 2 |
| `x` | 执行 | 1 |
| `-` | 无权限 | 0 |

## chmod 改权限

```bash
chmod 755 script.sh    # rwx r-x r-x（最常用）
chmod 644 file.txt     # rw- r-- r--
chmod 600 secret.key   # rw- --- ---（仅自己能读写）
chmod +x script.sh     # 添加执行权限
chmod -w file.txt      # 移除写权限
```

常用数字组合：
- `777` — 所有人所有权限（不安全）
- `755` — 目录/脚本 ✅
- `644` — 普通文件 ✅
- `600` — 密钥文件 ✅

## chown 改所有者

```bash
chown user:group file.txt       # 同时改用户和组
chown -R user:group ./dir/      # 递归修改目录
```

## sudo 提权

```bash
sudo apt install nginx         # 以 root 身份执行一条命令
sudo -i                        # 切换为 root shell
sudo !!                        # 以 sudo 重新执行上一条命令
```

> 普通用户不要直接登录 root。用 `sudo` 代替 — 安全、可审计。

← [[Linux 系统管理]] | ↑ [[Linux 常用命令]]
