# 04. 캐릭터챗 이미지·비주얼 에셋 제작 리서치 (2025–2026)

작성일: 2026-10-21
대상 플랫폼: 크랙(뤼튼) · 케이브덕 · 베이비챗 · 제타 (+ 참고: 캐럿, 포스타입 캐릭터톡, 인터랙트)

> 표기 규칙
> - **[공식]** 플랫폼 공식 도움말·공지·약관에서 확인한 내용
> - **[커뮤니티]** 아카라이브/디시/포스타입/블로그 등 이용자 글 (UI 변경으로 현재와 다를 수 있음)
> - **[추정]** 공개 자료를 조합한 리서처 추정
> - **미확인(로그인 후 제작 화면에서 확인)** : 공개 문서에 수치/목록이 없는 항목

---

## 0. 한눈에 보는 규격 요약표

| 항목 | 크랙 | 케이브덕 | 베이비챗 | 제타 |
|---|---|---|---|---|
| 프로필(대표) 형식/용량 | PNG/JPG/WebP, 5MB 이하 [공식] | 미확인 | 미확인 (AI 생성은 1:1 권장) [공식] | 미확인 (앱 내 AI 생성 또는 업로드) [공식] |
| 프로필 비율 | 정방형 기준 등록(미디어 기준), 권장 px 미확인 | 미확인 (아트 스튜디오 기본 비율 2:3 → 세로형 [추정]) | 1:1 [공식] | **3:4** (2025-11-25부터, 구 1:1은 좌우 크롭) [공식] |
| 대화 중 삽입 이미지 | 상황 이미지(미디어 탭): jpeg/jpg/png/webp/gif, 5MB, 정방형 기준, 구버전 시작설정별 50장 / 신버전 1회 1,000장·총 1,600장 [공식] | 앨범 이미지: 키워드 자동 부여 후 맥락 출력, 100장 초과 시 오작동 가능 [공식] | 캐릭터 에셋(감정 이미지) 최대 100개, 권장 **512×768 (2:3)** [공식] | 캐릭터별 이미지 최대 5장(표정·의상) [공식] |
| 배경/상황 와이드 | 분류를 '배경·사물'로도 등록 가능 [공식] | 에피소드 시작 장면 이미지 가능 [공식] | 상황·배경용 16:9 권장 [공식] | 커버 이미지 최대 10장 [공식]; 배경 이미지 생성(제타패스)은 2026-06-12 종료 [공식/나무위키] |
| 내장 AI 생성 | 있음(2025-09 리뉴얼, 세이프티 한정) [공식] | 아트 스튜디오(Quill 모델, 19+ NSFW 모델 있음), 앨범 생성 10윙 [공식] | 있음(130프로챗/장, 6스타일, 레퍼런스·i2i) [공식] | 스냅샷 15피스 [공식/나무위키] |
| 자동 전환 방식 | 배치표(분류×상황) 등록 → AI 자동 호출; 구버전 `{{img::이름}}` [공식] | 업로드 시 키워드 자동 부여 → 대화 맥락 매칭(동일 키워드 다수면 랜덤) [공식] | 이미지 코드(Slug) `img:[slug]` 자동 매핑 [공식] | (대화 중 자동 삽입 기능은 미확인) |

---

## 1. 플랫폼별 이미지 사용처와 규격

### 1-1. 크랙 (뤼튼) — "즉흥 서사 플레이"

