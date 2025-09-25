# Repository Guidelines

## Project Structure & Module Organization

- Root contains configuration: `.editorconfig`, `eslint.config.js`, `.prettierrc.json`, `.prettierignore`, `.husky/`, `.codex/`, `.idea/`, `.nvmrc`, and CI in `.github/`.
- No application code is included by default. Add source under `src/` and tests under `tests/` or colocated as `*.test.js` (use `.ts` only if TypeScript is added).
- Keep generated artifacts out of version control (`dist/`, `node_modules/`). Static assets can live in `public/` or `assets/`.

## Build, Test, and Development Commands

- `npm ci`: Install exact lockfile dependencies (required for CI parity).
- `npm run prepare`: Set up Husky git hooks.
- `npm run lint`: Lint codebase via ESLint.
- `npm run lint:fix`: Auto-fix lint issues where possible.
- `npm run format`: Format the repo with Prettier.
- `npm run format:check`: Verify formatting without writing changes.

## Coding Style & Naming Conventions

- Indentation: 2 spaces; LF line endings; final newline enforced (`.editorconfig`).
- Prettier: width 100, double quotes, semicolons on, trailing commas where valid.
- ESLint: `@eslint/js` recommended rules + `eslint-plugin-import`; Prettier config disables conflicting rules.
- Names: files/folders kebab-case (`my-module.js`), classes/types PascalCase, functions/vars camelCase, constants SCREAMING_SNAKE_CASE. Use `.ts` only if TypeScript is added.
- Imports: prefer absolute within project root or clean relative paths; group and sort consistently.

## Testing Guidelines

- Standard: Vitest for unit/integration tests; Playwright for E2E where applicable.
- Place tests in `tests/**` or alongside sources as `*.test.js`/`*.spec.js` by default. Use `.ts` only if TypeScript is added.
- Aim for meaningful unit coverage on utilities and modules that contain logic. Add lightweight integration tests when applicable.
- Run linting and formatting in CI; extend the workflow when tests are added.

## Commit & Pull Request Guidelines

- PR titles must follow Conventional Commits (enforced by `pr-title-check.yml`): `feat: ...`, `fix: ...`, `docs: ...`, etc.
- Use the PR template: include a clear summary, change type, how to test, and checklist. Link issues (e.g., `Closes #123`).
- Keep commits focused and descriptive; prefer incremental, reviewable changes over large dumps.
- CODEOWNERS exists; ensure reviewers are requested as appropriate.

### PR Authoring (for agents and contributors)

When opening a pull request, populate the template with:

- Summary: 1–3 sentences on what and why.
- Type of change: choose one (feat, fix, docs, chore, refactor, test, ci).
- How to test: exact steps/commands to verify locally.
- Checklist: confirm you followed CONTRIBUTING.md, ran `npm run format:check` and `npm run lint`, updated docs/tests if needed, and CI is green (or explain failures).
- Linked issues: use `Closes #<number>` where applicable.

Notes:

- PR titles must pass the Conventional Commits title check.
- Keep scope minimal; split unrelated changes into separate PRs.
- Prefer `npm ci` for reproducible installs.

## Security & Configuration Tips

- Require Node 20+. Never commit secrets; `.env` is ignored. Use GitHub Actions secrets for CI.
- Dependabot is enabled; keep dependencies current. Review updates with CI green.

## Agent Preflight

- Read config first: `.codex/.codex.json`, `AGENTS.md`, `README.md`, `package.json` (scripts), `.editorconfig`, `eslint.config.js`, `.prettierrc*`, `.prettierignore`, `.husky/**`, `.github/workflows/**`, `.github/CODEOWNERS`, `.github/PULL_REQUEST_TEMPLATE.md`, `CONTRIBUTING.md`, and `SECURITY.md` if present.
- Summarize the rules and propose a short plan before making edits or running non-read commands; wait for approval when requested.
- Branching: use `codex/<task-slug>` as per `.codex/.codex.json`. Do not commit or push if you cannot sign commits or without explicit approval.
- Validation: run `npm run format:check` and `npm run lint` before handing off changes. Prefer `npm ci` for installs.
- Scope: make minimal, focused changes aligned with the task; avoid unrelated fixes unless requested.
- CI alignment: ensure workflows still run `npm run lint` and `npm run format:check` and that Husky/lint-staged config remains intact.
