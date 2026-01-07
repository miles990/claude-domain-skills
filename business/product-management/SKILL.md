---
schema: "1.0"
name: product-management
version: "1.0.0"
description: 產品管理：PRD撰寫、用戶故事、OKR設定、路線圖規劃
triggers: [PRD, 產品需求, 用戶故事, user story, OKR, 路線圖, roadmap, 產品規格, spec, 功能規劃, feature, 產品經理, PM, product]
keywords: [business, product, management, planning]
author: claude-domain-skills
---

# 產品管理 Product Management

> 從需求到交付的完整產品開發流程

## 適用場景

- 撰寫產品需求文件（PRD）
- 定義用戶故事和驗收標準
- 設定 OKR 和成功指標
- 規劃產品路線圖
- 功能優先級排序

## PRD 結構框架

```
┌─────────────────────────────────────────────────────────────────┐
│  PRD 標準結構                                                   │
│                                                                 │
│  1. 概述 Overview                                               │
│     ├─ 問題陳述（為什麼做）                                    │
│     ├─ 目標用戶（為誰做）                                      │
│     └─ 成功指標（如何衡量）                                    │
│                                                                 │
│  2. 需求詳情 Requirements                                       │
│     ├─ 功能需求（User Stories）                                │
│     ├─ 非功能需求（效能、安全）                                │
│     └─ 設計約束                                                │
│                                                                 │
│  3. 設計 Design                                                 │
│     ├─ 用戶流程                                                │
│     ├─ 線框圖/原型連結                                         │
│     └─ 邊界情況處理                                            │
│                                                                 │
│  4. 技術考量 Technical                                          │
│     ├─ 架構影響                                                │
│     ├─ API 需求                                                │
│     └─ 依賴項目                                                │
│                                                                 │
│  5. 上線計劃 Launch                                             │
│     ├─ 里程碑                                                  │
│     ├─ 風險評估                                                │
│     └─ 驗收標準                                                │
└─────────────────────────────────────────────────────────────────┘
```

## User Story 格式

```markdown
### 標準格式
As a [用戶角色]
I want [功能/目標]
So that [價值/原因]

### 驗收標準 (Acceptance Criteria)
Given [前提條件]
When [觸發動作]
Then [預期結果]

### 範例
As a 電商買家
I want 保存商品到願望清單
So that 我可以稍後購買

驗收標準：
- Given 用戶已登入
- When 點擊「加入願望清單」
- Then 商品出現在願望清單中
- And 顯示成功提示
```

## OKR 設定框架

| 元素 | 說明 | 範例 |
|------|------|------|
| **Objective** | 定性目標，激勵人心 | 成為最受信任的支付平台 |
| **Key Result 1** | 可量化的結果 | NPS 從 45 提升到 60 |
| **Key Result 2** | 可量化的結果 | 交易成功率達 99.9% |
| **Key Result 3** | 可量化的結果 | 客訴處理時間 < 2 小時 |

### OKR 檢查清單

```
□ Objective 是否具有挑戰性但可達成？
□ Key Results 是否可量化？
□ Key Results 是否有明確的基準和目標值？
□ 是否有 3-5 個 Key Results？
□ 是否設定了檢查週期？
```

## 優先級排序框架

### RICE Framework

| 維度 | 說明 | 評分 |
|------|------|------|
| **R**each | 影響多少用戶 | 用戶數/季 |
| **I**mpact | 影響程度 | 0.25/0.5/1/2/3 |
| **C**onfidence | 信心程度 | 50%/80%/100% |
| **E**ffort | 開發成本 | 人月 |

**RICE Score = (Reach × Impact × Confidence) / Effort**

### MoSCoW 分類

| 分類 | 說明 |
|------|------|
| **Must have** | 核心功能，沒有就不能上線 |
| **Should have** | 重要功能，但可以後續迭代 |
| **Could have** | 錦上添花，有時間就做 |
| **Won't have** | 這次不做，明確排除 |

## 路線圖模板

```markdown
## Q1 2025

### 主題：基礎建設
- [ ] 用戶認證系統重構
- [ ] API Gateway 升級
- [ ] 監控系統建置

### 里程碑
- 1/15: 技術設計完成
- 2/28: 開發完成
- 3/15: 上線

---

## Q2 2025

### 主題：用戶體驗優化
- [ ] 新版首頁
- [ ] 搜尋功能強化
- [ ] 個人化推薦 V1
```

## 常見錯誤

| 錯誤 | 正確做法 |
|------|----------|
| PRD 寫太詳細像設計文件 | 聚焦 What & Why，留 How 給工程團隊 |
| User Story 沒有驗收標準 | 每個 Story 必須有明確的 AC |
| OKR 設太多 | 聚焦 3-5 個最重要的 |
| 路線圖鎖死日期 | 用「主題」而非「功能清單」 |

## 溝通模板

### 功能規格簡報

```markdown
# [功能名稱]

## 一句話描述
[用一句話說明這個功能是什麼]

## 為什麼做
- 用戶痛點：[描述]
- 商業價值：[描述]

## 做什麼
- [功能點 1]
- [功能點 2]

## 不做什麼
- [明確排除的範圍]

## 成功指標
- [指標 1]: 從 X 到 Y
- [指標 2]: 從 X 到 Y

## 時程
- 設計：X 週
- 開發：X 週
- 測試：X 週
```

## 相關資源

- [Inspired - Marty Cagan](https://www.amazon.com/INSPIRED-Create-Tech-Products-Customers/dp/1119387507)
- [Shape Up - Basecamp](https://basecamp.com/shapeup)
- [The Mom Test - Rob Fitzpatrick](http://momtestbook.com/)
