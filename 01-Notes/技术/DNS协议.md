---
date: "2026-05-28"
tags: [网络, DNS, 基础]
---

# DNS 协议

> Domain Name System — 互联网的电话簿，域名 → IP 地址

## 一句话

你输入 `baidu.com`，DNS 告诉电脑："这个网站的 IP 是 `110.242.68.66`"

## 解析链路

```
浏览器缓存 → OS 缓存(hosts) → 运营商 DNS → 根 DNS → .com DNS → baidu.com DNS
                                                                      │
                                                               返回 IP 地址
```

## 常用命令

```bash
nslookup baidu.com          # 查 IP
dig baidu.com               # 详细查询
ping baidu.com               # 先 DNS 解析再测试连通
```

## 面试必问

> "浏览器输入 URL 后发生了什么？"
> 第一步：DNS 解析，域名 → IP 地址，然后才能建立 TCP 连接

关联：[[Linux 网络命令]] | [[内网服务器开发]]
