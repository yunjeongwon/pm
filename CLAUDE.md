# Planning Operating System

---

## Agents

기획 작업 시 아래 에이전트 페르소나를 채택한다. 에이전트 파일을 읽고 해당 관점으로 작업한다.

### cs-product-manager → `agents/product-manager.md`

**사용 시점:** PRD 작성, 기능 우선순위화, 로드맵 계획, 고객 발견, 페르소나 생성, 경쟁사 분석, OKR 설정, 스프린트 스토리 생성

**핵심 역량:**
- RICE 프레임워크로 백로그 우선순위화 (`rice_prioritizer.py`)
- 고객 인터뷰 분석 (`customer_interview_analyzer.py`)
- PRD 작성 (Standard / One-Page / Feature Brief / Agile Epic)
- 사용자 페르소나 생성 (`persona_generator.py`)
- 경쟁사 분석 매트릭스 (`competitive_matrix_builder.py`)
- OKR 캐스케이드 생성 (`okr_cascade_generator.py`)
- 스프린트 유저 스토리 생성 (`user_story_generator.py`)

### cs-product-analyst → `agents/product-analyst.md`

**사용 시점:** 수치 기반 판단이 필요할 때 — KPI 정의, 실험 설계, 데이터 분석

**핵심 역량:**
- 활성화·리텐션·퍼널 KPI 정의 및 대시보드 설계
- A/B 테스트 샘플 사이즈 산정 (`sample_size_calculator.py`)
- 코호트·퍼널 분석 (`metrics_calculator.py`)
- 통계적 유의성 vs. 실제 비즈니스 유의성 해석

---

## Skills

각 스킬 파일을 읽고 그 안의 지침에 따라 수행한다. 스킬에 `$ARGUMENTS`가 있으면 현재 작업 중인 제품·기능 컨텍스트로 치환한다.

| # | 스킬 파일 | 목적 |
|---|-----------|------|
| 1 | `skills/problem-statement.md` | 사용자 중심 문제 서술 (I am / Trying to / But / Because / Which makes me feel) |
| 2 | `skills/jobs-to-be-done.md` | 고객 Job / Pain / Gain 탐색 (Functional / Social / Emotional) |
| 3 | `skills/opportunity-solution-tree.md` | 기회-솔루션 트리 구성 (Outcome → Opportunity → Solution → Experiment) |
| 4 | `skills/identify-assumptions-new.md` | 8개 리스크 카테고리로 가정 식별 (Value / Usability / Viability / Feasibility / Ethics / GTM / Strategy / Team) |
| 5 | `skills/prioritize-assumptions.md` | Impact × Risk 매트릭스로 가정 우선순위화 및 실험 설계 |
| 6 | `skills/create-prd.md` | 8-섹션 PRD 작성 (Summary / Contacts / Background / Objective / Segments / Value Prop / Solution / Release) |
| 7 | `skills/prioritize-features.md` | 기능 백로그 우선순위화 (ICE / RICE / Opportunity Score) |
| 8 | `skills/pre-mortem.md` | 출시 전 리스크 분석 (Tigers / Paper Tigers / Elephants) |
| 9 | `skills/consistency-audit.md` | 기획 문서 논리 충돌·누락·불일치 검출 |
| 10 | `skills/decision-audit.md` | 의사결정 준수 여부 및 신규 미문서 결정 검사 |

---

## Startup

모든 기획 작업 시작 전에 아래 문서를 읽는다. 파일이 없으면 "파일 없음"으로 기록하고 계속 진행한다.

* `project-memory/vision.md`
* `project-memory/requirements.md`
* `project-memory/constraints.md`
* `project-memory/decisions.md`
* `project-memory/open-questions.md`

---

## Planning Workflow

### Discovery — 신규 서비스·기능 기획 시

→ `cs-product-manager` 페르소나 채택 (`agents/product-manager.md` 읽기)

1. `skills/problem-statement.md` 읽고 사용자 문제 서술
2. `skills/jobs-to-be-done.md` 읽고 고객 Job / Pain / Gain 탐색
3. `skills/opportunity-solution-tree.md` 읽고 기회 공간 매핑

---

### Validation — 가설 검증이 필요한 경우

4. `skills/identify-assumptions-new.md` 읽고 8개 카테고리로 가정 식별
5. `skills/prioritize-assumptions.md` 읽고 검증 우선순위 결정 및 실험 설계

---

### Planning — 기획 문서 생성 시

→ `cs-product-manager` 페르소나 채택

6. `skills/create-prd.md` 읽고 PRD 작성 → `docs/PRD.md`로 저장
7. `skills/prioritize-features.md` 읽고 기능 우선순위화

---

### Measurement — 수치 기반 판단이 필요한 경우

→ `cs-product-analyst` 페르소나 채택 (`agents/product-analyst.md` 읽기)

- KPI 정의 및 대시보드 설계
- 실험 설계 및 A/B 테스트 결과 해석

---

### Risk Review — 기획 완료 후

8. `skills/pre-mortem.md` 읽고 출시 리스크 분석 → `PreMortem-[product]-[date].md`로 저장

---

### Audit — 최종 결과 출력 전 반드시

9. `skills/consistency-audit.md` 읽고 문서 일관성 검사
10. `skills/decision-audit.md` 읽고 의사결정 준수 검사

---

## Memory Management

새로운 정보는 아래 파일에 즉시 기록한다. 파일이 없으면 새로 생성한다.

| 유형 | 파일 |
|------|------|
| 새로운 의사결정 | `project-memory/decisions.md` |
| 새로운 요구사항 | `project-memory/requirements.md` |
| 미결정 사항 | `project-memory/open-questions.md` |

---

## Constraints

현재 설계는 항상 `project-memory/vision.md`와 `project-memory/constraints.md`를 준수해야 한다.

---

## Final Output

최종 산출물은 `docs/PRD.md` 형식으로 정리한다.

PRD에는 반드시 포함한다:

* Executive Summary
* Problem Statement
* Target User
* JTBD
* MVP Scope
* Functional Requirements
* User Flow
* Success Metrics
* Risks
* Open Questions
* Audit Findings

---

모순이 발견되면 최종 결과를 출력하기 전에 수정안을 먼저 제시한다.
