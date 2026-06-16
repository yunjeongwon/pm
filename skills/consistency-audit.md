Consistency Audit Skill

Purpose

서비스 기획 문서의 논리 충돌, 누락, 기존 결정과의 불일치를 검출한다.
에이전트는 반드시 모든 항목을 명시적으로 검사하고 결과를 빠짐없이 보고한다.

⸻

Inputs

반드시 아래 문서를 모두 읽고 검토한다. 파일이 존재하지 않으면 "파일 없음"으로 기록한다.

* project-memory/vision.md
* project-memory/requirements.md
* project-memory/constraints.md
* project-memory/decisions.md
* project-memory/open-questions.md
* 현재 생성된 PRD (또는 검토 대상 문서)

⸻

Audit Rules

아래 각 섹션을 순서대로 검사한다. 각 항목은 PASS / FAIL / N/A 중 하나로 판정한다.
FAIL 판정 기준: 명백한 충돌, 누락, 또는 문서 간 불일치가 존재할 때.

─────────────────────────────

Vision Consistency

* 현재 기능이 vision.md의 서비스 방향성과 일치하는가
* 타겟 사용자가 vision.md에서 정의한 핵심 사용자와 일치하는가
* MVP 범위를 초과하는 기능이 포함되었는가 (포함 시 FAIL)

─────────────────────────────

Constraint Consistency

* 기술 제약(constraints.md)을 위반하는 기능 또는 요구사항이 존재하는가
* 리소스·일정·팀 제약을 초과하는 범위가 포함되었는가
* 명시적으로 금지된 접근 방식이 사용되었는가

─────────────────────────────

Requirement Consistency

* requirements.md의 필수 요구사항이 PRD에 누락되었는가
* PRD에 포함된 기능이 requirements.md와 상충하는가
* 우선순위 판단이 requirements.md의 기준과 일치하는가

─────────────────────────────

Decision Consistency

* 과거 decisions.md의 결정과 충돌하는 내용이 존재하는가
* 폐기(rejected)된 기능 또는 접근 방식이 다시 등장하는가
* 제외로 결정된 범위가 다시 포함되었는가

─────────────────────────────

JTBD / OST Consistency

* PRD의 기능이 Jobs-to-be-Done을 실질적으로 해결하는가
* Opportunity Solution Tree에서 도출된 솔루션과 PRD의 솔루션이 일치하는가
* JTBD에서 정의한 사용자 맥락과 기능 설계가 일치하는가

(해당 문서가 없으면 N/A로 처리)

─────────────────────────────

Feature Consistency

* PRD 내 기능 간 논리적 모순이 존재하는가
* 사용자 흐름(User Flow)에서 충돌 또는 데드엔드가 존재하는가
* 권한 모델이 기능 간 일관되게 적용되는가

─────────────────────────────

Policy Consistency

아래 정책이 PRD에 존재하는지, 존재한다면 일관성이 있는지 검사한다.

* 탈퇴 정책
* 신고 정책
* 차단 정책
* 개인정보 처리 정책

각 항목: 존재함 / 누락 / 불일치 중 하나로 표기

─────────────────────────────

Open Questions Consistency

* open-questions.md에 미결 상태인 사항이 PRD에서 결정된 것으로 처리되었는가
* PRD에서 새롭게 발생한 미결 사항이 있는가

⸻

Output Format

아래 형식으로 출력한다. 발견된 항목이 없는 섹션도 생략하지 않는다.

## Consistency Audit Report

### Summary
- 검토 문서: [목록]
- 총 FAIL 항목: N건 (critical: N / high: N / medium: N / low: N)

### Findings

#### [CRITICAL] 항목명
- **위치**: 어느 섹션/기능
- **내용**: 무엇이 충돌하는가
- **이유**: 왜 문제인가 (어떤 문서의 어떤 내용과 충돌)
- **영향**: 그대로 진행 시 어떤 결과가 발생하는가

#### [HIGH] 항목명
(동일 구조)

#### [MEDIUM] 항목명
(동일 구조)

#### [LOW] 항목명
(동일 구조)

### No Issues Found
문제가 없는 섹션은 여기에 명시한다.
예: Vision Consistency — PASS, Feature Consistency — PASS

### New Open Questions
이번 검토에서 새롭게 발생한 미결 사항 목록 (없으면 "없음"으로 명시)

⸻

Severity 기준

* critical: 서비스 방향성 충돌, constraint 위반 — 즉시 수정 필요
* high: 과거 결정 위반, 필수 요구사항 누락
* medium: 정책 누락, JTBD 불일치
* low: 개선 권고, 명확성 보강 권고

⸻

Final Instruction

* 모든 Audit Rules 섹션을 반드시 검사한다. 건너뛰지 않는다.
* 문제를 발견하면 반드시 이유와 영향을 설명한다.
* 문제가 없는 섹션도 "PASS"로 명시한다.
* 전체적으로 문제가 없더라도 "발견된 문제 없음 — 모든 항목 PASS"로 명시한다.
