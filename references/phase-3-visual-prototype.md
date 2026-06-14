# Phase 2: 视觉探索 / visual-prototype

Use this phase immediately after the PRD. Generate high-fidelity primary-page UI effect images first, before writing the full UI Spec. The visual direction is then approved or revised, and the approved version becomes the basis for UI Spec.

## Inputs

Use:

- Stage-1 PRD.
- Page/module requirements from the PRD.
- User-provided visual references, screenshots, brand rules, or style notes.
- Any target platform: desktop admin, mobile app, web app, data dashboard, large-screen display.

If the user provides image references or a reference-image folder, inspect them before writing prompts.

## Visual Reference Intake

Before defining style, check whether the user provided reference images or a reference-image folder.

Priority:

1. Use user-provided reference images to extract style direction.
2. If reference images are absent, derive a style from the PRD, industry domain, target users, and product tone.
3. If the user provided multiple references, synthesize shared rules instead of copying one image blindly.

Extract from references:

- Layout shell: sidebar/topbar/tab layout, card density, content rhythm.
- Color system: primary color, neutrals, accents, status colors.
- Typography: scale, weight, information density.
- Components: table, card, form, chart, status tag, navigation, dialog, drawer.
- Interaction tone: enterprise, operational, data-heavy, lightweight, mobile-first, command-center, etc.
- Avoid list: visual traits that should not be copied or that clash with the product.

Separate style from structure:

- Reference images provide visual style, density, component treatment, and interaction tone.
- The PRD controls business content, page goals, modules, and information priority.
- Do not copy a reference image's business content unless it matches the current PRD.

Record the source of the style:

```markdown
## 视觉风格来源

- 参考图片：有/无
- 提取出的风格关键词：
- 布局特征：
- 色彩特征：
- 组件特征：
- 不采用的特征：
```

## Decide Visual Scope

Default to `primary pages first`.

Primary pages are module entry or representative pages. They show each major module's core task, information hierarchy, and visual/interaction pattern. They are used for human approval before expanding to subpages or writing the UI Spec.

Primary pages usually include:

- Workbench / dashboard.
- One entry page for each major navigation/business module.
- One representative core workflow page when process handling is central.
- One analytics/reporting entry page when data insight is central.
- One mobile home/task page when the product has a mobile side.

Do not generate every child page, detail page, edit page, drawer, modal, rare state, or secondary settings page in the first batch.

Use `full page set` only after:

- The user explicitly asks for all pages and confirms no approval gate is needed, or
- The primary-page batch has been approved.

## Approval Gate

After the first primary-page batch:

1. Stop and ask for approval.
2. If approved, write the UI Spec from the approved visuals and PRD.
3. If the user gives revision comments, redesign according to those comments.
4. If the user says it is not good but gives no specific comments, generate a second visual direction with clear differences in layout, density, color, and component treatment.

Do not move into UI Spec, child-page expansion, or HTML/code implementation before this approval unless the user explicitly asks to skip approval.

## Visual System

Record the visual system in every prompt:

```text
Style: modern high-fidelity commercial lightweight admin UI.
Primary color: [color].
Secondary colors: [colors].
Background: [background].
Cards: [radius, shadow].
Buttons: [primary, secondary].
Icons: flat linear icons.
Language: [language].
Consistency: same navigation, topbar, spacing, cards, table style, status tags, and typography across pages.
Avoid: watermark, browser chrome, decorative orbs, random gradients, inconsistent palettes, unreadable text.
```

## Optional Visual Parameters

Use these only when the user supplies them or asks to tune style. Otherwise infer from the PRD and reference images:

```text
DESIGN_VARIANCE: [1-10; 1 = stable/conventional, 10 = distinctive/asymmetrical/brand-forward]
VISUAL_DENSITY: [1-10; 1 = spacious/editorial, 10 = dense operational/dashboard]
MOTION_INTENSITY: [1-10; 1 = subtle states, 10 = rich motion; mainly affects implementation guidance]
```

For enterprise/admin products, prefer moderate design variance, medium-high visual density, and low motion intensity unless the user asks otherwise.

For backend/admin systems, avoid marketing landing-page layouts. Prefer:

- Fixed sidebar.
- Topbar with breadcrumb, search, notifications, avatar.
- White cards on light gray background.
- Filter bars.
- Dense but readable tables.
- KPI cards where useful.
- Status tags and row actions.
- Drawer/detail cards for workflows.

## Prompt Templates

Use the strict prompt by default. Use the quick prompt only when the user explicitly wants a short prompt.

### Quick Admin UI Image Prompt

Use this as the base for each generated desktop/admin page. Vary only the business content.

