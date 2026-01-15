# Game Design Examples

## growth-curve-formulas

### 常用成長公式

| 類型 | 公式 | 適用 |
|------|------|------|
| 線性 | `value = base + (level x growth)` | 簡單遞增 |
| 指數 | `value = base x (multiplier ^ level)` | 升級經驗 |
| 對數 | `value = base x log(level + offset)` | 玩家屬性 |
| S曲線 | `value = max / (1 + e^(-k(level - mid)))` | 解鎖內容 |

### 推薦用法
- **玩家屬性**: 對數曲線（避免後期爆炸）
- **升級經驗**: 指數曲線（延長遊戲壽命）
- **解鎖內容**: S曲線（控制節奏）

## damage-calculation

### 傷害計算範例

```
基礎傷害 = 攻擊力 x (100 / (100 + 防禦力))
DPS = (基礎傷害 x 暴擊加成) / 攻擊間隔
暴擊加成 = 1 + (暴擊率 x 暴擊倍率)
```

### 平衡檢查點
- TTK (Time To Kill) 合理嗎？
- 高低等級差距是否過大？
- 是否有數值溢出風險？
- 各職業/角色是否平衡？

## number-overflow-fix

### 數值溢出解決方案

```python
# 錯誤做法 - 純指數成長
damage = base * (1.5 ** level)  # Level 100 = 4e17

# 正確做法 - 對數或軟上限
damage = base * log(level + 1) * level  # 可控成長

# 或使用漸近線
damage = base * (max_multiplier * level / (level + k))
```

## economy-resource-types

| 資源類型 | 獲取難度 | 用途 | 範例 |
|----------|----------|------|------|
| 軟通貨 | 易 | 日常消耗 | 金幣 |
| 硬通貨 | 難 | 稀有物品 | 鑽石 |
| 體力 | 時間 | 限制遊玩 | 行動力 |
| 材料 | 中等 | 製造升級 | 素材 |

## dialogue-variables

```yaml
# 對話系統需要追蹤的變數
player_choices:
  helped_merchant: true
  sided_with_rebels: false

relationship_values:
  companion_a: 75  # -100 到 100
  faction_b: -20

story_flags:
  act1_completed: true
  secret_discovered: false
```

## pcg-applications

| 元素 | 方法 | 範例 |
|------|------|------|
| 地圖 | Wave Function Collapse | Spelunky |
| 關卡 | 規則系統 + 隨機種子 | Diablo |
| 敵人配置 | 難度曲線 + 隨機選擇 | Left 4 Dead |
| 對話 | LLM 生成 | AI Dungeon |
| 任務 | 模板 + 變數替換 | Radiant Quests |
| 名字/描述 | Markov Chain / LLM | Dwarf Fortress |

### PCG 設計原則
1. 設定合理的約束（避免不可能的生成）
2. 保證最低品質（過濾不合理結果）
3. 保留手工設計的關鍵內容
4. 種子系統（可復現的隨機）

## npc-ai-patterns

### 行為樹 (Behavior Tree)
傳統 AI，可預測，適合敵人 AI

```
Selector -> Sequence -> Action
   |
[攻擊] -> [追擊] -> [巡邏]
```

### 狀態機 (FSM)
簡單直覺，適合基礎 NPC

```
[待機] <-> [警戒] <-> [攻擊]
              ^          |
              +-- [逃跑] <+
```

### LLM 驅動 NPC（實驗性）
動態對話、個性化反應。挑戰：成本、延遲、一致性

## ui-types

### 遊戲 UI 層級

| 類型 | 說明 | 範例 | 優缺點 |
|------|------|------|--------|
| Diegetic UI | 存在於遊戲世界中 | Dead Space 背部血條 | 沉浸感強但不易讀取 |
| Non-Diegetic UI | 純粹介面元素 (HUD) | 血條、小地圖 | 資訊清晰但可能影響沉浸 |
| Spatial UI | 存在於 3D 空間但不屬於世界 | 敵人頭上的血條 | 介於兩者之間 |

### 設計要點
- 重要資訊放在視覺焦點區域
- 動態元素要有動畫過渡
- 顏色要有高對比度（紅=危險、綠=安全）
- 支援色盲模式
