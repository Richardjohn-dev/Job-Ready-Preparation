# Weak-Spot Tracker

Current as of 2026-06-02.

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
| WS-001 | Story, communication, and business impact | Concise 30-second self/project explanation under pressure | No formal interview history; `modern-dotnet-interview-readiness-map.md` says interview mechanics are missing | 1 | 3 | Market demand, low score, anxiety, interview blocker | High | Record a 30-second intro and one RDrive explanation, then rewrite once | Recording notes plus improved answer draft | Yes: replace estimate with diagnostic score |
| WS-002 | Story, communication, and business impact | RDrive business-impact/result statements are still weak | `behavioral-story-bank.md` repeatedly flags weak result sections and missing before/after examples | 2 | 3 | Market demand, weak evidence, interview blocker | High | Rewrite one DataBridge answer using Problem -> Constraint -> Decision -> Tradeoff -> Result | One improved answer and one business-impact bullet | Yes: confirm which result examples held up live |
| WS-003 | Behavioral stories | Missing concrete facts for origin, stakeholder estimate, refactor, feedback, Vue learning, and burnout/growth path | `behavioral-story-bank.md` missing-info checklist | 1 | 3 | Weak evidence, interview blocker | High | Pick one story gap and fill only confirmed facts or mark `needs confirmation` | Updated note or question list for Richard | Yes: add confirmed facts from live answers |
| WS-004 | Interview mechanics | Formal interview pressure and one-question-at-a-time practice | User context says no formal interview exposure; `codex-interviewer-workflow.md` defers first diagnostic to #12 | 0 | 3 | Low score, anxiety, interview blocker | High | Run one short mock session only when explicitly requested | Session notes with score, weakest part, next action | Yes: use #12 as first real baseline |
| WS-005 | Solo ownership and team-readiness framing | Need to explain mostly solo work without sounding defensive or overclaiming | `behavioral-story-bank.md` Story 4 gaps; handoff notes limited formal team process | 1 | 3 | Market demand, anxiety, weak evidence | High | Draft a 60-second answer focused on autonomy, feedback seeking, and desired team practices | Answer draft plus missing collaboration examples | Yes: revise with real diagnostic feedback |
| WS-006 | RefineBridge implementation certainty | Many implementation details are repo-inspection or human-confirmation gaps | `refinebridge-case-study.md` marks WorkOS, Lemon Squeezy, providers, jobs, credits, and production status as cautious | 1 | 3 | Weak evidence, interview blocker, product blocker | High | Inspect repo or ask Richard before using implementation-specific claims | Verified implemented/planned/unknown list | Yes: update if RefineBridge is tested in #12 |
| WS-007 | Practical coding aloud | Need baseline for practical .NET/TypeScript drills and talking while coding | `learning-system-plan.md` and readiness map call for drills; no practice-log entries yet | 1 | 3 | Market demand, low score, interview blocker | High | Complete one small API/query/debugging drill and explain the solution aloud | Drill result, tests/notes, confidence change | Yes: update if #12 exposes coding-related issues |
| WS-008 | System design and architecture explanation | Need concrete examples for background jobs, idempotency, retries, auth, billing, and tradeoffs | Target roles repeat architecture/reliability; case studies have strong raw material but not all answer drills | 2 | 3 | Market demand, weak evidence, interview blocker | High | Explain one DataBridge or RefineBridge subsystem in 5 minutes | Answer outline plus follow-up questions | Yes: re-score after diagnostic architecture question |
| WS-009 | Testing, debugging, and reliability proof | Need stronger evidence around tests, runbooks, incident-style answers, and production debugging | `modern-dotnet-interview-readiness-map.md` lists reliability as core proof; story bank lacks specific incidents | 1 | 3 | Market demand, weak evidence, interview blocker | High | Write one sync-failure or billing-webhook debugging answer | Debugging answer using symptom/risk/checks/hypotheses/fix/prevention | Yes: revise from #12 debugging prompt if used |
| WS-010 | External feedback and networking loop | Preparing alone is a known risk | `learning-system-plan.md` and handoff emphasize mentor/feedback loops | 1 | 3 | Anxiety, weak evidence, application blocker | Medium | Book or plan one narrow feedback action | Feedback request draft or call notes | No: update after issue #8 or real feedback |
| WS-011 | Hiring logistics and constraints | Location, work authorization, timezone, salary/rate, and public links are still open | `target-role-matrix.md` open questions | 1 | 3 | Application blocker, weak evidence | Medium | Fill a short facts checklist before applications | Confirmed constraints list | No: update during issue #9 or application prep |
| WS-012 | Product/customer-discovery discipline | RefineBridge should not become build-only preparation | `learning-system-plan.md`, handoff, and `refinebridge-case-study.md` warn against unsupported traction claims | 1 | 3 | Product blocker, weak evidence | Medium | Write one customer-discovery question set or log one conversation | Discovery artifact or decision note | No: update mainly during issue #10 |
| WS-013 | React adaptation | Many .NET full-stack roles use React, even when Vue/Nuxt is the current strength | `target-role-matrix.md` repeated requirements summary | 1 | 2 | Market demand, role-specific | Medium | Do a small React reading/drill only after first target roles demand it | Tiny comparison note or component drill | No |
| WS-014 | Cloud/Azure confidence | Azure, cloud deployment, queues, CI/CD, and observability recur in roles | `target-role-matrix.md` repeated requirements summary | 2 | 3 | Market demand, weak evidence | Medium | Tie one existing project flow to Azure/cloud concepts without overclaiming | One architecture note or answer draft | Maybe: update if diagnostic touches cloud |

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
