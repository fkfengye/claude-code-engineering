# 文档标准

## 通用原则

1. **清晰性**：文档应该清晰明确
2. **完整性**：包含所有必要信息
3. **一致性**：自始至终遵循相同格式
4. **时效性**：保持文档最新

## 端点文档

每个端点应记录：

### 必填字段
- **方法**：HTTP 方法（GET, POST, PUT, DELETE, PATCH）
- **路径**：完整端点路径包括基础 URL
- **描述**：端点的功能
- **参数**：所有输入参数
- **响应**：预期的响应格式

### 可选字段
- **认证**：所需的认证方法
- **速率限制**：任何速率限制
- **弃用**：如果端点已弃用
- **示例**：请求/响应示例

## 参数文档

对于每个参数，包括：

| 字段 | 必填 | 描述 |
|-------|------|------|
| name | 是 | 参数名称 |
| location | 是 | path, query, header, body |
| type | 是 | 数据类型 |
| required | 是 | true/false |
| description | 是 | 用途 |
| default | 否 | 如果可选的默认值 |
| constraints | 否 | 验证规则 |

## 响应文档

### 成功响应
```markdown
**状态码**: 200 OK

**响应体**:
| 字段 | 类型 | 描述 |
|------|------|------|
| id | string | 唯一标识符 |
| ... | ... | ... |
```

### 错误响应
记录常见错误情况：
- 400 Bad Request
- 401 Unauthorized
- 403 Forbidden
- 404 Not Found
- 500 Internal Server Error

## 写作风格

- 使用现在时："Returns a list" 而不是 "Will return a list"
- 直接表达："Gets user by ID" 而不是 "This endpoint is used to get a user by their ID"
- 使用一致的术语
- 除非有明确解释，否则避免使用术语
