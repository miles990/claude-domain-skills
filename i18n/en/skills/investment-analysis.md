---
schema: "1.0"
name: investment-analysis
version: "1.0.0"
language: en
original: zh-TW
description: Stock analysis, financial statement interpretation, and investment decision-making
triggers: [stock, financial report, investment, valuation, fundamental, technical, PE, ROE, financial-report]
keywords: [finance, investment, analysis, stock]
author: claude-domain-skills
---

# Investment Analysis

> Data-driven investment decision support

## Use Cases

- Reading and analyzing financial statements
- Company valuation calculations
- Investment portfolio evaluation
- Industry comparison analysis

## Analysis Framework

```
┌─────────────────────────────────────────────────────────────────┐
│  Investment Analysis Process                                     │
│                                                                 │
│  1. Industry → 2. Company → 3. Valuation → 4. Risk Assessment  │
│     Analysis     Analysis      Analysis                         │
│                                                                 │
│  Macro          Competitive   Intrinsic    Margin of           │
│  Environment    Advantage     Value        Safety               │
│  Industry       Financial     Relative     Investment           │
│  Trends         Health        Valuation    Decision             │
└─────────────────────────────────────────────────────────────────┘
```

## Core Metrics

### Profitability

| Metric | Formula | Good Standard |
|--------|---------|---------------|
| **ROE** | Net Income / Equity | > 15% |
| **ROA** | Net Income / Total Assets | > 8% |
| **Gross Margin** | Gross Profit / Revenue | Above industry avg |
| **Net Margin** | Net Income / Revenue | Above industry avg |

### Valuation Metrics

| Metric | Formula | Description |
|--------|---------|-------------|
| **P/E** | Price / EPS | Price-to-Earnings, lower = cheaper |
| **P/B** | Price / Book Value | Price-to-Book ratio |
| **PEG** | P/E / Earnings Growth | < 1 may be undervalued |
| **EV/EBITDA** | Enterprise Value / EBITDA | Valuation considering debt |

## Financial Statements

```
Income Statement     Balance Sheet        Cash Flow Statement
────────────────     ─────────────        ───────────────────
Revenue              Assets               Operating Cash Flow
- Cost               = Liabilities        Investing Cash Flow
= Gross Profit       + Equity             Financing Cash Flow
- Expenses                                ───────────────────
= Net Income                              Net Cash Flow
```

## Best Practices

1. **Look at Long-term Trends** - At least 5 years of data
2. **Peer Comparison** - Compare metrics with competitors
3. **Qualitative Analysis** - Understand the business model
4. **Margin of Safety** - Conservative valuation, leave room
5. **Diversification** - Don't put all eggs in one basket

## Common Mistakes

| Mistake | Correct Approach |
|---------|-----------------|
| ❌ Buy just because P/E is low | ✅ Use multiple metrics |
| ❌ Chase hot stocks | ✅ Independent fundamental analysis |
| ❌ Ignore cash flow | ✅ Cash flow > Earnings |
| ❌ Panic on short-term volatility | ✅ Focus on long-term value |

## DCF Valuation Model

```
┌─────────────────────────────────────────────────────────────────┐
│  DCF (Discounted Cash Flow)                                      │
│                                                                 │
│  Intrinsic Value = Σ (Future CF / (1 + r)^n) + Terminal Value   │
│                                                                 │
│  Steps:                                                         │
│  1. Forecast 5-10 years Free Cash Flow (FCF)                    │
│  2. Calculate Terminal Value                                     │
│  3. Choose appropriate discount rate (WACC)                      │
│  4. Discount to present value                                    │
│  5. Divide by shares = Intrinsic value per share                │
└─────────────────────────────────────────────────────────────────┘
```

### Free Cash Flow Calculation

```
Free Cash Flow (FCF) = Operating Cash Flow - CapEx

       = EBIT × (1 - Tax Rate)
         + Depreciation & Amortization
         - Capital Expenditure
         - Change in Working Capital
```

## DuPont Analysis

