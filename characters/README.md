# characters/ — 작품 폴더 규칙

작품 1개 = 폴더 1개. 폴더명은 `slug`(영문 소문자-하이픈). 공유 세계관은 `_worlds/<world-slug>/world.md`.

```
characters/<slug>/
├── intake.md          # 사용자 접수표 (templates/intake.md) — 컨셉·인물·외형의 유일한 출처
├── character.md       # 마스터 카드 (templates/character.master.md 복사) — 단일 진실 원천
├── lorebook.md        # 로어북·단축어 (templates/lorebook.md)
├── scenes/
│   ├── 01-<name>.md   # 시작 장면 (templates/first-message.md), 최대 3개
│   └── 02-<name>.md
├── variants.md        # (선택) 언세이프티 파생본 등 변형판의 '차이점만' 기록. 공통부는 character.md
├── image-brief.md     # 이미지 브리프 (templates/image-brief.md)
├── assets/            # raw/(NAI 원본 PNG, 커밋 안 함) · {캐릭터ID}/{상황코드}.webp(외장 업로드본) · profile.* · bg-* · intro-* · ending-*
│   ├── style-card.md  #   설정 카드(모든 이미지 프롬프트에 복사하는 고정 블록) + 팔레트
│   └── LICENSE.md     #   사용 도구·모델·라이선스 원문 링크·확인일 (수익화 작품 필수)
├── exports/           # 플랫폼별 변환본 (제출 직전 생성: crack.md, crack-unsafe.md, caveduck.md, babechat.md) — 수정 금지
├── versions/          # (선택) 큰 수정 전 원본 백업 v1/, v2/ … (플랫폼 데이터 반출 거부 사례 대비, 로컬이 원본)
└── status.md          # 플랫폼별 제출 상태·URL·등급·독점 조건·반응·수정 이력

characters/_worlds/<world-slug>/
└── world.md           # 여러 작품이 공유하는 세계관(케이브덕 '세계관 관리'·크랙 시리즈용). 각 작품 character.md에서 링크
```

## 규칙
1. 본문은 `character.md`·`lorebook.md`·`scenes/`·`variants.md`에서만 고친다. `exports/`는 파생물.
2. 언세이프티 파생본은 별도 폴더가 아니라 `variants.md`에 차이점만 적고, 제출 시 `exports/<플랫폼>-unsafe.md`로 따로 변환한다(플랫폼에서는 별개 작품으로 등록).
3. `status.md`에 날짜(YYYY-MM-DD)와 함께 기록: 제출일, 공개 URL, 등급(세이프/언세이프), 독점 여부와 만료일, 주간 대화 수, 댓글 요지, 수정 내용.
4. 독점(크랙 온리 18개월 / 크랙 오리지널 영구 / 케이브덕 오리지널 3개월 / B·T Only 100일)이 걸린 작품은 frontmatter `exclusivity`에 적고 다른 플랫폼에 올리지 않는다. 작품당 독점 1곳.
5. 등장인물 전원 성인·나이 명시. 실존 인물·타 IP·근친·학교 주배경 금지. (CLAUDE.md 6장)
6. 큰 수정(프롬프트 구조 변경, 등급 변경 불가 항목 재설정) 전에는 `versions/vN/`에 원본을 복사한다.
7. `_example/`은 형식 예시다. 실제 작품은 새 폴더로.
