# Weak-Spot Tracker

Current as of 2026-06-20.

Purpose: keep a lightweight manual list of interview, technical, communication, market, and feedback weak spots. This is the working input for practice sessions and weekly review, not a dashboard.

Use this with:
- `learning-system-plan.md`
- `codex-interviewer-workflow.md`
- `behavioral-story-bank.md`
- `target-role-matrix.md`
- `practice-log.md`
- `weekly-review-template.md`

## Operating Rule

Only count practice that produces at least one output:
- artifact
- spoken or written answer
- drill result
- application or outreach action
- feedback note
- revised score

Passive study does not count unless it produces one of those outputs.

## Score Definitions

| Score | Meaning |
| --- | --- |
| 0 | Missing, unknown, no reps, or unsafe to claim from current evidence. |
| 1 | Recognizable when reading notes, but cannot explain, perform, or defend it cleanly yet. |
| 2 | Can explain or perform slowly with notes, but weak under pressure or missing concrete evidence. |
| 3 | Can explain or perform without notes in a relaxed setting, with clear structure and reasonable evidence. |
| 4 | Can handle it under interview pressure, with concise delivery, evidence, tradeoffs, and feedback-backed confidence. |

## Priority Factors

Mark priority higher when several factors are true:
- Market demand: repeated in target roles.
- Low score: currently 0-2.
- Anxiety: likely to cause freezing, rambling, or avoidance.
- Weak evidence: missing example, artifact, metric, code proof, or feedback.
- Interview blocker: likely in recruiter screen, hiring-manager screen, coding, system design, or behavioral interview.
- Application blocker: prevents CV, LinkedIn, applications, outreach, or market feedback.
- Product blocker: affects RefineBridge optionality or customer-discovery discipline.

Priority labels:
- `High`: repeated in target roles and blocks interviews/applications, or score is 0-1.
- `Medium`: useful gap with score 2, or limited but real interview risk.
- `Low`: nice-to-have, role-specific, or not needed for the first market test.

## Tracker

Initial scores are seed estimates from known context and story-bank gaps. Re-score after actual practice, feedback, and issue #12 diagnostic output.

