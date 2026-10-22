---
name: generate-assets
description: 작품(characters/<slug>/)의 이미지 에셋을 NovelAI 웹에서 생성하는 절차. 그림체 비교컷 → 캐릭터 0번 기본컷 → 상황코드별 감정 세트 → 인페인트 → webp 변환까지. "이미지 뽑아", "에셋 만들어", "감정 세트 생성" 요청 시 사용. 사용자가 NovelAI에 로그인해 둔 Chrome에서만 진행.
---

# 에셋 생성 (NovelAI)

## 0. 읽을 것
- `docs/30-image-assets/08-novelai-production.md` (설정·프롬프트 구조·표정 블록·순서·예산) — 이 스킬의 기준 문서
- `docs/30-image-assets/07-external-hosting.md` (파일명·코드표), `06-policy-checklist.md` (정책)
- 작품의 `intake.md`(외형), `image-brief.md`, `assets/style-card.md`

## 1. 사전 조건 (하나라도 없으면 멈추고 질문 목록에 추가)
- `intake.md` 2장에 인물 외형이 있다. **외형을 지어내지 않는다.**
- 그림체가 정해졌다(`assets/style-card.md`). 없으면 §3-1만 진행.
- Chrome에서 novelai.net/image 로그인 상태(상단 "Log In" 버튼이 없음). 로그인·구독·할당량 부스트 결제는 하지 않는다.

## 2. 프롬프트 파일 먼저 (브라우저 열기 전)
`image-brief.md` 4장에 아래를 확정해 적는다.
1. 캐릭터 프롬프트: intake 외형 → danbooru 태그(08번 §2 형식). 부위별 복장·색, 핵심 앵커 1개, `adult`/`mature`.
2. 베이스 프롬프트: style-card 작가 블록 + 프레이밍(`upper body, straight on, looking at viewer`) + 배경 + `{표정}` 자리.
3. UC: 08번 §3 기본 UC(미성년 차단 줄 포함) + 작품 추가분.
4. 생성 계획표: 캐릭터 × 코드 × 시도 수, 예상 할당량(08번 §6).

## 3. 브라우저 작업
1. `tabs_context_mcp` → 새 탭 → `https://novelai.net/image`. 모델 V5 **Full** 확인(Curated 금지), 해상도 832×1216, Steps 28, Guidance 5, Euler Ancestral, Add Quality Tags 끔, Variety+ 끔. 화면 확인은 `find`/`read_page`로, 스크린샷은 결과 이미지 판정 때만.
   - 3-1 그림체 비교: 후보마다 같은 캐릭터 프롬프트로 4장 → 결과를 사용자에게 한 번에 보여 고르게 함. 탐색은 Effort Medium.
2. 0번 기본컷: 표정 블록 0으로 4~8장 → 기준(얼굴·앵커·손 정상)에 맞는 1장 선택 → **시드 고정**, 시드를 image-brief에 기록.
3. 감정 세트: 표정 블록만 교체(08번 §4 표 그대로)하며 코드별 4~8장. 0번과 비교해 앵커가 맞는 1장 채택. 3회 연속 실패 시 08번 §5-3 대체 경로(인페인트 → Emotion 툴 → V4.5 정밀 참조, 정밀 참조는 장당 +5 Anlas라 사용자에게 미리 알림).
4. 손·얼굴 오류는 Focused Inpainting으로 한 부위씩.
5. 채택본만 다운로드(파일 저장 위치: `characters/<slug>/assets/raw/`). 다운로드는 사용자 승인 범위 안에서.

## 4. 후처리 (로컬)
- 정책 체크(06번): 미성년 신호·실존 인물 유사·프로필 노출 기준.
- webp 변환(장당 1MB 이하, LSB 메타데이터 제거 겸함) → `assets/{캐릭터ID}/{상황코드}.webp`. 한글·공백 파일명 금지.
- `image-brief.md` 2장 에셋 표 상태 체크, `status.md`에 생성 장수·할당량 사용률 기록.

## 5. 하지 않는 것
- NovelAI 로그인·결제·부스트 구매·계정 설정 변경, 외형 임의 창작, Curated 모델로 에셋 생산, 사용자 확인 없는 대량(할당량 30% 이상) 생성.
