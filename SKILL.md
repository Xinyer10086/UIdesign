---
name: ai-ui-design-toolkit
description: >-
  Visual-first UI design toolbox for Chinese product/UI work. Use when Codex needs PRD writing, reference-image style extraction, primary-page high-fidelity UI effect images, UI Spec after visual approval, frontend implementation, screenshot comparison, redesign auditor, or delivery archive. Especially use when the user wants UI effect images before UI Spec, primary-page approval before expanding subpages, or end-to-end UI design pipeline rather than a single linear workflow.
  Do NOT use for: writing UI Spec or HTML before visual approval; generating every subpage before primary-page sign-off; inventing unconfirmed business rules.
---

# AI UI Design Toolkit

Use this skill as a toolbox for AI-assisted UI design. It has a recommended visual-first workflow, but it should be used as a set of composable tools rather than a rigid linear script.

Recommended default path:

```text
需求/PRD -> 首要页面高保真效果图 -> 人工审批 -> UI Spec -> 组件化实现 -> 截图对比修正 -> 交付沉淀
```

Do not invert this into `PRD -> UI Spec -> HTML`. The user's intended workflow is to see the visual direction first, then write the UI Spec from the approved visual direction.

## Toolkit Tools

| Tool | Use when | Main artifact |
| --- | --- | --- |
| Requirement Builder | Raw feature lists, docs, notes, screenshots need to become product requirements | PRD / 需求文档 |
| Reference Style Extractor | User provides reference images or a style folder | 视觉风格提炼 |
| Primary Page Image Generator | Need first visual direction before UI Spec | 首要页面高保真效果图 |
| UI Spec Writer | Visual direction is approved and needs implementation-ready spec | UI Spec |
| Brand/Visual System Kit | Need colors, type, components, status tags, page shell rules | 视觉系统 / design tokens |
| Frontend Implementation Guide | User explicitly asks for code/runnable pages | 组件化实现说明或代码 |
| Screenshot Verification | Implementation or generated visual needs comparison and correction | 截图对比报告 |
| Redesign Auditor | Existing UI needs diagnosis and improvement | UI 问题审计与重设计方向 |
| Delivery Archivist | Need package, naming, reuse, and handoff | 交付清单 |

## Optional Parameters

Use these only when the user asks to tune taste/style. If the user does not provide them, infer conservative defaults from the PRD, reference images, and product domain.

| Parameter | Range | Meaning | Default |
| --- | --- | --- | --- |
| `DESIGN_VARIANCE` | 1-10 | Low means stable/conventional; high means more distinctive, asymmetrical, experimental, or brand-forward | 5 |
| `VISUAL_DENSITY` | 1-10 | Low means spacious/editorial; high means dense dashboards, tables, operational tools | derive from PRD |
| `MOTION_INTENSITY` | 1-10 | Low means subtle hover/state changes; high means stronger transitions and scroll/micro-interactions | 2 for enterprise tools |

## Six-Stage Map

| Stage | UI workflow | SDD phase | Main artifact |
| --- | --- | --- | --- |
| 1 | 需求与目标 | define-spec | 需求文档：目标、指标、范围、约束 |
| 2 | 视觉探索 | visual-prototype | 首要页面高保真效果图：风格方向、模块首页、审批反馈 |
| 3 | UI Spec | design-spec | UI 规范文档：页面结构、组件、状态、工程约束 |
| 4 | 组件化实现 | execute-tasks | 可运行产物：组件库、代码、页面 |
| 5 | 截图对比修正 | verification | 对比报告：差异清单、修正记录 |
| 6 | 交付与沉淀 | iterate-archive | 交付包：文档、资产、复盘、指南 |

## When To Open Extra Files

| File | Open when |
| --- | --- |
| [references/toolkit-map.md](references/toolkit-map.md) | Need to choose a tool, understand toolbox positioning, or avoid treating the skill as a single linear workflow |
| [references/sdd-six-stage-map.md](references/sdd-six-stage-map.md) | Need the full six-stage operating model, stage outputs, feedback loops, or SDD mapping |
| [references/phase-1-define-spec.md](references/phase-1-define-spec.md) | Need to transform raw requirements into PRD, goals, scope, users, scenarios, page priorities, and acceptance criteria |
| [references/phase-3-visual-prototype.md](references/phase-3-visual-prototype.md) | Need reference-image style extraction, primary-page high-fidelity UI effect images, approval workflow, or visual prompt packs |
| [references/phase-2-design-spec.md](references/phase-2-design-spec.md) | Need to write UI Spec after visual approval: information architecture, page structure, components, states, rules, and engineering constraints |
| [references/phase-4-6-execution-verification-delivery.md](references/phase-4-6-execution-verification-delivery.md) | Need implementation, screenshot comparison, verification, delivery package, or archive guidance |
| [references/workflow-checklist.md](references/workflow-checklist.md) | Before final delivery or when checking whether stage artifacts are complete |

## General Rules

