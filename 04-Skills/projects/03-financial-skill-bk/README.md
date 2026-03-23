# 财务分析技能

一个用于财务分析的分层展示技能，展示了三层架构。

## 结构

```
03-financial-skill/
├── SKILL.md                    # 主技能文件（始终加载）
├── reference/
│   ├── revenue.md             # 收入分析公式
│   ├── costs.md               # 成本分析公式
│   └── profitability.md       # 盈利能力指标
├── templates/
│   └── analysis_report.md     # 报告模板
└── scripts/
    └── calculate_ratios.py    # 计算脚本
```

## 渐进式加载

| 用户请求 | 加载的文件 | Token 数量 |
|--------------|--------------|--------|
| "什么是毛利率？" | SKILL.md + profitability.md | ~1500 |
| "分析收入增长" | SKILL.md + revenue.md | ~1400 |
| "完整财务分析" | 所有文件 | ~4000 |

## 使用场景

当用户询问以下内容时触发此技能：
- 收入、销售、增长率
- 成本、费用、效率
- 利润、利润率、投资回报率
- 财务分析或报告

## 脚本使用

```bash
# 创建数据文件
echo '{"revenue": 1000000, "cogs": 400000, "net_income": 150000}' > data.json

# 运行计算
python scripts/calculate_ratios.py data.json
```
