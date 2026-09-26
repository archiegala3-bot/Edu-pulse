# EduPulse

EduPulse is a clickable role-based academic intelligence prototype for Maharashtra HSC Class 12 students, teachers, parents, and principals.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm --filter @workspace/edupulse run dev` — run the EduPulse web app
- `pnpm --filter @workspace/edupulse run typecheck` — typecheck the EduPulse frontend
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/edupulse/src/App.tsx` — role selector, shared shell, role dashboards, mock data, and demo interactions
- `artifacts/edupulse/src/index.css` — EduPulse visual tokens and responsive styling
- `artifacts/edupulse/.replit-artifact/artifact.toml` — artifact routing and workflow metadata
- `attached_assets/` — original consolidated product brief

## Architecture decisions

- This first build is frontend-only with local mock state because the product brief calls for a clickable prototype rather than a full backend.
- The four role views share a navigation shell but use different information density and copy so each role has a distinct decision surface.
- The student flow models the core loop locally: diagnose signals, prescribe targets and resources, practice, and escalate a repeated unresolved doubt.
- Learning recommendations use direct public YouTube video links and thumbnails verified during build; metadata that search did not expose is labeled instead of guessed.

## Product

- Role-selector login for Principal, Teacher, Parent, and Student demo views
- Aggregate principal drilldowns by stream and section
- Teacher class summary, student signals, doubt escalation inbox, and answer-sheet review queue
- Parent-friendly child progress and anonymized peer context
- Student targets, chapter mastery, doubt solver with second-attempt escalation, weekly test, study planner, leaderboard, and topic recommendations

## User preferences

_No project-specific preferences recorded._

## Gotchas

- The app intentionally uses mock data and local state; refreshing the page resets demo actions.
- YouTube thumbnail URLs are external and can change availability outside the app.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
