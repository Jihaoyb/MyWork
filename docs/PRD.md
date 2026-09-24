# MyWork product requirements

Review draft · 2026-09-24 · documentation/discovery phase

## Authority and problem

This document reconciles PROCESS.md with PRD-update.md and the initialization request. The update takes precedence; confirmed decisions are recorded in DECISIONS.md and suggestions in PROVISIONAL.md. This is a complete product-scope draft for review, not an assertion that discovery, design, implementation, or research has finished.

MyWork helps Jihao choose a realistic next action, begin it, preserve useful progress, stop deliberately, and resume from actual task state. Current needs include difficulty starting intended work, switching away from tempting alternatives, containing unplanned exploration, and stopping when absorbed. Support curiosity and concentration without moral judgments or inferred diagnoses.

On September 24, Jihao reported that none of the project work assigned by weekday planners had been started. Existing implementations elsewhere still exist. Study completion and unrelated career activity are unknown. This report does not establish task-by-task completion or inactivity and is not permission to import old assignments as overdue tasks.

## User and product direction

Initial user: Jihao, privately, with expressed personal preferences. A hosted Next.js + TypeScript app remains the product direction; the first trial environment is undecided. Later public usefulness is a direction, not approved audience scope. MyWork is also a portfolio project that should demonstrate explainable choices and honest engineering evidence. Broader psychological adaptation and public claims require research first.

Jobs to be done:

- When choosing work, identify one eligible task and a small concrete action.
- When starting, open its resource and define a stopping point without replanning everything.
- When interrupted or stopping, save what happened, the exact stopping point, and next action.
- When returning, resume the same unfinished task from the last known state.
- When blocked or skipping, change the plan honestly without inventing completion or debt.
- When a question tempts exploration, preserve its context for a deliberate later choice.

## First release scope

IN: persistent tasks, manually selected work, start/report/resume sessions, partial/skipped/blocked/completed/unreported outcomes, resumption notes, references and evidence, dependencies, optional saved questions, correctable history, and three simple views: Today, Progress, Review. One primary action is prominent while the broader plan stays available. No chat, essays, streaks, or extensive setup is required.

OUT: calendar writes, MCP access, external notifications, unattended supervision, social ingestion or posting, platform credentials, general module framework, public accounts/multi-user release, psychological profiling/adaptation, clinical claims, and engagement optimization. Infrastructure vendors and auth provider remain undecided. The milestone below is smaller than the complete first release.

## Core records and semantics

Logical requirements, not a database schema or approved state-enum design:

| Record | Required meaning |
| --- | --- |
| Task | Stable ID, observable outcome/definition of done, current status, concrete next action, relevant resource, and latest stopping context. |
| Session | Links to the existing task ID; captures start and intended stopping point, with its own outcome independent of task status. Skipping before start does not invent a start time. |
| Progress report | Timestamp, source/actor, reported outcome, progress/blocker and next action where applicable; relates to task/session and referenced evidence. |
| Evidence/reference | Resource or observation with provenance and confidence; distinguish self-report from independent verification. Evidence links are reusable. |
| Dependency | Prerequisite task and completion condition; prevents advancing dependent work prematurely. |
| Saved question | Optional interest with original context and a return reference, never an automatic obligation. |
| Change history | Traceable task/report changes and corrections; preserve what was corrected and when rather than silently rewriting history. |

Working semantics for review: tasks may be not started, in progress, blocked, or done, with deliberate pause supported; sessions may be active, partial, blocked, completed, explicitly not started/skipped, or unreported. Final enum design is deferred. A skipped session can belong to an already-in-progress task and must not reset it to not started. Ending a session is separate from completing the task. Report confidence is separate from both.

Self-reported completion is valid when the user reports the defined outcome achieved; independent verification is not mandatory for every task. A completion claim with unclear coverage needs reconciliation before unlocking dependents. Corrections that invalidate prerequisite completion must make dependent eligibility reflect the corrected state without erasing work already reported.

## Views and interaction requirements

**Today:** show one selected eligible task, its outcome, entry action, resource, and stopping point. Start creates a session attached to that task. Returning after partial/skipped work keeps the same task available unless the user explicitly chooses another priority. Support manual selection; do not require a scheduling engine.

**Progress:** show task state, dependencies, reports, evidence/source, stopping context, and exact next action. Separate proposed assignments from selected tasks. Explain why dependent work is unavailable. A blocker leads to an unblock action or deliberate pause.

**Review:** surface unresolved sessions and correctable reports. Missing feedback remains unreported, with last known state intact. Permit a status update or leaving it unknown. Avoid duplicate journals and mandatory explanations.

The reporting path accepts partial progress, a blocker, completion against the outcome, or explicit not-started/skipped work. Partial reports preserve a useful stopping point and next action. On resume, display that context before starting another session for the same task. Reports and references survive app closure and reopening; save failures must be visible and must not claim persistence. Preserve entered content for retry. Duplicate submission must not create duplicate reports or sessions.

## Hard invariants

1. Schedules, calendar attendance, elapsed timers, generated plans, and missing feedback never complete tasks.
2. Missing feedback remains unreported; preserve last known task state and flag reconciliation.
3. Dependent work is unavailable until prerequisites are reported or evidenced complete against their definitions of done.
4. Self-report remains distinguishable from independent verification. A commit alone does not prove an entire objective; absence of commits does not prove inactivity.
5. Existing generated assignments remain proposals until selected. Missed sessions can be rescheduled, reduced, paused, or replaced by a verified priority without invented progress.
6. Partial and skipped sessions preserve task identity. New sessions do not duplicate or silently advance the task.
7. Timers cannot silently extend sessions or mark work complete. Ignoring or dismissing a timer changes no task state.
8. Do not infer psychological state from inactivity, punish missed sessions, or repeatedly demand attention after dismissal. Reasons are optional.
9. The app makes no clinical diagnosis or treatment claims. Broader personalization is research-gated.
10. Future publishing requires explicit approval of the specific item on the specific platform; private notes and preferences are excluded from sharing by default.

