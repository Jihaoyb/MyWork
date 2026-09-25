# MyWork — Project Kickoff (paste this whole document as the first message in a new chat)

You are starting **MyWork** — my personal work-management dashboard — as a brand-new product in this empty repository. Read this entire brief, then follow the process at the bottom exactly: **interview me first, build second.**

## Who I am and how I work

- MyWork is both a tool I will use daily and a portfolio project that must demonstrate production judgment.
- I learn by building WITH understanding. When you present a choice, teach it: what it is, the 2–3 realistic options, each option's trade-offs, and your recommendation with reasons. I want to be able to defend every decision in an interview.
- Working agreements (carried over from my portfolio project):
  - Plan before code. Atomic, themed commits. Feature branch → PR → I review → merge commit (never squash). Exception: while the repo is docs-only (Phase 0), commit docs straight to main after each round — the PR rule starts when code exists.
  - Verify before claiming: exercise the real flow and show receipts (test output, screenshots, curl). If something fails, say so plainly.
  - All claims honest; no invented numbers.
  - Documentation lives in the repo and evolves with the code.

## What MyWork is

**Vision:** ONE dashboard for managing my work life. It starts with a single module and is architected so more modules keep joining it — elasticity and extensibility are first-class requirements. But **generality is earned, not speculative**: design clean module boundaries now, build the module framework only when the second module actually arrives.

