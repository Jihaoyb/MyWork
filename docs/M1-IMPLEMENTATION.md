# M1 design and technology decisions

Confirmed September 25, 2026.

## Context

MyWork is initially a private progress-tracking app for Jihao. M1 supports **choose task → start → report partial/skipped work → resume the same task** through three views: Today, Progress, and Review.

Tasks are entered manually from the existing ChatGPT scheduled task's daily output. Completion requires the stated observable outcome to be achieved and reported. The primary success criterion is resuming without replanning; easier starting is secondary.

## Selected stack

| Area | Choice | Why |
| --- | --- | --- |
| Application | Next.js + React + TypeScript; App Router | One application for the UI and server behavior, with shared types. |
| Reads and mutations | Server-rendered reads; Server Actions calling a shared task service | Keeps the initial browser flow small and centralizes task rules. |
| Architecture | Modular monolith with separate UI, task-rule, and persistence code | Clear boundaries and independent tests without operating separate services. Task rules remain independent of React and Next.js. |
| Database | Neon Free PostgreSQL; server-only access | Transactions keep related writes consistent; branches support isolated testing. |
| Hosting and access | Vercel Hobby; Vercel Authentication on All Deployments | Private access across production and previews without an additional app login system. |
| Environments | Separate production and synthetic nonproduction databases | Tests and previews cannot modify or copy personal production data. |
| Recovery | Manual encrypted exports for a bounded M1 trial; verified restore | Limits initial setup. Changes since the last successful export can be lost; automated backups need review before ongoing daily reliance. |

## Core design decisions

- Tasks retain stable IDs and resumption context across sessions. Skipped or unreported work never invents progress or completion.
- Tasks, sessions, and reports remain together; related updates commit atomically, and retries cannot duplicate records.
- Corrections preserve history; dependencies follow actual completion status.
- Database credentials remain server-only, with separate runtime and migration permissions.
- Microservices, a separate backend, and provider migration are not planned for M1. Components can be extracted later when independent operation provides a concrete benefit.
- Timers, calendar/MCP integration, publishing, and broader personalization are outside M1.

## Not yet selected

Exact package versions, database driver/ORM and migration tools, test/UI tooling, deployment region, and backup destination, retention, and key handling remain unspecified.

## References

- [Decision record](DECISIONS.md) — confirmed choices and alternatives.
- [Architecture](ARCHITECTURE.md) — data model, boundaries, and state behavior.
- [Database comparison](DATABASE.md) — provider trade-offs and recovery limits.
- [Roadmap](ROADMAP.md) — milestone scope and acceptance criteria.
