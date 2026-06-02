# Practice Log

Current as of 2026-06-02.

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
|  |  |  |  |  |  |  |  |  |  |  |

## Entries

No practice entries yet.

First useful entries to add:
- Record a 30-second intro or RDrive explanation.
- Rewrite one weak behavioral story result section.
- Complete one practical .NET drill with notes.
- Run a short Codex mock only when explicitly requested.
- Add #12 diagnostic results after that issue is completed.
