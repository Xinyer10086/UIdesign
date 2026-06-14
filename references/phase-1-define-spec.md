# Phase 1: 需求与目标 / define-spec

Use this phase to turn raw product material into a PRD-style requirements artifact. This is the source of truth for the next visual exploration stage.

## Intake

Inspect the user's sources before writing:

- Word/PDF/spreadsheet feature lists
- Existing PRD or Markdown notes
- Screenshots or rough interface sketches
- User-provided business background
- Target output folder and desired format

Capture:

- Product name and domain
- Target users and roles
- Business problem
- Core scenarios
- Page/module list
- Key user actions
- Success indicators
- Scope boundaries
- Constraints and open questions

## Extraction Rules

- Do not rely only on visible paragraphs when reading `.docx`; inspect tables and embedded content when available.
- Do not invent detailed business rules. Use `待确认` when the source is unclear.
- Keep the PRD useful for UI design. Page tasks, information priority, states, actions, and module relationships are more important than generic background prose.
- If the source is a feature list, convert each feature into a user-facing page/module requirement where possible.

## PRD Structure

Use this Markdown structure by default:

```markdown
# [产品名称] PRD（原始需求稿）

| 项目 | 内容 |
| --- | --- |
| 产品名称 |  |
| 文档类型 | PRD 原始需求稿 |
| 版本 | V0.1 |
| 编写日期 |  |
| 输入资料 |  |
| 目标用途 | 面向 UI 设计、交互设计与研发拆解 |

## 1. 文档目的
## 2. 业务背景
## 3. 需求与目标
### 3.1 问题定义
### 3.2 产品目标
### 3.3 成功指标
## 4. 用户、场景与任务
### 4.1 目标用户
### 4.2 核心场景
### 4.3 关键用户动作
## 5. 功能范围
### 5.1 本期纳入范围
### 5.2 不纳入范围
### 5.3 待确认范围
## 6. 页面需求总览
## 7. 主要模块需求描述
## 8. 通用页面模式
## 9. 关键业务规则
## 10. 数据对象初稿
## 11. 非功能需求
## 12. UI 设计重点
## 13. 验收标准初稿
## 14. 待确认问题
## 15. 下一阶段输入：首要页面视觉探索约束
```

For the page requirements table, include:

```markdown
| 页面名称 | 页面核心任务 | 目标用户 | 关键用户动作 | P0 主信息 | P1 次信息 | P2 补充信息 | 关键状态/规则 |
| --- | --- | --- | --- | --- | --- | --- | --- |
```

Information priority:

- `P0 主信息`: information required to complete the page's core task.
- `P1 次信息`: information used for judgment, comparison, filtering, navigation, or secondary action.
- `P2 补充信息`: logs, history, exports, rare settings, references, and optional details.

## Prompt Templates

Use the strict prompt by default. Use the quick prompt only for very small tasks or when the user explicitly asks for a lightweight draft.

### Quick Prompt

Use this prompt as the base for quick PRD drafts. Add task-specific context and source excerpts.

```text
请基于以下输入资料生成专业 PRD 原始需求稿，面向后续 UI 设计和研发拆解。

必须包含：
1. 页面名称、页面核心任务、页面主次信息优先级。
2. 目标用户、关键用户动作。
3. 核心场景、主要模块清单。
4. 业务背景、需求描述、关键业务规则、数据对象、验收标准、待确认问题。

输出格式：Markdown。
语言：简体中文。
要求：不要凭空补充未确认规则；不清楚的内容放入“待确认问题”。
```

### Strict Prompt

Use this prompt for normal work. It is designed to prevent missing sections and to make the PRD usable for the next step: primary-page high-fidelity UI effect images.

