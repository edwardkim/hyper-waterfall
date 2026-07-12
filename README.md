# Hyper-Waterfall

English | [한국어](README.ko.md) | [简体中文](README.zh-CN.md)

<!-- ![Hyper-Waterfall overview](docs/assets/hyper-waterfall.png) -->

## From Ephemeral Sessions to Persistent Project Memory

Hyper-Waterfall is a **human-governed AI coding workflow** that distills ephemeral session context into persistent project memory—making work traceable, reviewable, and resumable.

Instead of leaving task context trapped in a temporary chat, Hyper-Waterfall periodically captures what matters—intent, scope, plans, decisions, implementation progress, and verification evidence—as structured project artifacts such as Issues, plans, Stage reports, commits, and PRs.

These artifacts are not passive logs. Together, they become shared project memory that helps a new session, agent, or contributor recover the essential context and continue from a documented baseline without replaying chat history.

> **The session ends. The project remembers.**
>
> Every task becomes documentation, and every document becomes context for what comes next.

| Hyper-Waterfall Core | Meaning |
|---|---|
| Context distillation | Essential task context is extracted from temporary sessions and recorded as structured project artifacts. |
| Persistent project memory | Intent, decisions, progress, and verification evidence remain available after the session ends. |
| Human governance | Humans retain ownership of direction, scope, architecture, and quality; AI handles execution within explicit boundaries. |
| Staged execution | Large work is split into reviewable Stages, each with verification and a recorded completion report. |
| Resumable work | New sessions, agents, and contributors can recover essential context from project artifacts and continue the work. |

Hyper-Waterfall recommends **`1 Issue = 1 Task = 1 Branch = 1 Session`** to keep sessions intentionally small. A session can end cleanly because its essential context has already been distilled into the project.

> [!IMPORTANT]
> **Delegate execution to AI, but do not delegate decision ownership.**
>
> Hyper-Waterfall does not make AI magically capable of anything. It gives AI clear rails so it can move quickly without causing humans to lose direction or project context.

## Quick Start

### Existing repository

Send this one line to your AI coding tool.

```text
Apply the Hyper-Waterfall methodology from https://github.com/postmelee/hyper-waterfall to this repository.
```

### New project

When your project idea is ready to become a repository, create an empty GitHub or local repository first. Then send this prompt from that empty repository.

```text
I am starting a new project in this empty repository.

Apply the Hyper-Waterfall methodology from https://github.com/postmelee/hyper-waterfall to this repository first.

If a project brief or requirements draft is attached, use it for context only. Do not create product plans, architecture documents, or source code during adoption. After adoption, help me register the first product task as a separate GitHub Issue.
```

In both paths, the AI starts from [`docs/agent-entrypoint.en.md`](docs/agent-entrypoint.en.md) and follows the adoption procedure. It must report the proposed scope and receive approval before changing source files.

| What the AI reports first | Content |
|---|---|
| Adoption mode | Whether this is a new adoption or an update to an existing Hyper-Waterfall installation. |
| Change candidates | Which files it would create or modify, and whether placeholder substitution is needed. |
| Approval request | The scope the task requester must approve before actual file changes. |

### Language support

The default locale is `en`. Supported locale packs are `en`, `ko`, and `zh-CN`; missing locale sources are reported before fallback candidates are used.

| Language | Locale |
|---|---|
| English | `en` |
| Korean | `ko` |
| Simplified Chinese | `zh-CN` |

When using an AI coding tool, ask in the language you want to use. The AI reports the selected locale before changing files.

To check adoption from a terminal, pass the locale explicitly. Replace `en` with `ko` or `zh-CN` as needed.

```sh
npx hyper-waterfall@0.3.0 init --repo . --locale en --dry-run
```

On macOS, install the CLI with Homebrew if you run it often.

```sh
brew install postmelee/tap/hyper-waterfall
hyper-waterfall init --repo . --locale en --dry-run
```

The `npx` and Homebrew CLI commands print lifecycle judgment only. Actual file changes still move through the approval workflow.

After adoption, the AI proceeds according to the Hyper-Waterfall process. New users can simply ask the AI in natural language, such as `"Implement this."`

> Hyper-Waterfall lets anyone apply the method to a GitHub repository and makes multiple AI coding agents, including Codex and Claude Code, work under the same discipline and shared context.

## Learn More About Hyper-Waterfall

