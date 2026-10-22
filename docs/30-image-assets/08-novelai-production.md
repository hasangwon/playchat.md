# 08. NovelAI로 캐릭터챗 에셋 뽑는 절차 (실무 SOP)

> 목적: 이 프로젝트의 고정 도구인 NovelAI(NAI)로 **그림체 확정 → 캐릭터 기본컷 → 상황코드별 감정 세트 → 후처리 → 외장 업로드**까지 같은 방식으로 반복 생산한다.
> 근거: research/15(공식 문서 + 디시 Ai그림 여성향 갤 개념글 + 아카 aiart·characterai 추천글, 2026-10-22). 코드표 규칙은 07-external-hosting.md.
> 표기: [공식] / [커뮤니티] / [추정].

## 0. 먼저 알아둘 사실 (결정에 영향을 주는 것만)
| 사실 | 의미 | 근거 |
|---|---|---|
| **정밀 참조(Precise Reference)는 V4.5에서만 됨**, 참조 1장당 +5 Anlas, 여러 캐릭터 참조는 섞임 | V5는 "레퍼런스로 같은 얼굴 고정"을 못 함. V4.5 참조는 Opus 무료 범위 밖 | [공식] precisereference, [커뮤니티] characterai 186483553 |
| V5 Full = 품질·투명 배경·고른 화풍 혼합, V5 Curated = 전체연령 성향 | 에셋은 **Full**로. Curated로 뽑으면 구도·성인 컷이 안 나옴 | [공식] models, [커뮤니티] aipicture 1246, characterai 186454942 |
| V5는 Opus도 **주간 할당량**(100% ≈ 28스텝 1,600장), 부스트 +100% $5.99(최대 400%, 1년 소멸) | 작품당 생성 장수 예산을 잡아야 함 | [공식 저널] V5 usage boost, [커뮤니티] aiart 185863875 |
| Opus 무료 조건(V4.5): 1장씩, 베이스 이미지 없음, Normal 크기 이하, Steps ≤28 | 설정을 이 범위에 맞춘다 | [공식] subscription |
| NAI PNG는 픽셀 LSB에 생성 정보가 숨어 있어 메타데이터만 지워도 복원됨 | **webp(손실) 변환**으로 프롬프트 유출 차단 | [커뮤니티] genit 10811 |
| 출력 LLM이 에셋 이름을 `smile`↔`smiling`처럼 바꿔 부름 | 이름 대신 **숫자 상황코드**로 출력시키는 07번 방식이 맞음 | [커뮤니티] characterai 160553593 |
| 유저는 일관성을 생각보다 신경 안 씀. **구도·위치를 고정하고 얼굴·손만 바꾸면** 통일돼 보임. 핵심 디자인 요소 1개(앞머리 등)를 집요하게 맞추면 충분 | 감정 세트는 "같은 프레이밍, 표정 블록만 교체"로 만든다 | [커뮤니티] characterai 159738165 |

## 1. 고정 설정 (모든 작품 공통 기본값)
| 항목 | 값 | 이유 |
|---|---|---|
| 모델 | **V5 Full** (기본) / V4.5 Full(정밀 참조가 꼭 필요할 때만) | §0 |
| Effort | High (할당량 아낄 땐 Medium: 14스텝 고정·커스텀 UC 불가 → 음수 가중치로 대체) | [공식] effort |
| 해상도 | 세로 832×1216 (Normal Portrait) — 감정 세트·상황 컷 / 프로필은 플랫폼 비율로 별도 | Opus 무료 범위, 2:3에 가까움 |
| Steps | 28 | 무료 상한, 커뮤니티 기본값 |
| Prompt Guidance | 5 (만화체) ~ 6 (반실사·얼굴 안정) | [커뮤니티] aipicture 1246 |
| Variety+ | 끔 | 프롬프트 무시 방지 |
| Sampler | Euler Ancestral | V5 기준점 [커뮤니티] aiart 181003788 |
| Add Quality Tags | 끔 (작가 태그로 화풍 잡을 때). 필요한 품질 태그는 직접 씀 | 화풍 다양성 저하 [커뮤니티] 1246 |
| UC 프리셋 | Heavy + 아래 §3 기본 UC | |

