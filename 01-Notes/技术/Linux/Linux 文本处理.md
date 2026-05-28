---
date: "2026-05-28"
tags: [Linux, 文本处理, 命令]
---

# Linux 文本处理

## 查看与搜索

```bash
cat file.txt                  # 显示全部
tac file.txt                  # 倒序显示

grep "关键词" file.txt        # 搜索匹配行
grep -i "hello" file.txt      # 忽略大小写
grep -r "TODO" ./src/         # 递归搜索目录
grep -v "排除" file.txt       # 反向匹配
grep -c "pattern" file.txt    # 计数
```

## 管道组合

`|` 是关键 — 把一个命令的输出传给下一个：

```bash
cat /var/log/app.log | grep ERROR | head -20
# 显示日志中前 20 条 ERROR

ps aux | grep python | wc -l
# 统计运行的 Python 进程数

history | grep "git" | sort | uniq -c | sort -rn
# 你最常用的 git 命令排名
```

## 统计与排序

```bash
wc -l file.txt          # 行数
wc -w file.txt          # 单词数
wc -c file.txt          # 字节数

sort file.txt           # 排序
sort -n                 # 数字排序
sort -r                 # 倒序

uniq                    # 去重（通常先 sort）
uniq -c                 # 去重并计数
```

## 文本截取

```bash
head -n 5 file.txt      # 前 5 行
tail -n 20 file.txt     # 后 20 行

cut -d',' -f1 data.csv  # 按逗号分隔，取第 1 列
cut -c1-10 file.txt     # 每行取前 10 个字符

awk '{print $1}' file   # 打印第 1 列
sed 's/old/new/g' file  # 替换文本
```

← [[Linux 文件操作]] | → [[Linux 系统管理]]
