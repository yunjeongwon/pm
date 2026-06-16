# Planning OS

Claude를 기획 전문가로 만들어주는 워크스페이스입니다.
`claude` 명령어 하나로 PRD 작성, 기능 우선순위화, 리스크 분석까지 자동으로 진행합니다.

---

## 시작하는 법

```bash
claude
```

터미널에서 위 명령어를 입력하면 Claude가 이 워크스페이스의 설정을 자동으로 읽고 기획 모드로 진입합니다.

그 다음엔 그냥 말하면 됩니다.

```
"배달앱 재주문 기능 기획해줘"
"B2B SaaS 온보딩 개선 PRD 만들어줘"
"이 기능 목록 우선순위 정해줘"
```

---

## 참고 문서 첨부하는 법

기획에 참고할 문서가 있다면 `reference/` 폴더에 넣고 요청할 때 함께 언급하면 됩니다.

```
"reference/유저인터뷰.txt 참고해서 문제 정의해줘"
"@reference/경쟁사분석.pdf 보고 기회 영역 찾아줘"
```

PDF, txt, md, csv 파일 모두 읽을 수 있습니다.

---

## 폴더 구조

```
pm/
├── agents/                 # 에이전트 정의 (자동으로 사용됨)
├── skills/                 # 기획 프레임워크 모음 (자동으로 사용됨)
├── project-memory/         # 프로젝트 기억 저장소
│   ├── vision.md           # 서비스 방향성 · 핵심 사용자
│   ├── requirements.md     # 필수 요구사항
│   ├── constraints.md      # 기술 · 리소스 · 일정 제약
│   ├── decisions.md        # 의사결정 로그
│   └── open-questions.md   # 미결 사항
├── docs/                   # 최종 산출물 저장 위치
│   └── PRD.md
└── reference/              # 참고 문서 보관함 (직접 추가)
```

> `project-memory/`는 Claude가 대화하면서 자동으로 채워나갑니다.
> `vision.md`와 `constraints.md`는 처음에 직접 작성해두면 기획 품질이 올라갑니다.

---

## 에이전트

Claude가 작업 성격에 따라 자동으로 적절한 역할을 선택합니다.

| 에이전트 | 역할 | 언제 |
|---------|------|------|
| **Product Manager** | 기획자 | PRD 작성, 기능 우선순위, 고객 발견 |
| **Product Analyst** | 데이터 분석가 | KPI 정의, 실험 설계, 지표 해석 |

---

## 스킬

기획 단계마다 자동으로 적절한 프레임워크가 적용됩니다.

| 스킬 | 설명 |
|------|------|
| **problem-statement** | 사용자 문제를 한 문장으로 명확히 정리 |
| **jobs-to-be-done** | 유저가 진짜 원하는 것 · 불편한 것 · 얻고 싶은 것 탐색 |
| **opportunity-solution-tree** | 문제 → 기회 → 해결책 → 실험 순서로 구조화 |
| **identify-assumptions** | 잘못될 수 있는 가정들을 8가지 관점으로 도출 |
| **prioritize-assumptions** | 가정 중 뭘 먼저 검증할지 순위 정하기 |
| **create-prd** | 8섹션 기획 문서(PRD) 작성 |
| **prioritize-features** | 기능 목록 우선순위화 (ICE / RICE) |
| **pre-mortem** | 출시 전 "왜 실패할까?" 리스크 점검 |
| **consistency-audit** | 기획 문서 내 모순 · 누락 검사 |
| **decision-audit** | 과거 결정 준수 여부 검사 |

---

## 기획 워크플로

```
신규 기획 요청
    ↓
[Discovery]  문제 정의 → JTBD → 기회 매핑
    ↓
[Validation] 가정 식별 → 우선순위화 → 실험 설계
    ↓
[Planning]   PRD 작성 → 기능 우선순위화
    ↓
[Risk Review] Pre-mortem 리스크 점검
    ↓
[Audit]      일관성 검사 → 의사결정 준수 검사
    ↓
docs/PRD.md 저장
```

---

## 최종 산출물

기획이 완료되면 `docs/PRD.md`에 아래 내용이 포함된 문서가 생성됩니다.

- Executive Summary
- Problem Statement
- Target User & JTBD
- MVP Scope & Functional Requirements
- User Flow
- Success Metrics
- Risks & Open Questions
- Audit Findings
