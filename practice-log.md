# Practice Log

Current as of 2026-06-19.

Purpose: append-only log for practice minutes, outputs, confidence changes, and next actions. Minutes only count when practice produces an artifact, answer, drill result, application action, outreach action, or feedback loop.

## Rule

Do not log passive study by itself.

Bad:

```text
Watched videos for 2 hours.
```

Good:

```text
Watched 20 minutes on ASP.NET Core middleware, then wrote a 10-line request-pipeline explanation and answered one practice question.
```

## Activity Types

Use one of:
- `study-with-output`
- `build`
- `explain`
- `mock`
- `coding-drill`
- `debugging-drill`
- `rewrite`
- `outreach`
- `application`
- `review`
- `feedback`

## Confidence Scores

Use the same 0-4 scale as `weak-spot-tracker.md`.

| Score | Meaning |
| --- | --- |
| 0 | Missing, unknown, no reps, or unsafe to claim from current evidence. |
| 1 | Recognizable when reading notes, but cannot explain, perform, or defend it cleanly yet. |
| 2 | Can explain or perform slowly with notes, but weak under pressure or missing concrete evidence. |
| 3 | Can explain or perform without notes in a relaxed setting, with clear structure and reasonable evidence. |
| 4 | Can handle it under interview pressure, with concise delivery, evidence, tradeoffs, and feedback-backed confidence. |

## Log Template

Copy this block for each entry.

```markdown
## YYYY-MM-DD - Short activity title

- Date:
- Tree:
- Subskill:
- Weak spot ID:
- Minutes:
- Activity type:
- Resource used:
- Artifact/output produced:
- Confidence before:
- Confidence after:
- What improved:
- What still failed:
- Feedback received:
- Next action:
- Update after #12:
```

## Quick Table

Use this table if a compact view is easier. Keep the detailed entries below when the session produced useful notes.

| Date | Tree | Subskill | Weak spot ID | Minutes | Activity type | Resource | Artifact/output | Confidence before | Confidence after | Next action |
| --- | --- | --- | --- | ---: | --- | --- | --- | --- | --- | --- |
| 2026-06-19 | Interview mechanics | RDrive project walkthrough and architecture | WS-001, WS-002, WS-003, WS-004, WS-005 | Not recorded | mock | `codex-interviewer-workflow.md` and RDrive case study | `diagnostic-interview-session-001.md`; confirmed improved answer | 0 | 2 | Re-deliver improved answer in 30-45 seconds |

## Entries

## 2026-06-19 - First RDrive DataBridge Diagnostic

- Date: 2026-06-19
- Tree: Interview mechanics; story, communication, and business impact
- Subskill: Project walkthrough, architecture tradeoffs, estimation, and solo risk management
- Weak spot ID: WS-001, WS-002, WS-003, WS-004, WS-005
- Minutes: Not recorded
- Activity type: mock
- Resource used: `codex-interviewer-workflow.md`, `rdrive-databridge-case-study.md`, and interview practice packs
- Artifact/output produced: `diagnostic-interview-session-001.md`; confirmed improved DataBridge answer copied to the RDrive case study
- Confidence before: 0 for formal mock baseline
- Confidence after: 2
- What improved: Confirmed the manual workflow, mapping model, provider-discovery risk, provider-neutral architecture, and local/dev regression process; produced one structured answer.
- What still failed: Concision, consistent terminology, explicit results/tradeoffs, uncertain Asite/Autodesk timing, and evidence around automated tests and production controls.
- Feedback received: Raw answers scored 2/4 to 3/4. Strong technical recall and truthfulness; structure and answer length need work.
- Next action: Deliver the improved answer aloud in 30-45 seconds, then practice a 60-second provider-estimation answer.
- Update after #12: First live baseline completed; weak spots re-scored.
