# AI UI Design Toolkit | AI UI 设计工具箱

> *「先看见，再写 Spec——让产品团队在写代码之前就确认视觉方向」*

<div align="center">

[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-ai--ui--design--toolkit-blueviolet)](SKILL.md)
[![skills.sh](https://skills.sh/b/Xinyer10086/UIdesign)](https://skills.sh/Xinyer10086/UIdesign)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

**把 PRD、效果图、UI Spec 和前端实现串成一个视觉优先的端到端工作流**

[看它解决什么问题](#它解决什么问题) · [效果示例](#效果示例) · [快速开始](#快速开始) · [触发方式](#触发方式) · [它和同类有什么不同](#它和同类有什么不同)

</div>

---

## 它解决什么问题

你是一个产品经理、UI 设计师或者全栈工程师。团队拿到需求后，最常见的做法是直接从需求跳到 HTML——结果呢？做出来的东西「总觉得哪里不对」，因为**没有先看过视觉方向**。

这个工具箱换了一个顺序：先出 PRD → 生成首要页面高保真效果图 → 人工审批视觉方向 → 再写 UI Spec → 组件化实现 → 截图对比修正。**视觉方向确认之前不写代码**。

这不是一条死流水线——它是 9 个子工具的组合工具箱。需要写 PRD 就调需求构建器，需要参考图提炼风格就调样式提取器，需要单独生成效果图就调首要页面生成器。**用小工具解决当前问题，需要端到端时才走全长。**

## 效果示例

### 实战案例：平安班组（安全生产管理系统）

使用 Toolkit 的完整六阶段工作流，覆盖组织架构、一班三查、隐患整改、积分激励和数据分析 11 个模块。

完整案例见 [examples/平安班组](examples/平安班组/平安班组-端到端设计案例.md)。

```text
平安班组项目/
├── 01-需求与目标-PRD.md                # 423 行完整 PRD
├── 02-视觉风格与首要页面效果图.md       # 28 张高保真效果图
├── 03-UI规范文档.md                     # 11 模块的 UI Spec
├── 04-组件实现说明.md                   # 前端实现说明
├── 05-截图对比报告.md                   # 截图验证报告
└── 06-交付清单.md                       # 交付归档
```

> 典型产物结构也适用于任何新项目

<div align="center">

### 效果图示例

![组织架构-公司管理](examples/平安班组/01-公司管理.png)

*组织架构模块 · 公司管理页面*

![一班三查-作业派班](examples/平安班组/02-作业派班.png)

*一班三查模块 · 作业派班页面*

</div>


## 快速开始

### 安装

```bash
npx skills add Xinyer10086/UIdesign
```

或者克隆到本地：

```bash
git clone https://github.com/Xinyer10086/UIdesign.git ~/.agents/skills/ai-ui-design-toolkit
```

### 装完第一句话

对 Agent 说：

```text
用 $ai-ui-design-toolkit 把这份产品需求转换成 PRD、首要页面效果图，审批后再写 UI Spec
```

## 触发方式

- `写需求文档` → 需求构建器
- `参考图提炼风格` → 样式提取器
- `先出效果图 / 画首要页面` → 首要页面生成器
- `根据已确认效果图写 UI Spec` → UI Spec 书写器
- `实现页面 / 写代码` → 前端实现指南
- `截图对比 / 哪里不像` → 截图验证
- `重设计这个页面` → 重设计审计
- `整理交付物` → 交付归档

## 能做什么 / 它会交付什么

| 能力 | 交付物 | 典型耗时 |
| --- | --- | --- |
| 从原始需求生成 PRD | `01-需求与目标-PRD.md` | 1 轮对话 |
| 从参考图提炼视觉风格 | 视觉风格指南 + Avoid 清单 | 1-2 轮 |
| 生成首要页面高保真效果图 | `mockups/*.png` + 提示词包 | 1-2 轮 |
| 审批通过后写 UI Spec | `03-UI规范文档.md` | 1-2 轮 |
| 组件化前端实现 | 可运行页面/组件 | 2-3 轮 |
| 截图对比与修正 | `05-截图对比报告.md` | 1 轮 |
| 交付与设计资产沉淀 | `06-交付清单.md` | 1 轮 |

## 它和同类有什么不同

| 维度 | 同类做法 | AI UI Design Toolkit |
| --- | --- | --- |
| 工作流起点 | 大部分直接进入 UI Spec 或 HTML | 强迫先出效果图再写 Spec |
| 审批门 | 无显式审批门 | 首要页面效果图审批后才进入 UI Spec |
| 工具形态 | 固定线性流程 | 9 个子工具可自由组合 |
| 目标用户 | 面向开发者 | 面向产品经理 + UI 设计师 + 全栈 |
| 交付产物 | 代码为主 | PRD + 效果图 + Spec + 代码 + 验证报告 |
| 语言 | 英文为主 | 简体中文，产物和工作流均为中文 |

## 安全边界

- **不会** 直接写 HTML/代码，除非用户明确要求且视觉方向已确认
- **不会** 在审批门之前自动扩到子页面或完整 UI Spec
- **不会** 凭空编造未确认的业务规则——不清楚的内容标记为「待确认」
- **不会** 修改用户已有的项目资产或设计系统
- **视觉设计为零 API/零 Key**——不依赖外部 AI 服务来生成效果图

## 文件结构

```text
ai-ui-design-toolkit/
├── .claude-plugin/
│   └── marketplace.json       # 插件市场注册信息
├── .github/workflows/
│   └── ci.yml                 # CI 验证（frontmatter、路径、LICENSE）
├── SKILL.md                   # 主 Skill 文件 — Agent 入口
├── README.md                  # 本文件（你在这里）
├── CONTRIBUTING.md            # 贡献指南
├── LICENSE                    # MIT 许可证
├── agents/
│   └── openai.yaml            # Codex Agent 配置
├── examples/
│   └── README.md              # 示例输出结构说明
├── references/
│   ├── phase-1-define-spec.md         # PRD 需求稿模板
│   ├── phase-2-design-spec.md         # UI Spec 模板
│   ├── phase-3-visual-prototype.md    # 视觉探索指南
│   ├── phase-4-6-execution-verification-delivery.md  # 实现/验证/交付
│   ├── sdd-six-stage-map.md           # 六阶段映射与产物合约
│   ├── toolkit-map.md                 # 工具箱定位与子工具说明
│   └── workflow-checklist.md          # 各阶段检查清单
```

## 验证与测试

验证 prompt：

```text
用 $ai-ui-design-toolkit 的需求构建器，基于以下资料生成一个 PRD：
[粘贴原始需求描述]
```

合格表现：
- 输出完整的 `01-需求与目标-PRD.md`
- 包含页面清单、首要页面建议、信息优先级
- 下一阶段约束明确指向「首要页面视觉探索」
- 不凭空编造业务规则

## 致谢

- 工作流设计受 [Taste Skill](https://x.com/kepano/status/1890882424397713520) 「establish visual target → analyze/structure target → implement/document → verify」方法论启发
- README 模板遵循 [LearnPrompt House Style](https://github.com/LearnPrompt/learnprompt-house-style)

## 如何贡献

欢迎提交 Issue 和 PR！详见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## License

[MIT](LICENSE)

---

<div align="center">

*先看见，再动手 —— 每个产品都值得一个视觉方向确认的环节*

</div>

