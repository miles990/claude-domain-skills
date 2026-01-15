# Galgame 創作範例 Examples

> 角色類型詳細說明、對話生成範例、美術指示範例

## 角色類型完整定義

### 傲嬌 (Tsundere)

```json
{
  "type_id": "tsundere",
  "core_trait": "口是心非，越喜歡越彆扭",
  "surface_vs_private": {
    "public": "毒舌、冷淡、「才不是為了你」",
    "private": "偷偷關心、準備東西、臉紅心跳"
  },
  "speech_pattern": {
    "signature_phrases": ["才、才不是！", "不要誤會了！", "哼，隨便你", "笨蛋......"],
    "progression": {
      "lv0": "「你誰啊，走開。」",
      "lv3": "「才不是擔心你......只是剛好經過！」",
      "lv5": "「......只有你可以看到這樣的我。笨蛋。」"
    }
  },
  "gap_moe_triggers": ["被抓到偷偷關心", "收到禮物不知所措", "吃醋但嘴硬"],
  "bond_reactions": {
    "praise": "「哼、這種程度當然的吧！」（耳朵紅了）",
    "jealousy": "「你和那傢伙很好嘛......隨便你！」",
    "affection": "「......今天可以待久一點。才沒有別的意思！」"
  }
}
```

### 冷嬌 (Kuudere)

```json
{
  "type_id": "kuudere",
  "core_trait": "冰山美人，情感表達笨拙",
  "surface_vs_private": {
    "public": "面無表情、話少、看起來沒興趣",
    "private": "內心戲很多、不知道怎麼表達"
  },
  "speech_pattern": {
    "signature_phrases": ["......嗯", "......隨便", "（沉默）"],
    "progression": {
      "lv0": "「......」（看你一眼就走了）",
      "lv3": "「......你來了。」（其實等很久了）",
      "lv5": "「......想見你。」（說完就轉頭，耳朵紅）"
    }
  },
  "design_notes": "魅力在於『稀有的表情變化』，要設計明確的融化過程"
}
```

### 小惡魔 (Koakuma)

```json
{
  "type_id": "koakuma",
  "core_trait": "故意撩撥，享受狩獵遊戲",
  "surface_vs_private": {
    "public": "主動挑逗、若即若離",
    "private": "認真時反而害羞、怕被認真對待"
  },
  "speech_pattern": {
    "signature_phrases": ["想我了？", "臉紅了呢～", "上鉤了"],
    "progression": {
      "lv0": "「欸～你看起來很有趣呢～」",
      "lv3": "「奇怪......怎麼換我心跳加速了？」",
      "lv5": "「不要用那種認真的眼神看我......我會害羞的啦......」"
    }
  },
  "design_notes": "反轉在於『獵人變成獵物』"
}
```

### 病嬌 (Yandere)

```json
{
  "type_id": "yandere",
  "core_trait": "愛到極端，佔有慾強烈",
  "surface_vs_private": {
    "public": "溫柔完美、體貼周到",
    "private": "強烈佔有慾、容不下第三者"
  },
  "speech_pattern": {
    "signature_phrases": ["只要有你就好", "我們永遠在一起", "只能看著我"],
    "progression": {
      "lv0": "「你好～我是你的新同學。」（微笑）",
      "lv3": "「今天和誰說話了？告訴我。」",
      "lv5": "「從現在起，你的一切都是我的。」"
    }
  },
  "design_notes": "平衡愛與瘋狂，避免變成純粹恐怖角色"
}
```

---

## 情境對話範例

### 吃醋場景

```
[傲嬌] 「你和那個人很好嘛......隨便你！」（轉身想走）
[冷嬌] 「......那個人。」（沉默，但氣壓變低）
[天然] 「......你和她感情很好呢。」（不懂自己為何難過）
[病嬌] 「那個人是誰？」（微笑但眼神不笑）
[元氣] 「欸欸！我也要加入！」（掩飾不安）
[腹黑] 「真好呢～」（暗中記下那個人）
```

### 告白場景

