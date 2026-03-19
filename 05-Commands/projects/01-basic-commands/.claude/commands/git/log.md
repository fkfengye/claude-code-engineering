---
description: 显示最近的 git 提交历史及摘要
argument-hint: [可选：提交数量，默认 5]
allowed-tools: Bash(git:*)
model: haiku
---

显示最近的 git 提交历史。

提交数量：$ARGUMENTS（未指定时默认为 5）

## 步骤

1. 执行 `git log --oneline -n [数量]`
2. 提供简短摘要

## 输出格式

```
## 最近的提交

| Hash | 消息 | 作者 | 时间 |
|------|---------|--------|------|
| abc123 | feat: add login | John | 2小时前 |
| def456 | fix: null check | Jane | 5小时前 |
...

### 摘要
- 总计：显示 [n] 条提交
- 最活跃的：[出现频率最高的提交类型]
- 最近的重点：[最近工作的主要内容]
```

保持简洁和易浏览。
