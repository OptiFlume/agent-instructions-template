# AGENTS.md

Web app: Next.js 15 (App Router), TypeScript, Postgres via Prisma.
Package manager: pnpm. Node 22. Do not use npm or yarn.

## Commands

- Install: pnpm install
- Dev server: pnpm dev (http://localhost:3000)
- Typecheck: pnpm typecheck
- Lint: pnpm lint (ESLint + Prettier; fix with pnpm lint --fix)
- Unit tests: pnpm test (Vitest). One file: pnpm test src/lib/foo.test.ts
- E2E tests: pnpm e2e (Playwright; needs the dev server running)
- Database: pnpm db:migrate for migrations, pnpm db:seed for fixtures

Run pnpm typecheck and pnpm test before saying a change is done.

## Code style

- TypeScript strict. No any; use unknown and narrow.
- Named exports only. One component per file, PascalCase filenames.
- Server Components by default; add "use client" only when needed.
- Data access goes through src/lib/db/. Never query Prisma from a component.
- Follow the existing file's formatting; Prettier decides the rest.

## Do not touch

- src/generated/ and prisma/migrations/ (generated; change the source instead)
- .env, .env.* and anything under secrets/ (never read, print or commit)
- public/legal/ (owned by the legal team)

## Commits and pull requests

- Branch from main as feat/<ticket>-<slug> or fix/<ticket>-<slug>.
- Commit messages: type(scope): summary, present tense, under 72 chars.
- One logical change per commit. Do not amend or force-push shared branches.
- Open PRs against main with a short description and the ticket number.

## Ask before

- Adding a dependency or changing package.json scripts
- Changing a database schema or writing a migration
- Deleting files, rewriting history, or running anything with --force
- Any change under src/billing/
