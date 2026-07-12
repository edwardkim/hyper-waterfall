# Hyper-Waterfall

[English](README.md) | 한국어 | [简体中文](README.zh-CN.md)

![Hyper-Waterfall overview](docs/assets/hyper-waterfall.png)

## 일시적인 세션에서 지속되는 프로젝트 기억으로

Hyper-Waterfall은 일시적인 세션 맥락을 지속되는 프로젝트 기억으로 증류해 작업을 추적·검토·재개할 수 있게 하는 **사람이 결정권을 갖는 AI 코딩 워크플로**입니다.

임시 채팅 안에 작업 맥락을 가두는 대신, 각 task에서 중요한 의도·범위·계획·결정·구현 진행 상황·검증 근거를 Issue, 계획서, Stage 보고서, commit, PR 같은 구조화된 프로젝트 산출물로 주기적으로 남깁니다.

이 산출물은 단순한 로그가 아닙니다. 함께 축적되어 새 세션·에이전트·기여자가 채팅 기록을 다시 살펴보지 않고도 핵심 맥락을 복원하고 문서화된 기준선에서 작업을 이어가도록 돕는 공유 프로젝트 기억이 됩니다.

> **세션은 끝나도, 프로젝트는 기억합니다.**
>
> 모든 작업은 문서가 되고, 모든 문서는 다음 작업의 맥락이 됩니다.

| Hyper-Waterfall의 핵심 | 의미 |
|---|---|
| 작업 맥락 증류 | 일시적인 세션에서 핵심 작업 맥락을 추출해 구조화된 프로젝트 산출물로 기록합니다. |
| 지속되는 프로젝트 기억 | 의도, 결정, 진행 상황, 검증 근거가 세션 종료 후에도 남습니다. |
| 사람의 결정권 | 방향·범위·아키텍처·품질의 결정권은 사람이 갖고, AI는 명시된 경계 안에서 실행합니다. |
| 단계적 실행 | 큰 작업을 검토 가능한 Stage로 나누고 각 단계의 검증과 완료보고서를 남깁니다. |
| 재개 가능한 작업 | 새 세션·에이전트·기여자가 프로젝트 산출물에서 핵심 맥락을 복원해 작업을 이어갈 수 있습니다. |

Hyper-Waterfall은 세션을 의도적으로 작게 유지하도록 **`1 Issue = 1 Task = 1 Branch = 1 Session`**을 권장합니다. 필요한 핵심 맥락은 이미 프로젝트에 증류되어 있으므로 세션을 깔끔하게 종료할 수 있습니다.

> [!IMPORTANT]
> **AI에게 실행은 맡기되, 결정권은 넘기지 않습니다.**
>
> Hyper-Waterfall은 AI가 마법처럼 무엇이든 하게 만드는 도구가 아닙니다. 사람이 방향이나 프로젝트 맥락을 잃지 않으면서 AI가 빠르게 움직일 수 있도록 명확한 레일을 제공합니다.

## 바로 설치

### 기존 저장소

AI 코딩 도구에 다음 한 줄을 보내세요.

```text
https://github.com/postmelee/hyper-waterfall 의 하이퍼-워터폴 방법론을 이 저장소에 적용해줘.
```

### 새 프로젝트

프로젝트 아이디어를 저장소로 시작할 시점이 되면 먼저 빈 GitHub 저장소나 로컬 저장소를 만드세요. 그 빈 저장소에서 다음 프롬프트를 보내면 됩니다.

```text
이 빈 저장소에서 새 프로젝트를 시작하려고 합니다.

먼저 https://github.com/postmelee/hyper-waterfall 의 하이퍼-워터폴 방법론을 이 저장소에 적용해줘.

프로젝트 기획서나 요구사항 초안이 첨부되어 있다면 참고 맥락으로만 사용해줘. 적용 단계에서는 제품 계획서, 아키텍처 문서, 소스 코드를 만들지 말고, 적용 후 첫 제품 작업을 별도 GitHub Issue로 등록할 수 있게 도와줘.
```

두 경로 모두 AI는 [`docs/agent-entrypoint.md`](docs/agent-entrypoint.md)부터 읽어 적용 절차를 따릅니다. 소스 변경 전에 제안 범위를 보고하고 작업지시자 승인을 받아야 합니다.

| AI가 먼저 보고할 것 | 내용 |
|---|---|
| 적용 모드 | 신규 적용인지, 기존 Hyper-Waterfall 업데이트인지 |
| 변경 후보 | 어떤 파일을 만들거나 바꿀지, placeholder 치환이 필요한지 |
| 승인 요청 | 실제 파일 변경 전에 작업지시자가 승인해야 할 범위 |

### 언어 지원

기본 locale은 `en`입니다. 지원 locale pack은 `en`, `ko`, `zh-CN`이며, 선택한 locale source가 없으면 fallback 후보를 사용하기 전에 먼저 보고합니다.

| 언어 | Locale |
|---|---|
| English | `en` |
| 한국어 | `ko` |
| 중국어 간체 | `zh-CN` |

AI 코딩 도구를 사용할 때는 원하는 언어로 지시하세요. AI는 파일 변경 전 선택 locale을 먼저 보고합니다.

터미널에서 적용 판단을 확인하려면 locale을 명시해 실행하세요. 필요하면 `ko`를 `en` 또는 `zh-CN`으로 바꾸면 됩니다.

```sh
npx hyper-waterfall@0.3.0 init --repo . --locale ko --dry-run
```

macOS에서 자주 실행한다면 Homebrew로 CLI를 설치할 수 있습니다.

```sh
brew install postmelee/tap/hyper-waterfall
hyper-waterfall init --repo . --locale ko --dry-run
```

`npx`와 Homebrew CLI 명령은 lifecycle 판단 결과만 출력합니다. 실제 파일 변경은 계속 승인 workflow를 거쳐 진행합니다.

도입 후에는 AI가 Hyper-Waterfall 방식을 지키며 작업을 진행합니다. 처음 시작하는 사용자는 AI에게 `"이거 구현해줘"`와 같은 자연어 명령을 내리면 됩니다.

> 누구나 GitHub 저장소에 Hyper-Waterfall을 적용하고, Codex·Claude Code 등 여러 AI 코딩 에이전트가 같은 규율과 공유 맥락 위에서 작업하게 만듭니다.

## Hyper-Waterfall 자세히 알아보기

