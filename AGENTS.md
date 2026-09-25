# MyWork session instructions

Before doing any work, read these files completely, in order:

1. `docs/PROCESS.md` — original process and engineering standards.
2. `docs/PRD-update.md` — controlling direction update.
3. `docs/DECISIONS.md` — confirmed decisions and unresolved questions.
4. `docs/PROVISIONAL.md` — suggestions and experiments, never implicit approvals.
5. `docs/PRD.md` — reconciled product requirements.
6. `docs/ROADMAP.md` — milestone scope and review gates.
7. `docs/LOG.md` — actual progress, evidence, and next action.
8. `docs/DATABASE.md` and `docs/ARCHITECTURE.md` — technical proposals and their current approval status.

Begin each future session with two sentences stating where the project stands and what comes next. Repository records, never chat memory, are the durable source of truth. New explicit user instructions take precedence; record their effects. Where the original process conflicts with the update, the update wins. `docs/MyWork-PRD-update.md` is the preserved original import; `docs/PRD-update.md` is its canonical copy. Consult the canonical file going forward.

Current phase: documentation and discovery only. Do not scaffold, install dependencies, provision services, deploy, change calendars, create recurring tasks, or contact anyone. Implementation awaits review and explicit instruction. Preserve existing work and never modify the portfolio repository.

Progress tracking and daily execution come first, private and customized for Jihao. Never advance task state from elapsed time, scheduled sessions, attendance, missing feedback, or generated plans. Preserve stable task identity across partial, skipped, and unreported sessions. Social publishing is later; broader psychological personalization requires research before design.

Do not reopen confirmed decisions. Ask only questions needed for the next decision, at most four per round, under roughly 600 words. Explain why each matters, realistic options, trade-offs, and a recommendation. Deferrals to an assistant recommendation remain provisional. Log answers separately from suggestions; never turn silence into approval.

Plan before code. While docs-only, use atomic documentation commits directly on main after each round, as authorized by PROCESS.md. Once code exists: feature branch → PR → user review → merge commit, never squash. Verify before claiming and retain evidence. No fabricated completion, measurements, research, or tests. Architectural, security, and cost decisions require teaching and a recorded decision before adoption. Cheap reversible implementation details can proceed with a note once implementation is authorized.

Keep decisions, roadmap, and progress log current. Record what actually happened, pending feedback, and one exact next action. Revisit provisional choices using observed evidence. Read-only reference access to `/Users/jihaoy/dev/jihaoyb.github.io` is permitted; edits are forbidden. Secrets never enter the repository, production credentials stay in production, and potential costs must be flagged before they exist.