## Check-ins and accountability

Start should expose an already-prepared entry action; closing prepares the next one. Example: “Open the failing test and run it once.” A resumption note can read “At section 3; next explain why unlimited retries amplify overload.” Support deliberate deeper work and chosen finish times.

The one-week, one-important-session-per-day routine; five-minute entry; 25-minute initial duration; 10-second start; 20–30-second close; and one-minute evening review are provisional trials, not fixed requirements or demonstrated outcomes. See PROVISIONAL.md. Protect user autonomy and existing meals, interviews, and finish times. Optional extensions must be bounded and explicitly selected.

Initial notifications are dashboard-only. The closed app provides no proactive supervision. Frequency, quiet hours, and reminder controls require discovery before reminders are relied on. No external reminder, recurring task, or contact is authorized.

## Quality and privacy

Use clear module boundaries; build a framework only with the second module. Retain professional standards with scope appropriate to delivery: access control, error handling, meaningful tests, CI/CD, observability, and backup/recovery. Choose concrete mechanisms after the delivery decision. Before any hosted exposure, verify private access enforcement; before depending on storage, define recovery and migration behavior.

Keep secrets out of Git and production credentials out of previews. If Supabase is selected, apply the original RLS/server-only credential requirements; this does not select Supabase. Authenticate every eventual job route and verify webhook signatures. Flag potential costs before provisioning. Do not modify the portfolio repository.

Support preferences and personal notes are private by default. Decide retention, deletion/export, correction behavior, and any future sharing explicitly before implementing the affected features. A public release requires verified isolation of each user's data. Accessibility and interaction details require a focused design pass; do not infer support needs from diagnostic labels.

## Acceptance and success measures

Before advancing beyond the core loop, demonstrate with recorded evidence:

| Scenario | Required result |
| --- | --- |
| Choose and start | A selected task has a stable ID, outcome, next action, resource, and intended stopping point; its session references that ID. |
| Stop partway | Report partial progress and exact next action; the next session displays the saved context and references the same task. |
| Skip / do not start | Explicit skip records no invented work; an already-in-progress task retains its state. Resume uses the same task, with no duplicate. |
| No feedback | Session stays unresolved/unreported; task state and prerequisite eligibility do not advance. |
| Blocker | Plan offers an unblock action or pause and does not unlock dependent implementation. |
| Timer dismissed/ignored | Task state is unchanged; no silent extension. Test when a timer exists; absence of a timer does not require adding one to milestone one. |
| Tangent | Save the question with context and return to the original step. Required in the first release, not the smaller first milestone. |
| Reopen | Saved task state, reports, references, and resumption context persist. |
| Correct or retry report | Corrections remain traceable; duplicate submission does not duplicate records; failed save is visible. |

During the first week of actual use, examine reported starts, useful progress toward outcomes, ease of resumption, chosen stopping boundaries, and perceived check-in burden. Choose the primary criterion with Jihao; no numerical targets are yet ratified. Do not equate elapsed time with concentration or optimize total hours, streaks, or app engagement. Change one setting at a time based on feedback.

## Later integrations and social publishing

After manual state rules work: calendar represents time reservations, MyWork remains authoritative, and one writer owns calendar changes. MCP reads state and submits validated updates with provenance and duplicate protection; it cannot bypass dependency/completion rules. Verify both interactive and scheduled connector access before migrating planning.

Publishing later retains Lab Atom/GitHub change ingestion, SHA-gate reference pattern, repository/day digest with releases/tags always queued, editable per-platform drafts, approval, independent delivery states including partial success, retry/backoff, idempotency, connected-account health/reconnect, stored platform IDs/URLs and outbound attribution, authenticated jobs, verified webhooks, and a kill switch on every publish path. Validate current platform access/policies and token behavior then. Retain source/item/draft/review/publication/attempt distinctions. Post-publish editing and dashboard deletion are OUT of the initial progress release; their later publishing scope remains explicitly unresolved. Treat remote platform state as potentially divergent.

Optional manual draft/copy export attached to completed evidence can be considered after the loop works; no ingestion or credentials needed. It is not approved milestone-one scope. The old first-post-by-M3 deadline is retired.

## Research gate

Deep review has not been performed. Before broader personalization design or implementation, produce an evidence map covering task initiation/avoidance, attention switching, prospective memory, time estimation, deep absorption/disengagement, notification fatigue, accountability, and accessibility. Include populations, study quality, mechanisms, limitations, and unresolved questions; distinguish adult/child evidence, preferences/measured outcomes, and short/sustained use.

Conduct participatory research with intended users and appropriate professional input for mental-health-related features or claims. Evaluate usefulness, burden, annoyance, autonomy, unintended effects, and longer-term use. Resolve consent, private notes/preferences, export/deletion, sharing, and public data isolation. Supports should reflect expressed needs rather than inferred diagnoses or fixed personality categories. The source addendum lists initial references; they have not been independently reviewed in this initialization and do not establish this app's effectiveness.

## Review dependencies

See DECISIONS.md for the four pending foundational questions and ROADMAP.md for the proposed first milestone. Before implementation, resolve its delivery/persistence/access choices and produce a focused ARCHITECTURE.md with reasons, record model, boundaries, and security design. No provider, schema, research conclusion, or deployment is implicitly approved by this PRD.
