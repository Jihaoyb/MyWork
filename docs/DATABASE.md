# M1 database comparison

2026-09-25 · Neon Free PostgreSQL selected (D17) · not provisioned

## Selected database

Use **Neon Free Postgres**, with all database access through the Next.js server. The user confirmed this recommendation after reviewing alternatives (D17). Supabase Free Postgres remains an alternative, not selected infrastructure. Implementation and provisioning await the separate start instruction.

Postgres stores related records in tables and can commit several changes together in a transaction. For MyWork, recording a partial report, closing its session, and updating the task's next action must succeed together or leave the prior state intact. The recommendation is based on M1's needs, not on speculative public-product features.

## Two realistic options

Provider facts checked on 2026-09-25; account eligibility and effective limits must be checked again before provisioning.

| Consideration | Neon Free | Supabase Free |
| --- | --- | --- |
| Database | Managed Postgres. | Managed Postgres, plus optional Auth, Storage, Realtime, and APIs. |
| Included capacity | 0.5 GB storage and 100 CU-hours of compute per project/month; 10 branches/project. | 500 MB database/project; limit of two active free projects. |
| Idle behavior | Compute scales to zero after five minutes; returning requests must handle wake-up latency. | Projects pause after one week of inactivity. |
| Preview separation | Free branches can isolate development changes. Default data-copying branches must not copy personal production data into previews. | Managed branching is excluded from Free. A separate free project could isolate test data if a slot is available. This would replace the original branch-database preference and needs an explicit decision if selected. |
| Recovery | Free instant restore history is six hours, capped at 1 GB of changes. Insufficient as the only backup. | Automatic backups and point-in-time recovery are excluded from Free; maintain independent exports. |
| Cost trigger | Free quota exhaustion can suspend compute or reject writes; Free does not bill overages. A paid upgrade introduces usage charges and needs approval. | Pro starts at $25/month; branching and some other capabilities add costs. Do not upgrade or add paid services without review. |
| Fit for M1 | Database branching and a small server-only design fit the current scope. | Useful if we deliberately want its broader platform; M1 does not yet need those services. |

Sources: [Neon official Free-plan FAQ](https://github.com/neondatabase/website/blob/main/content/faqs/free-plan-limits-and-quotas.md), updated September 23, 2026; [Supabase pricing](https://supabase.com/pricing); [Supabase database overview](https://supabase.com/docs/guides/database/overview). Older Neon articles show different quotas; use current plan information rather than those historical numbers.

The comparison is not a prediction of actual usage or a guarantee of permanently free operation. No account inventory, quota availability, or billing configuration has been inspected.

## Confirmed environment and access baseline

- Production has its own database credentials, used only by the deployed production server.
- Development/CI/previews use synthetic data in a separate nonproduction database project. With Neon, create preview branches from that synthetic baseline, never from personal production data. Branching copies parent data unless explicitly configured otherwise. See [Neon branching primer](https://neon.com/docs/get-started-with-neon/workflow-primer).
- Use a least-privilege runtime database role and a separate migration/administration role. Keep credentials out of browser bundles, source control, and logs. Choose region and connection mode before provisioning; verify transaction support with the selected driver.
- Vercel Authentication protects the app, not direct database connections. A Vercel login is not a Supabase Auth session. If Supabase is selected, enable RLS from the first migration as PROCESS.md requires, keep app tables unexposed to public API roles, and design policies for the actual server runtime role. Do not assume an `auth.uid()` policy works with Vercel Authentication alone.
- No production database credentials in local development or PR CI. Any later production backup/migration operation must run in an explicitly production-scoped operational context; document it separately.

## Recovery for the bounded M1 trial

Confirmed trial approach (D21): user-triggered, complete exports after each day of actual use and before migrations, plus one verified restore into an isolated recovery target before depending on M1. Exports must preserve task/session/report IDs, corrections, references, dependencies, and schema version. Store them encrypted outside Git and outside the database provider; choose the destination, retention, and encryption/key handling before implementing real-data recovery and before real-data use.

This means **changes since the last successful export can be lost**. A missed export enlarges that window. Neon's short restore history is extra protection, not a substitute for exports. This approach is limited to a bounded trial with recoverable data. Review automated backups before ongoing daily reliance; if the trial cannot tolerate this loss window, resolve recovery before real-data use. No backup schedule, new storage account, or paid plan is authorized by this document.

Use a database-native logical dump for operational recovery and consider a user-readable export separately; they serve different purposes. Supabase explicitly recommends independent exports on Free. Postgres documents consistent logical dumps and restoration; verify provider permissions and role recreation in the eventual runbook. Sources: [Supabase backups](https://supabase.com/docs/guides/platform/backups), [Postgres SQL dump](https://www.postgresql.org/docs/current/backup-dump.html).

## Research limitations

Supabase's markdown changelog could not be fetched through the available web reader; the HTML changelog was checked instead. Its September 25 entry concerns Postgres upgrades and affected extensions/custom operators; no existing MyWork database or such features exist to migrate. Recheck relevant changes before implementation. [Supabase changelog](https://supabase.com/changelog).

Some Neon documentation URLs could not be opened by the web reader. Current quotas were verified in Neon's official documentation repository; no account-level capability has been tested. No benchmark or product-flow verification is claimed.
