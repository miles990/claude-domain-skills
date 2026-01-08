# Lifestyle → Tech Interface

> 生活領域需求到技術實現的映射

## Domain Skills Covered

- `personal-growth` - 人生規劃與個人成長
- `side-income` - 副業與被動收入

## Requirement → Technology Mapping

| Domain Requirement | Technical Implementation | Software Skills |
|-------------------|-------------------------|-----------------|
| 自媒體平台 | Blog/YouTube/Podcast | `content-platforms` |
| 電商副業 | E-commerce Platform | `e-commerce` |
| 知識產品 | Course Platform | `content-platforms`, `frontend` |
| 自動化工作流 | Automation Tools | `automation-scripts` |
| 個人品牌網站 | Portfolio/Landing Page | `frontend` |
| 財務追蹤 | Spreadsheet/App | `data-analysis` |

## Common Combination Patterns

### Pattern 1: Content Creator (自媒體創作者)

**Focus**: 內容創作、自媒體經營、流量變現

```yaml
domain_skills:
  - side-income (深度)
  - personal-growth (基礎)

software_skills:
  - content-platforms (必要)
  - automation-scripts (建議)
```

**Use Case**: YouTube、部落格、Podcast 經營

### Pattern 2: E-commerce Side Hustle (電商副業)

**Focus**: 電商創業、產品銷售、供應鏈管理

```yaml
domain_skills:
  - side-income (深度)

software_skills:
  - e-commerce (必要)
  - automation-scripts (建議)
```

**Use Case**: 蝦皮、自建電商、Dropshipping

### Pattern 3: Knowledge Product Creator (知識產品創作者)

**Focus**: 線上課程、電子書、顧問服務

```yaml
domain_skills:
  - side-income (深度)
  - personal-growth (基礎)

software_skills:
  - content-platforms (必要)
  - frontend (建議)
```

**Use Case**: 線上課程、會員訂閱、電子書

## Technology Stack Recommendations

### Content Platforms

| Use Case | Recommended Stack |
|----------|------------------|
| 部落格 | Ghost / WordPress / Medium |
| 課程 | Teachable / Gumroad / 自建 |
| 會員 | Patreon / Substack |

### E-commerce

| Use Case | Recommended Stack |
|----------|------------------|
| 平台 | Shopify / 蝦皮 |
| 自建 | WooCommerce / Next.js Commerce |
| 數位產品 | Gumroad / Lemonsqueezy |

### Automation

| Use Case | Recommended Stack |
|----------|------------------|
| 工作流 | Zapier / Make |
| 排程 | Buffer / Hootsuite |
| 自動化 | n8n / Custom Scripts |

## Anti-Patterns to Avoid

| Anti-Pattern | Problem | Better Approach |
|--------------|---------|-----------------|
| 過早優化技術 | 浪費時間 | 先驗證產品市場適配 |
| 沒有追蹤數據 | 無法優化 | 從 Day 1 建立追蹤 |
| 過度依賴平台 | 風險集中 | 建立自有渠道 |
