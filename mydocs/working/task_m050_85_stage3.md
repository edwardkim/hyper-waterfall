# 프로젝트 기억 중심 README 소개 개편 및 다국어 동기화 Stage 3 완료보고서

GitHub Issue: [#85](https://github.com/postmelee/hyper-waterfall/issues/85)
구현계획서: [`task_m050_85_impl.md`](../plans/task_m050_85_impl.md)
Stage: 3

## 단계 목적

Stage 1 영문 README의 구조와 의미를 중국어 간체로 현지화하고, Stage 2 한국어를 포함한 세 언어 README의 구조·링크·명령·버전·SKILL·핵심 메시지를 통합 검증한다. 모든 언어 README가 같은 프로젝트 기억 중심 포지셔닝을 제공하는지 현재 파일과 테스트 결과로 확인한다.

## 산출물

| 파일 | 변경 요약 |
|---|---|
| `README.zh-CN.md` | 749줄, 187줄 추가·143줄 삭제. 상단부터 Appendix까지 영문과 동일한 50개 H2/H3 구조와 프로젝트 기억 중심 메시지로 동기화 |
| `README.ko.md` | 통합 anchor 검사에서 발견한 하네스 섹션 점프 링크 1곳을 현재 제목과 일치하도록 보정 |
| `mydocs/working/task_m050_85_stage3.md` | 중국어 현지화, 세 언어 통합 검증, 잔여 위험 기록 |

## 본문 변경 정도 / 본문 무손실 여부

- 기존 705줄 중국어 README를 749줄로 확장했다.
- 영문·한국어와 같은 순서로 상단 소개, Quick Start, Why, 적합성, 비교, 즉시 효과, 강점, 작업 흐름, 문서 구조, 핵심 원칙, 역할 분담, 방법론 하네스, 설계 원칙, 프롬프트 정합성을 배치했다.
- `context distillation`은 `上下文提炼`, `persistent project memory`는 `持久项目记忆`, `human governance`는 `人类治理`/`由人治理`, `resumable work`는 `可恢复工作`로 현지화했다.
- 완전한 맥락 재현을 보장하지 않고 `恢复关键上下文`과 `文档化基线`으로 표현했다.
- `1 Issue = 1 Task = 1 Branch = 1 Session`은 `推荐模型`로 명시했다.
- 근거가 약한 `100 倍速度`, `AI 出现之前无法成立`, 대표 위치의 `AI 结对编程`/`AI 结对程序员` 표현을 제거했다.
- 기존 중국어 locale 명령, Homebrew 명령, 7개 핵심 SKILL 이름은 Stage 시작 전 본문과 자동 대조해 보존했다.
- 통합 내부 anchor 검사에서 Stage 2가 변경한 한국어 하네스 H2에 연결되는 본문 점프 링크 한 곳이 이전 anchor를 유지한 것을 발견해 현재 제목에 맞췄다.

## 검증 결과

구현계획서 고정 명령:

```bash
git diff -- README.zh-CN.md
rg -n "持久项目记忆|上下文提炼|人类治理|可恢复" README.zh-CN.md
rg -n "npx hyper-waterfall@0.3.0|brew install postmelee/tap/hyper-waterfall|task-register|task-start|task-stage-report|task-final-report|pr-merge-cleanup|external-pr-review" README.zh-CN.md
ruby -e 'ARGV.each{|f| s=File.read(f); s.scan(/\[[^\]]*\]\(([^)]+)\)/).flatten.each{|u| next if u =~ %r{\A(?:https?://|mailto:|#)}; p=u.sub(/#.*/, ""); abort("#{f}: missing #{u}") unless File.exist?(p)}}' README.md README.ko.md README.zh-CN.md
ruby -e 'ARGV.each{|f| s=File.read(f); abort("#{f}: unbalanced fences") unless s.lines.count{|l| l.start_with?("```")}.even?}' README.md README.ko.md README.zh-CN.md
rg -n "npx hyper-waterfall@0.3.0|brew install postmelee/tap/hyper-waterfall" README.md README.ko.md README.zh-CN.md
rg -n "task-register|task-start|task-stage-report|task-final-report|pr-merge-cleanup|external-pr-review|todo" README.md README.ko.md README.zh-CN.md
npm test
git diff --check
git status --short
```

결과:

- OK — 중국어 README 전체 diff를 검토했다.
- OK — `持久项目记忆`, `上下文提炼`, `人类治理`, `可恢复`가 의도한 핵심 섹션에 존재한다.
- OK — 중국어 README에서 locale CLI, Homebrew 명령, 7개 핵심 SKILL 이름을 확인했다.
- OK — 세 README의 모든 로컬 상대 링크 대상 파일이 존재한다.
- OK — 세 README의 Markdown code fence 개수가 모두 짝수다.
- OK — 세 README에 `npx hyper-waterfall@0.3.0`과 Homebrew 설치 명령이 존재한다.
- OK — 세 README에 7개 핵심 SKILL 이름이 모두 존재한다.
- OK — `npm test` 12개 테스트가 모두 통과했다.
- OK — `git diff --check`가 경고 없이 통과했다.
- `git status --short`는 보고서 작성 전 예상 산출물인 `README.zh-CN.md` 수정 상태를 표시했다.

구조·anchor·최종 상태 추가 검증:

```bash
ruby -e 'files=%w[README.md README.ko.md README.zh-CN.md]; a=File.readlines(files[0]).grep(/^(?:##|###) /).map{|l| l.start_with?("### ") ? 3 : 2}; files[1..].each{|f| b=File.readlines(f).grep(/^(?:##|###) /).map{|l| l.start_with?("### ") ? 3 : 2}; abort("#{f}: heading structure mismatch") unless a==b}; puts "heading structure parity: #{a.length} sections across #{files.length} files"'
ruby -e 'ARGV.each{|f| slugs={}; counts=Hash.new(0); File.readlines(f).each{|line| next unless line =~ /^#+\s+(.+)$/; t=$1.strip.gsub(/<[^>]+>/, "").gsub(/`/, "").gsub(/\[([^\]]+)\]\([^)]+\)/, "\\1"); base=t.downcase.gsub(/[^\p{L}\p{N}\s_-]/u, "").gsub(" ", "-"); n=counts[base]; counts[base]+=1; slug=n.zero? ? base : "#{base}-#{n}"; slugs[slug]=true}; File.read(f).scan(/\[[^\]]*\]\(#([^)]+)\)/).flatten.each{|a| abort("#{f}: missing anchor ##{a}") unless slugs[a]}; puts "#{f}: internal anchors ok"}' README.md README.ko.md README.zh-CN.md
ruby -e 'skills=%w[task-register task-start task-stage-report task-final-report pr-merge-cleanup external-pr-review todo]; ARGV.each{|f| s=File.read(f); missing=skills.reject{|x| s.include?("`#{x}`")}; abort("#{f}: missing #{missing.join(",")}") unless missing.empty?; puts "#{f}: 7 core SKILL names present"}' README.md README.ko.md README.zh-CN.md
rg -n "100x faster|100배 빠른|100 倍速度|impossible before AI|AI가 없던 시대에는 불가능했던|AI 出现之前无法成立|AI Pair Programmer|AI 페어 프로그래머|AI 结对程序员" README.md README.ko.md README.zh-CN.md
```

- OK — 세 README의 H2/H3 깊이 배열 50개가 정확히 일치한다.
- 내부 anchor 첫 검사 명령은 `/^#{1,6}/`의 `#{}`가 Ruby 보간으로 해석되어 문법 오류가 났다. 보간 없는 `/^#+/` 정규식으로 재실행했다.
- 두 번째 anchor 검사에서 한국어 점프 링크 1곳의 이전 anchor가 발견됐다. 링크를 현재 H2에 맞춘 뒤 재실행해 세 README 모두 통과했다.
- OK — 세 README에 7개 핵심 SKILL 이름이 모두 존재한다.
- OK — 제거 대상 표현 검색은 빈 출력과 종료 코드 1로 잔존하지 않음을 확인했다.
- 최종 링크·fence·명령·SKILL·`npm test`·`git diff --check` 검증은 한국어 anchor 보정 후 다시 실행해 모두 통과했다.

## 잔여 위험

- 세 언어는 의미와 구조를 맞춘 현지화이며 문장 단위 직역은 아니다. 향후 한 언어 README의 구조나 핵심 포지셔닝을 변경할 때 나머지 두 언어도 함께 갱신해야 한다.
- 내부 anchor 검사는 현재 README heading을 GitHub 방식에 가깝게 slug화한 로컬 검사다. 실제 GitHub 렌더링 화면의 클릭 검증은 PR review에서 한 번 더 확인할 수 있다.
- 외부 OpenAI·Anthropic·GitHub 링크의 실시간 접근성은 로컬 검증 범위에 포함하지 않았다.

## 다음 단계 영향

- 구현계획서의 세 Stage가 모두 완료됐다.
- 최종 보고서에서는 세 README의 포지셔닝, 50개 heading 구조, 링크, 명령, 7개 SKILL, 12개 테스트 결과를 수용 기준별로 종합한다.
- 최종 보고와 PR 게시 전 `README.ko.md`의 anchor 보정도 Stage 3 커밋에 함께 포함한다.

## 승인 요청

- Stage 3 중국어 README, 한국어 anchor 보정, 통합 검증 결과를 승인하면 최종 결과보고서와 PR 게시 단계로 진행한다.