**사용처**
- **프로필 사진(필수)**: 캐릭터 설정 1단계에서 등록. PNG/JPG/WebP, **5MB 이하**. 등록 시 "AI를 통한 선제적 검열"이 있을 수 있음. 권장 해상도(px)는 공개 문서에 없음 → **미확인(로그인 후 제작 화면에서 확인)**. [공식]
- **상황 이미지(스토리 제작 5단계 '미디어')** [공식]
  - 형식: jpeg/jpg/png/webp/**gif**, 최대 5MB. "등록은 정방형 기준으로 처리되며, 세로로 너무 긴 이미지는 권장하지 않음".
  - 구버전: 시작설정별 최대 50장. 이미지 등록 후 `{{img::이미지이름}}`을 **첫 인사말·예시 대화·캐릭터 설정**에 붙여 넣어 채팅에 띄움.
  - 신버전(상황 이미지 시스템 개편): 파일명을 `분류_상황` 형식으로 올리면 자동 분류 → 세부 정보(유저에게 보일 **해금 힌트**, AI 호출에 영향 없는 참고 메모) → **배치표**(분류×상황 2축, 분류는 인물 외 배경·사물도 가능)에 두면 플레이 중 AI가 자동으로 호출. 1회 업로드 최대 1,000장, 총 1,600장.
  - 구체적 호출 트리거(키워드 매칭 규칙)는 문서에 없음 → 미확인.
- **이미지 보관함/해금**: 작품을 플레이하며 이미지를 해금하고 갤러리에 모아보는 기능(앱 업데이트 노트). 해금 힌트와 연동되는 수집 요소. [공식]
- **상태창 이미지 배너**: 작품 상태창에 이미지 예시 배너가 들어감. [공식]
- **표시 팁**: 이미지를 상황 묘사 태그(`**...**`) 안에 넣으면 대사와 겹쳐 보일 수 있으니 태그 바깥 또는 별도 줄에 배치. [공식]
- **웹툰 삽입/'즉흥 서사 플레이' 비주얼**: '즉흥 서사 플레이'는 앱스토어 부제(브랜딩)이며, 별도의 "웹툰 컷 삽입" 전용 기능은 공개 문서에서 확인되지 않음. 실질적으로는 상황 이미지(배치표)+이미지 보관함이 웹툰 컷 역할을 함. 2026년 공지 "더 깊이 있는 연출을 위해 상황 이미지 시스템을 개편했습니다"는 로그인 필요로 본문 미확인.

**내장 이미지 생성** [공식]
- 튜토리얼 구성: 이미지 생성 / 이미지 변형 / 이미지 보관 / 빌더에서의 활용 / 운영정책.
- 빌더 프로필 등록 단계의 **'생성' 버튼** → 이미지 생성 화면으로 이동. **'업로드'**는 라이브러리·좋아요 탭 연동. 미디어 탭(상황 이미지)에서도 동일하게 생성 가능.
- 2025-09 리뉴얼: 품질 향상, **새 이미지 스타일 추가**, 변형(variation) 지원, 속도 개선. **'세이프티' 정책에 맞는 이미지만 생성 가능**(일부 주제 제한). 리뉴얼 시 기존 보관함 이미지 삭제됨.
- 모델명·스타일 목록·장당 비용(크랙 캐시)·무료 횟수 → **미확인(로그인 후 제작 화면에서 확인)**.

**이미지 정책** [공식, 운영정책]
- **프로필 이미지는 세이프티/언세이프티 공통으로 가장 보수적**: 속옷·비치는 옷·민감 부위 강조, 과도한 폭력·혈흔, 나체·성행위 연상 포즈, 이미지 내 비속어·성적 은어, **실제 인물과 유사하거나 실제 사진처럼 보이는 이미지** 모두 금지. 2025-07 운영정책 개정(프로필/상황 이미지 규정 구체화), 2025-08 "프로필 이미지 규정 강화" 공지(기존 캐릭터도 소급 적용 가능).
- **상황 이미지 – 세이프티**(전연령): 부적절 의상(비침·젖음·찢김), 성적 도구, 성행위 연상, 신체 훼손·과도한 혈흔 금지. 예외: 운동·수영복·전투 등 불가피한 노출은 민감 부위 제외 제한적 허용.
- **상황 이미지 – 언세이프티**(성인 인증): 성기·항문·음모·유두·유륜 직접 노출 및 윤곽 금지(불투명 물체로 가림), 체액·배설물 성적 활용 금지, **GIF/WebP 등 움직이는 이미지로 성행위 묘사 금지**.
- **미성년 외형 판단**: 실제 나이 설정과 무관하게 앳된 얼굴·미성숙 체형·교복·학교/학원 배경 등으로 "명백히 미성년자로 인식"되면 미성년으로 간주.
- **실존 인물**: 타인 얼굴·신원 정보 사용 금지, 딥페이크·실물 연상 콘텐츠 금지.
- **저작권/2차창작**: 타인 저작물 무단 사용 금지. 2차 창작물은 원작자 가이드라인 준수 + **세이프티 등급으로만 제작**. 책임은 생성자.
- **AI 생성 이미지 자체를 금지하는 조항은 없음**(위 등급 기준이 동일 적용). 외부 이미지 위반·미성년 성적 대상화는 경고 없이 최고 제재.
- 규정 가이드 하위 문서: 프로필 이미지 / 상체 이미지(가슴) / 혈흔 이미지 / 수영복 이미지 / 세부 정책 기준.

**출처**
- https://help.crack.wrtn.ai/guide/user/tutorial/character/1 (캐릭터 설정: PNG/JPG/WebP 5MB)
- https://help.crack.wrtn.ai/guide/user/tutorial/story/5 (미디어 탭: 형식·용량·배치표·1,600장)
- https://help.crack.wrtn.ai/guide/user/tutorial/image , https://help.crack.wrtn.ai/guide/user/tutorial/image/4 (이미지 생성 튜토리얼, 빌더 활용)
- https://help.crack.wrtn.ai/oppolicy (운영정책 이미지 규정)
- https://help.crack.wrtn.ai/crackguide/character (가이드 목차: 실시간 상황 이미지, 규정 가이드)
- https://crack.wrtn.ai/announcement/6889cb84ad7a69f4948cc37f (프로필 이미지 규정 강화 공지, 본문 로그인 필요)
- https://crack.wrtn.ai/announcement/6867395367d67e8be6242f47 (운영정책 개정: 캐릭터 생성 정책 구체화)
- https://crack.wrtn.ai/announcement/69f30d272fb890079879faf0 (상황 이미지 시스템 개편, 본문 로그인 필요)
- https://crack.wrtn.ai/announcement/69119449f7af6377f239f90d (이미지 보관함)
- https://x.com/crack_ai_/status/1972642927668257195 (이미지 생성 기능 리뉴얼 업데이트 노트)
- https://apps.apple.com/dm/app/id6740223370 , https://play.google.com/store/apps/details?id=com.wrtn.character (앱 소개·업데이트 노트)

### 1-2. 케이브덕

**사용처** [공식]
- **대표 이미지**: 채팅·스냅샷의 기준 이미지. 제작자 설정으로 앨범의 다른 이미지를 기준으로 지정 가능(나무위키). 규격(px/용량)은 공개 문서에 없음 → **미확인(로그인 후 제작 화면에서 확인)**.
- **앨범 이미지(미디어)** = 흔히 말하는 '이미지 표정/상황 이미지' 기능
  - 업로드하면 **키워드가 자동 부여**되고, 대화 맥락에 맞는 키워드의 이미지가 출력됨.
  - 키워드는 간결·명확·다양하게. 같은 상황 여러 장이면 `smile1, smile2`가 아니라 **`smile`로 통일** → 그중 1장이 랜덤 출력. `random`처럼 상황 특정이 안 되는 키워드는 오동작.
  - **100장 초과 시** 대화 중 이미지가 올바르게 표시되지 않을 수 있음.
  - 금지 이미지로 분류되면 업로드 불가 → '이미지 재분류 신청'으로 관리자 확인 요청.
  - 이미지별 **잠금** 설정 가능: 유저가 500윙으로 구매, 그중 250윙이 제작자 인센티브.
  - 앨범용 AI 이미지 생성: **10윙/장**, 구독(케덕 플러스) 시 무료.
  - 가리기 기능: [가리기] 버튼 자동 마스킹(베타), 펜 가리기(일반 제작자는 게시 불가 판정 이미지에서만, 공식 크리에이터는 전부). 실사 기반 이미지에는 **AI 생성물 표기** 기능(오인 가능성 시 관리자 강제 ON).
- **에피소드 시작 장면 이미지**: 에피소드의 시작 장면에 이미지 삽입 가능.
- **스냅샷**: 답변 우측 하단 카메라 아이콘 → 현재 상황·감정·의상을 분석해 장면 삽화 생성, 캐릭터 앨범 자동 저장. 생성 모델로 **Seedream** 선택 가능. 플레이어는 배경 생성·다중 이미지 답변에 쓰이지 않도록 특정 앨범 이미지를 제외 가능. [커뮤니티] 최근 4개 대화 반영, 그림체는 대표 이미지 영향이 가장 큼(2D 대표 이미지면 반실사 페르소나를 넣어도 2D로 나옴), 페르소나 이미지가 있으면 대화보다 이미지를 따름, 배경 이미지는 반영 안 됨, 글자는 깨짐.
- **다중 이미지 포함 답변**: 모델 옵션 토글. 답변 중간에 상황별 이미지를 여러 장 삽입. 고급 모델 전용(Gemini 3.1 Pro 궁합 최고라고 소개). (나무위키)
- **사용자 별도 설명(소개 페이지 꾸미기)**: 마크다운·HTML 가능, 최대 15,000자(이미지 주소 포함). 프롬프트에는 미포함 → 소개 페이지에 추가 일러스트/배너 삽입 용도. [공식]

**아트 스튜디오(내장 이미지 생성)** [공식]
- 모델: **Quill10-Anime / Quill10-Semi**(19세 이상, NSFW 가능, 성인 인증 필요), **Quill-Classic-M / F / SRM / SRF**(노골적 NSFW 불가).
- 비율 **2:3 / 1:1 / 16:9**, 1~4장, 인물 구성 선택. 자연어 문장 권장(태그 나열도 가능), 영어 외 언어는 품질 저하. '다듬기'(프롬프트 자동 보정), @단축어, 내 프롬프트 저장.
- 수정: **이미지 편집(원본 인물 유지하며 의상·배경·분위기 변경)**, **카메라 앵글 변경**, **민감부위 수정**(흰색 가림). 원본은 아트 스튜디오 생성물·이전 레퍼런스·업로드 중 선택(업로드는 사용 권리 필요).
- 비용 단위 윙, 금액은 '만들기' 버튼에서 확인(이벤트로 변동) → 구체 금액 **미확인**. 생성·수정·업로드·다듬기 각각 계정별 일일 한도(KST 09:00 초기화).
- 갤러리 공유 시 NSFW는 전원 성인 외형 + 성기·음모·항문 **불투명 유색 가림**(모자이크·블러·시스루 불가).

**이미지 정책** [공식, 캐릭터 제작 규정]
- 대표·앨범·소개란 공통: 불쾌감 유발 금지. **실사 또는 실존 인물로 보일 수 있는 이미지는 "AI로 제작된 이미지임"을 설명 또는 이미지 내에 명시**. 성적 행위·암시(표정·자세 포함) 금지. 수영복·운동복 등 일반 노출은 허용, 특정 부위 강조·유혹 연출은 제한.
- 언세이프 대표 이미지: 미성년 외형이면 제한(설정상 성인이어도). **치비(SD)** 이미지는 소개 페이지 장식·굿즈 등 비성적 용도로는 허용. 성관계 묘사·성기 접촉·X-ray·여성 유두 노출 불가.
- 언세이프 앨범 이미지: 성기·음모·항문·인접부 유색 가림(모자이크·블러·시스루·피부색 불가). 성인 용품·촉수 가림 기준 별도.
- 미성년 외형: 교복·학생복·교실/학교 배경·전반적 미성년 분위기는 나이를 성인으로 적어도 불가. 대학생+교실은 성인 외형·설정 명확히. 과거 시점 학교 배경 불가. 인간 캐릭터의 어린 시절·육아 설정 불가.
- 실존 인물: 조항 간 불일치(한 곳은 언세이프 불가, 다른 곳은 전체이용가+수익화 제한이면 가능) → 고객센터 확인 권장.
- **타인 저작권 관련 캐릭터는 '수익화 제한' 옵션 필수**. 저작권자 신고 시 안내 없이 비공개.
- 크리에이터 프로필(이미지·소개·링크)은 세이프티 기준, 위반 시 사전 안내 없이 초기화.

**출처**
- https://docs.caveduck.io/ko/articles/-%EC%BA%90%EB%A6%AD%ED%84%B0-%EA%B8%B0%EB%B3%B8-%EC%A0%9C%EC%9E%91-%EB%B0%A9%EB%B2%95-183ad6c3 (캐릭터 기본 제작 방법: 앨범 이미지·키워드·100장·10윙·500윙)
- https://docs.caveduck.io/ko/articles/-%EC%95%84%ED%8A%B8-%EC%8A%A4%ED%8A%9C%EB%94%94%EC%98%A4-%EC%9D%B4%EC%9A%A9-%EA%B0%80%EC%9D%B4%EB%93%9C-b98c3d54 (아트 스튜디오)
- https://docs.caveduck.io/ko/articles/-%EC%BA%90%EB%A6%AD%ED%84%B0-%EC%A0%9C%EC%9E%91-%EA%B7%9C%EC%A0%95-5da6343e (캐릭터 제작 규정)
- https://docs.caveduck.io/ko/articles/-%EC%82%AC%EC%9A%A9%EC%9E%90-%EB%B3%84%EB%8F%84-%EC%84%A4%EB%AA%85-%EA%B0%80%EC%9D%B4%EB%93%9C-97f264da (사용자 별도 설명)
- https://namu.wiki/w/CAVEDUCK (스냅샷·Seedream·다중 이미지·가리기·AI 표기)
- https://www.postype.com/@untitled-record/post/20400359 [커뮤니티] 스냅샷 테스트
- https://arca.live/b/caveduck/94638883 [커뮤니티] 초보자용 제작 팁(403으로 본문은 검색 요약만 확인)
- https://gall.dcinside.com/mgallery/board/view/?id=bigorismallori&no=302 [커뮤니티] 소개 페이지 HTML 꾸미기

### 1-3. 베이비챗

**사용처·규격** [공식]
- **프로필**: AI 생성 시 **1:1** 권장. 업로드 규격은 문서에 없음 → 미확인.
- **캐릭터 에셋(감정 이미지)**: 최대 **100개**, 권장 **512×768px (2:3)**. 직접 업로드 또는 AI 생성, 일괄 업로드 가능. 대표 1장 외 이미지마다 **공개/비공개**(스포일러 이미지는 비공개 권장).
- **상황·배경 이미지**: **16:9** 권장(AI 생성 공지).
- **호출 방식(2026 '이미지 출력 방식 업데이트')**: 기존 한글 키워드 `img:[item]` → **이미지 코드(Slug)** `img:[slug]`. 시스템이 이미지마다 코드를 자동 생성·1:1 매핑(예: "웃는 비비" → `xvz18 – 웃는 비비`, 모델은 `img:[xvz18]`로 호출). 의미 없는 식별자라 LLM 문맥 오염이 적음. 멀티 이미지 기능을 켠 채팅방에서 자동 적용. 프롬프트에 구형 `img:[item]`을 직접 썼다면 수정 권장. 코드는 AI 답변 '수정' 화면과 캐릭터 생성/수정 창에서 확인.
- **AI 이미지 생성(2026-09 오픈 공지)**: **130프로챗/장**(2026-09 한정 65), 실패·안전정책 제한 시 환불. 스타일 6종 **로판 / 청량 / 동양화 / 애니 / 순정 / 카툰**. 비율 1:1 / 4:3 / 3:4 / 16:9 / 9:16. 성별 선택, 1~4장. **레퍼런스 이미지**(기기 업로드 또는 AI 라이브러리, 얼굴·배경 참고 → "같은 얼굴로 표정만 바꾼 시리즈" 제작 가능), **변형(i2i)**. 프롬프트 최대 1,000자, 자동 생성 버튼(캐릭터·포즈·의상·액세서리 조합). 성별·스타일 변경 시 프롬프트 초기화 주의. 경로: 홈 > MY > AI 이미지 생성 / 캐릭터 제작 > 프로필·캐릭터 에셋 > AI로 생성.
- **외부 이미지** [커뮤니티, 디시 바베챗 갤러리]: 마크다운 `![](URL)`로 외부 호스팅 이미지 호출. imgur(고수위 검열), imgbb(다이렉트 링크, 느림), itimg(유료, webp 변환, 10MB면 1024² webp 약 200장). 프롬프트에 [이미지규칙]·출력형식·코드 분류표(캐릭터×상황 마크다운 표)·[CRITICAL: 코드 임의 생성 금지]를 두고, 특수 상황 이미지는 **로어북**으로 분리 호출해 메인 프롬프트 절약. 내부 에셋과 외부 이미지는 혼용하지 말 것.

**이미지 정책** [공식, 캐릭터 제작 정책]
- 공통: 타인 저작권·초상권 침해 이미지 금지. **실제 인물 사진, 딥페이크, 하이퍼리얼리즘 등 실사로 오인될 이미지 금지**. 실존 인물 성적 묘사 금지. 단체 표장 금지. 아동·청소년 또는 명백히 미성년으로 보이는 인물(교복 등) 성적 묘사 금지. 유명 캐릭터 무단 사용·변형 금지(영감은 허용, 복제 불가).
- 세이프티(14세+): 부분 노출까지, 성행위 묘사·옷 위 성기 형태·여성 유두 노출 금지. 선정적 이미지를 세이프티로 잘못 지정하면 차단.
- 민감 캐릭터(세이프티 OFF 전용): 기본 이미지에 과도한 음란 불가. 성기·음모·항문은 **불투명 처리**(검정/흰색 권장), 시스루는 바깥 윤곽만. 교복+노출은 성인 명시해도 제재 → 성인임이 분명한 제복 권장.

**출처**
- https://docs.channel.io/babechat/ko/articles/%EB%82%98%EB%A7%8C%EC%9D%98-AI-%EC%BA%90%EB%A6%AD%ED%84%B0-%EC%A0%9C%EC%9E%91%ED%95%98%EA%B8%B0-b8943f55 (제작 가이드: 100개, 512×768)
- https://docs.channel.io/babechat/ko/articles/%EC%9D%B4%EB%AF%B8%EC%A7%80-%EC%B6%9C%EB%A0%A5-%EB%B0%A9%EC%8B%9D-%EC%97%85%EB%8D%B0%EC%9D%B4%ED%8A%B8-%EC%95%88%EB%82%B4-c118b30f (Slug 방식)
- https://babechat.ai/notice/3cebfad922a780318debf293bdb649af (AI 이미지 생성 기능 오픈 안내)
- https://babechat.ai/policy/character-creation-policy (캐릭터 제작 정책)
- https://gall.dcinside.com/mgallery/board/view/?id=babechat&no=4416 [커뮤니티] 외부이미지 사용법
- https://gall.dcinside.com/mgallery/board/view/?id=babechat&no=5629 , https://m.dcinside.com/board/babechat/1192 [커뮤니티] 제작 필독·외형 설정

### 1-4. 제타 (스캐터랩)

**사용처·규격** [공식]
- **대표(프로필) 이미지**: 앱 내 AI 생성 또는 직접 업로드. **2025-11-25 제작 업데이트로 대표 이미지 비율 1:1 → 3:4**(홈·랭킹·상세 노출 영역 3:4). 기존 1:1은 상세 페이지에서만 1:1, 그 외 영역은 **좌우가 잘린 3:4**로 표시. px·용량은 공개 문서에 없음 → **미확인(로그인 후 제작 화면에서 확인)**.
- **커버 이미지**: 최대 **10장**(선택). 미등록 시 첫 캐릭터 대표 이미지가 커버로 노출.
- **캐릭터별 이미지**: 캐릭터당 최대 **5장**(표정·의상 등 여러 모습).
- **생성 기록**: 앱 내 생성 이미지는 별도 저장 없이 **90일 자동 보관**(기존 라이브러리·히스토리 종료).
- **스냅샷**: 캐릭터 프로필+대화 기반 이미지 생성, **15피스**(출시 초 50피스), 부적절 시 실패·환불. 결과 그림체가 "ChatGPT 그림체와 비슷하다"는 이용자 평(모델명 비공개). [커뮤니티] 업로드 프로필로도 동작하지만 비인간·실사 프로필은 동작 안 함. 비인간/풍경 키워드에도 인간이 나오는 등 오류 보고.
- **배경 이미지 생성**(제타패스 전용) → **2026-06-12 삭제**. (나무위키)
- **AI의 프로필 인식**: 외형을 안 적어도 프로필 사진으로 외모를 파악하지만, 식별이 어려운 그림은 오인식(흰머리 캐릭터가 빨간 왕좌에 앉으면 빨간 머리로 인식). → 프로필은 머리색·눈색이 또렷한 단순 배경 권장.
- **대화 프로필(유저 페르소나)**: 프로필 이미지+이름+짧은 소개+설명(프롬프트). 크리에이터 추천 대화 프로필은 선택 사항(2025-10 변경). [커뮤니티] 제타 갤러리에 '대화 프로필 실루엣 이미지', '[V2] 유저프로필 날먹 이미지' 공유 글 존재.

**이미지 정책**
- [공식, 일본어 공지] **실사와 유사한 AI 생성 이미지 금지**, 위키 등 외부 사이트 내용 그대로 인용 금지, 연예인·유튜버·애니 캐릭터 등 타인 저작권 침해 캐릭터·사진 금지, **"개인 사용 자유"로 표시된 외부 이미지도 제타에서 쓰려면 별도 허가 필요**.
- [공식] 2026-01-23 공지: 서비스 내 제작·사용 가능한 캐릭터를 **이용자가 직접 만든 오리지널 캐릭터로 한정**. 권리자 요청 시 사전 예고 없이 플롯 삭제·이용 제한.
- [나무위키] 저작권 침해 이미지 사용 시 사진 삭제 + 경고장, 연속 2회 누적 시 1일 정지.
- 신고 창구: copyright@zeta-ai.io.

**출처**
- https://zeta-ai.io/en/announcements/6766 (2025-11-25 제작 업데이트: 3:4, 커버 10장, 캐릭터 5장, 90일 보관)
- https://zeta-ai.io/en/announcements/4720 (대화 프로필 업데이트)
- https://namu.wiki/w/zeta(%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98) (스냅샷 15피스, 배경 생성 종료, 경고 체계)
- https://x.com/zetaAI_/status/1858320821347078242 , https://x.com/zetaAI_/status/1840777318861795533 (저작권 조치 안내)
- https://www.topcelev.co.kr/news/articleView.html?idxno=4055 (니지산지 플롯 삭제, 2026-10)
- https://note.com/fond_clam2634/n/n32188962fa92 (니지산지 캐릭터 삭제 해설, 2026)
- https://aidev.co.kr/chatbots/16061 [커뮤니티] 제타 vs 아이라 vs TonesAI 이미지 생성 비교
- https://gall.dcinside.com/mgallery/board/view/?id=zetam&no=562449 [커뮤니티] 제작 정보글 모음

### 1-5. 플랫폼 공통 — AI 생성 이미지 허용 여부와 공통 금지선

- 4개 플랫폼 모두 **AI 생성 이미지를 허용**하며, 자체 생성 기능까지 제공. 다만 **케이브덕은 실사풍이면 AI 제작 표기 의무**, **크랙·베이비챗·제타는 실사/실존 인물 유사 이미지 자체를 제한**.
- 공통 금지: 실존 인물(아이돌·스트리머 포함) 실사·유사 이미지, 미성년 외형(교복·학교 배경이 대표적 신호), 타 작품 공식 일러스트 무단 사용, 성기 등 직접 노출(언세이프라도 불투명 가림).
- 2차 창작 허용 폭: 크랙(원작 가이드라인 준수+세이프티만) > 케이브덕(수익화 제한 필수) > 베이비챗(유명 캐릭터 무단 사용·변형 금지) > 제타(2026년부터 오리지널 한정).

---

## 2. 2026년 기준 이미지 생성 도구 비교

### 2-1. 비교표

| 도구 | 2026-10 현재 버전 | 캐릭터 일관성 | 한국 웹툰/애니 품질 | 비용 | 상업 이용 | NSFW | 속도 | 비고 |
|---|---|---|---|---|---|---|---|---|
| **Nano Banana 계열(Google)** | Nano Banana 2.1(`gemini-nano-banana-2.1`), 2 Lite(`gemini-3.1-flash-lite-image`), 2(`gemini-3.1-flash-image`), **Pro**(`gemini-3-pro-image`), 레거시 2.5 Flash Image [공식] | 상: 캐릭터 레퍼런스 최대 **4장(2.1/3.1 Flash) / 5장(Pro)**, 오브젝트 최대 14장(Lite)/10/6(Pro), 스타일 레퍼런스 3장(Pro). 대화형 다중 턴 편집 [공식] | 상: 깔끔한 애니 선화·비율 유지 평 [커뮤니티]. **한글 텍스트 렌더링 우수**(Pro) | API Pro 약 $0.134/장(1K·2K), $0.24(4K), Batch 50% [3rd]. Gemini 앱 무료 사용자도 생성 가능(1K) / Google AI Pro 구독 시 Pro·2K/4K | 가능(Google 약관), **SynthID 워터마크 전 이미지 삽입** [공식] | 불가(엄격 필터, 격한 표정·혀 내밀기도 걸림 [커뮤니티]) | 빠름(Flash) / 보통(Pro) | 투명 배경 요청 시 체크무늬를 '그려' 버림 → 단색 배경 후 누끼 [커뮤니티] |
| **GPT Image(OpenAI)** | gpt-image-1.5(2026-12-01 퇴역 예정 [3rd]), **gpt-image-2**(2026-04, thinking 모드, 레퍼런스 최대 8장 [3rd]), GPT Image 2.5(2026-09 [Wikipedia]) | 중상: 다중 레퍼런스 연속성 지원 | 중: 애니는 다소 '회화적' 질감 평 [커뮤니티]. 제타 스냅샷이 "ChatGPT 그림체"로 체감되는 사례 | 1.5: 1024² low/med/high ≈ $0.009/0.034/0.133; image-2 ≈ $0.006/0.053/0.211 [3rd]. ChatGPT Plus $20 | 가능(출력물 소유권 사용자) | 불가 | 보통(thinking 시 느림) | 생존 작가 이름 차단, 스튜디오풍은 허용, 특정 저작권 캐릭터 거부 |
| **Midjourney** | **V8.2 기본**(2026-07-24), V8.1(2026-06-10) [공식]. **Omni Reference(--oref)는 V7 전용**, V8.2는 **Edit Model(레퍼런스 최대 4장)**이 cref/oref 대체 [공식 docs] | 중: V7 oref는 3~5컷부터 드리프트 보고. Niji 7(2026-01-09)은 cref 미지원 | 상(니지 계열 스타일) | Basic $10 / Standard $30 / Pro $60 / Mega $120 | 유료 구독자 가능(연매출 $1M 이상 기업은 Pro 이상 — 약관 확인) | 불가 | 빠름 | oref 사용 시 GPU 2배 [3rd] |
| **Stable Diffusion/ComfyUI – 애니 체크포인트** | **Illustrious XL**(v0.1~v2.0, v1.0 네이티브 1536, LoRA 생태계 최대), **NoobAI-XL**(Illustrious 기반, Danbooru+e621 약 1,300만장), **Animagine XL 4.0**, **WAI-illustrious-SDXL**(Civitai 인기), Pony V6(SDXL)/V7(AuraFlow) | 상(LoRA·IP-Adapter·시드 고정으로 가장 정밀) | 상(danbooru 태그로 애니/만화 제어 최적, 웹툰풍 LoRA 다수: 예 'My Life As A Loser Style', 'Reality Quest' 등 Illustrious LoRA) | 로컬 무료(GPU 필요: SDXL은 RTX 20번대도 가능 [커뮤니티]) / 온라인: Tensor.Art 100크레딧/일, Civitai Buzz, SeaArt, PixAI | **모델별 상이**: Animagine XL 4.0(CreativeML OpenRAIL++-M, 상업 OK) / NoobAI(Fair AI Public License 수정판, **출력물 상업 이용 금지**) / Illustrious(버전별 상이, v0.1 Fair AI PL) / 파생 모델은 별도 약관 | 가능(로컬·일부 사이트) | 빠름(로컬) | Tensor.Art는 2025년 말 SFW 전환(성인은 TensorHub 유료) [3rd] |
| **신형 범용 오픈/상용 모델** | **Flux.2**(klein/dev 오픈, Flex 상용), **Z-Image**(Apache 2.0, Turbo 2025-11-26 / Base 2026-01-27, 일러스트 강점·실사 중심), **Qwen-Image 2.x**(2.0 Apache 2.0 vs 2.1 Research License로 자료 상충), **Seedream 5.0 Pro**(ByteDance 상용, 2026-06/07, 케이브덕 스냅샷 옵션), **HunyuanImage 3**(Apache 2.0) | 중~상(Flux Kontext/Qwen-Image-Edit 계열 편집) | 중(범용 모델이라 '스타일라이즈드 일러스트'는 SDXL 애니 계열에 비해 약하다는 평) | 오픈 가중치 무료 / API 종량 | 라이선스별 확인 | 모델별 | Z-Image Turbo 매우 빠름 | 한글 텍스트는 Qwen-Image가 강점 |
| **NovelAI Diffusion V4.5 (+V5)** | V4.5(Precise Reference 지원), V5(초기엔 Vibe Transfer·Precise Reference 미지원 [3rd]) | 상: **Precise Reference**(Character/Style/Character&Style, +5 Anlas, strength·fidelity 조절, 다중 캐릭터 레퍼런스는 섞임), Vibe Transfer와 동시 불가 [공식] | 상(애니 특화, danbooru 태그) | Tablet $10 / Scroll $15 / **Opus $25**(일반 크기 ≤28스텝 무제한), 가입 시 30장 무료(1회) | **상업 이용 제한 없음**(NovelAI 명시) | 가능 | 빠름 | 레퍼런스 시트 태그: `multiple views, turnaround, reference sheet, no text, expressions` |
| **Leonardo.ai** | v4(2026) | 중: Character Reference 1장, 신형 Omni Image Reference 최대 6장 [3rd] | 중(Anime 계열 모델 보유) | 무료 150토큰/일(공개 생성), Essential $12 / Premium $30 / Ultimate $60 | 유료 플랜 포함; 무료 티어는 자료 상충(비독점 상업 라이선스 vs 불가) → 약관 확인 | 제한적 | 빠름 | 비인간 캐릭터에 약함 |
| **국내 툴** | 뤼튼 이미지 생성(2023 Stability 기반 무제한 무료 → 2026 모델 미확인), **크랙 내장 생성**(있음, 세이프티 한정), **케이브덕 아트 스튜디오**(Quill, 19+ 모델 NSFW 가능), **베이비챗 AI 생성**(130프로챗, 6스타일, 레퍼런스·i2i), **제타 스냅샷**(15피스), 카카오 칼로(2023 공개, 2024 이후 현황 미확인), 라이너(이미지 생성 관련 공개 자료 없음 → 미확인), 미리캔버스 GPT 애니 캐릭터 생성기(일일 무료 크레딧), 캐럿(프로필 AI 생성), 인터랙트(캐릭터챗 실시간 웹툰 컷) | 플랫폼 내장은 레퍼런스 기능이 있는 베이비챗·케이브덕이 유리 | 베이비챗 '로판/순정/동양화' 스타일이 한국 장르에 직결 | 플랫폼 재화 | 플랫폼 내 사용 전제 | 케이브덕만 공식 NSFW 모델 | 보통 | 플랫폼 정책 필터가 선적용되어 반려율 낮음 |

### 2-2. 선택 가이드(요약)
- **정책 안전한 프로필·상황 이미지 다량 + 한글 텍스트**: Nano Banana Pro(또는 2.1). 워터마크·NSFW 불가는 감수.
- **애니/웹툰 스타일 정밀 제어 + 표정 세트 대량**: Illustrious/NoobAI 계열(ComfyUI 또는 Tensor.Art). 상업 이용 시 Animagine 4.0 또는 라이선스 확인된 Illustrious 파생 사용.
- **언세이프(성인) 캐릭터 앨범**: NovelAI Opus(상업 OK, NSFW OK) 또는 케이브덕 Quill10 계열(플랫폼 내에서 바로 가림 처리까지).
- **브랜드/배경·오브젝트 중심 고급 컷**: Midjourney V8.2 + Edit Model, 또는 Flux.2.

**출처**
- https://ai.google.dev/gemini-api/docs/image-generation (모델명·레퍼런스 한도·해상도·SynthID)
- https://www.pixmind.io/posts/nano-banana-pro-pricing-guide-2026 , https://www.aifreeapi.com/en/posts/nano-banana-pro-pricing (Pro 단가)
- https://invideo.io/blog/best-ai-image-model-comparison/ , https://www.vidguru.ai/blog/nano-banana-pro-vs-gpt-image-1-5-comparison.html , https://aigf.love/blog/gpt-image-2-vs-nano-banana-ai-characters/ (NB Pro vs GPT Image 비교)
- https://aireiter.com/blog/gpt-image-1-5-api-pricing , https://costgoat.com/pricing/openai-images , https://dev.to/tokenmixai/gpt-image-2-api-developer-guide-pricing-thinking-mode-and-production-integration-2026-28p5 , https://en.wikipedia.org/wiki/GPT_Image
- https://the-decoder.com/openai-blocks-artist-names-in-image-prompts-but-allows-studio-styles/ (OpenAI 스타일 정책)
- https://updates.midjourney.com/v8-1-is-now-the-default-model/ , https://docs.midjourney.com/hc/en-us/articles/32199405667853-Version , https://blakecrosley.com/guides/midjourney , https://aivideobootcamp.com/blog/midjourney-complete-guide-2026/
- https://insiderllm.com/guides/best-anime-stylized-checkpoints-local-image-generation/ , https://localaimaster.com/blog/best-local-anime-image-model , https://offlinecreator.com/civitai-anime-models , https://morphic.com/resources/list/best-ai-models-for-anime
- https://note.com/ai_image_journey/n/n4982b466f663 , https://civitai.com/articles/18619/what-the-license , https://aiofm.info/en/guides/pony-vs-illustrious (라이선스)
- https://huggingface.co/xcreates/Z-Image-Turbo/blob/main/README.md , https://gigazine.net/gsc_news/en/20260128-z-image-image-generation-ai/ , https://www.gradually.ai/en/ai-image-model-comparison/seedream-5-pro-vs-qwen-image-2-pro/ , https://apidog.com/blog/hunyuan-vs-seedream-comparison-2026/ , https://www.eesel.ai/blog/qwen-image-2-1-alternatives
- https://docs.novelai.net/en/image/precisereference/ , https://arcanumrpgs.com/blog/novelai-pricing/ , https://namu.wiki/w/NovelAI/%EC%9D%B4%EB%AF%B8%EC%A7%80%20%EC%A0%9C%EB%84%A4%EB%A0%88%EC%9D%B4%ED%84%B0 , https://novelai.net/
- https://pricepertoken.com/leonardo-ai-pricing , https://techsifted.com/guides/leonardo-ai-pricing-2026/
- https://tooldirectory.ai/compare/civitai-ai-art-community-vs-tensor-art , https://blog.picassoia.com/tensor-art-vs-civitai-best-stable-diffusion-platform
- https://wrtn.io/news/%EB%A4%BC%ED%8A%BC-gpt-4-%EB%8C%80%ED%99%94-%EA%B8%B0%EB%8A%A5%EA%B3%BC-ai-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EC%83%9D%EC%84%B1-%EB%AC%B4%EC%A0%9C%ED%95%9C-%EB%AC%B4%EB%A3%8C-%EA%B3%B5%EA%B0%9C , https://namu.wiki/w/%EB%A4%BC%ED%8A%BC (뤼튼)
- https://www.miricanvas.com/features/ko/gpt-anime-character-maker , https://interact.do/app , https://docs.channel.io/carat/ko/articles/AI-%EC%B1%84%ED%8C%85-%EC%BA%90%EB%A6%AD%ED%84%B0%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EB%A7%8C%EB%93%9C%EB%82%98%EC%9A%94-762404c3

---

## 3. 캐릭터 일관성(동일 인물 여러 장) 기법

### 3-1. 마스터 레퍼런스와 캐릭터 시트
- **마스터 레퍼런스 1장을 먼저 확정**: 정면, 균일 조명, 중립 표정, 단순 배경. [커뮤니티·3rd 공통]
  - Nano Banana 실전 팁(디시 특이점 갤러리): **3:4, 2K, 정면 하프샷(상반신)** 기본. 풀바디는 얼굴 해상도 부족, 클로즈업은 체형 정보 부족. 얼굴이 작을수록 모델이 임의 창작.
  - NovelAI Precise Reference 권장: 전신·서 있는 중립 포즈·단순 배경 + 모서리에 얼굴 확대 크롭, 1024×1536 / 1472×1472 / 1536×1024 중 하나, 캔버스에 캐릭터를 최대한 크게. 스케치·회화풍 레퍼런스는 읽기 어려움.
- **캐릭터 시트는 필요할 때만**: 여러 각도 사진을 한꺼번에 넣으면 모델이 1장만 골라 쓰거나 혼란 → 특정 각도(옆얼굴 등)가 안 잡힐 때만 턴어라운드 시트를 추가. [커뮤니티·3rd]
- **고정 텍스트 프로필('설정 카드')**: 나이감·머리(색/길이/스타일)·눈색·피부·의상·시그니처 소품·아트 스타일·팔레트·"바꾸지 말 것" 항목을 한 블록으로 만들어 **모든 생성에 그대로 반복**. 장면(포즈·배경·소품·카메라 거리)만 변수로 교체. 흔들리면 스타일 단어를 더하지 말고 고정값을 프롬프트 앞으로.
- **베스트 결과를 다음 레퍼런스로 승격**: 시트에서 가장 잘 나온 1장을 새 마스터로 교체(세대 교체 시 드리프트 주의: 원본 마스터는 보존).
- **'진단서' 루프**(커뮤니티): 어긋난 부분을 포토샵/액화/보정앱으로 직접 고쳐 다시 레퍼런스로 투입 → 반복. 같은 세션에서 인물·구도를 크게 바꾸면 첫 입력의 영향이 남으므로 **새 세션**으로.

### 3-2. 도구별 일관성 기능
| 기능 | 도구 | 핵심 |
|---|---|---|
| 멀티 레퍼런스 편집 | Nano Banana 2.1/Pro | 캐릭터 레퍼런스 4~5장 + 오브젝트/스타일 레퍼런스 분리 입력, 대화형 다중 턴(`previous_interaction_id`) [공식] |
| Precise Reference | NovelAI V4.5 | Character / Style / Character&Style, strength(너무 높으면 표정·포즈까지 복제)·fidelity(프롬프트 덮어쓰기 저항) 조절, +5 Anlas, 인페인팅과 병용 [공식] |
| Omni Reference / Edit Model | Midjourney V7 / V8.2 | V7 `--oref --ow`, V8.2 Edit Model 레퍼런스 4장 [공식] |
| Character/Omni Image Reference | Leonardo | 1장 / 최대 6장 [3rd] |
| 레퍼런스 생성 | 베이비챗 AI 생성, 케이브덕 아트 스튜디오 '이미지 편집' | 플랫폼 내에서 같은 얼굴로 표정·의상·배경만 교체 [공식] |
| IP-Adapter / ControlNet | ComfyUI(SDXL·Illustrious) | NoobAI/Illustrious 전용 IP-Adapter 워크플로우(Civitai) 존재. 얼굴 weight 0.7~0.85, end 0.8~0.9 권장. ControlNet(OpenPose/Depth)로 포즈 고정. **항상 같은 레퍼런스 파일**을 투입 [3rd] |
| PuLID / FaceID | ComfyUI | 실사 얼굴 정체성에 강함(애니는 IP-Adapter+LoRA 조합이 일반적) |
| LoRA 학습 | kohya/OneTrainer 등 | 시트 생성 → 10~20장 크롭 → 캐릭터 LoRA. 잘 된 LoRA는 IP-Adapter 불필요. 표정·의상 태그 캡션을 꼼꼼히 |
| 시드 고정 | SD 계열 | 동일 시드+동일 프롬프트 블록에서 **표정 태그만** 교체. 단어 하나만 바꿔도 결과가 흔들릴 수 있으니 레퍼런스(IP-Adapter)와 병행 |

### 3-3. 표정 세트(기쁨/분노/슬픔/부끄러움 등) 일괄 생성 워크플로우
공통 표정 목록(플랫폼 자동 전환용 키워드와 1:1 대응시키기): `neutral, smile, grin, laugh, blush/embarrassed, angry, sad, crying, surprised, smug, pout, nervous/sweat, scared, sleepy, serious`.

**A. Nano Banana(가장 간단, 세이프티용)**
1. 마스터 하프샷 1장 업로드.
2. 프롬프트(한국어 OK): "이 캐릭터의 얼굴·머리·의상·조명·카메라 구도를 그대로 유지하고 **표정만** '부끄러워 얼굴이 빨개진 표정'으로 바꿔줘. 배경은 단색 #00FF00."
3. 표정당 1장씩 생성(3×3 그리드로 한 번에 뽑는 방식도 가능하나 분할 시 얼굴 해상도 저하 → 1K 초안 → 선별 → 업스케일).
4. 주의: 격한 표정·혀 내밀기·입 안 물체는 필터에 걸리는 사례. [커뮤니티]

**B. NovelAI V4.5**
- 마스터를 Character Reference로 넣고 `expressions, multiple views, reference sheet, no text` + 개별 표정 태그 → 시트 1장 생성 후 분할. 또는 Precise Reference strength를 낮추고 표정 태그만 바꿔 개별 생성. [공식 문서 태그]

**C. ComfyUI(Illustrious/NoobAI)**
- 베이스 프롬프트(설정 카드 태그) + IP-Adapter(마스터 1장) + 시드 고정 → 표정 태그 9종을 배치(Prompt Scheduling / 문자열 리스트 노드)로 돌림. 필요 시 ControlNet OpenPose로 머리 각도 고정. 배경 태그 `simple background, green background`.

**D. 플랫폼 내장**
- 베이비챗: 캐릭터 에셋 > AI로 생성 > 레퍼런스에 마스터 투입 → "표정만 변경" 시리즈. 2:3 비율 선택(512×768 권장과 일치).
- 케이브덕: 아트 스튜디오 > 이미지 편집(원본 인물 유지) → 앨범 업로드 시 키워드 `smile`, `angry`… 통일.

### 3-4. 배경 분리/투명 배경
- Nano Banana에 "투명 배경"을 요청하면 **체크무늬를 그려 넣는** 사례 → **순녹색/마젠타 단색 배경**으로 생성 후 크로마키 또는 `rembg`(ISNet/BiRefNet) 로 누끼. [커뮤니티]
- 로컬: rembg(Python, BiRefNet 모델), Photoshop '피사체 선택', Clip Studio, Photopea(무료 웹), remove.bg. 머리카락 가장자리는 BiRefNet 계열이 우수.
- 베이비챗 2:3 스탠딩, 케이브덕 앨범, 제타 3:4 대표 이미지는 배경 있는 이미지도 무방하므로 투명 PNG는 "표정 차분(差分)만 교체"하거나 웹툰 컷 합성용에 한정해 제작하면 공수 절약.

**출처**
- https://ai.google.dev/gemini-api/docs/image-generation
- https://docs.novelai.net/en/image/precisereference/
- https://gall.dcinside.com/mgallery/board/view/?id=thesingularity&no=894307 [커뮤니티] 나노바나나2 팁
- https://sider.ai/blog/ai-image/nano-banana-pro-cheat-sheet-for-character-consistency , https://bananabanana.pro/blog/character-consistent-image-generation , https://lilys.ai/ko/notes/nano-banana-20260127/consistent-character-sheets-nano-banana , https://nanobanana-pro.vip/ko/blog/nanobanana-pro-character-consistency-ip-mascot-batch-workflow/ , https://www.fotor.com/ko/blog/nano-banana-model-prompts/
- https://www.how-toai.com/blog/ai-webtoon-comic-maker-tools-4-comparison-character-consistency-2026 (컷마다 얼굴 바뀌는 문제 6가지 점검·시트 5단계)
- https://civitai.com/models/1466666/noobai-illustrious-ipadapter-workflow , https://www.runflow.io/blog/comfyui-consistent-characters-flux , https://www.apatero.com/blog/comfyui-character-consistency-advanced-workflows-2026 , https://www.media.io/image-tips/comfyui-consistent-characters.html , https://www.sozee.ai/resources/ipadapter-faceid-stable-diffusion-tutorial/
- https://www.ocmaker.ai/ko/ai-anime-generator/expression-sheet-generator (표정 시트 생성기 예)
- https://choojongbum.com/%EB%82%98%EB%85%B8%EB%B0%94%EB%82%98%EB%82%98%EB%A1%9C-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EB%88%84%EB%81%BC%EB%94%B0%EA%B8%B0-%ED%8F%AC%ED%86%A0%EC%83%B5-%EC%97%86%EC%9D%B4-5%EC%B4%88%EB%A9%B4-%EB%81%9D/ , https://cran.r-project.org/package=rembg

---

## 4. 웹툰/만화 컷 제작

### 4-1. 플랫폼별로 '컷'이 들어가는 자리
- **크랙**: 상황 이미지(정방형 기준, 세로로 긴 이미지 비권장) → 세로 스크롤 한 장이 아니라 **컷 단위(1:1 또는 4:5)로 분할**해 배치표에 등록. 첫 인사말에는 구버전 `{{img::}}` 또는 배치표 '인트로' 분류로. 이미지 보관함 해금과 결합하면 "진행할수록 컷이 열리는" 웹툰식 연출 가능.
- **베이비챗**: 상황·배경 16:9 권장, 감정 이미지 2:3. 외부 이미지(`![](url)`)를 쓰면 세로 긴 컷도 삽입 가능하나 내부 에셋과 혼용 금지. [공식/커뮤니티]
- **제타**: 커버 이미지 최대 10장(3:4) → **커버 10장을 인트로 컷 시퀀스로** 구성 가능 [추정]. 캐릭터별 5장은 표정·의상 차분용.
- **케이브덕**: 에피소드 시작 장면 이미지 + 앨범 키워드(`intro`, `prologue` 등) + 소개 페이지 HTML에 외부 이미지 URL로 세로 웹툰 삽입(15,000자 제한에 URL 포함). [공식]

### 4-2. 패널 레이아웃·말풍선·텍스트 합성 도구
- **전통 툴**: Clip Studio Paint(말풍선·집중선·폰트 도구, 웹툰 캔버스 프리셋), Photoshop, Procreate. 레터링·말풍선만 따로: Canva / Adobe Express / 미리캔버스 / Figma / Photopea(무료 웹).
- **AI 올인원(2026)**: Jenova Webtoon Creator(세로 스크롤 전용, 레퍼런스 시트), Comistitch(컷+말풍선+모바일 레이아웃), Dashtoon(그리드 출력→세로 재편집 필요), AI Comic Factory(단일 스트립), Anifusion, OLLI(인스타툰·말풍선 자동), Toonkit(1~4컷), WeToon, 인터랙트(캐릭터챗 대화에 맞춰 실시간 컷). 대부분 제작사 홍보 자료 기반이라 품질은 직접 테스트 필요. [3rd]
- **말풍선 한글**: Nano Banana Pro는 한글 렌더링이 우수해 말풍선까지 한 번에 생성 가능하나 오타·획 깨짐 검수 필수. 소형 로고·긴 문구는 생성 후 디자인 툴에서 후처리가 안전. [커뮤니티/3rd]
- **통용 규격(참고)**: 네이버웹툰식 세로 스크롤은 가로 690~800px, 컷당 세로 1,280px 이하 이미지를 이어 붙이는 방식이 일반적(플랫폼 외부 규격, 캐릭터챗 업로드 시에는 각 플랫폼 비율로 재단).

### 4-3. 세로 스크롤 웹툰 인트로 제작 흐름(권장)
1. **콘티**: 3~6컷 시놉(상황 → 캐릭터 등장 → 유저에게 말 거는 컷). 컷별 카메라 거리(원경→중경→클로즈업)와 대사 1줄.
2. **설정 카드·마스터 레퍼런스**(3장 참조) 확정. 색 팔레트·선 굵기·셀셰이딩 단계 명시.
3. **컷 생성**: 설정 카드(고정) + 컷 변수(포즈/배경/소품/카메라). 같은 툴·같은 모델·같은 시드/레퍼런스. "배경에 읽을 수 없는 글자·다른 인물 넣지 말 것" 명시.
4. **검수 4칸**: 얼굴·헤어 / 의상·주요 색 / 선 굵기·음영 / 소품 형태. 어긋나면 레퍼런스 품질·구도·강도·프롬프트·인물 수·모델 등급 6항목 점검.
5. **말풍선·텍스트 합성**(Clip Studio/Canva/Photopea). 크랙 프로필 이미지 내 비속어·성적 은어 금지 규정 주의.
6. **플랫폼 규격 재단**: 크랙 1:1(5MB, webp 권장), 베이비챗 16:9/2:3(512×768), 제타 3:4, 케이브덕 2:3/1:1. 파일명은 크랙 `분류_상황`, 케이브덕 키워드와 일치.
7. **등록·테스트**: 배치표/키워드/Slug 매핑 후 실제 플레이로 호출 타이밍 확인.

### 4-4. 참고할 만한 크리에이터·사례
- 포스타입 '제작 기록'(케이브덕 스냅샷 테스트+응용법) — 스냅샷으로 상황 컷을 뽑는 조건 실험.
- 디시 바베챗 갤러리 '외부이미지 사용법 정리' — 대형 시뮬레이션용 코드 분류표·로어북 호출 구조.
- 디시 제타 갤러리 '대화 프로필 실루엣 이미지', '[V2] 유저프로필 날먹 이미지' — 유저 프로필용 범용 이미지 공유.
- X @kyodnf — "취미로 AI 이미지를 만들어요. 베이비챗에서 캐릭터 제작" 유형의 이미지 중심 크리에이터.
- 공식 IP 사례: 네이버웹툰 '바이어스'(2026-07, 웹툰 IP 스토리챗), 원스토어 '원챗'(2026-09), 레진 참여 — 원작자 동의 기반 공식 일러스트 활용 모델.
- 디시 '특이점이 온다' 갤러리 나노바나나2 팁 — 하프샷 레퍼런스·한국어 프롬프트·1K→업스케일·ComfyUI 후보정 파이프라인.

**출처**
- https://www.jenova.ai/ko/resources/ai-webtoon-generator , https://www.jenova.ai/ko/resources/cartoon-bubble-text , https://comistitch.com/blog/text-to-webtoon-ai-complete-workflow/ , https://www.comicpad.app/ai-webtoon-maker , https://mangaflow.studio/blog/best-ai-webtoon-generators-2026 , https://olliai.art/ , https://toonkit.io/en/ai-cartoon-maker , https://wetoon.ai/ko , https://interact.do/app
- https://www.how-toai.com/blog/ai-webtoon-comic-maker-tools-4-comparison-character-consistency-2026
- https://allmyuniverse.com/image-prompt-guide-webtoon-cel-shaded-character-scene/ (설정 카드/장면 변수 분리, 4칸 검수)
- https://tilnote.io/en/pages/69ecc74f3f95b06dbd908f8f (웹툰 제작 보조 워크플로우)
- https://www.ajunews.com/view/20261014132831217 (플랫폼·IP 사업자 캐릭터챗 진출)
- https://x.com/kyodnf/status/1937720560307536310 , https://www.postype.com/@untitled-record/post/20400359 , https://gall.dcinside.com/mgallery/board/view/?id=babechat&no=4416

---

## 5. 프롬프트 작성 레시피

### 5-1. Danbooru 태그 체계 기본(Illustrious / NoobAI / Animagine / NovelAI 공통)
- 태그는 `언더스코어_연결`(사이트에 따라 공백도 허용). 순서: **인원·구도(1girl, solo, upper body) → 캐릭터 외형(머리·눈·체형) → 의상·소품 → 표정·포즈·시선 → 배경·조명 → 화풍 → 품질 태그**. 긴 프롬프트일수록 뒤쪽 태그 영향이 약해짐.
- Illustrious 품질 태그: `masterpiece, best quality, very aesthetic, absurdres`(+`newest`). 가이드에 따라 앞 또는 끝에 배치. CFG 4.5~5 권장, Clip Skip 2 권장 가이드 있음. v1.1 이후 부분 자연어 지원(100% 자연어는 비권장).
- **네거티브(Illustrious 계열은 네거티브를 잘 따름)**: `worst quality, low quality, lowres, bad quality, displeasing, very displeasing, bad anatomy, bad hands, extra digits, missing fingers, multiple views, comic, text, watermark, signature, jpeg artifacts`
- **플랫폼 정책용 네거티브(세이프티 프로필)**: `nsfw, nipples, see-through, underwear, cleavage, blood, gore, child, loli, shota, aged_down, school_uniform, realistic, photorealistic, photo`
- **표정 태그(danbooru face tags)**: `smile, light_smile, grin, :d, open_mouth, closed_mouth, laughing, happy / blush, nose_blush, embarrassed, flustered, shy / angry, furrowed_brow, v-shaped_eyebrows, clenched_teeth, glaring / sad, frown, crying, tears, streaming_tears, teary_eyes / surprised, wide-eyed, :o / smug, pout, tongue_out, wavy_mouth, nervous, sweatdrop, scared, expressionless, serious, sleepy, half-closed_eyes, closed_eyes, sparkling_eyes, heart-shaped_pupils / looking_at_viewer, looking_away, looking_to_the_side, head_tilt`
- **의상·장르 태그**: `hanbok, korean_clothes`(한복), `hanfu, chinese_clothes`(무협·중화풍), `ball_gown, off-shoulder_dress, tiara, jewelry, gloves, corset`(로판), `suit, necktie, office_lady, hoodie, school_uniform(주의)`(현대), `armor, cape, sword, katana`(판타지·무협).

### 5-2. 스타일별 태그 프롬프트 예시(Illustrious/NoobAI용, 예시 템플릿)
- **한국 웹툰풍 현대물(남주)**
  `1boy, solo, korean, black hair, undercut, sharp eyes, tall, white dress shirt, loosened necktie, rolled sleeves, modern office, window, city lights, night, upper body, looking at viewer, slight smile, clean lineart, cel shading, flat color, webtoon style, manhwa style, masterpiece, best quality, very aesthetic, absurdres`
- **로판(여주)**
  `1girl, solo, long wavy blonde hair, blue eyes, ball gown, off-shoulder dress, lace, jewelry, tiara, gloves, rose garden, marble terrace, chandelier light, soft lighting, elegant, upper body, looking at viewer, light smile, manhwa style, soft shading, pastel colors, masterpiece, best quality, very aesthetic, absurdres`
- **무협**
  `1boy, solo, long black hair, hair tie, hanfu, chinese clothes, black robe, sword, martial arts, bamboo forest, mist, wind, dynamic pose, serious, ink wash background, manhwa style, dramatic lighting, masterpiece, best quality, absurdres`
- **현대 캠퍼스/직장(여주, 교복 회피)**
  `1girl, solo, brown hair, ponytail, hoodie, denim, cafe interior, window seat, warm light, holding coffee cup, looking at viewer, smile, adult, mature female, clean lineart, cel shading, webtoon style, masterpiece, best quality, absurdres`
- **표정 차분 생성(시드 고정)**: 위 베이스에서 표정 블록만 교체 → `smile` → `blush, embarrassed, looking away` → `angry, furrowed brow` → `sad, teary eyes` → `surprised, wide-eyed, :o` → `smug` … + `simple background, green background` (누끼용).

### 5-3. 자연어 프롬프트 예시(Nano Banana / GPT Image / 베이비챗·케이브덕 내장)
```
[설정 카드 - 매번 동일하게 붙임]
캐릭터: 20대 중반 한국인 남성, 흑발 언더컷, 날카로운 눈매, 키 큰 체형.
의상: 흰 셔츠, 느슨한 네이비 넥타이, 소매 걷음. 소품: 은색 손목시계.
화풍: 한국 웹툰 스타일, 깨끗한 검은 외곽선, 2단계 셀셰이딩, 채도 높은 플랫 컬러, 배경 디테일 간결.
금지: 얼굴·머리·의상·화풍 변경 금지, 배경에 글자·다른 인물 넣지 않기.

[장면 변수]
구도: 3:4 상반신, 카메라 눈높이. 배경: 밤의 사무실 창가, 도시 야경.
표정: 살짝 비웃는 미소. 시선: 정면.
```
- 베이비챗 AI 생성은 스타일 선택(로판/순정/동양화/애니/카툰/청량)이 별도 UI라 프롬프트에서는 외형·장면만 기술. 케이브덕 아트 스튜디오는 영어 자연어 권장(+'다듬기').

### 5-4. 스타일 통일 팁
- 한 캐릭터 = 한 모델(체크포인트+LoRA 조합 또는 한 상용 모델)로 고정. 툴을 섞으면 선·음영이 달라져 표정 세트가 어색.
- 품질·화풍 태그 블록을 **스니펫으로 저장**(케이브덕 @단축어, NAI 프리셋, ComfyUI 문자열 노드).
- 팔레트(hex 3~4색)와 조명 방향을 명시. 1K 초안 다량 → 선별 → 2K 업스케일(4K는 출판 외 불필요).
- 플랫폼 비율에 맞춰 **처음부터 비율 지정**(1:1 프로필, 3:4 제타, 2:3 베이비챗, 16:9 배경). 나중에 크롭하면 구도가 깨짐.

**출처**
- https://github.com/charliecpeterson/comfyui_mcp/blob/main/skills/prompt-illustrious/SKILL.md , https://civitai.com/articles/23210/arctenoxs-simple-prompt-guide-for-illustrious-for-comfyuisite , https://www.seaart.ai/articleDetail/d182mq5e878c73cnnbo0 , https://tensor.art/articles/831123524065191393 , https://artificialguy.com/blog/illustrious-noobai-anime-guide/
- https://freeaipromptmaker.com/blog/2025-11-29-stable-diffusion-negative-prompts-guide (네거티브 목록)
- https://note.com/kazumu/n/n6390a899bdce , https://gist.github.com/massahud/8bc9fec2ffe6e4cbd0d232ee114b7bde (Illustrious 태그 순서·모디파이어)
- https://danbooru.donmai.us/wiki_pages/tag_group:face_tags (표정 태그 그룹; 본 리서치 시 접속 불안정, 태그명은 통용 목록 기준)
- https://prompthero.com/ai-models/search/tags/webtoon (웹툰풍 Illustrious LoRA 목록)
- https://chatgptprompt.in/blog/ai-webtoon-manhwa-prompts-guide , https://www.comicsai.org/en/format/korean-webtoon , https://stablediffusionweb.com/prompts/korean-webtoon-style , https://allmyuniverse.com/image-prompt-guide-webtoon-cel-shaded-character-scene/
- https://leonardo.ai/news/nano-banana-prompt-guide , https://carat.im/blog/nano-banana-ai-guide

---

## 6. 커뮤니티 노하우

### 6-1. 플랫폼별 실제 워크플로우(아카라이브·디시·포스타입·X)
- **케이브덕**: 제작자 대부분 외부 AI 생성 이미지 사용. 필터 오판(건전 그림도 19금/공개 불가 판정)이 잦아 **재분류 신청**이 루틴. 묘사는 영어. 앨범 키워드는 공식 문서대로 `smile` 통일(커뮤니티 일부 글의 `smile_1` 번호 방식은 구버전/상충 → 공식 우선). 스냅샷은 "잔잔한 서사 구간"에서만 품질 안정, 페르소나 이미지는 캐릭터와 같은 그림체로.
- **베이비챗**: 감정·일상 에셋은 메인 프롬프트, 특수 상황은 로어북. 외부 호스팅(imgbb/itimg) + 캐릭터코드 통일 파일명(NOA.png 등) + 마크다운 코드표. Slug 업데이트 이후 구형 `img:[item]` 프롬프트는 수정.
- **제타**: 3:4 전환 후 구 1:1 프로필이 좌우 잘림 → 중요 요소 중앙 배치·상반신 세로 구도로 재제작. 틱톡에 '제타 프사 추천' 류 트렌드 콘텐츠 다수(유저 프로필용 범용 이미지 수요). 유저 프로필용 '실루엣/날먹 이미지' 공유.
- **크랙**: 이미지 보관함 해금 힌트를 '수집 요소'로 설계(해금 조건 힌트 문구). 상황 이미지는 파일명 `분류_상황`로 대량 업로드(최대 1,600장) → 배치표 정리. 대사와 겹치지 않게 별도 줄.
- **나노바나나 공통 팁(디시 특이점 갤러리)**: 3:4·2K 하프샷 마스터, 한국어 프롬프트 그대로 OK, 사진 용어 기본 프롬프트(실사용), `noise/JPEG artifact/VHS` 키워드 금지, 1K 초안→선별→업스케일, ComfyUI(SDXL+8스텝 라이트닝 LoRA)로 의상·소품·표정 부분 수정, FLUX는 40~50번대 GPU 권장·SDXL은 20번대 가능.
- **NovelAI 유저(아카라이브 AI 그림 채널 계열)**: 가입 시 30장 무료 → Opus 무제한 전환, 레퍼런스 시트 태그(`reference sheet, expressions, no text`)로 표정 시트.

### 6-2. 썸네일이 클릭률에 미치는 영향·디자인 트렌드
- 플랫폼이 공개한 썸네일 CTR 데이터는 **없음**(미확인). 아래는 일반 썸네일 원칙 + 커뮤니티 관찰.
- 일반 원칙: 유저는 피드에서 0.x초 훑고 결정 → **고대비·감정이 드러나는 얼굴·모바일 가독성·A/B 테스트**. 프로필은 **정사각/세로에서 얼굴 중앙, 원형 크롭 안전 영역** 고려(캐럿 가이드).
- 캐릭터챗 특화 관찰 [추정/커뮤니티]:
  - **상반신 클로즈업 + 시선 맞춤(looking at viewer)**이 기본. 전신은 작은 썸네일에서 얼굴이 뭉개짐.
  - **장르 코드 즉시 전달**: 로판=드레스·보석·궁정 조명, 무협=도포·검·먹 배경, 현대=셔츠/후드·도시 야경. 베이비챗 스타일 프리셋(로판/순정/동양화)이 이 수요를 반영.
  - **텍스트 오버레이**: 제목·한 줄 훅을 넣는 경우가 늘었으나(Nano Banana Pro 한글 렌더링), 크랙은 프로필 이미지 내 비속어·성적 은어 금지, 제타는 2026-02 시위 문구 이미지 일괄 삭제 사례 → 텍스트는 짧고 중립적으로.
  - **표정은 '관계 암시'형**(살짝 웃음·시선 회피·도발)이 중립 표정보다 선호된다는 통념. 표정 차분을 썸네일 A/B에 재활용.
  - **제타 3:4·커버 10장**: 첫 커버가 사실상 썸네일 → 1장은 캐릭터 얼굴, 나머지는 세계관 컷.
  - 치비(SD) 서브 이미지는 소개 페이지 장식용으로 호감도 ↑(케이브덕은 언세이프라도 비성적 치비 허용).

### 6-3. 금지·제재 사례(반드시 피할 것)
- **실존 인물·아이돌 실사**: 전 플랫폼 초상권 위반. 스캐터랩 임직원 사진 도용 사과문(2025-02), 베이비챗 딥페이크·하이퍼리얼리즘 금지, 크랙 '실제 사진처럼 보이는 이미지' 프로필 제한, 케이브덕 실사풍은 AI 표기 강제.
- **타 작품 캐릭터·공식 일러스트**: 제타 니지산지 플롯 전면 삭제(애니컬러 요청, 2026-10-12), 대원미디어 요청으로 '나의 히어로 아카데미아' 캐릭터 상시 삭제, 웹툰 6개사(카카오엔터·리디·레진 등)의 스캐터랩 고소 보도(2026-05), 제타 2026-01-23 "오리지널 캐릭터만" 정책. 개인 창작자 그림 무단 사용 → 제작 정지(제타 X 공지).
- **미성년 외형**: 교복·학교 배경·앳된 체형은 성인 설정이어도 제재(케이브덕·크랙·베이비챗 공통). 크랙은 미성년 성적 대상화 이미지에 경고 없이 최고 제재.
- **외부 이미지 위반**: 크랙은 외부 이미지 활용 위반 시 최고 수준 제재. 제타는 "개인 사용 자유" 표기 이미지도 별도 허가 필요.
- **언세이프 노출 처리 미흡**: 모자이크·블러·시스루는 전 플랫폼 불인정 → 불투명 유색 가림만.

**출처**
- https://arca.live/b/caveduck/94638883 , https://www.postype.com/@untitled-record/post/20400359 , https://gall.dcinside.com/mgallery/board/view/?id=aichatting&no=167075 , https://gall.dcinside.com/mgallery/board/view/?id=aichatting&no=57618
- https://gall.dcinside.com/mgallery/board/view/?id=babechat&no=4416 , https://m.dcinside.com/board/babechat/412
- https://gall.dcinside.com/mgallery/board/view/?id=zetam&no=562449 , https://www.tiktok.com/discover/%EC%A0%9C%ED%83%80-%ED%94%84%EC%82%AC-%EC%B6%94%EC%B2%9C
- https://gall.dcinside.com/mgallery/board/view/?id=thesingularity&no=894307
- https://carat.im/prompt-gallery/character-profile-photo , https://carat.im/blog/character-ai-chat-tips , https://clip.dor.gg/ko/blog/game-thumbnail-design-tips
- https://namu.wiki/w/zeta(%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98)/%EB%AC%B8%EC%A0%9C%EC%A0%90%20%EB%B0%8F%20%EB%B9%84%ED%8C%90 , https://www.topcelev.co.kr/news/articleView.html?idxno=4055 , https://www.postype.com/@kimdongdang/post/18758012 , https://x.com/zetaAI_/status/1858320821347078242
- https://help.crack.wrtn.ai/oppolicy , https://babechat.ai/policy/character-creation-policy , https://docs.caveduck.io/ko/articles/-%EC%BA%90%EB%A6%AD%ED%84%B0-%EC%A0%9C%EC%9E%91-%EA%B7%9C%EC%A0%95-5da6343e

---

## 7. 비용/도구 추천 결론

### 7-1. 예산별 추천 스택
| 예산 | 스택 | 용도 분담 |
|---|---|---|
| **무료** | Gemini 앱(Nano Banana 2.x, 1K, 워터마크) + Tensor.Art(100크레딧/일, Illustrious) 또는 Civitai Buzz + NovelAI 체험 30장 + Leonardo 150토큰/일 + 플랫폼 내장(케이브덕 깃털/구독 무료 앨범 생성, 베이비챗 이벤트 프로챗, 제타 15피스) + rembg/Photopea/Canva | 프로필·표정 세트는 Nano Banana(레퍼런스 4장), 애니 톤 보정·추가 컷은 Tensor.Art, 누끼·말풍선은 무료 툴 |
| **월 2~3만원** | **Google AI Pro(약 ₩29,000, Nano Banana Pro·2K/4K)** 또는 **NovelAI Opus($25, 언세이프·상업 OK·무제한)** 중 택1 + 무료 스택 | 세이프티 중심이면 Google AI Pro, 성인 캐릭터·애니 특화면 NAI Opus. ChatGPT Plus($20)는 한글 텍스트·스토리보드 보조용으로 대체 가능 |
| **월 10만원** | Google AI Pro + NovelAI Opus + (Midjourney Standard $30 또는 Leonardo Premium $30) + 클라우드 ComfyUI(RunPod/RunComfy 시간제) 또는 로컬 GPU(RTX 4070↑) + 플랫폼 재화(베이비챗 130프로챗×n, 케이브덕 윙) | 마스터·시트는 NB Pro, 표정·앨범 대량은 ComfyUI(Illustrious+IP-Adapter+LoRA), 배경·키비주얼은 MJ V8.2, NSFW 앨범은 NAI/케이브덕 Quill |

### 7-2. 단계별 워크플로우(플랫폼 공통)
1. **기획**: 캐릭터 설정 카드(외형·의상·소품·화풍·금지 변경) 작성 → 플랫폼 등급(세이프/언세이프)과 2차창작 여부 확정(제타는 오리지널만).
2. **마스터 레퍼런스**: 3:4·2K 정면 하프샷 1장 + 전신 중립 1장(단순 배경). 정책 체크(교복·실사·노출·텍스트).
3. **표정 세트 9~15종**: 레퍼런스 고정, 표정만 교체, 단색 배경. 파일명을 플랫폼 키워드로(`smile`, `angry`… / 크랙 `캐릭터명_웃음`).
4. **상황·배경 컷**: 16:9(베이비챗) / 1:1(크랙) / 3:4(제타 커버) / 2:3(케이브덕·베이비챗 에셋). 인트로 3~6컷은 설정 카드+장면 변수로.
5. **후처리**: 누끼(rembg), 말풍선·텍스트(Clip Studio/Canva), 2K 업스케일, webp 변환(5MB 이하), 언세이프는 불투명 가림.
6. **정책 셀프 체크리스트**: 실사 유사 ✗ / 미성년 신호 ✗ / 타 작품·실존 인물 ✗ / 프로필은 세이프티 기준 / 케이브덕 실사풍은 AI 표기 / 케이브덕 타인 저작권은 수익화 제한.
7. **등록·매핑**: 크랙 배치표(분류×상황, 해금 힌트) / 케이브덕 앨범 키워드·잠금 / 베이비챗 Slug 확인·로어북 / 제타 커버 10장·캐릭터 5장.
8. **플레이 테스트**: 표정 호출 타이밍·중복 호출·대사 겹침 확인 → 썸네일 A/B(표정·텍스트 유무) 후 교체.

### 7-3. 핵심 결론
- 2026년 기준 **"Nano Banana Pro로 마스터·표정 세트 → 애니 계열(Illustrious/NoobAI 또는 NAI V4.5)로 대량 차분 → 플랫폼 비율 재단"**이 가장 비용 효율적인 표준 파이프라인. 플랫폼 내장 생성기는 정책 필터를 선통과한다는 장점이 있어 **최종 보정·추가 컷**용으로 병행.
- 규격은 **베이비챗(512×768·2:3, 100개)과 제타(3:4, 커버 10·캐릭터 5)**만 수치가 공식 확정. 크랙은 형식·용량(5MB)·정방형 기준만, 케이브덕은 비율·px 미확인이므로 **로그인 후 제작 화면에서 확인**이 필요.
- 상업 이용·NSFW·워터마크·라이선스는 도구마다 다르며 특히 **NoobAI(출력물 상업 불가)와 Nano Banana(SynthID)**는 사전에 인지할 것.
