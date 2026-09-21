# docs — TheOniProject / R.E.M — Reading Guide

> Source of truth for v0: whiteboard image `shapes at 26-09-21 20.19.00.png` in repo root + tldraw link `https://www.tldraw.com/f/DDV-H64LKaqOiPo_roWok?d=v-372.-779.3839.2306.page`.
> GitHub: `https://github.com/NiklasNK-Creator/TheOniProject/`
> Principle: fully local tool. Scope: BIG application, NOT a small MCP.

## How to use these docs (for a new human or agent)

1. Start with `00_WHITEBOARD_SOURCE_OF_TRUTH.md` — literal transcription. This prevents false interpretation. Everything else is built on it.
2. Then read `01_PROJECT_OVERVIEW_REM.md` — what R.E.M is and is NOT.
3. Then read `02_ARCHITECTURE_TAURI.md` + `11_FOLDERS_MAIN_DOCS_OUT.md` — where code goes, where output goes.
4. Then read feature docs `03`–`10` for your area.
5. Before you start coding: read `12_OPEN_QUESTIONS.md`. If your task touches an open question, ASK the owner first, do not guess.
6. When you finish: follow `AGENTS.md` at repo root — update docs BEFORE you are done, double-check code, never simplify silently.

## File index — do not skip

| File | What it answers | Status |
|------|-----------------|--------|
| `00_WHITEBOARD_SOURCE_OF_TRUTH.md` | What did the whiteboard literally say? Exact boxes, arrows, spellings, links | FACT — transcribed from PNG |
| `01_PROJECT_OVERVIEW_REM.md` | What is R.E.M? Fully local meaning? Big scope vs MCP? | FACT + OPEN QUESTIONS |
| `02_ARCHITECTURE_TAURI.md` | Tauri frontend + Rust backend, GUI-interface | FACT (thin) + OPEN QUESTIONS |
| `03_NATIVE_FEATURES.md` | Overview of 6 native feature boxes | FACT |
| `04_SESSIONS.md` | What Sessions means (and does NOT yet mean) | MOSTLY OPEN |
| `05_TOKEN_USAGE_DASHBOARD.md` | Token dashboard + 5h/1d/7d/30d/60d/all ranges | FACT (thin) + OPEN |
| `06_PLUGINS_SYSTEM.md` | Two plugin paths: Native-Features > Plugins AND R.E.M > Plugins (npm) | FACT + OPEN |
| `07_MCPS.md` | What MCPS box means | OPEN — needs owner decision |
| `08_SKILLS.md` | What Skills box means | OPEN — needs owner decision |
| `09_MODELS_PROVIDER_9ROUTER_FORK.md` | Fork of 9router, no-webgui-only-backend, auto-pull IDs, Opencode-provider fix | FACT (transcribed) + OPEN |
| `10_NATIVE_SCRAPLING_PLUGIN.md` | Native > Plugins > Nativ > Scrapling link | FACT + OPEN |
| `11_FOLDERS_MAIN_DOCS_OUT.md` | What `main/`, `docs/`, `out/` are for, what goes where | DECIDED in this scaffold |
| `12_OPEN_QUESTIONS.md` | Complete list of unclear things — must ask owner (incl. Q-tools-* for self-owned tools) | ACTION LIST |
| `13_IDEAS_PROPOSALS.md` | Ideas owner can say yes/no to — NOT decided (IDEA-001 React APPROVED, IDEA-013 self-owned principle APPROVED) | PROPOSALS |
| `14_CONTRIBUTING_FIRST_TASK.md` | How anyone can immediately help without misinterpreting | GUIDE |

## Folder map (repo root `D:\TheOniProject\`)

```
D:\TheOniProject\
  AGENTS.md                          <- mandatory rules for every agent/human
  shapes at 26-09-21 20.19.00.png    <- whiteboard source image, DO NOT DELETE
  main\                              <- ALL source code for R.E.M (see 11_)
    README.md
  docs\                              <- ALL specifications (you are here)
    README.md (this file)
    00_ ... 14_
  out\                               <- ALL generated outputs, NEVER source
    README.md
    .gitignore (keeps outputs local, not pushed unless explicitly wanted)
```

## Anti-misinterpretation rules for these docs

- FACT = directly visible in whiteboard PNG or explicitly stated by owner (`fully local`, `not an MCP, big one`, GitHub URL).
- TRANSCRIBED SPELLING is preserved in `00_` (e.g. `Nativ Fetures`, `PLugins`, `Taurin`, `Scrapling`, `Installabel`, `Spacial`, `proveres`). Corrected spelling is noted as `[likely means X — CONFIRM]`, never silently fixed.
- OPEN = we do not know yet. Listed in `12_OPEN_QUESTIONS.md`. Do not implement OPEN as if it were FACT.
- PROPOSAL = idea in `13_IDEAS_PROPOSALS.md`. Needs explicit yes/no from owner. Do not implement until approved.

Last updated: 2026-09-21 — initial scaffold from whiteboard. See git history for changes.
