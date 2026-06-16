Decision Audit Skill

Purpose

project-memory/decisions.md에 기록된 모든 의사결정을 기준으로
현재 PRD가 각 결정을 준수하는지, 결정이 암묵적으로 변경되었는지,
폐기된 결정이 재등장하는지, 새로운 미문서 결정이 발생했는지를 검사한다.

이 스킬은 consistency-audit의 Decision Consistency 섹션보다 더 깊은 수준으로
각 결정을 개별적으로 추적한다.

⸻

Inputs

반드시 아래 문서를 모두 읽고 검토한다. 파일이 존재하지 않으면 "파일 없음"으로 기록한다.

* project-memory/decisions.md  ← 핵심 입력. 각 결정 항목을 개별적으로 추출한다.
* project-memory/requirements.md
* project-memory/constraints.md
* project-memory/open-questions.md
* 현재 생성된 PRD (또는 검토 대상 문서)

⸻

Audit Rules

아래 각 섹션을 순서대로 검사한다. 각 항목은 PASS / FAIL / N/A 중 하나로 판정한다.
FAIL 판정 기준: 결정 위반, 미문서 변경, 폐기 결정 재등장, 신규 미문서 결정이 존재할 때.

─────────────────────────────

Decision Extraction

먼저 decisions.md에서 모든 결정 항목을 목록으로 추출한다.
각 항목에 대해 아래 속성을 파악한다:

* 결정 내용 (무엇을 결정했는가)
* 결정 근거 (왜 그렇게 결정했는가)
* 결정 상태 (활성 / 보류 / 폐기)
* 영향 범위 (어떤 기능, 정책, 설계에 영향을 주는가)

decisions.md에 상태가 명시되지 않은 경우 "활성"으로 간주한다.

─────────────────────────────

Compliance Review

각 활성 결정에 대해:

* PRD가 해당 결정을 명시적으로 반영하는가
* PRD가 해당 결정을 암묵적으로 위반하는가 (직접 언급 없이 다른 방향으로 설계)
* PRD에서 해당 결정과 관련된 내용이 완전히 누락되었는가

판정:
- 반영됨 → PASS
- 암묵적 위반 또는 누락 → FAIL

─────────────────────────────

Rejected Decision Reappearance

폐기(rejected) 상태로 기록된 결정에 대해:

* 폐기된 기능, 접근 방식, 기술 선택이 PRD에 다시 등장하는가
* 폐기 이유가 여전히 유효한가, 아니면 상황이 바뀌어 재검토가 필요한가

판정:
- 폐기 결정이 재등장 → FAIL
- 재등장하되 명시적 재논의가 있음 → 별도 메모 (FAIL 아님)

─────────────────────────────

Decision Chain Analysis

결정 간 의존성을 검사한다:

* A 결정이 B 결정에 의존할 때, B가 변경되었다면 A도 영향을 받는가
* 하나의 결정 변경이 연쇄적으로 다른 결정을 무력화하는가

판정:
- 연쇄 영향이 PRD에 반영되지 않음 → FAIL

─────────────────────────────

Implicit Decision Detection

PRD에서 새롭게 결정된 사항을 감지한다:

아래 패턴이 등장하면 신규 결정으로 간주한다:
* 기능 포함/제외 여부가 새롭게 결정된 경우
* 기술 방식, 정책, 우선순위가 처음으로 확정된 경우
* 기존 open-questions.md의 미결 사항이 PRD에서 암묵적으로 해소된 경우

판정:
- 신규 결정이 decisions.md에 미등록 → FAIL (등록 요청)

─────────────────────────────

Impact Analysis

FAIL로 판정된 항목에 대해:

영향받는 기능, 정책, 사용자 흐름을 식별한다.

예시:
결정 위반: B2C 전용 설계 → B2B 요소 포함
영향: 조직 기능, 관리자 권한, 멤버 관리

⸻

Output Format

아래 형식으로 출력한다. 발견된 항목이 없는 섹션도 생략하지 않는다.

## Decision Audit Report

### Summary
- 검토 문서: [목록]
- 총 검토 결정 수: N건
- FAIL 항목: N건 (critical: N / high: N / medium: N / low: N)
- 신규 등록 필요 결정: N건

### Decision Status Overview
| 결정 ID | 결정 내용 요약 | 상태 | 판정 |
|---------|--------------|------|------|
| D-001   | …            | 활성  | PASS |
| D-002   | …            | 활성  | FAIL |
| D-003   | …            | 폐기  | PASS |

### Findings

#### [CRITICAL] 항목명
- **위반 결정**: decisions.md의 어떤 결정인가
- **위반 위치**: PRD의 어느 섹션/기능
- **위반 내용**: 무엇이 충돌하는가
- **근거**: 결정의 원래 이유와 어떻게 상충하는가
- **영향**: 영향받는 기능 및 하위 결정 목록

#### [HIGH] 항목명
(동일 구조)

#### [MEDIUM] 항목명
(동일 구조)

#### [LOW] 항목명
(동일 구조)

### No Issues Found
문제가 없는 결정은 여기에 명시한다.
예: D-001 (B2C 전용 설계) — PASS, D-003 (모바일 우선) — PASS

### New Decisions to Register
이번 검토에서 발견된 신규 미문서 결정 목록.
각 항목은 decisions.md에 추가해야 한다.

| # | 결정 내용 | 발생 위치 (PRD 섹션) | 권장 상태 |
|---|---------|------------------|---------|
| 1 | …       | …                | 활성      |

없으면 "없음"으로 명시한다.

### Rejected Decisions Requiring Re-review
폐기 결정 중 상황 변화로 재검토가 필요한 항목.
없으면 "없음"으로 명시한다.

⸻

Severity 기준

* critical: 핵심 결정 위반, 서비스 방향성 변경에 해당하는 결정 무시
* high: 과거 명시적 결정을 PRD가 암묵적으로 변경, 폐기 결정 재등장
* medium: 결정 누락, 연쇄 영향 미반영
* low: 신규 결정 미문서화, 결정 근거 불명확

⸻

Final Instruction

* decisions.md의 모든 결정 항목을 개별적으로 검사한다. 건너뛰지 않는다.
* 각 결정에 대해 PASS / FAIL / N/A를 명시한다.
* FAIL 항목은 반드시 위반 내용, 근거, 영향을 함께 기술한다.
* PRD에서 암묵적으로 발생한 신규 결정을 반드시 식별한다.
* 전체적으로 문제가 없더라도 "발견된 문제 없음 — 모든 결정 PASS"로 명시한다.
* 이 스킬 실행 후 decisions.md 업데이트가 필요한 경우 사용자에게 명시적으로 안내한다.
