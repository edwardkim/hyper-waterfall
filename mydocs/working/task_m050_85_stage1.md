# 프로젝트 기억 중심 README 소개 개편 및 다국어 동기화 Stage 1 완료보고서

GitHub Issue: [#85](https://github.com/postmelee/hyper-waterfall/issues/85)
구현계획서: [`task_m050_85_impl.md`](../plans/task_m050_85_impl.md)
Stage: 1

## 단계 목적

작업지시자가 제공한 영문 README 초안을 기본으로 `README.md`의 대표 포지셔닝을 승인 중심 설명에서 작업 맥락 증류와 지속되는 프로젝트 기억 중심 설명으로 개편한다. 초안의 구성과 문장을 최대한 유지하면서 완전한 맥락 복원으로 읽히는 표현, 권장 세션 모델의 강도, 핵심 용어 반복을 보정하고 기존 운영 사실을 보존한다.

## 산출물

| 파일 | 변경 요약 |
|---|---|
| `README.md` | 761줄, 초안 기반 전면 편집. 상단 소개·Why·비교·Strengths·Appendix를 프로젝트 기억 중심으로 정렬하고 정확성 보정 16문장 반영 |
| `mydocs/working/task_m050_85_stage1.md` | Stage 1 변경 범위, 검증 근거, 다음 단계 현지화 기준 기록 |

## 본문 변경 정도 / 본문 무손실 여부

- 현재 `main`의 705줄 README에서 274줄 추가, 218줄 삭제되어 최종 761줄이 되었다.
- 작업지시자가 제공한 `/Users/melee/Downloads/README(1).md` 초안을 전체 구조와 문장의 기준으로 사용했다.
- 최종 영문 README와 초안의 차이는 16줄 추가·16줄 삭제이며 다음 범주로 제한된다.
  - `reconstruct`/`restore`를 핵심 맥락 복원과 문서화된 기준선 표현으로 완화
  - `1 Issue = 1 Task = 1 Branch = 1 Session`을 권장 운영 모델로 명시
  - 후반부 `project memory` 반복을 `shared context`, `documented context`, `durable work history`, `handoff context`로 조정
- 기존 CLI 명령, 버전, Homebrew 명령, 7개 핵심 SKILL 이름은 `main:README.md`와 자동 대조해 동일함을 확인했다.
- 설치·업데이트·Task 절차·배포 정책·dogfooding 사례의 기능적 사실은 보존했다.
- 근거가 약한 `100x faster`, `impossible before AI`와 기존 승인 중심 H2는 최종 본문에 남지 않는다.

## 검증 결과

실행 명령:

```bash
git diff -- README.md
rg -n "From Ephemeral Sessions to Persistent Project Memory|human-governed AI coding workflow|Context distillation|The session ends" README.md
rg -n "npx hyper-waterfall@0.3.0|brew install postmelee/tap/hyper-waterfall|task-register|task-start|task-stage-report|task-final-report|pr-merge-cleanup|external-pr-review" README.md
rg -n "100x faster|impossible before AI|A Methodology for Turning AI Pair Programming" README.md
ruby -e 's=File.read(ARGV[0]); s.scan(/\[[^\]]*\]\(([^)]+)\)/).flatten.each{|u| next if u =~ %r{\A(?:https?://|mailto:|#)}; p=u.sub(/#.*/, ""); abort("missing: #{u}") unless File.exist?(p)}' README.md
ruby -e 's=File.read(ARGV[0]); abort("unbalanced fences") unless s.lines.count{|l| l.start_with?("```")}.even?' README.md
git diff --check
```

결과:

- OK — 영문 diff를 확인했으며 492줄 변경은 제공된 초안의 전면 편집 범위와 일치한다.
- OK — 새 제목, `human-governed AI coding workflow`, `Context distillation`, 대표 슬로건이 모두 확인됐다.
- OK — `npx hyper-waterfall@0.3.0`, Homebrew 설치 명령과 7개 핵심 SKILL 이름이 확인됐다.
- OK — 제거 대상 검색은 빈 출력과 종료 코드 1로, 세 문자열이 남지 않았음을 확인했다.
- OK — 모든 로컬 상대 링크의 대상 파일이 존재한다.
- OK — Markdown 코드 fence 개수가 짝수다.
- OK — `git diff --check`가 경고 없이 통과했다.

추가 검증:

```bash
git diff --no-index --stat -- /Users/melee/Downloads/README\(1\).md README.md
git diff --no-index --unified=0 -- /Users/melee/Downloads/README\(1\).md README.md
ruby -e 'require "open3"; base,_=Open3.capture2("git","show","main:README.md"); cur=File.read("README.md"); pats=[/npx hyper-waterfall@[^\n]+/,/brew install postmelee\/tap\/hyper-waterfall/,/hyper-waterfall (?:init|doctor|--version)[^\n]*/,/`(?:task-register|task-start|task-stage-report|task-final-report|pr-merge-cleanup|external-pr-review|todo)`/]; pats.each{|p| b=base.scan(p).sort; c=cur.scan(p).sort; abort("mismatch #{p}: #{b} != #{c}") unless b==c}; puts "operational facts preserved: #{pats.length} pattern groups"'
```

- OK — 초안 대비 차이는 정확성 보정 16줄 추가·16줄 삭제다.
- OK — 네 패턴 그룹에서 `main`과 최종 영문의 명령·SKILL 표기가 일치했다.

## 잔여 위험

- 영문 README는 초안 기반 전면 편집이므로 Stage 2·3 현지화 중 운영 정보의 언어별 대응을 계속 확인해야 한다.
- `persistent project memory`는 핵심 포지셔닝 용어로 여러 주요 섹션에 의도적으로 남아 있다. 후속 언어에서도 같은 위치와 강도로 사용하되 과잉 반복은 피해야 한다.
- 외부 OpenAI·Anthropic 링크의 실시간 접근성은 이번 로컬 문서 검증 범위에 포함하지 않았다. 링크 URL 자체는 기존 정보와 초안에서 보존됐다.

## 다음 단계 영향

- Stage 2는 현재 `README.md`를 구조와 의미의 진실 원천으로 사용한다.
- 한국어에서는 `human governance`를 사람의 결정권, `context distillation`을 작업 맥락 증류, `persistent project memory`를 지속되는 프로젝트 기억, `resumable work`를 재개 가능한 작업으로 현지화한다.
- 영문에서 완화한 `recover the essential context`, `documented baseline`, 권장 세션 모델의 표현 강도를 동일하게 유지한다.

## 승인 요청

- Stage 1 영문 README와 검증 결과를 승인하면 Stage 2 한국어 README 동기화로 진행한다.
