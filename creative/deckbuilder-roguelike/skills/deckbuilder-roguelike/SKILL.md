---
schema: "1.0"
name: deckbuilder-roguelike
version: "1.0.0"
description: 類 Slay the Spire 的卡牌構築 Roguelike 遊戲設計框架
domain: creative
triggers:
  keywords:
    primary: [deckbuilder, 卡牌構築, Slay the Spire, roguelike deckbuilding, 卡牌戰鬥, 回合制卡牌]
    secondary: [能量系統, energy system, 遺物, relic, 卡池, card pool, 卡牌平衡, synergy]
  context_boost: [卡牌, card, 戰鬥, combat, 回合, turn, 抽牌, draw]
  context_penalty: [TCG, 集換式, 實體卡牌, physical card]
  priority: high
dependencies:
  domain-skills: [game-design, game-planner]
author: claude-domain-skills
---

# 卡牌構築 Roguelike 設計 (Deckbuilder Roguelike)

> 類 Slay the Spire 的單人卡牌構築 Roguelike 遊戲設計框架

## 適用場景

- 設計類 Slay the Spire 的卡牌戰鬥系統
- 卡牌數值平衡與效果設計
- 能量/資源系統設計
- 遺物與卡牌協同效應設計

## 快速指令

```
/deckbuilder card [名稱]      # 設計單張卡牌
/deckbuilder character [名稱] # 設計角色卡池
/deckbuilder relic [稀有度]   # 設計遺物
/deckbuilder balance [列表]   # 數值平衡檢查
```

---

## 核心系統架構

### Deckbuilder Roguelike 核心公式

```
能量系統 + 卡牌構築 + Roguelike = 決策張力 + Build多樣性 + 重玩價值
  └ 遺物系統 + 敵人意圖 → Synergy深度 + 戰術規劃
```

**為什麼成功：**
| 元素 | 作用 | 設計目標 |
|------|------|----------|
| 能量限制 | 強迫取捨 | 每張牌都是決策 |
| 隨機獎勵 | 被動構築 | 無法預設最佳策略 |
| 敵人意圖 | 資訊博弈 | 有意義的防禦選擇 |
| 遺物系統 | 永久改變 | 每局都不同體驗 |
| 卡組精簡 | 稀釋懲罰 | 少即是多 |

---

## 1. 能量系統

**基礎：** 每回合 3 能量，可透過遺物/卡牌增加

**能量成本分布：**
- 0費 (10-15%): 輔助/條件觸發
- 1費 (40-50%): 主力/基礎效果
- 2費 (25-30%): 強力/複合效果
- 3費 (10-15%): 終結技/大招
- X費 (5%): 可變/傾倒資源

**能量操控設計：**
| 類型 | 效果模板 | 設計考量 |
|------|----------|----------|
| 能量生成 | 獲得 X 能量 | 高價值，需平衡 |
| 成本降低 | 下一張牌 -X 費 | 組合潛力 |
| X 費牌 | 消耗所有能量 | 回合結算器 |

---

## 2. 卡牌類型

### 五大類型

- **攻擊牌 (Attack):** 造成傷害，可附帶 Debuff
- **技能牌 (Skill):** 格擋、抽牌、Buff/Debuff、卡組操作
- **能力牌 (Power):** 永久效果，打出後不進棄牌堆
- **狀態牌 (Status):** 負面效果，戰鬥後移除
- **詛咒牌 (Curse):** 永久負面，需特殊方式移除

### 稀有度

| 稀有度 | 出現率 | 特徵 |
|--------|--------|------|
| 基礎 | 起始牌 | 簡單直接 |
| 普通 | 60% | 構築基石 |
| 罕見 | 37% | 策略定義 |
| 稀有 | 3%* | Build核心 |

> *稀有保底：每抽普通牌，稀有率 +1%

### 關鍵詞速查

```
Exhaust: 使用後移除    Ethereal: 回合結束消耗
Innate: 必在起始手牌   Retain: 不棄牌保留
Block: 格擋(回合結束消失)
Vulnerable: 受傷+50%   Weak: 傷害-25%   Frail: 格擋-25%
Strength: 攻擊+X       Dexterity: 格擋+X
```

---

## 3. 回合結構

```
回合開始 → 獲能量(3) + 抽牌(5) + 格擋歸零
    ↓
玩家行動 → 打牌/使用藥水/結束回合
    ↓
回合結束 → 觸發效果 + 棄牌(Ethereal消耗) + 能量清零
    ↓
敵人行動 → 依意圖執行 + 決定下回合意圖
```

### 敵人意圖類型

- **攻擊:** 顯示傷害數值
- **防禦:** 獲得格擋
- **增益/減益:** Buff自己或Debuff玩家
- **未知:** 不顯示(精英/Boss)

