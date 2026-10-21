# 05. 프롬프트 레시피 (스타일별·표정 세트·네거티브·썸네일)

> 목적: 복사해서 바로 쓰는 프롬프트 블록. 태그형(Illustrious/NoobAI/Animagine/NovelAI)과 자연어형(Nano Banana/GPT Image/플랫폼 내장) 두 버전을 스타일별로 제공하고, 네거티브·표정 세트·썸네일 팁을 붙인다.
> 근거: research/04-image-assets.md §5(프롬프트 레시피)·§3-3(표정 세트)·§6-2(썸네일)·§1-2(케이브덕 아트 스튜디오 프롬프트)·§1-3(베이비챗 스타일), research/09-caveduck-official-docs-2026-10-21.md I, research/10-crack-official-docs-2026-10-21.md K, research/03-character-design-knowhow.md(썸네일 레이아웃 커뮤니티 팁)
> 표기: [공식] / [3rd] / [커뮤니티] / [추정]. **모든 예시 캐릭터는 성인(나이 명시)·오리지널.** `{ }` 안은 교체 변수.

---

## 1. 공통 원칙 (research/04 §5-1·§5-4)

1. **설정 카드(고정) + 장면 변수(교체)** 구조. 고정 블록은 프롬프트 맨 앞.
2. 태그 순서: **인원·구도 → 캐릭터 외형 → 의상·소품 → 표정·포즈·시선 → 배경·조명 → 화풍 → 품질**. 긴 프롬프트일수록 뒤쪽 영향이 약해진다.
3. 비율은 **생성 시점에 플랫폼 비율로 지정**(1:1 프로필·크랙 / 2:3 베이비챗·케이브덕 / 3:4 제타 / 16:9 배경).
4. 나이 표기: 태그형은 `adult, mature female/male`, 자연어형은 "28세 성인 여성"처럼 숫자+성인. 교복·학교 배경은 **금지 블록에 항상 포함**.
5. 품질·화풍 블록은 스니펫으로 저장(케이브덕 @단축어, NAI 프리셋, ComfyUI 문자열 노드).
6. 한 캐릭터 = 한 모델. 팔레트 hex 3~4색과 조명 방향 명시.

---

## 2. danbooru 태그 기본 (Illustrious / NoobAI / Animagine / NovelAI 공통)

- 표기: `언더스코어_연결` 또는 공백(사이트별). Illustrious v1.1 이후 부분 자연어 지원(100% 자연어 비권장). [3rd] research/04 §5-1
- **품질 태그(Illustrious)**: `masterpiece, best quality, very aesthetic, absurdres` (+`newest`). CFG 4.5~5, Clip Skip 2 권장 가이드 있음.
- **표정 태그 모음**:
```
smile, light_smile, grin, :d, open_mouth, closed_mouth, laughing, happy
blush, nose_blush, embarrassed, flustered, shy
angry, furrowed_brow, v-shaped_eyebrows, clenched_teeth, glaring
sad, frown, crying, tears, streaming_tears, teary_eyes
surprised, wide-eyed, :o
smug, pout, tongue_out, wavy_mouth, nervous, sweatdrop, scared
expressionless, serious, sleepy, half-closed_eyes, closed_eyes, sparkling_eyes, heart-shaped_pupils
looking_at_viewer, looking_away, looking_to_the_side, head_tilt
```
- **의상·장르 태그**:
```
한복/사극      hanbok, korean_clothes, gat, norigae
무협/중화풍    hanfu, chinese_clothes, black_robe, sword, katana, hair_tie
로판          ball_gown, off-shoulder_dress, lace, tiara, jewelry, gloves, corset, cape
현대          suit, necktie, dress_shirt, office_lady, hoodie, denim, turtleneck, coat
판타지        armor, cape, cloak, staff, magic_circle, pointy_ears
(주의)        school_uniform, serafuku, blazer+pleated_skirt 조합은 사용 금지(미성년 신호)
```

---

## 3. 네거티브 프롬프트 세트

**3-1. 기본(Illustrious 계열은 네거티브를 잘 따름)**
```
worst quality, low quality, lowres, bad quality, displeasing, very displeasing, bad anatomy, bad hands, extra digits, missing fingers, extra limbs, multiple views, comic, text, watermark, signature, jpeg artifacts, blurry
```

