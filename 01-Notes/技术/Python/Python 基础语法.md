---
date: "2026-05-28"
tags: [Python, 基础]
---

# Python 基础语法

## Hello World

```python
print("Hello, World!")
```

## 变量

Python 是动态类型，不需要声明类型：

```python
name = "张三"       # 字符串
age = 25            # 整数
height = 1.75       # 浮点数
is_student = True   # 布尔值
```

## 条件判断

```python
score = 85
if score >= 90:
    print("优秀")
elif score >= 80:
    print("良好")
else:
    print("继续加油")
```

> 注意：Python 用**缩进**（4 个空格）表示代码块，不用 `{}`

## 循环

```python
# for 循环 — 遍历一个序列
for i in range(5):
    print(i)  # 输出 0 1 2 3 4

# while 循环 — 满足条件时一直执行
count = 0
while count < 3:
    print(count)
    count += 1
```

## 缩进规则

```python
# 正确 ✓
def foo():
    print("yes")

# 错误 ✗ — 没有缩进
def foo():
print("no")
```

> Python 的缩进是语法的一部分，不是可选的 — 这是和 `[[C 语言]]`、Java 最大的区别

继续 → [[Python 数据类型]] | [[Python 函数与模块]]
