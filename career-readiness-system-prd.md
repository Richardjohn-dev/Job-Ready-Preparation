# Career Readiness System PRD

Current as of 2026-06-01.

Status: rough capture. This is intentionally broad and imperfect. Its job is to get the ideas down so they can be split into smaller implementation plans later.

## Problem Statement

The user has real engineering experience, especially solo ownership of integration-heavy .NET/full-stack systems, but does not currently have a reliable system for turning that experience into job interviews, interview performance, or market confidence.

The core problems are:

- No current CV/resume.
- LinkedIn needs repositioning.
- No established interview process experience.
- No clear funnel for getting interviews.
- Difficulty explaining complex past work concisely.
- Too much solo calibration and not enough external feedback.
- Anxiety around unknown weak spots.
- Risk of preparing by consuming resources instead of producing evidence.
- Need to balance job readiness, RefineBridge/product work, communication skill, and optionality.

The user does not need to start from zero technically. The gap is packaging, calibration, structured practice, feedback, and targeted improvement.

## Solution

Build a local-first career readiness operating system.

The system should help the user:

- Turn past work into credible hiring material.
- Get interview-visible through CV, LinkedIn, role targeting, and outreach.
- Diagnose weak spots through realistic practice.
- Use real projects as interview material.
- Practice explaining decisions with business impact.
- Track time, resources, artifacts, feedback, and progress.
- Avoid over-focusing on LeetCode unless target roles require it.
- Build optionality between employment, consulting, RefineBridge, and future SaaS work.

The first version should stay in local Markdown files. A Notion dashboard or app can come later after the workflow has been proven manually.

## Product Principles

1. Artifacts over passive study.
2. Feedback loops over perfect plans.
3. Real project evidence over generic interview theater.
4. Practical .NET/full-stack/SaaS readiness over FAANG-style algorithm grinding.
5. Concise business communication over long technical monologues.
6. External feedback over solo guessing.
7. Local-first until the workflow is stable.
8. Use paid help only for direct feedback, not motivation or vague transformation.

## Core Outcome

The user should be able to:

- Send a credible CV.
- Have a LinkedIn profile that clearly explains their value.
- Explain RDrive DataBridge and RefineBridge in 30 seconds, 2 minutes, and 10 minutes.
- Answer project, architecture, behavioral, debugging, and stakeholder questions without freezing.
- Apply to suitable roles with a tracked process.
- Identify weak spots from evidence.
- Improve weak spots through focused practice.
- Use Codex as a project-aware interviewer and coach.

## User Stories

1. As a job-seeking developer, I want a clear target-role definition, so that I do not prepare for the wrong job market.
2. As a job-seeking developer, I want a target-role matrix, so that I can compare real market demand instead of guessing.
3. As a job-seeking developer, I want repeated job-ad requirements extracted, so that I know which skills matter most.
4. As a job-seeking developer, I want roles grouped by fit, so that I can focus on realistic opportunities first.
5. As a job-seeking developer, I want a CV draft, so that I can start getting feedback and applying.
6. As a job-seeking developer, I want different CV versions, so that I can target backend, full-stack, SaaS, and integration-heavy roles.
7. As a job-seeking developer, I want LinkedIn headline options, so that my profile communicates my value quickly.
8. As a job-seeking developer, I want a LinkedIn About section, so that recruiters understand my background without needing context.
9. As a job-seeking developer, I want a clean Snagr/RDrive work-history framing, so that the non-standard employment structure does not weaken the story.
10. As a job-seeking developer, I want project experience bullets, so that complex work becomes readable hiring evidence.
11. As a job-seeking developer, I want business-impact bullets, so that I sound commercially useful rather than task-focused.
12. As a job-seeking developer, I want an application tracker, so that I know what I applied to and what changed.
13. As a job-seeking developer, I want a recruiter screen script, so that early calls do not feel improvised.
14. As a job-seeking developer, I want salary/location/availability answers, so that I can handle basic screening questions.
15. As a job-seeking developer, I want a warm outreach script, so that I can contact recruiters, mentors, and hiring managers without sounding vague.
16. As a job-seeking developer, I want a feedback request template, so that I can ask useful questions instead of asking for generic mentorship.
17. As a job-seeking developer, I want a weekly application rhythm, so that getting interviews becomes a process rather than a mystery.
18. As a job-seeking developer, I want rejection/no-response notes, so that each market signal improves my materials.
19. As a job-seeking developer, I want interview-stage notes, so that I understand how each company evaluates candidates.
20. As a job-seeking developer, I want debriefs after interviews, so that weak spots are captured immediately.