## 2. 프롬프트 구조 (V5)
```
[베이스 프롬프트]
{작가 태그 블록 — 그림체 카드에서 복사, 작가 사이는 | 또는 ,}, {화풍 태그}, 
1girl(또는 1boy), solo, adult, upper body, straight on, looking at viewer,
{배경: simple background, white background | transparent background}, 
{표정 블록 — §4 상황코드표에서 교체},
high complexity, year 2025, very aesthetic, masterpiece, -3::simple illustration::

[캐릭터 프롬프트 1] (캐릭터 시트에서 복사, 작품 내내 고정)
girl, {나이 인상: mature female / adult}, {머리: 색·길이·스타일·앞머리}, {눈: 색·눈매(tsurime/tareme/jitome)}, 
{피부}, {체형}, {복장: 부위별 + 색 (상의·하의·신발·액세서리)}, {핵심 디자인 앵커 1개}
```
- 태그는 개념(인원·의상·시점·정형 포즈), 자연어는 관계(무엇을 어느 손에 드는지, 광원 방향)에만 쓴다. [커뮤니티] aiart 181003788
- 복장은 부위별·색까지 구체적으로 써야 장마다 덜 바뀐다. [공식] tutorial-charactercreation
- `portrait`는 화풍에 따라 얼굴이 실사화되는 일이 있어 기본은 `upper body`. [커뮤니티] aipicture 2049
- 작가 태그 가중치는 V5에서 1.5를 넘기지 않고 0.1~0.2씩 조정. 태그가 숫자로 끝나면 `2::artist:abc123 ::`처럼 공백. [커뮤니티] 2049, aichat 22
- 서로 충돌하는 조건(뒤돈 자세 + 복근, 두 손으로 컵 + 허리에 손)을 같이 쓰지 않는다.

## 3. 기본 UC (Undesired Content)
```
text, logo, watermark, signature, artist name, username, multiple views, reference, 
lowres, blurry, jpeg artifacts, worst quality, bad quality, displeasing, very displeasing,
bad anatomy, bad hands, extra digits, fewer digits, extra limbs, bad proportions, heterochromia,
yellow tint, minigirl, miniboy, character doll,
loli, shota, child, aged down, school uniform, serafuku
```
- 마지막 줄은 **미성년 신호 차단(CLAUDE.md 6장)** — 모든 작품에서 빼지 않는다. 캐릭터 프롬프트엔 `adult` / `mature female`·`mature male`을 넣는다.
- 반복되는 문제만 추가한다(긴 UC가 좋은 게 아님). 정말 없애야 하는 건 UC보다 프롬프트 안 음수 가중치(`-2::hat::`)가 세다. [공식] strengthening, [커뮤니티] 1246

## 4. 상황코드 → 표정 블록 (07번 코드표와 1:1, 전 캐릭터 공통)
감정 프리셋(characterai 139347728)을 NAI 문법으로 바꾼 것. **표정 블록만 갈아 끼우고 나머지는 한 글자도 안 바꾼다.**
| 코드 | 이름 | 표정 블록 |
|---|---|---|
| 0 | 기본 | `closed mouth, neutral expression, arms at sides` |
| 1 | 미소 | `smile, closed mouth, 1.1::happy::` |
| 2 | 웃음 | `1.1::laughing, smile, closed eyes, open mouth::, hand over own mouth` |
| 3 | 슬픔 | `parted lips, 1.1::raised eyebrows, tearing up, hand on own chest::, 1.15::sad, frown::` |
| 4 | 오열 | `looking down, 1.5::closed eyes::, 1.4::sad::, crying, tears, 1.2::wiping tears, open mouth, wavy mouth::` |
| 5 | 삐짐 | `1.1::pout, crossed arms::, looking to the side` |
| 6 | 화남 | `1.1::angry::, anger vein, open mouth, 1.1::hands on own hips::, leaning forward` |
| 7 | 경멸 | `1.2::disgust, expressionless, half-closed eyes, frown::, 1.3::shaded face::` |
| 8 | 설렘/부끄 | `1.1::embarrassed, blush, shy::, averting eyes, 1.2::hand in own hair, playing with own hair::` |
| 9 | 놀람/당황 | `1.1::surprised, wide-eyed, open mouth::, 1.1::hand to own mouth::, sweat` |
| 10~ | 작품 전용 | 예: 포옹·전투·부상·잠듦. 같은 방식으로 블록 1줄씩 정의해 `image-brief.md`에 기록 |
| 20~ | 언세이프 | 별도 파생본. 업로드 전 불투명 가림(06-policy-checklist) |
- 감정 수는 캐릭터당 **10~16종이 현실선**. 등장인물 많은 시뮬봇은 36종도 버겁다는 경험담. 의상 바리에이션은 곱셈으로 늘어나니(의상 15 × 감정 24 = 360장) 의상은 최소화. [커뮤니티] 162231996, 175868853

