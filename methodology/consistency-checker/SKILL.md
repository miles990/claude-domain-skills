---
name: consistency-checker
version: 1.0.0
description: 內容一致性檢查器 — 確保程式碼、文檔、多來源之間保持一致
triggers: [check, 一致性, consistency, 檢查, sync, 同步]
keywords: [consistency, validation, sync, documentation, code-style, cross-repo, pre-commit]
---

# Consistency Checker v1.0.0

> 確保內容一致性：程式碼風格 → 文檔同步 → 跨 Repo 同步 → AI 輸出驗證

## 快速使用

```bash
/check                      # 檢查當前變更的一致性
/check --pre-commit         # PR/Commit 前完整檢查
/check --full               # 全專案一致性審查
/check --sync repo1 repo2   # 跨 Repo 同步檢查
/check --ai                 # 驗證 AI 輸出一致性
```

## 四大檢查模組

| 模組 | 用途 | 觸發時機 |
|------|------|----------|
| **code-consistency** | 命名、風格、API 一致性 | 開發中、PR 前 |
| **doc-consistency** | 文檔與程式碼同步 | 變更後、PR 前 |
| **cross-repo-sync** | 多 Repo 內容同步 | 跨專案更新時 |
| **output-consistency** | AI 輸出前後一致性 | 生成內容後 |

## 執行流程

```
/check → 判斷範圍 → 執行檢查 → 生成報告 → 有問題則提供修復建議
```

---

## 模組 1: 程式碼一致性 (code-consistency)

### 檢查項目

| 項目 | 說明 |
|------|------|
| **命名規則** | 變數、函數、類別命名是否符合專案慣例 |
| **程式碼風格** | 縮排、括號、分號等格式 |
| **API 一致性** | 相似功能的 API 設計是否一致 |
| **錯誤處理** | Error 類別、錯誤訊息格式 |
| **Import 順序** | 引入順序是否符合慣例 |

### 執行

```bash
/check code                    # 檢查當前變更
/check code src/auth/*.ts      # 檢查特定檔案
/check code --rule naming      # 檢查特定規則
```

---

## 模組 2: 文檔一致性 (doc-consistency)

### 檢查項目

| 項目 | 說明 |
|------|------|
| **README 同步** | README 描述是否與實際功能一致 |
| **API 文檔** | API 文檔是否與實作一致 |
| **SKILL.md** | version、description 是否正確 |
| **註解同步** | 函數註解是否與實作一致 |
| **範例程式碼** | 文檔中的範例是否能執行 |

### 執行

```bash
/check doc                     # 檢查文檔一致性
/check doc README.md           # 檢查特定文檔
/check doc --api               # 檢查 API 文檔
```

---

## 模組 3: 跨 Repo 同步 (cross-repo-sync)

### 檢查項目

| 項目 | 說明 |
|------|------|
| **版本同步** | 多個 Repo 的版本是否一致 |
| **共享檔案** | 相同檔案內容是否同步 |
| **設定同步** | 設定檔是否一致 |
| **依賴同步** | 共同依賴版本是否一致 |

### 執行

```bash
/check sync repo1 repo2              # 比較兩個 Repo
/check sync repo1 repo2 --path skills/  # 指定比較路徑
/check sync repo1 repo2 --version-only  # 僅檢查版本
```

### 同步流程

```
指定來源/目標 → 比對版本 → 比對檔案內容 → 有差異則詢問同步方向 → 執行同步
```

---

## 模組 4: AI 輸出一致性 (output-consistency)

### 檢查項目

| 項目 | 說明 |
|------|------|
| **前後矛盾** | 同一對話中的陳述是否矛盾 |
| **事實一致** | 引用的事實是否正確 |
| **指令一致** | 建議的指令是否真實存在 |
| **格式一致** | 輸出格式是否統一 |

### 執行

```bash
/check ai "要驗證的內容"
/check ai --verify-command "/some-command"  # 驗證指令
/check ai --verify-paths                     # 驗證檔案路徑
```

### 重點：指令驗證

**在建議指令前，務必先透過 context7 查詢官方文檔確認指令存在。**

---

## 整合使用場景

### 場景 1: 開發中

```bash
/check
# → ✅ 命名一致性：通過
# → ⚠️ 發現類似函數 `formatDate` 在 src/utils/time.ts
#    建議：考慮複用現有函數
```

### 場景 2: PR 前

```bash
/check --pre-commit
# → ✅ 程式碼一致性：通過
# → ⚠️ CHANGELOG.md 未更新
#    建議：新增此次變更的說明
```

### 場景 3: 跨 Repo 同步

```bash
/check --sync ~/self-evolving-agent ~/evolve-plugin
# → ❌ 版本不同步
#    self-evolving-agent: v5.2.0
#    evolve-plugin: v5.0.0
#    是否同步？ [Y/n]
```

### 場景 4: AI 輸出驗證

```bash
/check --ai --verify-command "/plugin install"
# → ✅ 指令驗證：/plugin install 存在
#    來源：Claude Code 官方文檔
```

---

## 擴展資源

- 完整範例與模板 → [extended/examples.md](./extended/examples.md)
- CLAUDE.md 配置範例 → [extended/examples.md#claude-md-配置範例](./extended/examples.md#claudemd-配置範例)

---

## 為什麼重要

1. **防止不一致** — 程式碼、文檔、多來源保持同步
2. **減少錯誤** — 提前發現潛在問題
3. **提升品質** — 統一風格和規範
4. **建立信任** — AI 輸出經過驗證更可靠
