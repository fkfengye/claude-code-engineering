---
name: api-conventions
description: 本项目的API设计模式与规范。涵盖RESTful URL命名规范、响应格式标准、错误处理和认证要求。适用于编写或审查API端点、设计新API、以及制定请求/响应格式决策。
allowed-tools:
  - Read
  - Grep
  - Glob
---

# API 设计规范

本文档定义了本项目的API设计标准。在处理API端点时，请遵循这些规范。

## URL 命名

- 资源使用复数名词：`/users`、`/orders`、`/products`
- 多单词资源使用 kebab-case：`/order-items`、`/user-profiles`
- belongsTo 关系使用嵌套资源：`/users/{id}/orders`
- 嵌套层级最多两级；超过两级应使用查询参数
- 筛选使用查询参数：`/orders?status=active&limit=20`

## 响应格式

所有API响应必须遵循以下结构：

```json
{
  "data": {},
  "error": null,
  "meta": {
    "page": 1,
    "limit": 20,
    "total": 100
  }
}
```

- `data`：成功时返回的业务数据
- `error`：错误时返回错误对象 `{ code, message, details }`，成功时为 `null`
- `meta`：分页和元信息，列表接口必须返回

## HTTP 状态码

- 200：成功返回数据
- 201：成功创建资源
- 400：请求参数错误
- 401：未认证
- 403：无权限
- 404：资源不存在
- 422：业务逻辑错误
- 500：服务器内部错误

## 认证

- 所有端点都需要Bearer令牌，除非明确标记为公开
- 公开端点必须使用 `@public` 注解标注
- 令牌格式：`Authorization: Bearer <jwt-token>`

## 版本控制

- API版本放在URL路径中：`/api/v1/users`
- 破坏性变更需要发布新版本
