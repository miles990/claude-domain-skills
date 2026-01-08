# Domain → Tech Interfaces

> 領域知識到技術實現的橋樑

## Overview

這些接口文件幫助 AI 和開發者理解：
- 領域需求如何對應到技術實現
- 推薦的 software-skills 組合
- 常見的工作模式 (Patterns)
- 應避免的反模式 (Anti-patterns)

## Interface Files

| File | Domain Skills | Focus |
|------|--------------|-------|
| [finance-to-tech.md](./finance-to-tech.md) | quant-trading, investment-analysis | 量化交易、投資分析 |
| [business-to-tech.md](./business-to-tech.md) | product-management, project-management, marketing, sales, business-strategy | 產品、專案、行銷、銷售 |
| [creative-to-tech.md](./creative-to-tech.md) | ui-ux-design, game-design, storytelling, visual-media, brainstorming | 設計、遊戲、創作 |
| [lifestyle-to-tech.md](./lifestyle-to-tech.md) | personal-growth, side-income | 個人成長、副業 |
| [professional-to-tech.md](./professional-to-tech.md) | research-analysis, knowledge-management | 研究、知識管理 |

## Usage

### For AI Agents (recommend_skills)

當 MatchingEngine 匹配到 domain skill 後，可參考對應的接口文件來：
1. 確定需要哪些 software-skills
2. 選擇適合的 Pattern
3. 推薦技術棧

### For Developers

了解特定領域任務需要哪些技術能力，規劃學習路徑。

## File Structure

每個接口文件包含：

```markdown
# Domain → Tech Interface

## Domain Skills Covered
[列出涵蓋的 domain skills]

## Requirement → Technology Mapping
[需求對應技術的表格]

## Common Combination Patterns
[常見的 skill 組合模式]

## Technology Stack Recommendations
[技術棧建議]

## Anti-Patterns to Avoid
[應避免的反模式]
```
