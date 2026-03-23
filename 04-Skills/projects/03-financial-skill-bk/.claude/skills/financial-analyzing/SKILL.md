---
name: financial-analyzing
description: Use when user asks about revenue, costs, profit, profit margin, ROI, financial metrics, or needs financial analysis of a company/project
---

# Financial Analyzing Skill

## Overview

分析财务数据、计算财务比率并生成结构化分析报告。当用户询问收入、成本、利润、利润率、投资回报率、财务指标或需要对公司/项目进行财务分析时使用。

## Quick Reference

| 用户问题类型 | 加载资源 | 说明 |
|------------|---------|------|
| 收入增长、同比/环比、ARPU | `reference/revenue.md` | 收入分析公式与异常信号 |
| 成本结构、Cost Ratio | `reference/costs.md` | 成本分析指标 |
| 毛利率、净利率、ROE/ROA | `reference/profitability.md` | 盈利能力与回报率分析 |
| 生成完整分析报告 | `templates/analysis_report.md` | 标准化报告模板 |

## Workflow

### 1. 识别财务数据类型

根据用户问题确定分析类型：
- **收入分析** → 加载 `reference/revenue.md`
- **成本分析** → 加载 `reference/costs.md`
- **盈利分析** → 加载 `reference/profitability.md`
- **综合报告** → 加载所有参考 + `templates/analysis_report.md`

### 2. 数据准备

收集财务数据，格式示例：

```json
{
  "revenue": 13700000,
  "previous_revenue": 10200000,
  "cogs": 4037000,
  "operating_expenses": 5700000,
  "net_income": 2680000,
  "total_assets": 11500000,
  "shareholders_equity": 6200000
}
```

### 3. 计算财务比率

使用 `scripts/calculate_ratios.py` 进行计算：

```bash
python scripts/calculate_ratios.py data/sample_financials.json
```

脚本输出：
- Revenue Growth (%)
- Gross Margin (%)
- Operating Margin (%)
- Net Margin (%)
- ROA (%)
- ROE (%)

### 4. 生成分析报告

按照 `templates/analysis_report.md` 模板结构输出报告。

## 数据文件位置

- 样本数据：`data/sample_financials.json`
- 计算脚本：`scripts/calculate_ratios.py`

## 异常信号识别

以下情况需特别关注：
- 收入增长为负
- 毛利率大幅下降
- 运营费用增长超过收入增长
- ROE/ROA 低于行业基准

## Common Mistakes

| 错误 | 正确做法 |
|-----|---------|
| 仅看绝对值忽视增长率 | 同时计算并分析增长率 |
| 混淆不同类型的利润率 | 区分 Gross/Operating/Net Margin |
| 忽略同比/环比对比 | 计算 YoY 和 QoQ 变化 |
