---
date: "2026-05-28"
tags: [插件, 数据查询]
---

# Dataview

> [[Obsidian]] 的核心插件，用 SQL 风格语法查询笔记库，把 Vault 变成数据库

## 四种查询类型

| 类型 | 语法 | 示例 |
|------|------|------|
| **List** | `LIST` | 列出符合条件的所有笔记 |
| **Table** | `TABLE` | 表格展示笔记 + 属性 |
| **Task** | `TASK` | 从所有笔记收集待办任务 |
| **Calendar** | `CALENDAR` | 按日期日历视图 |

## 入门示例

### List — 列出带某标签的笔记

```dataview
LIST
FROM #Python
SORT file.name ASC
```

### Table — 表格展示含属性

```dataview
TABLE date, tags
FROM "01-Notes/技术"
SORT date DESC
```

### Task — 收集所有未完成任务

```dataview
TASK
FROM "02-Daily"
WHERE !completed
```

### 按修改时间列出最近笔记

```dataview
TABLE file.mtime as "修改时间"
FROM ""
SORT file.mtime DESC
LIMIT 10
```

## 过滤条件

| 条件 | 写法 |
|------|------|
| 来自某文件夹 | `FROM "01-Notes/技术"` |
| 带某标签 | `FROM #Python` |
| 不含某标签 | `WHERE !contains(tags, "MOC")` |
| 创建于某天后 | `WHERE file.cday > date("2026-01-01")` |
| 链接到某笔记 | `FROM [[Obsidian]]` |

## 内置属性

| 属性 | 含义 |
|------|------|
| `file.name` | 文件名 |
| `file.cday` | 创建日期 |
| `file.mtime` | 最后修改时间 |
| `file.tags` | 所有标签 |
| `file.outlinks` | 出去的链接 |
| `file.inlinks` | 进来的链接（谁引用了我） |

## 和 MOC 配合

在 [[内容地图 MOC]] 里内嵌 Dataview，MOC 页面会自动收集所有关联笔记，不用手动维护列表：

```dataview
TABLE date, tags
FROM [[]]
SORT date DESC
LIMIT 20
```

> `FROM [[]]` = 查找所有链接到当前页面的笔记，非常适合 MOC 页面。

参见：[[Obsidian]] | [[个人知识管理]]
