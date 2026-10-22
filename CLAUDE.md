# make-playchat — AI 캐릭터챗(플레이챗) 제작·제출 프로젝트

> Claude 진입점 문서. 이 파일만 읽으면 프로젝트의 목적·구조·규칙·작업 순서를 알 수 있어야 한다.
> 세부 내용은 각 폴더의 `README.md` → 개별 문서 순으로 내려가며 읽는다 (progressive disclosure).

## 1. 프로젝트 한 줄 정의
**AI 캐릭터챗을 "만드는 프롬프트와 시스템"을 설계·개발하는 프로젝트.** 캐릭터/작품 자체를 Claude가 임의로 만드는 것이 아니다.
- 사용자가 컨셉·캐릭터·이미지 출처를 정하면, 이 시스템(문서·템플릿·스킬)이 그것을 플랫폼 규격에 맞는 작품으로 변환하고, 로그인된 플랫폼 폼에 입력·제출한다.
- 플랫폼·앱을 새로 개발하지 않는다. 산출물은 **지식 베이스(docs) + 템플릿 + 스킬(절차)**.
- Claude는 **컨셉·캐릭터·이미지 출처를 스스로 정하지 않는다.** 입력이 없으면 묻는다. `characters/_example/`은 형식 예시일 뿐이다.
- 목표는 수익(정산)과 승인(노출/오리지널 선정)을 내는 작품을 반복 생산할 수 있는 시스템.

## 2. 폴더 구조 (정형화 패턴)
```
make-playchat/
├── CLAUDE.md                 # (이 파일) 진입점. 규칙·구조·워크플로우
├── README.md                 # 사람용 요약
├── TASKS.md                  # 해야 할 일 / 진행 상태 / 사용자 확인 필요 항목
├── docs/                     # 정제된 지식 베이스 (research를 실무용으로 재구성)
│   ├── 00-overview.md        #   목적·범위·핵심 결론·워크플로우·용어 대응표
│   ├── 10-platforms/         #   README(비교표·추천·전략) crack / caveduck / babechat-tookit / zeta / others
│   ├── 20-character-design/  #   README(파이프라인·분량 예산) 01-concept … 08-testing-qa
│   ├── 30-image-assets/      #   README 01-specs 02-tools 03-consistency 04-webtoon-intro 05-prompt-recipes 06-policy-checklist
│   └── 40-growth/            #   README 01-trends 02-exposure 03-comments-ops 04-monetization 05-promotion 06-risks 07-case-studies
├── templates/                # character.master / lorebook / first-message / image-brief / platform-mapping
├── characters/               # 실제 제작 작품. 작품 1개 = 폴더 1개 (규칙: characters/README.md, 예시: _example/)
├── research/                 # 조사 원본 (날짜·출처 포함, README가 색인). docs의 근거. 수정하지 않고 추가만
└── .claude/skills/           # new-character / submit-crack / submit-caveduck / submit-babechat
```
파일명 규칙: `NN-주제.md` (숫자 접두어 = 읽는 순서), 폴더마다 `README.md`가 색인. 날짜가 있는 스냅샷은 `주제-YYYY-MM-DD.md`.

## 3. 읽기 순서 (작업 유형별)
| 하려는 일 | 먼저 읽을 것 |
|---|---|
| 프로젝트 파악 | `docs/00-overview.md` |
| 어느 플랫폼에 올릴지 결정 | `docs/10-platforms/README.md` |
| (사용자가 컨셉·캐릭터를 준 뒤) 작품 변환·작성 | `.claude/skills/new-character/SKILL.md` → `docs/20-character-design/README.md` → `templates/character.master.md` (예시 `characters/_example/`) |
| 이미지 에셋 제작 | `docs/30-image-assets/README.md` → `templates/image-brief.md` |
| 플랫폼 폼에 입력·제출 | `docs/10-platforms/<플랫폼>.md` → `templates/platform-mapping.md` → `.claude/skills/submit-<플랫폼>/SKILL.md` |
| 출시 후 운영(노출·댓글·수익) | `docs/40-growth/README.md` |
| 근거 확인 | `research/README.md` → 해당 번호 파일 |

