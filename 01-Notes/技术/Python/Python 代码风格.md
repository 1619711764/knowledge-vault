---
date: "2026-05-28"
tags: [Python, 工具]
---

# Python 代码风格

## PEP 8 速查

| 规则 | 示例 |
|------|------|
| 缩进 4 空格 | 不要用 Tab |
| 每行 ≤ 79 字符 | `black` 默认 88 |
| 函数之间空 2 行 | `def` 前后各两空行 |
| 类之间空 2 行 |
| import 放在文件顶部 | 标准库 → 第三方 → 本地 |
| 变量名 `snake_case` | `user_name` |
| 类名 `PascalCase` | `UserProfile` |
| 常量 `UPPER_CASE` | `MAX_SIZE = 100` |

## 命名规范

```python
# ✓ 好的命名
user_list = [1, 2, 3]              # 列表用复数
user_count = len(user_list)         # 计数变量
is_active = True                    # 布尔用 is/has 前缀
def calculate_total(items): ...     # 动词开头
class UserRepository: ...           # 名词

# ✗ 不好的命名
a = [1, 2, 3]                       # 无意义的单字母
def func(x): ...                    # 无意义函数名
```

## 自动格式化

```bash
pip install black
black your_file.py    # 一键格式化
```

## 类型注解（Python 3.6+）

```python
def greet(name: str, age: int) -> str:
    return f"{name} 今年 {age} 岁"
```

结合 → [[Python VS Code 配置]]

↑ [[Python 学习路线]]