- Use the toolbox metaphor. Choose the smallest useful tool for the user's current task.
- Do not invert the visual-first workflow. Generating primary-page high-fidelity UI effect images is the first step after the PRD, not UI Spec and not HTML/code.
- Use reference images for visual style. PRD controls business content and modules.
- Generate primary pages first, not every child page. Stop for approval before expanding.
- Write UI Spec after visual approval, not before.
- Implement only when the user explicitly asks for code or runnable pages, and only when the visual direction has been approved and the UI Spec has been written.
- Keep artifacts reusable: PRD feeds visual exploration, approved visuals feed UI Spec, UI Spec feeds implementation and verification.
- Do not invent unprovided business rules. Mark missing details as `待确认`.
- Use the strict prompt templates in phase references by default. Use quick prompts only for small drafts or when the user explicitly asks for a lightweight version.
- Keep every stage artifact reusable by the next stage. PRD feeds visual exploration; approved visuals feed UI Spec; UI Spec feeds implementation and verification.
- Audit actual files before saying the work is done.

## Tool Selection

If the user asks for a complete product/UI project, use the default path. If the user asks for a specific task, use the matching tool:

- `写需求文档` -> Requirement Builder.
- `参考图提炼风格` -> Reference Style Extractor.
- `先出效果图` / `画首要页面` -> Primary Page Image Generator.
- `根据已确认效果图写 UI Spec` -> UI Spec Writer.
- `实现页面` / `写代码` -> Frontend Implementation Guide.
- `截图对比` / `哪里不像` -> Screenshot Verification.
- `重设计这个页面` -> Redesign Auditor.
- `整理交付物` -> Delivery Archivist.

## Primary Page Approval Gate

`首要页面` means the entry or representative page for each major business module. It should show the module's core task, information hierarchy, navigation relationship, visual density, and main reusable components. It is not every child page, detail page, edit form, modal, or rare state.

Default first visual batch:

- Workbench or dashboard entry page.
- One entry/representative page for each major navigation module.
- One core workflow page if the product has a process-heavy module.
- One analytics or report entry page if data insight is important.
- One mobile home/task page if the product has a mobile side.

After generating the primary-page batch:

1. Present the images or prompt pack for human approval.
2. If approved, write the UI Spec, then expand to child pages/states only when asked.
3. If rejected with comments, regenerate according to comments.
4. If rejected without comments, generate a meaningfully different second visual direction and explain the changes.

## Default Workflow

1. Identify the user's current stage. If unclear, infer the earliest incomplete stage.
2. Inspect all provided source files before writing. For `.docx`, `.pdf`, `.xlsx`, screenshots, or images, use the relevant document/PDF/spreadsheet/image capabilities.
3. If the user provides reference images or a reference-image folder, inspect them before visual prompting.
4. Produce the stage artifact in a stable project folder using clear Chinese filenames when the project is Chinese.
5. State how this artifact constrains or enables the next stage.

## Stage Defaults

### 1. 需求与目标 / define-spec

Open [references/phase-1-define-spec.md](references/phase-1-define-spec.md).

Produce a PRD-style requirements document with:

- 问题、用户、场景、目标、成功指标
- 功能范围与约束
- 页面名称、页面核心任务、主次信息优先级
- 目标用户、关键用户动作
- 核心场景、主要模块清单
- 验收标准与待确认问题
- 下一阶段首要页面视觉探索约束

### 2. 视觉探索 / visual-prototype

Open [references/phase-3-visual-prototype.md](references/phase-3-visual-prototype.md).

Produce visual artifacts with:

- 参考图片风格提炼，或无参考图时的 AI 风格推导
- 视觉风格指南
- 高保真 UI 效果图提示词
- 各模块首要页面的高保真效果图
- 人工审批记录或下一版重设计说明
- 与 PRD 的一致性检查

### 3. UI Spec / design-spec

Open [references/phase-2-design-spec.md](references/phase-2-design-spec.md).

Produce a UI Spec after visual approval with:

- 已批准视觉方向沉淀
- 信息架构与导航结构
- 页面结构与模块关系
- 关键用户路径
- 状态、权限、异常、normal/loading/empty/error 四状态
- 数据字段、操作入口、交互规则、API 规则
- 文件夹结构、可复用组件、DRY、`src/api`、组件嵌套深度等工程约束

### 4-6. 实现、验证、交付

Open [references/phase-4-6-execution-verification-delivery.md](references/phase-4-6-execution-verification-delivery.md).

Use these stages when the user asks for runnable UI, screenshots, comparison fixes, final packaging, or reusable design-system documentation.

Do not enter implementation only because the PRD is finished. Stage 4 starts after explicit implementation instruction plus approved visual prototype and UI Spec.

## File Naming

Use clear names:

```text
01-需求与目标-PRD.md
02-视觉风格与首要页面效果图.md
03-UI规范文档.md
04-组件实现说明.md
05-截图对比报告.md
06-交付清单.md
UI效果图/01-primary-首页工作台.png
UI效果图/02-primary-用户管理.png
```

## Final Response

Keep the final response evidence-based:

```markdown
已完成：[阶段名称]

产物：
- [文件/目录]

下一阶段输入：
- [可直接用于下一阶段的约束或素材]

待确认：
- [仅列关键问题]
```
