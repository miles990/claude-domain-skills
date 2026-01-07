# Claude Domain Skills

> 非技術領域的專業知識 skills，讓 Claude 成為各領域專家

```
┌─────────────────────────────────────────────────────────────────┐
│                   Claude Domain Skills                          │
│                                                                 │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│   │   Business   │  │   Finance    │  │   Creative   │         │
│   │     商業     │  │     金融     │  │     創意     │         │
│   └──────────────┘  └──────────────┘  └──────────────┘         │
│                                                                 │
│   ┌──────────────┐  ┌──────────────┐                           │
│   │ Professional │  │  Lifestyle   │                           │
│   │   專業服務   │  │     生活     │                           │
│   └──────────────┘  └──────────────┘                           │
│                                                                 │
│              AI 自動識別任務 → 載入對應領域知識                 │
└─────────────────────────────────────────────────────────────────┘
```

## 領域分類

| 大類 | 子領域 | 說明 |
|------|--------|------|
| **business/** | marketing, planning, sales, management | 商業運營 |
| **finance/** | quant-trading, investment, risk-management | 金融專業 |
| **creative/** | design, writing, game-design, video | 創意創作 |
| **professional/** | legal, medical, education, consulting | 專業服務 |
| **lifestyle/** | sports, health, travel, food | 生活領域 |

## 安裝方式

### 使用 skillpkg（推薦）

```python
# 安裝特定領域
mcp__skillpkg__install_skill(
    source="github:miles990/claude-domain-skills#finance/quant-trading",
    scope="local"
)

# 安裝整個大類
mcp__skillpkg__install_skill(
    source="github:miles990/claude-domain-skills#finance",
    scope="local"
)
```

### 使用 claude-starter-kit

```bash
npx claude-starter-kit
# 選擇領域時會列出可用選項
```

## AI 自動選擇

搭配 `/evolve` skill 使用時，AI 會自動：

1. 分析任務關鍵詞
2. 搜尋匹配的領域 skills
3. 自動載入相關知識

```
用戶：「幫我分析這支股票的財報」
          ↓
/evolve 能力評估：偵測到「股票」「財報」
          ↓
自動載入：finance/investment-analysis
          ↓
執行任務（帶有金融領域知識）
```

## Skill 結構

每個 skill 包含：

```
finance/quant-trading/
├── SKILL.md          # 主要指令（含 triggers）
├── rules/            # 領域規則
│   └── trading.md
└── examples/         # 範例（可選）
```

### Triggers 機制

```yaml
# SKILL.md frontmatter (skillpkg 相容格式)
---
schema: "1.0"
name: quant-trading
triggers: [量化, 交易, 回測, 策略, 因子, quant, trading, backtest, strategy, factor]
keywords: [finance, trading, quantitative]
---
```

## 貢獻指南

歡迎貢獻新的領域知識！請參考 [CONTRIBUTING.md](CONTRIBUTING.md)

## 相關專案

- [claude-software-skills](https://github.com/miles990/claude-software-skills) - 軟體開發 skills
- [self-evolving-agent](https://github.com/miles990/self-evolving-agent) - `/evolve` 自我進化 skill
- [claude-starter-kit](https://github.com/miles990/claude-starter-kit) - 一鍵配置 CLI
