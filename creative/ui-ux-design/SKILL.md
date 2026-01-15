---
schema: "1.0"
name: ui-ux-design
version: "1.1.0"
description: UI/UX 設計：介面設計原則、用戶體驗、可用性、無障礙設計
triggers:
  keywords:
    primary: [UI, UX, 介面設計, 用戶體驗, interface, user-experience, wireframe]
    secondary: [usability, accessibility, 可用性, 無障礙, prototype, 原型, 設計系統]
  context_boost: [figma, design, component, layout, mobile, responsive]
  context_penalty: [backend, api, database, trading]
  priority: high
keywords: [creative, design, ui, ux, interface]
dependencies:
  software-skills: [frontend]
author: claude-domain-skills
---

# UI/UX 設計 UI/UX Design

> 以用戶為中心的設計思維

## 適用場景

- 設計用戶介面和互動流程
- 建立設計系統和元件庫
- 進行可用性評估
- 確保無障礙合規
- 製作線框圖和原型

## 核心設計原則

| 原則 | 說明 |
|------|------|
| **一致性** | 相同功能使用相同的視覺和互動模式 |
| **可見性** | 重要資訊和操作應該容易被發現 |
| **回饋** | 每個操作都應該有即時的視覺或聽覺回饋 |
| **容錯** | 允許用戶撤銷操作，避免災難性錯誤 |
| **簡約** | 只顯示必要的資訊，減少認知負荷 |

## 視覺層級

| 層級 | 用途 | 設計手法 |
|------|------|----------|
| **Primary** | 主要行動 | 大按鈕、強對比色 |
| **Secondary** | 次要行動 | 較小、輪廓按鈕 |
| **Tertiary** | 輔助資訊 | 文字連結、淡色 |

視覺重量優先級：大小 > 顏色對比 > 粗細 > 位置 > 間距

## 間距系統（8pt Grid）

| Token | 值 | 用途 |
|-------|-----|------|
| xs | 4px | 緊湊間距 |
| sm | 8px | 相關元素 |
| md | 16px | 區塊間距 |
| lg | 24px | 區塊間距 |
| xl | 32px | 章節間距 |
| xxl | 48px | 大區塊分隔 |

## 色彩使用

### 語意色彩

| 色彩 | 用途 | Hex 範例 |
|------|------|----------|
| Primary | 品牌主色、主要 CTA | #0066FF |
| Success | 成功、確認、完成 | #00C853 |
| Warning | 警告、需注意 | #FFB300 |
| Error | 錯誤、危險、刪除 | #FF3D00 |
| Info | 資訊、提示 | #00B0FF |

### 對比度要求（WCAG 2.1）

| 層級 | 普通文字 | 大型文字 |
|------|----------|----------|
| AA | 4.5:1 | 3:1 |
| AAA | 7:1 | 4.5:1 |

## 無障礙設計 (WCAG POUR)

| 原則 | 核心要求 |
|------|----------|
| **Perceivable** | 圖片有 alt、色彩不是唯一資訊、對比度 AA |
| **Operable** | 鍵盤可操作、Focus 明顯、無閃爍 |
| **Understandable** | 語言指定、表單標籤清楚、導航一致 |
| **Robust** | 語意化 HTML、ARIA 正確、跨裝置相容 |

### 常見修復

| 問題 | 解決方案 |
|------|----------|
| 圖片無 alt | `<img alt="描述">` |
| 低對比度 | 使用對比度檢查工具 |
| 無鍵盤導航 | 確保 `tabindex` 正確 |
| 無 focus 指示 | 加入 `:focus` 樣式 |

> 詳細 WCAG 檢查清單見 `extended/checklists.md`

## 互動設計模式

### 導航模式
- **Tab Bar**: 3-5 個主要功能（行動裝置）
- **Side Nav**: 多層級導航（桌面）
- **Breadcrumb**: 深層結構回溯

### 輸入模式
- **Inline Validation**: 即時驗證
- **Progressive Disclosure**: 逐步顯示
- **Default Values**: 預填合理預設

