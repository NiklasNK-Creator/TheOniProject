# 02 — Architecture: GUI-interface — Tauri Frontend + Rust Backend

## 1. FACT (from board)

- Box `GUI-interface` ← arrow from `R.E.M`.
- Box `Taurin frontend / Rust backend` ← curved arrow from `R.E.M` arching over `GUI-interface`.
- Transcribed spelling `Taurin` [likely means Tauri — CONFIRM].

Allowed interpretation: R.E.M’s graphical interface is built with Tauri (frontend + Rust backend). No other framework is named on the board.

## 2. What this means (careful, minimal inference)

> OWNER DECISION 2026-09-21 (Q-gui-framework): Frontend = React + TypeScript + Vite (IDEA-001 APPROVED). Tauri version still OPEN — default to v2 unless owner objects.
> OWNER DECISION 2026-09-21 (Q-os-targets): Windows desktop first.

- Frontend: Tauri webview (HTML/CSS/JS). Specific JS framework NOT on board — OPEN (React / Vue / Svelte / vanilla? See Q-gui-framework).
- Backend: Rust (Tauri commands, sidecar logic). All heavy / local / private work should live here to honor “fully local”.
- `GUI-interface` is the user-facing layer; `Models/Provider` fork is explicitly `No webgui only backend` (see `09_`), so the Tauri GUI is the primary GUI.

## 3. What is NOT decided (OPEN — see 12_)

- Window layout? Views for Sessions, Dashboard, Plugins, MCPS, Skills? No mockups on board.
- Single window vs multi-window? System tray? Auto-start?
- Frontend/backend IPC contract? Command names? Event names? Error shapes?
- Build targets? Windows only (owner path is `D:\`)? macOS/Linux too?
- Tauri v1 vs v2? (Decide at implementation; document choice + why.)
- Auth / lock screen for local sessions? (Fully local still may need at-rest protection.)

## 4. Rules for implementation (to honor AGENTS.md + fully local)

1. All file system + network access goes through Rust backend, never directly from frontend fetch to unknown hosts. Frontend calls whitelisted Tauri commands.
2. Every network call (model API, provider-ID pull, plugin install) must be: explicit, logged locally, user-toggleable where possible.
3. No bundling of secrets. Keys stay in OS keychain / encrypted local store, never in `out/` plain text, never in git.
4. If code gets long/complicated: SPLIT into smaller modules/files (per AGENTS.md). Example split: `main/src-tauri/src/commands/sessions.rs`, `.../dashboard.rs`, `.../plugins.rs`, `.../providers.rs`, NOT one giant `main.rs`.
5. Frontend and backend versions must be kept in sync and recorded in docs + `out/build-info.json` (proposal, see 13_).

## 5. Where code will live (see 11_)

- `main/` will contain the Tauri project (proposal: `main/src-tauri/` + `main/src/` frontend). NOT decided yet — needs owner yes/no on JS framework. Do not scaffold Tauri until Q-gui-framework is answered, or scaffold minimal placeholder with README stating it is placeholder.
- `out/` will contain built binaries/bundles, never source.

## 6. How to contribute here without misinterpreting

- Read `00_` §3 first.
- Do not assume React. Do not assume Tailwind. Propose, then ask.
- Any GUI text quoting board boxes must preserve meaning; fix typos only with `[likely means X — CONFIRM]` note until owner confirms.
