<!-- .github/copilot-instructions.md - guidance for AI coding agents in this repository -->
# Project snapshot for AI agents

This small Vite + React project (single-page) implements a "coffee supply" calculator. Keep instructions actionable and tied to the files below.

## Big picture (what to know first)
- App entry: `src/main.jsx` — mounts React root (StrictMode + `createRoot`).
- Top-level UI: `src/App.jsx` — renders the `Calculator` component.
- Primary feature: `src/components/Calculator/index.jsx` — contains the calculation logic (per README the logic should live here). It composes two `Input` components and a `Button`.
- Components convention: each component lives in `src/components/<Name>/` with `index.jsx` and `style.css`. Components import their CSS directly (e.g. `import './style.css'`).

Data flow and reasoning
- Calculator is the stateful parent: keep state and calculation functions inside `Calculator`. Inputs are simple presentational/controlled children. This matches the README spec that the calculation logic stays in the `Calculator` component.

## Key files to inspect
- `package.json` — scripts: `dev` (vite), `build` (vite build), `preview` (vite preview), `lint` (eslint).
- `vite.config.js` — standard Vite setup with `@vitejs/plugin-react`.
- `eslint.config.js` — project linting rules (run `npm run lint` before committing changes).
- `src/components/*` — component pattern: default export from `index.jsx`, CSS per-component in `style.css`.
- `README.md` — contains the canonical product spec (age, daily cups, max age = 99, calculation function signatures). Use it as the source of truth for feature behavior.

## Developer workflows (commands and expectations)
- Install deps: `npm install` (project uses ESM, node + npm). If dependencies are missing, install before running dev scripts.
- Run dev server: `npm run dev` — Vite serves on the default port (usually `http://localhost:5173`).
- Build for production: `npm run build`.
- Preview production build: `npm run preview`.
- Lint: `npm run lint` (ESLint + react plugins are configured as devDependencies).

Tips for local edits and debugging
- Keep component exports default (current code uses `export default`).
- Use `htmlFor` instead of `for` on labels when editing JSX (current `Input` uses `label for=''` which should be `htmlFor`).
- Input elements should be `type='number'` and enforce positive values (the README requires positive-only numeric inputs).
- When adding state or behavior, prefer hooking state into `Calculator` and pass handlers/values to `Input` components as props.

Project-specific conventions and patterns
- File layout: each component folder contains `index.jsx` and `style.css`. Follow this pattern for new components.
- CSS is global per component (no CSS modules). Class names use kebab-case (examples: `calculator-wrapper`, `input-wrapper`).
- Imports inside components are relative and concise, e.g. `import Button from '../Button'` or `import Button from './components/Button'` depending on file location.
- No backend or API integrations in the repo — everything is client-side.

Integration points and dependencies
- Runtime: `react` and `react-dom` (React 19). Build/dev: `vite` and `@vitejs/plugin-react`.
- Linting: `eslint`, `@eslint/js`, and React lint plugins are present in devDependencies. Use `npm run lint` to catch style/JSX issues.

Concrete examples to follow
- Mounting: `src/main.jsx` uses `createRoot(document.getElementById('root')).render(<StrictMode><App/></StrictMode>)` — preserve StrictMode for edits.
- Calculator composition: `Calculator` currently renders two `Input` components and a `Button` (see `src/components/Calculator/index.jsx`) — add props and handlers there.
- Calculation helpers from README (copy/paste-safe):
  - `function calculateSupply(age, amountPerDay) { return Math.round((maxAge - age) * 365 * amountPerDay) }`
  - Keep `maxAge = 99` as the canonical value unless README/spec is updated.

What not to change without confirmation
- Project structure (Vite + component folder pattern).
- ESLint config and package.json scripts unless a PR updates them and explains the reason.

If you add tests or CI
- There are no tests or CI configs. If you add tests, include a minimal devDependency (e.g., Vitest) and update `package.json` scripts. Note this change in the PR description.

Final notes
- Prefer small, isolated changes: run `npm run lint` and `npm run dev` locally to verify UI and linting.
- When behavior is ambiguous, reference `README.md` (it contains the expected input types, state shape, and calculation contracts).

If any of the above sections are unclear or you want more examples (sample Input props, controlled input pattern, or a suggested unit-test), tell me which part to expand and I will iterate.
