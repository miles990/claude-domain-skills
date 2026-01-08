# Business → Tech Interface

> 商業領域需求到技術實現的映射

## Domain Skills Covered

- `business-strategy` - 商業策略
- `product-management` - 產品管理
- `project-management` - 專案管理
- `marketing` - 數位行銷
- `sales` - 銷售與電商

## Requirement → Technology Mapping

| Domain Requirement | Technical Implementation | Software Skills |
|-------------------|-------------------------|-----------------|
| PRD 撰寫 | Markdown + Notion/Confluence | `documentation` |
| API 規格設計 | OpenAPI/GraphQL Schema | `api-design` |
| 數據追蹤 | Analytics + ETL Pipeline | `data-analysis`, `database` |
| 電商系統 | E-commerce Platform | `e-commerce`, `backend` |
| 專案追蹤 | JIRA/Linear + Git | `git-workflows`, `documentation` |
| 行銷自動化 | Marketing Automation Tools | `automation-scripts` |
| A/B 測試 | Feature Flags + Analytics | `testing-strategies`, `data-analysis` |
| CRM 整合 | API Integration | `api-design`, `backend` |

## Common Combination Patterns

### Pattern 1: Tech Product Manager

**Focus**: 技術產品規格、API 設計、跨部門協調

```yaml
domain_skills:
  - product-management (深度)
  - project-management (基礎)

software_skills:
  - documentation (必要)
  - api-design (必要)
  - git-workflows (建議)
```

**Use Case**: SaaS 產品開發、平台 API 規劃

### Pattern 2: Growth Marketer

**Focus**: 數據驅動行銷、轉換優化、用戶增長

```yaml
domain_skills:
  - marketing (深度)
  - sales (基礎)

software_skills:
  - data-analysis (必要)
  - automation-scripts (建議)
```

**Use Case**: 用戶獲取、轉換漏斗優化、A/B 測試

### Pattern 3: E-commerce Operator

**Focus**: 電商營運、訂單管理、庫存系統

```yaml
domain_skills:
  - sales (深度)
  - marketing (基礎)

software_skills:
  - e-commerce (必要)
  - database (建議)
  - backend (建議)
```

**Use Case**: 電商網站、購物車、支付整合

### Pattern 4: Scrum Master / Tech Lead

**Focus**: 敏捷開發、團隊協作、技術管理

```yaml
domain_skills:
  - project-management (深度)
  - product-management (基礎)

software_skills:
  - git-workflows (必要)
  - documentation (必要)
  - devops-cicd (建議)
```

**Use Case**: 軟體專案管理、Sprint 規劃、技術決策

## Technology Stack Recommendations

### Documentation & Collaboration

| Use Case | Recommended Stack |
|----------|------------------|
| PRD/Spec | Notion / Confluence / Markdown |
| API Docs | OpenAPI + Stoplight / Readme |
| 專案管理 | JIRA / Linear / GitHub Projects |

### Analytics & Data

| Use Case | Recommended Stack |
|----------|------------------|
| 網站分析 | Google Analytics / Mixpanel |
| 產品分析 | Amplitude / PostHog |
| 數據倉儲 | BigQuery / Snowflake |

### Marketing Tech

| Use Case | Recommended Stack |
|----------|------------------|
| Email 行銷 | SendGrid / Mailchimp |
| CRM | HubSpot / Salesforce |
| A/B 測試 | Optimizely / LaunchDarkly |

### E-commerce

| Use Case | Recommended Stack |
|----------|------------------|
| 平台 | Shopify / WooCommerce / 自建 |
| 支付 | Stripe / 綠界 / TapPay |
| 庫存 | Custom + ERP Integration |

## Anti-Patterns to Avoid

| Anti-Pattern | Problem | Better Approach |
|--------------|---------|-----------------|
| 無數據追蹤 | 無法衡量成效 | 先建立追蹤再做決策 |
| PRD 太模糊 | 開發理解落差 | 使用具體 User Story + AC |
| 技術債累積 | 長期開發效率低 | 納入重構到 Backlog |
| 過度工程 | MVP 延期 | 先求有再求好 |
