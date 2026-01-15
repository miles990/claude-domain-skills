# Galgame 創作模板 Templates

> 詳細模板與指示書格式

## 角色設定完整模板

```json
{
  "character_id": "unique_id",
  "name": "角色名",
  "age": 17,

  "type_combination": {
    "dere": "類型ID",
    "relationship": "類型ID",
    "identity": "類型ID",
    "special": ["屬性1", "屬性2"]
  },

  "appearance": {
    "height": "165cm",
    "hair": "黑色長髮",
    "eyes": "深褐色",
    "features": ["特徵1", "特徵2"],
    "usual_outfit": "服裝描述"
  },

  "personality": {
    "surface": "表面印象描述",
    "private": "私底下真實個性",
    "gap_moe": ["反差萌點1", "反差萌點2"]
  },

  "speech_pattern": {
    "tone": "語氣特色",
    "signature_phrases": ["口頭禪1", "口頭禪2"],
    "progression": {
      "lv0": "初見時的典型對話",
      "lv3": "熟悉後的對話",
      "lv5": "親密時的對話"
    }
  },

  "bond_reactions": {
    "praise": "被誇獎的反應",
    "jealousy": "吃醋時的反應",
    "affection": "撒嬌的方式"
  },

  "route_themes": ["路線主題1", "路線主題2"],
  "conflict_source": "角色內心衝突來源"
}
```

---

## CG 指示書模板

```yaml
cg_spec:
  scene_id: unique_id
  title: CG 名稱

  composition:
    type: [特寫/半身/全身/雙人/群像]
    focus: [焦點角色或元素]
    angle: [視角描述]

  characters:
    - id: 角色ID
      pose: 姿勢描述
      expression: 表情
      action: 動作

  environment:
    location: 場景
    time: 時間
    weather: 天氣（如適用）

  atmosphere:
    mood: [浪漫/緊張/溫馨/...]
    lighting: 光線描述
    color_tone: 色調

  key_elements:
    - 重要視覺元素1
    - 重要視覺元素2
```

---

## 標準表情差分清單

| ID | 表情 | 適用情境 |
|----|------|----------|
| neutral | 普通 | 日常對話 |
| smile | 微笑 | 友善互動 |
| laugh | 大笑 | 搞笑場景 |
| sad | 悲傷 | 感傷時刻 |
| angry | 生氣 | 衝突場景 |
| embarrassed | 害羞 | 曖昧互動 |
| surprised | 驚訝 | 突發事件 |
| crying | 哭泣 | 感動/悲傷 |
| love | 愛心眼 | 戀愛場景 |
| special_1 | 角色專屬1 | 依角色設計 |
| special_2 | 角色專屬2 | 依角色設計 |

---

## 劇本結構模板

### 共通路線章節

```yaml
common_route:
  prologue:
    title: 序章
    duration: 約30分鐘
    goals:
      - 介紹主角與世界觀
      - 第一印象事件（各角色）
      - 建立日常基調

  chapter_1:
    title: 日常篇
    duration: 約2小時
    goals:
      - 深化角色印象
      - 建立關係基礎
      - 埋下個人路線伏筆

  chapter_2:
    title: 事件篇
    duration: 約2小時
    goals:
      - 觸發各角色關鍵事件
      - 累積好感度
      - 準備分歧選擇

  branch_point:
    title: 分歧點
    timing: 共通路線結束時
    mechanism: 好感度 + 關鍵選擇
```

### 個人路線章節

```yaml
personal_route:
  character_id: 角色ID

  deep_chapter:
    title: 深入篇
    goals:
      - 揭露角色背景
      - 展現內心世界
      - 建立專屬互動

  conflict_chapter:
    title: 衝突篇
    goals:
      - 核心矛盾爆發
      - 關係危機
      - 角色成長契機

  resolution_chapter:
    title: 解決篇
    goals:
      - 一同克服困難
      - 關係昇華
      - 準備結局

  endings:
    true_end:
      condition: 好感度滿 + 正確選擇
      theme: 最完美的結局
    good_end:
      condition: 好感度高
      theme: 幸福但有遺憾
    normal_end:
      condition: 好感度中等
      theme: 淡淡的結束
    bad_end:
      condition: 錯誤選擇
      theme: 遺憾結局
```

---

## 設計檢查清單

### 角色設計
- [ ] 選定類型組合（Dere + 關係 + 身份 + 特殊）
- [ ] 基本資訊完整
- [ ] 有「表面 vs 私底下」反差
- [ ] 有 Lv0-Lv5 好感度變化
- [ ] 有專屬 speech_pattern
- [ ] 有 gap_moe_triggers
- [ ] 有 bond_reactions

### 劇本結構
- [ ] 共通路線完整
- [ ] 各角色個人路線
- [ ] 多結局設計
- [ ] 關鍵分歧點明確

### 美術資源
- [ ] 角色立繪指示
- [ ] 表情差分列表
- [ ] 關鍵 CG 指示書
- [ ] 背景清單

### 多角色平衡
- [ ] 有反差對照
- [ ] 戲份平衡
- [ ] 三角關係動態（如適用）
