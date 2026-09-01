# Repository Guidelines

## Project Structure & Module Organization

This repository is a SvelteKit application written in TypeScript. Route components and layouts live in `src/routes/`; shared components, utilities, and assets belong in `src/lib/`. Files in `static/` are served unchanged. Keep tests close to the code they cover, as shown by `src/lib/vitest-examples/*.spec.ts` and `src/routes/demo/playwright/*.e2e.ts`. The `reference/` directory is a separate Next.js/Drizzle/worker reference implementation with its own package metadata and tests; avoid mixing its dependencies with the root application.

## Build, Test, and Development Commands

Use Bun because `bun.lock` is committed.

- `bun install` installs the root dependencies.
- `bun run dev` starts the Vite development server; add `-- --open` to open a browser.
- `bun run check` runs SvelteKit synchronization and TypeScript/Svelte diagnostics.
- `bun run lint` checks Prettier formatting and ESLint rules.
- `bun run format` rewrites supported files with Prettier.
- `bun run test:unit -- --run` runs Vitest once; omit `-- --run` for watch mode.
- `bun run test:e2e` installs Playwright browsers and runs end-to-end tests.
- `bun run build` creates a production build; `bun run preview` serves it locally.

## Coding Style & Naming Conventions

Follow the checked-in Prettier and ESLint configurations. Use tabs, single quotes, no trailing commas, and a 100-character print width. TypeScript runs in strict mode. Name Svelte components in PascalCase (`Welcome.svelte`), functions and variables in camelCase, and follow SvelteKit's route conventions (`+page.svelte`, `+layout.svelte`). Prefer `$lib` imports for shared application code. Svelte 5 runes mode is enabled for project components.

## Testing Guidelines

Vitest covers server-side TypeScript and browser-rendered Svelte components; Playwright covers complete user flows. Name unit and component tests `*.test.ts` or `*.spec.ts`, and end-to-end tests `*.e2e.ts`. Add assertions to every Vitest test (`requireAssertions` is enabled), colocate tests with their subjects, and use accessible queries such as roles or visible text for UI behavior. No coverage threshold is currently configured.

## Commit & Pull Request Guidelines

The history currently contains only `Initial commit`, so no formal commit convention exists. Use short, imperative subjects such as `Add account settings route`, keeping each commit focused. Pull requests should explain the change and verification performed, link relevant issues, and include screenshots or recordings for visible UI changes. Before requesting review, run `bun run check`, `bun run lint`, and the relevant test suites.
