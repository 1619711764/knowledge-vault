---
date: "2026-05-28"
tags: [Python, 进阶]
---

# Python 函数与模块

## 定义函数

```python
def greet(name):
    """向某人问好（这是 docstring）"""
    return f"你好，{name}！"

print(greet("张三"))  # 你好，张三！
```

## 参数类型

```python
# 位置参数
def add(a, b):
    return a + b

# 默认参数
def greet(name, greeting="你好"):
    return f"{greeting}，{name}"

# 关键字参数
greet(name="张三", greeting="早上好")

# 可变参数 *args（打包成元组）
def sum_all(*numbers):
    return sum(numbers)

# 关键字可变参数 **kwargs（打包成字典）
def print_info(**info):
    for key, value in info.items():
        print(f"{key}: {value}")
```

## 导入模块

```python
import math                    # 导入整个模块
math.sqrt(16)                  # 4.0

from datetime import datetime  # 只导入需要的
datetime.now()

import numpy as np             # 别名
np.array([1, 2, 3])

from .utils import helper      # 相对导入（包内部用）
```

## 常用内置函数

```python
len([1, 2, 3])    # 3 — 长度
type("hello")     # <class 'str'> — 类型
range(5)          # 0..4 — 范围序列
enumerate(items)  # 带索引的迭代
zip(a, b)         # 并行迭代
map(func, items)  # 映射
filter(func, seq) # 过滤
```

← [[Python 数据类型]] | → [[Python 常用库]]
