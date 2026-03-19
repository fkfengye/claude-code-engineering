---
description: 带安全检查和自动测试的部署
argument-hint: [环境：staging | production]
allowed-tools: Bash(npm:*), Bash(git:*), Read
hooks:
  - event: PreToolUse
    matcher: Bash
    command: |
      if [[ "$TOOL_INPUT" == *"production"* ]] && [[ "$TOOL_INPUT" == *"deploy"* ]]; then
        echo "⚠️ 检测到生产环境部署 - 需要额外验证"
      fi
  - event: PostToolUse
    matcher: Bash
    command: echo "✓ 步骤完成于 $(date +%H:%M:%S)"
    once: true
---

将应用部署到：$ARGUMENTS

## 部署前检查

部署前请确认：
1. 所有测试通过（`npm test`）
2. 没有未提交的更改（`git status`）
3. 在正确的分支上（生产环境为 main/master）

## 部署步骤

### 对于预发环境（$ARGUMENTS = "staging"）
1. 运行测试
2. 构建应用
3. 部署到预发环境
4. 验证部署健康状态

### 对于生产环境（$ARGUMENTS = "production"）
1. 运行完整测试套件
2. 检查预发环境是否健康
3. 为发布创建 git 标签
4. 构建并部署
5. 验证生产环境健康状态
6. 通知团队

## 安全规则

- 绝对不要从非 main 分支部署到生产环境
- 部署前必须运行测试
- 如果测试失败，立即停止并报告

## 输出

```
## 部署报告

环境：[staging/production]
状态：[success/failed]
耗时：[duration]

### 已完成的步骤
✓ 测试通过
✓ 构建成功
✓ 部署完成
✓ 健康检查通过

### 下一步
[需要后续跟进的操作]
```
