---
date: "2026-05-28"
tags: [Python, 进阶]
---

# Python 文件操作

## 读文件

```python
# 方式 1：一次性读取
with open("file.txt", "r", encoding="utf-8") as f:
    content = f.read()

# 方式 2：逐行读取（大文件推荐）
with open("file.txt", "r", encoding="utf-8") as f:
    for line in f:
        print(line.strip())
```

## 写文件

```python
with open("output.txt", "w", encoding="utf-8") as f:
    f.write("Hello\n")
    f.write("World\n")

# 追加模式
with open("log.txt", "a", encoding="utf-8") as f:
    f.write("新的一行\n")
```

## 文件模式

| 模式 | 含义 |
|------|------|
| `r` | 只读（默认） |
| `w` | 写入（覆盖） |
| `a` | 追加 |
| `r+` | 读写 |
| `b` | 二进制模式 |

## with 语句

`with` 自动关闭文件，即使出现异常。**永远用 with，不要手动 f.close()**。

## pathlib（推荐）

```python
from pathlib import Path

p = Path("data/config.json")
if p.exists():
    text = p.read_text(encoding="utf-8")
    p.write_text(text.replace("old", "new"), encoding="utf-8")
```

↑ [[Python 学习路线]] | ← [[Python 常用库]] | → [[Python 错误处理]]
