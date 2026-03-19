---
description: 快速 git 提交，支持自动生成或指定提交信息
argument-hint: [可选：提交信息]
allowed-tools: Bash(git status:*), Bash(git add:*), Bash(git commit:*), Bash(git diff:*)
model: haiku
---

创建 git 提交。

如果提供了消息：$ARGUMENTS
- 使用该消息作为提交信息

如果没有提供消息：
- 使用 `git diff --staged` 分析变更（如果没有暂存内容则使用 `git diff`）
- 生成简洁、有意义的提交信息

## 步骤

1. 执行 `git status` 查看当前状态
2. 如果没有暂存内容，执行 `git add .` 暂存所有变更
3. 使用 `git diff --staged` 审查将要提交的内容
4. 创建提交：
   - 如果提供了 `$ARGUMENTS`，使用它作为提交信息
   - 否则根据 diff 内容生成提交信息
5. 显示提交结果

## 提交信息格式

- 以类型开头：`feat:`、`fix:`、`docs:`、`refactor:`、`test:`、`chore:`
- 简洁但有描述性（第一行最多 72 个字符）
- 示例：`feat: add user authentication with JWT`

## 输出

显示简短确认信息：
```
✓ 已提交：[提交信息]
  [数量] 个文件已更改
```