| ID | Tree | Weak spot | Evidence/source | Current score | Target score | Priority factors | Priority | Next practice action | Required output | Update after #12 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| WS-001 | Story, communication, and business impact | Concise 30-second self/project explanation under pressure | `diagnostic-interview-session-001.md` Q1: accurate core flow, but too long and used "CRM" incorrectly | 2 | 3 | Market demand, low score, anxiety, interview blocker | High | Deliver the confirmed DataBridge answer aloud in 30-45 seconds without notes | Timed delivery notes plus revised score | Q1 baseline: 2/4 on 2026-06-19 |
| WS-002 | Story, communication, and business impact | RDrive business-impact/result statements are still weak | Diagnostic confirmed manual per-document uploads and metadata entry as the before state | 2 | 3 | Market demand, weak evidence, interview blocker | High | Rehearse the confirmed Problem -> Constraint -> Decision -> Tradeoff -> Result answer and state the result in one sentence | Timed answer plus one evidence-safe result sentence | Improved answer confirmed; spoken retest pending |
| WS-003 | Behavioral stories | Missing concrete facts for origin, stakeholder estimate, refactor, feedback, Vue learning, and burnout/growth path | Diagnostic confirmed mapping, provider-discovery, estimate, and regression-testing facts; provider timeline remains uncertain | 2 | 3 | Weak evidence, interview blocker | High | Verify Asite versus Autodesk timing and add one exact architecture-evolution example | Confirmed timeline or explicit `needs confirmation` note | Partial: real facts added; several story gaps remain |
| WS-004 | Interview mechanics | Formal interview pressure and one-question-at-a-time practice | First live diagnostic completed; answers ranged from 2/4 to 3/4 and clarification/interview boundaries needed explicit labels | 2 | 3 | Anxiety, interview blocker, concision | High | Run a second short mock with strict interview/clarification labels and 60-second limits | Session note with timed scores | First baseline completed 2026-06-19 |
| WS-005 | Solo ownership and team-readiness framing | Need to explain mostly solo work without sounding defensive or overclaiming | Diagnostic Q4: architecture intent 2/4; concrete local/dev/manual regression follow-up 3/4 | 2 | 3 | Market demand, anxiety, weak evidence | High | Draft and deliver a 60-second risk-control answer including design, migration checks, environments, regression tests, and recovery | Spoken answer plus automated-test/monitoring gaps | Real controls confirmed; concise framing pending |
| WS-006 | RefineBridge implementation certainty and reacclimation | Current Nuxt 4 frontend was inspected, but Richard initially recalled several older Vue 2/RDrive workflows | `frontend-diagnostic-session-001.md` Q1; current dashboard, connected-account, import-flow, task/run, billing, auth, and admin surfaces verified | 2 | 3 | Weak evidence, interview blocker, product blocker | High | Reacclimate to one current end-to-end RefineBridge workflow and explain it without file-path recall | Verified current workflow explanation with code references | Frontend baseline completed 2026-06-20 |
| WS-007 | Practical coding aloud | Need baseline for practical .NET/TypeScript drills and talking while coding | `learning-system-plan.md` and readiness map call for drills; no practice-log entries yet | 1 | 3 | Market demand, low score, interview blocker | High | Complete one small API/query/debugging drill and explain the solution aloud | Drill result, tests/notes, confidence change | Yes: update if #12 exposes coding-related issues |
| WS-008 | System design and architecture explanation | Need concrete examples for background jobs, idempotency, retries, auth, billing, and tradeoffs | Target roles repeat architecture/reliability; case studies have strong raw material but not all answer drills | 2 | 3 | Market demand, weak evidence, interview blocker | High | Explain one DataBridge or RefineBridge subsystem in 5 minutes | Answer outline plus follow-up questions | Yes: re-score after diagnostic architecture question |
| WS-009 | Testing, debugging, and reliability proof | Need stronger evidence around tests, runbooks, incident-style answers, and production debugging | `modern-dotnet-interview-readiness-map.md` lists reliability as core proof; story bank lacks specific incidents | 1 | 3 | Market demand, weak evidence, interview blocker | High | Write one sync-failure or billing-webhook debugging answer | Debugging answer using symptom/risk/checks/hypotheses/fix/prevention | Yes: revise from #12 debugging prompt if used |
| WS-010 | External feedback and networking loop | Preparing alone is a known risk | `learning-system-plan.md` and handoff emphasize mentor/feedback loops | 1 | 3 | Anxiety, weak evidence, application blocker | Medium | Book or plan one narrow feedback action | Feedback request draft or call notes | No: update after issue #8 or real feedback |
| WS-011 | Hiring logistics and constraints | Location, work authorization, timezone, salary/rate, and public links are still open | `target-role-matrix.md` open questions | 1 | 3 | Application blocker, weak evidence | Medium | Fill a short facts checklist before applications | Confirmed constraints list | No: update during issue #9 or application prep |
| WS-012 | Product/customer-discovery discipline | RefineBridge should not become build-only preparation | `learning-system-plan.md`, handoff, and `refinebridge-case-study.md` warn against unsupported traction claims | 1 | 3 | Product blocker, weak evidence | Medium | Write one customer-discovery question set or log one conversation | Discovery artifact or decision note | No: update mainly during issue #10 |
| WS-013 | React adaptation | Many .NET full-stack roles use React, even when Vue/Nuxt is the current strength | `target-role-matrix.md` repeated requirements summary | 1 | 2 | Market demand, role-specific | Medium | Do a small React reading/drill only after first target roles demand it | Tiny comparison note or component drill | No |
| WS-014 | Cloud/Azure confidence | Azure, cloud deployment, queues, CI/CD, and observability recur in roles | `target-role-matrix.md` repeated requirements summary | 2 | 3 | Market demand, weak evidence | Medium | Tie one existing project flow to Azure/cloud concepts without overclaiming | One architecture note or answer draft | Maybe: update if diagnostic touches cloud |
| WS-015 | Frontend state management | Server data, global state, feature coordination, local UI state, and URL state are not yet distinguished cleanly under interview pressure | `frontend-diagnostic-session-001.md` Q2: strong composable/store pattern, but URL state was unfamiliar and local state was initially over-associated with Pinia | 2 | 3 | Market demand, interview blocker, concision | High | Classify state for one import-flow list and justify `useAsyncData`, composable, Pinia, refs, and route query choices | One state-placement table plus 60-second explanation | Frontend baseline: 2/4 on 2026-06-20 |
| WS-016 | Frontend accessibility and semantic HTML | Native link/button semantics, keyboard focus, nested controls, announcements, and non-color status cues are not yet usable independently | `frontend-diagnostic-session-001.md` Q8-Q9: repository code-reading 1-2/4; coaching answer not yet demonstrated | 1 | 3 | Market demand, low score, interview blocker, WCAG risk | High | Repair and independently explain a clickable-card pattern with semantic links/buttons, `:focus-visible`, keyboard use, and an independent dropdown | Code/pseudocode, keyboard checklist, and later unprompted explanation | New weak spot from #14 |
| WS-017 | Frontend testing strategy | Historical frontend had no automated tests; current repo has 70 Vitest specs but test-layer strategy remains unclear | `frontend-diagnostic-session-001.md` Q7 and current frontend test inventory | 2 | 3 | Market demand, weak evidence, interview blocker | High | Classify five existing specs and design one missing component/integration/E2E test for a critical workflow | Test taxonomy note plus one implemented or sketched higher-level test | Historical gap confirmed; current unit-test progress verified |
| WS-018 | Loading, stale-data, and realtime recovery UX | Initial loading and typed errors are familiar, but empty, background refresh, stale data, and disconnection behavior are not yet explained as a coherent state model | `frontend-diagnostic-session-001.md` Q4: 1-2/4 answers | 2 | 3 | Market demand, failure-mode awareness, interview blocker | Medium | Design a state table for an import-flow list with cached data, refresh failure, and SignalR disconnect/reconnect | UI state table plus recovery actions | New weak spot from #14 |
| WS-019 | TypeScript runtime boundaries | Strong compile-time TypeScript confidence, but generic API types can still give false confidence about runtime JSON | `frontend-diagnostic-session-001.md` Q6: concrete rename/tooling example; runtime mismatch understood after follow-up | 2 | 3 | Market demand, correctness, weak evidence | Medium | Explain and demonstrate runtime validation for one external/API payload | Typed schema/parser example plus failure test | Frontend baseline: 3/4 follow-up; implementation rep pending |

## Re-Scoring Rules

Re-score a weak spot when:
- a mock/interview answer is scored
- a drill is completed
- a mentor or peer gives feedback
- an artifact is revised
- a job ad or recruiter call exposes a new requirement
- issue #12 produces the first diagnostic interview output

Do not raise a score for reading alone. Raise it only when the output improves.

## After Issue #12

When the deferred diagnostic interview is complete, update:
- `Current score`
- `Priority`
- `Next practice action`
- `Required output`
- any weak spots that were not visible from current notes

Do not wait for #12 to use this tracker. The seed weak spots above are enough to start lightweight practice now.
