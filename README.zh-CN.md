# Hyper-Waterfall

[English](README.md) | [한국어](README.ko.md) | 简体中文

[![GitHub Release](https://img.shields.io/github/v/release/postmelee/hyper-waterfall?logo=github&style=flat-square)](https://github.com/postmelee/hyper-waterfall/releases)
[![npm version](https://img.shields.io/npm/v/hyper-waterfall?logo=npm&style=flat-square)](https://www.npmjs.com/package/hyper-waterfall)
[![License: MIT](https://img.shields.io/github/license/postmelee/hyper-waterfall?style=flat-square)](LICENSE)

<!-- ![Hyper-Waterfall overview](docs/assets/hyper-waterfall.png) -->

## 从短暂会话到持久项目记忆

Hyper-Waterfall 是一种**由人治理的 AI 编码工作流**，它把短暂的会话上下文提炼为持久项目记忆，使工作可追踪、可审查、可恢复。

它不会把任务上下文困在临时聊天中，而是定期提取每个 task 中真正重要的内容——意图、范围、计划、决策、实现进度和验证依据——并记录为 Issue、计划书、Stage 报告、commit、PR 等结构化项目产出物。

这些产出物不是被动日志。它们共同构成共享的项目记忆，帮助新会话、agent 或贡献者无需重放聊天记录，就能恢复关键上下文并从文档化基线继续工作。

> **会话会结束，项目会记住。**
>
> 每项工作都会成为文档，每份文档都会成为下一项工作的上下文。

| Hyper-Waterfall 核心 | 含义 |
|---|---|
| 上下文提炼 | 从临时会话中提取关键任务上下文，并记录为结构化项目产出物。 |
| 持久项目记忆 | 意图、决策、进度和验证依据在会话结束后仍然保留。 |
| 人类治理 | 方向、范围、架构和质量的决策权由人掌握；AI 在明确边界内执行。 |
| 分阶段执行 | 大任务被拆成可审查的 Stage，每个 Stage 都有验证和完成报告。 |
| 可恢复工作 | 新会话、agent 和贡献者可以从项目产出物中恢复关键上下文并继续工作。 |

Hyper-Waterfall 建议使用 **`1 Issue = 1 Task = 1 Branch = 1 Session`** 来让会话保持小而集中。关键上下文已经提炼到项目中，因此会话可以干净地结束。

> [!IMPORTANT]
> **可以把执行交给 AI，但不要把决策权交出去。**
>
> Hyper-Waterfall 不是让 AI 神奇地做到一切的工具。它提供清晰轨道，让 AI 快速行动，同时避免人失去方向或项目上下文。

## 快速开始

### 现有仓库

把下面这一行发送给你的 AI 编码工具。

```text
将 https://github.com/postmelee/hyper-waterfall 的 Hyper-Waterfall 方法论应用到这个仓库。
```

### 新项目

当你的项目想法准备进入仓库时，先创建一个空的 GitHub 仓库或本地仓库。然后从这个空仓库发送下面的 prompt。

```text
我想在这个空仓库中开始一个新项目。

请先将 https://github.com/postmelee/hyper-waterfall 的 Hyper-Waterfall 方法论应用到这个仓库。

如果附带了项目简报或需求草案，请只把它作为上下文参考。不要在应用阶段创建产品计划、架构文档或源代码。应用完成后，请帮我把第一个产品任务注册为单独的 GitHub Issue。
```

在两种路径中，AI 都会先阅读 [`docs/agent-entrypoint.zh-CN.md`](docs/agent-entrypoint.zh-CN.md)，并按应用流程执行。在修改源码前，它必须先报告建议范围并获得任务指示者批准。

| AI 需要先报告的内容 | 内容 |
|---|---|
| 应用模式 | 是新应用 Hyper-Waterfall，还是更新已有 Hyper-Waterfall 安装。 |
| 变更候选 | 会创建或修改哪些文件，是否需要 placeholder 替换。 |
| 审批请求 | 实际文件变更前，任务指示者需要批准的范围。 |

### 语言支持

默认 locale 是 `en`。支持的 locale pack 是 `en`、`ko`、`zh-CN`；如果所选 locale source 缺失，会先报告 fallback 候选，而不是静默替换。

| 语言 | Locale |
|---|---|
| English | `en` |
| 韩语 | `ko` |
| 简体中文 | `zh-CN` |

使用 AI 编码工具时，请用你想使用的语言提出请求。AI 会在修改文件前先报告选择的 locale。

要在终端中检查应用判断，请显式传入 locale。需要时可以把 `zh-CN` 替换为 `en` 或 `ko`。

```sh
npx hyper-waterfall@0.3.0 init --repo . --locale zh-CN --dry-run
```

在 macOS 上，如果经常运行 CLI，可以通过 Homebrew 安装。

```sh
brew install postmelee/tap/hyper-waterfall
hyper-waterfall init --repo . --locale zh-CN --dry-run
```

`npx` 和 Homebrew CLI 命令只输出 lifecycle 判断。实际文件变更仍然必须经过审批 workflow。

导入后，AI 会按照 Hyper-Waterfall 方式推进工作。第一次使用时，你可以直接用自然语言告诉 AI，例如 `"请实现这个功能"`。

> 任何人都可以把 Hyper-Waterfall 应用到 GitHub 仓库，并让 Codex、Claude Code 等多个 AI 编码 agent 在同一套纪律和共享上下文下工作。

## 进一步了解 Hyper-Waterfall

[为什么选择 Hyper-Waterfall？](#为什么选择-hyper-waterfall) ·
[适用场景](#适用场景) ·
[与传统 AI 编码方式比较](#与传统-ai-编码方式比较) ·
[会发生什么变化](#会发生什么变化) ·
[Hyper-Waterfall 的强点](#hyper-waterfall-的强点) ·
[导入后的工作流](#导入后的工作流) ·
[生成的结构](#应用后的目标仓库结构生成的结构)

## 为什么选择 Hyper-Waterfall？

AI 编码 agent 有两个结构性弱点：

- 会话上下文是临时的；随着对话变长或工具变化，它会越来越不可靠。
- 即使方向错误，AI 也可能自信地继续执行。

Hyper-Waterfall 把这两个弱点转化为工作流约束。它把工作记忆提炼为项目产出物，并把 AI 执行放在人的决策门之内。

| 问题 | Hyper-Waterfall 约束 | 结果 |
|---|---|---|
| 上下文随会话结束而消失 | 把意图、决策、进度和验证记录为结构化产出物 | 持久项目记忆 |
| 长会话变得嘈杂 | 推荐模型：`1 Issue = 1 Task = 1 Branch = 1 Session` | 小而集中的上下文 |
| AI 可能在错误方向上快速执行 | 计划书和 Stage 边界需要人工审查 | 更早发现方向错误 |
| 每个 agent 都自行发明流程 | 共享规则、SKILL、manual 和 template | agent 之间执行一致 |
| reviewer 必须从聊天重建历史 | 报告、commit、PR 保留理由和依据 | 工作可追踪、可审查 |

结果不只是一个审批驱动的编码工具，而是一套工作流：在人保留关键决策权的同时，把临时 AI 执行转化为持久、可复用的项目知识。

## 适用场景

Hyper-Waterfall 面向真实源码变更：即使工作跨越单次 AI 会话，也必须保持可理解、可恢复。

| 适合的情况 | 不适合的情况 |
|---|---|
| 工作需要跨多天、会话、agent 或贡献者继续推进。 | 一两行修改，计划书和报告成本比变更本身还大。 |
| 希望意图、决策、进度和验证成为可复用的项目上下文。 | 一次性原型，比可追踪性更看重即时试验。 |
| 让 AI 编码工具修改真实源码，但范围和质量必须由人掌握。 | 人不打算审查结果，只想直接接受 AI 输出。 |
| PR review 时需要马上看出改了什么、为什么改、如何验证。 | 不重视交接或可恢复性的个人实验。 |
| 想按 Issue、branch、Stage 拆分大任务并尽早发现方向错误。 | 不使用当前实现所假定的 GitHub Issue、branch、PR 流程。 |
| 新贡献者或 AI 会话必须只靠项目产出物重新开始。 | 保存决策和工作历史没有价值的任务。 |

> 当 AI 承担大量实现，而人必须保留决策权、工程上下文和可审查性时，Hyper-Waterfall 最有价值。相反，如果即时试验比连续性更重要，它可能过重。

## 与传统 AI 编码方式比较

核心差异不在于 AI 是否在执行命令前请求权限，而在于会话消失后，项目是否仍能保存、审查并复用工作背后的上下文。

普通 AI 编码常依赖一次对话的流向。Hyper-Waterfall 在项目层面固定任务单位、决策门、产出格式和上下文交接规则。

| 传统 AI 编码方式 | 应用 Hyper-Waterfall 后 |
|---|---|
| 说“做这个”，AI 立刻改文件。 | 先用 Issue 和 task plan 定义目的、范围、验证标准。 |
| 工作范围在对话中不断摇摆。 | implementation plan 按 Stage 拆分，只在批准范围内推进。 |
| 任务上下文困在临时聊天会话中。 | 把关键上下文提炼到 `mydocs/`、Issue、PR、commit history。 |
| 事后很难追踪 AI 为什么改了哪些文件。 | Stage 报告和 commit 记录理由、产出物、验证结果。 |
| 大实现完成后才发现方向错误。 | 在 task plan、implementation plan、Stage 边界批准或纠正。 |
| 新会话或 agent 每次都要手动说明。 | 项目产出物提供关键上下文和下一步行动。 |
| PR review 时需要重新翻聊天记录。 | PR 和报告直接展示改了什么、为什么改、如何验证。 |

人类任务指示者保留方向、优先级、架构和质量的决策权。AI 快速执行探索、草拟、实现、验证和文档化。

> [!IMPORTANT]
> **核心差异：人不会停止思考，项目也不依赖某个会话记住一切。**

## 会发生什么变化

1. **会话上下文变成持久项目记忆。**
   意图、范围、决策、进度和验证依据保留在 `mydocs/`、Issue、PR、commit history 中。新会话、agent 或贡献者无需重放聊天记录即可继续。

2. **“做到哪里了？”有文档化答案。**
   Issue、今日待办、task plan、implementation plan、Stage 报告、最终报告、commit、PR 构成可恢复的任务时间线。

3. **会话保持小而集中。**
   推荐运用方式是 `1 Issue = 1 Task = 1 Branch = 1 Session`。task 结束后关闭会话；下一项工作在干净的新会话中按需读取文档化上下文。

4. **AI 不会随意改代码。**
   源码修改前要经过计划书和人的决策门，因此任务指示者始终控制方向和范围。

5. **人不会失去决策权。**
   源码修改、Stage 切换、最终报告、PR 创建之前都有 gate。AI 执行，但方向、架构和质量由人判断。

6. **可以并行运行多个 AI 会话。**
   独立 Issue 可以分别在 `local/task{N}` branch 或分离 worktree 中推进。上下文和变更范围不会混在一起。

7. **PR review 更容易。**
   PR 会整理改了什么、为什么改、经过哪些 Stage、做了哪些验证。reviewer 查看项目产出物，而不是重建聊天记录。

8. **更早发现方向错误。**
   在错误方向上积累大量工作前，task plan、implementation plan、Stage 完成报告会作为人工审查的质量门。

9. **不牺牲 AI 速度也能保留工程纪律。**
   AI 快速草拟计划、测试、报告和实现，工作流保留依据、理由和交接上下文。

10. **AI 编码从一次性对话变成可复用的项目流程。**
    所有工作通过 Issue、branch、文档、commit、PR 连接起来，可追踪、审查、恢复，并作为后续工作的上下文。

## Hyper-Waterfall 的强点

### 1. 把会话上下文提炼为持久项目记忆 — 知识资产化

- 任务意图、约束、计划、决策、逐 Stage 进度、验证结果和故障排查知识会积累为结构化项目产出物。
- 这些产出物不是被动记录，而是**下一项工作的输入**。未来会话和贡献者可以建立在过去工作之上，而不是从零重建。
- 无需把原始对话作为项目的 source of truth，也能保存会话中真正重要的部分。

> `mydocs/` 像一个专门保存工作历史的 vault。它按流程规定的格式积累任务意图、计划、决策、验证、产出物、反馈和故障排查。

### 2. 在方向错误变成大失败前通过 gate 发现 — 风险控制

- 工作遵循 `Issue -> branch -> task plan -> implementation plan -> Stage implementation, verification, and report -> final report -> Open PR`。
- 人会在 task plan、implementation plan、每个 Stage 边界和最终报告处审查。
- Stage 验证失败就在该 Stage 内恢复；范围改变则更新计划并重新批准。
- 这能提前发现错误目标、错误范围、错误架构方向等仅靠代码审查难以及早识别的语义错误。

### 3. 不只是“拜托 AI 做好”，而是让好工作在结构上更可能出现 — 自动化角色分工

- 任务指示者保留**方向、优先级、架构和质量决策**的责任。
- AI 承担探索、草拟、实现、测试、报告和 PR 正文准备等重复执行。
- SKILL 定义每一步要做什么、必须留下什么产出物、何时停止并把控制权交还给人。
- 中央 template 固定预期输出结构，避免 agent 每次重新发明计划书、报告或验证格式。

### 4. 会话保持小，记忆留在项目中 — 轻量上下文

- Hyper-Waterfall 不把所有项目历史不断堆进一个 AI 会话。推荐模型中，一个会话负责一个 Issue，并在 task 结束时关闭。
- 每个会话只读取当前 Issue、相关计划书、Stage 报告、项目文档和代码。
- 过去决策可从项目产出物按需读取，不必污染每个 prompt，也不依赖越来越模糊的长对话。
- 变更范围不冲突的独立 Issue 可以在不同 branch 或 worktree 中并行推进。

> AI 会话不一定越长越聪明，反而可能失去焦点。Hyper-Waterfall 保持会话短小，把记忆留在项目中。

### 5. 结果

这些强点形成一个循环：

```text
临时会话上下文
        ↓ 提炼
结构化项目产出物
        ↓ 积累
持久项目记忆
        ↓ 恢复
下一个会话、agent、贡献者或 task
```

同时，人的决策门让 AI 执行持续对齐项目方向。

结果是，AI 编码成为一种拥有持久项目记忆、可跨会话、agent 和贡献者追踪、审查、恢复的由人治理工作流。

> [!NOTE]
> 这个结构与 OpenAI 和 Anthropic 官方提示指南强调的清晰指令、充分上下文、输出格式约束、验证标准、停止条件、长期工作记忆、agentic workflow 控制原则一致。详细映射见 [提示指南对齐](#提示指南对齐)。

## 导入后的工作流

Hyper-Waterfall 以 **task** 为单位工作。每个 task 在产出代码的同时，也提炼理解、验证和继续该工作所需的上下文。

### Task 推进步骤

所有 task 都**严格**遵循下面的步骤。

```text
1. 确认或登记 GitHub Issue
2. 记录今日待办 (mydocs/orders/)
3. 创建 task branch (local/task{number})
4. 编写 task plan -> [任务指示者批准]
5. 编写 implementation plan -> [任务指示者批准]
6. 按 Stage 实现
7. 编写 Stage completion report -> [任务指示者批准]
8. 重复下一 Stage
9. 编写 final result report -> [任务指示者批准]
10. 更新今日待办状态
```

> 每个 `[approval]` 点既是决策门，也是上下文提炼边界。在继续前审查方向错误并记录当前状态。

详细流程以 [task workflow manual](templates/locales/zh-CN/mydocs/manual/task_workflow_guide.md) 为准。branch 和 PR 发布流程见 [Git workflow manual](templates/locales/zh-CN/mydocs/manual/git_workflow_guide.md)。

### 核心 SKILL 细节

| SKILL | 使用时机 | 主要产出物 |
|---|---|---|
| `task-register` | 新任务需要先创建 GitHub Issue 时 | 遵循 `task.yml` Issue Form 结构的 GitHub Issue、milestone/label 候选及选择理由 |
| `task-start` | 开始处理已批准的 Issue 时 | `local/task{N}` branch、今日待办行、基于 `task_plan.md` 的执行计划书 |
| `task-stage-report` | 一个 Stage 实现完成、进入下一阶段前 | 基于 `stage_report.md` 的阶段报告、阶段打包 commit、阶段验证结果 |
| `task-final-report` | 所有 Stage 完成、发布 PR 之前 | 基于 `final_report.md` 的最终报告、今日待办完成处理、Open PR |
| `pr-merge-cleanup` | PR 实际 merge 后立即使用 | close Issue、删除 `publish/task{N}` 远程 branch、清理本地 branch/worktree |
| `external-pr-review` | 审查外部贡献者 PR 时 | 基于 `external_pr_*` 模板的 `mydocs/pr/` 审查文档、验证结果、建议（merge/要求修改/close） |
| `todo` | 创建或更新今日待办板时 | 基于 `orders.md` 更新 `mydocs/orders/yyyymmdd.md` 表格 |

何时向用户显示每个 SKILL，遵循 [SKILL call display guide](templates/locales/zh-CN/mydocs/manual/task_workflow_guide.md)。PR 正文编写与验证结构遵循 [internal task PR guide](templates/locales/zh-CN/mydocs/manual/internal_pr_guide.md)，PR 创建命令和文档链接格式遵循 [PR command and link guide](templates/locales/zh-CN/mydocs/manual/pr_command_guide.md)。

文档结构和 manual 文档中立性标准不是独立 SKILL，而是通过 [document structure manual](templates/locales/zh-CN/mydocs/manual/document_structure_guide.md) 确认。

### Task Cycle

如果 Issue 已经存在，就跳过 `task-register`，直接进入 `task-start` 编写执行计划书。例如任务指示者说 `"处理 issue #17"` 时，AI 会确认 #17 的 milestone 和正文，然后创建 `local/task17`、今日待办和执行计划书。只有尚无 Issue 时，`task-register` 才会检查重复 Issue、milestone、label，并在创建前获得批准，然后创建 GitHub Issue。

每次阶段切换都需要任务指示者明确批准。

```text
0. Task 登记 -> `task-register`
   └─ AI: 检查重复 Issue、milestone、label 候选
   └─ 任务指示者: 批准创建 Issue
   └─ AI: 创建 GitHub Issue 后，请求批准进入 `task-start`

1. 执行计划书 -> `task-start`
   └─ 任务指示者: 指定现有 Issue，例如 "处理 issue #N"，或批准从刚创建的 Issue 开始
   └─ AI: 编写计划书（最少 3 个阶段，最多 6 个阶段）
   └─ 任务指示者: 审查 -> 批准或要求修改

2. 分阶段实现 -> `task-stage-report`（按阶段数量重复）
   └─ AI: 编写代码 + 运行测试
   └─ AI: 编写阶段完成报告
   └─ 任务指示者: 验证 -> 批准或反馈

3. 反馈反映 -> (manual)
   └─ 任务指示者: 编写反馈文档 (mydocs/feedback/)，AI 反映。如果 scope 改变，更新计划书并重新批准
   └─ AI: 反映反馈并修正

4. 最终报告 + Open PR -> `task-final-report`
   └─ AI: 编写最终结果报告，并创建结构化验证依据的 Open PR
   └─ 任务指示者: 验证 -> 批准或反馈

5. PR review + merge + 清理 -> `pr-merge-cleanup`
   └─ 任务指示者: PR review -> 批准或反馈
   └─ AI: review/merge 后 close Issue，清理 branch/今日待办
```

`todo` 会在上述流程中任何需要更新今日待办板的时点调用。`external-pr-review` 是外部贡献者 PR review 用的独立流程。

### 文档结构

task 使用或产生的文档结构：

```text
mydocs/
├── _templates/                         <- 各类产出物的输出格式
├── orders/yyyymmdd.md                  <- 今日待办（task 列表 + 状态）
├── plans/task_{milestone}_{N}.md       <- 执行计划书
├── plans/task_{milestone}_{N}_impl.md  <- 实现计划书
├── working/task_{milestone}_{N}_stage{S}.md
│                                        <- Stage 完成报告
├── report/task_{milestone}_{N}_report.md
│                                        <- 最终结果报告
├── feedback/                           <- 反馈与 review 意见
├── tech/                               <- 技术调查与正式化前草案
├── manual/                             <- 运营手册与重复工作标准
├── troubleshootings/                   <- 故障排查
└── pr/                                 <- 外部 PR review 记录
```

这些文档共同保存持久工作历史的不同部分：

| 区域 | 保存的上下文 |
|---|---|
| `orders/` | 当前 task 状态和下一步行动 |
| `plans/` | 意图、范围、决策、实现顺序、验证标准 |
| `working/` | Stage 进度、产出物、依据、残余风险、下一阶段上下文 |
| `report/` | 最终综合、验收状态、交接上下文 |
| `feedback/` | 人工审查、修正意见、判断依据 |
| `tech/` | 尚未提升为正式文档的调查、方案和设计推理 |
| `troubleshootings/` | 已知失败模式、诊断和恢复知识 |
| `pr/` | 外部贡献审查依据和建议 |

文件夹角色、文档文件名规则和产出物输出格式都在 [document structure manual](templates/locales/zh-CN/mydocs/manual/document_structure_guide.md) 中定义。每个文件夹的详细编写规则以该文件夹的 `README.md` 为准。

| 区域 | 策略 |
|---|---|
| `mydocs/` | 保存工作记忆、运营手册和调查依据。它不是目标项目的正式产品文档根目录。 |
| 正式产品文档 | Hyper-Waterfall 不固定正式文档根目录名称。目标项目可以选择 `docs/`、`specs/`、`site/`、`website/`、`adr/`、GitHub Wiki 等路径。创建、移动或修改产品/用户/贡献者/API/架构/路线图文档的 task，必须先在执行计划书的文档位置判断中说明目标读者、正式化级别、选择路径、替代路径、选择理由，并获得批准。 |
| `manual/` | 包含重复适用的运营标准和流程。特定 Issue、PR、release 验证、事故记录应分离到对应产出物文档。细节遵循 [manual document neutrality policy](templates/locales/zh-CN/mydocs/manual/document_structure_guide.md)。 |
| `tech/` | 包含技术调查、方案比较、设计判断依据和尚未正式化的草案。若要提升为用户或外部集成者必须遵循的正式契约文档，需要在单独 task 中选择正式文档根目录并获得批准。 |
| `_templates/` | 输出格式的 source of truth，不是实际 task 产出物。每个 Skill 生成产出物时先读取 `mydocs/_templates/` 中的相应模板，只有无法读取模板时才使用 Skill 内部的最小章节摘要作为 fallback。 |
| GitHub Issue 与 Pull Request | GitHub 平台产出物。Issue 正文以 `.github/ISSUE_TEMPLATE/task.yml` 为准，PR 正文以 `.github/pull_request_template.md` 为准，留在仓库内的工作文档以 `mydocs/_templates/` 为准。细节遵循 [GitHub platform template policy](templates/locales/zh-CN/mydocs/manual/document_structure_guide.md)。 |

## 应用后的目标仓库结构（生成的结构）

复制 `templates/` 并替换 placeholder 后，目标仓库会变成如下结构。

```text
your-repo/
├── AGENTS.md                       运营规则的单一 source of truth
├── CLAUDE.md                       Claude Code 用（引用 AGENTS.md）
├── .hyper-waterfall/
│   └── version.json                 记录已应用的 Hyper-Waterfall version 和 locale
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   └── task.yml
│   └── pull_request_template.md
├── .agents/
│   └── skills -> ../mydocs/skills  Codex 识别路径（符号链接）
├── .claude/
│   └── skills -> ../mydocs/skills  Claude Code 识别路径（符号链接）
└── mydocs/
    ├── _templates/         各类产出物的输出格式模板
    ├── manual/             运营手册（文档结构、task 流程、Git、PR、lifecycle、release/update、冲突规则）
    ├── skills/             SKILL source of truth（Codex/Claude Code 共用）
    ├── orders/             今日待办 (yyyymmdd.md)
    ├── plans/              执行/实现计划书
    │   └── archives/
    ├── working/            Stage 完成报告
    ├── report/             最终结果报告
    ├── feedback/           反馈与 review 意见
    ├── tech/               技术调查与正式化前草案
    ├── troubleshootings/   故障排查
    └── pr/                 外部 PR review 记录
        └── archives/
```

| 区域 | 提供什么 |
|---|---|
| `AGENTS.md`, `CLAUDE.md` | 将共同运营规则加载到 AI 编码 agent。`AGENTS.md` 是 source of truth，`CLAUDE.md` 委托给它。 |
| `.hyper-waterfall/version.json` | 记录已应用的框架 version 和所选 locale，并支持 update 判断。 |
| `.github/` | 固定 GitHub Issue Form 和 Pull Request 正文结构。 |
| `.agents/skills`, `.claude/skills` | 通过符号链接让 Codex 和 Claude Code 读取同一份 SKILL 文本。 |
| `mydocs/_templates/` | 固定计划书、报告、反馈、技术调查、故障排查、外部 PR review 的输出格式。 |
| `mydocs/manual/` | 存放重复适用的运营政策和流程。 |
| `mydocs/orders/`, `plans/`, `working/`, `report/` | 保存当前 task 状态、计划、Stage 进度、验证依据和最终交接上下文。 |
| `mydocs/feedback/`, `tech/`, `troubleshootings/`, `pr/` | 保存人的决策、调查、恢复知识和外部 PR review 记录。 |

应用仓库中的 `.agents/skills` 和 `.claude/skills` 符号链接结构遵循 [Agent Skills location policy](templates/locales/zh-CN/mydocs/manual/document_structure_guide.md)。`.hyper-waterfall/version.json` 和 manifest 基准 update 流程整理在 [distribution manifest and version record policy](templates/locales/zh-CN/mydocs/manual/document_structure_guide.md)、[`docs/lifecycle/update.zh-CN.md`](docs/lifecycle/update.zh-CN.md)、[`docs/lifecycle/update_pr.zh-CN.md`](docs/lifecycle/update_pr.zh-CN.md) 中。

框架的文档模板、GitHub Issue Form、SKILL source of truth 分别位于 `templates/mydocs/_templates/`、`templates/.github/ISSUE_TEMPLATE/task.yml`、`templates/mydocs/skills/`。在应用仓库中，`.agents/skills` 和 `.claude/skills` 符号链接会指向同一个 `mydocs/skills` 正文。

## 维护者细节

<details>
<summary><strong>更新已有应用仓库</strong></summary>

已有应用仓库的更新基于 GitHub Release/tag 和 manifest 执行。AI 以 [`docs/agent-entrypoint.zh-CN.md`](docs/agent-entrypoint.zh-CN.md) 为入口，按照 [`docs/lifecycle/update.zh-CN.md`](docs/lifecycle/update.zh-CN.md) 的既有更新判断结果格式，先报告当前 version、当前 locale、requested locale 或 switch request、目标 release/tag、目标 release locale support、migration guide、manifest diff、locale manifest diff、Hyper-Waterfall version update PR 候选。

将已批准的 update 候选转换为 PR 时，遵循 [`docs/lifecycle/update_pr.zh-CN.md`](docs/lifecycle/update_pr.zh-CN.md)。npm CLI 是让同一判断更容易执行的便利渠道，不替代 canonical 基准：GitHub Release/tag、`templates/manifest.json`、migration guide。不会只凭 CLI 输出自动应用文件，而是只把已批准范围转换为普通 task flow。

</details>

<details>
<summary><strong>CLI 与发布渠道</strong></summary>

`hyper-waterfall` CLI 通过 npm 分发，可使用固定 version 的 `npx` 命令执行 lifecycle 判断。`v0.3.0` release 状态和发布后验证结果在 [`docs/releases/v0.3.0.md`](docs/releases/v0.3.0.md) 中管理。

```bash
npx hyper-waterfall@0.3.0 init --repo . --dry-run
npx hyper-waterfall@0.3.0 update --repo . --from v0.2.0 --to v0.3.0 --dry-run
npx hyper-waterfall@0.3.0 doctor --repo .
```

macOS 可以通过 Homebrew public tap 安装 CLI。

```bash
brew install postmelee/tap/hyper-waterfall
hyper-waterfall --version
hyper-waterfall doctor --repo .
```

Homebrew、Docker、Codex plugin、Claude plugin 等其他发布渠道，也只被视为协议执行手段，不替代 canonical 基准。各渠道的目的、非目标、运营成本和优先级整理在 [`docs/distribution-channels.md`](docs/distribution-channels.md) 中。

这个 Homebrew formula 是安装 npm CLI 的 wrapper，不替代 canonical 基准：GitHub Release/tag、`templates/manifest.json`、migration guide。Homebrew 可以把 Node runtime 作为依赖安装。不指定 tap 的 `brew install hyper-waterfall` 路径需要进入 Homebrew core，但根据 [#46](https://github.com/postmelee/hyper-waterfall/issues/46) 的审查标准，目前保留 public tap 路径，不提交到 core。

</details>

---

## 附录

**Part 1. 最初的 Hyper-Waterfall** ([rhwp](https://github.com/edwardkim/rhwp))

1. [什么是 Hyper-Waterfall？](#什么是-hyper-waterfall)
2. [核心结构](#核心结构)
3. [核心原则](#核心原则)
4. [角色分工](#角色分工)
5. [Vibe Coding vs Hyper-Waterfall](#vibe-coding-vs-hyper-waterfall)
6. [为什么强大 — AI 让人到达原本到不了的地方](#为什么强大--ai-让人到达原本到不了的地方)

**Part 2. postmelee/hyper-waterfall**

1. [postmelee/hyper-waterfall：将方法论做成可复用 harness](#postmeleehyper-waterfall将方法论做成可复用-harness)
2. [活的示例 — 自己跟着看](#活的示例--自己跟着看)
3. [设计原则](#设计原则)
4. [提示指南对齐](#提示指南对齐)
5. [许可证](#许可证)

---

## 什么是 Hyper-Waterfall？

### 宏观 Waterfall + 微观 Agile：AI 让两者可以同时成立

Hyper-Waterfall 把 waterfall 的计划与验证纪律和 agile 的快速 task 反馈循环结合起来。AI 降低文档化、实现、验证和报告成本，使两者能在同一流程中共存。

> 这个方法论基于 [`edwardkim/rhwp`](https://github.com/edwardkim/rhwp) 和 [`postmelee/alhangeul-macos`](https://github.com/postmelee/alhangeul-macos) 等真实项目经验被提炼出来。
> 其核心哲学最完整地整理在 [edwardkim/rhwp · hyper_waterfall.md](https://github.com/edwardkim/rhwp/blob/main/mydocs/manual/hyper_waterfall.md)。本仓库把该方法论模块化，使其可以轻松应用到其他仓库。

如果想先理解方法论，请从 [核心结构](#核心结构) 开始；如果只想看本仓库的差异点，请跳到 [postmelee/hyper-waterfall：将方法论做成可复用 harness](#postmeleehyper-waterfall将方法论做成可复用-harness)。

## 核心结构

### 宏观 Waterfall + 微观 Agile

```text
宏观（项目层面）— waterfall 的纪律：
  计划 ──→ 设计 ──→ 实现 ──→ 验证 ──→ 发布
   │       │       │       │       │
   ▼       ▼       ▼       ▼       ▼
  文档化   文档化   文档化   文档化   文档化

微观（task 层面，数小时）— agile 的速度：
  实现 ──→ 测试 ──→ 反馈 ──→ 修改 ──→ 测试 → ...（快速迭代）
   │       │       │       │       │
  AI      自动化    人判断    AI      自动化
```

- 宏观方向用 **waterfall 的纪律**控制：计划书、审批、阶段报告、最终验证。
- 微观执行用 **agile 的快速迭代**推进：在工作允许时，通过 AI 和即时反馈循环让一个 task 周期在数小时内完成。
- 每个边界都会把重要上下文提炼为产出物，而不是只留在当前会话中。

每项工作都会成为文档，每项决策都保持可审查，每份文档都会成为后续工作的上下文。

## 核心原则

> **人不会停止思考。会话可以结束，但项目必须记住。**

无论 AI 多么优秀，决定方向和判断质量的都是人。不阅读 AI 输出就接受的瞬间，Hyper-Waterfall 就会退化成 vibe coding。把这个原则落到运营层面，就是下面三点。

### 1. 人把方向掌握到最后

Stage 切换、计划变更和有意义的源码修改都需要任务指示者明确批准。AI 支持并执行决策，但不拥有决策权。方向、优先级、架构和质量仍是人的责任。

### 2. 始终给 AI 足够上下文

意图、范围、计划、决策和验证标准被写入项目产出物，因此无需在每个 prompt 中从头解释。agent 读取相同的文档化上下文并从同一基线工作。上下文分散或缺失时，AI 会用猜测填补空白。

### 3. 定期把工作记忆提炼为项目记忆

Stage 报告、最终报告、commit、PR 正文会提炼并记录意图、决策、实现状态和验证依据。对话可能消失，但结构化项目产出物会留下。新会话、agent 和贡献者可以恢复关键上下文，并从文档化基线继续。

## 角色分工

### 任务指示者（人）

人专注于**思考和判断**：

- 方向设定：“下一步该做什么？”
- 优先级：“什么更重要？”
- 质量判断：“这是否足够好？”
- 架构决策：“这个结构是否正确？”
- 领域知识：“这个领域里这种情况应该如何表现？”
- 反馈：“这部分错了，因为……”

### AI 编码 Agent

AI 专注于**执行和结构化上下文记录**：

- 分析：探索代码库、追踪根因
- 计划：草拟 task plan 和 implementation plan
- 实现：编写代码、生成测试
- 验证：运行检查、收集依据
- 文档：Stage 报告、最终报告、技术文档、commit message
- 调试：分析日志、提出修正方案
- 迭代：反映反馈、重试

## Vibe Coding vs Hyper-Waterfall

> Vibe coding——不阅读 AI 输出就接受、让 AI 做架构决策、部署自己不理解的代码——是陷阱。表面上可能运行，但如果结果既不理解也不文档化，诊断和继续工作都会很脆弱。
>
> Hyper-Waterfall 采取相反方法。人类任务指示者保留方向、质量和架构的决策权，AI 快速执行。项目也保存审查和恢复该执行所需的上下文。
>
> — [edwardkim/rhwp · Vibe Coding vs AI-Driven Development](https://github.com/edwardkim/rhwp#%EB%B0%94%EC%9D%B4%EB%B8%8C-%EC%BD%94%EB%94%A9-vs-ai-%EC%A3%BC%EB%8F%84-%EA%B0%9C%EB%B0%9C)

| | Vibe Coding | Hyper-Waterfall |
|---|---|---|
| **人的角色** | 接受 AI 输出 | 指示、审查、决定 |
| **计划** | 无 — “直接做” | 执行计划书 -> 批准 -> 实现计划书 -> Stage 单位执行 |
| **质量门** | 希望它能工作 | 每个 Stage 验证 + 审批门 + Open PR review |
| **项目记忆** | 上下文留在聊天或某个人脑中 | 意图、决策、进度和依据被提炼到项目产出物 |
| **调试** | 没有持久诊断就让 AI 修 AI 的 bug | 保存诊断和理由，AI 实现已批准修复 |
| **架构** | 偶然形成 | 由任务指示者有意决定 |
| **文档** | 缺失或事后补写 | 在 task 全程产生 `mydocs/` 产出物和 Issue/PR 正文 |
| **交接** | 手动重新说明 | 新会话和贡献者从产出物恢复关键上下文 |
| **结果物** | 脆弱、难维护 | 可追踪、可审查、可交接、可恢复 |

## 为什么强大 — AI 让人到达原本到不了的地方

宏观 waterfall 和微观 agile 长期以来是一种 trade-off：纪律使工作变慢，速度又常削弱纪律。AI 编码 agent 降低计划、文档化、实现和验证成本，使两者能在同一工作流中实际并存。

### 1. 不失去速度，同时恢复纪律

waterfall 变重的一个主要原因是**人必须承担所有计划、文档、实现和验证**。AI 可以快速草拟和执行这些工作，让团队在不放弃快速迭代的情况下恢复纪律。

### 2. 把工作历史变成持久项目记忆

决策、依据、进度、验证结果、反馈和故障排查会留在 `mydocs/`、commit、PR、Issue 中。即使集中在某个人或会话中的上下文消失，下一个人或 AI 会话也能从**同一文档化基线**开始。

这不仅降低 bus-factor 风险，也让积累的工作历史成为未来 task 可复用的上下文。

### 3. 人专注决策，AI 专注执行

人始终负责方向、优先级、架构和质量，AI 负责探索、实现、测试、文档和反复迭代。一个人的注意力无法覆盖的工作量，会进入一个周期内。**AI 是倍增器**。把它放在好的流程之上，就能得到非凡结果。

### 4. 让工作跨会话、Agent、贡献者和地点移动

[rhwp](https://github.com/edwardkim/rhwp) 的维护者会在办公室、家里、移动中三个地点，用不同的 Claude 会话工作。每个新会话都没有之前的记忆。

但有文档时：

| 问题 | 答案 |
|---|---|
| “现在该做什么？” | `orders/20260409.md` |
| “做到哪里了？” | `working/task_m100_86_stage1.md` |
| “决定怎么做来着？” | `plans/task_m100_86_impl.md` |
| “为什么用这个方式？” | `feedback/` + `tech/` |
| “这个坑是什么？” | `troubleshootings/` |

工作本身持续产生交接材料，因此任务指示者手动传递上下文所需的时间大幅减少。

---

## postmelee/hyper-waterfall：将方法论做成可复用 harness

> 本仓库把 [rhwp](https://github.com/edwardkim/rhwp) 中最初引入的 Hyper-Waterfall 方法论扩展为可复用的 multi-agent 工作流 harness。

### 1. 用一行 prompt 应用到任何仓库 — 模块化 + placeholder 替换

原始方法论（rhwp）与该仓库的文档和惯例强绑定，很难直接搬到其他项目。本仓库把运营规则、manual、SKILL 分离到 `templates/`，并用 [`docs/agent-entrypoint.zh-CN.md`](docs/agent-entrypoint.zh-CN.md) 固定入口流程。结果是，**只要给 AI 编码工具一行 prompt**，就可以应用到任何仓库。AI 会按入口流程自动替换 `REPO_SLUG`、`BASE_BRANCH` 等 placeholder。

已有应用仓库更新的 lifecycle 基准也整理成独立文档。GitHub Release/tag、manifest、migration guide、`.hyper-waterfall/version.json` 用来先判断当前 version、当前 locale、requested locale 或 switch request、目标 release/tag、目标 release locale support、manifest diff、locale manifest diff、Hyper-Waterfall version update PR 候选。细节见 [`docs/lifecycle/update.zh-CN.md`](docs/lifecycle/update.zh-CN.md) 和 [`docs/lifecycle/update_pr.zh-CN.md`](docs/lifecycle/update_pr.zh-CN.md)。本仓库本身就是把该方法应用到自己的第一个 dogfooding 案例（Issue #1, PR #2）。

### 2. 让结构化项目产出物与官方提示指南对齐

工作文档格式被设计为自然满足 [OpenAI](https://developers.openai.com/api/docs/guides/prompt-guidance) 和 [Anthropic](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices) 官方提示指南的核心。尤其是 GitHub Issue/PR 模板负责结构化 GitHub 平台产出物，`templates/mydocs/_templates/` 则明确计划书、报告、反馈、外部 PR review 文档的输出格式。

> 在 AI 编写文档、再读取并把文档作为 reference 使用的递归过程中，这能尽量减少回答质量下降。

- **清晰性**：定义任务目标和边界。
- **一致性**：重复工作产出物共享中央格式。
- **分阶段推进**：把工作拆成小而可审查的 Stage。
- **上下文**：把关键信息记录在未来 agent 可以读取的位置。
- **输出格式**：把 task 结果变成可预测的项目产出物。
- **停止条件**：agent 在明确决策边界把控制权交还给人。

详细映射见 [提示指南对齐](#提示指南对齐)。

### 3. 用高 token/context 效率的规则支持多个 Agent

rhwp 把运营规则、文档结构、文件夹政策、命名规则、PR 处理都 inline 在一个 `CLAUDE.md` 文件中，且没有 `AGENTS.md`，因此是 Claude Code 专用。本仓库沿两个方向分离和扩展。

**(1) Multi-agent 兼容**：`AGENTS.md` 是单一 source of truth，`CLAUDE.md` 只用一行 `@AGENTS.md` 引用。SKILL 通过 `.agents/skills`（Codex）和 `.claude/skills`（Claude Code）符号链接，让两个工具识别同一正文。新的 SKILL 识别工具也可以用同一模式扩展。

**(2) 运营规则、SKILL、manual、template 分离**：`AGENTS.md` 只保留每轮系统 prompt 必须加载的政策、约束和索引。流程细节被分离到 [`mydocs/manual/`](templates/locales/zh-CN/mydocs/manual/) 下按主题拆分的 manual（文档结构、task 流程、Git、PR、lifecycle、release/update、冲突规则）、各 `mydocs/` 文件夹的 `README.md`、[`.github/`](templates/locales/zh-CN/.github/) 下的 GitHub Issue/PR 模板、[`mydocs/_templates/`](templates/locales/zh-CN/mydocs/_templates/) 下的文档输出格式、[`mydocs/skills/`](templates/locales/zh-CN/mydocs/skills/) 下的 7 个 SKILL。

效果：

- **token 效率**：减少每轮系统 prompt 加载的内容。manual 和 SKILL 正文只在调用时进入上下文。
- **context 效率**：模型只在需要时读取需要的流程。无关流程不会污染上下文。
- **意图传递清晰**：GitHub 模板和中央模板固定重复产出物结构，分阶段 SKILL 明确流程中何时调用，AI 不需要靠推断重建流程或输出格式。
- **模型间可移植性**：SKILL 是标准格式，容易移植到其他支持 SKILL 的工具。
- **共享上下文**：不同 agent 读取相同计划书、报告、决策和验证依据，而不是依赖工具专属聊天记录。

## 活的示例 — 自己跟着看

本仓库本身就是把 Hyper-Waterfall 应用到自身的第一个案例。如果在决定是否应用前想看真实运营如何运转，可以按下面顺序查看。

1. **Issue** [`#1` Hyper-Waterfall self-adoption (dogfooding)](https://github.com/postmelee/hyper-waterfall/issues/1) — 3 个 label、milestone M010、linked PR 自动显示的清晰结构（没有状态通知噪音评论）
2. **Pull Request** [`#2`](https://github.com/postmelee/hyper-waterfall/pull/2) — Open PR 正文格式：4 个摘要 bullet（目标 task/为什么/做了什么/review point）、Stage 5 个 timeline 双链接（阶段报告 + commit URL）、影响区域表、工作文档、验证结果和依据
3. **执行计划书** [`mydocs/plans/task_m010_1.md`](mydocs/plans/task_m010_1.md) — 目的、背景、范围、设计方向、预计变更文件、暂定阶段、验证计划、风险
4. **5 阶段实现计划书** [`mydocs/plans/task_m010_1_impl.md`](mydocs/plans/task_m010_1_impl.md) — 预先确定阶段产出物、验证命令、commit message
5. **5 个阶段报告** [`mydocs/working/`](mydocs/working/) — 每个 Stage 结束时的产出物、验证结果、残余风险、下一阶段影响
6. **最终报告** [`mydocs/report/task_m010_1_report.md`](mydocs/report/task_m010_1_report.md) — 5 阶段综合、变更前后定量比较、验收标准验证
7. **今日待办** [`mydocs/orders/`](mydocs/orders/) — 日板格式（按 milestone 分表 + 完成时间）
8. **commit log** [`git log` (main)](https://github.com/postmelee/hyper-waterfall/commits/main) — 从第一个 task commit 到 `pr-merge-cleanup`，12 个 task commit 按时间顺序保留

第一个 task 经历了两次 scope 扩展，并以 5 个阶段推进。审批门、Stage 边界的上下文提炼、scope 变更处理、PR 正文重写和 merge 后清理，都可以通过活的产出物查看。

## 设计原则

- 关键任务上下文必须比产生它的会话保留得更久。
- 结构化项目产出物而不是原始聊天记录，是可恢复工作的 source of truth。
- 有意义的源码变更需要人的决策门。
- 任务指示者保留方向、优先级、架构和质量的决策权。
- 最新状态应该能从 Issue metadata、当前 branch 或 PR、`mydocs/` 找到。
- Issue 进展追踪委托给 GitHub 的 linked PR 自动 cross-reference、label 和 milestone；评论只用于讨论、blocker、决策记录。
- 这个框架必须适用于多种项目类型。特定语言、构建、发布、产品规则应放在目标仓库的模板和设置中，而不是 core 中。
- 对流程严格，对工具灵活。

> Hyper-Waterfall 不是新魔法。它把 AI 作为倍增器，放在保存人的判断、持久工作历史、验证依据和交接上下文的流程之上。

## 提示指南对齐

Hyper-Waterfall 在开发流程层面实现 OpenAI 和 Anthropic 官方提示指南的核心。它不只追求一次好的 prompt，而是创建一种**由工作流反复产生良好上下文、清晰输出、验证和停止条件的项目结构**。

### 对齐摘要

| 原则 | Hyper-Waterfall 中的实现方式 | 效果 |
|---|---|---|
| 清晰目标 | GitHub Issue、执行计划书、实现计划书 | AI 先理解工作范围和成功标准。 |
| 充分上下文 | `mydocs/` 中的计划书、报告、反馈、技术调查 | 新会话从项目产出物恢复关键上下文。 |
| 输出格式约束 | `mydocs/_templates/`、Issue/PR template | 计划、报告、验证结果每次都按相同结构留下。 |
| 分阶段推进 | Stage 单位实现、验证、报告 | 复杂工作被拆成可 review 单位。 |
| 验证标准 | Stage 报告、最终报告、PR 正文 | 结果不是凭感觉判断，而是依据记录的标准。 |
| 停止条件 | 人的决策门 | AI 不会任意进入下一阶段。 |
| 持久项目记忆 | `mydocs/`、commit history、Issue/PR timeline | 聊天消失后关键工作上下文仍然保留。 |
| 轻量上下文 | `1 Issue = 1 Task = 1 Branch = 1 Session` | 会话保持小而清晰。 |
| Multi-agent 连续性 | 共享规则、SKILL、manual 和产出物 | 不同 agent 从同一基线继续工作。 |

<details>
<summary><strong>OpenAI prompt guidance 映射</strong> · 来源: <a href="https://developers.openai.com/api/docs/guides/prompt-guidance">OpenAI prompt guidance</a></summary>

1. **先确定产出物。**
   Hyper-Waterfall 从任务开始就明确 Issue、执行计划书、实现计划书、Stage 报告、最终报告、PR 这些产出物。不是让 AI “做好一点”，而是先固定必须留下什么。

2. **写明好回答的标准。**
   每个 Stage 不只留下实现，也留下验证标准和 review point。因此 AI 结果不是凭感觉评价，而是在文档化标准上判断。

3. **设置简短约束。**
   Hyper-Waterfall 明确 AI 不应越过的边界，例如“不经批准不得进入下一 Stage”“源码修改前先批准”“按 Issue 追踪”。这不是消除自由度，而是铺设防止失控的轨道。

4. **说明需要的依据层级。**
   实现结果会被提炼成 Stage 报告、验证日志、PR 正文。仓库里留下的不只是代码变更，还有为什么变更、如何确认。

5. **指定输出格式。**
   `mydocs/_templates/` 固定执行计划书、实现计划书、阶段报告、最终报告、反馈、技术调查、故障排查、外部 PR review 文档的 expected output shape。PR 正文由 `.github/pull_request_template.md` 按 review 画面结构化。AI 的回答不再散乱，而是成为下一个工作者能再次阅读的结构。

6. **告诉模型何时停止。**
   Hyper-Waterfall 在每个 Stage 边界停止，并等待人的批准。AI 不是一路跑到底，而是在可以由人确认方向的停止线前停下。

</details>

<details>
<summary><strong>Anthropic Claude prompting best practices 映射</strong> · 来源: <a href="https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices">Claude prompting best practices</a></summary>

1. **清晰直接的指令。**
   任务意图通过 Issue、执行计划书、实现计划书在每个阶段被明确化。不是把模糊意图丢给模型，而是在 gate 前固定要做什么、为什么做、做到哪里。

2. **提供 workflow 和目标上下文。**
   用户不需要每次 prompt 都说明工作属于哪个流程、结果物放在哪里。`mydocs/`、Issue、PR 正文中已经嵌入这些上下文，模型会自然读取同一上下文。

3. **顺序化步骤。**
   Stage 单位推进和每阶段审批门，直接实现了把指令拆成顺序步骤的建议。

4. **控制输出格式。**
   执行计划书、阶段报告、最终报告、反馈、技术调查、外部 PR review 文档遵循 `mydocs/_templates/` 的 desired output format，PR 正文遵循 `.github/pull_request_template.md`。模型不需要每次发明“哪里写什么”。

5. **长期工作与外部记忆。**
   `mydocs/` 直接对应 long-horizon agentic work 和 memory task。即使聊天上下文消失，工作记忆也会被提炼并留在文件系统中。

6. **Literal 指令遵循与对齐。**
   更 literal 的模型往往更准确地绑定到明确范围。Hyper-Waterfall 先把“源码修改前批准”“未经批准不得进入下一 Stage”“按 Issue 追踪”等边界文档化，因此越 literal 的模型越容易良好运行。

> Hyper-Waterfall 优先考虑人的控制权、持久工作历史和可追踪性，而不是最大自律性。它在一次性 interactive coding 之上增加项目级 task 边界和产出物要求。文件夹结构、文件名规则和中央 template 提供跨完整 task 生命周期的结构作用，这不是单靠 inline prompt 格式能完成的。
>
> **一句话总结**：Hyper-Waterfall 把 prompting best practices 实现为可重复、由人治理的 AI 编码工作流，而不是一句 prompt。

</details>

## 许可证

MIT。详情见 [LICENSE](LICENSE)。
