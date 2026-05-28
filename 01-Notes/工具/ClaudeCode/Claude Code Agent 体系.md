---
date: "2026-05-28"
tags: [ClaudeCode, Agent, 工具]
---

# Claude Code Agent 体系

> Claude Code 支持 80+ 预定义 Agent 角色，覆盖开发、运维、安全、测试等全流程

## Agent 分类

### 核心开发（core/）
| Agent | 职责 |
|-------|------|
| `coder` | 写代码实现 |
| `reviewer` | 代码审查 |
| `tester` | 写测试 |
| `planner` | 设计方案 |
| `researcher` | 调研分析 |

### 语言专家
| Agent | 专长 |
|-------|------|
| `python-pro` | Python 专家 |
| `javascript-pro` | JS/Node.js |
| `typescript-pro` | TypeScript 深度 |
| `django-pro` | Django 框架 |
| `fastapi-pro` | FastAPI 框架 |
| `temporal-python-pro` | Temporal 工作流 |

### 架构与设计
| Agent | 职责 |
|-------|------|
| `architect-review` | 架构审查 |
| `backend-architect` | 后端架构 |
| `event-sourcing-architect` | 事件溯源 |
| `graphql-architect` | GraphQL 设计 |

### 安全
| Agent | 职责 |
|-------|------|
| `security-auditor` | 安全审计（OWASP、漏洞扫描） |
| `security-manager` | 安全机制实现 |

### 测试
| Agent | 职责 |
|-------|------|
| `tdd-orchestrator` | TDD 红-绿-重构流程 |
| `test-automator` | 自动化测试套件 |
| `production-validator` | 生产部署验证 |

### 性能
| Agent | 职责 |
|-------|------|
| `performance-engineer` | 性能优化 |
| `performance-benchmarker` | 基准测试 |

### 运维部署
| Agent | 职责 |
|-------|------|
| `deployment-engineer` | CI/CD、GitOps |
| `dx-optimizer` | 开发体验优化 |

### 文档与教学
| Agent | 职责 |
|-------|------|
| `docs-architect` | 文档生成 |
| `tutorial-engineer` | 教程编写 |

### 前端/移动端
| Agent | 职责 |
|-------|------|
| `frontend-developer` | React/Vue 前端 |
| `mobile-developer` | React Native/Flutter |

### 协作与共识（高级）
| Agent | 职责 |
|-------|------|
| `hierarchical-coordinator` | 层级式蜂群 |
| `mesh-coordinator` | 去中心化网格 |
| `raft-manager` | Raft 共识算法 |
| `crdt-synchronizer` | 无冲突数据类型 |

## 什么时候用哪个

| 场景 | 推荐 Agent |
|------|-----------|
| 写新功能 | `coder` → `tester` → `reviewer` 流水线 |
| 改 bug | `debugger` → `coder` |
| 安全审查 | `security-auditor` |
| 性能问题 | `performance-engineer` |
| 复杂架构 | `architect-review` + `backend-architect` |
| 写 API | `fastapi-pro` 或 `django-pro` |
| 多文件重构 | 启动 swarm（`swarm_init`）协调多个 Agent |

## Agent 协作模式

参见 CLAUDE.md 中的三种模式：
- **Pipeline**：A → B → C → D（串行依赖）
- **Fan-out**：Lead → A,B,C → Lead（并行）
- **Supervisor**：Lead ↔ workers（持续协调）

关联：[[Ruflo 使用指南]]
