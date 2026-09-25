# M1 implementation handoff

2026-09-25 · design confirmed · waiting for Jihao's explicit start instruction

## Authorization and readiness

The user confirmed the final M1 recommendations and asked to record them and get ready. **Do not begin implementation until the user confirms the start.** This handoff creates no application code, resources, scheduled jobs, or deployments. No paid plan is authorized.

The selected design is ready to guide implementation. Operational details below are still unconfigured; readiness does not mean every tool or account has been selected or validated. Read AGENTS.md and the project records before resuming.

## Confirmed baseline

| Area | Choice |
| --- | --- |
| Product | Private, customized progress tracking; choose → start → report partial/skipped → resume the same task. |
| Capacity | M1 temporarily replaces Unity work time. |
| Task input | Manually enter/select that day's existing ChatGPT scheduled-task output; keep the stated observable outcome and source. |
| Completion | Outcome achieved and reported; calendar/time/generated assignments never imply completion. |
| Success | Resumption without replanning first; easier starting second; stopping-support trials later. |
| Application | Next.js + React + TypeScript; App Router, server-rendered reads, Server Actions. |
| Structure | One deployment with clear UI, task-rule, and persistence boundaries. Tasks/sessions/reports remain together. |
| Database | Neon Free PostgreSQL, accessed only on the server; transactional mutations, traceable corrections, duplicate protection. |
| Access | Vercel Hobby; Vercel Authentication on All Deployments; private sole-user access, no separate application login for M1. |
| Environments | Separate production and synthetic nonproduction storage; previews branch only from synthetic data; no production credentials in PR CI. |
| Recovery | Manual encrypted exports for a bounded trial, plus a verified restore. Changes since the last successful export may be lost; review automation before ongoing daily reliance. |

Authoritative choices and rationale: DECISIONS.md D13–D22. Technical behavior and verification: ARCHITECTURE.md. Historical provider facts: DATABASE.md; recheck before provisioning.

## Build sequence after start confirmation

1. **Implementation kickoff and feature branch.** Inspect working state and preserve changes. Confirm the runtime/package versions, database driver and migration tooling, test runners, and basic UI conventions in a short implementation note. Use supported stable versions and a lockfile. Explain and record any newly material choice; do not reopen the confirmed architecture.
2. **Task rules and persistence.** Define task/session/report records and constraints; implement the task service and migrations. Verify partial, skipped, unknown, blocked, done, correction, duplicate-save, stale-revision, and dependency behavior with synthetic data before building a broad UI.
3. **Minimal user flow.** Build Today, Progress, and Review around one primary action. Show outcome/resource/next action, report stopping context, reopen and resume the same ID. Handle save failures visibly and preserve input for retry. No timer, automatic scheduling, publishing, MCP, or general module framework.
4. **Integration and browser evidence.** Test transactional rollback, retries/concurrency and stale state against Postgres, then exercise the real browser loop. Synthetic fixtures must be labeled; obtain the real day's generated task before claiming real-task acceptance.
5. **Hosted setup and recovery preparation.** Within the user's authorized scope, verify free-plan availability, account/project access, region, credentials, and environment separation before provisioning. Set All Deployments protection before exposing app data. Define backup location, retention, encryption/key handling, and production-scoped recovery operations. Do not silently incur costs or create recurring jobs.
6. **Review and protected delivery.** Run checks, open the feature PR with evidence, and let Jihao review and merge using a merge commit. Deploy within the granted authorization and verify signed-out/unauthorized access is denied on every relevant URL/data path while Jihao can use the app. Rehearse restore into an isolated target before reliance on real data.
7. **Acceptance and retrospective.** Demonstrate partial and skipped recovery with stable task identity and preserved context. Record actual evidence and remaining limitations in LOG.md. Review provisional experiments and backup burden before moving beyond the bounded trial.

Do not claim a stage complete based on elapsed development sessions. The next stage follows completed work and evidence. Starting code does not automatically approve merging, paid upgrades, new integrations, or public access.

## Details to settle when needed

| Detail | When / why |
| --- | --- |
| Runtime, package manager, driver/migration tooling, test runners | At implementation kickoff, before installing dependencies; choose versions compatible with the confirmed architecture. |
| Exact schema and correction behavior | Before persistence implementation; preserve history without letting old corrections overwrite later progress. |
| UI conventions and accessibility | Before UI work; keep Today/Progress/Review small and keyboard-usable. |
| Neon/Vercel accounts, region, role permissions, quotas | Before provisioning; verify actual availability and cost implications. No account inspection has occurred. |
| Backup destination, retention, encryption/key handling | Before recovery implementation or real-data use. No location or secret-handling method is assumed. |
| Deletion/retention and export scope | Before affected feature implementation or real-data retention; do not silently implement irreversible deletion. |
| Exact generated task and observable outcome | Before real-task acceptance; no ChatGPT automation access or changes are implied. |

These are remaining implementation inputs, not a request to repeat the foundational interview. Cheap reversible details can proceed with a recorded rationale once building is authorized; unresolved consequential choices need a focused question when they become relevant.

## Acceptance evidence to retain

- Task ID and saved context before and after partial → reopen → resume.
- Skip before start and skip after partial; no invented start/progress, no task reset/duplication.
- Unreported session retains known task state; blocked prerequisites prevent dependent work.
- Completion requires the defined outcome to be reported achieved; report source/confidence remains visible.
- Save retry and concurrent/stale updates cannot silently duplicate or overwrite progress.
- Typecheck, lint, build, meaningful state/integration tests and browser flow checks pass.
- Hosted access boundaries, production/nonproduction isolation, and restore verified with actual receipts.

## First action when Jihao says to start

Re-read the current records, inspect Git state, create the implementation feature branch, and prepare the concrete tool/version choices for the first persistence-and-flow slice. Until that instruction arrives, remain documentation-only.
