# Tech Spec Generator - Examples

> 完整使用範例，展示不同類型設計文件的轉換流程

---

## 1. GDD (遊戲設計文件) 轉換範例

### 輸入

```bash
/tech-spec-gen docs/design/GDD-MASTER.md
```

### 執行過程

```
Step 1: 文件解析
├── 偵測文件類型：GDD (遊戲設計文件)
├── 識別 Feature Documents: 5 個
│   ├── card-system.md
│   ├── battle-system.md
│   ├── progression.md
│   ├── deck-building.md
│   └── meta-game.md
└── 識別設計支柱：3 個

Step 2: 技術分析
├── 現有技術棧：Flutter 3.38+ / Flame / Dart
├── 識別系統模組：12 個
└── 技術決策點：5 個

Step 3: 架構設計
├── 核心架構：ECS + State Machine
├── 資料模型：8 個實體
└── 核心 API：24 個

Step 4: 任務分解
├── Phase 1 (Foundation): 6 tasks
├── Phase 2 (Core): 8 tasks
├── Phase 3 (Features): 9 tasks
└── Phase 4 (Integration): 4 tasks

Step 5: 產出
├── tech-spec.md (主規格)
├── tasks/*.md (27 個任務規格)
└── adr/*.md (5 個決策記錄)
```

### GDD 章節映射表

| GDD 章節 | 技術規格對應 |
|----------|-------------|
| 設計支柱 | ADR (架構約束) |
| 核心玩法 | 系統架構 + 狀態機 |
| 遊戲機制 | API 設計 + 業務邏輯 |
| 數值設計 | 常數定義 |
| 角色設計 | Entity Schema |
| UI/UX | 畫面狀態機 |

---

## 2. PRD (產品需求文件) 轉換範例

### 輸入

```bash
/tech-spec-gen docs/PRD-v1.md
```

### 執行過程

```
Step 1: 文件解析
├── 偵測文件類型：PRD (產品需求文件)
├── 識別用戶故事：15 個
├── 識別功能列表：8 個模組
└── 識別成功指標：5 個 KPI

Step 2: 技術分析
├── 建議技術棧：Next.js / TypeScript / PostgreSQL
├── 識別功能模組：8 個
└── 技術決策點：3 個

Step 3: 架構設計
├── 核心架構：Clean Architecture
├── 資料模型：12 個實體
└── 核心 API：36 個端點

Step 4: 任務分解
├── Phase 1 (Foundation): 5 tasks
├── Phase 2 (Core): 12 tasks
├── Phase 3 (Features): 10 tasks
└── Phase 4 (Polish): 5 tasks

Step 5: 產出
└── 產生技術規格於 docs/tech-spec/
```

### PRD 章節映射表

| PRD 章節 | 技術規格對應 |
|----------|-------------|
| 問題定義 | 專案目標 (驗收標準) |
| 用戶故事 | 功能模組 + API |
| 功能列表 | 任務分解 |
| 成功指標 | 效能驗收標準 |
| 限制條件 | ADR |

---

## 3. FRD (功能需求文件) 轉換範例

### 輸入

```bash
/tech-spec-gen docs/api-requirements.md --type frd
```

### 執行過程

```
Step 1: 文件解析
├── 文件類型：FRD (功能需求文件)
├── 識別 API 端點：24 個
├── 識別業務規則：18 條
└── 識別資料需求：6 個實體

Step 2: 技術分析
├── 建議技術棧：FastAPI / Python / MongoDB
├── 識別服務模組：6 個
└── 技術決策點：2 個

Step 3-5: [略]
```

### FRD 章節映射表

| FRD 章節 | 技術規格對應 |
|----------|-------------|
| 功能描述 | API 設計 |
| 業務規則 | 業務邏輯 + 驗證規則 |
| 數據要求 | 資料模型 |
| 介面需求 | 外部整合 |
| 例外處理 | 錯誤處理策略 |

---

## 4. 任務管理範例

### 查看任務清單

```bash
/tech-spec-gen tasks

# 輸出：
Task ID | Name              | Priority | Status    | Dependencies
--------|-------------------|----------|-----------|-------------
T001    | 專案初始化         | P0       | completed | -
T002    | 核心資料模型       | P0       | completed | T001
T003    | 認證模組           | P1       | in-progress | T002
T004    | 卡牌系統           | P1       | pending   | T002
T005    | 戰鬥系統           | P1       | pending   | T002, T004
```

### 查看特定任務

```bash
/tech-spec-gen tasks T004

# 輸出任務詳細規格...
```

### 建立 Worktree

```bash
/tech-spec-gen worktree T004

# 執行動作：
# 1. git worktree add ../myproject-T004 -b feature/T004-card-system
# 2. cd ../myproject-T004
# 3. 複製 TASK-SPEC.md 到 worktree
# 4. 建立 .claude/context.md

# 輸出：
Worktree created at: ../myproject-T004
Branch: feature/T004-card-system
Task spec: TASK-SPEC.md
Ready to implement!
```

### 更新任務狀態

```bash
/tech-spec-gen tasks T004 --status completed

# 輸出：
Task T004 marked as completed.
Next available tasks:
- T005: 戰鬥系統 (dependencies: T002, T004 ✓)
```

---

## 5. Worktree 工作流程完整範例

```bash
# 1. 查看可執行的任務
/tech-spec-gen tasks --available

# 2. 選擇任務並建立 worktree
/tech-spec-gen worktree T006

# 3. 進入 worktree 目錄
cd ../myproject-T006

# 4. 查看任務規格
cat TASK-SPEC.md

# 5. [AI Agent 在 worktree 中實作]
# ... 實作過程 ...

# 6. 驗證完成
/tech-spec-gen verify T006

# 7. 合併回主分支
git checkout main
git merge feature/T006-xxx
git worktree remove ../myproject-T006

# 8. 更新任務狀態
/tech-spec-gen tasks T006 --status completed
```

---

## 6. 產出檔案結構範例

```
docs/
├── design/                  # 原有設計文件
│   ├── GDD-MASTER.md
│   └── features/
│       ├── card-system.md
│       └── battle-system.md
└── tech-spec/               # 產生的技術規格
    ├── tech-spec.md         # 主規格文件
    ├── architecture.md      # 架構詳述 (可選)
    ├── data-models.md       # 資料模型詳述 (可選)
    ├── api-reference.md     # API 參考 (可選)
    ├── tasks/               # 任務規格
    │   ├── README.md        # 任務索引與依賴圖
    │   ├── T001-project-setup.md
    │   ├── T002-core-models.md
    │   ├── T003-auth-module.md
    │   └── ...
    └── adr/                 # 架構決策記錄
        ├── ADR-001-ecs-pattern.md
        ├── ADR-002-state-management.md
        └── ...
```
