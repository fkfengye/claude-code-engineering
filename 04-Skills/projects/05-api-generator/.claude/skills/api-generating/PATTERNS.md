# API 文档模式

## 常见框架

### Express.js
```javascript
// 路由模式
app.get('/users/:id', handler)
router.post('/auth/login', authController.login)

// 查找：
// - app.get(), app.post() 等
// - router.METHOD()
// - @route 装饰器（如果使用装饰器）
```

### FastAPI (Python)
```python
# 路由模式
@app.get("/users/{user_id}")
@router.post("/auth/login")

# 查找：
# - @app.METHOD 装饰器
# - @router.METHOD 装饰器
# - Pydantic 模型用于模式
```

### Spring Boot (Java)
```java
// 路由模式
@GetMapping("/users/{id}")
@PostMapping("/auth/login")
@RequestMapping(value = "/api", method = RequestMethod.GET)

// 查找：
// - @XXXMapping 注解
// - @RequestMapping
// - @RestController 类
```

### Go (Gin/Echo)
```go
// 路由模式
r.GET("/users/:id", handler)
e.POST("/auth/login", controller.Login)

// 查找：
// - router.METHOD() 调用
// - 组定义
// - 中间件附件
```

## 参数检测

### 路径参数
- Express: `:paramName`
- FastAPI: `{param_name}`
- Spring: `{paramName}`
- Go: `:paramName` 或 `*paramName`

### 查询参数
查找：
- `req.query` (Express)
- `Query()` (FastAPI)
- `@RequestParam` (Spring)
- `c.Query()` (Gin)

### 正文参数
查找：
- `req.body` (Express)
- Pydantic 模型 (FastAPI)
- `@RequestBody` (Spring)
- `c.Bind()` (Gin)

## 响应检测

### 状态码
- 查找显式状态码：`res.status(201)`, `status_code=201`
- 默认通常是 200
- 错误处理器表示错误码

### 响应模式
- TypeScript 接口/类型
- Pydantic 模型
- Java DTO
- 带 json 标签的 Go 结构体
