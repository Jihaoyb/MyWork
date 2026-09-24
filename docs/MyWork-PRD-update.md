# MyWork — PRD update

Decision date: September 24, 2026

This focused addendum records the decisions from the current conversation and revises the direction in the supplied MyWork kickoff brief. It is not a claim that a complete PRD, repository, or application has been implemented. Integrate it into the repository's PRD, decisions, and roadmap during the next documentation session.

## 1. Confirmed direction

**Purpose:** MyWork helps Jihao choose a realistic next action, begin it, preserve useful progress, stop deliberately, and resume from actual task state. Calendar plans must follow that state.

| Decision | Status |
| --- | --- |
| Progress tracking and daily execution become the first module. | Confirmed by user |
| Initial release is private and customized for Jihao. | Confirmed by user |
| A later public product should support people with similar difficulties and different support preferences. | Confirmed direction; audience and feature scope require research |
| Social publishing remains on the roadmap. | Confirmed by user |
| Deep psychological, behavioral, and mental-health research must precede broader personalization design and implementation. | Confirmed requirement for a later improvement stage |
| Exact check-in timings, reminder behavior, and focus periods below. | Provisional recommendations to trial |

The current functional needs are difficulty starting intended work, shifting away from tempting alternatives, containing unplanned deep exploration, and stopping once absorbed. Preserve curiosity and sustained concentration while helping the user choose when to explore. The product should describe these needs without moral judgments or inferred diagnoses.

Current project baseline: on September 24, Jihao reported that none of the project work assigned by the weekday planners had been started. Existing repository implementations still exist. Study completion and unrelated career activities remain unknown unless separately reported or evidenced.

## 2. Smallest useful release

The first usable release must support this complete loop:

1. Select one current task with a stable ID, observable outcome, and next action.
2. Show a small entry action and the relevant file, page, or resource.
3. Start a session with an intended stopping point.
4. Record partial progress, a blocker, completion, or a decision not to start.
5. Resume the same unfinished task next time without duplicating or advancing it.

Use three simple views: **Today**, **Progress**, and **Review**. Show one primary action prominently; allow the broader plan to remain available without presenting every project as immediately actionable.

Core records: task, session, progress report, evidence/reference, dependency, and saved question. A report records its source and timestamp. Separate task status from session outcome and evidence confidence. Keep an auditable, correctable history of changes.

### Progress invariants

- A scheduled session, elapsed timer, calendar attendance, or assistant-generated plan does not complete a task.
- Missing session feedback means the outcome is unreported. Preserve the last known task state and flag that reconciliation is needed.
- A dependent task remains unavailable until its prerequisites are reported or evidenced complete against their definitions of done.
- Self-reported completion is valid information and must remain distinguishable from independently verified evidence. A commit alone is insufficient proof of an entire objective; absent commits are insufficient proof of inactivity.
- Existing generated assignments are proposals until selected. Do not convert every old plan into overdue debt.
- A missed session can be rescheduled, reduced, paused, or replaced by a verified priority without inventing progress.

## 3. Provisional check-in routine

Trial this for one week of actual use, initially on one important session per day. These timings are design hypotheses, not clinical prescriptions or permanent commitments.

| Moment | Interaction | Suggested burden |
| --- | --- | --- |
| Start | One tap on **Start this step**; read the already-prepared first action. | About 10 seconds |
| Initial work | Begin with a five-minute entry action inside an initial 25-minute session. Stopping after the entry action is allowed. | Actual work, not reporting |
| During work | Save a distracting term or question with its original context, then return to the current step. | Optional, a few seconds |
| Stop or extend | At the planned boundary, choose **Wrap up**, **Pause**, or an explicit bounded extension that fits existing commitments. | One choice |
| Close | Select **Not started / In progress / Blocked / Done** and capture one exact next action. Reuse existing evidence links where possible. | About 20–30 seconds |
| Evening | Show only unresolved sessions. Permit a one-tap status update or leaving the outcome unknown. No duplicate journal. | At most one minute |

Prepare the next entry action when closing the previous session, so starting does not require replanning. Example: “Open the failing test and run it once” rather than “Work on reliability.”

For unfamiliar terms, ask whether understanding the term is necessary for the current step. If necessary, use a short lookup; otherwise save it for an explicitly chosen exploration session. Saved questions are optional interests, not automatic obligations. Offer deeper work periods when deliberately selected.

At stopping time, save a resumption note such as: “At section 3; retry budget example understood; next: explain why unlimited retries amplify overload.” Protect meals, interviews, and chosen finish times. A timer cannot silently extend the session or mark work complete.

## 4. Accountability behavior

