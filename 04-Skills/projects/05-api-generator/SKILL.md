---
name: api-generating
description: Generate API endpoint code and documentation from specifications. Use when the user wants to create new API endpoints, generate route handlers, scaffold REST APIs, or produce OpenAPI/Swagger specs from code.
allowed-tools:
  - Read
  - Grep
  - Glob
  - Write
  - Bash(python:*)
  - Bash(./scripts/*:*)
---

# API 文档生成器

从源代码生成全面的 API 文档。

## 快速参考

| 任务 | 资源 |
|------|------|
| 识别框架 | 参见 `PATTERNS.md` |
| 文档标准 | 参见 `STANDARDS.md` |
| 输出示例 | 参见 `EXAMPLES.md` |

## 流程

### 步骤 1: 识别 API 端点

查找路由定义。关于框架特定的模式，参见 `PATTERNS.md`。

### 步骤 2: 提取信息

对于每个端点，提取：
- HTTP 方法（GET, POST, PUT, DELETE 等）
- 路径/路由
- 参数（路径、查询、正文）
- 请求/响应模式
- 认证要求

### 步骤 3: 生成文档

为每个端点使用 `templates/endpoint.md` 中的模板。

### 步骤 4: 创建概述

使用 `templates/index.md` 生成索引。

## 输出格式

### Markdown（默认）
生成适合 README 或文档站点的 markdown。

### OpenAPI/Swagger
如果需要，生成 OpenAPI 3.0 规范。参见 `templates/openapi.yaml`。

## 自动化

自动检测路由：
```bash
python scripts/detect_routes.py <source_directory>
```

验证 OpenAPI 规范：
```bash
./scripts/validate_openapi.sh <spec_file>
```
