---
date: "2026-05-28"
tags: [Python, 工具, VS Code]
---

# Python VS Code 配置

## 必装插件

| 插件 | 用途 |
|------|------|
| **Python** (ms-python.python) | Python 语言支持 |
| **Pylance** | 智能提示、类型检查 |
| **Black Formatter** | 自动格式化 |
| **Ruff** | 超快的 Linter |

## settings.json 推荐

```json
{
  "[python]": {
    "editor.defaultFormatter": "ms-python.black-formatter",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.organizeImports": "explicit"
    }
  },
  "python.analysis.typeCheckingMode": "basic"
}
```

## 虚拟环境

```bash
# 创建虚拟环境
python -m venv .venv

# 激活（Windows）
.venv\Scripts\activate

# 激活（Linux/Mac）
source .venv/bin/activate

# 安装依赖
pip install -r requirements.txt

# 冻结依赖
pip freeze > requirements.txt
```

VS Code 会自动检测 `.venv` 目录。打开项目后 `Ctrl+Shift+P` → "Python: Select Interpreter" 选择虚拟环境。

关联：[[Python 代码风格]] | [[Python 学习路线]]
