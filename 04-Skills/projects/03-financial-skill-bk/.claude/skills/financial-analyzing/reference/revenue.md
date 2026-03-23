# 收入分析

## 核心指标

### Revenue Growth Rate (收入增长率)

```
Revenue Growth = (Current Revenue - Previous Revenue) / Previous Revenue × 100%
```

**判断标准：**
- > 20%: 高速增长
- 10-20%: 稳健增长
- 0-10%: 低速增长
- < 0%: 负增长，需警惕

### Year-over-Year (YoY) 同比增长率

```
YoY Growth = (Current Period Revenue - Same Period Last Year Revenue) / Same Period Last Year Revenue × 100%
```

### Quarter-over-Quarter (QoQ) 环比增长率

```
QoQ Growth = (Current Quarter Revenue - Previous Quarter Revenue) / Previous Quarter Revenue × 100%
```

### ARPU (Average Revenue Per User) 每用户平均收入

```
ARPU = Total Revenue / Number of Users
```

### New Customer Revenue (新客户收入)

监控新客户获取对增长的贡献比例。

## 异常信号检测

| 信号 | 阈值 | 说明 |
|-----|------|------|
| 收入环比下降 | QoQ < -5% | 可能是季节性或需求问题 |
| YoY 增长放缓 | 连续2季 YoY 下降 > 10% | 增长动能减弱 |
| ARPU 下降 | ARPU 下降 > 5% | 可能定价策略问题或客户结构变化 |

## Industry Benchmarks (行业基准参考)

| 行业 | 收入增长基准 |
|-----|------------|
| SaaS | 20-30% |
| 电商 | 15-25% |
| 制造业 | 5-15% |
| 传统服务 | 3-8% |

## Quick Calculation

对于 sample_financials.json 中的 TechVision AI:

```python
revenue_growth = (13700000 - 10200000) / 10200000 * 100  # = 34.31%
```
