# 端点文档模板

为每个 API 端点使用此模板：

```markdown
## {METHOD} {PATH}

{简要描述此端点的功能。}

### 认证
{必需 | 可选 | 无}

### 参数

| 名称 | 位置 | 类型 | 必填 | 描述 |
|------|------|------|------|------|
| {name} | {path/query/header/body} | {type} | {Yes/No} | {description} |

### 请求体
{如果适用}

```json
{
  "field": "value"
}
```

### 响应

#### {状态码} {状态文本}
{描述何时会发生此响应}

```json
{
  "example": "response"
}
```

### 示例

**请求**:
```bash
curl -X {METHOD} '{BASE_URL}{PATH}' \
  -H 'Content-Type: application/json' \
  -d '{request_body}'
```

**响应**:
```json
{
  "example": "response"
}
```

### 备注
{任何附加信息、注意事项或相关端点}
```
