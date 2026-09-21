# 12 — Open Questions (MUST ask owner — do not guess)

> Rule (AGENTS.md): if your task touches a question below, ASK first. Do not implement as if decided. Check off with date + owner answer + link to updated doc.

## Answered 2026-09-21 (owner replies via agent questions)

- **Q-repo: ANSWERED 2026-09-21 → `Init + remote + pull`** — local `D:\TheOniProject\` to be `git init + remote add origin https://github.com/NiklasNK-Creator/TheOniProject/ + pull LICENSE`, then push scaffold. See `11_` §3. [x]
- **Q-gui-framework: ANSWERED 2026-09-21 → `React + TS + Vite`** — Tauri frontend = React + TypeScript + Vite (IDEA-001 APPROVED). See `02_`. Tauri v1 vs v2 still OPEN (default to v2 unless owner objects). [x]
- **Q-main-scaffold: ANSWERED 2026-09-21 → `YES, scaffold now`** (implied by React choice). Awaiting Tauri version confirm before `cargo tauri init`. [x partial]
- **Q-big-scope: ANSWERED 2026-09-21 → `ALL whiteboard boxes are v0`** — owner: “all from me sayed things since this is my v0 plan :3”. So v0 = Sessions + Token Dashboard + Plugins (Installable/Native/Scrapling) + MCPS + Skills + And-more placeholder + GUI Tauri + Models/Provider 9router fork + npm plugins. See `01_` §5, `03_`. [x]
- **Q-os-targets: ANSWERED 2026-09-21 → `Windows desktop first`** — owner: “win destop”. macOS/Linux explicitly NOT v0. See `01_`, `02_`. [x]
- **Q-router-integration: ANSWERED 2026-09-21 (partial) → `9router for model/provider`** — owner: “for model/ provider we have 9router”. Fork location + sync mechanism still OPEN (Q-router-fork-location, Q-router-ids-source). See `09_`. [x partial]
- **Q-tools-selfowned: ANSWERED 2026-09-21 → `YES, all internal tools self-owned`** — owner: “any interel tools we use should always be selfowned so we dont effct the useres inaled packedges”. Binding rule in `AGENTS.md` §4b + `01_` §4b + `11_` owned-tools section. Details still OPEN below (Q-tools-*). [x principle, open details]

## Answered 2026-09-21 round 2 (ideas yes/no — owner ticked YES unless noted)

- APPROVED: IDEA-002 (SQLite), IDEA-003 (provider sync), IDEA-004 (plugin manifest), IDEA-005 (MCP local-first), IDEA-006 (skills folders), IDEA-007 (usage schema), IDEA-008 (build-info), IDEA-009 (session IDs), IDEA-011 (repro template), IDEA-012 (docs-first check), IDEA-013 details (owned Node + owned Python + verify/uninstall). See `13_` for per-idea decisions. [x]
- NOT APPROVED (NO for now): IDEA-010 (Scrapling Python sidecar) — owner left unticked. Do NOT implement; re-propose as IDEA-014+ with license/size evaluation. [x]
- APPROVED: Q-repo-push (`Commit+push now`) — commit scaffold on top of LICENSE + push to origin main. See `11_` §3 evidence. [x — executed below]

Remaining below still OPEN — ask before implementing.

## How to answer

Reply with `Q-<id>: <answer>` (e.g. `Q-rem-meaning: R.E.M = Remember Everything Machine`). Agent will update the relevant doc + mark checked.

---

## A. Project / scope

