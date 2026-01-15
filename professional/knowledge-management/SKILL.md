---
schema: "1.0"
name: knowledge-management
version: "1.0.0"
description: 知識管理：第二大腦、筆記系統、資訊整理、數位工具流
domain: professional
triggers:
  keywords:
    primary: [知識管理, knowledge management, 第二大腦, second brain, 筆記, note-taking, PKM, zettelkasten, 卡片盒]
    secondary: [資訊整理, 數位花園, digital garden, 工具流, workflow, PARA, Obsidian, Notion, Roam, Logseq]
  context_boost: [生產力, productivity, 學習, learning, 輸出, output, 連結, linking]
  context_penalty: [code, 程式, api, database, 技術]
  priority: medium
dependencies:
  software-skills: [documentation]
author: claude-domain-skills
---

# 知識管理 Knowledge Management

> 建立個人知識系統，讓資訊成為可複利的資產

## 適用場景

- 建立個人筆記系統
- 設計資訊整理工作流
- 打造第二大腦
- 數位工具選擇與整合
- 知識輸出與分享

## CODE 方法 (Building a Second Brain)

**Capture → Organize → Distill → Express**

| 階段 | 動作 | 重點 |
|------|------|------|
| Capture 捕捉 | 收集有價值的資訊 | 只收集會用到的 |
| Organize 整理 | 用 PARA 系統分類 | 按可操作性分類 |
| Distill 萃取 | 提煉重點摘要 | 漸進式摘要 |
| Express 表達 | 輸出和創造 | 學以致用 |

**核心：不是收集更多，而是找到時能用得上**

## PARA 分類系統

| 分類 | 定義 | 範例 |
|------|------|------|
| **P**rojects 專案 | 有明確截止日期的任務 | 產品發布、報告撰寫 |
| **A**reas 領域 | 持續維護的責任範圍 | 健康、財務、職涯 |
| **R**esources 資源 | 感興趣的主題參考資料 | 投資、寫作、AI |
| **A**rchives 封存 | 已完成或不再活躍的項目 | 舊專案、過期資料 |

**分類原則：按「可操作性」而非「主題」**

## 卡片盒筆記法 (Zettelkasten)

### 核心原則
1. **原子性** - 一張卡片一個概念
2. **連結性** - 卡片之間互相連結
3. **自己的話** - 用自己的理解重寫
4. **永久筆記** - 經過思考的筆記

### 筆記類型

| 類型 | 說明 | 保留時間 |
|------|------|----------|
| 閃念筆記 | 快速捕捉想法 | 臨時 |
| 文獻筆記 | 閱讀時的摘錄 | 參考用 |
| 永久筆記 | 自己消化後的理解 | 永久 |
| 專案筆記 | 特定專案相關 | 專案期間 |

## 漸進式摘要

Layer 0: 原始內容 → Layer 1: 粗體標記重點句 → Layer 2: 螢光標記關鍵詞 → Layer 3: 頂部摘要 → Layer 4: 原創見解

**原則：只在需要時才進行下一層，按需深入**

## 工具選擇矩陣

| 需求 | 推薦工具 | 特點 |
|------|----------|------|
| 雙向連結筆記 | Obsidian, Logseq | 本地、Markdown |
| 全功能 All-in-One | Notion | 雲端、團隊協作 |
| 快速捕捉 | Apple Notes, Drafts | 速度優先 |
| 閱讀稍後 | Readwise, Instapaper | 標註同步 |
| 任務管理 | Todoist, Things | GTD 流程 |
| 長期儲存 | DEVONthink, Evernote | 搜尋強大 |

## 工作流設計

```
資訊流: 瀏覽器 → 稍後閱讀 → 標註 → 筆記軟體 → 永久筆記
任務流: 收件匣 → 處理 → 專案/待辦 → 執行 → 歸檔
```

### 每日流程
1. 早上：檢視今日任務
2. 工作：專注執行
3. 隨時：快速捕捉想法
4. 晚上：整理收件匣，規劃明天

## 輸入與輸出平衡

**知識複利週期：輸入 → 連結 → 創造 → 分享 → (回饋成為新輸入)**

| 輸入 | 輸出 |
|------|------|
| 閱讀、課程、Podcast、對話 | 寫作、教學、創作、應用 |

**建議比例：輸入 : 處理 : 輸出 = 3 : 2 : 5**

**關鍵：輸出倒逼輸入，學以致用**

## 搜尋優先原則

**現代思維：快速存入 + 強大搜尋 > 花大量時間分類**

### 搜尋優化技巧
- **標題命名**：`2024-01-15-產品策略會議-Q1目標討論.md`
- **關鍵詞嵌入**：`tags: 產品, 策略, OKR, Q1`
- **別名同義詞**：`aliases: [PKM, 個人知識管理]`
- **特殊標記**：`TODO:`, `IDEA:`, `QUESTION:`

## 連結策略

| 連結類型 | 說明 | 範例 |
|----------|------|------|
| 定義連結 | 解釋概念 | [[費曼技巧]]是什麼 |
| 證據連結 | 支持論點 | 根據[[研究報告]] |
| 應用連結 | 使用案例 | 在[[專案X]]中應用 |
| MOC 連結 | 索引頁面 | 屬於[[生產力 MOC]] |

**何時建立連結？當你發現「這讓我想到...」的時候**

## 常見陷阱

| 陷阱 | 解決 |
|------|------|
| 收集狂 | 只收集會用到的 |
| 工具控 | 工具服務目的，不是目的 |
| 過度分類 | 搜尋比分類更重要 |
| 只輸入不輸出 | 強制輸出，學以致用 |
| 追求完美系統 | 開始比完美重要 |

## 延伸資源

完整模板請見 `extended/templates.md`：
- 會議筆記模板
- 閱讀筆記模板
- 專案筆記模板
- 週回顧模板
- 每日/週/月/季流程清單

範例與架構請見 `extended/examples.md`：
- 數位花園架構
- 個人 Wiki 結構
- MOC 範例
- 知識管理成熟度模型
- AI 輔助知識管理

## 工具推薦

- **筆記**: Obsidian, Notion, Logseq, Roam
- **閱讀**: Readwise, Kindle, Pocket
- **任務**: Todoist, Things 3, TickTick
- **自動化**: Zapier, Make, Shortcuts
- **寫作**: Ulysses, iA Writer, Typora

## 相關資源

- [Building a Second Brain - Tiago Forte](https://www.buildingasecondbrain.com/)
- [How to Take Smart Notes - Sönke Ahrens](https://www.soenkeahrens.de/en/takesmartnotes)
- [Obsidian](https://obsidian.md/)
- [Zettelkasten Method](https://zettelkasten.de/)