[왜 Hyper-Waterfall인가](#왜-hyper-waterfall인가) ·
[언제 쓰면 좋은가](#언제-쓰면-좋은가) ·
[기존 AI 코딩 방식과 비교](#기존-ai-코딩-방식과-비교) ·
[적용하면 바로 달라지는 것](#적용하면-바로-달라지는-것) ·
[Hyper-Waterfall의 강점](#hyper-waterfall의-강점) ·
[도입 후 작업 흐름](#도입-후-작업-흐름) ·
[적용 후 대상 저장소 구조](#적용-후-대상-저장소-구조)

## 왜 Hyper-Waterfall인가

AI 코딩 에이전트에는 두 가지 구조적 약점이 있습니다.

- 세션 맥락은 일시적이며 대화가 길어지거나 도구가 바뀌면 신뢰도가 낮아집니다.
- 방향이 틀렸는데도 AI는 자신 있게 실행을 계속할 수 있습니다.

Hyper-Waterfall은 이 두 약점을 작업 제약으로 바꿉니다. 작업 기억을 프로젝트 산출물로 증류하고, AI의 실행을 사람의 결정 게이트 안에 둡니다.

| 문제 | Hyper-Waterfall의 제약 | 결과 |
|---|---|---|
| 세션 종료와 함께 맥락이 사라짐 | 의도·결정·진행 상황·검증을 구조화된 산출물로 기록 | 지속되는 프로젝트 기억 |
| 긴 세션이 흐려짐 | 권장 모델: `1 Issue = 1 Task = 1 Branch = 1 Session` | 작고 집중된 컨텍스트 |
| AI가 잘못된 방향으로 빠르게 실행할 수 있음 | 계획서와 Stage 경계에서 사람 검토 필요 | 방향 오류를 더 일찍 발견 |
| 에이전트마다 절차를 새로 해석함 | 공통 규칙·SKILL·매뉴얼·템플릿 | 에이전트 간 일관된 실행 |
| 리뷰어가 채팅에서 작업 이력을 복원해야 함 | 보고서·commit·PR에 근거와 검증 기록 | 추적·검토 가능한 작업 |

그 결과는 단순한 승인 기반 코딩 도구가 아닙니다. 중요한 결정권은 사람이 유지하면서 일시적인 AI 실행을 오래 재사용할 수 있는 프로젝트 지식으로 전환하는 워크플로입니다.

## 언제 쓰면 좋은가

Hyper-Waterfall은 작업이 한 번의 AI 세션을 넘어도 이해하고 재개할 수 있어야 하는 실제 소스 변경을 위해 설계되었습니다.

| 잘 맞는 경우 | 어울리지 않는 경우 |
|---|---|
| 여러 날·세션·에이전트·기여자에 걸쳐 작업을 이어가야 할 때 | 한두 줄 수정처럼 계획서와 보고서 비용이 변경 자체보다 큰 작업 |
| 작업 의도·결정·진행 상황·검증을 재사용 가능한 프로젝트 맥락으로 남기고 싶을 때 | 버리는 프로토타입처럼 추적 가능성보다 즉시 실험이 중요한 작업 |
| AI 코딩 도구에 실제 소스 수정을 맡기되 범위와 품질 결정은 사람이 가져야 할 때 | 사람이 결과를 검토하지 않고 AI 출력만 그대로 수락하려는 작업 |
| PR 리뷰에서 무엇을 왜 바꿨고 어떻게 검증했는지가 바로 보여야 할 때 | 인수인계나 재개 가능성이 중요하지 않은 개인 실험 |
| 큰 작업을 Issue, branch, Stage 단위로 나눠 방향 오류를 일찍 잡고 싶을 때 | 현재 구현이 전제하는 GitHub Issue·branch·PR 흐름을 사용하지 않는 저장소 |
| 새 기여자나 AI 세션이 프로젝트 산출물만으로 다시 시작해야 할 때 | 결정과 작업 이력을 보존할 가치가 없는 작업 |

> AI가 상당한 구현을 맡는 동안 사람이 결정권·엔지니어링 맥락·검토 가능성을 보존해야 하는 작업에 가장 잘 맞습니다. 반대로 연속성보다 즉시 실험이 중요한 작업에는 과할 수 있습니다.

## 기존 AI 코딩 방식과 비교
핵심 차이는 AI가 명령 실행 전에 권한을 요청하는지 여부가 아닙니다. 세션이 끝난 뒤에도 프로젝트가 작업의 맥락을 보존·검토·재사용할 수 있는지에 있습니다.

일반적인 AI 코딩은 한 대화의 흐름에 의존하는 경우가 많습니다. Hyper-Waterfall은 작업 단위, 결정 게이트, 산출물 형식, 맥락 인수인계 규칙을 프로젝트 수준에서 고정합니다.

| 기존 AI 코딩 방식 | Hyper-Waterfall 적용 후 |
|---|---|
| “이거 만들어줘”라고 시키고 AI가 바로 파일을 고침 | 먼저 Issue와 수행계획서로 작업 목적·범위·검증 기준을 정의 |
| 작업 범위가 대화 중 계속 흔들림 | 구현계획서에서 Stage 단위로 나누고 승인된 범위 안에서만 진행 |
| 작업 맥락이 일시적인 채팅 세션 안에 갇힘 | 핵심 맥락을 `mydocs/`, Issue, PR, commit history로 증류 |
| AI가 어느 파일을 왜 고쳤는지 나중에 추적하기 어려움 | Stage 보고서와 commit으로 변경 근거·산출물·검증 결과 기록 |
| 큰 구현이 끝난 뒤에야 방향 오류를 발견 | 수행계획서·구현계획서·Stage 경계에서 작업지시자가 승인 또는 수정 지시 |
| 새 세션이나 에이전트에 매번 수동으로 설명해야 함 | 프로젝트 산출물이 핵심 맥락과 다음 행동을 제공 |
| PR 리뷰 때 채팅 로그를 다시 뒤져야 함 | PR과 보고서로 무엇을 왜 바꿨고 어떻게 검증했는지 확인 |

사람 작업지시자는 방향·우선순위·아키텍처·품질의 결정권을 유지합니다. AI는 탐색·초안 작성·구현·검증·문서화를 빠르게 수행합니다.

> [!IMPORTANT]
> **핵심 차이: 사람은 생각을 멈추지 않고, 프로젝트는 한 세션의 기억에 의존하지 않습니다.**

## 적용하면 바로 달라지는 것

1. **세션 맥락이 지속되는 프로젝트 기억이 됩니다.**
   의도·범위·결정·진행 상황·검증 근거가 `mydocs/`, Issue, PR, commit history에 남습니다. 새 세션·에이전트·기여자는 채팅 기록을 다시 살펴보지 않고도 작업을 이어갈 수 있습니다.

2. **“어디까지 했지?”에 문서화된 답이 생깁니다.**
   Issue, 오늘할일, 수행계획서, 구현계획서, Stage 보고서, 최종 보고서, commit, PR이 복원 가능한 작업 타임라인을 만듭니다.

3. **세션이 작고 집중된 상태로 유지됩니다.**
   권장 운용은 `1 Issue = 1 Task = 1 Branch = 1 Session`입니다. task가 끝나면 세션을 닫고, 다음 작업은 문서화된 맥락을 필요할 때 읽는 깨끗한 새 세션에서 시작합니다.

4. **AI가 마음대로 코드를 고치지 않습니다.**
   소스 수정 전 계획서와 사람의 결정 게이트를 거치므로 작업지시자가 방향과 범위를 통제합니다.

5. **사람이 결정권을 잃지 않습니다.**
   소스 수정·Stage 전환·최종 보고·PR 생성 앞에 게이트가 있습니다. AI는 실행하지만 방향·아키텍처·품질은 사람이 판단합니다.

6. **여러 AI 세션을 병렬로 돌릴 수 있습니다.**
   독립적인 Issue는 각각 `local/task{N}` 브랜치나 분리 worktree에서 진행할 수 있습니다. 컨텍스트와 변경 범위가 섞이지 않습니다.

7. **PR 리뷰가 쉬워집니다.**
   PR에는 무엇을 왜 바꿨는지, 어떤 Stage를 거쳤는지, 어떤 검증을 했는지가 정리됩니다. 리뷰어는 채팅 로그를 재구성하는 대신 프로젝트 산출물을 검토합니다.

8. **방향 오류를 더 일찍 발견합니다.**
   잘못된 방향으로 많은 작업이 쌓이기 전에 수행계획서·구현계획서·Stage 완료보고서가 사람이 검토하는 품질 게이트로 작동합니다.

9. **AI의 속도를 잃지 않고 엔지니어링 규율을 유지합니다.**
   AI가 계획·테스트·보고서·구현 초안을 빠르게 만들고, 워크플로는 근거·판단 이유·인수인계 맥락을 보존합니다.

10. **AI 코딩이 일회성 대화가 아니라 재사용 가능한 프로젝트 프로세스가 됩니다.**
    모든 작업은 Issue, branch, 문서, commit, PR로 연결되어 추적·검토·재개하고 다음 작업의 맥락으로 사용할 수 있습니다.

## Hyper-Waterfall의 강점

### 1. 세션 맥락을 지속되는 프로젝트 기억으로 증류한다 — 지식 자산화

- 작업 의도·제약·계획·결정·Stage별 진행·검증 결과·트러블슈팅 지식이 구조화된 프로젝트 산출물로 쌓입니다.
- 이 산출물은 단순한 기록이 아니라 **다음 작업의 입력**입니다. 미래 세션과 기여자는 처음부터 다시 구성하지 않고 이전 작업 위에서 시작할 수 있습니다.
- 원본 대화 전체를 프로젝트의 진실 원천으로 삼지 않고도 세션에서 중요한 부분을 보존합니다.

> `mydocs/`는 작업 이력에 특화된 vault처럼 동작합니다. 일반 지식 저장소와 달리 작업 의도·계획·결정·검증·산출물·피드백·트러블슈팅을 프로세스가 정한 형식으로 축적합니다.

### 2. 큰 실패가 되기 전에 게이트에서 방향 오류를 발견한다 — 리스크 제어

- 작업은 `Issue -> branch -> 수행계획서 -> 구현계획서 -> Stage 구현·검증·보고 -> 최종 보고서 -> Open PR` 순서를 따릅니다.
- 수행계획서·구현계획서·각 Stage 경계·최종 보고에서 사람이 검토합니다.
- Stage 검증이 실패하면 그 단계 안에서 회복하고, 범위가 바뀌면 계획서를 갱신해 재승인을 받습니다.
- 코드 리뷰만으로 일찍 발견하기 어려운 잘못된 목표·범위·아키텍처 방향 같은 의미 오류를 앞단에서 잡습니다.

### 3. “AI에게 잘 부탁한다”가 아니라 좋은 작업이 구조적으로 나오게 한다 — 자동화된 역할 분담

- 작업지시자는 **방향·우선순위·아키텍처·품질 결정**의 책임을 유지합니다.
- AI는 탐색·초안 작성·구현·테스트·보고서·PR 본문 준비 같은 반복 실행을 맡습니다.
- SKILL은 단계별 행동, 남겨야 할 산출물, 사람에게 제어권을 돌려줄 시점을 정의합니다.
- 중앙 템플릿은 에이전트가 매 task마다 계획서·보고서·검증 형식을 새로 만들지 않도록 출력 구조를 고정합니다.

### 4. 세션은 작게, 기억은 프로젝트에 — 컨텍스트 경량화

- Hyper-Waterfall은 모든 프로젝트 이력을 하나의 AI 세션에 계속 누적하지 않습니다. 권장 모델에서 한 세션은 한 Issue를 맡고 task가 끝나면 닫힙니다.
- 각 세션은 현재 Issue, 관련 계획서, Stage 보고서, 프로젝트 문서와 코드만 읽습니다.
- 이전 결정은 모든 프롬프트를 오염시키거나 길어진 대화에 의존하지 않고 프로젝트 산출물에서 필요할 때 확인합니다.
- 변경 범위가 충돌하지 않는 독립 Issue는 별도 branch나 worktree에서 병렬로 진행할 수 있습니다.

> AI 세션은 길어진다고 반드시 더 똑똑해지지 않으며 오히려 집중력이 떨어질 수 있습니다. Hyper-Waterfall은 세션을 짧게 유지하고 기억은 프로젝트에 남깁니다.

### 5. 결과

이 강점은 하나의 루프를 이룹니다.

```text
일시적인 세션 맥락
        ↓ 증류
구조화된 프로젝트 산출물
        ↓ 축적
지속되는 프로젝트 기억
        ↓ 복원
다음 세션, 에이전트, 기여자 또는 task
```

동시에 사람의 결정 게이트가 AI의 실행을 프로젝트 방향에 맞게 유지합니다.

그 결과 AI 코딩은 세션·에이전트·기여자를 넘어 추적·검토·재개할 수 있는, 지속되는 프로젝트 기억을 갖춘 사람 주도 워크플로가 됩니다.

> [!NOTE]
> 이 구조는 [OpenAI prompt guidance](https://developers.openai.com/api/docs/guides/prompt-guidance)와 [Anthropic prompting best practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices)가 강조하는 명확한 지시, 충분한 맥락, 출력 형식 제약, 검증 기준, 멈춤 조건, 장기 작업 기억, agentic workflow 제어 원칙과 정합됩니다. 상세 매핑은 [프롬프트 가이드 준수](#프롬프트-가이드-준수)에서 확인할 수 있습니다.

## 도입 후 작업 흐름

Hyper-Waterfall은 **타스크** 단위로 작업합니다. 각 task는 코드를 생산하는 동시에 그 작업을 이해·검증·재개하는 데 필요한 맥락을 증류합니다.
### 타스크 진행 절차

모든 타스크는 아래 절차를 **엄격하게** 따릅니다.

```
1. GitHub Issue 확인 또는 등록
2. 오늘할일(mydocs/orders/) 기록
3. 타스크 브랜치 생성 (local/task{번호})
4. 수행계획서 작성 → [작업지시자 승인]
5. 구현계획서 작성 → [작업지시자 승인]
6. 단계별 구현
7. 단계별 완료보고서 → [작업지시자 승인]
8. (다음 단계 반복)
9. 최종 결과보고서 → [작업지시자 승인]
10. 오늘할일 상태 갱신
```

> 각 `[승인]` 지점은 결정 게이트이자 작업 맥락 증류 경계입니다. 다음 단계로 넘어가기 전에 방향 오류를 검토하고 현재 상태를 기록합니다.

세부 절차는 [타스크 진행 절차 매뉴얼](templates/mydocs/manual/task_workflow_guide.md#타스크-진행-절차)을 기준으로 합니다. 브랜치와 PR 게시 흐름은 [Git 워크플로우 매뉴얼](templates/mydocs/manual/git_workflow_guide.md#브랜치-관리)에서 확인할 수 있습니다.

### 핵심 SKILL 상세

| SKILL | 사용하는 시점 | 주요 산출물 |
|---|---|---|
| `task-register` | 신규 작업이라 GitHub Issue를 먼저 만들어야 할 때 | `task.yml` Issue Form 구조를 따르는 GitHub Issue, milestone·label 후보와 선택 이유 |
| `task-start` | 승인된 이슈 작업을 시작할 때 | `local/task{N}` 브랜치, 오늘할일 행, `task_plan.md` 기반 수행계획서 |
| `task-stage-report` | 한 Stage 구현이 끝나고 다음 단계로 넘어가기 직전 | `stage_report.md` 기반 단계 보고서, 단계 묶음 커밋, 단계 검증 결과 |
| `task-final-report` | 모든 Stage가 끝나고 PR을 게시하기 직전 | `final_report.md` 기반 최종 보고서, 오늘할일 완료 처리, Open PR |
| `pr-merge-cleanup` | PR이 실제로 merge된 직후 | 이슈 close, `publish/task{N}` 원격 삭제, 로컬 브랜치/worktree 정리 |
| `external-pr-review` | 외부 기여자 PR을 검토할 때 | `external_pr_*` 템플릿 기반 `mydocs/pr/` 검토 문서, 검증 결과, 권고(merge/수정/닫기) |
| `todo` | 오늘할일 보드를 새로 만들거나 갱신할 때 | `orders.md` 기반 `mydocs/orders/yyyymmdd.md` 표 형식 갱신 |

각 SKILL을 언제 사용자에게 표시하는지는 [SKILL 호출 표시 안내](templates/mydocs/manual/task_workflow_guide.md#skill-호출-표시-안내)를 따릅니다. PR 본문 작성과 검증 구조는 [내부 task PR 작성 가이드](templates/mydocs/manual/internal_pr_guide.md)를 기준으로 하고, PR 생성 명령과 문서 링크 형식은 [PR 생성 명령과 링크 가이드](templates/mydocs/manual/pr_command_guide.md)를 따릅니다.

문서 구조와 manual 문서 중립성 기준은 별도 SKILL이 아니라 [문서 구조 매뉴얼](templates/mydocs/manual/document_structure_guide.md)을 기준으로 확인합니다.

### 타스크 사이클

이슈가 이미 있으면 `task-register`를 건너뛰고 바로 `task-start`로 수행계획서 작성에 들어갑니다. 예를 들어 작업지시자가 `"issue #17 작업을 진행해줘"`라고 지시하면 AI는 #17의 milestone과 본문을 확인한 뒤 `local/task17`, 오늘할일, 수행계획서를 만듭니다. 아직 이슈가 없을 때만 `task-register`가 중복 이슈·milestone·label을 확인하고 생성 전 승인을 받은 뒤 GitHub Issue를 만듭니다.

각 단계 전환에는 작업지시자의 명시 승인이 필요합니다.
```
0. 타스크 등록 → `task-register`
   └─ AI: 중복 이슈, milestone, label 후보 확인
   └─ 작업지시자: 이슈 생성 승인
   └─ AI: GitHub Issue 생성 후 `task-start` 진입 승인 요청

1. 수행 계획서 → `task-start`
   └─ 작업지시자: "issue #N 작업을 진행해줘"처럼 기존 이슈를 지정하거나, 방금 생성한 이슈로 시작 승인
   └─ AI: 계획서 작성 (최소 3단계, 최대 6단계)
   └─ 작업지시자: 검토 → 승인 또는 수정 요청

2. 단계별 구현 → `task-stage-report`(단계 수만큼 반복)
   └─ AI: 코드 작성 + 테스트
   └─ AI: 단계 완료 보고서 작성
   └─ 작업지시자: 검증 → 승인 또는 피드백

3. 피드백 반영 → (수동)
   └─ 작업지시자: 피드백 문서 작성 (mydocs/feedback/), AI가 반영. scope가 바뀌면 계획서를 갱신해 재승인
   └─ AI: 피드백 반영, 수정

4. 최종 보고 + Open PR → `task-final-report`
   └─ AI: 최종 결과 보고서 작성, 검증 결과·근거를 구조화한 Open PR 생성
   └─ 작업지시자: 검증 → 승인 또는 피드백

5. PR 리뷰 + merge + 정리 → `pr-merge-cleanup`
   └─ 작업지시자: PR 검토 → 승인 또는 피드백
   └─ AI: 리뷰·merge 후 이슈 close, 브랜치/오늘할일 정리
```
`todo`는 위 흐름 어느 단계에서든 오늘할일 보드를 갱신할 때 호출합니다. `external-pr-review`는 외부 기여자 PR 검토용 별도 흐름입니다.

### 문서 구조

타스크가 사용하거나 만들어내는 문서 구조:

```
mydocs/
├── _templates/                         ← 산출물별 출력 형식
├── orders/yyyymmdd.md                  ← 오늘 할일 (타스크 목록 + 상태)
├── plans/task_{milestone}_{N}.md       ← 수행 계획서
├── plans/task_{milestone}_{N}_impl.md  ← 구현 계획서
├── working/task_{milestone}_{N}_stage{S}.md
│                                        ← 단계별 완료 보고서
├── report/task_{milestone}_{N}_report.md
│                                        ← 최종 결과 보고서
├── feedback/                           ← 피드백·리뷰 의견
├── tech/                               ← 기술 조사·공식화 전 초안
├── manual/                             ← 운영 매뉴얼·반복 작업 기준
├── troubleshootings/                   ← 트러블슈팅
└── pr/                                 ← 외부 PR 검토 기록
```

이 문서들은 지속되는 작업 이력의 서로 다른 부분을 보존합니다.

| 영역 | 보존하는 맥락 |
|---|---|
| `orders/` | 현재 task 상태와 다음 행동 |
| `plans/` | 의도, 범위, 결정, 구현 순서, 검증 기준 |
| `working/` | Stage별 진행, 산출물, 근거, 잔여 위험, 다음 단계 맥락 |
| `report/` | 최종 종합, 수용 상태, 인수인계 맥락 |
| `feedback/` | 사람의 검토, 수정 지시, 판단 근거 |
| `tech/` | 아직 공식 문서로 승격되지 않은 조사, 대안, 설계 판단 |
| `troubleshootings/` | 알려진 실패 유형, 진단, 복구 지식 |
| `pr/` | 외부 기여 검토 근거와 권고 |

폴더별 역할은 [문서 구조 매뉴얼의 폴더 역할](templates/mydocs/manual/document_structure_guide.md#폴더-역할-엄격-준수)에서 확인하고, 각 폴더의 상세 작성 규칙은 해당 폴더의 `README.md`를 기준으로 확인합니다. 문서 파일명은 [문서 파일명 규칙](templates/mydocs/manual/document_structure_guide.md#문서-파일명-규칙)을 따릅니다. 산출물 출력 형식은 [중앙 템플릿 정책](templates/mydocs/manual/document_structure_guide.md#중앙-템플릿-정책)에 정리되어 있습니다.

`mydocs/`는 작업 기억, 운영 매뉴얼, 조사 근거를 보관하는 구조이며 대상 프로젝트의 공식 제품 문서 루트가 아닙니다. 공식 문서 루트 이름은 Hyper-Waterfall이 고정하지 않습니다. 대상 프로젝트가 `docs/`, `specs/`, `site/`, `website/`, `adr/`, GitHub Wiki 등을 선택할 수 있지만, 제품/사용자/기여자/API/아키텍처/로드맵 문서를 생성·이동·수정하는 task는 수행계획서의 문서 위치 판단에서 대상 독자, 공식화 수준, 선택 경로, 대안 경로, 선택 이유를 먼저 승인받습니다.

`manual/` 문서는 반복 적용되는 운영 기준과 절차를 담고, 특정 이슈·PR·릴리즈 검증·장애 기록은 해당 산출물 문서로 분리합니다. 세부 경계는 [manual 문서 중립성 정책](templates/mydocs/manual/document_structure_guide.md#manual-문서-중립성-정책)을 따릅니다.

`tech/` 문서는 기술 조사, 대안 비교, 설계 판단 근거, 아직 공식화되지 않은 초안을 담습니다. 사용자나 외부 통합자가 따라야 하는 공식 계약 문서로 승격하려면 별도 task에서 공식 문서 루트를 선택하고 승인받습니다.

`_templates/`는 실제 task 산출물이 아니라 출력 형식의 진실 원천입니다. 각 Skill은 산출물을 만들 때 먼저 `mydocs/_templates/`의 해당 템플릿을 참조하고, 템플릿을 읽을 수 없는 상황에서만 Skill 안의 최소 섹션 요약을 fallback으로 사용합니다.

GitHub Issue와 Pull Request는 GitHub 플랫폼 산출물입니다. 이슈 본문은 `.github/ISSUE_TEMPLATE/task.yml`, PR 본문은 `.github/pull_request_template.md`를 기준으로 구조화하고, 저장소 안에 남는 작업 문서는 `mydocs/_templates/`를 기준으로 작성합니다. 세부 경계는 [GitHub 플랫폼 템플릿 정책](templates/mydocs/manual/document_structure_guide.md#github-플랫폼-템플릿-정책)을 따릅니다.

## 적용 후 대상 저장소 구조

`templates/`를 복사하고 placeholder를 치환한 뒤 사용자 저장소에 만들어지는 모습입니다.

```text
your-repo/
├── AGENTS.md                       운영 규칙 단일 진실 원천
├── CLAUDE.md                       Claude Code용 (AGENTS.md 참조)
├── .hyper-waterfall/
│   └── version.json                 적용된 Hyper-Waterfall version과 locale 기록
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   └── task.yml
│   └── pull_request_template.md
├── .agents/
│   └── skills -> ../mydocs/skills  Codex 인식 경로 (심볼릭 링크)
├── .claude/
│   └── skills -> ../mydocs/skills  Claude Code 인식 경로 (심볼릭 링크)
└── mydocs/
    ├── _templates/         산출물별 출력 형식 템플릿
    ├── manual/             운영 매뉴얼 (문서 구조, 타스크 진행, Git, PR, lifecycle, release/update, 충돌 규칙)
    ├── skills/             SKILL 진실 원천 (Codex/Claude Code 공용)
    ├── orders/             오늘할일 (yyyymmdd.md)
    ├── plans/              수행/구현 계획서
    │   └── archives/
    ├── working/            단계별 완료 보고서
    ├── report/             최종 결과 보고서
    ├── feedback/           피드백·리뷰 의견
    ├── tech/               기술 조사·공식화 전 초안
    ├── troubleshootings/   트러블슈팅
    └── pr/                 외부 PR 검토 기록
        └── archives/
```

| 영역 | 제공하는 것 |
|---|---|
| `AGENTS.md`, `CLAUDE.md` | AI 코딩 에이전트에 공통 운영 규칙을 적재합니다. `AGENTS.md`가 진실 원천이고 `CLAUDE.md`가 이를 참조합니다. |
| `.hyper-waterfall/version.json` | 적용된 프레임워크 version과 locale을 기록해 업데이트 판단을 지원합니다. |
| `.github/` | GitHub Issue Form과 Pull Request 본문 구조를 고정합니다. |
| `.agents/skills`, `.claude/skills` | Codex와 Claude Code가 심볼릭 링크를 통해 같은 SKILL 본문을 읽게 합니다. |
| `mydocs/_templates/` | 계획서·보고서·피드백·기술 조사·트러블슈팅·외부 PR 검토의 출력 형식을 고정합니다. |
| `mydocs/manual/` | 반복 적용되는 운영 정책과 절차를 보관합니다. |
| `mydocs/orders/`, `plans/`, `working/`, `report/` | 현재 task 상태, 계획, Stage 진행, 검증 근거, 최종 인수인계 맥락을 보관합니다. |
| `mydocs/feedback/`, `tech/`, `troubleshootings/`, `pr/` | 사람의 결정, 조사, 복구 지식, 외부 PR 검토 기록을 보관합니다. |

적용 저장소의 `.agents/skills`와 `.claude/skills` 심볼릭 링크 구조는 [Agent Skills 위치 정책](templates/mydocs/manual/document_structure_guide.md#agent-skills-위치-정책)을 따릅니다. `.hyper-waterfall/version.json`과 manifest 기준 업데이트 흐름은 [배포 manifest와 버전 기록 정책](templates/mydocs/manual/document_structure_guide.md#배포-manifest와-버전-기록-정책), [`docs/lifecycle/update.md`](docs/lifecycle/update.md), [`docs/lifecycle/update_pr.md`](docs/lifecycle/update_pr.md)에 정리되어 있습니다.

프레임워크의 문서 템플릿, GitHub Issue Form, SKILL 진실 원천은 각각 `templates/mydocs/_templates/`, `templates/.github/ISSUE_TEMPLATE/task.yml`, `templates/mydocs/skills/`입니다. 적용 저장소에서는 `.agents/skills`와 `.claude/skills` 심볼릭 링크가 같은 `mydocs/skills` 본문을 가리킵니다.

## 유지보수자 세부 정보

<details>
<summary><strong>기존 적용 저장소 업데이트</strong></summary>

기존 적용 저장소 업데이트는 GitHub Release/tag와 manifest를 기준으로 수행합니다. AI는 [`docs/agent-entrypoint.md`](docs/agent-entrypoint.md)를 진입점으로 삼고, [`docs/lifecycle/update.md`](docs/lifecycle/update.md)의 기존 업데이트 판단 결과 형식에 따라 현재 version, 현재 locale, 요청 locale 또는 전환 요청, 목표 release/tag, 목표 release locale 지원, migration guide, manifest diff, locale manifest diff, Hyper-Waterfall 버전 업데이트 PR 후보를 먼저 보고합니다.

승인된 업데이트 후보를 PR로 전환할 때는 [`docs/lifecycle/update_pr.md`](docs/lifecycle/update_pr.md)를 따릅니다. npm CLI는 같은 판단을 실행하기 쉽게 하는 편의 실행 채널이며, canonical 기준인 GitHub Release/tag, `templates/manifest.json`, migration guide를 대체하지 않습니다. CLI 출력만으로 파일을 자동 적용하지 않고, 승인된 범위만 일반 task 흐름으로 전환합니다.

</details>

<details>
<summary><strong>CLI와 배포 채널</strong></summary>

`hyper-waterfall` CLI는 npm을 통해 배포되며, version을 고정한 `npx` 명령으로 lifecycle 판단을 실행할 수 있습니다. `v0.3.0` release 상태와 publish 후 검증 결과는 [`docs/releases/v0.3.0.md`](docs/releases/v0.3.0.md)에서 관리합니다.

```bash
npx hyper-waterfall@0.3.0 init --repo . --dry-run
npx hyper-waterfall@0.3.0 update --repo . --from v0.2.0 --to v0.3.0 --dry-run
npx hyper-waterfall@0.3.0 doctor --repo .
```

macOS에서는 Homebrew public tap으로 CLI를 설치할 수 있습니다.

```bash
brew install postmelee/tap/hyper-waterfall
hyper-waterfall --version
hyper-waterfall doctor --repo .
```

Homebrew, Docker, Codex plugin, Claude plugin 같은 추가 배포 채널도 canonical 기준을 대체하지 않는 프로토콜 실행 수단으로만 다룹니다. 채널별 목적, 비목표, 운영 비용, 우선순위는 [`docs/distribution-channels.md`](docs/distribution-channels.md)에 정리합니다.

이 Homebrew formula는 npm CLI를 설치하는 wrapper이며, canonical 기준인 GitHub Release/tag, `templates/manifest.json`, migration guide를 대체하지 않습니다. Homebrew는 Node runtime을 의존성으로 설치할 수 있습니다. 아무 tap도 지정하지 않는 `brew install hyper-waterfall` 경로는 Homebrew core 등재가 필요하지만, [#46](https://github.com/postmelee/hyper-waterfall/issues/46) 검토 기준 현재는 제출을 보류하고 public tap 경로를 유지합니다.

</details>

---

## 부록

**Part 1. 최초의 Hyper-Waterfall** ([rhwp](https://github.com/edwardkim/rhwp))

1. [Hyper-Waterfall이란?](#hyper-waterfall이란)
2. [핵심 구조](#핵심-구조)
3. [핵심 원칙](#핵심-원칙)
4. [역할 분담](#역할-분담)
5. [바이브 코딩 vs Hyper-Waterfall](#바이브-코딩-vs-hyper-waterfall)
6. [왜 강력한가 — AI 없이는 닿을 수 없는 지점](#왜-강력한가--ai-없이는-닿을-수-없는-지점)

**Part 2. postmelee/hyper-waterfall**
1. [`postmelee/hyper-waterfall`: 방법론을 재사용 가능한 하네스로](#postmeleehyper-waterfall-방법론을-재사용-가능한-하네스로)
2. [살아있는 예시 — 직접 따라가보기](#살아있는-예시--직접-따라가보기)
3. [설계 원칙](#설계-원칙)
4. [프롬프트 가이드 준수](#프롬프트-가이드-준수)
5. [라이선스](#라이선스)
---

## Hyper-Waterfall이란?
### 거시적 워터폴 + 미시적 애자일, AI가 이 둘을 동시에 가능하게 한다

Hyper-Waterfall은 워터폴의 계획·검증 규율과 애자일의 빠른 task 단위 피드백 루프를 결합합니다. AI가 문서화·구현·검증·보고 비용을 낮춰 두 방식이 같은 프로세스 안에서 공존할 수 있게 합니다.

> 이 방법론은 [`edwardkim/rhwp`](https://github.com/edwardkim/rhwp)와 [`postmelee/alhangeul-macos`](https://github.com/postmelee/alhangeul-macos) 같은 실제 프로젝트 경험을 바탕으로 정제되었습니다.
> 본 방법론의 핵심 철학은 [edwardkim/rhwp · hyper_waterfall.md](https://github.com/edwardkim/rhwp/blob/main/mydocs/manual/hyper_waterfall.md)에 가장 완성된 형태로 정리되어 있습니다. 본 저장소는 그 방법론을 다른 저장소에 손쉽게 적용할 수 있게 모듈화한 프레임워크입니다.

방법론을 먼저 이해하려면 아래 [핵심 구조](#핵심-구조)부터, 우리 저장소의 차별점만 보려면 [`postmelee/hyper-waterfall`: 방법론을 재사용 가능한 하네스로](#postmeleehyper-waterfall-방법론을-재사용-가능한-하네스로)로 점프하세요.

## 핵심 구조

### 거시적 워터폴 + 미시적 애자일

```
거시 (프로젝트 수준) — 워터폴의 규율:
  계획 ──→ 설계 ──→ 구현 ──→ 검증 ──→ 배포
   │       │       │       │       │
   ▼       ▼       ▼       ▼       ▼
  문서화   문서화    문서화   문서화    문서화

미시 (타스크 수준, 수 시간) — 애자일의 속도:
  구현 ──→ 테스트 ──→ 피드백 ──→ 수정 ──→ 테스트 → ... (빠른 반복)
   │       │        │        │        │
  AI      자동화    사람 판단    AI     자동화
```

- 거시적 방향: **워터폴의 규율**로 통제한다 — 계획서, 승인, 단계별 보고, 최종 검증.
- 미시적 실행: **애자일의 빠른 반복**으로 수행한다 — 작업이 허용하는 범위에서 AI와 즉각적인 피드백 루프로 task 주기를 수 시간 안에 완료합니다.
- 각 경계에서는 중요한 맥락을 활성 세션에만 남기지 않고 산출물로 증류합니다.

모든 작업은 문서가 되고, 모든 결정은 검토 가능하게 남으며, 모든 문서는 다음 작업의 맥락이 됩니다.

## 핵심 원칙

> **사람은 생각을 멈추지 않습니다. 세션은 끝나도 프로젝트는 기억해야 합니다.**

AI가 아무리 뛰어나도 방향을 결정하고 품질을 판단하는 것은 사람입니다. AI의 출력을 읽지 않고 수락하는 순간 Hyper-Waterfall은 바이브 코딩으로 전락합니다. 이 원칙을 운영 차원에서 풀어내면 다음 세 가지가 됩니다.

### 1. 사람이 방향을 끝까지 가진다

Stage 전환, 계획 변경, 의미 있는 소스 수정에는 작업지시자의 명시 승인이 필요합니다. AI는 결정을 지원하고 실행하지만 결정권을 갖지 않습니다. 방향·우선순위·아키텍처·품질은 사람의 책임입니다.

### 2. AI에게 항상 충분한 맥락을 준다

의도·범위·계획·결정·검증 기준을 프로젝트 산출물에 담아 매번 프롬프트에서 처음부터 다시 설명하지 않게 합니다. 에이전트는 같은 문서화된 맥락과 기준선에서 작업합니다. 맥락이 흩어지거나 빠지면 AI는 추측으로 빈 자리를 메웁니다.

### 3. 작업 기억을 프로젝트 기억으로 주기적으로 증류한다

Stage 보고서·최종 보고서·commit·PR 본문에 의도·결정·구현 상태·검증 근거를 증류해 기록합니다. 대화는 사라질 수 있지만 구조화된 프로젝트 산출물은 남습니다. 새 세션·에이전트·기여자는 핵심 맥락을 복원해 문서화된 기준선에서 작업을 이어갈 수 있습니다.

## 역할 분담

### 작업지시자 (사람)

사람은 **생각과 판단**에 집중합니다.

- 방향 설정: "다음에 뭘 해야 하는가?"
- 우선순위: "무엇이 더 중요한가?"
- 품질 판단: "이것이 충분히 좋은가?"
- 아키텍처 결정: "이 구조가 올바른가?"
- 도메인 지식: "한컴은 이 경우 어떻게 동작하는가?"
- 피드백: "이 부분이 잘못되었다, 왜냐하면..."

### AI 코딩 에이전트

AI는 **실행과 구조화된 맥락 기록**에 집중합니다.

- 분석: 코드베이스 탐색과 원인 추적
- 계획: 수행계획서와 구현계획서 초안 작성
- 구현: 코드 작성과 테스트 생성
- 검증: 검사 실행과 근거 수집
- 문서: Stage 보고서, 최종 보고서, 기술 문서, commit 메시지
- 디버깅: 로그 분석과 수정안 제시
- 반복: 피드백 반영과 재시도

## 바이브 코딩 vs Hyper-Waterfall

> 바이브 코딩—AI 출력을 읽지 않고 수락하고, AI에게 아키텍처 결정을 맡기고, 이해하지 못하는 코드를 배포하는 것—은 함정입니다. 겉보기에는 동작해도 결과를 이해하거나 문서화하지 않으면 진단과 후속 작업이 취약해집니다.
>
> Hyper-Waterfall은 정반대의 접근을 취합니다. 사람 작업지시자가 방향·품질·아키텍처의 결정권을 유지하고 AI가 빠르게 실행합니다. 프로젝트는 그 실행을 검토하고 재개하는 데 필요한 맥락도 보존합니다.
>
> — [edwardkim/rhwp · 바이브 코딩 vs AI 주도 개발](https://github.com/edwardkim/rhwp#%EB%B0%94%EC%9D%B4%EB%B8%8C-%EC%BD%94%EB%94%A9-vs-ai-%EC%A3%BC%EB%8F%84-%EA%B0%9C%EB%B0%9C)

| | 바이브 코딩 | Hyper-Waterfall |
|---|---|---|
| **사람의 역할** | AI 출력 수락 | 지시, 검토, 결정 |
| **계획** | 없음 — "그냥 만들어" | 수행계획서 → 승인 → 구현계획서 → Stage 단위 실행 |
| **품질 관문** | 동작하길 바람 | 단계마다 검증 + 승인 게이트 + Open PR 리뷰 |
| **프로젝트 기억** | 맥락이 채팅이나 한 사람의 머릿속에 남음 | 의도·결정·진행·근거를 프로젝트 산출물로 증류 |
| **디버깅** | 지속되는 진단 없이 AI에게 AI 버그 수정 요청 | 진단과 근거를 보존하고 AI가 승인된 수정 구현 |
| **아키텍처** | 우연히 형성 | 작업지시자가 의도적으로 결정 |
| **문서** | 없거나 나중에 작성 | task 전 과정에서 `mydocs/` 산출물과 Issue/PR 본문 생성 |
| **인수인계** | 수동으로 다시 설명 | 새 세션과 기여자가 산출물에서 핵심 맥락 복원 |
| **결과물** | 취약하고 유지보수 어려움 | 추적·검토·인수인계·재개 가능 |

## 왜 강력한가 — AI 없이는 닿을 수 없는 지점

거시적 워터폴과 미시적 애자일은 오랫동안 trade-off였습니다. 규율은 작업을 느리게 했고, 속도는 규율을 약화시키곤 했습니다. AI 코딩 에이전트는 계획·문서화·구현·검증 비용을 낮춰 두 방식을 같은 워크플로에서 실용적으로 만듭니다.

### 1. 속도는 잃지 않으면서 규율을 회복한다

워터폴이 무거워진 큰 이유 중 하나는 **사람이 모든 계획·문서·구현·검증을 직접 감당했기 때문**입니다. AI가 이를 빠르게 초안 작성하고 실행하므로 빠른 반복을 포기하지 않고도 규율을 회복할 수 있습니다.

### 2. 작업 이력을 지속되는 프로젝트 기억으로 바꾼다

결정·근거·진행 상황·검증 결과·피드백·트러블슈팅이 `mydocs/`, commit, PR, Issue에 남습니다. 한 사람이나 세션에 집중된 맥락이 사라져도 다음 사람이나 AI 세션은 **같은 문서화된 기준선**에서 시작할 수 있습니다.

이는 bus-factor 위험을 줄이는 데 그치지 않고 축적된 작업 이력을 미래 task의 재사용 가능한 맥락으로 만듭니다.

### 3. 사람은 결정에, AI는 실행에 집중한다

사람이 방향·우선순위·아키텍처·품질을 끝까지 책임지고, AI는 탐색·구현·테스트·문서·반복을 맡습니다. 한 사람의 집중력으로는 닿을 수 없는 작업량이 한 사이클 안에 들어옵니다. **AI는 배율기**입니다 — 좋은 프로세스 위에 올리면 비범한 결과물이 됩니다.

### 4. 세션·에이전트·기여자·장소를 넘어 작업을 이동한다

[rhwp](https://github.com/edwardkim/rhwp)의 메인테이너는 사무실, 집, 이동 중 — 3곳에서 각각 다른 클로드 세션으로 작업한다. 매번 새 세션은 이전의 기억이 없다.

하지만 문서가 있으면:

| "지금 뭘 해야 하지?" | → `orders/20260409.md` |
|---|---|
| "어디까지 했지?" | → `working/task_m100_86_stage1.md` |
| "어떻게 하기로 했지?" | → `plans/task_m100_86_impl.md` |
| "왜 이 방식으로 하지?" | → `feedback/` + `tech/` |
| "이 함정은 뭐지?" | → `troubleshootings/` |

작업 자체가 지속적으로 인수인계 자료를 만들기 때문에 작업지시자가 맥락을 수동으로 전달하는 시간이 크게 줄어듭니다.

---

## `postmelee/hyper-waterfall`: 방법론을 재사용 가능한 하네스로

> 이 저장소는 [rhwp](https://github.com/edwardkim/rhwp)에서 처음 도입된 Hyper-Waterfall 방법론을 재사용 가능한 multi-agent 워크플로 하네스로 확장합니다.

### 1. 프롬프트 한 줄로 어떤 저장소에든 적용 — 모듈화 + placeholder 치환

원본 방법론(rhwp)은 그 저장소의 문서·관습과 강하게 결합되어 있어, 다른 프로젝트에 그대로 가져다 쓰기 어려웠습니다. 본 저장소는 운영 규칙·매뉴얼·SKILL을 `templates/`로 분리하고 진입 절차를 [`docs/agent-entrypoint.md`](docs/agent-entrypoint.md)로 정형화했습니다. 결과적으로 **AI 코딩 도구에 한 줄 프롬프트만 보내면** 어떤 저장소에든 적용됩니다. AI가 진입 절차를 따라 `REPO_SLUG`·`BASE_BRANCH` 같은 placeholder까지 자동으로 치환합니다.

기존 적용 저장소 업데이트를 위한 lifecycle 기준도 별도 문서로 정리하고 있습니다. GitHub Release/tag, manifest, migration guide, `.hyper-waterfall/version.json`을 읽어 현재 version, 현재 locale, 요청 locale 또는 전환 요청, 목표 release/tag, 목표 release locale 지원, manifest diff, locale manifest diff, Hyper-Waterfall 버전 업데이트 PR 후보를 먼저 판단하는 구조입니다. 세부 기준은 [`docs/lifecycle/update.md`](docs/lifecycle/update.md)와 [`docs/lifecycle/update_pr.md`](docs/lifecycle/update_pr.md)에 둡니다. 본 저장소 자체가 자기 자신에 적용한 dogfooding 첫 사례입니다 (Issue #1, PR #2).

### 2. 구조화된 프로젝트 산출물을 공식 프롬프팅 가이드와 정렬

작업 문서 포맷이 [OpenAI](https://developers.openai.com/api/docs/guides/prompt-guidance)와 [Anthropic](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices)의 공식 프롬프팅 가이드 핵심을 자연스럽게 만족하도록 설계했습니다. 특히 GitHub Issue/PR 템플릿은 GitHub 플랫폼 산출물의 본문 구조를 잡고, `templates/mydocs/_templates/`는 계획서·보고서·피드백·외부 PR 검토 문서의 출력 형식을 명시합니다.

> AI가 문서를 작성하고 다시 참조 및 레퍼런스로 사용하는 재귀적 과정에서 응답 품질 저하를 최소화할 수 있습니다.

- **명확성**: 작업 목표와 경계를 정의합니다.
- **일관성**: 반복되는 작업 산출물이 중앙 형식을 공유합니다.
- **단계적 진행**: 작업을 작고 검토 가능한 Stage로 나눕니다.
- **맥락**: 미래 에이전트가 읽을 위치에 핵심 정보를 기록합니다.
- **출력 형식**: task 결과를 예측 가능한 프로젝트 산출물로 만듭니다.
- **멈춤 조건**: 명시적인 결정 경계에서 에이전트가 사람에게 제어권을 돌려줍니다.

상세 매핑은 아래 [프롬프트 가이드 준수](#프롬프트-가이드-준수) 섹션에서 펼쳐 확인할 수 있습니다.

### 3. 토큰·컨텍스트 효율적인 규칙으로 여러 에이전트를 지원

rhwp는 `CLAUDE.md` 한 파일에 운영 규칙·문서 구조·폴더 정책·명명 규칙·PR 처리를 모두 인라인했고, `AGENTS.md`가 없어 Claude Code 전용으로 동작했습니다. 본 저장소는 두 축으로 분리·확장했습니다.

**(1) Multi-agent 호환**: `AGENTS.md`를 단일 진실 원천으로 두고 `CLAUDE.md`는 `@AGENTS.md` 한 줄로 참조합니다. SKILL은 `.agents/skills`(Codex) + `.claude/skills`(Claude Code) 심볼릭 링크로 같은 본문이 양쪽 도구에서 인식됩니다. 새로 추가되는 SKILL 인식 도구도 같은 패턴으로 확장됩니다.

**(2) 운영 규칙·SKILL·매뉴얼·템플릿 분리**: `AGENTS.md`에는 매 턴 시스템 프롬프트로 적재될 정책·제약·인덱스만 두고, 절차 상세는 [`mydocs/manual/`](templates/mydocs/manual/)의 주제별 매뉴얼(문서 구조, 타스크 진행, Git, PR, lifecycle, release/update, 충돌 규칙), 각 `mydocs/` 폴더의 `README.md`, [`.github/`](templates/.github/)의 GitHub Issue/PR 템플릿, [`mydocs/_templates/`](templates/mydocs/_templates/)의 문서 출력 형식, [`mydocs/skills/`](templates/mydocs/skills/)의 7개 SKILL로 분리했습니다.

효과:

- **토큰 효율**: 매 턴 시스템 프롬프트로 적재되는 분량을 축소. 매뉴얼·SKILL 본문은 호출 시점에만 컨텍스트로 들어옵니다.
- **컨텍스트 효율**: 모델은 필요한 시점에 필요한 절차만 읽습니다. 무관한 절차로 컨텍스트가 오염되지 않습니다.
- **의도 전달 명확성**: GitHub 템플릿과 중앙 템플릿이 반복 산출물의 구조를 고정하고, 단계별 SKILL이 절차의 어느 시점에 호출되는지 명시해 AI가 추론으로 절차나 출력 형식을 재구성하지 않습니다.
- **모델 간 이식성**: SKILL은 표준 형식이라 다른 SKILL 인식 도구로 옮기기 쉽습니다.
- **공유 맥락**: 서로 다른 에이전트가 도구별 채팅 기록 대신 같은 계획서·보고서·결정·검증 근거를 읽습니다.

## 살아있는 예시 — 직접 따라가보기

이 저장소 자체가 하이퍼-워터폴을 자기 자신에게 적용한 첫 사례입니다. 적용 여부를 검토하기 전에 실제 운영이 어떻게 돌아가는지 보고 싶다면 다음 순서로 둘러보세요.

1. **이슈** [`#1` 하이퍼-워터폴 자기 적용 (dogfooding)](https://github.com/postmelee/hyper-waterfall/issues/1) — 라벨 3개, 마일스톤 M010, linked PR이 자동 표시되는 깔끔한 구조 (상태 알림 댓글 없음)
2. **Pull Request** [`#2`](https://github.com/postmelee/hyper-waterfall/pull/2) — Open PR 본문 형식: 요약 4 bullet (대상 타스크/왜/무엇/리뷰 포인트), Stage 5개 timeline 이중 링크(단계 보고서 + commit URL), 영향 영역 표, 작업 문서, 검증 결과와 근거
3. **수행계획서** [`mydocs/plans/task_m010_1.md`](mydocs/plans/task_m010_1.md) — 목적·배경·범위·설계 방향·예상 변경 파일·잠정 단계·검증 계획·리스크
4. **구현계획서 5단계** [`mydocs/plans/task_m010_1_impl.md`](mydocs/plans/task_m010_1_impl.md) — 단계별 산출물·검증 명령·커밋 메시지를 사전에 확정
5. **단계 보고서 5개** [`mydocs/working/`](mydocs/working/) — 각 Stage 종료 시 산출물·검증 결과·잔여 위험·다음 단계 영향
6. **최종 보고서** [`mydocs/report/task_m010_1_report.md`](mydocs/report/task_m010_1_report.md) — 5단계 종합, 변경 전·후 정량 비교, 수용 기준 검증
7. **오늘할일** [`mydocs/orders/`](mydocs/orders/) — 일일 보드 형식 (마일스톤별 표 + 완료 시각)
8. **commit log** [`git log` (main)](https://github.com/postmelee/hyper-waterfall/commits/main) — `Task #1: 수행 계획서 작성`부터 `pr-merge-cleanup`까지 12개 task 커밋이 시간 순서로 보존

이 첫 task는 scope 확장 두 번을 거치며 5단계로 진행됐습니다. 승인 게이트, Stage 경계의 작업 맥락 증류, scope 변경 처리, PR 본문 재작성, merge 후 정리까지 README의 절차를 살아있는 산출물로 확인할 수 있습니다.

## 설계 원칙

- 핵심 작업 맥락은 그것을 만든 세션보다 오래 남아야 합니다.
- 원본 채팅이 아니라 구조화된 프로젝트 산출물이 재개 가능한 작업의 진실 원천입니다.
- 의미 있는 소스 변경에는 사람의 결정 게이트가 필요합니다.
- 작업지시자는 방향·우선순위·아키텍처·품질의 결정권을 유지합니다.
- 최신 상태는 이슈 metadata, 현재 branch 또는 PR, `mydocs/`에서 찾을 수 있어야 합니다.
- 이슈 진행 추적은 GitHub의 linked PR 자동 cross-reference와 라벨/마일스톤에 위임하고, 댓글은 토론·블로커·결정 기록 용도로만 둡니다.
- 이 프레임워크는 다양한 프로젝트 유형에서 동작해야 합니다. 특정 언어, 빌드, 배포, 제품 규칙은 core가 아니라 대상 저장소의 템플릿과 설정에 둡니다.
- 프로세스에는 엄격하고, 도구에는 유연해야 합니다.

> Hyper-Waterfall은 새로운 마법이 아닙니다. 사람의 판단, 지속되는 작업 이력, 검증 근거, 인수인계 맥락을 보존하는 프로세스 위에서 AI를 배율기로 사용합니다.

## 프롬프트 가이드 준수

Hyper-Waterfall은 OpenAI와 Anthropic의 공식 프롬프팅 가이드의 핵심을 개발 프로세스 차원에서 구현합니다. 한 번의 좋은 프롬프트에 그치지 않고, **좋은 맥락·명확한 출력·검증·멈춤 조건을 워크플로가 반복 생산하는 프로젝트 구조**를 만듭니다.

### 정합성 요약

| 원칙 | Hyper-Waterfall에서 구현되는 방식 | 효과 |
|---|---|---|
| 명확한 목표 | GitHub Issue, 수행계획서, 구현계획서 | AI가 작업 범위와 성공 기준을 먼저 이해함 |
| 충분한 맥락 | `mydocs/`의 계획서·보고서·피드백·기술 조사 | 새 세션이 프로젝트 산출물에서 핵심 맥락 복원 |
| 출력 형식 제약 | `mydocs/_templates/`, Issue/PR template | 계획·보고·검증 결과가 매번 같은 구조로 남음 |
| 단계적 진행 | Stage 단위 구현·검증·보고 | 복잡한 작업을 검토 가능한 단위로 분할 |
| 검증 기준 | Stage 보고서, 최종 보고서, PR 본문 | 결과물을 감이 아니라 기록된 기준으로 판단 |
| 멈춤 조건 | 사람의 결정 게이트 | AI가 임의로 다음 단계로 넘어가지 않음 |
| 지속되는 프로젝트 기억 | `mydocs/`, commit history, Issue/PR timeline | 채팅이 사라져도 핵심 작업 맥락 유지 |
| 컨텍스트 경량화 | `1 Issue = 1 Task = 1 Branch = 1 Session` | 세션이 작고 선명하게 유지됨 |
| Multi-agent 연속성 | 공통 규칙·SKILL·매뉴얼·산출물 | 서로 다른 에이전트가 같은 기준선에서 이어서 작업 |

<details>
<summary><strong>OpenAI 프롬프팅 가이드 매핑</strong> · 출처: <a href="https://developers.openai.com/api/docs/guides/prompt-guidance">OpenAI prompt guidance</a></summary>

1. **결과물을 먼저 정한다.**
   Hyper-Waterfall은 작업 시작부터 Issue, 수행계획서, 구현계획서, Stage 보고서, 최종 보고서, PR이라는 산출물을 명확히 둡니다. AI에게 "잘 해줘"라고 맡기는 게 아니라, 무엇을 남겨야 하는지 먼저 고정합니다.

2. **좋은 답변의 기준을 적는다.**
   각 Stage는 구현뿐 아니라 검증 기준과 리뷰 포인트를 함께 남깁니다. 그래서 AI의 결과물은 감으로 평가되지 않고, 문서화된 기준 위에서 판단됩니다.

3. **제약 조건을 짧게 건다.**
   Hyper-Waterfall은 "승인 없이 다음 단계 진행 금지", "소스 수정 전 승인", "Issue 기준 추적"처럼 AI가 넘지 말아야 할 경계를 명시합니다. 자유도를 없애는 게 아니라, 폭주하지 않게 레일을 까는 방식입니다.

4. **필요한 근거 수준을 말한다.**
   구현 결과는 Stage 보고서, 검증 로그, PR 본문으로 증류됩니다. 단순히 코드가 바뀐 것이 아니라, 왜 바뀌었고 어떻게 확인했는지가 저장소에 남습니다.

5. **출력 형식을 정한다.**
   `mydocs/_templates/`는 계획서, 구현계획서, 단계 보고서, 최종 보고서, 피드백, 기술 조사, 트러블슈팅, 외부 PR 검토 문서의 expected output shape를 파일로 고정합니다. PR 본문은 `.github/pull_request_template.md`가 리뷰 화면에 맞춰 구조화합니다. AI의 답변이 흩어지는 대신, 다음 작업자가 다시 읽을 수 있는 구조가 됩니다.

6. **언제 멈출지도 알려준다.**
   Hyper-Waterfall은 Stage 경계마다 멈추고 사람의 승인을 기다립니다. AI가 끝까지 달리는 것이 아니라, 사람이 방향을 확인할 수 있는 정지선을 둡니다.

</details>

<details>
<summary><strong>Anthropic 프롬프팅 가이드 매핑</strong> · 출처: <a href="https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices">Claude prompting best practices</a></summary>

1. **명확하고 직접적인 지시.**
   작업의 의도를 Issue, 수행계획서, 구현계획서로 단계마다 명시화합니다. 모호한 의도를 모델에 던지는 대신, 무엇을 만들지·왜 만드는지·어디까지 만들지를 게이트 전에 고정합니다.

2. **워크플로우와 목표 맥락 제공.**
   작업이 어떤 흐름의 일부인지, 어떤 결과물의 어디에 들어가는지를 매번 프롬프트에 적게 하지 않습니다. `mydocs/`, Issue, PR 본문에 그 맥락이 박혀 있어 모델이 자연스럽게 같은 컨텍스트를 읽습니다.

3. **순차적 단계 제시.**
   Stage 단위 진행과 단계마다의 승인 게이트가 Anthropic이 권장하는 "지시를 순차적 단계로 쪼개기"를 그대로 구현합니다.

4. **출력 형식 통제.**
   계획서·단계 보고서·최종 보고서·피드백·기술 조사·외부 PR 검토 문서는 `mydocs/_templates/`의 desired output format을 따르고, PR 본문은 `.github/pull_request_template.md`를 따릅니다. 모델이 "어디에 무엇을 적을지"를 매 작업마다 발명하지 않게 합니다.

5. **장기 작업과 외부 기억.**
   Anthropic 가이드가 강조하는 long-horizon agentic work와 memory task에 `mydocs/`가 그대로 대응합니다. 채팅 컨텍스트가 사라져도 파일시스템에 작업 기억이 증류되어 남습니다.

6. **Literal 지시 따름과 정합.**
   더 literal하게 지시를 따르는 모델은 명시된 범위에 더 정확히 묶이는 경향이 있습니다. Hyper-Waterfall은 "소스 수정 전 승인", "승인 없이 다음 Stage 진행 금지", "Issue 기준 추적" 같은 경계를 애초에 문서화하므로 literal한 모델일수록 잘 작동합니다.

> Hyper-Waterfall은 최대 자율성보다 사람의 통제권, 지속되는 작업 이력, 추적 가능성을 우선합니다. 한 번의 interactive coding보다 높은 층에서 task 경계와 산출물 요구사항을 추가합니다. 폴더 구조·파일명 규칙·중앙 템플릿은 전체 task 생명주기에서 인라인 프롬프트 형식만으로 제공하기 어려운 구조적 역할을 수행합니다.
>
> **한 줄 요약**: Hyper-Waterfall은 프롬프팅 모범 사례를 단일 프롬프트 문장이 아니라 반복 가능한 사람 주도 AI 코딩 워크플로로 구현합니다.

</details>

## 라이선스

MIT. 자세한 내용은 [LICENSE](LICENSE)를 참고하세요.