## 4. 작업 워크플로우 (표준 파이프라인)
1. **플랫폼·장르 결정** — `docs/10-platforms/README.md` 4장(전략), `docs/40-growth/01-trends.md`.
2. **기획** — `templates/character.master.md`를 복사해 `characters/<slug>/character.md` 작성.
3. **본문** — 배경/세계관 → 캐릭터 프롬프트 → 로어북(`lorebook.md`) → 시작 장면(`scenes/`, 최대 3개) → 예시 대화. 가이드 `docs/20-character-design`.
4. **이미지** — `image-brief.md` 작성 후 `assets/`에 프로필·배경·표정·상황·인트로 컷. 가이드 `docs/30-image-assets`.
5. **자체 QA** — `docs/20-character-design/08-testing-qa.md` 체크리스트 + 플랫폼 테스트 채팅.
6. **제출** — `templates/platform-mapping.md`로 `exports/<플랫폼>.md` 생성 → 사용자가 로그인한 브라우저에서 폼 입력. **약관 동의·최종 등록/공개·독점 토글은 사용자 확인 후.**
7. **운영** — `status.md`에 제출 상태·반응·수정 이력. 출시 72시간 홍보, 댓글 대응(`docs/40-growth`).

## 5. 작성 규칙
- 모든 문서는 **한국어**. 플랫폼 고유 용어는 원문 그대로(예: 크랙 "스토리/캐릭터·키워드북", 케이브덕 "에피소드·비밀·위젯", 베이비챗 "유저노트").
- 사실과 의견을 분리: `[공식]` 공식 문서 / `[회사 발표]` / `[커뮤니티]` 경험담 / `[추정]` 해석 / **미확인**. 숫자는 출처·날짜와 함께.
- 날짜는 절대 날짜(YYYY-MM-DD). "최근", "다음 달" 금지.
- `research/`는 근거 보관소. 요약·결론은 `docs/`에만. docs를 고치면 근거 research 파일 번호를 함께 적는다. 문서 간 충돌 시 공식 문서 정리본(research/09·10) 우선.
- 작품 본문은 플랫폼 공통 **마스터 카드 1개**로 쓰고 제출 시 변환한다(중복 집필 금지). `exports/`는 파생물이므로 직접 수정하지 않는다.

## 6. 안전·정책 가드레일 (모든 작품에 적용)
- 미성년자 설정·외형·배경 금지. **등장인물은 전원 성인**으로 설정하고 나이를 명시. 교복·교실·학교·학원·아이돌 연습생 배경은 설정상 성인이어도 플랫폼이 미성년으로 간주하므로 쓰지 않는다.
- 혈연 근친 금지(케이브덕·베이비챗 명시). 비혈연 관계는 비혈연임을 명시.
- 실존 인물·실존 아이돌·타 작품 캐릭터(2차 창작) 금지. 플랫폼 공식 콜라보만 예외.
- 이미지: 실사풍 실존 인물 유사 금지, 타인 저작 이미지 금지, 프로필은 가장 보수적 기준(속옷·비침·혈흔·부위 강조 금지). 언세이프 앨범은 불투명 유색 가림(모자이크·블러 불가).
- 세이프티 버전을 본진으로, 언세이프는 파생본으로 분리(같은 폴더의 `variants.md`에 차이점만 기록, 제출 시 별도 변환). 크랙은 등록 후 등급 변경 불가, 베이비챗은 성인→전체 되돌리기 불가.
- 독점 조건(크랙 온리 18개월 / 크랙 오리지널 영구 / 케이브덕 오리지널 3개월 / B·T Only 100일)이 걸린 작품은 다른 플랫폼에 올리지 않는다. 작품당 독점 1곳. `status.md`에 기록.
- 브라우저 자동화 시: 로그인·본인인증·결제·약관/정책 **동의 버튼, 최종 등록·공개 버튼, 독점 토글, 삭제**는 사용자 확인 후에만 클릭.

## 7. 현재 상태 (2026-10-21)
- 조사(research 01~10)와 문서화(docs 00~40, templates, characters/_example, skills) 1차 완료. 상세와 사용자 확인 필요 항목은 `TASKS.md`.
- 핵심 결론: 1순위 크랙(현금화·오리지널·온리, 단 크리에이터 미션 전 정산 없음) → 2순위 케이브덕(자격 조건 없이 즉시 적립, 월 출금). 베이비챗/투킷은 비독점 보조, 제타는 노출용.
- 브라우저 로그인 상태(2026-10-21 갱신): 크랙·케이브덕·제타·베이비챗 모두 로그인됨.
