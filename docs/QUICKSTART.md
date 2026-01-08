# Claude Domain Skills Quick Start

> 3 分鐘開始使用 16 個領域技能

## 什麼是 Claude Domain Skills？

這是為 Claude Code 設計的**非技術領域**技能庫，涵蓋商業、創意、金融、生活和專業領域。

| 類別 | 技能數 | 範例 |
|------|--------|------|
| Business | 5 | marketing, sales, strategy, product-management |
| Creative | 5 | game-design, storytelling, ui-ux-design |
| Finance | 2 | investment-analysis, quant-trading |
| Lifestyle | 2 | personal-growth, side-income |
| Professional | 2 | research-analysis, knowledge-management |

---

## Step 1: 安裝完整技能庫 (1 分鐘)

### 方式 A: 在 Claude Code 中

```
安裝 claude-domain-skills 技能庫
```

### 方式 B: 使用 CLI

```bash
npx skillpkg-cli install miles990/claude-domain-skills
```

---

## Step 2: 安裝單一技能 (30 秒)

只需要特定技能？

```bash
# 安裝 marketing 技能
npx skillpkg-cli install github:miles990/claude-domain-skills#business/marketing

# 安裝 game-design 技能
npx skillpkg-cli install github:miles990/claude-domain-skills#creative/game-design

# 安裝 quant-trading 技能
npx skillpkg-cli install github:miles990/claude-domain-skills#finance/quant-trading
```

---

## Step 3: 使用技能 (1 分鐘)

安裝後，Claude 會自動套用相關知識。

### 範例對話

```
# 使用 marketing 技能
幫我規劃一個新產品的行銷策略

# 使用 game-design 技能
/evolve 設計一個 RPG 遊戲的經濟系統

# 使用 investment-analysis 技能
分析這間公司的財報，判斷是否值得投資

# 使用 storytelling 技能
幫我寫一個科幻短篇故事的大綱
```

---

## 技能目錄

### 商業 (Business)
`marketing` `sales` `strategy` `product-management` `project-management`

### 創意 (Creative)
`game-design` `storytelling` `brainstorming` `ui-ux-design` `visual-media`

### 金融 (Finance)
`investment-analysis` `quant-trading`

### 生活 (Lifestyle)
`personal-growth` `side-income`

### 專業 (Professional)
`research-analysis` `knowledge-management`

---

## 與軟體技能組合

Domain Skills 可以與 Software Skills 組合使用：

| 組合 | 效果 |
|------|------|
| `game-design` + `frontend` | 遊戲 UI 開發 |
| `quant-trading` + `python` + `database` | 量化交易系統 |
| `marketing` + `data-analysis` | 行銷數據分析 |
| `ui-ux-design` + `react-ecosystem` | 設計系統實作 |

---

## 常見問題

### Q: Domain Skills 和 Software Skills 有什麼不同？

**Software Skills** 專注於技術實作（如 Python, React, API Design）。
**Domain Skills** 專注於領域知識（如行銷策略、遊戲設計、投資分析）。

兩者可以組合使用，達到更好的效果。

### Q: 技能會自動載入嗎？

是的。Self-Evolving Agent 會根據任務描述自動識別並載入相關技能。

例如：任務「設計一個手遊的付費機制」會自動載入 `game-design` 技能。

### Q: 如何查看已載入的技能？

```bash
npx skillpkg-cli list
```

或在 Claude Code 中說：
```
列出已載入的技能
```

---

## 下一步

| 目標 | 指令 |
|------|------|
| 查看完整技能清單 | [README.md](../README.md) |
| 貢獻新技能 | [CONTRIBUTING.md](../CONTRIBUTING.md) |
| 安裝軟體技能 | `npx skillpkg-cli install miles990/claude-software-skills` |

---

## 成功！

```
✅ Domain Skills 已安裝
✅ Claude 可以使用領域知識
✅ 與 Software Skills 組合獲得更強能力

/evolve [你的目標]
```
