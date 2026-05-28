---
date: "2026-05-28"
tags: [NLP, 面试, 话术]
---

# NLP 面试话术

> 面向数据分析 / 运维 / Agent 开发岗位的 NLP 面试准备

## 高频问题 + 标准回答

### Q1："你了解 NLP 吗？"

> 了解。NLP 的核心是让机器理解文本。实际工作中主要用分词、正则清洗、信息抽取这些技术。比如用 jieba 分词提取关键词，用正则表达式解析日志格式。了解 Word2Vec 和 BERT 的基本思想，但日常更多是工程落地而非模型训练。

### Q2："正则表达式会吗？用过哪些？"

> 常用。`\d` 匹配数字、`\w` 匹配字母数字、`[]` 字符集、`()` 分组捕获、`*+?` 量词。实际项目里用来解析日志格式、验证手机号邮箱、清洗文本。Python 的 `re` 模块 `search`/`findall`/`sub` 用得最多。

### Q3："文本数据怎么清洗？"

> 三步：去噪音（特殊字符、HTML 标签、多余空格）→ 统一格式（全角半角、大小写）→ 去停用词（的、了、是等无意义词）。用 Python 的 `re` 模块为主，jieba 分词配合。

### Q4："jieba 分词的三种模式区别？"

> 精确模式：最常用的，把句子精确切开；全模式：所有可能的词都切出来，速度快但有冗余；搜索引擎模式：在精确模式基础上对长词再切分，适合搜索场景。

### Q5："怎么做关键词提取？"

> 常用 TF-IDF 或直接词频统计。流程：分词 → 去停用词 → 统计词频 → 取 Top N。如果想效果好一点，用 jieba 自带的 `jieba.analyse.extract_tags()`。

## 综合实操题

> "给你一批运维日志，每天 100 万行，要你找出所有 ERROR 级别的异常 IP 并统计频率，怎么做？"

```python
import re
from collections import Counter

def extract_error_ips(logs):
    errors = Counter()
    for line in logs:
        if 'ERROR' in line:
            ip = re.search(r'\d+\.\d+\.\d+\.\d+', line)
            if ip:
                errors[ip.group()] += 1
    return errors.most_common(50)
```

> "数据量大怎么办？逐行读不要全加载到内存；用 `grep ERROR log.txt` 预处理；如果是生产环境接 Elasticsearch，用 ES 的聚合查询。"

## 简历中的 NLP 关键词

如果你的简历里写了 NLP 项目经验，确保能回答：
- Word2Vec 和 GloVe 的区别（Word2Vec 用上下文窗口，GloVe 用全局共现矩阵）
- BERT 为什么好（双向注意力机制，比单向模型理解上下文更好）
- TextCNN 的思想（用不同大小的卷积核抓局部特征，适合短文本分类）

← [[文本清洗与分词]] | ↑ [[NLP 速成笔记]]