**3-2. 세이프티 프로필·상황 이미지용(기본에 추가)**
```
nsfw, nipples, see-through, underwear, lingerie, cleavage, bare_shoulders_emphasis, wet_clothes, torn_clothes, blood, gore, injury, weapon_pointing_at_viewer, child, loli, shota, aged_down, petite, flat_chest, school_uniform, serafuku, classroom, school, realistic, photorealistic, photo, 3d, real_person
```
- 수영복·운동복 장면이 필요하면 `cleavage, bare_shoulders_emphasis`만 제거하고 나머지는 유지(크랙·케이브덕·베이비챗 모두 "일반 노출 허용, 부위 강조 금지").

**3-3. 썸네일 전용(세이프티용에 추가)**
```
full_body, from_behind, multiple_girls, multiple_boys, 2girls, 2boys, busy_background, cluttered, small_face, text, speech_bubble
```

**3-4. 언세이프 앨범용(가림은 후처리; 미성년 신호는 여전히 금지)**
```
worst quality, low quality, bad anatomy, bad hands, extra digits, child, loli, shota, aged_down, petite, flat_chest, school_uniform, serafuku, classroom, school, realistic, photorealistic, photo, real_person, text, watermark, mosaic, censored_bar
```
- `mosaic, censored_bar`를 네거티브에 두는 이유: 플랫폼은 모자이크·블러를 인정하지 않으므로 생성물의 자동 검열을 끄고 **불투명 도형을 직접** 얹는다(`06-policy-checklist.md` §4).

---

## 4. 스타일별 레시피

각 레시피는 (A) 태그형 (B) 자연어형. 예시 캐릭터는 전부 오리지널·성인.

### 4-1. 한국 웹툰풍 공통 베이스 (모든 스타일의 화풍 블록)
```
# (A) 화풍 블록 — 모든 태그형 프롬프트 끝에 붙임
clean lineart, cel shading, flat color, vivid colors, webtoon style, manhwa style, simple background, masterpiece, best quality, very aesthetic, absurdres
```
```
# (B) 자연어 화풍 블록
화풍: 한국 웹툰 스타일. 깨끗한 검은 외곽선(중간 굵기), 2단계 셀셰이딩, 채도 높은 플랫 컬러, 배경 디테일 간결. 실사풍·3D·회화풍 아님.
```

### 4-2. 현대물 (예: 서하린, 28세, 광고회사 기획팀장)
```
# (A) Illustrious
1girl, solo, adult, mature female, korean, short dark brown hair, inward curl bob, brown eyes, ivory blouse, navy pants, rolled sleeves, silver wristwatch, pearl earrings,
modern office, window, city lights, night, upper body, looking at viewer, light smile,
clean lineart, cel shading, flat color, webtoon style, manhwa style, masterpiece, best quality, very aesthetic, absurdres
```
```
# (B) Nano Banana / 내장
[설정 카드]
캐릭터: 서하린, 28세 한국인 성인 여성. 어깨 길이 흑갈색 단발(안쪽 C컬), 짙은 갈색 눈, 밝은 피부, 보통 체형.
의상: 아이보리 블라우스, 네이비 슬랙스, 소매 걷음. 소품: 은색 손목시계, 작은 진주 귀걸이.
{화풍 블록}
금지: 얼굴·머리·의상·화풍 변경 금지. 배경 글자·다른 인물 금지. 교복·학교 배경 금지. 실사풍 금지.
[장면]
구도: 3:4 상반신, 눈높이. 배경: 밤의 사무실 창가, 도시 야경. 표정: 살짝 웃는 얼굴. 시선: 정면.
```

### 4-3. 로판 (예: 윤세아, 24세, 몰락 백작가의 공녀)
```
# (A)
1girl, solo, adult, mature female, long wavy silver hair, violet eyes, ball gown, off-shoulder dress, lace, jewelry, tiara, white gloves, rose garden, marble terrace, chandelier light, soft lighting, elegant, upper body, looking at viewer, light smile,
manhwa style, soft shading, pastel colors, clean lineart, masterpiece, best quality, very aesthetic, absurdres
```
```
# (B)
캐릭터: 윤세아, 24세 성인 여성. 허리까지 오는 은빛 웨이브 머리, 보라색 눈, 창백한 피부, 가는 체형이지만 성인의 얼굴선.
의상: 오프숄더 아이보리 볼가운, 레이스, 작은 티아라, 흰 장갑. 소품: 가문 문장이 새겨진 반지.
화풍: 한국 로맨스판타지 웹툰 스타일, 부드러운 음영, 파스텔 톤, 화려한 장식 디테일, 깨끗한 선.
금지: 가슴·허리 강조 포즈 금지, 유혹적 표정 금지, 실사풍 금지, 어린 얼굴 금지.
[장면] 3:4 상반신. 장미 정원의 대리석 테라스, 샹들리에 불빛. 표정: 고요한 미소. 시선: 정면.
```
- 로판은 드레스·보석·궁정 조명이 "장르 코드"(썸네일 §7). 베이비챗 내장 생성은 스타일 '로판' 프리셋이 따로 있으므로 (B)에서 화풍 문장은 빼고 외형·장면만.

