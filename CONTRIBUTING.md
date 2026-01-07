# Contributing to Claude Domain Skills

感謝你有興趣貢獻！以下是貢獻指南。

## 如何貢獻新領域

### 1. Fork 並 Clone

```bash
git clone https://github.com/YOUR_USERNAME/claude-domain-skills.git
cd claude-domain-skills
```

### 2. 選擇適當的分類

| 分類 | 適用內容 |
|------|----------|
| `business/` | 商業運營、銷售、行銷、產品 |
| `finance/` | 金融、投資、交易 |
| `creative/` | 設計、創意、內容創作 |
| `professional/` | 專業服務、研究、顧問 |
| `lifestyle/` | 個人成長、生活品質 |

### 3. 建立 Skill 目錄

```bash
mkdir -p category/your-domain
```

### 4. 建立 SKILL.md

使用以下模板：

```markdown
---
schema: "1.0"
name: your-domain
version: "1.0.0"
description: 簡短描述（一行）
triggers: [中文關鍵詞, english-keyword, 常用術語]
keywords: [category, subcategory]
author: your-name
---

# 領域名稱

> 一句話說明這個領域的價值

## 適用場景

- 場景 1
- 場景 2
- 場景 3

## 核心知識

### 主題 1

[內容...]

### 主題 2

[內容...]

## 最佳實踐

- 實踐 1
- 實踐 2

## 工具推薦

- 工具 1
- 工具 2

## 相關資源

- [資源名稱](URL)
```

### 5. Triggers 設計原則

```yaml
triggers:
  # ✅ 好的 triggers
  - 量化        # 領域專有詞
  - backtest    # 英文同義詞
  - 回測        # 常用說法

  # ❌ 避免的 triggers
  - 分析        # 太廣泛
  - 報告        # 太通用
```

### 6. 提交 Pull Request

```bash
git checkout -b feat/add-your-domain
git add .
git commit -m "feat: 新增 category/your-domain skill"
git push origin feat/add-your-domain
```

然後在 GitHub 上建立 Pull Request。

## 品質檢查清單

- [ ] SKILL.md frontmatter 完整（schema, name, version, triggers, keywords）
- [ ] triggers 包含中英文關鍵詞
- [ ] 內容有實用價值（框架、方法論、最佳實踐）
- [ ] 沒有版權問題的內容
- [ ] README.md 已更新（如需要）

## 問題回報

如果發現問題，請在 [Issues](https://github.com/miles990/claude-domain-skills/issues) 回報。

## 授權

貢獻的內容將以 MIT 授權發布。
