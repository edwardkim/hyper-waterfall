# 프로젝트 기억 중심 README 소개 개편 및 다국어 동기화 Stage 2 완료보고서

GitHub Issue: [#85](https://github.com/postmelee/hyper-waterfall/issues/85)
구현계획서: [`task_m050_85_impl.md`](../plans/task_m050_85_impl.md)
Stage: 2

## 단계 목적

Stage 1에서 확정한 영문 `README.md`를 구조와 의미의 진실 원천으로 삼아 한국어 `README.ko.md`를 같은 프로젝트 기억 중심 포지셔닝으로 현지화한다. 영문에서 조정한 핵심 맥락 복원 표현과 권장 세션 모델의 강도를 유지하고 기존 한국어 명령·경로·절차를 보존한다.

## 산출물

| 파일 | 변경 요약 |
|---|---|
| `README.ko.md` | 742줄, 203줄 추가·147줄 삭제. 상단부터 Appendix까지 영문과 동일한 H2/H3 구조와 프로젝트 기억 중심 메시지로 동기화 |
| `mydocs/working/task_m050_85_stage2.md` | 한국어 현지화 범위, 검증 근거, 중국어 단계 인수인계 기준 기록 |

## 본문 변경 정도 / 본문 무손실 여부

- 기존 686줄 한국어 README를 742줄로 확장했다.
- 영문과 동일하게 상단 소개 뒤에 Quick Start를 두고, `왜 Hyper-Waterfall인가`를 자세히 알아보기 이후로 이동했다.
- `언제 쓰면 좋은가`, 기존 방식 비교, 즉시 효과, 강점, 작업 흐름, 문서 구조, 핵심 원칙, 역할 분담, Vibe Coding 비교, 방법론 하네스, 설계 원칙, 프롬프트 가이드 정합성을 영문 최종안과 같은 의미로 갱신했다.
- `human governance`는 사람이 결정권을 갖는 구조, `context distillation`은 작업 맥락 증류, `persistent project memory`는 지속되는 프로젝트 기억, `resumable work`는 재개 가능한 작업으로 현지화했다.
- `reconstruct`에 해당하는 표현은 모든 맥락의 완전 복원이 아니라 핵심 맥락 복원과 문서화된 기준선으로 제한했다.
- `1 Issue = 1 Task = 1 Branch = 1 Session`은 권장 모델로 명시했다.
- 근거가 약한 `100배 빠른 속도`, `AI가 없던 시대에는 불가능했던 방법론`과 대표 위치의 `AI 페어 프로그래밍` 표현을 제거했다.
- 기존 한국어 locale 명령, Homebrew 명령, 7개 핵심 SKILL 이름은 Stage 시작 전 `README.ko.md`와 자동 대조해 동일함을 확인했다.

## 검증 결과

실행 명령:

```bash
git diff -- README.ko.md
rg -n "세션은 끝나도|프로젝트 기억|작업 맥락 증류|사람의 결정권|재개 가능한" README.ko.md
rg -n "npx hyper-waterfall@0.3.0|brew install postmelee/tap/hyper-waterfall|task-register|task-start|task-stage-report|task-final-report|pr-merge-cleanup|external-pr-review" README.ko.md
ruby -e 's=File.read(ARGV[0]); s.scan(/\[[^\]]*\]\(([^)]+)\)/).flatten.each{|u| next if u =~ %r{\A(?:https?://|mailto:|#)}; p=u.sub(/#.*/, ""); abort("missing: #{u}") unless File.exist?(p)}' README.ko.md
ruby -e 's=File.read(ARGV[0]); abort("unbalanced fences") unless s.lines.count{|l| l.start_with?("```")}.even?' README.ko.md
git diff --check
```

결과:

- OK — 한국어 README 전체 diff를 검토했다.
- OK — 대표 슬로건, 프로젝트 기억, 작업 맥락 증류, 사람의 결정권, 재개 가능성 표현을 확인했다.
- OK — `npx hyper-waterfall@0.3.0`, Homebrew 설치 명령과 7개 핵심 SKILL 이름을 확인했다.
- OK — 모든 로컬 상대 링크의 대상 파일이 존재한다.
- OK — Markdown 코드 fence 개수가 짝수다.
- OK — `git diff --check`가 경고 없이 통과했다.

구조·보존 추가 검증:

```bash
ruby -e 'a=File.readlines("README.md").grep(/^(?:##|###) /).map{|l| l.start_with?("### ") ? 3 : 2}; b=File.readlines("README.ko.md").grep(/^(?:##|###) /).map{|l| l.start_with?("### ") ? 3 : 2}; abort("heading structure mismatch #{a} != #{b}") unless a==b; puts "heading structure parity: #{a.length} sections"'
ruby -e 'require "open3"; base,_=Open3.capture2("git","show","HEAD:README.ko.md"); cur=File.read("README.ko.md"); pats=[/npx hyper-waterfall@[^\n]+/,/brew install postmelee\/tap\/hyper-waterfall/,/hyper-waterfall (?:init|doctor|--version)[^\n]*/,/`(?:task-register|task-start|task-stage-report|task-final-report|pr-merge-cleanup|external-pr-review|todo)`/]; pats.each{|p| b=base.scan(p).sort; c=cur.scan(p).sort; abort("mismatch #{p}: #{b} != #{c}") unless b==c}; puts "operational facts preserved: #{pats.length} pattern groups"'
rg -n "AI 페어 프로그래밍|AI 페어 프로그래머|100배 빠른|AI가 없던 시대에는 불가능했던|AI의 작업 기억을 주기적으로 외부화|지식이 머릿속이 아니라 저장소에 외부화" README.ko.md
```

- 첫 heading 대응 명령은 `/^#{2,3} /` 안의 `#{}`가 Ruby 문자열 보간으로 해석되어 문법 오류가 발생했다. 같은 검사를 `^(?:##|###)` 정규식으로 즉시 재실행했다.
- OK — 수정한 명령으로 영문·한국어 H2/H3 깊이 배열 50개가 정확히 일치했다.
- OK — 네 패턴 그룹에서 Stage 시작 전 한국어와 최종 한국어의 명령·SKILL 표기가 일치했다.
- OK — 제거 대상 검색은 빈 출력과 종료 코드 1로 여섯 표현이 남지 않았음을 확인했다.

## 잔여 위험

- 한국어는 영문과 구조·의미를 맞췄지만 문장 단위 직역이 아니므로 최종 통합 검증에서 세 언어 핵심 용어의 위치와 강도를 다시 확인해야 한다.
- 내부 목차 anchor는 GitHub의 Unicode heading slug 규칙을 전제로 한다. 상대 파일 링크는 검증됐으며, 목차 anchor는 Stage 3 통합 검증에서 heading과 별도로 대응 확인한다.
- 외부 링크의 실시간 접근성은 이번 로컬 검증 범위에 포함하지 않았다.

## 다음 단계 영향

- Stage 3은 영문을 의미·구조의 진실 원천으로, 한국어를 동아시아 언어 현지화의 보조 기준으로 사용한다.
- 중국어 간체에서도 완전한 복원을 보장하지 않고 핵심 맥락 복원과 문서화된 기준선을 표현한다.
- 영문·한국어의 H2/H3 깊이 배열 50개를 중국어에서도 동일하게 유지한다.
- Stage 3 통합 검증에서 세 README의 링크, code fence, CLI 명령, version, SKILL 이름, 핵심 용어와 전체 테스트를 확인한다.

## 승인 요청

- Stage 2 한국어 README와 검증 결과를 승인하면 Stage 3 중국어 README 동기화 및 통합 검증으로 진행한다.