### 4-4. 무협 (예: 이도윤, 31세, 파문당한 검객)
```
# (A)
1boy, solo, adult, mature male, long black hair, hair tie, sharp eyes, scar on cheek, hanfu, chinese clothes, black robe, sword, martial arts, bamboo forest, mist, wind, dynamic pose, serious, ink wash background,
manhwa style, dramatic lighting, clean lineart, masterpiece, best quality, absurdres
```
```
# (B)
캐릭터: 이도윤, 31세 성인 남성. 허리까지 묶은 긴 흑발, 날카로운 눈매, 왼뺨의 오래된 흉터, 단단한 체형.
의상: 검은 도포, 가죽 손목 보호대, 등에 멘 장검. 소품: 낡은 붉은 끈.
화풍: 한국 무협 웹툰 스타일, 굵고 거친 외곽선, 먹 번짐 배경, 명암 대비 강함.
금지: 과도한 혈흔·상처 노출 금지(프로필용), 실사풍 금지.
[장면] 3:4 상반신. 안개 낀 대나무 숲, 바람. 표정: 진지, 입 다묾. 시선: 카메라를 지나 먼 곳.
```
- 혈흔은 크랙 프로필에서 금지, 상황 이미지도 "과도한 혈흔" 금지 → 전투 컷은 피 없이 검광·먼지로 연출.

### 4-5. 남성향 (여성 캐릭터 중심 연출; 예: 한소율, 26세, 동네 카페 사장)
```
# (A)
1girl, solo, adult, mature female, korean, long brown hair, ponytail, warm brown eyes, apron, white shirt, rolled sleeves, cafe interior, counter, coffee cup, morning light, window, upper body, looking at viewer, smile, head tilt,
clean lineart, cel shading, flat color, webtoon style, manhwa style, masterpiece, best quality, very aesthetic, absurdres
```
```
# (B)
캐릭터: 한소율, 26세 성인 여성. 긴 갈색 포니테일, 따뜻한 갈색 눈, 건강한 피부, 보통 체형.
의상: 흰 셔츠 위 갈색 앞치마, 소매 걷음. 소품: 손에 든 커피잔.
{화풍 블록}
금지: 노출·가슴 강조·유혹 포즈 금지(세이프티 프로필), 앳된 얼굴 금지, 교복 금지.
[장면] 1:1 상반신 클로즈업. 아침 햇살 드는 카페 카운터. 표정: 고개를 살짝 기울인 미소. 시선: 정면.
```
- 남성향 썸네일의 통념은 "친근한 미소·시선 맞춤"이지만 **부위 강조·유혹 연출은 4사 모두 제한**(케이브덕·제타는 표정·자세의 성적 암시도) → 관계 암시는 표정·거리로만.

### 4-6. 여성향 (남성 캐릭터 중심 연출; 예: 차서진, 32세, 외과 전문의)
```
# (A)
1boy, solo, adult, mature male, korean, black hair, undercut, sharp eyes, glasses, tall, white coat, dress shirt, loosened necktie, stethoscope, hospital corridor, evening light, upper body, looking at viewer, slight smile,
clean lineart, cel shading, flat color, webtoon style, manhwa style, masterpiece, best quality, very aesthetic, absurdres
```
```
# (B)
캐릭터: 차서진, 32세 성인 남성. 짧은 흑발 언더컷, 날카로운 눈매, 얇은 은테 안경, 키 큰 체형, 넓은 어깨.
의상: 흰 가운, 셔츠, 느슨한 네이비 넥타이. 소품: 목에 건 청진기, 은색 시계.
{화풍 블록}
금지: 셔츠 풀어헤침·상체 노출 금지(프로필), 실사풍 금지.
[장면] 3:4 상반신. 저녁 빛 드는 병원 복도. 표정: 살짝 비웃는 듯한 미소. 시선: 정면.
```
- 여성향 썸네일은 **눈매·입꼬리** 디테일이 클릭을 좌우한다는 통념[추정] → 얼굴이 화면의 40% 이상, 역광보다 정면 보조광.

---

## 5. 표정 세트 프롬프트 템플릿

