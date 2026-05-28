---
date: "2026-05-28"
tags: [Linux, 命令, 进阶]
---

# Linux 管道与重定向

## 管道 `|`

把一个命令的**输出**变成另一个命令的**输入**：

```bash
ls -l | grep ".md"           # 查找 md 文件
cat notes.txt | wc -w        # 统计单词数
ps aux | grep nginx | awk '{print $2}'  # 获取 nginx 的 PID
history | sort | uniq -c | sort -rn | head -10  # 最常用的 10 个命令
```

> 管道是 Linux 哲学的核心：每个命令做一件事，组合起来完成复杂任务。

## 输出重定向

```bash
echo "hello" > file.txt      # 覆盖写入
echo "world" >> file.txt     # 追加写入
ls 2> error.log              # 只重定向错误输出
ls > all.log 2>&1            # 标准输出和错误都写入同一个文件
ls &> all.log                # 同上（bash 简写）
```

| 符号 | 含义 |
|------|------|
| `>` | 覆盖输出 |
| `>>` | 追加输出 |
| `2>` | 重定向 stderr |
| `2>&1` | stderr 合并到 stdout |
| `<` | 输入重定向 |
| `/dev/null` | 黑洞（丢弃输出）|

## 实用组合

```bash
# 静默执行，丢弃所有输出
some_command > /dev/null 2>&1

# 后台运行，日志写到文件
python app.py >> app.log 2>&1 &

# 管道串行处理
cat urls.txt | xargs -I {} curl -O {}
```

← [[Linux 常用命令]] | → [[Linux 网络命令]]
