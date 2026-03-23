# {{ROUTE_GROUP}} API

> 由 api-generating Skill 自动生成，请勿手动编辑。

## Base Path（基础路径）

`{{BASE_PATH}}`

---

## Endpoints（端点）

### {{METHOD}} `{{PATH}}`

{{#if AUTH}}🔒 需要认证{{/if}}

**描述**: {{DESCRIPTION}}

**参数**:

| 名称 | 位置 | 类型 | 必填 | 描述 |
|------|----|------|------|------|
{{#each PARAMS}}
| {{name}} | {{in}} | {{type}} | {{required}} | {{description}} |
{{/each}}

{{#if REQUEST_BODY}}
**请求体**:

```json
{{REQUEST_BODY_EXAMPLE}}
```
{{/if}}

**响应**:

| 状态码 | 描述 |
|--------|------|
{{#each RESPONSES}}
| {{status}} | {{description}} |
{{/each}}

**响应示例**:

```json
{{RESPONSE_EXAMPLE}}
```

---

## 错误码

| 代码 | 消息 | 描述 |
|------|---------|------|
| 400 | 错误请求 | 输入参数无效 |
| 401 | 未授权 | 认证令牌缺失或无效 |
| 404 | 未找到 | 资源不存在 |
| 500 | 服务器内部错误 | 意外的服务器错误 |
