[issues]: https://github.com/doinel1a/vanilla-node-ts/issues
[pulls]: https://github.com/doinel1a/vanilla-node-ts/pulls
[license]: https://github.com/doinel1a/vanilla-node-ts/blob/main/LICENSE
[node]: https://nodejs.org/en
[pnpm]: https://pnpm.io/installation
[typescript]: https://www.typescriptlang.org/
[zod]: https://zod.dev/
[t3-env]: https://env.t3.gg/
[tsup]: https://tsup.egoist.dev/
[tsx]: https://tsx.is/
[eslint]: https://eslint.org/
[eslint-sonarjs]: https://github.com/SonarSource/eslint-plugin-sonarjs
[eslint-unicorn]: https://github.com/sindresorhus/eslint-plugin-unicorn
[prettier]: https://prettier.io/
[husky]: https://typicode.github.io/husky/
[commitlint]: https://commitlint.js.org/
[conventional-commits]: https://www.conventionalcommits.org/

# Node · TypeScript - Template

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)][license]
[![TypeScript](https://img.shields.io/badge/TypeScript-6.x-3178c6)][typescript]
[![Node.js](https://img.shields.io/badge/node-%3E%3D24-brightgreen)][node]
[![pnpm](https://img.shields.io/badge/pnpm-%3E%3D11-orange)][pnpm]

Every new Node.js project starts the same way: configuring TypeScript, wiring up ESLint, setting up git hooks, and validating environment variables - before a single line of real code is written. This template eliminates that overhead.

It combines **[TypeScript][typescript]** with a strict, battle-tested configuration, **[tsup][tsup]** + **[tsx][tsx]** for build and development, and a complete quality pipeline pre-wired and ready to use.

- **TypeScript 6** - strict mode, ESNext target, bundler module resolution, path aliases (`@/*`, `~/*`), and incremental builds
- **Environment validation** - runtime-safe env vars with [`@t3-oss/env-core`][t3-env] and [Zod][zod]; bad config fails fast at boot
- **ESLint** - [`typescript-eslint`][typescript] (strict + stylistic), [`eslint-plugin-sonarjs`][eslint-sonarjs], [`eslint-plugin-unicorn`][eslint-unicorn], and [Prettier][prettier] integration
- **Git hooks** - [Husky][husky] pre-commit runs type-check, ESLint, and Prettier via lint-staged; `commit-msg` enforces [Conventional Commits][conventional-commits] via [Commitlint][commitlint]
- **Bundling** - [tsup][tsup] for production ESM output; [tsx][tsx] for watch-mode development
- **Sorted imports** - consistent import order enforced by `@ianvs/prettier-plugin-sort-imports`

---

[Report a bug][issues] &nbsp;|&nbsp; [Request a feature][issues] &nbsp;|&nbsp; [Open a pull request][pulls]

---

## Table of contents

- [Getting started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment variables](#environment-variables)
- [Project structure](#project-structure)
- [Available scripts](#available-scripts)
- [Tech stack](#tech-stack)

---

## Getting started

### Prerequisites

- **[Node.js][node]** >= 24
- **[pnpm][pnpm]** >= 11

### Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/doinel1a/vanilla-node-ts YOUR-PROJECT-NAME
cd YOUR-PROJECT-NAME
pnpm install
```

### Environment variables

Copy the example file and fill in the required values:

```bash
cp .env.example .env
```

| Variable      | Description                       | Default       |
| ------------- | --------------------------------- | ------------- |
| `NODE_ENV`    | Runtime environment               | `development` |
| `PLACEHOLDER` | Replace with your actual variable | -             |

> [!NOTE]
> Set `SKIP_ENV_VALIDATION=true` to bypass env validation at startup. Useful for Docker builds where env vars are injected at runtime.

Then start the development server:

```bash
pnpm dev
```

---

## Project structure

```
vanilla-node-ts/
├── src/
│   ├── index.ts             # Application entry point
│   └── env.ts               # Environment variable schema and validation
├── .env.example             # Environment variable reference
├── .husky/                  # Git hooks (pre-commit, commit-msg)
├── commitlint.config.ts
├── eslint.config.ts
├── lint-staged.config.ts
├── prettier.config.ts
├── tsconfig.json
└── tsup.config.ts
```

---

## Available scripts

| Script           | Description                                         |
| ---------------- | --------------------------------------------------- |
| `pnpm dev`       | Start the development server with hot reload        |
| `pnpm build`     | Bundle for production with tsup                     |
| `pnpm start`     | Run the production build                            |
| `pnpm typecheck` | Run TypeScript type checking without emitting files |
| `pnpm lint`      | Run ESLint                                          |
| `pnpm lint:fix`  | Run ESLint and auto-fix issues                      |
| `pnpm format`    | Format all source files with Prettier               |

---

## Tech stack

| Tool                                              | Purpose                                        |
| ------------------------------------------------- | ---------------------------------------------- |
| **[TypeScript][typescript]**                      | Static typing with strict mode                 |
| **[tsup][tsup]** + **[tsx][tsx]**                 | Production bundling and development watch mode |
| **[Zod][zod]** + **[T3 Env][t3-env]**             | Runtime schema validation and env var safety   |
| **[ESLint][eslint]** + **[Prettier][prettier]**   | Linting and formatting                         |
| **[Husky][husky]** + **[Commitlint][commitlint]** | Git hooks and conventional commit enforcement  |
