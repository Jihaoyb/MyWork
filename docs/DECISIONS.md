# Confirmed decisions and open questions

Recorded 2026-09-24. Status labels are literal: CONFIRMED means user-ratified; OPEN means unanswered. Assistant suggestions live in PROVISIONAL.md. Sources: PROCESS.md, the imported PRD update, and the initialization request. The original documents remain intact.

## Confirmed product decisions

| ID | Decision | Alternatives / reasoning | Source |
| --- | --- | --- | --- |
| D01 | Progress tracking and daily execution are module one. | Supersedes social publishing first; recover actual unfinished work before integrating publishing. | Update §1, §5; current request |
| D02 | Initial release is private and customized for Jihao. | Public release is a later direction with audience and scope subject to research. | Update §1; current request |
| D03 | Plan from actual task status; retain task identity across sessions. | Calendar-based advancement and treating proposals as overdue obligations are rejected. | Update §2; current request |
| D04 | First acceptance target is choose → start → partial/skipped report → resume the same task. | Replaces first-post-by-M3 and the original milestone order. Persistence, blockers, and unknown outcomes are essential. | Update §2, §7; current request |
| D05 | Social publishing remains later, with native X/LinkedIn APIs and explicit approval per item/platform. | Third-party publishing services were not selected. Retain digest policy: at most one change item per repository/day; releases/tags always queue. | PROCESS.md; Update §5 |
| D06 | Next.js + TypeScript, hosted web app as product direction. | Existing ratified stack remains; the first milestone's local versus hosted delivery is still open. No provider selected. | PROCESS.md; Update §5 |
| D07 | Dashboard-only notifications for the initial release. | External reminders are later; the closed dashboard cannot proactively supervise. No new channel or automation is authorized. | PROCESS.md; Update §4 |
| D08 | Deep research precedes broader psychological personalization design and implementation. | Expressed needs, autonomy, and evidence replace diagnosis inference or fixed personality categories. No research completion is claimed. | Update §6; current request |
| D09 | Manual persistent task loop precedes calendar and MCP integration. | MyWork owns task truth; calendar holds reservations; one calendar writer. Validated MCP updates require provenance and duplicate protection. | Update §5 |
| D10 | MyWork replaces existing project time when implementation starts. | It is not an extra sixth workload. Which allocation is replaced remains open. | Update §7 |
| D11 | Preserve learning, honest verification, repo documentation, and professional engineering standards. | Explain consequential choices, prefer simple boundaries; defer a module framework until module two. | PROCESS.md; Update §5 |
| D12 | Initialize documentation and discovery only in this round. | No application scaffold, dependency installation, services, or deployment. Prepare PRD and a small milestone for review. | Current request |

## Process reconciliation

- PRD-update.md controls conflicts with PROCESS.md. PROCESS.md remains an unedited historical process source.
- The docs-only exception permits direct commits on main after discovery rounds. The original synthesis-PR instruction does not require a code-style PR for this initialization round; feature branches and reviewed PRs apply once code exists.
- Original M0/MV/M1–M5 publishing milestones and first-post deadline are superseded. No production deploy is required in this documentation round. The proposed first milestone's delivery environment remains pending; do not silently carry the original production-deploy criterion into a local-trial recommendation.
- Publishing API access, token lifetime assumptions, platform policies, and vendor capabilities must be verified when publishing discovery resumes; historical statements are not current validation.
- Auth, authorization, security, error recovery, observability, tests, CI/CD, and backups remain the engineering bar, scoped to the chosen delivery environment. Vendor-specific rules are conditional, not vendor approvals.

## Open foundational questions — round one

Asked 2026-09-24; answers pending. Do not infer answers from recommendations.

1. Which existing project allocation does MyWork replace?
2. Which real task will exercise milestone one, and what observable outcome counts as done?
3. Must milestone one run across devices as a private hosted app, or is a local browser trial sufficient first?
4. Which first-week outcome matters most: resumption, initiation, or stopping at chosen boundaries?

## Decisions deferred until needed

- After delivery preference: persistence strategy, hosting, database, authentication provider, access enforcement, and architecture. Vercel, Supabase, and GitHub OAuth/Auth.js remain unratified.
- Before implementation: record/task lifecycle details, report corrections, deletion/export scope, retention, security design, test ownership, repository conventions, and cost implications. Draft requirements in PRD.md are not approval of an implementation choice.
- Before UI work: design language, component strategy, mobile posture, accessibility verification, dark mode, and control details.
- After core loop evidence: calendar writer and permissions; MCP trust boundaries and interactive/scheduled access.
- Before publishing: platform feasibility/policies, credentials, background execution, retries/idempotency, attribution, account health, and explicit post-publish edit/delete scope.
- Before broader personalization or public launch: research outputs, consent, privacy, data isolation, audience, and evaluation.