21. As an interview candidate, I want a 30-second intro, so that I can answer "tell me about yourself" without rambling.
22. As an interview candidate, I want a 2-minute project explanation, so that I can explain complex work clearly.
23. As an interview candidate, I want RDrive DataBridge explained at product level, so that business stakeholders understand the value.
24. As an interview candidate, I want RDrive DataBridge explained at engineering level, so that technical interviewers see depth.
25. As an interview candidate, I want RefineBridge explained at product level, so that it sounds like a real SaaS/product effort.
26. As an interview candidate, I want RefineBridge explained at architecture level, so that it can support system-design conversations.
27. As an interview candidate, I want reusable story structures, so that behavioral answers are not invented live.
28. As an interview candidate, I want stories shaped as Problem -> Constraint -> Decision -> Tradeoff -> Result, so that answers are concise and senior.
29. As an interview candidate, I want STAR stories when appropriate, so that people/process questions have clear structure.
30. As an interview candidate, I want a story bank, so that common questions map to prepared examples.
31. As an interview candidate, I want a business-impact story bank, so that I can talk about risk, time, cost, reliability, and revenue.
32. As an interview candidate, I want a stakeholder-estimation story, so that I can explain provider integration uncertainty maturely.
33. As an interview candidate, I want a solo-ownership story, so that working alone becomes a strength rather than a concern.
34. As an interview candidate, I want a burnout/growth-path story, so that I can explain career transition honestly without sounding negative.
35. As an interview candidate, I want a "project underuse" story, so that I can explain product adoption as outside engineering ownership.
36. As an interview candidate, I want a "changed product direction" story, so that I can show adaptability.
37. As an interview candidate, I want a "requirements were ambiguous" story, so that I can show ownership under uncertainty.
38. As an interview candidate, I want a "refactored while delivering" story, so that I can show incremental architecture judgment.
39. As an interview candidate, I want a "learned new technology under pressure" story, so that first-time SPA/Vue experience becomes evidence.
40. As an interview candidate, I want recorded answers, so that I can hear rambling and improve.

41. As an interview candidate, I want Codex to inspect my project notes, so that practice questions use my real experience.
42. As an interview candidate, I want Codex to inspect project code where appropriate, so that questions are grounded in implementation.
43. As an interview candidate, I want one interview question at a time, so that practice feels realistic.
44. As an interview candidate, I want follow-up questions, so that weak answers get pressure-tested.
45. As an interview candidate, I want scored answers, so that progress is visible.
46. As an interview candidate, I want improved answer versions, so that every session produces a better artifact.
47. As an interview candidate, I want Codex to ask "why did you choose X?", so that architectural decisions become defensible.
48. As an interview candidate, I want Codex to ask "what would fail?", so that reliability thinking improves.
49. As an interview candidate, I want Codex to ask "what did the business care about?", so that answers avoid pure implementation detail.
50. As an interview candidate, I want Codex to run project walkthrough interviews, so that I can explain projects at different depths.
51. As an interview candidate, I want Codex to run architecture grills, so that tradeoffs become clearer.
52. As an interview candidate, I want Codex to run behavioral interviews, so that common stories become smoother.
53. As an interview candidate, I want Codex to run debugging interviews, so that incident and reliability answers improve.
54. As an interview candidate, I want Codex to run stakeholder interviews, so that I can translate technical work into business terms.
55. As an interview candidate, I want Codex to track weak spots from each session, so that practice leads to a learning plan.
56. As an interview candidate, I want each session to save one artifact, so that practice is never passive.
57. As an interview candidate, I want a reusable prompt library, so that future practice sessions are easy to start.
58. As an interview candidate, I want interview sessions linked to skill trees, so that practice updates the broader plan.
59. As an interview candidate, I want question banks for RDrive DataBridge and RefineBridge, so that real experience drives preparation.
60. As an interview candidate, I want answer scores over time, so that pressure-handling progress is visible.

