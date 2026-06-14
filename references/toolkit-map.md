# AI UI Design Toolkit Map

This skill is a UI design toolbox, not only a workflow. Use the smallest useful tool for the user's current task, while preserving the recommended visual-first path when the user asks for an end-to-end project.

## Taste-Skill-Inspired Lessons

The important pattern is:

```text
establish visual target -> analyze/structure target -> implement or document target -> verify output
```

For this toolkit, the equivalent is:

```text
PRD -> primary-page effect images -> approval -> UI Spec -> implementation -> screenshot verification -> delivery archive
```

The article's strongest lesson is that many AI-generated interfaces fail because they start from code without a clear visual target. This toolkit should therefore provide tools for style extraction, image-first design, UI Spec writing after approval, and verification, rather than only a linear prompt.

## Tools

## Optional Taste Parameters

Use these optional parameters when the user wants to tune the visual direction. Do not require them for ordinary work.

| Parameter | Range | Use |
| --- | --- | --- |
| `DESIGN_VARIANCE` | 1-10 | Controls how conventional vs. distinctive the visual direction should be. Low is centered and safe; high is more asymmetrical, modern, and expressive. |
| `VISUAL_DENSITY` | 1-10 | Controls information density. Low is spacious and brand/editorial; high is operational, table-heavy, dashboard-like. |
| `MOTION_INTENSITY` | 1-10 | Controls animation guidance for implementation. Low is subtle state transitions; high allows richer scroll, hover, magnetic, or staged motion. |

Default guidance:

- If the product is an enterprise/admin system, default `DESIGN_VARIANCE=4-6`, `VISUAL_DENSITY=6-8`, `MOTION_INTENSITY=1-3`.
- If the product is a brand/landing experience, default `DESIGN_VARIANCE=6-8`, `VISUAL_DENSITY=2-5`, `MOTION_INTENSITY=4-7`.
- If the user provides reference images, let the reference style override these defaults.

### Requirement Builder

Use when raw inputs need to become a PRD or requirements document.

Open:

- [phase-1-define-spec.md](phase-1-define-spec.md)

Output:

- `01-需求与目标-PRD.md`
- Page list.
- Primary-page candidates.
- Next-stage visual constraints.

### Reference Style Extractor

Use when the user provides reference images, screenshots, a visual folder, or a product style direction.

Open:

- [phase-3-visual-prototype.md](phase-3-visual-prototype.md)

Output:

- Visual style source.
- Layout, color, typography, density, component, and interaction-tone extraction.
- Avoid list.

Rules:

- Use reference images for style only.
- PRD controls business content and modules.
- If no reference exists, derive style from product domain and users.

### Primary Page Image Generator

Use when the user wants UI effect images, first visual direction, prototype images, or page mockups.

Open:

- [phase-3-visual-prototype.md](phase-3-visual-prototype.md)

Output:

- Primary-page prompt pack.
- High-fidelity effect images for module entry/representative pages.
- Approval request.

Rules:

- Generate primary pages first.
- Do not generate all child pages in the first batch.
- Stop for approval before UI Spec, child pages, or implementation unless the user explicitly skips approval.

### UI Spec Writer

Use after primary-page visual approval, or when the user explicitly asks for UI Spec.

Open:

- [phase-2-design-spec.md](phase-2-design-spec.md)

Output:

- UI Spec.
- Component inventory.
- State rules.
- API/data rules.
- Frontend structure and engineering constraints.

### Brand / Visual System Kit

Use when the user needs a style system, design tokens, brand direction, or reusable UI rules.

Use:

- Reference images when provided.
- Approved primary-page mockups when available.
- PRD product tone when no image exists.

Output:

- Colors.
- Typography.
- Spacing.
- Radius and shadow.
- Icon style.
- Buttons, cards, tables, forms, status tags, charts.
- Do/don't list.

### Frontend Implementation Guide

Use only when the user explicitly asks for code, HTML, React/Vue/Svelte, or runnable pages.

Open:

- [phase-4-6-execution-verification-delivery.md](phase-4-6-execution-verification-delivery.md)

Inputs:

- Approved visual direction.
- UI Spec.
- Existing codebase rules.

Rules:

- Follow DRY.
- Put backend service calls under `src/api`.
- Use `src/mocks` for prototype mock data when needed.
- Keep page component nesting shallow.
- Reuse components.

### Screenshot Verification

Use when comparing implementation screenshots to approved mockups or UI Spec.

Open:

- [phase-4-6-execution-verification-delivery.md](phase-4-6-execution-verification-delivery.md)

Output:

- Screenshot comparison report.
- Difference classification: layout, style, interaction, business, engineering.
- Fix list and re-verification notes.

### Redesign Auditor

Use when the user has an existing page and asks to improve, redesign, or remove template taste.

Method:

1. Identify current UI problems: layout, hierarchy, spacing, typography, color, components, interaction, consistency.
2. Compare against product goal and target user.
3. Propose redesign direction.
4. Generate new primary-page effect image or prompt pack.

### Delivery Archivist

Use when the user asks for final packaging, reusable assets, or handoff.

Output:

- PRD.
- Approved UI images.
- UI Spec.
- Visual prompt assets.
- Code prompt assets.
- Implementation files or links.
- Screenshot reports.
- Fix records.
- Final acceptance report.

## Naming Guidance

Use toolkit language in user-facing explanations:

- "工具箱"
- "子工具"
- "按当前任务调用"
- "视觉优先"
- "首要页面审批门"

Avoid describing the skill as only a fixed workflow unless the user asks for the full end-to-end path.
