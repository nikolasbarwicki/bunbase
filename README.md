# bunbase 🧊

Strict TypeScript starter optimized for AI-assisted development. Every commit is validated by five parallel checks — linting, formatting, type checking, dead code detection, and tests — so agents (and humans) get instant feedback on every change.

## Tech Stack

- **Runtime / Package Manager / Test Runner / Bundler:** [Bun](https://bun.sh)
- **Language:** TypeScript (strictest settings)
- **Lint & Format Preset:** [Ultracite](https://www.ultracite.ai) — strict, zero-config preset for oxlint + oxfmt
- **Linter:** [oxlint](https://oxc.rs/docs/guide/usage/linter) — Ultracite core preset with type-aware rules via `oxlint-tsgolint`
- **Formatter:** [oxfmt](https://oxc.rs/docs/guide/usage/formatter) — Ultracite preset with sorted imports
- **Dead Code:** [knip](https://knip.dev)
- **Commit Linting:** [commitlint](https://commitlint.js.org) (Conventional Commits)
- **Git Hooks:** [lefthook](https://github.com/evilmartians/lefthook)

## Getting Started

```bash
bun install
```

## Scripts

| Command | Description |
| --- | --- |
| `bun run dev` | Start with watch mode |
| `bun run build` | Bundle to `dist/` |
| `bun run lint` | Lint with oxlint |
| `bun run lint:fix` | Lint and auto-fix |
| `bun run fix` | Apply safe lint and format fixes with Ultracite |
| `bun run format` | Format with oxfmt |
| `bun run format:check` | Check formatting without writing |
| `bun run typecheck` | Type-check with `tsc --noEmit` |
| `bun run knip` | Detect unused exports and dependencies |
| `bun test` | Run tests |
| `bun run check` | Run all checks (lint + format + types + knip + tests) |

## Git Hooks

Lefthook runs automatically on every commit:

**pre-commit** (parallel):

- `bun run lint`
- `bun run format:check`
- `bun run typecheck`
- `bun test`
- `bun run knip`

**commit-msg:**

- Enforces [Conventional Commits](https://www.conventionalcommits.org) via commitlint

## TypeScript Config

Maximum strictness enabled:

- `strict: true`
- `noUncheckedIndexedAccess` — indexed access returns `T | undefined`
- `exactOptionalPropertyTypes` — no implicit `undefined` in optional props
- `noImplicitReturns`, `noImplicitOverride`, `noFallthroughCasesInSwitch`
- Bundler module resolution with `verbatimModuleSyntax`

## Linter Highlights

[Ultracite's](https://www.ultracite.ai/docs/configuration) strict `core` preset (`oxlint.config.ts`):

- Type-aware rules enabled (`typeAware: true`) — e.g. `no-floating-promises` is an **error**
- `no-explicit-any`, `no-var`, `require-await`, `no-mutable-exports` are **errors**
- Override rules in the `rules` field of `oxlint.config.ts`

## Formatter Config

Ultracite's oxfmt preset (`oxfmt.config.ts`):

- Print width: 80
- Double quotes, ES5 trailing commas, semicolons
- Automatic import sorting, sorted `package.json`

## Project Structure

```
.
├── src/
│   ├── index.ts          # Entrypoint
│   └── index.test.ts     # Tests
├── oxlint.config.ts      # Linter config (Ultracite strict preset, type-aware)
├── oxfmt.config.ts       # Formatter config (Ultracite preset)
├── knip.json             # Dead code detection config
├── lefthook.yml          # Git hooks
├── commitlint.config.js  # Commit message rules
├── tsconfig.json         # TypeScript config
├── .editorconfig         # Editor settings
└── AGENTS.md             # AI agent instructions (Claude Code reads it when no CLAUDE.md exists)
```

---

Built with [Yapper](https://yapper.to/) by [Nikolas](https://nbarwicki.com)