[Why Hyper-Waterfall?](#why-hyper-waterfall) ·
[When to Use](#when-to-use) ·
[Compared with Conventional AI Coding](#compared-with-conventional-ai-coding) ·
[What Changes Immediately](#what-changes-immediately) ·
[Strengths of Hyper-Waterfall](#strengths-of-hyper-waterfall) ·
[Workflow After Adoption](#workflow-after-adoption) ·
[Target Repository Structure After Adoption](#target-repository-structure-after-adoption)

## Why Hyper-Waterfall?

AI coding agents have two structural weaknesses:

- Session context is temporary and becomes less reliable as conversations grow or tools change.
- AI can continue executing confidently even when the direction is wrong.

Hyper-Waterfall turns both weaknesses into workflow constraints. It distills work memory into project artifacts and places AI execution inside human decision gates.

| Problem | Hyper-Waterfall Constraint | Result |
|---|---|---|
| Context disappears with the session | Intent, decisions, progress, and verification are recorded in structured artifacts | Persistent project memory |
| Long sessions become noisy | Recommended model: `1 Issue = 1 Task = 1 Branch = 1 Session` | Small, focused context |
| AI can run quickly in the wrong direction | Plans and Stage boundaries require human review | Direction errors are caught earlier |
| Each agent invents its own process | Shared rules, SKILLs, manuals, and templates | Consistent execution across agents |
| Reviewers must reconstruct history from chat | Reports, commits, and PRs preserve rationale and evidence | Traceable and reviewable work |

The result is not merely an approval-driven coding tool. It is a workflow for converting temporary AI execution into durable, reusable project knowledge while humans keep control of the decisions that matter.

## When to Use

Hyper-Waterfall is designed for real source changes where work must remain understandable and resumable beyond a single AI session.

| Good Fit | Poor Fit |
|---|---|
| Work must continue across multiple days, sessions, agents, or contributors. | A one- or two-line change where plan and report overhead is larger than the change itself. |
| You want task intent, decisions, progress, and verification to remain as reusable project context. | Disposable prototypes where immediate experimentation matters more than traceability. |
| You let an AI coding tool modify real source code, but humans must retain control of scope and quality. | Work where humans intend to accept AI output without review. |
| PR reviewers need to see what changed, why it changed, and how it was verified. | Personal experiments where handoff or resumability does not matter. |
| You want to split large work by Issue, branch, and Stage so wrong direction is caught early. | Repositories that do not use the GitHub Issue, branch, and PR workflow assumed by the current implementation. |
| New contributors or AI sessions must restart from project artifacts alone. | Tasks where preserving decisions and work history has no value. |

> Hyper-Waterfall is most useful when AI performs substantial implementation work while humans must preserve decision ownership, engineering context, and reviewability. It can be too heavy when immediate experimentation matters more than continuity.

## Compared with Conventional AI Coding

The key difference is not whether AI asks for permission before executing a command. It is whether the project can preserve, review, and reuse the context behind the work after the session is gone.

Conventional AI coding often depends on the flow of one conversation. Hyper-Waterfall fixes task units, decision gates, artifact formats, and context handoff rules at the project level.

| Conventional AI Coding | After Applying Hyper-Waterfall |
|---|---|
| You say “build this,” and AI edits files immediately. | An Issue and task plan first define purpose, scope, and verification criteria. |
| Scope keeps shifting during conversation. | The implementation plan splits work into Stages, and execution stays inside the approved scope. |
| Task context is trapped in a temporary chat session. | Essential context is distilled into `mydocs/`, Issues, PRs, and commit history. |
| It is hard to trace later which files AI changed and why. | Stage reports and commits record the rationale, artifact, and verification result for each change. |
| Wrong direction is discovered only after a large implementation. | The task requester approves or redirects at the task plan, implementation plan, and Stage boundaries. |
| A new session or agent must be briefed manually. | Project artifacts provide the essential context and next action. |
| PR reviewers need to search through chat logs again. | The PR and reports show what changed, why it changed, and how it was verified. |

The human task requester keeps ownership of direction, priority, architecture, and quality decisions. AI performs exploration, drafting, implementation, verification, and documentation at a speed and scale humans cannot reach alone.

> [!IMPORTANT]
> **Key difference: humans never stop thinking, and the project never depends on one session remembering everything.**

## What Changes Immediately

1. **Session context becomes persistent project memory.**
   Intent, scope, decisions, progress, and verification evidence remain in `mydocs/`, Issues, PRs, and commit history. A new session, agent, or contributor can continue without replaying chat history.

2. **“Where did we stop?” has a documented answer.**
   The Issue, today's todo, task plan, implementation plan, Stage reports, final report, commits, and PR form a recoverable task timeline.

3. **Sessions stay small and focused.**
   The recommended operation is `1 Issue = 1 Task = 1 Branch = 1 Session`. When a task ends, the session closes; the next task starts in a clean session with documented context available on demand.

4. **AI does not modify code arbitrarily.**
   Source changes pass through a plan and human decision gate first, so the task requester keeps control of direction and scope.

5. **Humans do not lose decision ownership.**
   Gates stand before source edits, Stage transitions, final reporting, and PR creation. AI executes, but humans judge direction, architecture, and quality.

6. **Multiple AI sessions can work in parallel.**
   Independent Issues can run in separate `local/task{N}` branches or separate worktrees. Their context and change scope remain isolated.

7. **PR review becomes easier.**
   The PR explains what changed, why it changed, which Stages were completed, and what verification ran. Reviewers inspect project artifacts instead of reconstructing the work from chat.

8. **Direction errors are found earlier.**
   Task plans, implementation plans, and Stage completion reports act as human-reviewed quality gates before large amounts of work accumulate in the wrong direction.

9. **Engineering discipline no longer requires losing AI speed.**
   AI drafts plans, tests, reports, and implementation quickly, while the workflow preserves evidence, rationale, and handoff context.

10. **AI coding becomes a reusable project process rather than a disposable conversation.**
    Every task connects through Issue, branch, document, commit, and PR so the work can be traced, reviewed, resumed, and used as context for what comes next.

## Strengths of Hyper-Waterfall

### 1. Distill Session Context into Persistent Project Memory — Knowledge Captured as Assets

- Task intent, constraints, plans, decisions, Stage-by-Stage progress, verification results, and troubleshooting knowledge accumulate as structured project artifacts.
- These artifacts are not passive records. They are **input for the next task**, allowing future sessions and contributors to build on previous work rather than reconstruct it from scratch.
- The workflow preserves the parts of the session that matter without requiring the raw conversation to become the project's source of truth.

> `mydocs/` works like a vault specialized for work history. Unlike a general knowledge vault, it accumulates task intent, plans, decisions, verification, artifacts, feedback, and troubleshooting in formats enforced by the process.

### 2. Catch Direction Errors at Gates Before They Become Large Failures — Risk Control

- Work follows `Issue -> branch -> task plan -> implementation plan -> Stage implementation, verification, and report -> final report -> Open PR`.
- Human review occurs at the task plan, implementation plan, each Stage boundary, and final report.
- If Stage verification fails, recovery happens inside that Stage. If scope changes, the plan is updated and re-approved.
- This catches semantic errors—wrong goals, wrong scope, wrong architecture direction—that code review alone may not detect early.

### 3. Do Not “Ask AI Nicely”; Make Good Work Structurally Likely — Automated Role Split

- The task requester retains responsibility for **direction, priority, architecture, and quality decisions**.
- AI handles high-repetition execution such as exploration, drafting, implementation, tests, reports, and PR body preparation.
- SKILLs define what the agent should do at each step, which artifacts it must leave, and when it must stop and return control to the human.
- Central templates define the expected output shape so agents do not reinvent plans, reports, or verification formats on every task.

### 4. Keep Sessions Small; Keep Memory in the Project — Lightweight Context

- Hyper-Waterfall does not accumulate all project history inside one AI session. One session owns one Issue and closes when that task ends.
- Each session reads only the current Issue, relevant plans, Stage reports, related project documents, and code.
- Previous decisions remain available through project artifacts without polluting every prompt or relying on an increasingly blurry conversation.
- Independent Issues can run in parallel across separate branches or worktrees when their change scopes do not conflict.

> AI sessions do not necessarily become smarter as they grow longer. They often become less focused. Hyper-Waterfall keeps sessions short and leaves memory in the project.

### 5. Result

These strengths form one loop:

```text
Temporary session context
        ↓ distill
Structured project artifacts
        ↓ accumulate
Persistent project memory
        ↓ restore
Next session, agent, contributor, or task
```

At the same time, human decision gates keep AI execution aligned with project direction.

As a result, AI coding becomes a human-governed workflow with persistent project memory—traceable, reviewable, and resumable across sessions, agents, and contributors.

> [!NOTE]
> This structure aligns with the official OpenAI and Anthropic prompting guides: clear instructions, sufficient context, output-format constraints, verification criteria, stop conditions, long-term work memory, and agentic workflow control. See [Prompt Guide Alignment](#prompt-guide-alignment) for the detailed mapping.

## Workflow After Adoption

Hyper-Waterfall works in **task** units. Each task both produces code and distills the context required to understand, verify, and continue that work.

### Task Procedure

Every task follows this procedure **strictly**.

```text
1. Confirm or register a GitHub Issue
2. Record today's todo (mydocs/orders/)
3. Create task branch (local/task{number})
4. Write task plan -> [task requester approval]
5. Write implementation plan -> [task requester approval]
6. Implement by Stage
7. Write Stage completion report -> [task requester approval]
8. Repeat next Stage
9. Write final result report -> [task requester approval]
10. Update today's todo status
```

> Each `[approval]` point is both a decision gate and a context-distillation boundary. Direction errors are reviewed, and the current state is recorded before the work advances.

Detailed procedure follows the [task workflow manual](templates/locales/en/mydocs/manual/task_workflow_guide.md). Branch and PR publication flow is described in the [Git workflow manual](templates/locales/en/mydocs/manual/git_workflow_guide.md).

### Core SKILL Details

| SKILL | When to Use | Main Artifacts |
|---|---|---|
| `task-register` | When a new task needs a GitHub Issue first | A GitHub Issue following the `task.yml` Issue Form structure, milestone and label candidates, and selection rationale |
| `task-start` | When starting work on an approved Issue | `local/task{N}` branch, today's todo row, task plan based on `task_plan.md` |
| `task-stage-report` | After one Stage is implemented and before moving to the next Stage | Stage report based on `stage_report.md`, Stage bundle commit, Stage verification result |
| `task-final-report` | After all Stages are complete and just before publishing the PR | Final report based on `final_report.md`, today's todo completion update, Open PR |
| `pr-merge-cleanup` | Immediately after a PR is actually merged | Issue close, `publish/task{N}` remote deletion, local branch/worktree cleanup |
| `external-pr-review` | When reviewing an external contributor PR | `mydocs/pr/` review documents based on `external_pr_*` templates, verification result, recommendation (merge/request changes/close) |
| `todo` | When creating or updating today's todo board | `mydocs/orders/yyyymmdd.md` table update based on `orders.md` |

When each SKILL should be displayed to the user follows the [SKILL call display guide](templates/locales/en/mydocs/manual/task_workflow_guide.md). PR body structure and verification follow the [internal task PR guide](templates/locales/en/mydocs/manual/internal_pr_guide.md), and PR creation commands plus document link formats follow the [PR command and link guide](templates/locales/en/mydocs/manual/pr_command_guide.md).

Document structure and manual-document neutrality are checked in the [document structure manual](templates/locales/en/mydocs/manual/document_structure_guide.md), not through a separate SKILL.

### Task Cycle

If an Issue already exists, skip `task-register` and go directly to `task-start` to write the task plan. For example, when the task requester says `"work on issue #17"`, AI checks the milestone and Issue body for #17, then creates `local/task17`, today's todo, and the task plan.

Only when no Issue exists does `task-register` check duplicate Issues, milestone, and labels, ask for approval before creation, and then create the GitHub Issue.

Every Stage transition requires explicit approval from the task requester.

```text
0. Task registration -> `task-register`
   └─ AI: check duplicate Issues, milestone, and label candidates
   └─ task requester: approve Issue creation
   └─ AI: create GitHub Issue and request approval to enter `task-start`

1. Task plan -> `task-start`
   └─ task requester: specify an existing Issue such as "work on issue #N",
      or approve starting from the newly created Issue
   └─ AI: write plan (minimum 3 Stages, maximum 6 Stages)
   └─ task requester: review -> approve or request edits

2. Stage implementation -> `task-stage-report` (repeat for each Stage)
   └─ AI: write code + run tests
   └─ AI: distill implementation state and verification into a Stage report
   └─ task requester: verify -> approve or give feedback

3. Feedback application -> manual
   └─ task requester: write feedback in mydocs/feedback/
   └─ AI: apply feedback and revise
   └─ if scope changes: update the plan and receive re-approval

4. Final report + Open PR -> `task-final-report`
   └─ AI: synthesize the task into a final report
   └─ AI: create an Open PR with structured verification evidence
   └─ task requester: verify -> approve or give feedback

5. PR review + merge + cleanup -> `pr-merge-cleanup`
   └─ task requester: review PR -> approve or give feedback
   └─ AI: after review and merge, close Issue and clean branches/today's todo
```

`todo` is called whenever today's todo board is updated in the above flow. `external-pr-review` is a separate flow for reviewing external contributor PRs.

### Document Structure

Documents used or produced by tasks:

```text
mydocs/
├── _templates/                         <- output formats by artifact type
├── orders/yyyymmdd.md                  <- today's todo (task list + status)
├── plans/task_{milestone}_{N}.md       <- task plan
├── plans/task_{milestone}_{N}_impl.md  <- implementation plan
├── working/task_{milestone}_{N}_stage{S}.md
│                                        <- Stage completion report
├── report/task_{milestone}_{N}_report.md
│                                        <- final result report
├── feedback/                           <- feedback and review notes
├── tech/                               <- technical research and pre-official drafts
├── manual/                             <- operating manuals and repeated work standards
├── troubleshootings/                   <- troubleshooting
└── pr/                                 <- external PR review records
```

Together, these documents preserve different parts of durable work history:

| Area | Memory Preserved |
|---|---|
| `orders/` | Current task state and what should happen next |
| `plans/` | Intent, scope, decisions, implementation sequence, and verification criteria |
| `working/` | Stage-level progress, artifacts, evidence, residual risks, and next-stage context |
| `report/` | Final synthesis, acceptance status, and handoff context |
| `feedback/` | Human review, corrections, and decision rationale |
| `tech/` | Research, alternatives, and design reasoning not yet promoted to official documentation |
| `troubleshootings/` | Known failure modes, diagnosis, and recovery knowledge |
| `pr/` | External contribution review evidence and recommendations |

Folder roles, document filename rules, and artifact output formats are defined in the [document structure manual](templates/locales/en/mydocs/manual/document_structure_guide.md). Each folder's detailed writing rules are checked from that folder's `README.md`.

| Area | Policy |
|---|---|
| `mydocs/` | Stores project work memory, operating manuals, and research evidence. It is not the official product documentation root of the target project. |
| Official product docs | Hyper-Waterfall does not fix the official documentation root name. A target project may choose `docs/`, `specs/`, `site/`, `website/`, `adr/`, GitHub Wiki, or another path. Tasks that create, move, or edit product/user/contributor/API/architecture/roadmap docs must first get approval in the task plan's document-location decision, including target audience, officialization level, selected path, alternative path, and reason. |
| `manual/` | Contains recurring operating standards and procedures. Records for a specific Issue, PR, release verification, or incident are separated into the corresponding artifact document. Details follow the [manual document neutrality policy](templates/locales/en/mydocs/manual/document_structure_guide.md). |
| `tech/` | Contains technical research, alternative comparisons, design rationale, and drafts that are not yet official. To promote them into official contract docs for users or external integrators, open a separate task, choose the official docs root, and receive approval. |
| `_templates/` | The source of truth for artifact output formats, not an actual task-artifact folder. Each SKILL reads the corresponding template in `mydocs/_templates/` first and uses the minimal section summary inside the SKILL only as fallback when the template cannot be read. |
| GitHub Issue and Pull Request | GitHub platform artifacts. Issue bodies follow `.github/ISSUE_TEMPLATE/task.yml`, PR bodies follow `.github/pull_request_template.md`, and project-resident work documents follow `mydocs/_templates/`. Details follow the [GitHub platform template policy](templates/locales/en/mydocs/manual/document_structure_guide.md). |

## Target Repository Structure After Adoption

After `templates/` is copied and placeholders are replaced, the target repository looks like this.

```text
your-repo/
├── AGENTS.md                       single source of truth for operating rules
├── CLAUDE.md                       for Claude Code (references AGENTS.md)
├── .hyper-waterfall/
│   └── version.json                 records the applied Hyper-Waterfall version and locale
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   └── task.yml
│   └── pull_request_template.md
├── .agents/
│   └── skills -> ../mydocs/skills  Codex recognition path (symlink)
├── .claude/
│   └── skills -> ../mydocs/skills  Claude Code recognition path (symlink)
└── mydocs/
    ├── _templates/         output format templates by artifact type
    ├── manual/             operating manuals (document structure, task workflow, Git, PR, lifecycle, release/update, conflict rules)
    ├── skills/             SKILL source of truth (shared by Codex/Claude Code)
    ├── orders/             today's todo (yyyymmdd.md)
    ├── plans/              task and implementation plans
    │   └── archives/
    ├── working/            Stage completion reports
    ├── report/             final result reports
    ├── feedback/           feedback and review notes
    ├── tech/               technical research and pre-official drafts
    ├── troubleshootings/   troubleshooting
    └── pr/                 external PR review records
        └── archives/
```

| Area | What It Provides |
|---|---|
| `AGENTS.md`, `CLAUDE.md` | Loads common operating rules into AI coding agents. `AGENTS.md` is the source of truth, and `CLAUDE.md` delegates to it. |
| `.hyper-waterfall/version.json` | Records the applied framework version and selected locale, then supports update judgment. |
| `.github/` | Fixes the GitHub Issue Form and Pull Request body structure. |
| `.agents/skills`, `.claude/skills` | Lets Codex and Claude Code read the same SKILL text through symlinks. |
| `mydocs/_templates/` | Fixes output formats for plans, reports, feedback, technical research, troubleshooting, and external PR reviews. |
| `mydocs/manual/` | Contains repeated operating policies and procedures. |
| `mydocs/orders/`, `plans/`, `working/`, `report/` | Stores current task state, plans, Stage progress, evidence, and final handoff context. |
| `mydocs/feedback/`, `tech/`, `troubleshootings/`, `pr/` | Stores human decisions, research, recovery knowledge, and external PR review records. |

The symlink structure for `.agents/skills` and `.claude/skills` in the adopted repository follows the [Agent Skills location policy](templates/locales/en/mydocs/manual/document_structure_guide.md). `.hyper-waterfall/version.json` and manifest-based update flow are documented in the [distribution manifest and version record policy](templates/locales/en/mydocs/manual/document_structure_guide.md), [`docs/lifecycle/update.en.md`](docs/lifecycle/update.en.md), and [`docs/lifecycle/update_pr.en.md`](docs/lifecycle/update_pr.en.md).

The framework's document templates, GitHub Issue Form, and SKILL source of truth are `templates/mydocs/_templates/`, `templates/.github/ISSUE_TEMPLATE/task.yml`, and `templates/mydocs/skills/`. In an adopted repository, `.agents/skills` and `.claude/skills` symlinks point to the same `mydocs/skills` text.

## Maintainer Details

<details>
<summary><strong>Updating Existing Adopted Repositories</strong></summary>

Existing adopted repositories are updated based on GitHub Releases/tags and the manifest. AI uses [`docs/agent-entrypoint.en.md`](docs/agent-entrypoint.en.md) as the entry point and follows the existing-update judgment format in [`docs/lifecycle/update.en.md`](docs/lifecycle/update.en.md), first reporting current version, current locale, requested locale or switch request, target release/tag, target-release locale support, migration guide, manifest diff, locale manifest diff, and Hyper-Waterfall version-update PR candidates.

When converting approved update candidates into a PR, follow [`docs/lifecycle/update_pr.en.md`](docs/lifecycle/update_pr.en.md). The npm CLI is a convenience execution channel for the same judgment and does not replace the canonical basis: GitHub Release/tag, `templates/manifest.json`, and migration guide. CLI output alone does not automatically apply files; only approved scope is converted into the normal task flow.

</details>

<details>
<summary><strong>CLI and Distribution Channels</strong></summary>

The `hyper-waterfall` CLI is distributed through npm and can run lifecycle judgment through version-pinned `npx` commands. The `v0.3.0` release status and post-publish verification results are tracked in [`docs/releases/v0.3.0.md`](docs/releases/v0.3.0.md).

```bash
npx hyper-waterfall@0.3.0 init --repo . --dry-run
npx hyper-waterfall@0.3.0 update --repo . --from v0.2.0 --to v0.3.0 --dry-run
npx hyper-waterfall@0.3.0 doctor --repo .
```

On macOS, you can install the CLI through the public Homebrew tap.

```bash
brew install postmelee/tap/hyper-waterfall
hyper-waterfall --version
hyper-waterfall doctor --repo .
```

Additional distribution channels such as Homebrew, Docker, Codex plugin, and Claude plugin are treated only as protocol execution channels that do not replace the canonical basis. Channel purpose, non-goals, operating cost, and priority are summarized in [`docs/distribution-channels.md`](docs/distribution-channels.md).

This Homebrew formula is a wrapper that installs the npm CLI and does not replace the canonical basis: GitHub Release/tag, `templates/manifest.json`, and migration guide. Homebrew may install the Node runtime as a dependency. The path `brew install hyper-waterfall` without specifying a tap requires inclusion in Homebrew core, but as of the review criteria in [#46](https://github.com/postmelee/hyper-waterfall/issues/46), this repository keeps the public tap path and does not submit to core.

</details>

---

## Appendix

**Part 1. The Original Hyper-Waterfall** ([rhwp](https://github.com/edwardkim/rhwp))

1. [What Is Hyper-Waterfall?](#what-is-hyper-waterfall)
2. [Core Structure](#core-structure)
3. [Core Principles](#core-principles)
4. [Role Split](#role-split)
5. [Vibe Coding vs Hyper-Waterfall](#vibe-coding-vs-hyper-waterfall)
6. [Why It Is Powerful — The Point AI Makes Reachable](#why-it-is-powerful--the-point-ai-makes-reachable)

**Part 2. postmelee/hyper-waterfall**

1. [Turning the Methodology into a Reusable Harness](#postmeleehyper-waterfall-turning-the-methodology-into-a-reusable-harness)
2. [Live Example — Follow It Yourself](#live-example--follow-it-yourself)
3. [Design Principles](#design-principles)
4. [Prompt Guide Alignment](#prompt-guide-alignment)
5. [License](#license)

---

## What Is Hyper-Waterfall?

### Macro Waterfall + Micro Agile: AI Makes Both Possible at the Same Time

Hyper-Waterfall combines waterfall's planning and verification discipline with agile's fast task-level feedback loops. AI makes the documentation, implementation, verification, and reporting workload fast enough for both to coexist in the same process.

> This methodology was refined from real project experience such as [`edwardkim/rhwp`](https://github.com/edwardkim/rhwp) and [`postmelee/alhangeul-macos`](https://github.com/postmelee/alhangeul-macos).
>
> Its core philosophy is captured most completely in [edwardkim/rhwp · hyper_waterfall.md](https://github.com/edwardkim/rhwp/blob/main/mydocs/manual/hyper_waterfall.md). This repository modularizes that methodology so it can be applied more easily to other repositories.

To understand the methodology first, start with [Core Structure](#core-structure). To see what this repository adds, jump to [Turning the Methodology into a Reusable Harness](#postmeleehyper-waterfall-turning-the-methodology-into-a-reusable-harness).

## Core Structure

### Macro Waterfall + Micro Agile

```text
Macro (project level) — waterfall discipline:
  Plan ──→ Design ──→ Implement ──→ Verify ──→ Release
   │        │          │             │          │
   ▼        ▼          ▼             ▼          ▼
  Docs     Docs       Docs          Docs       Docs

Micro (task level, hours) — agile speed:
  Implement ──→ Test ──→ Feedback ──→ Revise ──→ Test → ... (fast iteration)
      │          │          │           │          │
      AI      automation  human judgment AI      automation
```

- Macro direction is controlled by **waterfall discipline**: plans, approvals, staged reporting, and final verification.
- Micro execution uses **agile fast iteration**: AI and immediate feedback loops, with a task cycle completing within hours when the work allows it.
- At each boundary, important context is distilled into artifacts instead of remaining only in the active session.

Every task becomes documentation, every decision remains reviewable, and every document becomes context for what comes next.

## Core Principles

> **Humans never stop thinking. The session may end, but the project must remember.**

No matter how capable AI becomes, humans decide direction and judge quality. The moment people accept AI output without understanding or reviewing it, Hyper-Waterfall collapses into vibe coding. Operationally, the philosophy becomes three rules.

### 1. Humans Keep Direction Until the End

Stage transitions, plan changes, and meaningful source edits require explicit approval from the task requester. AI supports and executes decisions; it does not own them. Direction, priority, architecture, and quality remain human responsibilities.

### 2. Always Give AI Enough Context

Intent, scope, plans, decisions, and verification criteria are embedded in project artifacts so they do not need to be re-explained from scratch in every prompt. Agents read the same documented context and work from the same baseline. When context is scattered or missing, AI fills the gaps by guessing.

### 3. Periodically Distill Work Memory into Project Memory

Stage reports, final reports, commits, and PR bodies distill and record intent, decisions, implementation state, and verification evidence. The conversation may disappear, but structured project artifacts remain. New sessions, agents, and contributors can recover the essential context and continue from a documented baseline.

## Role Split

### Task Requester (Human)

The human focuses on **thinking and judgment**:

- Direction: “What should we do next?”
- Priority: “What matters more?”
- Quality judgment: “Is this good enough?”
- Architecture decision: “Is this structure correct?”
- Domain knowledge: “How should this behave in this domain?”
- Feedback: “This part is wrong, because…”

### AI Coding Agent

AI focuses on **execution and structured context capture**:

- Analysis: codebase exploration and root-cause tracing
- Planning: task and implementation plan drafting
- Implementation: code writing and test generation
- Verification: running checks and collecting evidence
- Documentation: Stage reports, final reports, technical docs, and commit messages
- Debugging: log analysis and fix proposals
- Iteration: applying feedback and retrying

## Vibe Coding vs Hyper-Waterfall

> Vibe coding—accepting AI output without reading it, letting AI make architecture decisions, and shipping code you do not understand—is a trap. It may appear to work, but because the result is not understood or documented, diagnosing and continuing the work becomes fragile.
>
> Hyper-Waterfall takes the opposite approach. The human task requester keeps ownership of direction, quality, and architecture decisions, while AI performs execution at a speed and scale humans cannot reach alone. The project also preserves the context needed to review and resume that execution.
>
> — [edwardkim/rhwp · Vibe Coding vs AI-Driven Development](https://github.com/edwardkim/rhwp#%EB%B0%94%EC%9D%B4%EB%B8%8C-%EC%BD%94%EB%94%A9-vs-ai-%EC%A3%BC%EB%8F%84-%EA%B0%9C%EB%B0%9C)

| | Vibe Coding | Hyper-Waterfall |
|---|---|---|
| **Human role** | Accept AI output | Direct, review, and decide |
| **Plan** | None—“just build it” | Task plan -> approval -> implementation plan -> Stage execution |
| **Quality gates** | Hope it works | Verification at every Stage + human decision gates + Open PR review |
| **Project memory** | Context remains in chat or one person's head | Intent, decisions, progress, and evidence are distilled into project artifacts |
| **Debugging** | Ask AI to fix AI's bug without durable diagnosis | Preserve diagnosis and rationale; AI implements the approved fix |
| **Architecture** | Accidentally formed | Intentionally decided by the task requester |
| **Docs** | Missing or written after the fact | `mydocs/` artifacts + Issue/PR body produced throughout the task |
| **Handoff** | Manual re-briefing | New sessions and contributors recover essential context from artifacts |
| **Result** | Fragile and hard to maintain | Traceable, reviewable, handoff-ready, and resumable |

## Why It Is Powerful — The Point AI Makes Reachable

Macro waterfall and micro agile were long treated as a trade-off. Discipline made work slow; speed often removed discipline. AI coding agents reduce the cost of planning, documentation, implementation, and verification enough to make both practical in the same workflow.

### 1. Recover Discipline Without Losing Speed

One major reason waterfall became heavy was that **humans had to carry all plans, documents, implementation, and verification themselves**. AI can draft and execute these quickly, allowing teams to recover discipline without giving up rapid iteration.

### 2. Turn Work History into Persistent Project Memory

Decisions, rationale, progress, verification results, feedback, and troubleshooting remain in `mydocs/`, commits, PRs, and Issues. Even when context concentrated in one person or session disappears, the next person or AI session can start from **the same documented baseline**.

This does more than reduce bus-factor risk. It makes accumulated work history reusable as context for future tasks.

### 3. Let Humans Focus on Decisions and AI on Execution

Humans remain responsible for direction, priority, architecture, and quality. AI handles exploration, implementation, tests, documents, evidence collection, and repeated iteration. AI becomes a multiplier when it operates on top of a deliberate process.

### 4. Let Work Move Across Sessions, Agents, Contributors, and Places

The maintainer of [rhwp](https://github.com/edwardkim/rhwp) works from the office, home, and while moving, using different Claude sessions in each place. Each new session has no native memory of the previous one.

Project artifacts answer the continuity questions:

| Question | Answer |
|---|---|
| “What should I do now?” | `orders/20260409.md` |
| “Where did we stop?” | `working/task_m100_86_stage1.md` |
| “What did we decide to do?” | `plans/task_m100_86_impl.md` |
| “Why this approach?” | `feedback/` + `tech/` |
| “What is the trap here?” | `troubleshootings/` |

The task requester spends far less time transferring context manually because the work itself continuously produces the handoff material.

---

## postmelee/hyper-waterfall: Turning the Methodology into a Reusable Harness

> This repository references the Hyper-Waterfall methodology first introduced in [rhwp](https://github.com/edwardkim/rhwp) and extends it into a reusable, multi-agent workflow harness.

### 1. Apply It to Any Repository with One Prompt — Modularization + Placeholder Substitution

The original methodology in rhwp is tightly coupled to that repository's documents and conventions, so it is difficult to copy directly into other projects. This repository separates operating rules, manuals, SKILLs, and templates into reusable sources and formalizes the entry procedure in [`docs/agent-entrypoint.en.md`](docs/agent-entrypoint.en.md).

As a result, **one prompt to an AI coding tool** can apply the method to another repository. The AI follows the entry procedure and substitutes placeholders such as `REPO_SLUG` and `BASE_BRANCH`.

Lifecycle criteria for updating existing adopted repositories are also documented separately. GitHub Release/tag, manifest, migration guide, and `.hyper-waterfall/version.json` are used to determine the current version, current locale, requested locale or switch request, target release/tag, target-release locale support, manifest diff, locale manifest diff, and Hyper-Waterfall version-update PR candidates first.

Detailed criteria live in [`docs/lifecycle/update.en.md`](docs/lifecycle/update.en.md) and [`docs/lifecycle/update_pr.en.md`](docs/lifecycle/update_pr.en.md). This repository itself is the first dogfooding case applying Hyper-Waterfall to itself through Issue #1 and PR #2.

### 2. Align Structured Project Artifacts with Official Prompting Guidance

The work-document formats are designed to satisfy the core of official prompting guidance from [OpenAI](https://developers.openai.com/api/docs/guides/prompt-guidance) and [Anthropic](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices).

GitHub Issue/PR templates structure platform artifacts, while `templates/mydocs/_templates/` specifies output formats for plans, reports, feedback, technical research, troubleshooting, and external PR reviews.

> This reduces quality degradation in the recursive process where AI writes documents and later agents read those documents as context.

- **Clarity**: task goals and boundaries are defined.
- **Consistency**: repeated work artifacts share central formats.
- **Stepwise progress**: work is split into smaller, reviewable Stages.
- **Context**: essential information is captured where future agents can read it.
- **Output format**: task results are emitted as predictable project artifacts.
- **Stop conditions**: agents return control to humans at explicit decision boundaries.

See the detailed mapping in [Prompt Guide Alignment](#prompt-guide-alignment).

### 3. Support Multiple Agents with Token- and Context-Efficient Rules

rhwp inlined operating rules, document structure, folder policy, naming rules, and PR handling into a single `CLAUDE.md` file and did not include `AGENTS.md`, so it operated as Claude Code-specific. This repository separates and expands the method along two axes.

**(1) Multi-agent compatibility**: `AGENTS.md` is the single source of truth, while `CLAUDE.md` references it with one `@AGENTS.md` line. SKILLs are recognized by both tools through `.agents/skills` for Codex and `.claude/skills` for Claude Code, with both symlinks pointing to the same text. New SKILL-aware tools can extend the same pattern.

**(2) Separation of operating rules, SKILLs, manuals, and templates**: `AGENTS.md` keeps only the policies, constraints, and index that must be loaded into every-turn system prompts. Procedural details are split into topic manuals under [`mydocs/manual/`](templates/locales/en/mydocs/manual/), each `mydocs/` folder's `README.md`, GitHub Issue/PR templates under [`.github/`](templates/locales/en/.github/), document output formats under [`mydocs/_templates/`](templates/locales/en/mydocs/_templates/), and seven SKILLs under [`mydocs/skills/`](templates/locales/en/mydocs/skills/).

Effects:

- **Token efficiency**: reduces content loaded into every-turn system prompts. Manuals and SKILL text enter context only when needed.
- **Context efficiency**: the model reads only the procedure needed at the current step. Unrelated procedures do not pollute judgment.
- **Clearer intent transfer**: platform templates and central document templates fix repeated artifact structures, while staged SKILLs define when they are produced.
- **Model portability**: SKILLs use a standard format and can be moved to other SKILL-aware tools.
- **Shared context**: different agents read the same plans, reports, decisions, and verification evidence instead of depending on tool-specific chat history.

## Live Example — Follow It Yourself

This repository is the first case of Hyper-Waterfall applying itself to itself. To see the workflow before adopting it, review these artifacts in order.

1. **Issue** [`#1` Hyper-Waterfall self-adoption (dogfooding)](https://github.com/postmelee/hyper-waterfall/issues/1) — a clean structure with three labels, milestone M010, and automatically linked PR without status-noise comments
2. **Pull Request** [`#2`](https://github.com/postmelee/hyper-waterfall/pull/2) — Open PR body with target task, reason, changes, review points, Stage timeline, artifact links, impact table, and verification evidence
3. **Task plan** [`mydocs/plans/task_m010_1.md`](mydocs/plans/task_m010_1.md) — purpose, background, scope, design direction, expected changed files, tentative Stages, verification plan, and risks
4. **Five-Stage implementation plan** [`mydocs/plans/task_m010_1_impl.md`](mydocs/plans/task_m010_1_impl.md) — Stage artifacts, verification commands, and commit messages fixed in advance
5. **Five Stage reports** [`mydocs/working/`](mydocs/working/) — artifacts, verification results, residual risks, and next-Stage impact at each boundary
6. **Final report** [`mydocs/report/task_m010_1_report.md`](mydocs/report/task_m010_1_report.md) — five-Stage synthesis, before/after quantitative comparison, and acceptance-criteria verification
7. **Today's todo** [`mydocs/orders/`](mydocs/orders/) — daily board format with milestone tables and completion time
8. **Commit log** [`git log` on `main`](https://github.com/postmelee/hyper-waterfall/commits/main) — twelve task commits preserved chronologically from `Task #1: 수행 계획서 작성` through `pr-merge-cleanup`

This first task expanded scope twice and proceeded through five Stages. The README procedure is visible as live artifacts: approval gates, context distillation at Stage boundaries, scope-change handling, PR body revision, and cleanup after merge.

## Design Principles

- Essential task context must survive the session that produced it.
- Structured project artifacts, not raw chat history, are the source of truth for resumable work.
- Meaningful source changes require a human decision gate.
- The task requester retains ownership of direction, priority, architecture, and quality.
- The latest state must be discoverable from Issue metadata, the current branch or PR, and `mydocs/`.
- Issue progress tracking is delegated to GitHub linked-PR auto-cross-references plus labels and milestones; comments are reserved for discussion, blockers, and decision records.
- This framework must work across many project types. Project-specific language, build, deployment, and product rules belong in the target repository's templates and settings, not in core.
- Be strict about process and flexible about tools.

> Hyper-Waterfall is not new magic. It uses AI as a multiplier on top of a process that preserves human judgment, durable work history, verification evidence, and handoff context.

## Prompt Guide Alignment

Hyper-Waterfall implements the core of the official OpenAI and Anthropic prompting guides at the development-process level. It is not only about writing one good prompt; it is about building a **project structure where good context, clear outputs, verification, and stop conditions are repeatedly produced by the workflow**.

### Alignment Summary

| Principle | How Hyper-Waterfall Implements It | Effect |
|---|---|---|
| Clear goal | GitHub Issue, task plan, implementation plan | AI understands scope and success criteria first. |
| Sufficient context | Plans, reports, feedback, and technical research in `mydocs/` | New sessions recover essential context from project artifacts. |
| Output-format constraints | `mydocs/_templates/`, Issue/PR templates | Plans, reports, and verification results keep consistent structures. |
| Stepwise progress | Stage-level implementation, verification, and reporting | Complex work is divided into reviewable units. |
| Verification criteria | Stage reports, final report, PR body | Results are judged by recorded criteria and evidence. |
| Stop conditions | Human decision gates | AI does not advance arbitrarily. |
| Persistent project memory | `mydocs/`, commit history, Issue/PR timeline | Essential work context remains after chat disappears. |
| Lightweight context | `1 Issue = 1 Task = 1 Branch = 1 Session` | Sessions stay small and focused. |
| Multi-agent continuity | Shared rules, SKILLs, manuals, and artifacts | Different agents can continue from the same baseline. |

<details>
<summary><strong>OpenAI prompt guidance mapping</strong> · source: <a href="https://developers.openai.com/api/docs/guides/prompt-guidance">OpenAI prompt guidance</a></summary>

1. **Define the output first.**
   Hyper-Waterfall defines artifacts from the start: Issue, task plan, implementation plan, Stage report, final report, and PR. Instead of asking AI to “do a good job,” it defines what must be left behind.

2. **Describe what a good answer means.**
   Each Stage records implementation, verification criteria, evidence, and review points. AI output is judged against documented criteria rather than intuition.

3. **Set short constraints.**
   Hyper-Waterfall makes boundaries explicit: do not proceed to the next Stage without approval, ask before source edits, and track work by Issue. These rails prevent runaway execution without eliminating useful autonomy inside the approved scope.

4. **State the level of evidence needed.**
   Implementation results are distilled into Stage reports, verification logs, commits, and PR bodies. The project keeps not only what changed, but why it changed and how it was checked.

5. **Specify the output format.**
   `mydocs/_templates/` fixes the expected shape for task plans, implementation plans, Stage reports, final reports, feedback, technical research, troubleshooting, and external PR review documents. `.github/pull_request_template.md` structures PR bodies for the review screen. AI responses become artifacts that the next worker can read again.

6. **Tell the model when to stop.**
   Hyper-Waterfall stops at every Stage boundary and waits for human approval. AI returns control at points where humans can verify direction and quality.

</details>

<details>
<summary><strong>Anthropic Claude prompting best practices mapping</strong> · source: <a href="https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices">Claude prompting best practices</a></summary>

1. **Clear and direct instructions.**
   Task intent is explicit through the Issue, task plan, and implementation plan. The method defines what to build, why, how far to proceed, and where to stop.

2. **Workflow and goal context.**
   Users do not need to repeat in every prompt how the work fits into the larger process. That context is embedded in `mydocs/`, Issues, and PR bodies so agents read the same shared context.

3. **Sequential steps.**
   Stage-based progress and human decision gates split long-running work into sequential, reviewable units.

4. **Output-format control.**
   Task plans, Stage reports, final reports, feedback, technical research, and external PR review documents follow formats in `mydocs/_templates/`, while PR bodies follow `.github/pull_request_template.md`.

5. **Long-running work and external memory.**
   `mydocs/` supports long-horizon agentic work by distilling temporary session context into persistent filesystem artifacts.

6. **Literal instruction following and alignment.**
   Explicit boundaries such as “ask before source edits,” “do not proceed to the next Stage without approval,” and “track by Issue” make literal instruction following work in favor of the process.

> Hyper-Waterfall prioritizes human control, durable work history, and traceability over maximum autonomy. It operates above one-turn interactive coding by adding project-level task boundaries and artifact requirements. Folder structure, filename rules, and central templates provide the structural role that inline prompt formatting alone cannot provide across a full task lifecycle.
>
> **One-line summary**: Hyper-Waterfall implements prompting best practices as a repeatable, human-governed AI coding workflow—not as a single prompt sentence.

</details>

## License

MIT. See [LICENSE](LICENSE) for details.