61. As a learner, I want skill trees, so that preparation is organized without becoming abstract.
62. As a learner, I want subskills under each tree, so that vague goals become specific practice targets.
63. As a learner, I want weak-spot scores from 0-4, so that I know what needs work.
64. As a learner, I want weak spots prioritized by market relevance, anxiety, evidence, and score, so that effort goes where it matters.
65. As a learner, I want a practice log, so that minutes are tracked only when paired with output.
66. As a learner, I want each practice log to include an artifact, so that study translates into proof.
67. As a learner, I want resources attached to subskills, so that I know what to use and when.
68. As a learner, I want one primary resource per subskill, so that I do not collect endless courses.
69. As a learner, I want paid resources filtered by usefulness, so that money is spent on feedback rather than vague motivation.
70. As a learner, I want a diagnostic sprint, so that real weak spots are discovered before committing to a large roadmap.
71. As a learner, I want a weekly review, so that progress and next actions stay visible.
72. As a learner, I want a time split, so that job readiness, RefineBridge, communication, and networking all get attention.
73. As a learner, I want a first-30-days plan, so that the system starts with concrete action.
74. As a learner, I want a six-month roadmap, so that preparation has direction beyond the current week.
75. As a learner, I want technical gap audits, so that .NET/frontend/system-design weaknesses are explicit.
76. As a learner, I want practical coding drills, so that interviews are not only theoretical.
77. As a learner, I want light DSA practice, so that basic coding screens do not cause panic.
78. As a learner, I want system-design case studies, so that architecture interviews use real projects.
79. As a learner, I want runbooks and debugging stories, so that reliability maturity is visible.
80. As a learner, I want security/auth/SaaS-boundary notes, so that trust and tenancy questions are not fuzzy.

81. As a product builder, I want RefineBridge kept in the plan, so that job readiness does not erase long-term optionality.
82. As a product builder, I want customer discovery tasks, so that product direction is based on market evidence.
83. As a product builder, I want SaaS/sales resources mapped, so that RefineBridge can improve without random content consumption.
84. As a product builder, I want offer and objection notes, so that customer conversations become useful.
85. As a product builder, I want a consulting-bridge option, so that income and product learning can support each other.
86. As a product builder, I want to compare job, consulting, SaaS, and hybrid paths, so that optionality remains the core goal.

87. As a future dashboard user, I want high-level progress by learning tree, so that I can see where I am improving.
88. As a future dashboard user, I want top weak spots visible, so that weekly focus is obvious.
89. As a future dashboard user, I want practice minutes by category, so that effort distribution is visible.
90. As a future dashboard user, I want artifacts linked to learning goals, so that proof of progress is easy to review.
91. As a future dashboard user, I want interview sessions linked to questions and answers, so that improved responses can be found.
92. As a future dashboard user, I want resources linked to produced artifacts, so that resources are judged by output.
93. As a future dashboard user, I want mentor feedback linked to revisions, so that external advice changes the plan.
94. As a future dashboard user, I want application/interview outcomes linked to materials used, so that market feedback improves CV and LinkedIn.
95. As a future dashboard user, I want a weekly review view, so that planning stays lightweight.
96. As a future dashboard user, I want the system to stay simple, so that maintaining the dashboard does not replace doing the work.

## Implementation Decisions

### Local-First System

The first version will be a set of local Markdown artifacts. This avoids spending early effort on dashboards, databases, automations, or Notion structure before the workflow has been tested.

### Treat This As An Operating System, Not A Course

The system is not a static curriculum. It is a feedback loop:

1. Diagnose a weak spot.
2. Pick a focused practice action.
3. Produce an artifact.
4. Get feedback or self-score.
5. Update the weak-spot score.
6. Choose the next action.

### Main Modules

The system has these conceptual modules:

- Career positioning.
- Hiring funnel.
- Target-role research.
- CV and LinkedIn material.
- Project story bank.
- Business-impact translation.
- Codex interviewer sessions.
- Skill trees.
- Weak-spot tracker.
- Practice log.
- Resource library.
- Feedback and mentorship tracker.
- Application and interview tracker.
- RefineBridge product/customer-discovery track.
- Weekly review.
- Future dashboard layer.