### 5-1. 태그형 (시드 고정 + IP-Adapter, 표정 블록만 교체)
```
# BASE (고정)
{인원·구도} 1girl, solo, adult, mature female, upper body, looking at viewer,
{외형} short dark brown hair, inward curl bob, brown eyes,
{의상} ivory blouse, navy pants, silver wristwatch, pearl earrings,
{표정} ← 아래 목록에서 교체
simple background, green background, clean lineart, cel shading, flat color, webtoon style, manhwa style, masterpiece, best quality, very aesthetic, absurdres

# 표정 블록 목록 (파일명 stem과 1:1)
neutral   : expressionless, closed mouth
smile     : light smile
laugh     : laughing, open mouth, :d, closed eyes
blush     : blush, embarrassed, looking away, flustered
angry     : angry, furrowed brow, v-shaped eyebrows, clenched teeth
sad       : sad, frown, teary eyes
surprised : surprised, wide-eyed, :o
smug      : smug, half-closed eyes, light smile
sleepy    : sleepy, half-closed eyes, yawning
crying    : crying, tears, streaming tears
nervous   : nervous, sweatdrop, wavy mouth
scared    : scared, wide-eyed, trembling
serious   : serious, closed mouth
pout      : pout, looking away
excited   : sparkling eyes, open mouth, happy
```
- ComfyUI: 문자열 리스트 노드에 표정 블록 15줄 → 배치 실행, 시드 고정, IP-Adapter 마스터 A. 필요 시 ControlNet OpenPose로 머리 각도 고정. research/04 §3-3 C
- NAI: Character Reference 마스터 A + strength 낮춤 + 표정 태그 교체. 또는 `expressions, multiple views, reference sheet, no text` 시트 1장 후 분할.

### 5-2. 자연어형 (Nano Banana / GPT Image)
```
[마스터 A 업로드]
이 캐릭터의 얼굴·머리·의상·조명·카메라 구도·배경(단색 #00FF00)을 그대로 유지하고,
표정만 "{표정 설명}"으로 바꿔줘. 3:4 비율. 글자·다른 인물 없이.

표정 설명 목록:
neutral  = 무표정, 입 다묾
smile    = 입꼬리만 살짝 올라간 미소
laugh    = 눈을 감고 활짝 웃음, 입 벌림
blush    = 볼이 붉어진 채 시선을 옆으로 피함
angry    = 미간 찌푸림, 이 악묾
sad      = 눈가에 눈물 맺힘, 입꼬리 내려감
surprised= 눈 크게 뜨고 입 약간 벌림
smug     = 반쯤 감은 눈, 비웃는 듯한 미소
sleepy   = 반쯤 감긴 눈, 하품
```
- 표정당 1장씩. 격한 표정·혀 내밀기는 NB 필터에 걸릴 수 있음 [커뮤니티].

### 5-3. 플랫폼 내장
- **베이비챗**(130프로챗/장): 캐릭터 에셋 > AI로 생성 > 레퍼런스 = 마스터 A, 스타일은 UI에서 선택(로판/청량/동양화/애니/순정/카툰), 비율 3:4, 프롬프트에는 외형·표정만(≤1,000자). "성별·스타일 변경 시 프롬프트 초기화" 주의.
- **케이브덕 아트 스튜디오**: 영어 자연어 권장 + '다듬기'. 이미지 편집(원본 인물 유지)으로 표정 변경. 예:
```
Same character, keep face, hair, outfit and lighting identical. Change only the expression to a shy blush, looking away. Plain green background, 2:3.
```
- **크랙 변형**(95크래커): 마스터 업로드 → "표정만 부끄러워하는 얼굴로, 나머지는 그대로"처럼 **한 끗만** 한글로 기술 [공식] research/10 K. 일관성 보장 없음 → 결과를 4칸 검수.

---

## 6. 배경·상황 컷 템플릿

```
# 배경(인물 없음) — 16:9
(A) no humans, scenery, {장소: modern office interior}, {시간: night}, {날씨/분위기: rain on window, city lights}, wide shot, clean lineart, cel shading, flat color, webtoon style, masterpiece, best quality, absurdres
(B) 인물 없는 빈 장소. {장소}, {시간}, {날씨}. 16:9 와이드. 화풍: {화풍 블록}. 글자·간판 문구 없이.

# 상황 컷 — 1:1(크랙) / 2:3(케이브덕·베이비챗)
(A) {BASE 외형·의상 블록}, {동작: holding umbrella, offering hand}, {배경: rooftop, night, after rain}, {구도: upper body, from side}, {표정}, {조명: rim lighting}, {화풍 블록}
(B) [설정 카드] + 구도/배경/동작/표정/조명/금지 6줄 (04-webtoon-intro.md §2-3 참고)
```
같은 장소의 낮/밤/비 3종은 같은 시드·같은 레퍼런스로.

