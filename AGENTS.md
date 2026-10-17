# Instructions for AI coding agents

Read this file before writing or changing code in this repository. Lovable users: paste this into the project's custom knowledge.

## Project context
- **Product:** [name and one-sentence description]
- **Target customer:** [who pays]
- **User roles:** [e.g. Admin, Manager, Staff, Customer — with one line on what each can do]
- **Core workflow:** [the one end-to-end flow that must work, e.g. "Customer requests booking → Manager approves → Staff sees schedule"]

## Source of truth
- Requirements: `docs/03-requirements.md`. Implement user stories by their ID (e.g. `US-04`). Do not invent features that are not in this file; propose them instead.
- Scope for the current version: see the "V1 / V2 scope" section in `docs/03-requirements.md`.
- Architecture and data model: `docs/04-architecture.md`. Update the data model section whenever you change the database schema.

## Stack
- Node.js (LTS), TypeScript, React / Next.js
- PostgreSQL ([Supabase / Neon / local])
- Authentication: [Supabase Auth / Auth.js / Clerk], role-based access enforced on the server or by row-level security, never only in the UI

## Rules
1. Never commit secrets. Read configuration from environment variables and list every new variable in `.env.example` with a placeholder value.
2. Use synthetic seed data only. Provide a seed script with at least one test user per role.
3. Enforce permissions in the backend or database, and add a short test or manual check for each role.
4. Work in small steps: one user story per change. Suggest a commit message in the form `US-XX: short description`.
5. When you make a significant technical decision (library, schema change, trade-off), add one line to `docs/07-iteration-log.md` under "Decisions".
6. Explain changes in plain language. The product owner is not a professional developer.
7. If a request conflicts with the requirements or would weaken security, say so before implementing it.