```text
Use case: ui-mockup
Asset type: 1440x1024 desktop admin screenshot
Primary request: 生成“[产品名称]”产品“[页面名称]”页面 UI 效果图。
Style: 现代、高保真、商业化、真实可上线，轻量化后台管理风格。主色调 [主色]，辅助色 [辅助色]。浅灰背景 + 白色卡片，卡片圆角 12px，轻阴影。蓝底白字主按钮，白底蓝字次按钮。扁平化线性图标。简体中文专业管理短句。
Layout: 左侧固定导航栏，顶部栏包含面包屑、搜索、消息、用户头像。当前导航高亮“[模块名]”。
Page content: [根据 PRD 写页面标题、筛选、按钮、表格/卡片/图表/流程/表单/详情区]。
Composition: crisp high fidelity SaaS/admin interface, dense but readable, realistic product UI.
Constraints: 与其他页面保持同一品牌视觉系统；不要浏览器外壳；不要水印；不要营销首页；不要装饰性渐变光球；文字清晰可读。
```

### Strict Admin UI Image Prompt

Use this for normal desktop/admin UI effect image generation. It forces the agent to use PRD content, reference-image style extraction, primary-page scope, and approval gating.

```text
Use case: ui-mockup
Asset type: 1440x1024 desktop admin screenshot

Primary request:
生成“[产品名称]”产品“[页面名称]”首要页面高保真 UI 效果图。

Workflow stage:
这是第 2 阶段“视觉探索 / visual-prototype”。当前任务只生成首要页面效果图，用于人工审批视觉方向；不要生成 UI Spec，不要生成 HTML/code，不要扩展所有子页面。

Source of truth:
必须基于 PRD 中的页面需求、核心任务、目标用户、关键动作、P0/P1/P2 信息优先级、模块清单、数据对象和业务状态生成。
不要复制参考图中的业务内容，参考图只用于风格提炼。

Visual reference:
[如果用户提供参考图，写明参考图风格提炼结果：布局、色彩、组件、信息密度、卡片/表格/按钮/标签/图表风格。]
[如果没有参考图，写明：无参考图，根据 PRD 的行业属性、用户角色和产品气质推导视觉风格。]

Optional parameters:
- DESIGN_VARIANCE：[未提供则按产品类型推导]
- VISUAL_DENSITY：[未提供则按 PRD 的信息密度推导]
- MOTION_INTENSITY：[未提供则后台/管理系统默认较低]

Unified style:
- 现代、高保真、商业化、真实可上线。
- 后台/SaaS/业务系统风格，不是营销落地页。
- 主色：[主色]；辅助色：[辅助色]；状态色：[成功/警告/错误/信息色]。
- 背景：[浅灰/白色/深色/其他]。
- 卡片：[圆角、阴影、边框、留白]。
- 按钮：[主按钮、次按钮、危险操作、禁用态]。
- 图标：[线性/面性/双色/其他]。
- 字体与信息密度：[紧凑/适中/宽松]。
- 语言：简体中文，使用专业、真实、短句式产品文案。

Layout:
- 左侧固定导航栏，体现产品主要模块。
- 顶部栏包含面包屑、搜索、消息/通知、用户头像。
- 当前导航高亮“[模块名]”。
- 页面标题区清楚表达当前页面任务。
- 主内容区根据页面任务组织为卡片、表格、筛选区、图表、流程、表单、详情区或任务列表。
- 保持栅格、间距、对齐和信息层级稳定。

Page content:
- 页面名称：[页面名称]
- 页面核心任务：[从 PRD 提取]
- 目标用户：[从 PRD 提取]
- 关键用户动作：[从 PRD 提取]
- P0 主信息：[从 PRD 提取，必须醒目呈现]
- P1 次信息：[从 PRD 提取]
- P2 补充信息：[从 PRD 提取，可弱化呈现]
- 必须出现的模块：[模块列表]
- 必须出现的数据样例：[真实感中文数据，不要 lorem ipsum]
- 必须出现的状态/标签：[如待处理、进行中、已完成、异常、风险、启用/停用等]
- 必须出现的操作：[新增、编辑、查看、筛选、导出、提交、审批、重试等，按 PRD 选择]

Component requirements:
- 筛选/搜索区要真实可用。
- 表格或卡片列表要有真实字段、状态标签和行操作。
- KPI/图表只在页面任务需要时出现，不要为了装饰强行添加。
- 重要状态要有视觉区分，但不要过度花哨。
- 如果页面需要四状态表达，可在局部体现 normal/loading/empty/error 中最相关的状态提示。

Primary-page scope:
- 这是模块首要页面或代表页，必须体现该模块的核心信息架构和可复用组件。
- 不要生成新增页、编辑页、详情页、弹窗、抽屉、罕见状态页，除非 PRD 明确要求该页面就是首要页面。

Constraints:
- 不要浏览器外壳。
- 不要水印。
- 不要营销首页。
- 不要装饰性渐变光球。
- 不要随机插画堆砌。
- 不要英文占位符。
- 不要无意义图表。
- 不要与 PRD 无关的模块。
- 文字必须清晰可读，不能拥挤、重叠或溢出。

Output intent:
这张图用于人工审批视觉方向。生成后必须停下来等待用户确认；用户确认后才写 UI Spec 或扩展子页面。
```

