# AI UI Design Toolkit Checklist

Use this checklist before final delivery or before moving to the next stage.

## Stage 1: 需求与目标

- Source files inspected.
- Tables, embedded sheets, screenshots, or images checked when applicable.
- Business background written.
- Problem, users, scenarios, goals, and success indicators written.
- Functional scope and constraints written.
- Page requirements table includes:
  - Page name.
  - Page core task.
  - Target users.
  - Key user actions.
  - P0 main information.
  - P1 secondary information.
  - P2 supplemental information.
  - Key states/rules.
- Business rules listed.
- Data objects drafted.
- UI design priorities listed.
- Acceptance criteria listed.
- Unclear items captured as `待确认`.
- Stage-2 visual exploration constraints summarized.

## Stage 2: 视觉探索

- Reference images checked first when provided.
- If no reference image exists, style is derived from PRD/domain/users/product tone.
- Optional parameters `DESIGN_VARIANCE`, `VISUAL_DENSITY`, and `MOTION_INTENSITY` are applied only if provided, otherwise inferred conservatively.
- Style reference is separated from structural source of truth; PRD still controls business content and modules.
- Output scope is primary pages first.
- Primary-page list covers major modules without generating every subpage at once.
- Unified visual system written.
- Page prompt pack created or images generated.
- Each page prompt includes real product text, filters, tables/cards/forms/charts, and actions.
- Consistent navigation, topbar, spacing, cards, table style, status tags, and typography enforced.
- Images saved to the project output folder when generated.
- Human approval requested after the first primary-page batch.
- If rejected, comments were applied or a second visual direction was generated.
- UI Spec was not written before visual approval unless the user explicitly asked for it.

## Stage 3: UI Spec

- UI Spec is written after primary-page visual approval unless the user explicitly asked for UI Spec first.
- Approved visual direction is distilled into component and style rules.
- Information architecture written.
- Navigation and module grouping written.
- User roles and entry points written.
- Key user paths written.
- Each important page has:
  - Page goal.
  - Page structure.
  - Core components.
  - Actions.
  - Data fields and API/source.
  - Interaction states.
  - Normal/loading/empty/error states.
- Engineering principles written: DRY, `src/api`, `src/mocks`, module layering, naming, component reuse, shallow nesting, asset/config/test separation, centralized dependencies.
- Recommended folder structure written or adapted from the existing codebase.
- Open questions preserved.

## Stage 4: 组件化实现

- Implementation starts only after explicit implementation request, visual prototype approval, and UI Spec completion.
- Existing codebase/framework inspected.
- Components match UI Spec and approved visual direction.
- Backend calls are placed under `src/api`.
- Prototype mock data is centralized in `src/mocks` when used.
- Reusable components are identified before page implementation.
- Page component nesting kept shallow.
- Normal/loading/empty/error/permission/business states implemented.
- Responsive behavior checked when relevant.
- Dev server or build verified when applicable.

## Stage 5: 截图对比修正

- Screenshots captured for relevant viewports.
- Screenshot comparison report created.
- Differences classified as layout, style, interaction, business, or engineering issues.
- Material differences fixed or recorded.
- Re-capture completed after fixes.

## Stage 6: 交付与沉淀

- Delivery package listed.
- All file paths verified.
- PRD, approved UI images, UI Spec, prompts, implementation, verification records, and final report included when relevant.
- Reusable assets and decisions recorded.
- Deferred issues recorded.
- Next iteration input summarized.