- **Module 1 (build first): Social publishing queue.** Two feeds — (a) new Lab posts from my portfolio site, (b) meaningful updates in my GitHub repos — flow into a review queue. I review/edit/approve each item; approved items publish to X and LinkedIn with links back to my site. **Nothing ever auto-posts; the approval gate is a hard product invariant** — and approval is per (item, platform): each platform gets its own editable copy (280-char X post vs. longer LinkedIn text), its own approve action, and its own delivery state, so "X succeeded, LinkedIn failed" is a first-class, visible situation — never a silent one.
- **Future modules (design for, don't build yet):** job-application tracker, tasks, schedule/calendar, notes.

**Already-ratified decisions** (build on these; don't reopen them unless something genuinely changes the calculus — and if so, say why):

- Next.js + TypeScript, hosted web app.
- Queue policy: digest — max 1 item per repo per day from the change signal; releases/tags always queue.
- Notifications: dashboard-only for MVP (email digest later).
- Native X + LinkedIn APIs (not Buffer/Typefully) — the integration is part of the portfolio story.
- Reference materials on this machine:
  - Lab feed (ingestion source #1): https://jihaoyb.github.io/feed/learning.xml — Atom; posts carry a `category` (Build log / Deep dive / Field notes).
  - Repo change detection (ingestion source #2) should mirror the SHA-gate design in my portfolio pipeline; you may read `/Users/jihaoy/dev/jihaoyb.github.io/.github/scripts/generate_project_pages.py` for the pattern (read-only).
- Proposed but NOT ratified (ask me): Vercel hosting, Supabase Postgres, GitHub OAuth via Auth.js/NextAuth.

**Product bar:** treat this as a real product from day one — authentication, authorization, security, error handling, observability, tests, CI/CD, backups. Small scale, professional grade. **Counterweight:** the dominant failure mode for a solo project is never shipping the payoff. Target: **the first real post published through this tool by the end of Milestone 3** — every process choice answers to that date.

## Session zero — do this before anything else

1. Commit this entire document, verbatim, as `docs/PROCESS.md`, and create a `CLAUDE.md` that says: "Read docs/PROCESS.md, docs/DECISIONS.md, docs/ROADMAP.md, and docs/LOG.md before doing anything. Those files — never chat memory — are the source of truth for process, decisions, and project state."
2. **Every future session starts the same way:** re-read those files, state in two sentences where the project stands and what's next, then continue. If chat memory and the repo docs disagree, the docs win.

## The process

### Phase 0 — Interview me (FIRST — before any scaffold or package install)

Run a structured discovery interview in two tiers. **Batches of at most 4 questions, each batch under ~600 words.** For every question give: (a) why it matters, (b) the realistic options, (c) trade-offs, (d) your recommendation and why. After each round, append the outcomes to `docs/DECISIONS.md` (decision, options considered, reasoning) and commit.

**When I answer "I don't know":** teach the concept in ~5 lines with a concrete example from THIS project, then ask again. If I still defer to your recommendation, record it as **PROVISIONAL** — your pick, marked for revisit — so the log distinguishes my convictions from my deferrals.

**Tier A — foundational (interview now, timebox: ~2 working sessions):**

1. **Vision & success.** What does success look like in 6 months — for the tool and the portfolio story? Am I the only user forever, or could this serve others someday? (Press me: this one answer reshapes auth, data isolation, and every service choice.) Module order after the queue, and whether any future module constrains today's design.
2. **Identity & access.** OAuth provider(s) and why; allowlist enforcement; session length/refresh; the blast radius of a stolen session (this app can post as me — that's the core risk); whether publish actions deserve step-up confirmation; machine access (API keys for anything non-human, and their scope).
3. **Architecture.** Modular monolith vs services at this scale; module boundary rules and how they're enforced; API style (tRPC vs REST route handlers vs GraphQL — teach this one properly); **background work: where scheduled ingestion and publish jobs actually run** (Vercel cron + route handlers, Inngest, Supabase pg_cron, GitHub Actions) — the most consequential infra choice here, take real time; whether we keep an event/activity log from day one.
4. **Data core.** The queue module's entities — source, item, per-platform draft, review decision, publication, delivery attempt (refine with me); item lifecycle states including `partially published` and `publish failed`; schema-per-module philosophy; soft vs hard delete; audit trail. **Post-publish lifecycle is a PRD decision, not an accident:** platform APIs mostly can't edit (X edit is paid; LinkedIn has none) — so is delete-from-dashboard in or out, and the dashboard must treat platform state as potentially divergent, never authoritative.
5. **Integration risk & idempotency.** X free-tier and LinkedIn `w_member_social` constraints AND their platform automation policies (we comply — this is also a ToS question); token storage (encryption at rest), rotation, and expiry-mid-publish recovery — LinkedIn tokens expire ~every 60 days with no self-serve refresh, so **a connected-accounts health screen with a reconnect flow is core scope, not polish**; retry/backoff; **idempotency for publishes — double-posting to my own accounts is this project's most embarrassing failure mode, design against it explicitly**; UTM-tagged outbound links and stored platform post IDs/URLs from the very first publish (analytics dashboards can wait; attribution data can't be backfilled).

**Tier B — just-in-time (interview in a short round immediately before the milestone that needs each):**

6. **Product shape details** (before M2): dashboard shell IA; home screen contents; the review/edit/approve screen's ergonomics — keyboard flow, edit-in-place, per-platform preview-as-it-will-post; **user-visible failure states** (what a failed publish looks like on the item, what "reconnect LinkedIn" looks like); empty and overflowing queue states; mobile posture (responsive/PWA/desktop-first).
7. **UX & design language** (before M2): share my portfolio's editorial DNA (paper/ink/accent tokens) or stand apart; component strategy (Tailwind + shadcn/ui vs CSS modules vs hand-rolled) — speed vs learning; dark mode day one?
8. **Security depth** (before M0 ships): threat model in plain words; the OWASP items that actually apply; CSRF/CSP in Next.js; **Supabase discipline: RLS enabled on every table from migration one, token tables reachable only via server-side service-role key, security-advisor check as a gate**; dependency updates and vulnerability scanning.
9. **Testing** (before M1): which layer owns what — unit (digest policy, change detection, formatting), integration (API routes + real test DB), E2E (Playwright on the approve→publish path with mocked externals); contract tests around the X/LinkedIn client wrappers; test-data strategy; what gates CI (typecheck, lint, tests, build); coverage as signal, not target.
10. **DevOps** (basics before M0, depth before M5): environments (local/preview/production) and which data each touches — **production secrets scoped to production ONLY; Vercel previews get mock credentials and a branch database, plus Deployment Protection** (a public preview URL with real tokens is a breach, not a convenience); migration deploy order AND failure recovery (expand/contract vs down-migrations, pre-migration backup); observability — error tracking (I know Sentry), structured logs, uptime check, **and a dead-man's-switch heartbeat on every scheduled job** (silent cron death produces no error to alert on); where alerts go; **cost ceiling: free tiers, flag anything that could ever bill me before it exists**; custom domain.
11. **Conventions** (before M0): repo name; folder layout; strict TS config; lint/format tooling; commit style; error-handling pattern; PR template; README standard.

Challenge answers that conflict with earlier ones. Surface the questions I don't know to ask.

### Phase 1 — Synthesize (before scaffolding)

Produce, as one PR I review: `docs/PRD.md` (problem, user, jobs-to-be-done, module-1 IN/OUT lists — post-publish edit explicitly decided, module-framework generality explicitly deferred; hard invariants with the approval gate leading; success measures), `docs/ARCHITECTURE.md` (stack with reasons, module boundaries, ERD, background-job design, integration sequence diagrams, security model — mermaid welcome), `docs/ROADMAP.md` (milestones below, each with a Definition of Done that includes tests passing and a production deploy). `docs/DECISIONS.md` continues from Phase 0.

**Milestones** (adjust with me):
- **M0 — walking skeleton:** auth + empty dashboard shell live in production with CI/CD.
- **MV — platform validation spike (before M1, riskiest assumption first):** register both developer apps, obtain real tokens, publish one hello-world to X and one to LinkedIn via API from a script. If either platform blocks us, we redesign *now*, not after building the queue.
- **M1 — ingestion:** both feeds landing as items in the DB, visible read-only.
- **M2 — queue UX:** review/edit/approve/dismiss with digest rules and per-platform drafts.
- **M3 — publish to X** with idempotency, failure handling, the connected-accounts health screen, and the kill switch. **First real post ships here.**
- **M4 — LinkedIn** (including reconnect flow for the 60-day expiry).
- **M5 — hardening:** alerts + heartbeats, backups **with one rehearsed restore**, `docs/RUNBOOK.md` (per-credential revocation/rotation steps, rehearsed once), load sanity check, docs pass.

### Phase 2 — Build loop (every milestone)

Short JIT interview round if the milestone has one → plan → build in small commits → tests green + typecheck clean → verify the real flow in a browser and show me proof → PR with what/why/receipts → I review and merge → deploy → retro in `docs/LOG.md` (5 lines; written like notes for a future Lab post — my portfolio reserves a "MyWork build series").

**Decision materiality during builds:** choices that are cheap to reverse (~under 15 minutes) proceed with a one-line note in the PR description. Anything architectural, security-relevant, or money-costing stops for a mini teach-and-decide and gets a DECISIONS.md entry. **Milestone retro includes a DECISIONS.md sweep:** list entries this milestone's evidence weakens plus all PROVISIONAL entries; re-ratify or reopen each explicitly.

### Hard rules

- The approval gate is inviolable: no code path publishes without an explicit human approval of that specific item **on that specific platform**.
- **Every cron/job route authenticates** (e.g. `CRON_SECRET` bearer check) and **every webhook verifies its signature** (e.g. GitHub `X-Hub-Signature-256`) — with a test asserting unauthenticated requests get 401. Vercel cron hits public route handlers; never leave them open.
- A **`PUBLISHING_ENABLED` kill switch** (env/flag) is checked by every publish path from M3 on — the instant-halt lever for incidents.
- Secrets never enter the repo; `.env.example` documents shape only. Production credentials exist only in the production environment.
- Never modify my portfolio repo (`/Users/jihaoy/dev/jihaoyb.github.io`) — read-only access to the referenced files.
- Prefer boring, documented technology; prefer free tiers; flag any potential cost before it exists.
- When uncertain, ask. When I'm wrong, say so with reasons.

Begin now with **Session zero**, then Phase 0, Tier A, round 1: outline your interview plan in a few sentences, then ask the first batch — at most 4 questions, the biggest ones.
