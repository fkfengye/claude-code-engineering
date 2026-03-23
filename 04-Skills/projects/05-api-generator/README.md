# API 文档生成器 Skill

一个可用于生产的从源代码生成 API 文档的 skill。

## 功能特性

- **多框架支持**：Express.js, FastAPI, Spring Boot, Go (Gin/Echo)
- **多种输出格式**：Markdown, OpenAPI 3.0
- **自动化路由检测**：用于批量处理的 Python 脚本
- **验证工具**：OpenAPI 规范验证

## 项目结构

```
04-api-generator/
├── SKILL.md                    # 主 skill 文件
├── PATTERNS.md                 # 框架检测模式
├── STANDARDS.md                # 文档标准
├── EXAMPLES.md                 # 输入/输出示例
├── templates/
│   ├── index.md               # API 索引模板
│   ├── endpoint.md            # 端点文档模板
│   └── openapi.yaml           # OpenAPI 规范模板
└── scripts/
    ├── detect_routes.py       # 路由检测脚本
    └── validate_openapi.sh    # OpenAPI 验证脚本
```

## 使用示例

### 单个端点文档

让 Claude 记录特定端点：
```
请记录这个 Express 路由：
router.get('/users/:id', userController.getUser);
```

### 批量文档

扫描整个目录：
```
扫描 src/routes 目录并为所有端点生成 API 文档。
```

### OpenAPI 生成

生成 OpenAPI 规范：
```
为 src/api 中定义的 API 生成 OpenAPI 3.0 规范。
```

## 脚本

### 路由检测

```bash
# 检测所有路由
python scripts/detect_routes.py src/

# 仅检测 Express 路由
python scripts/detect_routes.py src/ --framework express

# 保存到文件
python scripts/detect_routes.py src/ -o routes.json
```

### OpenAPI 验证

```bash
# 验证 OpenAPI 规范
./scripts/validate_openapi.sh api-spec.yaml
```

## allowed-tools 配置

此 skill 使用：
- `Read` - 读取源文件
- `Grep` - 搜索路由模式
- `Glob` - 查找文件
- `Write` - 创建文档文件
- `Bash(python:*)` - 运行 Python 脚本
- `Bash(./scripts/*:*)` - 运行项目脚本

无 `Edit` 权限 - 此 skill 创建新文件但不修改现有文件。
