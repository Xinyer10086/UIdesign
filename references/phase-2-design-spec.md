# Phase 3: UI Spec / design-spec

Use this phase after the primary-page visual direction has been approved. The UI Spec distills the approved high-fidelity effects into implementable structure, reusable components, interaction states, data/API rules, and engineering constraints.

Do not write the full UI Spec before the first visual direction unless the user explicitly asks for UI Spec first.

## Inputs

Use:

- Stage-1 PRD.
- Approved primary-page high-fidelity mockups.
- Human approval comments and redesign notes.
- Reference-image style extraction, if any.
- Existing frontend codebase/design system, if implementation is expected.

If there are no approved visual mockups yet, go to phase 2 visual exploration first.

## UI Spec Contents

Use this structure:

```markdown
# [产品名称] UI Spec（设计规格）

## 1. 设计目标与已批准视觉方向
## 2. 信息架构
### 2.1 导航结构
### 2.2 模块分组
### 2.3 页面层级
## 3. 用户角色与权限入口
## 4. 关键用户路径
## 5. 页面规格
### 5.x [页面名称]
#### 页面目标
#### 适用用户
#### 信息优先级
#### 页面结构
#### 核心组件
#### 操作入口
#### 数据字段
#### 四状态规则
#### 异常与权限状态
#### 与其他页面关系
## 6. 组件规范
## 7. 通用交互规则
## 8. 通用状态规范
## 9. 工程实现原则
## 10. 目录结构与组件复用约束
## 11. 内容与文案规则
## 12. 数据与 API 规范
## 13. 视觉规则沉淀
## 14. 待确认问题
## 15. 下一阶段输入：组件化实现约束
```

## Engineering Principles To Include

Write these principles into the UI Spec whenever implementation may follow:

- Follow the DRY principle and avoid repeated code.
- All backend service calls must go through API modules under `src/api`.
- Prototype mock data may be centralized in `src/mocks`; real backend integration must not bypass `src/api`.
- Page component nesting should not exceed three layers where possible.
- Use layered organization by feature/domain and separate concerns clearly.
- Use consistent, descriptive directory and file names that reflect purpose and content.
- Keep related functionality in the same module and reduce cross-module dependencies.
- Avoid overly deep directories; keep nesting generally within 3-4 levels.
- Separate code, assets, configuration, and tests.
- Centralize dependency management and avoid duplicate dependency declarations.

## Recommended Frontend Structure

Use or adapt this structure unless the existing codebase has a stronger convention:

```text
src/
  api/                 # all backend service calls
  assets/              # images, icons, fonts, static assets
  components/          # shared reusable components
  layouts/             # app shell, sidebar, topbar, page frame
  mocks/               # prototype mock data when needed
  modules/             # feature/domain modules
    [module-name]/
      pages/
      components/
      hooks/
      types/
      utils/
  routes/              # route definitions
  stores/              # global state when needed
  styles/              # global tokens, theme, reset
  tests/               # shared test utilities or integration tests
```

Page-level guidance:

- Put reusable UI into `components/` or module-level `components/`.
- Put page containers in `modules/[module]/pages/`.
- Keep API request functions out of page components.
- Keep business state and transformation logic out of presentational components.
- Prefer composition through small, named components over deeply nested anonymous JSX.

## Component Four-State Contract

Every important page and reusable component must define:

| State | Required design |
| --- | --- |
| Normal | Realistic content/data display, available actions, normal boundary styling |
| Loading | Skeleton, spinner, or loading placeholder that preserves layout stability |
| Empty | Clear empty copy and CTA when appropriate |
| Error | Error copy plus retry/recovery action |

Missing state definitions should be marked as `待补充` before implementation.

## Page Spec Template

Use this for every important page:

```markdown
### [页面名称]

| 项目 | 规格 |
| --- | --- |
| 页面核心任务 |  |
| 是否首要页面 | 是/否；若是，说明它代表哪个业务模块 |
| 目标用户 |  |
| 关键用户动作 |  |
| P0 主信息 |  |
| P1 次信息 |  |
| P2 补充信息 |  |
| 主要入口 |  |
| 主要出口 |  |
| 对应已批准效果图 |  |

#### 页面结构
- 顶部区域：
- 筛选/搜索区：
- 主内容区：
- 详情/编辑区：
- 底部或辅助区：

#### 核心组件
- 

#### 交互流程
1. 
2. 
3. 

#### 四状态规则
- Normal：
- Loading：
- Empty：
- Error：
- 权限不足：
- 提交/审批/完成等业务状态：

#### 数据字段
| 字段 | 类型/示例 | 是否必需 | 来源/API | 用途 | 展示位置 |
| --- | --- | --- | --- | --- | --- |
```

## Design-Spec Prompt

Use this prompt as the base for generating the UI Spec after visual approval.

```text
请基于 PRD、已批准的首要页面高保真效果图和人工反馈，生成专业 UI Spec（设计规格文档），用于后续前端实现。

必须包含：
1. 已批准视觉方向：布局、色彩、组件、信息密度、页面外壳。
2. 信息架构：导航结构、模块分组、页面层级。
3. 页面结构：每个页面的核心任务、主次信息优先级、主要区域、核心组件。
4. 交互流：关键用户路径、入口出口、主要操作步骤。
5. 四状态规则：normal、loading、empty、error，以及权限和业务状态。
6. 数据字段：页面展示字段、操作字段、状态字段、数据来源/API。
7. 工程实现约束：DRY、src/api、src/mocks、组件复用、目录结构、组件嵌套深度、资源分类、依赖管理。

要求：
- 不要写成泛泛的设计原则，要写成可执行的页面规格。
- 不要凭空补充业务规则；不确定内容进入“待确认问题”。
- 保持简体中文，面向产品经理、UI 设计师和前端工程师共同使用。
- 明确写出后续实现时必须遵循的目录结构、可复用组件和工程原则。
```

Save the result as:

```text
03-UI规范文档.md
```
