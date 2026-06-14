# AI UI Workflow x SDD Six-Stage Map

Use this reference when the task needs a full workflow view, stage boundaries, or a reasoned mapping from UI design work to SDD-style execution.

## Core Idea

The workflow is visual-first after PRD:

```text
1 需求与目标 -> 2 视觉探索/首要页面效果图 -> 3 UI Spec -> 4 组件化实现 -> 5 截图对比修正 -> 6 交付与沉淀
        ^                                                                                 |
        |------------------------- 反馈、审批、复盘、方法复用 -----------------------------|
```

The PRD defines what the product needs. The first visual batch proves whether the design direction feels right. The UI Spec is written after visual approval, so it captures the approved structure, component system, states, and engineering rules.

## Stage Contracts

| Stage | Output | Must constrain |
| --- | --- | --- |
| 1 需求与目标 | 需求文档：目标、指标、范围、约束 | 首要页面视觉探索的页面范围、用户动作、信息优先级 |
| 2 视觉探索 | 首要页面效果图、风格方向、审批反馈 | UI Spec 的布局、组件、视觉规则、状态表达 |
| 3 UI Spec | UI 规范文档：页面结构、组件、交互、状态、工程约束 | 实现阶段的组件拆分、目录结构、API 与状态规则 |
| 4 组件化实现 | 可运行产物：组件库、代码、页面 | 验证阶段的截图基准、交互检查 |
| 5 截图对比修正 | 对比报告：差异清单、修正记录 | 交付阶段的质量标准和遗留问题 |
| 6 交付与沉淀 | 交付包：文档、资产、复盘、指南 | 下一轮需求与目标、方法复用 |

## Working Rules

- Start from the earliest incomplete stage.
- After stage 1, the next default step is stage 2 primary-page high-fidelity UI effect images, not UI Spec and not HTML/code.
- After stage 2 approval, the next default step is stage 3 UI Spec.
- In stage 2, generate module-level primary pages first and stop for human approval before expanding to child pages.
- If the user rejects the first visual direction with comments, regenerate according to comments.
- If the user rejects without comments, create a second visual direction with materially different layout, density, color treatment, and component style.
- If a new requirement appears during visual or implementation work, route it back to stage 1 as a change note.
- If visual exploration reveals a better interaction, capture it in the UI Spec after approval.
- Treat verification as an explicit stage, not as a final glance.

## Artifact Handoff

### Stage 1 -> Stage 2

Pass:

- Product objective.
- Target users and roles.
- Core scenarios.
- Main modules and pages.
- Page-level task and information priority.
- Constraints and open questions.
- Reference images or style source, if provided.

### Stage 2 -> Stage 3

Pass:

- Approved primary-page mockups.
- Visual system: color, typography, spacing, cards, buttons, tags, tables, charts.
- Layout patterns.
- Component inventory visible in mockups.
- Navigation and module relationship.
- Human approval comments and redesign notes.
- Unresolved visual or business questions.

### Stage 3 -> Stage 4

Pass:

- UI Spec.
- Component inventory.
- State rules.
- API/data requirements.
- Directory structure and implementation constraints.
- Typography, color, spacing, icon, table, card, button rules.

### Stage 4 -> Stage 5

Pass:

- Runnable URL or build output.
- Target screenshots or generated mockups.
- Expected page list and viewport sizes.
- Known compromises.

### Stage 5 -> Stage 6

Pass:

- Screenshot comparison report.
- Fixed issues.
- Remaining differences.
- QA evidence and test commands.

### Stage 6 -> Next Loop

Pass:

- Final delivery list.
- Reusable assets.
- Lessons learned.
- Design-system decisions.
- Backlog of improvements.
