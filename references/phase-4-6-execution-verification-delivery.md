# Phase 4-6: Implementation, Verification, Delivery

Use this reference when the user moves beyond prompts and mockups into runnable UI, screenshot comparison, fixes, delivery package, or knowledge reuse.

These stages are intentionally lighter than phases 1-3 in this version.

## Phase 4: 组件化实现 / execute-tasks

Goal: turn visual prototype and UI Spec into runnable UI.

Blocking precondition:

- Do not start implementation only because a PRD exists.
- Start implementation only when the user explicitly asks for code/HTML/runnable pages after the primary-page visual prototype has been approved and UI Spec has been written.
- If the user says “继续下一步” after PRD generation, interpret the next step as primary-page high-fidelity UI effect images, not UI Spec and not HTML.

Inputs:

- PRD
- UI Spec
- Visual system
- UI mockups or prompt pack
- Existing codebase/design system, if any

Implementation contract:

- Follow the existing frontend framework and design system when present.
- Split UI into reusable layout shell, navigation, page sections, cards, tables, filters, forms, dialogs, drawers, status tags, and charts.
- Keep page content faithful to UI Spec instead of inventing new product scope.
- Implement states: loading, empty, error, permission denied, success, validation, disabled, selected, hover/focus.
- Preserve visual consistency with phase 3.
- Follow DRY and avoid repeated code.
- Put all backend service calls under `src/api`; pages and components must not call backend services directly.
- Keep page component nesting to three layers where possible.
- Organize directories by feature/domain and separate concerns clearly.
- Use consistent descriptive naming for directories, files, components, hooks, types, and API modules.
- Keep related functionality inside the same module and reduce cross-module dependencies.
- Avoid deep nesting; keep directories generally within 3-4 levels.
- Separate code, assets, configuration, and tests.
- Centralize dependency management.

Recommended structure:

```text
src/
  api/
  assets/
  components/
  layouts/
  mocks/
  modules/
    [module-name]/
      pages/
      components/
      hooks/
      types/
      utils/
  routes/
  stores/
  styles/
  tests/
```

Reusable component candidates:

- App shell: sidebar, topbar, breadcrumb, page container.
- Data display: table, filter bar, KPI card, chart card, status tag.
- Input: search box, form section, date range, select group, upload.
- Feedback: empty state, loading state, error state, confirmation dialog.
- Workflow: stepper, approval timeline, detail drawer, action toolbar.

Quality gate before screenshot comparison:

- Page can run.
- All intended modules render.
- Component boundaries are clear.
- Normal/loading/empty/error states are implemented.
- Mock data or API layer is configured.
- No blank screen, missing key component, missing state, or completely wrong layout.

Suggested artifact:

```text
04-组件实现说明.md
```

or a runnable app/code changes when the user requests implementation.

## Phase 5: 截图对比修正 / verification

Goal: compare implementation screenshots with visual prototype/spec and fix differences.

Verification workflow:

1. Start the local dev server if needed.
2. Capture screenshots for desktop and mobile viewports where relevant.
3. Compare against phase-3 mockups and phase-2 UI Spec.
4. Record differences:
   - layout
   - spacing
   - typography
   - color
   - component state
   - content completeness
   - interaction behavior
5. Fix material differences.
6. Re-capture screenshots after fixes.

Suggested report:

```markdown
# 05-截图对比报告

| 页面 | 对比对象 | 差异 | 严重程度 | 修正方式 | 状态 |
| --- | --- | --- | --- | --- | --- |
```

## Phase 6: 交付与沉淀 / iterate-archive

Goal: package outputs and preserve reusable design knowledge for the next iteration.

Delivery package:

- PRD
- UI Spec
- Visual system and prompt pack
- UI mockup images
- Runnable implementation or code path, if created
- Screenshot comparison report
- Final QA notes
- Reusable design decisions
- Deferred issues and next iteration backlog
- Final visual-generation prompts
- Final code-generation prompts
- Revision prompts and fix records
- Acceptance criteria and final acceptance report

Suggested artifact:

```markdown
# 06-交付清单

## 1. 本轮目标
## 2. 已交付产物
## 3. 文件路径
## 4. 覆盖页面
## 5. 质量验证
## 6. 复用资产
## 7. 遗留问题
## 8. 下一轮建议
```

## Final Audit

Before final response, verify:

- Files exist on disk.
- Image count matches stated scope.
- Main modules are represented.
- Implementation runs if code was requested.
- Screenshots were checked if visual implementation was requested.
- Any deferred pages or uncertain rules are stated.