### Quick Mobile UI Image Prompt

Use this for mobile app screens:

```text
Use case: ui-mockup
Asset type: 390x844 mobile app screenshot
Primary request: 生成“[产品名称]”移动端“[页面名称]”页面 UI 效果图。
Style: 与后台端同品牌系统，主色 [主色]，浅灰背景，白色卡片，圆角 12px，轻阴影，线性图标，简体中文。
Layout: 顶部标题栏，核心数据卡片，任务列表/表单/快捷入口，底部导航。
Page content: [移动端核心操作和信息]。
Constraints: 文本不可拥挤，按钮适合触控，信息层级清晰，不要浏览器外壳，不要水印。
```

### Strict Mobile UI Image Prompt

Use this when generating mobile primary-page UI effects.

```text
Use case: ui-mockup
Asset type: 390x844 mobile app screenshot

Primary request:
生成“[产品名称]”移动端“[页面名称]”首要页面高保真 UI 效果图。

Workflow stage:
这是第 2 阶段“视觉探索 / visual-prototype”。只生成移动端首要页面效果图用于审批；不要写 UI Spec，不要写 HTML/code。

Source of truth:
基于 PRD 中的目标用户、核心场景、关键动作、P0/P1/P2 信息优先级、数据对象和状态规则生成。

Visual reference:
[有参考图则提炼布局、色彩、卡片、按钮、图标、信息密度。无参考图则根据 PRD 推导。]

Optional parameters:
- DESIGN_VARIANCE：[未提供则按产品类型推导]
- VISUAL_DENSITY：[未提供则按 PRD 的信息密度推导]
- MOTION_INTENSITY：[未提供则移动端保持克制]

Style:
- 与产品整体品牌一致。
- 主色：[主色]；辅助色：[辅助色]。
- 背景：[背景规则]。
- 白色或浅色卡片，圆角 [数值]，轻阴影。
- 线性图标或与参考图一致的图标风格。
- 简体中文，短句、清晰、真实。

Layout:
- 顶部标题栏体现当前页面任务。
- 首屏必须呈现 P0 核心信息。
- 根据场景使用核心数据卡片、任务列表、快捷入口、表单、状态提示或底部导航。
- 触控区域足够大，按钮和列表项不能拥挤。

Page content:
- 页面名称：[页面名称]
- 页面核心任务：[从 PRD 提取]
- 目标用户：[从 PRD 提取]
- 关键动作：[从 PRD 提取]
- 必须出现的模块：[模块列表]
- 必须出现的数据样例：[真实感中文数据]
- 必须出现的状态/标签：[状态列表]

Constraints:
- 不要浏览器外壳。
- 不要水印。
- 不要桌面后台缩小版。
- 不要文字拥挤、重叠或不可读。
- 不要与 PRD 无关的功能。

Output intent:
用于审批移动端视觉方向。生成后停下来等待确认。
```

## Prompt Pack Structure

When the user asks for prompts instead of direct images, produce:

```markdown
# 02-视觉风格与首要页面效果图

## 1. 视觉风格来源
## 2. 统一视觉系统
## 3. 首要页面清单
## 4. 全局禁止事项
## 5. 页面级提示词
### 5.1 [页面名称]
## 6. 审批记录
```

Each page prompt must include:

- Product and page name.
- Platform and target size.
- Visual reference extraction or derived visual system.
- Layout shell.
- Actual page content from PRD.
- States or business labels.
- Constraints.

## Image Generation Workflow

When the user asks for UI effect images:

1. Generate one image per primary page in the first batch.
2. Use one prompt per image because each page has distinct content.
3. Keep navigation, topbar, spacing, cards, table style, status tags, and typography consistent.
4. Stop for approval before writing UI Spec, generating child pages, or implementing HTML/code.
5. Save generated images into the user's project folder, usually:

```text
mockups/
```

6. Use stable numbered names:

```text
01-primary-[模块名]-[页面名称].png
02-primary-[模块名]-[页面名称].png
```

7. Audit actual files before final response.

## Visual Verification Before Handoff

Check:

- Is every generated page traceable to the PRD?
- Does the page support its core task?
- Are P0/P1 information priorities visible?
- Is the product shell consistent?
- Are labels readable?
- Are there watermarks, browser chrome, random decorative elements, or inconsistent palettes?
- Are status tags, tables, forms, filters, and actions realistic for the product?
- Has the primary-page batch been approved before UI Spec, subpages, or implementation?
