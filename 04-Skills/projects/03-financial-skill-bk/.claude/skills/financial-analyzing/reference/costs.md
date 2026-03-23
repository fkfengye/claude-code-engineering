# Costs Analysis (成本分析)

## Core Metrics

### Cost of Goods Sold (COGS) 销货成本

直接与产品/服务生产相关的成本。

### Cost Ratios (成本比率)

```
COGS Ratio = COGS / Revenue × 100%
```

**判断标准：**
- < 30%: 优秀（高毛利）
- 30-50%: 良好
- 50-70%: 一般
- > 70%: 成本过高

### Operating Expenses (OpEx) 运营费用

包括：
- 销售与市场营销费用
- 研发费用
- 管理费用

```
OpEx Ratio = Operating Expenses / Revenue × 100%
```

### Cost Growth vs Revenue Growth (成本增长 vs 收入增长)

```
成本收入弹性 = COGS 增长率 / Revenue 增长率
```

- 弹性 < 1: 规模效应，成本控制良好
- 弹性 > 1: 成本增长快于收入，需关注

## Anomaly Detection 异常信号

| 信号 | 阈值 | 说明 |
|-----|------|------|
| COGS Ratio 上升 | 连续2季上升 > 5% | 原材料涨价或生产效率下降 |
| OpEx 增长过快 | OpEx 增长 > Revenue 增长 × 1.5 | 运营效率降低 |
| 营销费用 ROI 下降 | 获客成本上升 > 20% | 获客效率降低 |

## Cost Structure Analysis (成本结构分析)

```
固定成本占比 = 固定成本 / 总成本 × 100%
变动成本占比 = 变动成本 / 总成本 × 100%
```

**判断：**
- 固定成本占比高 → 规模效应强，但经营杠杆高
- 变动成本占比高 → 灵活性强，但毛利率可能较低

## Industry Benchmarks (行业基准参考)

| 行业 | COGS Ratio 基准 |
|-----|----------------|
| SaaS | 10-20% |
| 电商 | 60-80% |
| 制造业 | 50-70% |
| 专业服务 | 30-40% |

## Quick Calculation

对于 TechVision AI 示例数据:

```python
cogs_ratio = 4037000 / 13700000 * 100  # = 29.47%
opex_ratio = 5700000 / 13700000 * 100   # = 41.61%
```
