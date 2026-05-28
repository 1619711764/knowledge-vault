---
date: "2026-05-28"
tags: [Python, 进阶]
---

# Python 面向对象

## 定义类

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        return f"{self.name} says Woof!"

dog = Dog("旺财", 3)
print(dog.bark())   # 旺财 says Woof!
```

## 继承

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        pass

class Cat(Animal):
    def speak(self):
        return f"{self.name} says Meow!"

class Dog(Animal):
    def speak(self):
        return f"{self.name} says Woof!"
```

## 魔法方法

```python
class Point:
    def __init__(self, x, y):
        self.x, self.y = x, y

    def __str__(self):
        return f"({self.x}, {self.y})"

    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)
```

| 魔法方法 | 触发 |
|----------|------|
| `__init__` | 创建对象 |
| `__str__` | `print()` |
| `__len__` | `len()` |
| `__getitem__` | `obj[key]` |
| `__call__` | `obj()` |

> 和传统 `[[C 语言]]`/C++ 不同，Python 的面向对象更简洁，没有复杂的访问修饰符。

↑ [[Python 学习路线]] | ← [[Python 文件操作]] | → [[Python 错误处理]]