### 回饋模式
- **Toast**: 非阻斷式通知
- **Modal**: 需要用戶決策
- **Skeleton**: 載入中佔位

## 設計系統元件

### 基礎元件
Button, Input, Select, Checkbox/Radio, Toggle, Icon

### 複合元件
Card, Modal, Toast, Table, Pagination, Navigation

### 版面元件
Container, Grid, Stack, Divider

## Nielsen 10 大可用性啟發式

| # | 啟發式 | 檢查問題 |
|---|--------|----------|
| 1 | 系統狀態可見 | 用戶知道目前發生什麼事嗎？ |
| 2 | 現實與系統匹配 | 使用用戶熟悉的語言嗎？ |
| 3 | 用戶控制與自由 | 可以撤銷/返回嗎？ |
| 4 | 一致性與標準 | 遵循平台慣例嗎？ |
| 5 | 錯誤預防 | 是否預防錯誤發生？ |
| 6 | 識別而非回憶 | 選項是否可見？ |
| 7 | 靈活與效率 | 有快捷方式嗎？ |
| 8 | 美學與極簡 | 是否只顯示必要資訊？ |
| 9 | 錯誤恢復 | 錯誤訊息有幫助嗎？ |
| 10 | 幫助與文件 | 需要時能找到幫助嗎？ |

## 常見錯誤

| 錯誤 | 正確做法 |
|------|----------|
| 按鈕顏色區分功能 | 用大小/位置/文字區分 |
| Placeholder 當標籤 | 使用獨立的 label |
| 無 hover 狀態 | 所有可互動元素有 hover |
| 自動播放影片 | 需要用戶主動播放 |

## 用戶測試類型

| 類型 | 說明 | 適用階段 |
|------|------|----------|
| 探索性 | 了解用戶如何自然使用 | 早期原型 |
| 任務導向 | 完成特定任務 | 設計中期 |
| 比較測試 | A vs B 方案 | 決策階段 |
| 基準測試 | 量化效能指標 | 上線前/後 |

> 測試準備清單見 `extended/checklists.md`

## 響應式設計

### 斷點（Mobile First）

| 裝置 | 寬度 |
|------|------|
| 手機 | < 640px（預設）|
| 平板 | >= 768px |
| 筆電 | >= 1024px |
| 桌機 | >= 1280px |

### 關鍵策略
- 手機：觸控區域 44px+、單欄布局
- 桌面：hover 狀態、多欄布局

> 響應式詳細指南見 `extended/examples.md`

## 動效設計原則

| 原則 | 實作 |
|------|------|
| 目的性 | 引導注意力、表達關係 |
| 自然性 | 使用緩動函數 |
| 快速 | 大多 200-300ms |
| 一致性 | 建立動效規範 |

> 緩動函數詳細參考見 `extended/examples.md`

## 深色模式要點

- 不是簡單反轉，需重新設計色階
- 背景層級：#121212 → #1E1E1E → #2D2D2D
- 文字：87% / 60% / 38% 白色透明度
- 強調色降低飽和度，確保對比度

> 深色模式完整指南見 `extended/examples.md`

## 設計系統建立

Audit(審計) → Define(定義) → Build(建立) → Maintain(維護)

> 詳細步驟與 Design Token 範例見 `extended/templates.md`

## 工具推薦

- **設計**：Figma, Sketch
- **原型**：Figma, ProtoPie
- **無障礙測試**：axe, WAVE
- **對比度**：WebAIM Contrast Checker

## 相關資源

- [Material Design](https://m3.material.io/)
- [Apple HIG](https://developer.apple.com/design/human-interface-guidelines/)
- [Nielsen Norman Group](https://www.nngroup.com/articles/)
- [WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/)

## 延伸閱讀

- `extended/templates.md` - 設計交接清單、測試報告模板、Design Token
- `extended/examples.md` - 響應式、動效、深色模式詳細指南
- `extended/checklists.md` - WCAG、可用性測試、上線前檢查清單
