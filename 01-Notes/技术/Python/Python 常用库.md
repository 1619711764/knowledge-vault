---
date: "2026-05-28"
tags: [Python, 库]
---

# Python 常用库

## 标准库（自带，不用安装）

| 模块 | 用途 | 常用 API |
|------|------|----------|
| `os` | 操作系统接口 | `os.path.join()`, `os.listdir()`, `os.getenv()` |
| `sys` | 系统参数 | `sys.argv`, `sys.exit()`, `sys.path` |
| `json` | JSON 处理 | `json.loads()`, `json.dumps()` |
| `datetime` | 日期时间 | `datetime.now()`, `timedelta` |
| `pathlib` | 路径操作（推荐） | `Path("a/b").exists()` |
| `re` | 正则表达式 | `re.match()`, `re.findall()` |
| `collections` | 高级容器 | `defaultdict`, `Counter`, `deque` |
| `itertools` | 迭代工具 | `chain()`, `groupby()` |
| `subprocess` | 调用外部命令 | `subprocess.run()` |

## 常用第三方库

| 库 | 用途 | 安装 |
|----|------|------|
| `requests` | HTTP 请求 | `pip install requests` |
| `numpy` | 科学计算 | `pip install numpy` |
| `pandas` | 数据分析 | `pip install pandas` |
| `fastapi` | Web API | `pip install fastapi` |
| `rich` | 终端美化 | `pip install rich` |
| `pydantic` | 数据验证 | `pip install pydantic` |

## 速查示例

```python
import json
data = '{"name": "张三", "age": 25}'
obj = json.loads(data)       # 字符串 → 字典
text = json.dumps(obj)       # 字典 → 字符串

from datetime import datetime
now = datetime.now()
print(now.strftime("%Y-%m-%d %H:%M"))  # 2026-05-28 15:30

from pathlib import Path
home = Path.home()
config = home / ".config" / "app.yaml"
if config.exists():
    print("配置文件存在")
```

← [[Python 函数与模块]] | ↑ [[Python 学习路线]]
