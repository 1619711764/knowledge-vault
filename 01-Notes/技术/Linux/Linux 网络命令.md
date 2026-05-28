---
date: "2026-05-28"
tags: [Linux, 网络, 命令]
---

# Linux 网络命令

## 下载文件

```bash
curl -O https://example.com/file.zip    # 下载并保存
curl -L https://redirect-url             # 跟随重定向
curl -H "Authorization: Bearer xxx" url  # 带请求头
curl -X POST -d '{"key":"val"}' url     # POST JSON

wget https://example.com/file.zip       # 简单下载
wget -c url                              # 断点续传
```

## 网络诊断

```bash
ping google.com             # 测试连通性（Ctrl+C 停止）
ping -c 4 google.com        # 发 4 个包后停止

ss -tlnp                    # 查看监听的 TCP 端口
ss -tlnp | grep 8080        # 查看 8080 端口被谁占用

nc -zv host 443             # 测试端口是否通
nc -l 8080                  # 临时监听 8080 端口
```

## DNS 相关

```bash
nslookup example.com         # 查 DNS
dig example.com              # 更详细的 DNS 查询
host example.com             # 简单版
```

## 常用组合

```bash
# 测试 API
curl -s https://api.github.com/users/octocat | python -m json.tool

# 看哪个进程占用了 3000 端口
lsof -i :3000          # macOS
ss -tlnp | grep 3000   # Linux
```

← [[Linux 管道与重定向]] | → [[Linux 压缩打包]]
