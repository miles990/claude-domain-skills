# Creative → Tech Interface

> 創意領域需求到技術實現的映射

## Domain Skills Covered

- `ui-ux-design` - UI/UX 設計
- `game-design` - 遊戲設計
- `storytelling` - 故事創作
- `visual-media` - 影像創作
- `brainstorming` - 創意發想

## Requirement → Technology Mapping

| Domain Requirement | Technical Implementation | Software Skills |
|-------------------|-------------------------|-----------------|
| 介面設計實作 | React/Vue + CSS | `frontend` |
| 遊戲開發 | Unity/Godot/Phaser | `game-development` |
| 設計系統 | Component Library | `frontend`, `documentation` |
| 互動原型 | Framer/Protopie → Code | `frontend` |
| 動畫效果 | CSS/GSAP/Lottie | `frontend` |
| 響應式設計 | Media Queries + Flexbox/Grid | `frontend` |
| 內容發布 | CMS/Blog Platform | `content-platforms` |
| 遊戲後端 | Multiplayer Server | `backend`, `realtime-systems` |

## Common Combination Patterns

### Pattern 1: Product Designer (Who Codes)

**Focus**: 設計轉實作、設計系統、原型開發

```yaml
domain_skills:
  - ui-ux-design (深度)

software_skills:
  - frontend (必要)
  - documentation (建議)
```

**Use Case**: Design-to-Code、設計系統維護、互動原型

### Pattern 2: Indie Game Developer

**Focus**: 獨立遊戲開發、全端能力

```yaml
domain_skills:
  - game-design (深度)
  - storytelling (基礎)

software_skills:
  - game-development (必要)
  - frontend (建議 - for UI)
```

**Use Case**: 獨立遊戲、Game Jam、原型開發

### Pattern 3: Multiplayer Game Developer

**Focus**: 多人遊戲、即時同步、伺服器架構

```yaml
domain_skills:
  - game-design (深度)

software_skills:
  - game-development (必要)
  - backend (必要)
  - realtime-systems (必要)
  - database (建議)
```

**Use Case**: MMO、多人對戰、即時同步遊戲

### Pattern 4: Content Creator (Tech-Enabled)

**Focus**: 自媒體、內容發布、技術輔助創作

```yaml
domain_skills:
  - storytelling (深度)
  - visual-media (基礎)

software_skills:
  - content-platforms (建議)
  - automation-scripts (可選)
```

**Use Case**: 部落格、電子書、自動化發布

### Pattern 5: Interactive Experience Designer

**Focus**: 互動藝術、數位體驗、創意科技

```yaml
domain_skills:
  - ui-ux-design (基礎)
  - brainstorming (基礎)

software_skills:
  - frontend (必要)
  - game-development (建議)
```

**Use Case**: 互動網站、數位藝術、沉浸式體驗

## Technology Stack Recommendations

### Design Implementation

| Use Case | Recommended Stack |
|----------|------------------|
| Web UI | React/Vue + Tailwind/Styled |
| Design System | Storybook + Component Library |
| 動畫 | Framer Motion / GSAP |
| 3D Web | Three.js / React Three Fiber |

### Game Development

| Use Case | Recommended Stack |
|----------|------------------|
| 2D 遊戲 | Godot / Phaser.js |
| 3D 遊戲 | Unity / Unreal |
| Web 遊戲 | Phaser / PixiJS |
| 多人遊戲後端 | Colyseus / Socket.io |

### Content Publishing

| Use Case | Recommended Stack |
|----------|------------------|
| 部落格 | Next.js + MDX / Ghost |
| CMS | Strapi / Sanity / Contentful |
| 影片 | YouTube API / Cloudflare Stream |

## Creative-Tech Synergies

### Design → Code 轉換流程

```
Figma Design → Design Tokens → Component Code → Production
     ↓              ↓               ↓
  手動設計      JSON/CSS 變數     React/Vue 元件
```

### Game Design → Implementation 流程

```
GDD Document → Prototype → Core Loop → Polish → Ship
     ↓            ↓           ↓         ↓
  遊戲企劃     快速驗證      核心玩法    打磨細節
```

## Anti-Patterns to Avoid

| Anti-Pattern | Problem | Better Approach |
|--------------|---------|-----------------|
| 設計過度交接 | 實作失真 | Designer 參與實作 review |
| 跳過原型 | 核心玩法未驗證 | 先做 paper prototype |
| 過早優化視覺 | 浪費資源 | 先驗證 gameplay |
| 技術限制設計 | 創意受限 | 先想像再評估可行性 |