```
┌─────────────────────────────────────────────────────────────────┐
│  DuPont Analysis: Breaking Down ROE into 3 Drivers              │
│                                                                 │
│  ROE = Net Margin × Asset Turnover × Financial Leverage         │
│                                                                 │
│      Net Income     Revenue       Total Assets                  │
│  = ─────────── × ─────────── × ───────────────                 │
│      Revenue      Total Assets     Equity                       │
│                                                                 │
│  ┌────────────┬────────────┬────────────┐                      │
│  │ Profitability │ Efficiency │ Leverage │                      │
│  │  Net Margin   │  Turnover  │ Multiplier│                     │
│  └────────────┴────────────┴────────────┘                      │
│                                                                 │
│  Analysis Focus:                                                │
│  • Which factor contributes most?                               │
│  • Is high ROE from profits or leverage?                        │
│  • What's causing trend changes?                                │
└─────────────────────────────────────────────────────────────────┘
```

## Moat Analysis

```markdown
## Five Types of Economic Moats

| Type | Description | Examples |
|------|-------------|----------|
| **Brand** | Consumers pay premium | Coca-Cola, Hermès |
| **Switching Costs** | High cost to switch | SAP, Adobe |
| **Network Effects** | More users = more value | Facebook, Visa |
| **Cost Advantage** | Low-cost production | Walmart, TSMC |
| **Intangible Assets** | Patents, licenses | Pfizer, Franchises |

## Moat Evaluation

Wide & Durable → Strong Buy
Wide but Threatened → Evaluate Carefully
Narrow → Short-term Opportunity
No Moat → Pure Price Competition
```

## Investment Checklist

```markdown
## Pre-Investment Checklist

### Business Model
- [ ] Understand how company makes money
- [ ] What is the competitive advantage (moat)
- [ ] Industry outlook

### Financial Health
- [ ] ROE > 15% for 5+ consecutive years
- [ ] Positive operating cash flow
- [ ] Reasonable debt ratio (< 60%)
- [ ] Consistent dividend payments

### Valuation
- [ ] P/E below historical average
- [ ] PEG < 1 or close to 1
- [ ] DCF shows margin of safety

### Risk Assessment
- [ ] Understand key risk factors
- [ ] Set stop-loss points
- [ ] Investment amount within acceptable loss
```

## Portfolio Management

```
┌─────────────────────────────────────────────────────────────────┐
│  Risk Tolerance vs Asset Allocation                              │
│                                                                 │
│  Conservative: Stocks 30% | Bonds 50% | Cash 20%               │
│  Balanced:     Stocks 50% | Bonds 35% | Cash 15%               │
│  Aggressive:   Stocks 70% | Bonds 20% | Cash 10%               │
│                                                                 │
│  Principles:                                                     │
│  • Age Rule: Bond % = 100 - Age                                 │
│  • Diversify: Single holding < 10%                              │
│  • Rebalance: Review annually                                   │
└─────────────────────────────────────────────────────────────────┘
```

## Behavioral Finance Traps

| Bias | Description | Solution |
|------|-------------|----------|
| **Anchoring** | Stuck on purchase price | Re-evaluate intrinsic value |
| **Confirmation** | Only see supporting info | Actively seek contrary views |
| **Herd Mentality** | Follow the crowd | Independent analysis |
| **Loss Aversion** | Hate losses more than love gains | Set and execute stop-loss |
| **Overconfidence** | Overestimate own judgment | Record and review decisions |
| **Recency Bias** | Overweight recent events | Look at long-term data |

## Recommended Tools

- **Financial Data**: Yahoo Finance, Simply Wall St, SEC EDGAR
- **Valuation**: Excel DCF templates, Finviz
- **Research**: Seeking Alpha, Morningstar
- **Tracking**: TradingView, Portfolio Tracker

## Disclaimer

```
⚠️ This content is for educational purposes only and does not
   constitute investment advice. Investing involves risk.
   Please consult a professional advisor before making decisions.
```
