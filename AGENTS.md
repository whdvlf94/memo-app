# Repository Guidelines

## Project Structure & Module Organization
- Main application code lives in `src/`.
- Routing and server logic: `src/app/` (App Router, API route at `src/app/api/summarize/route.ts`, server actions in `src/app/actions/`).
- UI components: `src/components/` (memo form/list/item/detail modal).
- Reusable hooks: `src/hooks/`.
- Shared types and utilities: `src/types/`, `src/utils/`.
- Static assets: `public/`.
- Database artifacts: `supabase/migrations/` and `supabase/seed.sql`.
- E2E tests are configured under `tests/` via `playwright.config.ts`.

## Build, Test, and Development Commands
- `npm install`: install dependencies.
- `npm run dev`: start local dev server at `http://localhost:3000`.
- `npm run build`: production build.
- `npm run start`: run built app.
- `npm run lint`: run Next.js ESLint rules.
- `npm run format` / `npm run format:check`: apply/check Prettier formatting.
- `npm run test`: run Playwright tests across configured browsers.
- `npm run test:e2e`: run E2E suite in `tests/e2e/`.
- `npm run test:report`: open Playwright HTML report.

## Coding Style & Naming Conventions
- Language: TypeScript (`.ts`/`.tsx`).
- Prettier is the source of formatting truth: 2 spaces, single quotes, no semicolons, `printWidth: 80`.
- Follow ESLint config (`next/core-web-vitals`, `next/typescript`); fix lint warnings before PR.
- Components/hooks use PascalCase and `use*` naming (`MemoList.tsx`, `useMemos.ts`).
- Keep utility modules focused and colocate by concern (e.g., `src/utils/supabase/`).

## Testing Guidelines
- Framework: Playwright (`@playwright/test`).
- Place tests under `tests/` (use `tests/e2e/` for end-to-end flows).
- Use descriptive names like `memo-create.spec.ts`.
- Run `npm run test` locally before opening a PR; use `npm run test:headed` for debugging UI behavior.
- No fixed coverage gate is configured; ensure critical memo CRUD and summarize flows are covered.

## Commit & Pull Request Guidelines
- Prefer Conventional Commit prefixes seen in history: `feat:`, `docs:`, `fix:`, `chore:`.
- Keep commit messages imperative and scoped (example: `feat: add memo summary refresh action`).
- PRs should include:
  - Clear summary of behavior changes.
  - Linked issue/task when available.
  - Screenshots or short recordings for UI updates.
  - Notes for env/config changes (e.g., `.env.local`, Supabase migrations).
