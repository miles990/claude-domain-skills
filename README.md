# Claude Domain Skills

> 非技術領域的專業知識 skills，讓 Claude 成為各領域專家

[![Skills](https://img.shields.io/badge/skills-24-blue)](./README.md)
[![Categories](https://img.shields.io/badge/categories-6-green)](./README.md)
[![Plugin](https://img.shields.io/badge/Claude_Code-Plugin-orange)](https://code.claude.com/docs/en/discover-plugins)

```
┌─────────────────────────────────────────────────────────────────┐
│                   Claude Domain Skills                          │
│                                                                 │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│   │   Business   │  │   Finance    │  │   Creative   │         │
│   │     商業     │  │     金融     │  │     創意     │         │
│   └──────────────┘  └──────────────┘  └──────────────┘         │
│                                                                 │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│   │ Professional │  │  Lifestyle   │  │  Methodology │         │
│   │   專業服務   │  │     生活     │  │     方法論   │         │
│   └──────────────┘  └──────────────┘  └──────────────┘         │
│                                                                 │
│              AI 自動識別任務 → 載入對應領域知識                 │
└─────────────────────────────────────────────────────────────────┘
```

## 領域分類

| 大類 | 子領域 | 說明 |
|------|--------|------|
| **business/** | marketing, sales, product-management, project-management, strategy | 商業運營 |
| **finance/** | quant-trading, investment-analysis, strategy-optimization | 金融專業 |
| **creative/** | game-design, game-planner, galgame-master, deckbuilder-roguelike, ui-ux-design, brainstorming, storytelling, visual-media | 創意創作 |
| **professional/** | research-analysis, knowledge-management | 專業服務 |
| **lifestyle/** | personal-growth, side-income | 生活領域 |
| **methodology/** | knowledge-acquisition-4c, tech-spec-gen, skill-optimizer, consistency-checker | 開發方法論 |

### 已實現的領域

| 領域 | 觸發詞範例 | 說明 |
|------|------------|------|
| `finance/quant-trading` | 量化, backtest, 策略 | 量化交易策略開發 |
| `finance/investment-analysis` | 財報, 投資, 估值 | 投資分析與估值 |
| `finance/strategy-optimization` | 策略優化, 提高勝率, 調參 | 交易策略優化方法論 |
| `business/product-management` | PRD, OKR, 路線圖 | 產品管理 |
| `business/project-management` | Scrum, sprint, 甘特圖 | 專案管理 |
| `business/marketing` | 行銷, CAC, 漏斗 | 行銷策略 |
| `business/sales` | 銷售, 電商, CRM | 銷售與電商營運 |
| `creative/game-design` | 遊戲, 關卡, 平衡 | 遊戲設計 |
| `creative/game-planner` | GDD, 遊戲企劃, 設計支柱 | 遊戲企劃文件 |
| `creative/galgame-master` | galgame, 美少女遊戲, 視覺小說, 攻略對象 | Galgame 創作 |
| `creative/deckbuilder-roguelike` | Slay the Spire, 卡牌構築, deckbuilder, roguelike | 類 StS 卡牌 Roguelike 設計 |
| `creative/ui-ux-design` | UI, UX, 無障礙 | 介面體驗設計 |
| `creative/brainstorming` | 靈感, 頭腦風暴, 創意 | 創意發想方法論 |
| `creative/storytelling` | 小說, 漫畫, 劇本, 角色 | 故事創作與敘事 |
| `creative/visual-media` | 攝影, 影片, 動畫, 電影 | 影像創作與製作 |
| `business/strategy` | 策略, 藍海, 差異化 | 商業策略與競爭優勢 |
| `professional/research-analysis` | 研究, 競品, 調研 | 研究分析方法論 |
| `lifestyle/personal-growth` | 人生規劃, 個人品牌, 時間管理 | 個人成長與職涯發展 |
| `lifestyle/side-income` | 副業, 被動收入, 投資, 加密貨幣 | 副業與財務自由 |
| `professional/knowledge-management` | 知識管理, 筆記, PKM | 個人知識系統 |
| `methodology/knowledge-acquisition-4c` | 學習, 研究, 進入新領域, 知識習得 | 系統化學習方法論 (4C) |
| `methodology/tech-spec-gen` | tech-spec, 技術規格, 設計轉規格, PRD, GDD | 設計文件 → 技術規格轉換 |
| `methodology/skill-optimizer` | skill 優化, 減少 token, skill 瘦身 | Skill 優化與 token 效率 |
| `methodology/consistency-checker` | check, 一致性, 檢查, sync, 同步 | 內容一致性檢查器 |

## 安裝方式

### 使用 Plugin Marketplace（推薦）

```bash
# 1. 添加 marketplace（GitHub 格式：owner/repo）
/plugin marketplace add miles990/claude-domain-skills

# 2. 開啟 plugin 管理介面，在 Discover 頁籤查看可用 plugins
/plugin

# 3. 安裝特定 skill（選擇你需要的）
/plugin install marketing@claude-domain-skills
/plugin install quant-trading@claude-domain-skills
/plugin install game-design@claude-domain-skills

# 或在對話中提及 skill 名稱，Claude 會自動載入
```

**支援的 GitHub 格式：**
```bash
# 短格式（推薦）
/plugin marketplace add miles990/claude-domain-skills

# HTTPS URL
/plugin marketplace add https://github.com/miles990/claude-domain-skills.git

# 指定分支或標籤
/plugin marketplace add miles990/claude-domain-skills#main
```

**Plugin 指令：**
| 指令 | 說明 |
|------|------|
| `/plugin` | 開啟互動式 plugin 管理介面 |
| `/plugin install <name>@<marketplace>` | 安裝特定 plugin |
| `/plugin disable <name>@<marketplace>` | 暫時停用 plugin |
| `/plugin uninstall <name>@<marketplace>` | 完全移除 plugin |

### 可用 Plugins（24 個）

#### Business（商業運營）
| Plugin | 說明 |
|--------|------|
| `marketing` | 行銷策略與數位行銷 |
| `product-management` | 產品管理與 PRD |
| `project-management` | 專案管理與 Scrum |
| `sales` | 銷售與電商營運 |
| `strategy` | 商業策略與競爭優勢 |

#### Finance（金融專業）
| Plugin | 說明 |
|--------|------|
| `quant-trading` | 量化交易策略開發 |
| `investment-analysis` | 投資分析與估值 |
| `strategy-optimization` | 交易策略優化 |

#### Creative（創意創作）
| Plugin | 說明 |
|--------|------|
| `game-design` | 遊戲設計與關卡平衡 |
| `game-planner` | 遊戲企劃 GDD 文件 |
| `galgame-master` | Galgame 視覺小說創作 |
| `deckbuilder-roguelike` | 類 StS 卡牌 Roguelike 設計 |
| `ui-ux-design` | UI/UX 介面體驗設計 |
| `brainstorming` | 創意發想方法論 |
| `storytelling` | 故事創作與敘事 |
| `visual-media` | 影像創作與製作 |

#### Professional（專業服務）
| Plugin | 說明 |
|--------|------|
| `research-analysis` | 研究分析方法論 |
| `knowledge-management` | 個人知識管理系統 |

#### Lifestyle（生活領域）
| Plugin | 說明 |
|--------|------|
| `personal-growth` | 個人成長與職涯發展 |
| `side-income` | 副業與財務自由 |

#### Methodology（方法論）
| Plugin | 說明 |
|--------|------|
| `knowledge-acquisition-4c` | 系統化學習方法論 4C |
| `tech-spec-gen` | 設計文件轉技術規格 |
| `skill-optimizer` | Skill 優化與 token 效率 |
| `consistency-checker` | 內容一致性檢查器 |

### 其他安裝方式

#### Clone 到 Skills 目錄

```bash
# Clone 到你的 skills 目錄
git clone https://github.com/miles990/claude-domain-skills.git ~/.claude/skills/domain-skills
```

Claude 會在需要時自動發現並使用相關的 skills。

#### 使用 claude-starter-kit

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

### Skill 強化功能

每個領域 skill 可以包含以下強化功能：

| 功能 | 說明 | 用途 |
|------|------|------|
| **Sharp Edges** | 領域常見陷阱警告 | 主動提醒用戶避開常見錯誤 |
| **Validations** | 品質檢查規則 | 自動驗證輸出符合領域標準 |
| **Collaboration** | 跨領域協作定義 | 智能委派和上下文傳遞 |

```yaml
# SKILL.md frontmatter 範例
---
schema: "1.0"
name: quant-trading
collaboration:
  prerequisites:
    - skill: python
      reason: 量化開發基礎
  delegation_triggers:
    - trigger: 資料庫設計
      delegate_to: database
---

# Sharp Edges
- id: backtest-overfitting
  severity: critical
  situation: 策略回測看起來收益驚人
  solution: 使用 Walk-forward 驗證和樣本外測試
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

# 3. 添加到 marketplace.json（讓它成為可安裝的 plugin）
# 在 .claude-plugin/marketplace.json 的 plugins 陣列中添加：
{
  "name": "my-domain",
  "description": "領域描述",
  "source": "./finance/my-domain",
  "version": "1.0.0",
  "strict": true
}

# 4. 測試
# 在 Claude Code 對話中提及關鍵詞，應該能自動載入
```

## 貢獻指南

歡迎貢獻新的領域知識！請參考 [CONTRIBUTING.md](CONTRIBUTING.md)

## 快速參考

```
┌─────────────────────────────────────────────────────────────────┐
│  Quick Reference - 24 Domain Skills                             │
├─────────────────────────────────────────────────────────────────┤
│  💼 Business (5)                                                │
│     marketing | sales | product-management                      │
│     project-management | strategy                               │
├─────────────────────────────────────────────────────────────────┤
│  💰 Finance (3)                                                 │
│     quant-trading | investment-analysis | strategy-optimization │
├─────────────────────────────────────────────────────────────────┤
│  🎨 Creative (8)                                                │
│     game-design | game-planner | galgame-master                 │
│     deckbuilder-roguelike | ui-ux-design | brainstorming        │
│     storytelling | visual-media                                 │
├─────────────────────────────────────────────────────────────────┤
│  🔬 Professional (2)                                            │
│     research-analysis | knowledge-management                    │
├─────────────────────────────────────────────────────────────────┤
│  🌱 Lifestyle (2)                                               │
│     personal-growth | side-income                               │
├─────────────────────────────────────────────────────────────────┤
│  🔧 Methodology (4)                                             │
│     knowledge-acquisition-4c | tech-spec-gen | skill-optimizer  │
│     consistency-checker                                         │
└─────────────────────────────────────────────────────────────────┘
```

## 目錄結構

```
claude-domain-skills/
├── .claude-plugin/          # Plugin 設定
│   └── marketplace.json     # 列出所有 24 個 skills 作為獨立 plugins
├── business/                # 商業運營（5 skills）
├── finance/                 # 金融專業（3 skills）
├── creative/                # 創意創作（8 skills）
├── professional/            # 專業服務（2 skills）
├── lifestyle/               # 生活領域（2 skills）
├── methodology/             # 方法論（4 skills）
├── interfaces/              # 介面定義
├── docs/                    # 文件
├── SKILL-TEMPLATE.md        # Skill 建立模板
├── CONTRIBUTING.md          # 貢獻指南
├── README.md
└── LICENSE
```

## 相關專案

- [claude-software-skills](https://github.com/miles990/claude-software-skills) - 軟體開發 skills
- [self-evolving-agent](https://github.com/miles990/self-evolving-agent) - `/evolve` 自我進化 skill
- [claude-starter-kit](https://github.com/miles990/claude-starter-kit) - 一鍵配置 CLI

## License

MIT