### Initial Skill Trees

The main learning trees are:

- Hiring funnel.
- Interview mechanics.
- Modern .NET backend.
- Architecture and system design.
- Integrations, webhooks, and external APIs.
- Testing, debugging, and reliability.
- Security, auth, and SaaS boundaries.
- Frontend/Nuxt/Vue 3.
- Communication and business impact.
- Networking, mentorship, and feedback.
- Product, SaaS, sales, and customer discovery.
- AI-assisted engineering and interview practice.

### Target Role Bias

The system should bias toward roles where existing experience is strongest:

- Full-stack .NET engineer.
- Backend .NET engineer.
- SaaS/product engineer.
- Integrations/platform engineer.
- Workflow automation/internal tools engineer.
- Remote .NET/Vue/Nuxt/Postgres roles.

FAANG-style algorithm-heavy preparation is not the default path unless the target role matrix proves it is necessary.

### Answer Framework

The default answer shape for project/design/business questions is:

- Problem.
- Constraint.
- Decision.
- Tradeoff.
- Result.

STAR remains useful for explicit behavioral people/process questions, but it should not replace the clearer engineering decision format.

### RDrive DataBridge Positioning

RDrive DataBridge should be positioned as multi-year commercial integration-platform ownership.

Safe claim:

- Long-term independent developer/contractor for Snagr/RDrive.
- Owned integration-heavy product work.
- Built core platform capabilities for RDrive DataBridge.
- Implemented and supported integrations across Aconex, Azure Blob Storage, Autodesk, and Asite.

Boundary:

- Do not claim ownership of sales, marketing, adoption, or client conversion.
- Do not claim SharePoint or 4Projects implementation unless evidence confirms it.
- Do not lead with informal employment context; explain it plainly if asked.

### RefineBridge Positioning

RefineBridge should be used as the modern stack/product case study.

It can support discussion of:

- .NET backend.
- Nuxt/Vue 3 frontend.
- PostgreSQL.
- Modular monolith structure.
- DDD-informed boundaries.
- Background jobs.
- Integrations.
- Billing/webhooks.
- Credits/BYOK.
- Auth/account boundaries.
- Admin workflows.
- Product/customer uncertainty.

### Codex Interviewer

Codex should act as a repo-aware interviewer later, but the first version can operate from existing notes.

Session types:

- Project walkthrough.
- Architecture and tradeoff grill.
- Behavioral/story simulator.
- Reliability/debugging interview.
- Business/stakeholder interview.
- Code-backed interview.

Every session must produce at least one artifact:

- Better answer.
- Weak-spot note.
- Case-study bullet.
- ADR.
- Runbook.
- Practice-log entry.

### Resource Use

Resources should be attached to subskills and judged by artifacts produced.

Default rule:

- Free/official/reference sources first.
- Paid help only for direct feedback.
- One primary resource per subskill at a time.
- No passive binge-watching.

### Weak-Spot Scoring

Use a 0-4 score:

- 0 = missing or unknown.
- 1 = recognizable when reading, but not explainable/doable cleanly.
- 2 = doable slowly with notes.
- 3 = doable without notes in relaxed setting.
- 4 = doable under interview pressure with evidence/feedback.

Priority is based on:

- Market demand.
- Current score.
- Anxiety level.
- Lack of evidence.
- Whether it blocks interviews, RefineBridge, or confidence.

### First Diagnostic Sprint

Before building a dashboard, run a diagnostic sprint.

Rough scope:

- Collect target job ads.
- Draft CV and LinkedIn.
- Record core answers.
- Run first Codex interview sessions.
- Do a few practical coding/debugging drills.
- Write business-impact bullets.
- Book at least one external feedback call.
- Score weak spots.
- Produce a short next-month plan.

### Future Dashboard

A Notion dashboard or similar system should only be built after the manual workflow has been used for a few weeks.

Potential dashboard databases:

- Learning trees.
- Subskills.
- Weak spots.
- Practice logs.
- Resources.
- Artifacts.
- Interview sessions.
- Question bank.
- Answer library.
- Feedback log.
- Applications.
- Weekly reviews.

