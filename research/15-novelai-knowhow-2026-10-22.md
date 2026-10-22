# 15. NovelAI 이미지 생성 노하우 수집 (2026-10-22)

> 방법: NovelAI 공식 문서(docs.novelai.net) 직접 열람 + 디시 「Ai 그림 여성향」 미니갤 개념글(추천순 상위 정보글 전수) + 아카라이브 AI그림 채널(aiart)·캐릭터챗 채널(characterai) 추천순 가이드 열람. 브라우저(로그인 불필요) + WebFetch.
> 원칙: 원문 그대로 옮기지 않고 사실·수치·문법만 정리. 출처는 게시글 번호.

## A. 공식 문서 [공식]
### A1. 모델 (docs.novelai.net/en/image/models)
| 모델 | 특징 | 프롬프트 한도 |
|---|---|---|
| V5 Full | 2026-08-21 출시. V4.5의 약 2배 크기, 넓은 데이터셋. 자연어·다국어(일본어) 이해, 최대 22인, 투명 배경, 만화 컷 생성 | 약 1,471 토큰 |
| V5 Curated | 정제 데이터셋, 전체연령가 성향("Recommended for Streaming") | 약 703 토큰 |
| V4.5 Full / Curated | 다인물 1급 지원, T5 토크나이저(이모지·일본어 불가) | 베이스+캐릭터 합산 512 T5 토큰 |
- V5는 Opus 무료 생성에 **사용량 한도**가 있음. V4.5는 기존 Opus 무료 조건 그대로.
- Opus 무료 조건(subscription 문서): 1장씩, 베이스 이미지 없음, Normal 크기 이하, Steps 28 이하. 매월 10,000 Anlas.

### A2. Precise Reference(정밀 참조) (…/precisereference)
- **V4.5 모델에서만** 사용 가능(문서 기준, V5 미지원). Vibe Transfer와 동시 사용 불가.
- 유형: Character / Style / Character & Style(기본). 카드별 Strength·Fidelity.
  - Strength↑ = 참조를 강하게 모방(표정·각도·포즈까지 닮아버릴 수 있음). 과의존하면 낮춘다.
  - Fidelity 1 = 참조를 강하게 강제(프롬프트로 덮기 어려움), 0 = 유연.
- 비용: 참조 1장당 생성마다 +5 Anlas(참조 수만큼 증가). → Opus 무료 생성 조건에서 벗어남.
- 여러 캐릭터 참조를 동시에 넣으면 **섞인다**(슬롯별 분리 안 됨).
- 참조 이미지 권장: 단순 배경·중립 포즈의 전신 1장 / 구석에 얼굴 확대 크롭 / 여러 각도 턴어라운드 시트. 생성하려는 부위(상반신이면 상반신 참조)를 크게. 깔끔한 일러스트가 유리.
- 참조용 시트 태그: `multiple views`, `turnaround`, `reference sheet` + `no text`, `cropped shoulders`, `expressions`.
- 인페인트와 함께 쓰면 의상·디테일 수정 가능.

### A3. 다인물 (…/multiplecharacters)
- 캐릭터 프롬프트 박스 권장. 인원수 태그(`2girls`)는 베이스에, 각 캐릭터 박스엔 `girl`/`boy`(숫자 없이).
- 캐릭터별 UC로 특징 번짐 차단. Custom 위치(V4/V4.5는 5×5 그리드).
- 액션 태그 `source#`/`target#`/`mutual#` — 문서도 "항상 신뢰할 수는 없음". 커뮤니티(aichat.tistory 32)는 "행동 주체를 캐릭터 1, 대상을 캐릭터 2로 두는 편이 잘 됨".

### A4. 문법 (…/strengthening-weakening, …/tags)
- `{}` ×1.05, `[]` ÷1.05. 수치 `1.5::태그::`(V4+), 음수 `-1::hat::`(V4.5+, 개념 제거·반전). UC에서는 효과 반대.
- 태그 끝이 숫자면 `::` 앞에 공백: `2::artist:jp06 ::`(커뮤니티 aichat 22·아카 144911662).
- 품질 태그: `best quality`, `amazing quality` … / 미학: `masterpiece`(V4.5+), `very aesthetic` / V5 전용: `low|medium|high|ultra complexity`, `depthness`, `attractive male`, `meta:novel era`, `meta:golden era`, `visual novel sprite` 등, 투명: `transparent background`.
- Add Quality Tags가 붙이는 문자열: V5 `, very aesthetic, masterpiece, no text` / V4.5 Full `, location, very aesthetic, masterpiece, no text` / V4.5 Curated는 `rating:general` 포함.
- 프롬프트 청크 `!macro:이름!`, 랜덤 `||a|b||`.

