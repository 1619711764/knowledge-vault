---
date: "2026-05-28"
tags: [Python, 基础]
---

# Python 数据类型

## 核心类型一览

| 类型 | 关键字 | 可变 | 有序 | 示例 |
|------|--------|------|------|------|
| 整数 | `int` | 不可变 | - | `42` |
| 浮点数 | `float` | 不可变 | - | `3.14` |
| 字符串 | `str` | 不可变 | 有序 | `"hello"` |
| 列表 | `list` | 可变 | 有序 | `[1, 2, 3]` |
| 元组 | `tuple` | 不可变 | 有序 | `(1, 2, 3)` |
| 字典 | `dict` | 可变 | 无序 | `{"key": "value"}` |
| 集合 | `set` | 可变 | 无序 | `{1, 2, 3}` |
| 布尔 | `bool` | 不可变 | - | `True` / `False` |

## 字符串

```python
name = "张三"
greeting = f"你好，{name}"  # f-string (Python 3.6+)
text = "hello world"
print(text.upper())       # HELLO WORLD
print(text.split(" "))    # ['hello', 'world']
```

## 列表

```python
fruits = ["苹果", "香蕉", "橙子"]
fruits.append("葡萄")      # 追加
fruits[0]                  # 索引 → "苹果"
fruits[-1]                 # 倒数第一 → "葡萄"
fruits[0:2]                # 切片 → ["苹果", "香蕉"]
```

## 字典

```python
person = {
    "name": "张三",
    "age": 25,
    "skills": ["Python", "Linux"]
}
print(person["name"])      # 张三
person["city"] = "北京"    # 添加新键
```

## 常用类型转换

```python
int("42")       # 字符串 → 整数 → 42
str(42)         # 整数 → 字符串 → "42"
list("abc")     # 字符串 → 列表 → ['a', 'b', 'c']
```

← [[Python 基础语法]] | → [[Python 函数与模块]]
