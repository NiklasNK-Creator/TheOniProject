# 11 — Folders: main / docs / out (decided scaffold)

Owner request (2026-09-21): create a `main` folder, a `docs` folder, and an `out` folder.

## 1. Decided layout (this scaffold implements it)

```
D:\TheOniProject\
  AGENTS.md
  shapes at 26-09-21 20.19.00.png
  main\           <- ALL hand-written source code
    README.md     <- what belongs in main, build instructions (once decided)
  docs\           <- ALL specs/decisions (you are here)
    README.md
    00_ ... 14_
  out\            <- ALL generated outputs, NEVER hand-edit as source
    README.md
    .gitignore    <- ignores everything except README + .gitignore by default
```

## 2. Rules (binding, per AGENTS.md)

### main/
- ONLY human/agent-written source: Rust, frontend (JS/TS/HTML/CSS), configs, manifests, skills, plugin skeletons.
- No build artifacts, no downloaded models, no logs, no usage DBs, no cached provider lists.
- If a file is generated (e.g. `package-lock.json`, `Cargo.lock` — keep lockfiles, they are intentional; `dist/`, `target/`, `node_modules/` — NEVER commit those; they belong in `out/` or ignored).
- Structure proposal (NOT decided, needs yes/no): `main/src-tauri/` (Rust), `main/src/` (frontend), `main/skills/`, `main/plugins/`. Do not create until Q-gui-framework answered, or create as empty placeholders with README.

### docs/
- ONLY markdown specs + diagrams-as-text. No code, no binaries.
- Every behavior change MUST update the relevant `docs/*.md` BEFORE marking work done (AGENTS.md).
- Numbered prefix `NN_` keeps reading order. Add new files as `15_`, `16_`, ... Update `README.md` index.
- Whiteboard image stays at repo root (source of truth), NOT moved into docs (so path stays stable).

### out/
- EVERYTHING generated: binaries, bundles, logs, repro captures, usage DB exports, scraped samples (with consent), build-info, prototypes marked `PROTOTYPE`.
- NEVER hand-edit `out/` as if it were source. Regenerate instead.
- Default `out/.gitignore` ignores all contents except `README.md` + `.gitignore` itself, to keep repo small + honor fully-local (large local artifacts stay local). Owner can override per-file with `!` if something in `out/` SHOULD be committed (e.g. `out/repro/TEMPLATE.md`).
- `out/` is NOT backup. User data (sessions, keys) lives in OS app-data, NOT in `out/` (proposal — needs Q-session-storage confirmation). `out/` is for inspectable exports + builds.

### Self-owned internal tools — where they live (OWNER DECISION 2026-09-21 — binding)
- Owned runtimes/helpers (portable Node, R.E.M-owned Python venv, Rust sidecars, 9router fork binary, Scrapling env, MCP servers) live ONLY in R.E.M-owned locations: app install dir (`<install>/resources/...`) and/or OS app-data owned by R.E.M (`%LOCALAPPDATA%/R.E.M/...` on Windows) — NEVER in user global locations.
- `main/` may contain manifests/pins/lockfiles + build scripts that PRODUCE the owned tools, but NOT the installed tool copies themselves.
- `out/` may contain local build/test copies of owned tools for inspection (git-ignored).
- Rule: `main/` source + docs must list exact version + source URL + license for every bundled tool BEFORE it is added. Install/uninstall scripts must be reversible and must assert user packages are untouched (record check per AGENTS.md §4b).
- Banned: `pip install` into system Python, `npm i -g`, modifying system PATH globally, upgrading/removing user packages.

## 3. Git status (2026-09-21, FACT + DECISION)

- GitHub remote `NiklasNK-Creator/TheOniProject` exists, `main` branch, 1 commit (LICENSE only).
- Local `D:\TheOniProject\` was NOT a git repo (no `.git`, verified 2026-09-21). Only files: PNG + new `main/docs/out/AGENTS.md`.
- OWNER DECISION 2026-09-21 (Q-repo): `git init + remote add + pull` APPROVED. Procedure: `git init -b main`, `git remote add origin https://github.com/NiklasNK-Creator/TheOniProject.git`, `git fetch origin`, `git pull origin main --allow-unrelated-histories` (keep LICENSE), then commit scaffold + push. Do NOT force-push. Record commands + outputs when done.
- EVIDENCE 2026-09-21 (Windows, pwsh, git 2.55.0): `git init -b main` → `Initialized empty Git repository in D:/TheOniProject/.git/`; `git remote add origin ...` + `git fetch origin` → `* [new branch] main -> origin/main`; `git pull origin main --allow-unrelated-histories` → HEAD now `0b4008f Add MIT License to the project`, `LICENSE` tracked, scaffold (`AGENTS.md`, `docs/`, `main/`, `out/`, PNG) untracked and intact. Next: `git add` + commit + push (pending owner confirm — see Q-repo-push).
- EVIDENCE 2026-09-21 (push done, owner approved `Commit+push now`): `git add -A` staged 21 files (1168 insertions, no secrets/artifacts); commit `7b808c8` on top of `0b4008f`; `git push origin main` → `0b4008f..7b808c8 main -> main`. Working tree clean. No force-push. Commit identity passed via one-shot `-c` flags (repo `user.name/email` config left untouched — set it locally if you want future commits without flags).

## 4. How to add code correctly (when approved)

1. Answer relevant `12_` questions first.
2. Put source in `main/`, spec update in `docs/`, artifacts in `out/`.
3. Split long/complicated code into smaller files (AGENTS.md). No 1000-line files.
4. Double-check: build + run + test locally, record evidence (what command, what output, what OS) in docs or `out/build-info.json` (proposal).