### A5. 일관된 캐릭터 튜토리얼 (…/tutorial-charactercreation)
- `1girl, solo` → 프레이밍 → 머리(스타일·길이·색) → 눈·피부 → 복장(부위별·색까지 구체) → 체형. **복장 태그가 구체적일수록 일관성↑.**
- 시드 고정 후 한 번에 한 태그씩 바꿔 비교. 오드아이 방지 `heterochromia`를 UC에. 캔버스가 세로로 길면 키가 커 보임.
- 완성된 전체 태그 세트를 재사용하고 포즈·앵글·배경만 바꾼다.

### A6. 디렉터 툴 (…/directortools)
- Emotion: 표정 변경, Emotion Level, Emotion Prompt. **정면·중립·단독 애니 캐릭터에서 가장 잘 됨**, 중립이 아니면 먼저 중립으로 변환 권장. 표정 외 부분도 바뀔 수 있음.
- Remove Background(누끼), Line Art, Sketch, Colorize, Declutter(떠다니는 글자·잡티 제거).

### A7. 인페인트·이펙트
- Inpaint: 마스크 영역만 재생성, Strength(V4+), Focused Inpainting(약 1MP로 확대해 재생성, Opus는 큰 이미지도 0 Anlas). 한 번에 한 부위씩 고친다.
- Effort(V5 Full): Medium = 증류 모델, High 대비 약 42% 적은 사용량, 14 steps·Euler Ancestral 고정, 커스텀 UC 불가(음수 가중치로 대체).

### A8. V5 할당량 부스트 [공식 저널, 아카 aiart 185863875 요약]
- journal.novelai.net "novelai-diffusion-v5-opus-usage-boost": 할당량 100% 추가 $5.99, 부스트 최대 400%, 기존 할당량 먼저 소모, 구매 후 1년 소멸. 댓글 "28스텝 기준 100% ≈ 1,600장".
- [3rd] airmore.ai 리뷰: Opus V5 약 1,800장/주, 시간당 약 0.5% 회복.

## B. 디시 「Ai 그림 여성향」 미니갤 개념글 (gall.dcinside.com/mini/aipicture)
| 글 | 추천 | 핵심 |
|---|---|---|
| 1246 NovelAI 입문부터 짤팁까지 (2026-08-08) | 57 | 기본 세팅 Steps 28, Guidance 5~6, Variety+ 끔, Rescale 자율. 프롬프트 = 작가 태그 + (장르) + (화풍) + 일반 + 퀄리티 + 음수 가중치(`-3::simple illustration::`) + UC. 작가 태그 뭉치: 양끝 1개씩은 마감 인상, 양끝 2~3번째가 화풍의 핵심, 중앙은 형태·디테일·색감. 끝쪽이 앞쪽보다 영향 강함. **화풍 고정↑ = 디테일↓ 트레이드오프.** Curated = 전체연령, Full = NSFW. Add Quality Tags는 화풍 다양성 해쳐서 끄는 사람 많음. 반실사는 Guidance 6 + UC 프리셋 끔. 작가 태그는 단부루 게시물 50개 이상(퀄업용은 100개 이상). 태그는 "단어"가 아니라 단부루에서 그 태그로 분류된 이미지 유형을 불러오는 명령 → 캐릭터명·장르 태그가 그림체를 덮어쓸 수 있음 |
| 2049 V5 깎을 때 하고 있는 것들 (2026-09-05) | 34 | V4.5 긍정 태그 버리고 시작, 나중에 `year 2024~2026, very aesthetic, masterpiece` 추가. V5 작가 태그 가중치 1.5 넘기지 않기, 0.1~0.2씩(안정되면 0.05씩) 조정. 남캐는 `adult`만 넣어도 좋아짐. `portrait`는 화풍에 따라 얼굴이 실사화 → `upper body` 권장. 칙칙하면 `pale color, muted color`에 음수 가중치. 노란 색감은 UC `yellow tint`(1678도 동일). 긴 UC 실사용 목록 공유 |
| 1242 뉴비 그깎 방법 (2026-08-08) | 31 | 캐릭터 프롬프트를 고정해 두고 작가 태그만 하나씩 `2::artist:이름 ::`로 돌려보며 화풍 선택. 실사용 UC 목록 |
| 2155 V5는 4.5처럼 고정 안 해도 됨 (2026-09-09) | 19 | V4.5는 핵심 작가 1개에 큰 가중치를 줘야 화풍이 일정, **V5는 고른 가중치(1::A::,1::B::…)여도 섞인 상태를 일정하게 유지** |
| 1719 V5 그깎 개꿀팁 / 아카 characterai 184632304 | 29 / 56 | 작가 태그 사이를 `,` 대신 `|`로 구분하면 서로 먹히지 않고 섞임(V5, 문서 미기재·커뮤니티 검증) |
| 1862 그림체 안정 유지 (2026-08-30) | 26 | `coloring artist:이름`, `ligne claire coloring`처럼 선화/채색/인체 역할을 지정하면 V5에서 더 안정 |
| 2808 i2i로 V5와 V4.5 섞기 (2026-10-17) | 31 | V5로 뽑은 그림을 V4.5에서 i2i(strength 0.39~0.44)로 돌리면 V5 디테일 + V4.5 부드러움 |
| 2526 V5 작태 통계 | 48 | 공유된 V5 그깎 남성향 2,100개·여성향 175개 통계 뷰어(작태 빈도·동시 사용·평균 가중치) |
| 903 / 1085 화풍 태그 모음·조합 | 55 / 29 | `watercolor (medium)`, `ligne claire`, `muted color`, `flat color`, `anime coloring`, `thick lineart` 등. 조합 예: 애니화 `2::animeStyle(medium), anime coloring, animated::` |
| 1309 표정 바리에이션 태그 | 22 | `full body, multiple views, 3::game asset, game ui, expression variation, character profile, multiple expressions, variations::` |
| 1281 단부루에서 작태 찾기 | 18 | SNS 작가 → `danbooru artist profile @아이디` 검색, 다른 아이디로 학습됐을 수 있음 |
| genit 10811 NAI 메타데이터 지우기 | 7 | **NAI는 PNG 픽셀 LSB에 생성 정보를 숨긴다 → 메타데이터만 지워도 NAI Inspect가 복원.** JPG 손실 압축이면 사라지고, LSB 0 치환 도구도 있음. → 우리 파이프라인의 webp(손실) 변환이 이 역할을 겸함 |