```text
请基于输入资料生成专业 PRD 原始需求稿，作为后续“首要页面高保真 UI 效果图”的唯一业务依据。

输入资料：
[粘贴或引用用户提供的功能清单、业务说明、文档路径、截图说明、访谈笔记、约束条件]

输出格式：
- Markdown。
- 语言：简体中文。
- 不要输出泛泛而谈的说明，要输出可以直接指导 UI 效果图生成的产品需求文档。

必须严格包含以下章节：

# [产品名称] PRD（原始需求稿）

## 1. 产品概述
必须写清楚：
- 产品名称：
- 产品定位：
- 业务背景：
- 当前问题：
- 产品目标：
- 成功指标：
- 使用边界：

## 2. 目标用户与角色
必须用表格描述：
| 用户/角色 | 使用场景 | 核心诉求 | 关键动作 | 权限边界 |
| --- | --- | --- | --- | --- |

## 3. 核心场景与业务流程
必须包含：
- 核心场景清单。
- 至少 1 条主业务流程，按步骤描述用户从进入系统到完成核心任务的路径。
- 如果存在审批、流转、异常处理、数据回填、导入导出等流程，必须写出。

## 4. 功能范围
必须分为：
- 本期纳入范围。
- 本期不纳入范围。
- 待确认范围。

## 5. 模块清单
必须用表格描述：
| 模块名称 | 模块目标 | 主要用户 | 核心功能 | 关联数据 | 优先级 |
| --- | --- | --- | --- | --- | --- |

## 6. 页面清单与首要页面建议
必须按模块列出页面，并标记页面类型：
| 模块 | 页面名称 | 页面类型（首要页面/子页面/状态页） | 页面核心任务 | 为什么需要该页面 | 是否进入首批效果图 |
| --- | --- | --- | --- | --- | --- |

规则：
- 每个主要业务模块至少建议 1 个“首要页面”。
- 首要页面是模块入口页或代表页，不是所有子页面。
- 首批效果图只生成首要页面，不生成全部子页面。

## 7. 页面需求表
每个页面必须包含：
| 页面名称 | 页面核心任务 | 目标用户 | 关键用户动作 | P0 主信息 | P1 次信息 | P2 补充信息 | 主要模块 | 页面状态 | 数据来源/API | 验收标准 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

页面状态必须至少考虑：
- normal：正常数据展示。
- loading：加载中。
- empty：空状态。
- error：错误状态。
- permission：无权限/权限不足，如适用。

## 8. 数据对象与字段
必须用表格描述：
| 数据对象 | 关键字段 | 字段含义 | 出现页面 | 数据来源 | 备注 |
| --- | --- | --- | --- | --- | --- |

## 9. 业务规则与约束
必须写清楚：
- 权限规则。
- 状态流转规则。
- 表单校验规则。
- 列表筛选/搜索/排序规则。
- 导入、导出、下载、上传规则，如适用。
- 异常与边界场景。

## 10. UI 设计重点
必须写清楚：
- 产品气质：
- 信息密度：
- 页面类型：
- 首要页面生成顺序：
- 需要强调的数据/状态：
- 视觉参考来源（如用户提供参考图则写“使用参考图提炼风格”；没有则写“由 AI 根据 PRD 推导风格”）：
- 禁止事项：

## 11. 验收标准初稿
必须按页面或模块列出可检查的验收标准。

## 12. 待确认问题
所有不确定内容必须放在这里，不要自行编造。

## 13. 下一阶段输入：首要页面高保真效果图约束
必须总结给下一阶段使用：
- 产品名称：
- 首批首要页面：
- 每个首要页面的核心任务：
- 必须体现的模块：
- 必须体现的状态/数据：
- 参考图片/视觉来源：
- 不要生成的内容：

硬性要求：
- 不要凭空补充未确认业务规则。
- 不要直接写 UI Spec。
- 不要写 HTML 或代码。
- PRD 完成后的下一步是生成首要页面高保真 UI 效果图。
- 如果源资料信息不足，仍然输出完整结构，但在对应位置标注“待确认”。
```

## Output

Save the result as:

```text
01-需求与目标-PRD.md
```

or, when a product name is clear:

```text
[产品名称]PRD.md
```

Before moving on, audit that every important source module/page appears in the PRD. If a module is merged, deferred, or unclear, record it.

## Handoff Rule

After this PRD is complete, the next default step is:

```text
PRD -> high-fidelity primary-page visual prototype -> UI Spec
```

Do not jump directly from PRD to UI Spec or HTML/code unless the user explicitly asks for that. If the user says `继续下一步`, interpret it as generating high-fidelity primary-page UI effect images.
