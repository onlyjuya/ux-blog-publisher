# ux-blog-publisher

레퍼런스 블로그 조사부터 프로덕트·디자인·UX 케이스 스터디 초안 작성, 통일된 에디토리얼 톤의 이미지 일괄 생성·검수, 한국어 AI 윤문(`korean-humanizer`), 마크다운 정리 및 인라인 HTML 프리뷰 생성까지 블로그 발행 전 과정을 자동화하는 **Agent Skill**입니다.

## 설치 (`npx skills add`)

```bash
# 기본 설치 (프로젝트)
npx skills add onlyjuya/ux-blog-publisher

# 전역 설치 (-g)
npx skills add onlyjuya/ux-blog-publisher --skill ux-blog-publisher -g
```

*(선택)* 4단계 한국어 AI 윤문 절차를 함께 쓰려면 [`korean-humanizer`](https://github.com/NomaDamas/k-skill/blob/main/docs/features/korean-humanizer.md) 스킬도 같이 설치해 두면 좋습니다.

```bash
npx skills add NomaDamas/k-skill --skill korean-humanizer -g
```

## 워크플로우 (5단계)

1. **레퍼런스 조사 및 원문 구조 파싱** — 검색 결과의 추측 URL을 그대로 쓰지 않고 HTTP 200과 `<title>`을 직접 검증한 뒤 원문 구조·호흡을 추출합니다.
2. **6단 서사 구조 초안 작성** — `도입 → 문제 → 가설(3원칙) → 1/2/3 핵심 실행 → 결과 → 적용해보기` 흐름으로 초안을 쓰고 시각 자료 슬롯을 설계합니다.
3. **에디토리얼 이미지 일괄 생성 및 검수** — 통일된 16:9 오프화이트·코발트 블루 톤(`#F8FAFC` / `#3182F6`)으로 이미지를 병렬 생성하고, 전량 육안 검수 후 PNG로 저장합니다. (AI 이미지 모델 쿼터 제한 시 UI 다이어그램은 헤드리스 브라우저 PNG 렌더링으로 폴백 가능)
4. **마크다운 조립 및 한국어 윤문** — 이미지 속 라벨·수치와 본문을 1:1 일치시키고, `korean-humanizer` 기준으로 AI 흔적(S1 0건, 변경률 30% 이하)을 제거합니다.
5. **자동 검증 및 인라인 프리뷰** — `scripts/audit_and_preview.ps1`로 이미지 링크 실존 여부, S1/S2 잔존 패턴, 글자수(공백 포함/제외)를 점검하고 인라인 HTML 프리뷰를 생성합니다.

## 디렉터리 구조

```text
ux-blog-publisher/
├── README.md
├── LICENSE
└── skills/
    └── ux-blog-publisher/
        ├── SKILL.md
        ├── references/
        │   ├── structure-template.md
        │   └── image-style-guide.md
        └── scripts/
            └── audit_and_preview.ps1
```

## 사용 예시

```text
ux-blog-publisher 스킬로 "맨땅에서 디자인 시스템 구축하기" 블로그 글이랑 이미지까지 한 번에 만들어줘
```

```text
이 레퍼런스 URL 참고해서 "매일 하던 디자인 업무를 AI에게 시키기" 케이스 스터디 아티클 완성본 만들어줘
```

## License

MIT