## Testing Decisions

This is not a software feature yet, so "testing" means validating the workflow against real outcomes.

### Workflow Validation

The system is working if:

- CV v1 exists and can be sent.
- LinkedIn v1 clearly positions the user.
- A target-role matrix contains real roles.
- RDrive DataBridge can be explained clearly in 30 seconds.
- RefineBridge can be explained clearly in 30 seconds.
- At least one Codex interview session produces a better answer.
- Practice logs include artifacts, not just minutes.
- Weak-spot scores change based on evidence.
- External feedback is captured and causes revisions.
- The user applies to a small batch of roles and tracks outcomes.

### Interview Readiness Validation

Use mock sessions and recorded answers to test:

- Clarity.
- Concision.
- Technical accuracy.
- Business impact.
- Tradeoff awareness.
- Failure-mode awareness.
- Ownership.
- Calmness under follow-up questions.

### Hiring Funnel Validation

Use actual market response to test:

- Whether the CV gets recruiter or hiring manager attention.
- Whether LinkedIn profile views/messages improve.
- Whether target roles match the user’s experience.
- Whether repeated rejection points reveal missing skills or weak positioning.
- Whether outreach scripts get replies.

### Learning Validation

A learning activity is valid only if it produces one of:

- Improved answer.
- CV/LinkedIn bullet.
- Case study.
- ADR.
- Runbook.
- Coding drill.
- Mock interview feedback.
- Mentor feedback note.
- Customer discovery note.
- Application/interview insight.

### Future Software Testing

If this later becomes a Notion system, app, or Codex skill, test:

- Creating and updating practice logs.
- Linking weak spots to subskills and artifacts.
- Starting an interview session from a project/question bank.
- Saving session scores and improved answers.
- Generating weekly review summaries.
- Preventing duplicate or stale resource entries.
- Keeping private/sensitive project material out of public outputs.

## Out Of Scope

The following are out of scope for the rough PRD:

- Building a full Notion dashboard immediately.
- Building a custom web app immediately.
- Automating everything before the manual loop is proven.
- Buying expensive coaching/cohort programs.
- Heavy LeetCode or FAANG-specific preparation unless target roles require it.
- Public portfolio publishing before private story material is clean.
- Sharing confidential RDrive screenshots or client data.
- Claiming integrations or commercial outcomes that are not supported by evidence.
- Solving every career question before producing the first CV and LinkedIn draft.

## Rough Milestones

### Milestone 1: Capture And Position

Outcome:

- Central PRD exists.
- CV draft exists.
- LinkedIn draft exists.
- Target role families are chosen.
- RDrive and RefineBridge summaries exist.

### Milestone 2: Diagnose

Outcome:

- Target-role matrix has real roles.
- Core answers are recorded.
- Weak-spot scores exist.
- First Codex interview sessions are completed.
- First external feedback action is booked or completed.

### Milestone 3: Practice Loop

Outcome:

- Weekly practice log is active.
- Question bank is used.
- Story bank improves.
- Practical coding/debugging drills begin.
- System-design case studies are drafted.

### Milestone 4: Market Test

Outcome:

- Small batch of applications sent.
- Outreach messages sent.
- Responses tracked.
- CV/LinkedIn revised from market feedback.
- Interview preparation adjusts based on real signals.

### Milestone 5: Dashboard Decision

Outcome:

- Decide whether a Notion dashboard, local docs, or lightweight app would genuinely improve the workflow.
- Only build the dashboard if the manual process is already useful.

## Further Notes

The likely next concrete artifacts are:

- CV draft.
- LinkedIn profile draft.
- Target-role matrix.
- Application tracker.
- Recruiter screen script.
- RDrive DataBridge case study.
- RefineBridge case study.
- Weak-spot tracker.
- Practice log.

The strongest current positioning is not "junior trying to break in." It is:

> Full-stack .NET/Nuxt engineer with real ownership of integration-heavy SaaS and document/data workflow systems, now packaging that experience into a more conventional hiring story.

The main risk is not lack of ability. The main risk is staying invisible, under-explaining the work, preparing alone, and delaying market feedback.

