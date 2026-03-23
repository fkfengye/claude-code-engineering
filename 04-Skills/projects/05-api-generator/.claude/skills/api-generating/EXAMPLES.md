# API 文档示例

## 示例 1: 简单的 Express.js 端点

### 输入代码
```javascript
// routes/users.js
router.get('/users/:id', async (req, res) => {
  const { id } = req.params;
  const user = await User.findById(id);
  if (!user) {
    return res.status(404).json({ error: 'User not found' });
  }
  res.json(user);
});
```

### 生成的文档
```markdown
## GET /users/:id

通过唯一标识符检索用户。

### 参数

| 名称 | 位置 | 类型 | 必填 | 描述 |
|------|------|------|------|------|
| id | path | string | Yes | 用户的唯一标识符 |

### 响应

#### 200 OK
返回用户对象。

```json
{
  "id": "123",
  "name": "John Doe",
  "email": "john@example.com",
  "createdAt": "2024-01-15T10:30:00Z"
}
```

#### 404 Not Found
指定 ID 的用户不存在。

```json
{
  "error": "User not found"
}
```
```

---

## 示例 2: 带 Pydantic 的 FastAPI

### 输入代码
```python
from pydantic import BaseModel
from fastapi import FastAPI, HTTPException

class UserCreate(BaseModel):
    name: str
    email: str
    password: str

class UserResponse(BaseModel):
    id: str
    name: str
    email: str

@app.post("/users", response_model=UserResponse, status_code=201)
async def create_user(user: UserCreate):
    """创建新用户账户。"""
    # ... 实现
    return new_user
```

### 生成的文档
```markdown
## POST /users

创建新用户账户。

### 请求体

| 字段 | 类型 | 必填 | 描述 |
|------|------|------|------|
| name | string | Yes | 用户的显示名称 |
| email | string | Yes | 用户的电子邮件地址 |
| password | string | Yes | 用户的密码 |

**示例**:
```json
{
  "name": "Jane Smith",
  "email": "jane@example.com",
  "password": "securePassword123"
}
```

### 响应

#### 201 Created
用户创建成功。

```json
{
  "id": "456",
  "name": "Jane Smith",
  "email": "jane@example.com"
}
```
```

---

## 示例 3: OpenAPI 规范输出

### 生成的 OpenAPI YAML
```yaml
openapi: 3.0.0
info:
  title: User API
  version: 1.0.0
paths:
  /users/{id}:
    get:
      summary: Get user by ID
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/User'
        '404':
          description: User not found
components:
  schemas:
    User:
      type: object
      properties:
        id:
          type: string
        name:
          type: string
        email:
          type: string
```