---

## 4. 遺物系統

### 設計哲學

> 「遺物應該改變你的決策，而不只是加數值」

**好的遺物設計：**
- 改變策略優先級
- 創造新的 Synergy
- 定義 Build 方向

**避免：**
- 純數值加成（無感）
- 過於複雜（難評估）
- 無條件強力（必選，無趣）

### 稀有度來源

| 稀有度 | 來源 | 設計目標 |
|--------|------|----------|
| 起始 | 角色自帶 | 定義風格 |
| 普通 | 精英/商店 | 通用增益 |
| 罕見 | 精英/商店 | Build定義 |
| 稀有/Boss | Boss | 遊戲改變者 |

---

## 5. Build 與 Synergy

### 常見 Build 原型

| Build | 核心 | Synergy |
|-------|------|---------|
| 力量流 | 累積力量Buff | 力量 + 多段攻擊 |
| 格擋流 | 超量格擋/保留 | Barricade + 疊格擋 |
| 消耗流 | 消耗觸發效果 | 每消耗 +X 效果 |
| 抽牌流 | 大量抽牌/小卡組 | 薄卡組 + 無限循環 |
| 毒/DOT流 | 累積持續傷害 | 毒加倍 + 存活 |

### Synergy 設計原則

- 每個 Build 需要 2-3 張「核心構築」牌
- 「安全選擇」牌維持基礎可玩性
- 「高風險高回報」牌創造刺激感

---

## 6. 數值基準線

**1 能量 ≈**
- 6-8 傷害 / 5-6 格擋
- 1 張抽牌 / 1 能量生成
- 輕度 Debuff (1回合)

**關鍵詞價值：**
- Exhaust = -0.5 能量
- Ethereal = -0.3 能量
- Innate = +0.3 能量
- Retain = +0.2 能量
- 升級 = +0.5~1.0 能量

> 詳細數值表見 `extended/balance-tables.md`

---

## 7. 地圖與進度

### 節點類型

- **普通戰鬥:** 獲得卡牌獎勵
- **精英戰鬥:** 獲得遺物 + 卡牌
- **未知事件:** 隨機事件
- **商店:** 購買/移除卡牌
- **休息:** 治療 or 升級卡牌
- **Boss:** 擊敗進入下一章

### 三幕結構

| Act | 敵人HP | 敵人傷害 | 目標 |
|-----|--------|----------|------|
| 1 | 30-50 | 8-15 | Build雛形 |
| 2 | 50-100 | 15-25 | 完善Synergy |
| 3 | 100-200 | 25-40 | 證明Build |

---

## 8. Sharp Edges

### SE-1: 卡組膨脹

**問題:** 拿太多牌 → 關鍵牌抽不到

**解決:**
- 設計卡組上限或懲罰
- 提供移除卡牌機會
- 教育「不拿也是選擇」

### SE-2: 必選牌/遺物

**問題:** 過強選項 → 無腦必選 → 減少多樣性

**解決:**
- 所有選項都有 Trade-off
- 強力牌需要 Build 配合
- 選擇率 >80% 需要 Nerf

### SE-3: 防禦無聊

**問題:** 玩家覺得打格擋牌無聊

**解決:**
- 防禦牌也要有爽感
- 設計反擊/格擋轉攻擊
- 過量格擋的獎勵

### SE-4: 運氣 vs 技術

**問題:** 玩家抱怨「運氣決定勝負」

**解決:**
- 保證基礎可玩性
- 提供「選擇」而非純隨機
- 稀有卡保底機制
- 多種 Build 路線可選

---

## 9. 平衡追蹤

### 關鍵指標

| 指標 | 警戒值 | 動作 |
|------|--------|------|
| 選擇率 > 80% | 過強 | Nerf |
| 選擇率 < 5% | 過弱/定位不明 | Buff/重設計 |
| 勝率差異 > 10% | 需調整 | 分析原因 |

### 調整原則

1. 修復 Bug/非預期互動 — 最高優先
2. 削弱「必選」牌/遺物 — 高優先
3. 加強「從不選」的選項 — 中優先
4. 微調數值 — 低優先

---

## 延伸資料

- `extended/templates.md` — 卡牌/遺物/角色/敵人設計模板
- `extended/examples.md` — Build範例/成功案例分析
- `extended/balance-tables.md` — 詳細數值平衡表

## 相關資源

- [Slay the Spire Wiki](https://slaythespire.wiki.gg/)
- [How StS devs use data](https://www.gamedeveloper.com/design/how-i-slay-the-spire-i-s-devs-use-data-to-balance-their-roguelike-deck-builder)

## 相關領域

- [[game-design]] — 通用遊戲設計理論
- [[game-planner]] — GDD 撰寫