Recommended tone: clear, brief, supportive, and specific. Ask for an action choice rather than a justification. Offer **Start the smaller step**, **Snooze to a chosen time**, or **Skip today**. Reasons remain optional.

The initial app must work without chat, essays, streaks, or extensive setup. Do not infer distraction, motivation, or psychological state from inactivity. Do not punish missed sessions or repeatedly demand attention after dismissal. Reminder frequency, channels, and quiet hours require user control.

The existing dashboard-only notification decision remains in force for the first release. It will not provide proactive supervision when closed. Calendar reminders or a separately chosen notification channel are the next delivery step; test that delivery actually works before relying on it. No new notification channel, recurring task, or external contact is authorized by this document.

## 5. Integration and publishing order

**First:** persistent task state and the manual start/report/resume loop.

**Next:** calendar and MCP integration after the state rules work. MyWork is the authoritative task store; the calendar represents time reservations. Choose one writer for calendar changes. MCP reads state and submits validated updates with provenance and duplicate protection; it cannot bypass dependency or completion rules. Verify connector access from both interactive and scheduled environments before migrating planning to it.

**Publishing later:** retain Lab/GitHub ingestion, editable per-platform drafts, explicit approval, delivery states, retries, and idempotency from the original brief. Native X/LinkedIn integrations move out of the first-release path. Optionally add a plain draft attached to completed evidence with manual copy/export once the progress loop is usable. No feed ingestion, platform credentials, or direct posting is needed for that small feature. Personal notes and support preferences are excluded by default; the user selects what to share.

The original first-post-by-M3 target and publishing-first milestone order are superseded. The first product acceptance target is successful recovery from a partial or skipped session. Keep Next.js + TypeScript and the original learning, review, verification, and engineering standards. Hosting, database, and authentication-provider proposals remain unratified.

## 6. Research gate before broader personalization

This stage is explicitly required, but the deep review has not yet been performed. Complete it before designing or implementing psychological adaptation or expanding the product's claims to a wider audience.

Research should cover task initiation and avoidance, attention switching, prospective memory, time estimation, deep absorption and disengagement, notification fatigue, human accountability, and accessibility. Examine psychological and mental-health evidence alongside HCI and human-behavior research. Distinguish adult evidence from child studies, qualitative preferences from measured outcomes, and short experiments from sustained use.

Required outputs:

- An evidence map: proposed support, hypothesized mechanism, relevant population, study quality, limitations, and unresolved questions.
- Participatory research with intended users; appropriate professional input for mental-health-related features or claims.
- Configurable supports based on expressed needs—such as help starting, protecting concentration, or help stopping—rather than fixed personality categories or inferred diagnoses.
- Evaluation of usefulness, burden, reminder annoyance, autonomy, and unintended effects, including longer-term use.
- Privacy decisions for optional personal notes and preferences, deletion/export, consent, and any future data sharing. A public release must have verified user-data isolation.

MyWork is a work-support product. Clinical diagnosis or treatment claims require a separate evidence and product decision; the initial app makes neither.

### Initial sources checked September 24, 2026

- **NIMH, revised 2024:** [Attention-Deficit/Hyperactivity Disorder: What You Need to Know](https://www.nimh.nih.gov/health/publications/attention-deficit-hyperactivity-disorder-what-you-need-to-know). Describes organization, written reminders, manageable steps, and breaks as practical supports. It does not establish that this app or the proposed timings will work for Jihao.
- **Chen, Meng, and Nie, March 18, 2026; revised April 20, 2026:** [“Not Just Me and My To-Do List”](https://arxiv.org/html/2603.17258v2). Interviews with 22 ADHD-identifying adults and concept feedback from 20 additional participants identify design needs and preferences. The concepts were not evaluated as deployed working systems, so the paper does not demonstrate long-term effectiveness.

## 7. Acceptance and learning

Before advancing beyond the core loop, demonstrate these scenarios:

- Skip a planned session: its outcome remains unreported or explicitly not started; tomorrow references the same task, with no false completion or duplicate.
- Stop partway through: the next session displays the saved stopping point and next action.
- Record a blocker: the next plan offers an unblock step or pause, not dependent implementation work.
- Dismiss or ignore a timer: the task status is unchanged.
- Save a tangent and return to the original context.
- Close the app and reopen it: progress and evidence persist.

During the first week, examine starts reported, useful task progress, ease of resumption, stopping at chosen boundaries, and perceived check-in burden. Treat timer duration as time elapsed, not proof of concentration. Do not optimize for app engagement or total hours. Change one setting at a time after reviewing the user's experience.

MyWork development must replace a chosen portion of existing project time when implementation begins. It is not an additional sixth workload. The next planning decision is which existing project allocation it replaces; this addendum does not change the calendar or initiate implementation.
