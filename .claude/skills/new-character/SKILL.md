---
name: new-character
description: 새 AI 캐릭터챗 작품을 기획부터 QA까지 만드는 절차. "새 캐릭터 만들어", "작품 기획해", "스토리 써줘" 요청 시 사용. 마스터 카드 → 로어북 → 시작 장면 → 예시 대화 → 이미지 브리프 → QA 순서로 characters/<slug>/ 에 파일을 만든다.
---

# 새 작품 만들기

## 0. 읽을 것 (순서대로, 처음 한 번)
1. `CLAUDE.md` 6장 가드레일
2. `docs/10-platforms/README.md` — 어느 플랫폼에 올릴지, 독점 여부
3. `docs/40-growth/01-trends.md` — 지금 먹히는 장르·제목 패턴
4. `docs/20-character-design/README.md` — 파이프라인과 분량 예산표

## 1. 컨셉 확정 (입력 = `characters/<slug>/intake.md`, 양식 `templates/intake.md`)
- 플랫폼(복수 가능, 독점이면 1개), 장르, 타깃(남성향/여성향/전체), 등급(세이프 본진 + 언세이프 파생 여부), 1:1 캐릭터인지 시뮬레이션/군상극(크랙 스토리형)인지.
- 사용자가 컨셉을 줬으면 그대로 따른다. **없으면 작성을 시작하지 않고 사용자에게 받는다.** Claude가 컨셉·캐릭터·이미지 출처를 임의로 정하지 않는다(사용자 정정 2026-10-22). 받을 것: 컨셉·장르, 등장인물(이름·나이·관계), 타깃, 등급, 플랫폼·독점 여부, 이미지 출처(NAI·로컬 SD·직접 제작 등)와 호스팅 여부.
- 가드레일 위반(미성년·실존 인물·타 IP·근친·학교 주배경)이면 이유를 한 줄로 말하고 대안 컨셉을 제시한다.

## 2. 파일 생성
```
characters/<slug>/
  character.md   ← templates/character.master.md 복사 후 작성
  lorebook.md    ← templates/lorebook.md
  scenes/01-*.md ← templates/first-message.md (1~3개)
  image-brief.md ← templates/image-brief.md
  status.md      ← characters/_example/status.md 형식
  assets/ exports/
```
`characters/_example/`이 완성 예시다. 분량은 `templates/platform-mapping.md`의 가장 엄격한 상한을 지킨다.

## 3. 작성 순서와 기준
1. **컨셉 §1** — 한 줄 피치는 "유저가 되는 상황" 1문장. 훅·차별점·참고 인기작(research/06·08)을 적는다.
2. **노출 텍스트 §2** — 한 줄 소개 30자(말투가 들리게), 긴 소개 500자(숫자로 구체성), 태그 5개.
3. **프롬프트 §3** — `docs/20-character-design/03-persona-prompt.md`. 말투는 형용사가 아니라 호칭·어미·실제 대사. 행동 규칙은 명령문 5~10개, "유저 대신 말하지 않는다" 포함. 상태창은 답변 맨 끝.
4. **로어북** — `docs/20-character-design/04-lorebook.md`. 상시 설정은 프롬프트에, 조건부만 로어북. 중요 순으로 정렬.
5. **시작 장면** — `docs/20-character-design/05-first-message.md`. 원하는 응답의 본보기. 유저 행동 금지. 열린 끝. 추천 답변 3개.
6. **예시 대화 3개** — 서로 다른 무드. 유저 입력은 짧게.
7. **이미지 브리프** — `docs/30-image-assets/08-novelai-production.md` §2 형식으로 캐릭터 프롬프트(intake 외형 그대로 태그화)·상황코드 계획을 쓴다. 생성은 `generate-assets` 스킬.
8. **QA** — `docs/20-character-design/08-testing-qa.md` 체크리스트를 `status.md`에 체크. 가능하면 플랫폼 테스트 채팅(베이비챗 10회, 크랙 미리보기, 케이브덕 프롬프트 와치)으로 새 채팅·이어지는 채팅·장기 턴을 본다.

## 4. 완료 보고
- 작품 폴더 경로, 플랫폼·등급·독점, 남은 확인 항목(이미지 생성 여부, 사용자 승인 필요 사항)을 5줄 이내로.
- 제출은 `submit-<플랫폼>` 스킬로 넘긴다. **공개 버튼은 사용자 확인 후.**
