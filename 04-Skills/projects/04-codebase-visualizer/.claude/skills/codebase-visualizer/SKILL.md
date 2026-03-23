---
name: codebase-visualizer
description: Generate an interactive tree visualization of your codebase. Use when exploring a new repo or understanding project structure.
allowed-tools:
  - Bash(python *)
---

从项目根目录运行可视化脚本：

```bash
python .claude/skills/codebase-visualizer/scripts/visualize.py .
```

这会创建 `codebase-map.html` 并在默认浏览器中打开它。
