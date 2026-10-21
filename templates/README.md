# templates/ — 작성 템플릿

| 파일 | 용도 | 복사 위치 |
|---|---|---|
| character.master.md | 플랫폼 공통 마스터 캐릭터 카드(frontmatter + 컨셉·노출 텍스트·프롬프트·예시 대화·페르소나 가이드) | characters/<slug>/character.md |
| lorebook.md | 로어북 엔트리 표 + 단축어 | characters/<slug>/lorebook.md |
| first-message.md | 시작 장면(상황·첫 대사·확장 프롤로그·추천 답변·상태창·비밀) | characters/<slug>/scenes/NN-*.md |
| image-brief.md | 캐릭터 시트·에셋 목록·키워드 매핑·정책 체크 | characters/<slug>/image-brief.md |
| platform-mapping.md | 마스터 필드 → 플랫폼 입력란·글자 제한·문법 변환·잘라내기 순서 | 제출 시 참조 (exports/ 생성 규칙) |

분량 상한은 가장 엄격한 플랫폼 기준(제타 프롬프트 2,400자, 베이비챗 첫 대사 500자·키워드 5×20자, 크랙 이름 30자·로어북 400자). 상세 근거: research/02 §7, research/09, research/10.