## C. 아카라이브
### C1. AI그림 채널(aiart)
| 글 | 추천 | 핵심 |
|---|---|---|
| 159947900 AI 그림 기초 가이드 + 그림체 1,000종 (V4.5) | 197 | 채널 대표 가이드(V5 미반영). |
| 181003788 V5 초보 가이드 | 68 | V4.5 설정 다 지우고 기본값부터. **태그 = 개념(인원·의상·시점·정형 포즈), 자연어 = 관계(누가 무엇을 잡는지·좌우·광원).** 영역별 정리 [STYLE][LIGHTING][CHARACTER][EXPRESSION][POSE][COMPOSITION][BACKGROUND]. 인체 오류는 조건 충돌부터 제거. Complexity는 high 기준. 국소 오류는 인페인트. 한 번에 변수 하나 |
| 185743404 뉴비 퀵가이드 V5 | 40 | 초보는 V5 Full, effort medium, steps 28 이하, Opus면 무료 범위 |
| 182356864 레퍼런스로 뽑은 사람들 이거 넣어 | 42 | V4.5 정밀 참조 0.9/0.9 + 프롬프트 `2::The character has the same distinctive physical features hairstyle and accessories as in the reference image::` → 복장·머리장식·뿔·꼬리·독특한 헤어 유지 |
| 182941525 (눈_눈) 표정 | 60 | 특정 표정을 70% 타율로: 표정 태그를 묶어 가중치 + 반대 개념 음수 가중치 |
| 161316593 정밀 참조 출시 번역 | 36 | A2와 동일. 스타일 참조로 인페인트할 땐 강도·충실도 낮춤 |
| 144911662 V4.5 가이드라인 | 57 | 공식 문서 통합본. 등급 태그 `rating:general/sensitive/questionable/explicit`. Seed 고정 후 Guidance 0.1 단위 미세조정 |
| 181837481 ComfyUI 감정 에셋 워크플로우 | 24 | 로컬 38종 감정 세트. "NAI 4.5 캐릭터 레퍼런스가 별로라 로컬로 감" — 레퍼런스 한계 의견 |

