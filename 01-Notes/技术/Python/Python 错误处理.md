---
date: "2026-05-28"
tags: [Python, 基础]
---

# Python 错误处理

## try/except

```python
try:
    num = int(input("输入数字: "))
    result = 100 / num
except ValueError:
    print("请输入一个有效的数字！")
except ZeroDivisionError:
    print("不能除以零！")
except Exception as e:
    print(f"未知错误: {e}")
else:
    print(f"结果是: {result}")  # 没有异常时执行
finally:
    print("无论是否异常都会执行")
```

## 常见异常

| 异常 | 触发场景 |
|------|---------|
| `ValueError` | 类型对但值不对 |
| `TypeError` | 类型错误 |
| `IndexError` | 列表索引越界 |
| `KeyError` | 字典键不存在 |
| `FileNotFoundError` | 文件不存在 |
| `ZeroDivisionError` | 除以零 |

## 自定义异常

```python
class InvalidAgeError(Exception):
    """年龄无效的自定义异常"""
    pass

def set_age(age):
    if age < 0 or age > 150:
        raise InvalidAgeError(f"年龄 {age} 不合理")
    print(f"年龄设为 {age}")
```

## 原则

1. **不要用 `except:` 裸捕获** — 会吞掉所有异常
2. **捕获具体的异常类型**
3. **不要滥用 try** — 先检查条件（如 `if key in dict`）

↑ [[Python 学习路线]] | ← [[Python 面向对象]] | ← [[Python 文件操作]]
