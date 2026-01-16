---
schema: "1.0"
name: skill-optimizer
version: "1.0.0"
description: Skill 瘦身優化器 — 減少 token 使用同時保持功能完整
triggers:
  - skill 優化
  - skill 瘦身
  - 減少 token
  - skill optimization
  - reduce tokens
keywords: [methodology, optimization, skill-development, token-efficiency]
author: claude-domain-skills
---

# Skill Optimizer v1.0.0

> 優化 SKILL.md 的 token 使用效率，同時保持功能完整

## 快速開始

```bash
# 分析單一 skill
/skill-optimizer analyze [skill-path]

# 優化單一 skill
/skill-optimizer optimize [skill-path]

# 批次分析整個 repo
/skill-optimizer audit [repo-path]
```

---

## 1. 優化原則

### 1.1 Token 效率金字塔

```
               ┌─────────┐
               │ 必要的  │ ← 保留：triggers, 核心知識
               ├─────────┤
               │ 有用的  │ ← 精簡：最佳實踐, 常見錯誤
               ├─────────┤
               │ 美化的  │ ← 移除：ASCII art, 裝飾性圖表
               ├─────────┤
               │ 範例化  │ ← 外連：模板, 完整範例, checklist
               └─────────┘
```

### 1.2 核心策略

| 策略 | 說明 | 節省估計 |
|------|------|----------|
| **分層載入** | 核心 + 擴展分離 | 40-60% |
| **外連參考** | 大型範例移到獨立檔案 | 20-30% |
| **精簡表達** | 移除冗餘修飾語 | 10-15% |
| **圖表簡化** | ASCII → 簡潔描述 | 5-10% |

---

## 2. 分層結構

### 2.1 建議的 Skill 結構

```
skill-name/
├── SKILL.md           # 核心層 (< 300 行)
│   ├── frontmatter    # triggers, keywords
│   ├── 核心知識       # 最重要的 20%
│   └── 快速參考       # 常用項目
│
├── extended/          # 擴展層 (按需載入)
│   ├── templates.md   # 模板集合
│   ├── examples.md    # 完整範例
│   └── checklists.md  # 檢查清單
│
└── references/        # 參考層 (外部連結)
    └── links.md       # 外部資源連結
```

### 2.2 核心層內容標準

**必須包含** (< 300 行):
- Frontmatter (triggers, keywords)
- 適用場景 (5-10 項)
- 核心概念 (3-5 個)
- 決策框架 (1-2 個)
- Sharp Edges (3-5 個)

**應該外連**:
- 完整範例 (> 20 行)
- 模板 (> 10 行)
- 詳細 checklist
- ASCII 圖表 (> 10 行)

---

## 3. 優化流程

### 3.1 分析階段

```
Step 1: 統計
────────────────────────────────────────
wc -l SKILL.md                    # 總行數
grep -c "^#" SKILL.md             # 章節數
grep -c "```" SKILL.md            # 程式碼區塊數
grep -E "┌|└|│|─" SKILL.md | wc -l  # ASCII 圖表行數

Step 2: 分類
────────────────────────────────────────
識別各區塊的類型：
□ 核心知識 (必要)
□ 最佳實踐 (有用)
□ 範例/模板 (可外連)
□ ASCII 圖表 (可簡化)
□ 裝飾性內容 (可移除)

Step 3: 評分
────────────────────────────────────────
Token 效率分數 = 核心內容行數 / 總行數 × 100

優秀: > 70%
良好: 50-70%
需優化: < 50%
```

### 3.2 優化執行

**A. 圖表簡化**

Before (8 行, ~200 tokens):
```
┌─────────────────────────────────────┐
│  MDA Framework                       │
│                                      │
│  Mechanics → Dynamics → Aesthetics   │
│  機制        動態        美學        │
│                                      │
│  設計師角度 ─────────→ 玩家角度     │
└─────────────────────────────────────┘
```

After (2 行, ~30 tokens):
```
MDA: Mechanics(規則) → Dynamics(行為) → Aesthetics(感受)
     設計師視角 ───────────────────────→ 玩家視角
```

**B. 表格精簡**

Before (大型數值表):
```markdown
| 階段 | 玩家 HP | 敵人 HP | 戰鬥時長 | 經驗值 | 金幣 |
|------|---------|---------|----------|--------|------|
| 初期 | 100 | 30-50 | 10-30 秒 | 10-20 | 5-10 |
| 中期 | 500 | 200-400 | 30-60 秒 | 50-100 | 20-50 |
| 後期 | 2000 | 1000+ | 1-3 分鐘 | 200+ | 100+ |
```

After (外連):
```markdown
數值平衡參考 → [extended/balance-tables.md]
```

**C. 範例外連**

Before (內嵌 50 行模板):
```markdown
## GDD 模板

