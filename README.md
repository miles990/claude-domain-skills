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
| **business/** | marketing, sales, product-management, project-management, strategy | 商業運營 |
| **finance/** | quant-trading, investment-analysis | 金融專業 |
| **creative/** | game-design, ui-ux-design, brainstorming | 創意創作 |
| **professional/** | research-analysis, knowledge-management | 專業服務 |
| **lifestyle/** | personal-growth, side-income | 生活領域 |

### 已實現的領域

| 領域 | 觸發詞範例 | 說明 |
|------|------------|------|
| `finance/quant-trading` | 量化, backtest, 策略 | 量化交易策略開發 |
| `finance/investment-analysis` | 財報, 投資, 估值 | 投資分析與估值 |
| `business/product-management` | PRD, OKR, 路線圖 | 產品管理 |
| `business/project-management` | Scrum, sprint, 甘特圖 | 專案管理 |
| `business/marketing` | 行銷, CAC, 漏斗 | 行銷策略 |
| `business/sales` | 銷售, 電商, CRM | 銷售與電商營運 |
| `creative/game-design` | 遊戲, 關卡, 平衡 | 遊戲設計 |
| `creative/ui-ux-design` | UI, UX, 無障礙 | 介面體驗設計 |
| `creative/brainstorming` | 靈感, 頭腦風暴, 創意 | 創意發想方法論 |
| `business/strategy` | 策略, 藍海, 差異化 | 商業策略與競爭優勢 |
| `professional/research-analysis` | 研究, 競品, 調研 | 研究分析方法論 |
| `lifestyle/personal-growth` | 人生規劃, 個人品牌, 時間管理 | 個人成長與職涯發展 |
| `lifestyle/side-income` | 副業, 被動收入, 投資, 加密貨幣 | 副業與財務自由 |
| `professional/knowledge-management` | 知識管理, 筆記, PKM | 個人知識系統 |

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

Triggers 讓 AI 能自動識別應該載入哪個領域 skill：

```yaml
# SKILL.md frontmatter (skillpkg 相容格式)
---
schema: "1.0"
name: quant-trading
triggers: [量化, 交易, 回測, 策略, 因子, quant, trading, backtest, strategy, factor]
keywords: [finance, trading, quantitative]
---
```

#### Triggers vs Keywords

| 欄位 | 用途 | 範例 |
|------|------|------|
| `triggers` | **任務匹配** - 用戶說什麼時觸發 | `[財報, 投資, 股票]` |
| `keywords` | **分類搜尋** - 按領域查找 | `[finance, business]` |

#### 最佳實踐

```yaml
triggers:
  # ✅ 包含中英文同義詞
  - 量化
  - quantitative
  - quant

  # ✅ 包含常見用語
  - 回測
  - backtest
  - 策略測試

  # ❌ 避免太通用的詞
  # - 分析 (太廣泛)
  # - 報告 (太廣泛)
```

## 創建新的領域 Skill

```bash
# 1. 創建目錄
mkdir -p finance/my-domain

# 2. 創建 SKILL.md
cat > finance/my-domain/SKILL.md << 'EOF'
---
schema: "1.0"
name: my-domain
version: "1.0.0"
description: 領域描述
triggers: [關鍵詞1, 關鍵詞2, keyword1, keyword2]
keywords: [category1, category2]
---

# 領域名稱

## 適用場景
- 場景 1
- 場景 2

## 核心知識
...

## 最佳實踐
...
EOF

# 3. 測試
skillpkg search "關鍵詞1"  # 應該能找到
```

## 貢獻指南

歡迎貢獻新的領域知識！請參考 [CONTRIBUTING.md](CONTRIBUTING.md)

## 相關專案

- [claude-software-skills](https://github.com/miles990/claude-software-skills) - 軟體開發 skills
- [self-evolving-agent](https://github.com/miles990/self-evolving-agent) - `/evolve` 自我進化 skill
- [claude-starter-kit](https://github.com/miles990/claude-starter-kit) - 一鍵配置 CLI
