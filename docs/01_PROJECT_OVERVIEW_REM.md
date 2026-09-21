# 01 — Project Overview: R.E.M (our software)

## 1. One-sentence definition (FACT)

R.E.M is our software — a fully local, big-scope desktop application (NOT a small MCP server) hosted at `https://github.com/NiklasNK-Creator/TheOniProject/`.

## 2. What R.E.M is (from whiteboard + owner)

- Central product: `R.E.M` labeled `(our software)` on whiteboard.
- Fully local tool (owner statement). Interpretation allowed only this far: the tool itself runs locally on the user's machine. See §4 for what still needs clarification.
- Big scope: owner explicitly said `we dont scop a mcp we scop a big one`. That means:
  - DO NOT design R.E.M as a single MCP server.
  - DO design R.E.M as a full application that MAY *contain/use* MCPs, plugins, skills, sessions, dashboards (see `03_`).
  - If anyone proposes “just make it an MCP”, point them to this file + `00_` + AGENTS.md and stop.

## 3. What R.E.M is NOT (to prevent false interpretation)

- NOT only a model router — the `Fork Of 9router` is ONE subsystem (`09_`), not the whole product.
- NOT only a GUI — the Tauri GUI is ONE interface (`02_`), backend logic is separate.
- NOT only plugins — plugins are TWO sub-paths (`06_`), not the core.
- NOT cloud-hosted (per owner: fully local). No cloud backend is planned unless owner explicitly approves.

## 4. Fully local — precise meaning (FACT thin, mostly OPEN)

FACT: owner said fully local.

NOT YET DECIDED (see `12_OPEN_QUESTIONS.md`):
- Does fully local mean zero network except model-provider API calls? Or also support fully offline local models?
- Where is data stored? (SQLite? Files in `out/`? OS app-data? All must remain local.)
- Telemetry: none? Opt-in? (Default must be none to honor “fully local” until owner says otherwise.)
- Updates: auto-update allowed? That needs network — is it permitted?
- Model API keys: stored locally via OS keychain? Encrypted file? Never leave machine?

Rule: any network call must be documented, user-visible, and necessary (model APIs, optional plugin installs, optional provider-ID pull from GitHub). No hidden calls.

## 4b. Self-owned internal tools (OWNER DECISION 2026-09-21 — binding)

Owner: “any interel tools we use should always be selfowned so we dont effct the useres inaled packedges” [transcribed as-is; means: any internal tools we use should always be self-owned so we don't affect the users' installed packages — CONFIRMED intent].

- R.E.M bundles/owns every runtime it needs (Node sidecar, Python venv for Scrapling, 9router fork, MCP servers, CLIs) in its own isolated install/app-data location.
- NEVER touches user global packages: no `pip install` into system Python, no `npm i -g`, no PATH mutation, no upgrade/remove of user tools. Install/run/uninstall must leave user packages bit-identical.
- See `AGENTS.md` §4b (binding) + `11_` (where owned tools live) + `13_` IDEA-013. Open details in `12_` (Q-tools-*).

## 5. High-level subsystems (map to other docs)

> OWNER DECISION 2026-09-21 (Q-big-scope): ALL whiteboard boxes are v0. Quote: “all from me sayed things since this is my v0 plan :3”.
> OWNER DECISION 2026-09-21 (Q-os-targets): Windows desktop first. macOS/Linux NOT v0.

```
R.E.M
├── Native Features (03_) ── Sessions (04_), Token Dashboard (05_),
│                            Plugins Installable/Native (06_,10_), MCPS (07_),
│                            Skills (08_), And more
├── GUI-interface — Tauri frontend + Rust backend (02_)
├── Models/Provider — Fork of 9router, backend-only (09_)
└── Plugins (npm, must be made for R.E.M) (06_)
```

Details in each linked file. Do not duplicate logic here — link, don’t copy.

## 6. Current repo state (2026-09-21)

- GitHub remote has only `LICENSE` (MIT, © 2026 Nik) + empty `main` branch with 1 commit.
- Local `D:\TheOniProject\` before this scaffold had only the PNG. Now has `main/`, `docs/`, `out/`, `AGENTS.md`.
- Local is NOT yet a git clone (no `.git`). Owner must decide: `git clone` vs `git init + remote add` vs fresh start. See `12_OPEN_QUESTIONS.md` Q-repo.
- No source code yet. `main/` is empty except README.

## 7. How to talk about R.E.M without misinterpreting

- Always spell `R.E.M` with dots (as on board).
- Do not expand the acronym unless owner defines it. There is no expansion on the board. List as OPEN: Q-rem-meaning.
- Quote board spellings when citing: `Nativ Fetures`, `PLugins`, `Taurin`, `Scrapling`, etc., with `[likely means X — CONFIRM]`.
- Never present a proposal from `13_` as decided.