---

## 7. 썸네일 디자인 팁 (research/04 §6-2, research/03 커뮤니티 팁)

플랫폼이 공개한 썸네일 CTR 데이터는 **없음**(미확인). 아래는 일반 원칙 + 커뮤니티 관찰 [추정/커뮤니티].

### 7-1. 구도
- **상반신 클로즈업 + 시선 맞춤(looking at viewer)** 기본. 전신은 작은 썸네일에서 얼굴이 뭉개짐. 얼굴이 화면 짧은 변의 1/3 이상.
- **얼굴 중앙 배치**: 크랙 대화 아이콘은 원형 크롭, 제타 구 1:1은 좌우 크롭 → 중앙 안전 영역(짧은 변 기준 지름 80% 원) 안에 얼굴·핵심 소품.
- **우하단 비움**: 크랙은 연령 표시·다중 이미지 뱃지가 우하단을 가림 [커뮤니티 뤼튼갤 76734]. 다른 플랫폼도 뱃지 위치 미확인 → 우하단에 얼굴·글자 두지 않기.
- 채도 높고 색감 화려하며 얼굴이 크게 보이는 이미지가 클릭이 높다는 커뮤니티 통념 [커뮤니티] research/03.

### 7-2. 장르 코드 즉시 전달
로판 = 드레스·보석·궁정 조명 / 무협 = 도포·검·먹 배경 / 현대 = 셔츠·후드·도시 야경 / 힐링 = 따뜻한 역광·카페·식물. 썸네일 1장에서 장르가 읽혀야 한다.

### 7-3. 표정
"관계 암시형"(살짝 웃음·시선 회피·도발)이 중립 표정보다 선호된다는 통념 → **표정 세트의 smile / smug / blush 3장을 썸네일 후보로 재활용**. 단, 케이브덕·제타는 표정·자세의 성적 암시를 제한하므로 "도발"은 입꼬리·눈매 수준까지만.

### 7-4. 텍스트 오버레이
- NB Pro는 한글 렌더링이 좋아 제목·한 줄 훅을 넣을 수 있으나 **짧고 중립적으로**(크랙 프로필 내 비속어·성적 은어 금지, 제타 2026-02 시위 문구 이미지 삭제).
- 크랙 세이프티 버전 관례: 제목에 `S`, `ˢᵃᶠᵉ` 등 세이프 표식 [추정] research/05 → 썸네일에도 작은 "SAFE" 뱃지를 넣는 사례가 있으나 공식 규정 아님.
- 텍스트는 상단 또는 좌측(우하단 금지), 폰트는 굵은 고딕, 배경과 대비 4.5:1 이상, 글자 수 8자 이내.

### 7-5. A/B 테스트 방법 [프로젝트 규칙]
1. 후보 3장(표정 2종 × 텍스트 유무) 준비, 같은 구도·같은 팔레트.
2. 제타는 통계 탭 **노출 대비 클릭률**로 7일 비교 [나무위키] research/02 5.1. 크랙·케이브덕·베이비챗은 클릭률 지표 **미확인** → 대화 시작 수/노출 추정으로 7일 간격 교체 비교.
3. 결과를 `characters/<slug>/status.md`에 날짜·버전·수치로 기록.
4. 제타 커버 10장: 1장 = 얼굴 썸네일, 2~4장 = 인트로 컷, 나머지 = 세계관·장소.

### 7-6. 썸네일 프롬프트 템플릿
```
# (A) 1:1 / 2:3 / 3:4 각각 생성
{BASE 외형·의상 블록}, portrait, upper body, face focus, looking at viewer, {smile | smug | blush}, {장르 코드 배경 1~2개}, centered composition, simple background, soft lighting on face, clean lineart, cel shading, vivid colors, webtoon style, masterpiece, best quality, very aesthetic, absurdres
NEG: {기본} + {세이프티용} + {썸네일 전용}

# (B)
[설정 카드] 구도: {비율} 상반신 클로즈업, 얼굴이 화면 중앙·세로 1/3 이상, 우하단 비움. 배경: {장르 코드}, 단순. 표정: {smile|smug|blush}. 시선: 정면. 글자 없음(또는 상단에 "{8자 이내 훅}" 굵은 고딕 흰색).
```