```
[傲嬌] 「才、才不是告白！只是......不討厭你而已......笨蛋」
[冷嬌] 「......喜歡。」（說完轉頭，耳朵紅透）
[天然] 「我想了很久喔......最喜歡你了！這樣對嗎？」
[元氣] 「我喜歡你！......欸，我說出來了？」
[小惡魔] 「......這次不是開玩笑。我是認真的。」（紅著臉）
[腹黑] 「終於讓你落入我的手中了。」（但眼神很溫柔）
```

### 約會遲到場景

```
[傲嬌] 「遲到了30分鐘......我才沒有等很久！」（其實提早1小時到）
[冷嬌] 「......沒關係。」（其實很在意但不會說）
[天然] 「我以為你不來了......太好了！」（開心得忘記責怪）
[元氣] 「你終於來啦！走吧走吧！」（拉著手就跑）
[病嬌] 「這30分鐘，你在哪裡？做什麼？和誰在一起？」
```

### 被摸頭場景

```
[傲嬌] 「幹、幹嘛啦......」（但沒有閃開）
[冷嬌] （無表情但靠近一點點）
[天然] 「好舒服～再摸一下！」
[元氣] 「欸嘿嘿～」（開心蹭頭）
[小惡魔] 「平常都是我摸你......角色對調了呢」（害羞）
```

---

## CG 指示範例

### 告白場景 CG

```yaml
cg_spec:
  scene_id: confession_sakura
  title: 櫻花樹下的告白

  composition:
    type: 雙人
    focus: 女主角表情
    angle: 稍微仰視，強調女主角站在高處

  characters:
    - id: heroine_01
      pose: 雙手握在胸前
      expression: embarrassed（害羞）
      action: 低頭不敢直視

    - id: protagonist
      pose: 站立面對女主角
      expression: 認真
      action: 伸出手

  environment:
    location: 學校後山櫻花樹下
    time: 傍晚（夕陽）
    weather: 晴朗，櫻花花瓣飄落

  atmosphere:
    mood: 浪漫、緊張
    lighting: 暖橘色夕陽側光
    color_tone: 粉橘暖色調

  key_elements:
    - 飄落的櫻花花瓣
    - 夕陽光暈
    - 女主角泛紅的臉頰
    - 兩人之間的距離感（即將跨越）
```

### 日常場景 CG

```yaml
cg_spec:
  scene_id: cooking_together
  title: 一起做料理

  composition:
    type: 雙人
    focus: 互動動作
    angle: 側面平視

  characters:
    - id: heroine_02
      pose: 圍裙姿態，拿著鍋鏟
      expression: smile
      action: 轉頭看向主角

    - id: protagonist
      pose: 站在旁邊
      expression: 笑容
      action: 遞食材

  environment:
    location: 家庭廚房
    time: 下午
    weather: 室內

  atmosphere:
    mood: 溫馨、日常
    lighting: 室內自然光
    color_tone: 暖色調

  key_elements:
    - 圍裙的居家感
    - 蒸氣上升
    - 眼神交會
    - 幸福的日常感
```

---

## 經典角色組合範例

### 王道後宮配置（4人）

| 角色 | 組合公式 | 定位 |
|------|----------|------|
| A | 傲嬌 + 青梅竹馬 + 雙馬尾 | 王道女主角 |
| B | 冷嬌 + 學姐 + 學生會長 + 黑長直 | 高嶺之花 |
| C | 天然呆 + 學妹 + 元氣 | 治癒系妹妹 |
| D | 腹黑 + 大小姐 | 反差型角色 |

**設計重點**：
- A 和 B 形成「活潑 vs 冷靜」對比
- C 和 D 形成「純真 vs 計算」對比
- A 和 C 搶「日常陪伴」戲份
- B 和 D 搶「神秘感」戲份

### 三角關係配置

```
        主角
       /    \
      /      \
   角色A ---- 角色B
   (青梅竹馬)  (轉學生)

A: 傲嬌，從小認識，太熟悉難開口
B: 冷嬌，神秘轉學生，打破日常

衝突設計：
- A 嫉妒 B 能自然靠近主角
- B 其實羨慕 A 和主角的回憶
- 主角夾在兩人之間
```