### C2. 캐릭터챗 채널(characterai) — 에셋봇 제작자
| 글 | 추천 | 핵심 |
|---|---|---|
| 159738165 애셋 일관성에 대한 개인적 생각 | 54 | 일관성 수단 3가지: Nano Banana, LoRA(로컬), NAI 캐릭터 레퍼런스 — 다만 세팅·비용 때문에 대량 생산은 결국 수동 뽑기가 많음. **실전 결론: ① 인물 위치·구도를 고정하고 얼굴·손만 바꾸면 스크롤 시 통일돼 보인다 ② 자세를 크게 바꾸면 비교가 안 돼 통일돼 보인다 ③ 핵심 디자인 요소(예: 특정 앞머리) 하나만 집요하게 맞춰도 통일감 ④ 유저는 생각보다 신경 안 씀.** 일관성 상위 사례: 성간 제국 연대기(1,600+장), 단간 HER, 전투원화 개조 시뮬레이터 |
| 139347728 감정 에셋 프리셋 72종(235개) | 25 | SD스튜디오용 감정 프리셋(아래 D에 상황코드로 변환). NAI 원본은 124020289(V3)·160306435(최신, 열람 불가 처리) |
| 160553593 프리셋 씬 명칭 수정 | 3 | 출력 모델(Gemini 등)이 `smile`/`smiling`처럼 **에셋 이름을 제멋대로 바꿔 출력** → 명칭을 통일해야 함. → 우리 숫자 코드표 방식이 이 문제를 피함 |
| 162231996 36종 sfw + 32종 nsfw | 3 | 시뮬봇은 캐릭터당 sfw 36종이 현실적 상한(댓글: 등장인물 많으면 36도 빡셈) |
| 175868853 | 56 | 의상 15종 × 감정 24종 = 캐릭터 1명에 360장 — 노동량 경고 |
| 176196083 SDStudio 막차 / 162731397 87-studio / NAIS2·NAIS3 | 49 / — | **NAI 대량 생성 관리 앱**: SDStudio(프로젝트·씬 단위, 개발 중단 예정, 포크 존재), NAIS3(경량 신작), 87-studio(웹, 모바일, SDStudio json 호환, github.com/snuff8729/87-studio). 캐릭터 프리셋 × 감정 씬을 일괄 생성 |
| 186212629 / 186016798 나히아 얼티밋 | 52 / 80 | 에셋봇 제작은 그림·출력식·**V5 할당량 비용**이 병목. 배경 CG와 인물 CG 분리 배치, 투명 배경은 V5 필요 |
| 186454942 | 3 | 실수로 Curated로 에셋을 뽑아 구도·성인 컷이 안 나옴 → **모델 선택 확인** |
| 186483553 | 3 | "nai5 레퍼(정밀 참조) 안 나와서 4.5로 에셋 뽑는 중"(2026-10-20) — V5 정밀 참조 미지원 재확인 |
| 185087113 | 55 | (농담조) 홍보 스샷용 컷만 인페인트로 공들이기 → 대표 이미지·홍보 컷 우선 품질 관리 |

## D. 감정 프리셋 → 우리 상황코드 매핑용 원문 태그 (characterai 139347728, 로컬 문법 `(tag:1.1)`을 NAI `1.1::tag::`로 바꿔 사용)
- default: `looking at viewer`
- smiling(미소): (원 프리셋 smile) — `looking at viewer, smile, closed mouth`
- laughing: `hand over own mouth, (happy, smile, laughing, closed eyes, +++:1.1)`
- giggling: `(happy, smile, closed eyes:1.15), (^ ^, hand over own mouth, covering mouth:1.25)`
- sad: `looking at viewer, parted lips, (raised eyebrows, tearing up, hand on own chest, clenched hand:1.1), (sad, frown:1.15)`
- crying with eyes closed: `looking down, (closed eyes:1.5), (sad:1.4), frown, crying, tears, (rubbing eyes, wiping tears, open mouth, wavy mouth:1.2), clenched hand`
- pouting: `looking at viewer, (pout, crossed arms:1.1)`
- angry: `looking at viewer, (angry:1.1), anger vein, wavy mouth, open mouth, (hands on own hips:1.1), leaning forward`
- contemptuous: `looking at viewer, (disgust, expressionless, frown, half-closed eyes, parted lips:1.2), (shaded face:1.3), (arms at sides:1.1)`
- blushing shyly: `looking at viewer, embarrassed, full-face blush, half-closed eyes, furrowed brow, raised eyebrows, (covering mouth, hand over own mouth, own hands together:1.25), (clenched hands:1.15)`
- flustered: `looking at viewer, surprised, sweat, (flustered, embarrassed, shy, blush, raised eyebrows, chestnut mouth:1.1), (hand in own hair, playing with own hair, twirling hair:1.2)`
- surprised: `looking at viewer, surprised, open mouth, (wide-eyed, hand to own mouth, hand on own face, ^^^:1.1)`
- shocked: `looking at viewer, furrowed brow, (surprised, wide-eyed, confused, open mouth, rectangular mouth, wavy mouth, shaded face, ^^^, !?:1.1), (constricted pupils:1.2), (hands up:1.2)`
- 그 외 프리셋 항목: annoyed, confused, curious, disappointed, depressed, disgusted, embarrassed, fidgeting shyly, full-face blush, guilty, indifferent, joyful, lovestruck, looking away shyly, nervous, proud, scared, serious, sleepy, smug, thinking, worried, excited, admiring, sniggering, suspicious, relieved, pleading, determined, jealous, bored, exhausted 등(총 72종).