## 5. 생산 순서
1. **그림체 카드 확정** — 공유 그깎(디시 aipicture 프롬 탭, 아카 aiart "그림체 공유", V5 작태 통계 2526)에서 후보를 고르고, 고정 캐릭터 프롬프트로 후보마다 4장씩 뽑아 비교 → 사용자가 고른 1개를 `assets/style-card.md`에 프롬프트 전문·시드와 함께 저장. 화풍을 꽉 고정할수록 디테일이 떨어지는 트레이드오프가 있다. [커뮤니티] 1246
2. **캐릭터 시트 → 0번 기본컷** — §2 캐릭터 프롬프트 작성 → 코드 0으로 뽑아 마음에 드는 1장을 고르고 **시드 고정**. 이 1장이 마스터 레퍼런스. 필요하면 `reference sheet, multiple views, turnaround, no text`로 시트도 1장.
3. **감정 세트** — 시드·프롬프트 고정, §4 표정 블록만 교체해 코드별 4~8장 생성 → 0번과 나란히 놓고 핵심 앵커(앞머리·눈색·복장 포인트)가 맞는 것만 채택.
   - 일관성이 계속 깨지면 순서대로 시도: ① 0번 이미지를 인페인트로 얼굴(+손)만 마스크하고 표정 블록으로 재생성 → 위치·몸이 그대로라 가장 통일돼 보임 ② 디렉터 툴 Emotion(정면·중립·단독 컷에서 잘 됨) ③ V4.5 Full + 정밀 참조(Character, Strength 0.9 / Fidelity 0.9) + `2::The character has the same distinctive physical features hairstyle and accessories as in the reference image::` (장당 +5 Anlas). [공식] directortools·precisereference, [커뮤니티] aiart 182356864
4. **손·얼굴 찐빠** — 전체를 다시 뽑지 말고 Focused Inpainting으로 한 부위씩. [공식] inpaint
5. **프로필·썸네일** — 세이프티 기준으로 별도 생성(속옷·비침·부위 강조 금지). 홍보·대표 컷은 공들여 인페인트까지. 
6. **후처리** — (필요 시) Remove Background → webp 변환(장당 1MB 이하, LSB 메타데이터 제거 겸함) → 파일명 `{캐릭터ID}/{상황코드}.webp`.
7. **업로드·코드표** — 07-external-hosting.md 3장 절차.

## 6. 장수·비용 예산
| 규모 | 채택 장수 | 생성 시도(채택×4~8) | V5 할당량 |
|---|---|---|---|
| 1:1 캐릭터 1명, 코드 0~9 + 전용 4 | 14 | 약 60~110 | 100%의 4~7% |
| 주연 5명 × 14 | 70 | 약 280~560 | 100%의 18~35% |
| 군상극 22명 × 17 (크랙 1위작 규모) | 374 | 약 1,500~3,000 | 100~190% → 1~2주 또는 부스트 1~2회($5.99/회) |
- 그림체 깎기에도 할당량이 크게 든다(커뮤니티: 한 번에 30%p 소모 사례). 그림체 탐색은 Effort Medium으로. [커뮤니티] characterai 186452242

## 7. 도구
- **NAI 웹(novelai.net/image)**: 기본. Claude가 사용자 로그인 상태의 브라우저에서 조작 가능(프롬프트 입력·생성·다운로드).
- 대량 생성 관리 앱(캐릭터 프리셋 × 감정 씬 일괄): SDStudio(개발 중단 예정), NAIS3, 87-studio(github.com/snuff8729/87-studio, 웹·모바일). 모두 사용자 PC 설치형이고 NAI 계정 토큰이 필요 → **설치·토큰 입력은 사용자가 결정**. 웹으로 충분하면 쓰지 않는다.
- 보조: Danbooru(태그·작가 확인, 게시물 50개 이상 작가 태그 권장), NovelAI Inspect(공유 이미지의 프롬프트 확인).

## 8. 이 문서를 쓰는 사람의 역할 분담
| 단계 | Claude | 사용자 |
|---|---|---|
| 캐릭터 외형 태그화 | 사용자가 준 설정을 §2 형식으로 변환 | 캐릭터 외형 결정 |
| 그림체 | 후보 수집·비교 생성 | 1개 선택 |
| 생성·선별·인페인트·후처리 | NAI 웹에서 수행, 선별 기준은 §5-3 | 최종 확인 |
| 구독·결제·로그인·할당량 부스트 | 하지 않음 | 직접 |
