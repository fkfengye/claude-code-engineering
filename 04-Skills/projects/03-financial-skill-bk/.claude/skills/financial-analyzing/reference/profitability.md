# Profitability Analysis (盈利分析)

## Margin Metrics (利润率指标)

### Gross Margin (毛利率)

```
Gross Margin = (Revenue - COGS) / Revenue × 100%
```

**判断标准：**
- > 60%: 优秀
- 40-60%: 良好
- 20-40%: 一般
- < 20%: 较低

### Operating Margin (营业利润率)

```
Operating Margin = (Revenue - COGS - Operating Expenses) / Revenue × 100%
```

**判断标准：**
- > 30%: 优秀
- 15-30%: 良好
- 5-15%: 一般
- < 5%: 微利或亏损

### Net Margin (净利率)

```
Net Margin = Net Income / Revenue × 100%
```

**判断标准：**
- > 20%: 优秀
- 10-20%: 良好
- 5-10%: 一般
- < 5%: 微利

## Return Metrics (回报率指标)

### ROA (Return on Assets) 资产回报率

```
ROA = Net Income / Total Assets × 100%
```

**判断标准：**
- > 15%: 优秀
- 8-15%: 良好
- 3-8%: 一般
- < 3%: 较低

### ROE (Return on Equity) 股东权益回报率

```
ROE = Net Income / Shareholders' Equity × 100%
```

**判断标准：**
- > 25%: 优秀
- 15-25%: 良好
- 8-15%: 一般
- < 8%: 较低

### ROI (Return on Investment) 投资回报率

```
ROI = (投资收益 - 投资成本) / 投资成本 × 100%
```

## DuPont Analysis (杜邦分析)

```
ROE = Net Margin × Asset Turnover × Equity Multiplier
    = (Net Income / Revenue) × (Revenue / Total Assets) × (Total Assets / Equity)
```

分解各因素影响：
- 净利率：盈利能力
- 资产周转率：运营效率
- 权益乘数：财务杠杆

## Industry Benchmarks (行业基准参考)

| 指标 | SaaS | 电商 | 制造业 |
|-----|------|------|--------|
| Gross Margin | 70-80% | 20-30% | 30-40% |
| Operating Margin | 15-25% | 5-10% | 8-15% |
| Net Margin | 10-20% | 2-5% | 5-10% |
| ROA | 10-15% | 5-10% | 6-12% |
| ROE | 15-30% | 10-20% | 12-20% |

## Anomaly Detection 异常信号

| 信号 | 阈值 | 说明 |
|-----|------|------|
| 毛利率持续下降 | 连续2季下降 > 5% | 定价压力或成本上升 |
| 营业利润率低于 OpEx 增长率 | OpEx 增长 > 收入增长 | 费用失控 |
| ROE 大幅波动 | YoY 变化 > 30% | 可能是财务杠杆变化或非经常性损益 |

## Quick Calculation

对于 TechVision AI 示例数据:

```python
gross_margin = (13700000 - 4037000) / 13700000 * 100   # = 70.53%
operating_margin = (13700000 - 4037000 - 5700000) / 13700000 * 100  # = 28.93%
net_margin = 2680000 / 13700000 * 100                    # = 19.56%
roa = 2680000 / 11500000 * 100                           # = 23.30%
roe = 2680000 / 6200000 * 100                            # = 43.23%
```
