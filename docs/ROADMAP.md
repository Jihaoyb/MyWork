# Roadmap

Review draft · 2026-09-24. Replaces the original publishing-first M0/MV/M1–M5 schedule. Dates and effort estimates are not commitments. Milestone advancement follows actual acceptance evidence, never elapsed sessions.

## Current — documentation and discovery

Inventory and preserve existing files; retain Git history; add session guidance, separate confirmed/provisional records, reconcile PRD, and propose the first milestone. Ask no more than four foundational questions per round. No implementation or deployment.

Done in this round: initial inventory, complete source reads, reconciliation draft, and foundational questions issued. Remaining: user answers and review; incorporate answers in a subsequent documentation commit. Architecture and service choices are intentionally pending.

## M1 — resume one real task

**Payoff:** choose task → start → report partial/skipped work → resume the same task after reopening the app.

Small scope for review:

1. Manually create/select one real task with stable identity, observable outcome, next action, and resource. Show it as the primary Today action.
2. Start a session attached to that task with an intended stopping point.
3. Report partial progress with stopping context and next action; also allow explicit skipped/not-started, blocked, and done outcomes. Missing feedback remains unreported.
4. Persist task, session, report, and reference data. Resume displays saved context and creates a new session on the same task ID. Provide minimal Progress/history and Review/unresolved views.
5. Exercise one prerequisite/dependent pair to demonstrate that time and skipped work do not unlock dependencies. Support report correction and safe save retries as required to maintain trustworthy state.

Exclude timers/reminders, automatic scheduling, calendar/MCP, publishing, broad task-management features, saved-question UI, and personalization. Use a manually chosen stopping point; timed check-ins can follow. No elaborate dashboard shell or general module framework.

Before coding: incorporate foundational answers; user reviews PRD and this plan and instructs implementation. Choose the delivery environment, persistence and recovery approach, private access if hosted, and minimal architecture. Document decisions and ARCHITECTURE.md; resolve material technical/security/cost choices without reopening the confirmed stack or product order. Define test ownership and conventions in a short just-in-time round.

Definition of Done:

- Demonstrate partial and skipped branches using the same real task identity across sessions; include skip before first start and skip after partial progress.
- Reopen the app and verify saved reports, evidence links, stopping context, and next action remain available.
- Verify no-feedback leaves state unchanged, blocker prevents dependent work, completion checks the defined outcome, corrections are traceable, and repeated save does not duplicate records.
- Verify visible failure/retry behavior for a failed save; do not display success before persistence succeeds.
- Appropriate automated state/integration tests and browser flow evidence pass; typecheck, lint, and build pass for the chosen implementation. Record actual receipts, not aspirational checks.
- Delivery works in the user-selected environment. A local trial does not silently imply deployment; if hosted is selected, private authorization and production delivery become explicit gates before use.
- Code uses feature branch → PR → user review → merge commit; record evidence and a brief retrospective in LOG.md and sweep provisional decisions.

## M2 — first-use trial and daily execution refinement

After M1 evidence, add optional saved questions with context and only the reminder/timer controls chosen for trial. Complete remaining first-release acceptance scenarios in PRD.md, including tangent return and timer dismissal where implemented. Trial one important session per day for a week of actual use if ratified. Review primary success criterion and burden; revise one setting at a time. Hosted delivery, if deferred from M1, requires separate access/storage/deployment decisions before exposure.

## M3 — calendar and MCP, after state rules work

Choose one calendar writer, validate provenance and duplicate protection, and verify interactive and scheduled access. Acceptance: reservations cannot imply completion; external updates obey the same task/dependency rules. No automatic calendar migration or recurring jobs before explicit authorization.

## Later — publishing

Revisit native platform feasibility and policies before committing integration scope. Optional manual draft export may precede integrations. Preserve approval per platform, independent delivery/recovery states, attribution, account health, idempotency, and kill switch. Decide post-publish edit/delete explicitly before implementation. Rehearse credential recovery and backups with a restore; original engineering safeguards still apply where relevant.

## Later — research before broader personalization/public scope

Complete PRD research outputs before adaptation design or implementation. Review target audience, privacy/consent, expressed support preferences, evaluation, and verified data isolation before public release. No deadline or clinical claim is implied.

## Capacity constraint

Implementation replaces a named existing project allocation; it does not add a sixth workload. Allocation remains a pending user decision. The roadmap neither changes the calendar nor claims old assignments were completed.