### 1. 概述
- 遊戲名稱
- 類型、平台
... (50 行)
```

After (外連):
```markdown
## GDD 模板

完整模板 → [extended/templates.md#gdd]

快速版 (核心三要素):
1. 核心體驗：一句話描述
2. 核心循環：玩家重複做什麼
3. 獨特賣點：為什麼玩這款
```

---

## 4. 優化檢查清單

### 4.1 結構檢查

- [ ] 總行數 < 300
- [ ] 核心知識佔比 > 70%
- [ ] 無 > 20 行的範例
- [ ] 無 > 10 行的 ASCII 圖表
- [ ] 有 extended/ 目錄放置擴展內容

### 4.2 內容檢查

- [ ] Frontmatter 完整 (triggers, keywords)
- [ ] 適用場景明確
- [ ] 核心概念精簡
- [ ] Sharp Edges 保留
- [ ] 大型範例已外連

### 4.3 連結檢查

- [ ] 外連路徑正確
- [ ] extended/ 檔案存在
- [ ] 參考資源可訪問

---

## 5. 範例：優化前後對比

### Before: game-design (934 行)

```
章節分布：
├── 核心知識: 200 行 (21%)
├── 範例/模板: 450 行 (48%) ← 可外連
├── ASCII 圖表: 180 行 (19%) ← 可簡化
└── 最佳實踐: 104 行 (11%)

Token 效率: 21% (需優化)
```

### After: game-design (280 行)

```
章節分布：
├── 核心知識: 180 行 (64%)
├── 簡化圖表: 30 行 (11%)
├── 最佳實踐: 50 行 (18%)
└── 外連指引: 20 行 (7%)

Token 效率: 64% (良好)
節省: 70% tokens
```

---

## 6. 自動化腳本

### 6.1 分析腳本

```bash
#!/bin/bash
# skill-analyzer.sh

SKILL_PATH="$1"

echo "=== Skill Analysis ==="
echo "Total lines: $(wc -l < "$SKILL_PATH")"
echo "Sections: $(grep -c "^#" "$SKILL_PATH")"
echo "Code blocks: $(grep -c '```' "$SKILL_PATH" | awk '{print $1/2}')"
echo "ASCII art lines: $(grep -cE '┌|└|│|─|╭|╰' "$SKILL_PATH")"

# 計算效率
TOTAL=$(wc -l < "$SKILL_PATH")
ASCII=$(grep -cE '┌|└|│|─|╭|╰' "$SKILL_PATH")
EFFICIENCY=$((100 - ASCII * 100 / TOTAL))
echo "Estimated efficiency: ${EFFICIENCY}%"
```

### 6.2 批次審計

```bash
#!/bin/bash
# skill-audit.sh

REPO_PATH="$1"

echo "=== Skill Repository Audit ==="
echo ""
printf "%-40s %8s %10s\n" "Skill" "Lines" "Efficiency"
echo "────────────────────────────────────────────────────────────"

find "$REPO_PATH" -name "SKILL.md" -not -path "*/\.*" | while read skill; do
  NAME=$(dirname "$skill" | xargs basename)
  LINES=$(wc -l < "$skill")
  ASCII=$(grep -cE '┌|└|│|─' "$skill" 2>/dev/null || echo 0)
  EFF=$((100 - ASCII * 100 / LINES))

  if [ $LINES -gt 500 ]; then
    STATUS="⚠️"
  elif [ $LINES -gt 300 ]; then
    STATUS="🟡"
  else
    STATUS="✅"
  fi

  printf "%-40s %8d %9d%% %s\n" "$NAME" "$LINES" "$EFF" "$STATUS"
done

echo ""
echo "Legend: ✅ Good (<300) | 🟡 Review (300-500) | ⚠️ Optimize (>500)"
```

---

## 7. 常見問題

### Q: 分層後如何確保完整功能？

A: 核心層包含 80% 常用功能。當需要完整範例時，AI 會自動提示：
```
「需要完整的 GDD 模板嗎？我可以載入 extended/templates.md」
```

### Q: 外連檔案會增加複雜度？

A: 是的，但：
- 大多數情況不需要載入
- 按需載入節省 token
- 結構更清晰

### Q: 如何判斷內容是否該外連？

A: 使用「3 次法則」：
- 如果這段內容在 3 次對話中只用到 1 次 → 外連
- 如果每次都用到 → 保留在核心

---

## 版本歷史

| 版本 | 日期 | 變更 |
|------|------|------|
| 1.0.0 | 2026-01-15 | 初版：Skill 優化方法論 |
