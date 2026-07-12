# 프로젝트 기억 중심 README 소개 개편 및 다국어 동기화 구현계획서

수행계획서: [`task_m050_85.md`](task_m050_85.md)
GitHub Issue: [#85](https://github.com/postmelee/hyper-waterfall/issues/85)
마일스톤: M050

## 단계 개요

| Stage | 제목 | 주요 산출 | 검증 |
|---|---|---|---|
| 1 | 영문 README 포지셔닝 개편 | `README.md`, `mydocs/working/task_m050_85_stage1.md` | 초안 반영, 운영 정보 보존, 링크·Markdown 구조 확인 |
| 2 | 한국어 README 동기화 | `README.ko.md`, `mydocs/working/task_m050_85_stage2.md` | 영문-한국어 섹션·핵심 메시지 대응, 링크 확인 |
| 3 | 중국어 README 동기화 및 통합 검증 | `README.zh-CN.md`, `mydocs/working/task_m050_85_stage3.md` | 세 언어 정합성, 링크·명령·버전·SKILL, `npm test` |

## 문서 위치 확인

| 파일 | 수행계획서상 선택 위치 | Stage 산출물 경로 | 일치 여부 | 비고 |
|---|---|---|---|---|
| `README.md` | 저장소 루트 | Stage 1 `README.md` | OK | 영어 사용자·기여자의 공식 진입 문서 |
| `README.ko.md` | 저장소 루트 | Stage 2 `README.ko.md` | OK | 한국어 사용자·기여자의 공식 진입 문서 |
| `README.zh-CN.md` | 저장소 루트 | Stage 3 `README.zh-CN.md` | OK | 중국어 간체 사용자·기여자의 공식 진입 문서 |
| `mydocs/working/task_m050_85_stage{N}.md` | `mydocs/working/` | 각 Stage | OK | 단계별 작업 맥락과 검증 근거 |
| `mydocs/report/task_m050_85_report.md` | `mydocs/report/` | 최종 보고 | OK | 최종 결과와 수용 기준 검증 기록 |

## Stage 1 — 영문 README 포지셔닝 개편

### 산출물

신규:

- `mydocs/working/task_m050_85_stage1.md`

수정:

- `README.md`

### 변경 내용

- `/Users/melee/Downloads/README(1).md`를 영문 README 변경의 기본 초안으로 사용한다.
- 상단 소개, `Why Hyper-Waterfall?`, 비교표, 즉시 효과, Strengths와 Appendix의 관련 설명을 프로젝트 기억 중심으로 정렬한다.
- `human-governed AI coding workflow`, `context distillation`, `persistent project memory`, `resumable work`의 관계를 명확히 한다.
- 문서가 모든 맥락을 완전히 재현한다고 단정하는 표현은 핵심 맥락과 문서화된 기준선 복원으로 완화한다.
- `1 Issue = 1 Task = 1 Branch = 1 Session`은 권장 운영 모델로 표현한다.
- 후반부의 `project memory` 반복은 `shared context`, `documented baseline`, `handoff context`, `durable work history`로 문맥에 맞게 조정한다.
- 기존 명령, 버전, 링크, Task 절차, SKILL 목록, 배포 정책, 실제 사례를 현재 README와 대조해 보존한다.
- 근거가 약한 `100x faster`, `impossible before AI` 표현을 제거하거나 방어 가능한 표현으로 바꾼다.

### 검증

```bash
git diff -- README.md
rg -n "From Ephemeral Sessions to Persistent Project Memory|human-governed AI coding workflow|Context distillation|The session ends" README.md
rg -n "npx hyper-waterfall@0.3.0|brew install postmelee/tap/hyper-waterfall|task-register|task-start|task-stage-report|task-final-report|pr-merge-cleanup|external-pr-review" README.md
rg -n "100x faster|impossible before AI|A Methodology for Turning AI Pair Programming" README.md
ruby -e 's=File.read(ARGV[0]); s.scan(/\\[[^\\]]*\\]\\(([^)]+)\\)/).flatten.each{|u| next if u =~ %r{\\A(?:https?://|mailto:|#)}; p=u.sub(/#.*/, ""); abort("missing: #{u}") unless File.exist?(p)}' README.md
ruby -e 's=File.read(ARGV[0]); abort("unbalanced fences") unless s.lines.count{|l| l.start_with?("```")}.even?' README.md
git diff --check
```

### 커밋

```text
Task #85 Stage 1: 영문 README 프로젝트 기억 중심 개편
```

## Stage 2 — 한국어 README 동기화

### 산출물

신규:

- `mydocs/working/task_m050_85_stage2.md`

수정:

- `README.ko.md`

### 변경 내용

- Stage 1에서 확정한 영문 README의 전체 구조와 의미를 한국어로 현지화한다.
- 대표 제목은 세션 종료 후에도 프로젝트 기억이 남는다는 메시지를 자연스러운 한국어로 전달한다.
- `human governance`, `context distillation`, `persistent project memory`, `resumable work`를 각각 사람의 결정권, 작업 맥락 증류, 지속되는 프로젝트 기억, 재개 가능한 작업으로 일관되게 옮긴다.
- 영문에서 완화한 보장 표현과 권장 운영 모델의 강도를 한국어에서도 동일하게 유지한다.
- 기존 한국어 명령, 링크, Task 절차, SKILL 목록, 배포 정책, 실제 사례를 보존한다.
- 한국어 독자에게 어색한 직역을 피하되 영문과 섹션 순서 및 정보량을 맞춘다.

### 검증

```bash
git diff -- README.ko.md
rg -n "세션은 끝나도|프로젝트 기억|작업 맥락 증류|사람의 결정권|재개 가능한" README.ko.md
rg -n "npx hyper-waterfall@0.3.0|brew install postmelee/tap/hyper-waterfall|task-register|task-start|task-stage-report|task-final-report|pr-merge-cleanup|external-pr-review" README.ko.md
ruby -e 's=File.read(ARGV[0]); s.scan(/\\[[^\\]]*\\]\\(([^)]+)\\)/).flatten.each{|u| next if u =~ %r{\\A(?:https?://|mailto:|#)}; p=u.sub(/#.*/, ""); abort("missing: #{u}") unless File.exist?(p)}' README.ko.md
ruby -e 's=File.read(ARGV[0]); abort("unbalanced fences") unless s.lines.count{|l| l.start_with?("```")}.even?' README.ko.md
git diff --check
```

### 커밋

```text
Task #85 Stage 2: 한국어 README 프로젝트 기억 중심 동기화
```

## Stage 3 — 중국어 README 동기화 및 통합 검증

### 산출물

신규:

- `mydocs/working/task_m050_85_stage3.md`

수정:

- `README.zh-CN.md`

### 변경 내용

- Stage 1에서 확정한 영문 README의 전체 구조와 의미를 중국어 간체로 현지화한다.
- `human governance`, `context distillation`, `persistent project memory`, `resumable work`의 관계와 표현 강도를 영문·한국어와 맞춘다.
- 기존 중국어 명령, 링크, Task 절차, SKILL 목록, 배포 정책, 실제 사례를 보존한다.
- 세 README의 H2/H3 구조, 핵심 메시지, 명령, 버전, 경로, SKILL 이름을 통합 비교한다.
- 모든 로컬 링크와 코드 블록 구조를 검사하고 전체 테스트를 실행한다.

### 검증

```bash
git diff -- README.zh-CN.md
rg -n "持久项目记忆|上下文提炼|人类治理|可恢复" README.zh-CN.md
rg -n "npx hyper-waterfall@0.3.0|brew install postmelee/tap/hyper-waterfall|task-register|task-start|task-stage-report|task-final-report|pr-merge-cleanup|external-pr-review" README.zh-CN.md
ruby -e 'ARGV.each{|f| s=File.read(f); s.scan(/\\[[^\\]]*\\]\\(([^)]+)\\)/).flatten.each{|u| next if u =~ %r{\\A(?:https?://|mailto:|#)}; p=u.sub(/#.*/, ""); abort("#{f}: missing #{u}") unless File.exist?(p)}}' README.md README.ko.md README.zh-CN.md
ruby -e 'ARGV.each{|f| s=File.read(f); abort("#{f}: unbalanced fences") unless s.lines.count{|l| l.start_with?("```")}.even?}' README.md README.ko.md README.zh-CN.md
rg -n "npx hyper-waterfall@0.3.0|brew install postmelee/tap/hyper-waterfall" README.md README.ko.md README.zh-CN.md
rg -n "task-register|task-start|task-stage-report|task-final-report|pr-merge-cleanup|external-pr-review|todo" README.md README.ko.md README.zh-CN.md
npm test
git diff --check
git status --short
```

### 커밋

```text
Task #85 Stage 3: 중국어 README 동기화와 통합 검증
```

## 검증

- 각 Stage 검증 명령은 단계 보고서 작성 전에 실행한다.
- 검색 명령에서 제거 대상 문자열이 없는지 확인하는 검증은 빈 출력과 종료 코드 1을 기대 결과로 기록한다.
- 실패한 검증은 단계 완료로 처리하지 않는다.
- 계획 변경이 필요하면 구현계획서를 먼저 갱신하고 작업지시자 승인을 받는다.
- 문서 위치가 수행계획서 판단과 달라지면 구현 전에 수행계획서 또는 구현계획서를 갱신하고 작업지시자 승인을 받는다.

## 커밋

- 구현계획서 자체는 `Task #85: 구현 계획서 작성`으로 별도 커밋한다.
- 단계 커밋은 각 언어 README와 `mydocs/working/task_m050_85_stage{N}.md`를 함께 묶는다.
- 커밋 메시지는 `Task #85 Stage {N}: {핵심 내용 요약}` 형식을 따른다.

## 단계 의존성

- Stage 2는 Stage 1 영문 문구와 구조가 확정되고 단계 보고서가 승인된 뒤 진행한다.
- Stage 3은 Stage 2 한국어 현지화와 단계 보고서가 승인된 뒤 진행한다.
- 최종 보고는 Stage 3에서 세 README 통합 검증과 단계 보고서가 승인된 뒤 진행한다.

## 위험과 대응

- **초안과 현재 README의 불필요한 문체 차이**: 초안을 기본으로 하되 운영 정보와 인용 맥락은 현재 문서를 함께 대조한다.
- **완전한 기억 복원으로 읽히는 표현**: `essential context`, `documented baseline`, `handoff context` 중심으로 한계를 명확히 한다.
- **다국어 의미 편차**: 영문을 진실 원천으로 두고 H2/H3 및 핵심 용어를 단계별로 대응 확인한다.
- **중국어 번역 품질**: 방법론 용어는 설명 문맥을 함께 제공하고 고유명사, 명령, 경로는 번역하지 않는다.
- **로컬 링크 검사 오탐**: 외부 URL, mailto, 문서 내부 anchor를 제외하고 저장소 루트 기준 상대 경로만 검사한다.
- **운영 정보 누락**: 세 README에서 버전, CLI 명령, 7개 SKILL 이름을 공통 검색하고 기존 README diff를 수동 검토한다.

## 승인 요청 사항

- 영문, 한국어, 중국어를 각각 독립 Stage로 수정·검증·보고하는 3단계 구성
- 제공된 영문 초안을 기본으로 사용하면서 정확성, 반복, 운영 사실만 제한적으로 보정하는 Stage 1 범위
- 영문 최종안을 의미와 구조의 진실 원천으로 삼아 한국어와 중국어를 현지화하는 방향
- 위 Stage별 산출물, 검증 명령, 커밋 메시지
