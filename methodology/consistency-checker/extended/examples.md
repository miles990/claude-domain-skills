# Consistency Checker - 範例與模板

## 程式碼一致性檢查範例

```python
# 1. 命名一致性檢查
Grep(
    pattern="(function|const|class|interface) [a-z_]+[A-Z]",  # 混用 snake_case 和 camelCase
    path="src/",
    output_mode="content"
)

# 2. 錯誤處理一致性
Grep(
    pattern="throw new (Error|.*Error)\\(",
    path="src/",
    output_mode="content"
)
# 確認是否統一使用專案的 Error 類別

# 3. API 風格一致性
Grep(
    pattern="(get|fetch|retrieve|load)[A-Z]",  # 取得資料的動詞是否統一
    path="src/",
    output_mode="files_with_matches"
)
```

## 文檔一致性檢查範例

```python
# 1. 版本號一致性
# 檢查 SKILL.md、package.json、CHANGELOG 版本是否一致
version_skill = Grep(pattern="^version:", path="SKILL.md")
version_pkg = Read(file_path="package.json")  # 取 version 欄位
# 比對兩者是否相同

# 2. 函數文檔同步
# 檢查 JSDoc/docstring 與實際參數是否一致
Grep(
    pattern="@param|:param",
    path="src/",
    output_mode="content",
    C=5
)

# 3. README 功能列表
# 比對 README 列出的功能與實際 export 的函數
```

## 跨 Repo 同步範例

```bash
# 1. 版本比對
grep "^version:" /path/to/repo1/SKILL.md
grep "^version:" /path/to/repo2/SKILL.md

# 2. 檔案差異
diff -rq /path/to/repo1/skills/ /path/to/repo2/skills/

# 3. 詳細比對
diff /path/to/repo1/skills/SKILL.md /path/to/repo2/skills/SKILL.md
```

## AI 輸出驗證範例

```python
# 1. 指令驗證 - 在建議指令前先確認
# 錯誤示範：直接說「請執行 /install-plugin」
# 正確示範：先驗證指令存在

# 透過 context7 查詢官方文檔
mcp__context7__query-docs(
    libraryId="/anthropics/claude-code",
    query="plugin install command"
)

# 2. 路徑驗證
Bash(command="ls -la /suggested/path 2>/dev/null || echo 'Path not found'")

# 3. 版本驗證
Bash(command="curl -s https://api.github.com/repos/owner/repo/releases/latest | jq -r '.tag_name'")
```

## 檢查報告格式模板

```
┌─────────────────────────────────────────────────────────────────┐
│  🔍 一致性檢查報告                                              │
│                                                                 │
│  專案：[專案名稱]                                               │
│  時間：[時間戳]                                                 │
│  範圍：[當前變更 | 全專案 | 跨 Repo]                           │
│                                                                 │
│  ═══════════════════════════════════════════════════════════   │
│                                                                 │
│  📝 程式碼一致性：[✅ 通過 | ⚠️ 有警告 | ❌ 有錯誤]            │
│     [詳細說明]                                                  │
│                                                                 │
│  📄 文檔一致性：[✅ 通過 | ⚠️ 有警告 | ❌ 有錯誤]              │
│     [詳細說明]                                                  │
│                                                                 │
│  🔄 跨 Repo 同步：[✅ 同步 | ⚠️ 有差異 | ❌ 不同步]            │
│     [詳細說明]                                                  │
│                                                                 │
│  ═══════════════════════════════════════════════════════════   │
│                                                                 │
│  📋 修復建議：                                                  │
│     1. [建議 1]                                                 │
│     2. [建議 2]                                                 │
│                                                                 │
│  總結：[X/Y 項通過]                                             │
└─────────────────────────────────────────────────────────────────┘
```

## CLAUDE.md 配置範例

```yaml
consistency-checker:
  # 啟用/停用模組
  modules:
    code: true
    doc: true
    cross-repo: true
    ai-output: true

  # 自動檢查時機
  auto-check:
    on-save: false        # 儲存時檢查
    pre-commit: true      # Commit 前檢查
    pre-push: false       # Push 前檢查

  # 跨 Repo 同步設定
  sync:
    repos:
      - ~/self-evolving-agent
      - ~/evolve-plugin
    auto-sync: false      # 自動同步（危險）

  # 忽略規則
  ignore:
    - "*.test.ts"
    - "node_modules/"
    - ".git/"
```
