# Professional → Tech Interface

> 專業技能領域需求到技術實現的映射

## Domain Skills Covered

- `research-analysis` - 研究分析
- `knowledge-management` - 知識管理

## Requirement → Technology Mapping

| Domain Requirement | Technical Implementation | Software Skills |
|-------------------|-------------------------|-----------------|
| 研究報告 | Markdown/LaTeX | `documentation` |
| 數據分析 | Python/R | `data-analysis`, `python` |
| 文獻管理 | Zotero/Mendeley | `documentation` |
| 知識庫系統 | Obsidian/Notion | `documentation` |
| 視覺化報告 | Charts/Dashboards | `data-analysis`, `frontend` |
| 問卷系統 | Survey Tools | `automation-scripts` |

## Common Combination Patterns

### Pattern 1: Data-Driven Researcher

**Focus**: 量化研究、數據分析、統計驗證

```yaml
domain_skills:
  - research-analysis (深度)

software_skills:
  - documentation (必要)
  - data-analysis (必要)
  - python (建議)
```

**Use Case**: 市場調研、競品分析、學術研究

### Pattern 2: Knowledge Worker (知識工作者)

**Focus**: 知識積累、個人知識系統、輸出能力

```yaml
domain_skills:
  - knowledge-management (深度)
  - research-analysis (基礎)

software_skills:
  - documentation (必要)
```

**Use Case**: 第二大腦建構、知識萃取、內容創作

### Pattern 3: Consultant / Analyst

**Focus**: 專業分析、報告撰寫、客戶溝通

```yaml
domain_skills:
  - research-analysis (深度)
  - knowledge-management (基礎)

software_skills:
  - documentation (必要)
  - data-analysis (必要)
```

**Use Case**: 管理顧問、產業分析師、策略研究

## Technology Stack Recommendations

### Research & Analysis

| Use Case | Recommended Stack |
|----------|------------------|
| 數據分析 | Python + Pandas + Jupyter |
| 統計分析 | R / Python statsmodels |
| 視覺化 | Matplotlib / Seaborn / Plotly |
| 報告 | Markdown + Pandoc / LaTeX |

### Knowledge Management

| Use Case | Recommended Stack |
|----------|------------------|
| 個人筆記 | Obsidian / Logseq |
| 團隊知識庫 | Notion / Confluence |
| 文獻管理 | Zotero / Mendeley |
| 寫作發布 | Markdown + Static Site |

### Survey & Data Collection

| Use Case | Recommended Stack |
|----------|------------------|
| 問卷 | Typeform / Google Forms |
| 質性分析 | NVivo / Atlas.ti |
| 訪談整理 | Otter.ai + Notion |

## Anti-Patterns to Avoid

| Anti-Pattern | Problem | Better Approach |
|--------------|---------|-----------------|
| 只收集不產出 | 知識無法變現 | 設定輸出目標 |
| 工具過多 | 分散注意力 | 精簡核心工具 |
| 無結構化 | 難以檢索 | 建立標籤/連結系統 |
| 孤立筆記 | 無法產生洞察 | 建立筆記間連結 |
