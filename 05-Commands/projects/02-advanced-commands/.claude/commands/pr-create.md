---
description: 创建 Pull Request，自动检测上下文
argument-hint: [标题] [描述]
allowed-tools: Bash(git:*), Bash(gh:*)
---

创建一个 Pull Request。

标题：$1
描述：$2

## 当前上下文（自动检测）

当前分支：
!`git branch --show-current`

此分支上的最近提交：
!`git log origin/main..HEAD --oneline 2>/dev/null || echo "没有领先于 main 的提交"`

变更的文件：
!`git diff --stat origin/main 2>/dev/null || git diff --stat HEAD~3`

## 操作步骤

1. 确保不在 main/master 分支上
2. 将当前分支推送到远程（如果还没有）
3. 使用 `gh pr create` 创建 PR：
   - 标题：$1（或根据分支名自动生成）
   - 正文：$2（或根据提交自动生成）
4. 返回 PR URL

## PR 正文模板

如果未提供 $2，则自动生成：

```markdown
## 概述
[根据提交信息自动生成]

## 变更内容
[变更文件列表及简要说明]

## 测试
- [ ] 本地测试通过
- [ ] 手动测试完成

---
由 `/pr-create` 创建
```

## 输出

```
✓ PR 已创建：[URL]

标题：[标题]
分支：[分支] → main
变更：[n] 个文件
```