- **Q-rem-meaning**: What does R.E.M stand for? Or should it stay unexplained? (Doc: `01_`)
- **Q-big-scope**: “Big one, not an MCP” — what are the MUST-HAVE pillars for v0? (e.g. Sessions + Dashboard + Providers + GUI only? Or also Plugins/MCPs/Skills day one?) (Doc: `01_`, `03_`)
- **Q-fully-local**: What network is allowed? (a) model APIs only, (b) + provider-ID sync, (c) + plugin installs, (d) auto-updates? Is offline-first required? (Doc: `01_`)
- **Q-os-targets**: Windows only (you use `D:\`)? Or Win+macOS+Linux from day one? (Doc: `02_`)
- **Q-repo**: Local `D:\TheOniProject\` is NOT a git repo; GitHub has only LICENSE. How to connect? (a) `git clone` into new folder and copy scaffold in, (b) `git init + remote add + pull`, (c) keep local unpushed for now? (Doc: `11_`)

## B. Architecture / GUI

- **Q-gui-framework**: Tauri frontend in what? React / Vue / Svelte / vanilla TS? Styling? (Doc: `02_`) — BLOCKS scaffolding `main/`.
- **Q-tauri-version**: Tauri v1 or v2? (Doc: `02_`)
- **Q-gui-views**: For v0, which views? Sessions list, chat, dashboard, plugins, MCPs, skills, settings? Any mockup or text description? (Doc: `02_`)
- **Q-app-data**: Where does local data live? Tauri app-data? `out/`? SQLite? Encrypted? (Doc: `02_`, `04_`, `05_`)

## C. Native features

- **Q-session-definition**: What IS a session? Chat + agent run + context? What fields? (Doc: `04_`)
- **Q-session-storage**: SQLite vs JSON files? Location? Encryption? Export/import? (Doc: `04_`)
- **Q-session-lifecycle**: Create/rename/fork/archive/delete? Auto-save? Search/tags? (Doc: `04_`)
- **Q-tokens-metrics**: Which metrics? input/output/cached/cost/latency/errors? Per what scope? Estimated when missing? (Doc: `05_`)
- **Q-tokens-storage**: How long to retain raw events for `60d/all`? Rollups? Export? (Doc: `05_`)
- **Q-plugin-api**: What can a plugin do? Tauri commands? JS sandbox? Permissions? (Doc: `06_`)
- **Q-plugin-security**: Audit/signature/allowlist? Sandbox? Permission prompts? (Doc: `06_`)
- **Q-plugin-relationship**: Is upper `Installabel` == lower npm-plugins mechanism? Or separate? (Doc: `06_`)
- **Q-npm-spec**: What makes an npm package “made for R.E.M”? Manifest? Prefix `rem-plugin-*`? Required exports? (Doc: `06_`)
- **Q-mcp-meaning**: Does `MCPS` = Model Context Protocol? CONFIRM. (Doc: `07_`)
- **Q-mcp-role**: Does R.E.M connect to external MCPs, host its own, manage/install them, or all? (Doc: `07_`)
- **Q-mcp-transport**: stdio / HTTP / WebSocket? Spec version? Local-only or allow remote? (Doc: `07_`)
- **Q-mcp-security**: Per-tool permissions? Per-session scoping? Logs? (Doc: `07_`)
- **Q-skill-definition**: What is a Skill in R.E.M? Agent skill (SKILL.md+scripts)? Example? (Doc: `08_`)
- **Q-skill-format**: Folder layout? Metadata? Versioning? (Doc: `08_`)
- **Q-skill-execution**: Who runs skill code? Sandbox? Permissions? (Doc: `08_`)
- **Q-and-more**: Is `And more` just placeholder for future, or do you already have features in mind to list? (Doc: `03_`)

## D. Models / Provider fork

- **Q-router-inspect**: May we inspect `https://github.com/decolua/9router` (language, license, structure) and record facts? (Doc: `09_`) — [yes expected, but ask]
- **Q-router-fork-location**: Where should the fork live? New GitHub repo? Same repo? Submodule? (Doc: `09_`)
- **Q-router-integration**: How does Rust backend use the fork? Library / sidecar / localhost HTTP? (Doc: `09_`)
- **Q-router-ids-source**: What is canonical source for “new provider/model IDs from GitHub”? Upstream repo file? Which file? Sync frequency? Offline fallback? (Doc: `09_`)
- **Q-router-opencode-fix**: Can we reproduce the Opencode-provider bug (need provider, endpoint, error, versions)? May we capture redacted repro in `out/repro/`? Is header-spoofing fix acceptable (check provider ToS)? (Doc: `09_`)
- **Q-router-keys**: How are provider API keys stored? OS keychain? Encrypted file? Per-provider? (Doc: `09_`)
- **Q-router-local-models**: Should router support local models (Ollama/LM Studio) or only cloud APIs? (Doc: `09_`)

## E. Scrapling native plugin

- **Q-scrap-usecase**: What should Scrapling be used for? Agent web-scrape tool? Manual “scrape URL”? (Doc: `10_`)
- **Q-scrap-integration**: How to embed Python Scrapling in Rust/Tauri? Sidecar / subprocess / binding? Pin version? Offline? (Doc: `10_`)
- **Q-scrap-security**: Allowed domains? Robots.txt? Rate limits? User confirm? Where does scraped data go? (Doc: `10_`)
- **Q-scrap-license**: Have you checked Scrapling license compatibility with MIT + fully-local bundling? May we record it? (Doc: `10_`)

## F. Folders / workflow

- **Q-out-git**: Should `out/` stay git-ignored (local only) except templates? Or commit some outputs? (Doc: `11_`)
- **Q-main-scaffold**: May we scaffold `main/` (Tauri + frontend) now, or wait until Q-gui-framework is answered? Minimal placeholder OK? (Doc: `11_`, `02_`) — [partially answered 2026-09-21: React YES, scaffold YES, Tauri version still open]

## G. Self-owned internal tools (owner principle decided 2026-09-21, details OPEN)

Principle DECIDED: all internal tools self-owned, never touch user packages (see `AGENTS.md` §4b). Details OPEN:

- **Q-tools-node**: Bundle portable Node sidecar in R.E.M install (recommended for npm plugins) vs require user Node? Which Node version to pin? (Docs: `06_`, `11_`)
- **Q-tools-python**: Bundle owned Python venv for Scrapling (recommended) vs system Python? Which Python version? Size budget? (Docs: `10_`, `11_`)
- **Q-tools-router**: Ship 9router fork as Rust library vs localhost sidecar binary owned by R.E.M? (Doc: `09_`)
- **Q-tools-verify**: How strict must the “user packages untouched” check be? (Proposal: installer + first-run + tests assert global npm root / `pip list` unchanged — needs yes/no.) (Doc: `11_`, `AGENTS.md`)
- **Q-tools-uninstall**: Must uninstall remove 100% of owned tools + caches, leaving zero trace outside user data export? Confirm. (Doc: `11_`)

---

## Answer template (copy-paste for owner)

```
Q-rem-meaning:
Q-big-scope:
Q-fully-local:
Q-os-targets:
Q-repo:
Q-gui-framework:
Q-tauri-version:
Q-gui-views:
Q-app-data:
Q-session-definition:
Q-session-storage:
Q-session-lifecycle:
Q-tokens-metrics:
Q-tokens-storage:
Q-plugin-api:
Q-plugin-security:
Q-plugin-relationship:
Q-npm-spec:
Q-mcp-meaning:
Q-mcp-role:
Q-mcp-transport:
Q-mcp-security:
Q-skill-definition:
Q-skill-format:
Q-skill-execution:
Q-and-more:
Q-router-inspect:
Q-router-fork-location:
Q-router-integration:
Q-router-ids-source:
Q-router-opencode-fix:
Q-router-keys:
Q-router-local-models:
Q-scrap-usecase:
Q-scrap-integration:
Q-scrap-security:
Q-scrap-license:
Q-out-git:
Q-main-scaffold:
Q-tools-node:
Q-tools-python:
Q-tools-router:
Q-tools-verify:
Q-tools-uninstall:
```
