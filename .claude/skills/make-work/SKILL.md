---
name: make-work
description: 작품 1개를 접수부터 제출까지 끝내는 전체 파이프라인 실행. "전체 진행해", "작품 만들어서 올려", "처음부터 끝까지" 요청 시 사용. intake → new-character → generate-assets → 호스팅/코드표 → QA → submit-<플랫폼> 순서로 하위 스킬을 호출하고, 사용자 결정이 필요한 것은 단계마다 멈추지 않고 질문 목록에 모아 한 번에 묻는다.
---

# 전체 파이프라인

## 원칙
- 사용자 입력은 `characters/<slug>/intake.md` 하나. 비어 있는 필수 칸(1장 컨셉·장르·타깃·등급·형태, 2장 인물)은 **지어내지 않고** 질문 목록에 넣는다. (선택) 칸은 docs 기본값으로 채우고 기록.
- 질문은 모아서 한 번에. 답을 기다리는 동안 그 답과 무관한 단계를 계속 진행한다.
- 서브에이전트를 쓰지 않는다(사용자 요청 시만). 브라우저는 JS 텍스트 추출·`find`·`read_page(interactive)` 위주, 스크린샷은 판정이 필요할 때만.
- 사용자 확인 필수: 로그인·결제·약관 동의·최종 등록/공개·독점 토글·삭제·댓글 작성·파일 다운로드 범위.

## 단계
| # | 단계 | 스킬/문서 | 산출물 | 막히는 조건 |
|---|---|---|---|---|
| 1 | 접수 | `templates/intake.md` 복사 | `intake.md` | 필수 칸 공란 → 질문 |
| 2 | 본문 | `new-character` | character.md·lorebook.md·scenes/·variants.md | intake 1·2장 |
| 3 | 이미지 브리프 | `templates/image-brief.md`, 08번 §2 | image-brief.md(프롬프트·계획표) | 인물 외형 |
| 4 | 그림체 | 09-style-candidates.md → generate-assets §3-1 | style-card.md | NAI 로그인, 사용자 선택 |
| 5 | 에셋 생성 | `generate-assets` | assets/{ID}/{코드}.webp | NAI 로그인 |
| 6 | 호스팅·코드표 | 07-external-hosting.md | 업로드된 URL, 프롬프트 이미지 규칙 블록, 고정댓글용 코드표 | 도메인·R2(사용자 계정) — 없으면 플랫폼 업로드 방식으로 전환 |
| 7 | QA | 08-testing-qa.md | status.md 체크 | — |
| 8 | 변환·입력 | `submit-crack` / `submit-caveduck` / `submit-babechat` | exports/<플랫폼>.md, 임시 저장된 폼 | 플랫폼 로그인 |
| 9 | 등록 | 사용자 확인 | 공개 URL | 사용자 승인 |
| 10 | 운영 | docs/40-growth | status.md | — |

## 보고 형식 (단계 묶음마다)
- 완료한 것 / 만든 파일 경로 / 질문 목록(번호, 각 1줄, 선택지 있으면 추천 표시) — 5~10줄.
