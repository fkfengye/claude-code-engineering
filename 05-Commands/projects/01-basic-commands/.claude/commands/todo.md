---
description: 在代码中添加 TODO 注释
argument-hint: [todo 消息，使用 ! 表示高优先级]
allowed-tools: Read, Edit
---

根据 $ARGUMENTS 添加 TODO 注释。

## 优先级检测

- 以 `!` 开头 → 高优先级：`// TODO [HIGH]: message`
- 以 `?` 开头 → 待讨论：`// TODO [DISCUSS]: message`
- 无标记 → 普通：`// TODO: message`

## 按语言的注释格式

检测文件类型并使用适当的注释语法：

- JavaScript/TypeScript：`// TODO: message`
- Python：`# TODO: message`
- HTML：`<!-- TODO: message -->`
- CSS：`/* TODO: message */`
- Shell：`# TODO: message`

## 步骤

1. 识别文件上下文（当前打开或最近编辑的文件）
2. 解析消息并检测优先级
3. 适当格式化 TODO 注释
4. 添加到合理的位置：
   - 如果上下文清晰，在相关代码附近
   - 否则在函数/代码块顶部
5. 确认添加成功

## 示例

输入：`/todo fix null check`
输出：`// TODO: fix null check`

输入：`/todo ! critical security fix`
输出：`// TODO [HIGH]: critical security fix`

输入：`/todo ? should we use async here`
输出：`// TODO [DISCUSS]: should we use async here`

## 输出

简要确认：
```
✓ 已在 [file]:[line] 添加 TODO
```
