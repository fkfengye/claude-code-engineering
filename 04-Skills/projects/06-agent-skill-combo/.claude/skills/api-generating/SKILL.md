---
name: api-generating
description: 从 Express 路由文件生成 API 端点文档。当用户要求为 Express.js 路由生成、更新或审查 API 文档时使用。
allowed-tools: [Read, Grep, Glob, Write, Bash(python *)]
---

# API 文档生成 Skill

## 工作流程 — 强制执行

**重要**：你必须按顺序遵循以下步骤。不要跳过或替换任何步骤。

### 步骤 1: 路由发现

**你必须使用 Python 脚本进行路由检测：**

```bash
python3 skills/scripts/detect-routes.py src/
```

不要使用 Grep 手动搜索路由——该脚本处理了 Grep 模式会遗漏的边界情况
（动态路由、中间件挂载的子路由器、重导出的路由）。

### 步骤 2: 路由分析

对于脚本发现的每个路由：

1. 读取路由处理器源文件
2. 识别：HTTP 方法、路径、参数、请求体 schema、响应 schema
3. 检查认证中间件（例如 `requireAuth`、`isAdmin`）
4. 检查验证中间件（例如 `validate(schema)`）

### 步骤 3: 文档生成

使用 `templates/api-doc.md` 处的模板生成文档。

**输出规则：**
- 每个路由组一个 markdown 文件（例如 `docs/api/users.md`）
- 包含请求/响应示例
- 使用 🔒 标记需要认证的端点

## 参考文件

- 路由检测脚本：`scripts/detect-routes.py`
- 文档模板：`templates/api-doc.md`
- Express 路由模式：参见 PATTERNS.md（同一目录）

## 质量检查清单

完成前请验证：
- [ ] 脚本输出的所有路由都已文档化
- [ ] 请求/响应 schema 与实际代码匹配
- [ ] 认证要求已标记
- [ ] 示例是有效的 JSON
