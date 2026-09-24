# MyWork

A private work-management dashboard for choosing a realistic next action, preserving progress, and resuming unfinished work.

MyWork starts with progress tracking and daily execution, customized for Jihao. Its central rule is simple: **plans follow actual task state**. A calendar reservation, elapsed timer, or missed session never means a task is complete.

## Current status

**Documentation and discovery.** The repository contains the product requirements draft, confirmed decisions, provisional experiments, milestone plan, and progress log. These establish the intended product; application behavior has not been implemented or tested.

There is no application scaffold, dependency setup, database, authentication implementation, CI pipeline, or deployment yet. There are no install or run commands at this stage.

## First milestone

**Choose a task → start → report partial or skipped work → resume the same task.**

The proposed milestone will let Jihao:

1. Select a task with a stable ID, observable outcome, concrete next action, and relevant resource.
2. Start a session with an intended stopping point.
3. Report partial progress, a blocker, completion, or a decision not to start.
4. Close and reopen the app without losing the report or resumption context.
5. Resume the same unfinished task, without duplicating it or advancing to dependent work prematurely.

Three simple views are planned: **Today** for the next action, **Progress** for task state and history, and **Review** for unresolved session outcomes. The first milestone keeps these minimal and excludes timers, reminders, calendar integration, and publishing.

See the [roadmap](docs/ROADMAP.md) for scope and acceptance criteria.

## Product rules

- Task status, session outcome, and evidence confidence are separate concepts.
- Missing feedback remains unreported; the last known task state is preserved.
- Partial or skipped sessions retain the same task identity and useful next action.
- Dependencies unlock only when prerequisites are reported or evidenced complete against their definitions of done.
- Self-reported progress is valid and stays distinguishable from independently verified evidence.
- Old generated assignments remain proposals until selected; they do not automatically become overdue obligations.
- Check-in timings and focus periods are provisional experiments to test during actual use.
- Initial notifications are dashboard-only; the closed app does not provide proactive reminders.

## Technology direction

Next.js and TypeScript are confirmed, with a hosted web app as the product direction. Whether the first milestone should begin as a local browser trial or a private hosted app remains open.

Hosting, database, and authentication providers have not been selected. Vercel, Supabase, and GitHub OAuth/Auth.js are proposals, not adopted dependencies.

## What comes next

Resolve the four remaining foundational questions:

1. Which existing project-time allocation will MyWork replace?
2. Which real task will demonstrate the first milestone, and what observable result counts as done?
3. Does the first milestone need cross-device hosted access, or is a local browser trial sufficient?
4. Which first-week outcome matters most: easier resumption, more reliable starts, or stopping at chosen boundaries?

Then review the PRD and milestone scope, document the necessary architecture, persistence, recovery, and access decisions, and begin implementation when instructed. MyWork development replaces part of existing project time rather than adding another workload.

## Later work

- Refine daily execution through actual use, including optional saved questions and chosen check-in experiments.
- Add calendar and MCP integration after task-state rules work. MyWork remains the task authority; calendars represent time reservations.
- Add social publishing later, retaining explicit approval per item and platform, independent delivery states, and duplicate prevention.
- Complete research before designing broader psychological personalization or expanding product claims to a wider audience.

These are later directions, not implemented features. The original publishing-first milestone order is superseded.

## Documentation

| Document | Purpose |
| --- | --- |
| [PRD](docs/PRD.md) | Reconciled product requirements and acceptance scenarios; draft for review. |
| [Decisions](docs/DECISIONS.md) | Confirmed choices, reasons, and open questions. |
| [Provisional suggestions](docs/PROVISIONAL.md) | Unratified recommendations and experiments. |
| [Roadmap](docs/ROADMAP.md) | First-milestone plan and later sequencing. |
| [Progress log](docs/LOG.md) | Actual work, verification, and next action. |
| [Process](docs/PROCESS.md) | Original kickoff and engineering agreements. |
| [PRD update](docs/PRD-update.md) | Controlling direction update; takes precedence over conflicting process content. |
| [Agent instructions](AGENTS.md) | Required reading and working rules for future Codex sessions. |

The original imported update is preserved as `docs/MyWork-PRD-update.md`; use `docs/PRD-update.md` as the canonical update. Repository documents are the durable project record, rather than chat memory.

## Working agreements

Plan before code, explain consequential choices, and verify behavior before claiming it works. Keep confirmed decisions separate from suggestions and update the documentation as evidence changes.

During the documentation-only phase, use atomic commits on `main`. Once code exists, use feature branches and pull requests, user review, and merge commits rather than squash merges. Keep secrets out of Git and flag potential costs before provisioning anything.
