# main — R.E.M source code (placeholder — DO NOT scaffold until approved)

> See `../docs/02_ARCHITECTURE_TAURI.md`, `../docs/11_FOLDERS_MAIN_DOCS_OUT.md`, `../docs/12_OPEN_QUESTIONS.md` (Q-gui-framework, Q-main-scaffold).

## Status (2026-09-21)

EMPTY — no source yet. Awaiting owner answers on:

- Q-gui-framework (React/Vue/Svelte/vanilla?)
- Q-tauri-version (v1 vs v2?)
- Q-main-scaffold (scaffold now or wait? placeholder OK?)

## What WILL live here (once approved)

- `src-tauri/` — Rust backend (Tauri commands, sessions, dashboard, plugins, MCPs, skills, providers)
- `src/` — frontend (framework TBD)
- `skills/` — skill sources (if IDEA-006 approved)
- `plugins/` — first-party plugin skeletons (if plugin spec approved)

## Rules

1. No build artifacts (`target/`, `node_modules/`, `dist/`) — those go to `../out/` or are ignored.
2. Keep lockfiles (`Cargo.lock`, `package-lock.json`) — intentional.
3. Split long files (AGENTS.md). No 1000-line modules.
4. Every change updates `../docs/*.md` BEFORE done.
