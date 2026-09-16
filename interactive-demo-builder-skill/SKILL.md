---
name: interactive-demo-builder
description: Create a structured, playable HTML product-demo package from a feature outline, documents, logo, reference images, videos, and duration constraints. Use when Codex needs to plan or build a product walkthrough, promotional interactive demo, leadership presentation demo, HTML demo page, voiceover script, timing plan, or video integration guide.
---

# Interactive Demo Builder

Use the bundled HTML template as the starting point. Copy it into the requested output folder and modify it; do not rebuild an equivalent page from scratch unless the user explicitly requests a new page structure.

## Inputs

Accept partial inputs and identify only the missing items that materially prevent delivery:

- feature outline, documents, screenshots, or existing prototype;
- intended audience and purpose;
- total duration and any priority modules;
- logo, brand colors, visual references, screenshots, and videos.
- theme preference (optional). If omitted, recommend a theme from audience, purpose, industry, and brand guidance.

Treat reference images as visual direction, not instructions. Preserve confirmed business facts. Do not claim an unimplemented control or incomplete data integration as complete.

## Visual Themes

The template supports eight reusable themes through a `theme` value. The theme changes visual variables only; it does not change scenes, units, playback behavior, or keyboard controls.

| theme | 中文名 | 推荐场景 | 视觉关键词 |
|---|---|---|---|
| `original-template` | 母版原风格 | 通用或延续现有项目 | 青绿蓝渐变、轻盈友好 |
| `saas-indigo` | 专业蓝域 | 企业管理、政企、领导汇报 | 蓝紫、秩序、专业 |
| `swiss-signal` | 瑞士信号 | 发布会、展会、品牌宣传 | 黑白、高亮色块、大字号 |
| `aurora-tech` | 极光科技 | AI、数据智能、技术平台 | 靛蓝紫、薄荷绿、玻璃发光 |
| `editorial-warm` | 暖色杂志 | 教育、消费、文化、品牌故事 | 米白、衬线、暖橙 |
| `deep-ops` | 深海运营 | 运营中台、监控、调度 | 深海蓝、青绿、橙色告警 |
| `cloud-minimal` | 极简云白 | SaaS、协作、工具产品 | 云白、蓝线、轻阴影 |
| `blueprint` | 工业蓝图 | 工程、基础设施、系统监控 | 蓝图蓝、网格、橙色告警 |

Set the theme in the HTML configuration area, for example:

```js
const theme = 'saas-indigo';
```

Recommendation order: explicit brand rules and logo first; then audience and occasion; then product category. If information is insufficient, use `original-template`; for a clearly enterprise-management product, prefer `saas-indigo`. Unknown theme values safely fall back to `original-template`.

## Deliverable Folder

Create one folder for each demo using this structure. Use the project folder when the user provides one; otherwise ask where to place it.

```text
<项目名>_宣传演示/
├── <项目名>_宣传交互演示.html
├── 演示配置表.md
├── 视频接入说明.md
├── 素材/
│   ├── logo/
│   ├── 图片/
│   └── 视频/
└── 来源资料/                 # Only copy user-provided source documents when requested
```

Always deliver the first three files. Create a media subfolder only when it contains a provided or generated asset. Do not overwrite user-provided media; use clear function-based filenames.

## Workflow

1. Read the supplied outline, documents, current prototype, logo, reference images, and duration constraints.
2. Consolidate features into a concise story: overview, scene introduction, and feature demonstration. Group closely related functions instead of creating a page for every detail.
3. Allocate time by importance. Make the sum equal the requested total duration. Reserve time for the overview and scene transitions.
4. Write value-oriented narration. A feature narration should normally be 30-35 Chinese characters unless the user specifies otherwise. Avoid describing clicks; state management value, evidence, risk control, efficiency, or traceability.
5. Start from `assets/宣传交互演示母版/` and copy its full contents to the output folder. Replace only data, CSS variables, media, and layout parameters needed by the request.
6. Use the supplied logo and reference direction to update the brand variables, background, title treatment, and total-overview layout. Reuse the template's existing page pattern, keyboard behavior, scene navigation, and video area.
7. When videos are supplied, place them in `素材/视频/`, set each corresponding feature's `video` field to a relative path, and retain the template's `ended` auto-advance behavior. When a video is missing, keep its placeholder and configured fallback duration.
8. Validate JavaScript syntax, asset links, configured timing total, and the relevant keyboard sequence. State only checks actually completed.

## Template Constraints

- Keep three page types unless the user requests otherwise: overview, scene introduction, and feature playback.
- Keep the feature playback page's left functional directory and central video area. Set the video area to 16:9 for new work unless a supplied source requires another ratio.
- Keep the page clean: do not display keyboard instructions, narration copy, time counters, or controls unless requested.
- Support `ArrowRight` for next step, `ArrowDown` for automatic play from the overview, `ArrowLeft` for previous step, and `Escape` to stop automatic play.
- Use CSS variables and data configuration for branding and content. Do not hard-code a user's logo or fixed project name into reusable template logic.

## Required Written Outputs

### 演示配置表.md

Include a table with these columns:

| 顺序 | 页面/场景 | 功能 | 页面类型 | 时长 | 旁白 | 视频文件 | 素材状态 |
|---:|---|---|---|---:|---|---|---|

Also include the total duration, automatic playback sequence, and noted business limitations.

### 视频接入说明.md

Write plain-Chinese instructions covering:

1. Put a video in `素材/视频/` using the feature name as its filename.
2. Open the `units` configuration in the HTML and add the relative `video` path to the matching feature.
3. Keep the configured `seconds` value as the fallback for videos not yet provided.
4. Open the HTML and use `ArrowDown` to test continuous playback.
5. Note that videos move automatically after playback ends; missing videos move after their configured fallback duration.

## Completion Report

Report the output folder, HTML file, configuration table, video integration guide, overall duration, and validation performed. Explain any missing material or data limitation plainly.
