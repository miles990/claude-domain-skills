---
schema: "1.0"
name: ui-ux-design
version: "1.0.0"
description: UI/UX 設計：介面設計原則、用戶體驗、可用性、無障礙設計
triggers: [UI, UX, 介面設計, 用戶體驗, 使用者體驗, 可用性, usability, accessibility, 無障礙, wireframe, 線框圖, prototype, 原型, design system, 設計系統]
keywords: [creative, design, ui, ux, interface]
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

## 設計原則

```
┌─────────────────────────────────────────────────────────────────┐
│  核心設計原則                                                   │
│                                                                 │
│  1. 一致性 Consistency                                          │
│     └─ 相同功能使用相同的視覺和互動模式                        │
│                                                                 │
│  2. 可見性 Visibility                                           │
│     └─ 重要資訊和操作應該容易被發現                            │
│                                                                 │
│  3. 回饋 Feedback                                               │
│     └─ 每個操作都應該有即時的視覺或聽覺回饋                    │
│                                                                 │
│  4. 容錯 Forgiveness                                            │
│     └─ 允許用戶撤銷操作，避免災難性錯誤                        │
│                                                                 │
│  5. 簡約 Simplicity                                             │
│     └─ 只顯示必要的資訊，減少認知負荷                          │
└─────────────────────────────────────────────────────────────────┘
```

## 視覺層級

| 層級 | 用途 | 設計手法 |
|------|------|----------|
| **Primary** | 主要行動 | 大按鈕、強對比色 |
| **Secondary** | 次要行動 | 較小、輪廓按鈕 |
| **Tertiary** | 輔助資訊 | 文字連結、淡色 |

### 層級建立技巧

```
視覺重量由大到小：
大小 > 顏色對比 > 粗細 > 位置 > 間距

範例：
┌──────────────────────────────────────┐
│  標題（24px, Bold, #000）           │  ← 最高層級
│  副標題（16px, Medium, #666）       │  ← 次要層級
│  內文（14px, Regular, #999）        │  ← 最低層級
└──────────────────────────────────────┘
```

## 間距系統

```
8pt Grid System（業界標準）

間距倍數：
- xs: 4px   (0.5x)
- sm: 8px   (1x)
- md: 16px  (2x)
- lg: 24px  (3x)
- xl: 32px  (4x)
- xxl: 48px (6x)

使用規則：
- 相關元素：sm (8px)
- 區塊間距：md-lg (16-24px)
- 章節間距：xl-xxl (32-48px)
```

## 色彩使用

### 語意色彩

| 色彩 | 用途 | Hex 範例 |
|------|------|----------|
| **Primary** | 品牌主色、主要 CTA | #0066FF |
| **Success** | 成功、確認、完成 | #00C853 |
| **Warning** | 警告、需注意 | #FFB300 |
| **Error** | 錯誤、危險、刪除 | #FF3D00 |
| **Info** | 資訊、提示 | #00B0FF |

### 對比度要求（WCAG 2.1）

| 層級 | 普通文字 | 大型文字 |
|------|----------|----------|
| **AA** | 4.5:1 | 3:1 |
| **AAA** | 7:1 | 4.5:1 |

## 無障礙設計（Accessibility）

### WCAG 2.1 核心要求

```markdown
## POUR 原則

### Perceivable（可感知）
- [ ] 所有圖片有 alt 文字
- [ ] 色彩不是唯一的資訊傳達方式
- [ ] 對比度符合 AA 標準

### Operable（可操作）
- [ ] 所有功能可用鍵盤操作
- [ ] Focus 狀態明顯
- [ ] 沒有會導致癲癇的閃爍內容

### Understandable（可理解）
- [ ] 語言明確指定
- [ ] 表單有清楚的標籤和錯誤提示
- [ ] 導航一致

### Robust（健壯）
- [ ] 語意化 HTML
- [ ] ARIA 標籤正確使用
- [ ] 跨瀏覽器/輔助工具相容
```

### 常見修復

| 問題 | 解決方案 |
|------|----------|
| 圖片無 alt | `<img alt="描述">` |
| 低對比度 | 使用對比度檢查工具 |
| 無鍵盤導航 | 確保 `tabindex` 正確 |
| 無 focus 指示 | 加入 `:focus` 樣式 |

## 互動設計模式

### 常用模式

```
┌─ 導航模式 ────────────────────────────────────────────────────┐
│  Tab Bar: 3-5 個主要功能（行動裝置）                          │
│  Side Nav: 多層級導航（桌面）                                 │
│  Breadcrumb: 深層結構回溯                                     │
└───────────────────────────────────────────────────────────────┘

┌─ 輸入模式 ────────────────────────────────────────────────────┐
│  Inline Validation: 即時驗證                                  │
│  Progressive Disclosure: 逐步顯示                             │
│  Default Values: 預填合理預設                                 │
└───────────────────────────────────────────────────────────────┘

┌─ 回饋模式 ────────────────────────────────────────────────────┐
│  Toast: 非阻斷式通知                                          │
│  Modal: 需要用戶決策                                          │
│  Skeleton: 載入中佔位                                         │
└───────────────────────────────────────────────────────────────┘
```

## 設計系統元件

### 核心元件清單

```
基礎元件：
├── Button (Primary/Secondary/Ghost)
├── Input (Text/Number/Password)
├── Select/Dropdown
├── Checkbox/Radio
├── Toggle/Switch
└── Icon

複合元件：
├── Card
├── Modal/Dialog
├── Toast/Notification
├── Table
├── Pagination
└── Navigation (Tab/Breadcrumb/Menu)

版面元件：
├── Container
├── Grid
├── Stack
└── Divider
```

## 可用性檢查清單

```markdown
## 上線前檢查

### 導航
- [ ] 用戶知道自己在哪裡
- [ ] 用戶知道可以去哪裡
- [ ] 用戶可以輕鬆返回

### 內容
- [ ] 重要資訊在折疊線之上
- [ ] 文案清晰、無歧義
- [ ] 錯誤訊息有幫助

### 互動
- [ ] 可點擊元素看起來可點擊
- [ ] 操作有回饋
- [ ] 表單驗證即時

### 效能
- [ ] 首次載入 < 3 秒
- [ ] 互動回應 < 100ms
- [ ] 動畫流暢（60fps）
```

## 常見錯誤

| 錯誤 | 正確做法 |
|------|----------|
| 按鈕顏色區分功能 | 用大小/位置/文字區分 |
| Placeholder 當標籤 | 使用獨立的 label |
| 無 hover 狀態 | 所有可互動元素有 hover |
| 自動播放影片 | 需要用戶主動播放 |

## 工具推薦

- **設計**：Figma, Sketch
- **原型**：Figma, ProtoPie
- **協作**：Figma, Zeplin
- **無障礙測試**：axe, WAVE
- **對比度**：WebAIM Contrast Checker

## 相關資源

- [Material Design](https://m3.material.io/)
- [Apple Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/)
- [Nielsen Norman Group](https://www.nngroup.com/articles/)
- [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
