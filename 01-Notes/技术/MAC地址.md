---
date: "2026-05-28"
tags: [网络, MAC, 基础]
---

# MAC 地址

> Media Access Control — 网卡的物理身份证，出厂刻录，全球唯一

## IP vs MAC

| | IP 地址 | MAC 地址 |
|---|--------|---------|
| 类比 | 收货地址（可变） | 身份证号（不变） |
| 层级 | 网络层 | 数据链路层 |
| 可变 | 换网络就变 | 出厂烧录不变 |
| 格式 | `192.168.1.1` | `AA:BB:CC:DD:EE:FF` |

## 查看本机 MAC

```bash
# Linux
ip link show
# Windows
ipconfig /all | findstr "物理"
```

## 通信过程

局域网内设备通信用 MAC 地址。主机 A 要知道主机 B 的 MAC → 发 ARP 广播问"谁的 IP 是 192.168.1.20？"→ B 回复自己的 MAC

## 实际场景

- 公司网络 MAC 白名单认证
- Docker 容器有虚拟 MAC
- ARP 欺骗攻击 = 伪造 MAC 地址

关联：[[DNS协议]] | [[Linux 网络命令]]
