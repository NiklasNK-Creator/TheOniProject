# AGENTS.md — Mandatory rules for EVERY human and AI agent working on TheOniProject / R.E.M

> Repo: `https://github.com/NiklasNK-Creator/TheOniProject/`
> Whiteboard source of truth: `shapes at 26-09-21 20.19.00.png` (root) + transcribed in `docs/00_WHITEBOARD_SOURCE_OF_TRUTH.md`.
> Scope: **BIG application, NOT a small MCP.** If anyone says “just make it an MCP”, stop and point here + `docs/01_PROJECT_OVERVIEW_REM.md`.
> Nature: **FULLY LOCAL tool.** No hidden network, no telemetry, no cloud backend unless owner explicitly approves per-feature.

---

## 0. READ FIRST (blocking)

Before ANY task, read:

1. `docs/README.md` (index + how to avoid misinterpretation)
2. `docs/00_WHITEBOARD_SOURCE_OF_TRUTH.md` (literal board — WINS over all other docs)
3. The `docs/NN_*.md` file(s) for your area
4. `docs/12_OPEN_QUESTIONS.md` (if your task touches an OPEN question, ASK first — do not guess)

If you have not read these, you are NOT ready. Say so and read them.

## 1. NEVER FORGET: ALWAYS UPDATE DOCS BEFORE DONE (binding)

- Every behavior decision, schema, command, config, file layout, or workflow change MUST update the relevant `docs/*.md` BEFORE you claim done.
- Docs update is part of DONE, not afterthought. No docs update = NOT done. State explicitly: “NOT done — docs pending” if you haven’t.
- Update the SMALLEST relevant file(s) (e.g. sessions → `docs/04_SESSIONS.md`), plus `docs/README.md` index if you add a file, plus `docs/12_OPEN_QUESTIONS.md` (check off answered Q with date + answer).
- Quote board boxes exactly when citing; preserve board spellings (`Nativ Fetures`, `PLugins`, `Taurin`, `Scrapling`, `Installabel`, `Spacial`, `proveres`) with `[likely means X — CONFIRM]` until owner confirms. Never silently “fix” `00_`.
- New files: number as `15_`, `16_`, ... Update index. Never overwrite `00_` with interpretation — append only with owner approval.

## 2. DOUBLE-CHECK CODE (binding)

- Before marking done: build + run + test locally. Record: exact command, OS, output (paste short output or write `out/build-info.json` per IDEA-008).
- Check: no secrets committed, no keys logged (redact `sk-...abcd`), no `target/`/`node_modules/`/`dist/` committed, no `out/` contents treated as source.
- Re-read your own diff: does it match the docs you updated? If docs say X but code does Y, fix one — never leave them inconsistent.
- If you cannot verify (missing tool, missing answer), say `UNVERIFIED: <reason>` — do not claim verified.

## 3. NEVER SIMPLIFY — SPLIT INSTEAD (binding)

- DO NOT simplify, shorten, stub out, or drop requirements to “make it fit”. If it’s too long or complicated, SPLIT it into smaller pieces.
- Code: split into smaller modules/files/functions (e.g. `session_model.rs`, `session_store.rs`, `session_commands.rs` instead of one giant file). No 1000-line files. No “TODO: implement later” silently replacing required logic — mark `UNIMPLEMENTED: <Q-id>` explicitly.
- Docs: split into smaller `docs/NN_*.md` files instead of deleting detail. Prefer 15 precise files over 1 vague file.
- If you feel the urge to simplify, STOP and: (a) list the pieces, (b) implement/document piece by piece, (c) mark remainder as pending with Q-ids.

## 4. FULLY LOCAL (binding)

- All data stays on machine by default (sessions, keys, usage, logs). Network ONLY for: user-approved model APIs, provider-ID sync, plugin installs, app updates — each explicit, logged, toggleable where possible.
- Keys: OS keychain / encrypted local store only. Never in git, never in `out/` plain text, never in logs (redact).
- No telemetry. No phone-home. If a dependency phones home, document + disable or replace (needs owner decision).
- `out/` is git-ignored by default (see `out/.gitignore`). Large artifacts stay local.

## 4b. SELF-OWNED INTERNAL TOOLS (binding — owner decision 2026-09-21)

- Owner rule: “any internal tools we use should always be selfowned so we dont affect the users installed packages.”
- Meaning: every runtime/helper R.E.M needs (Node, Python, sidecars, CLIs, scrapers, router, MCP servers) MUST be bundled/owned by R.E.M in its own isolated location — NEVER installed into, modified, upgraded, or removed from the user’s global/system packages.
- Concretely:
  - NEVER `pip install` / `npm install -g` / modify system PATH, global `node_modules`, system Python, user site-packages, or shared tools as part of install/run.
  - Ship our own: e.g. portable Node sidecar, venv under app-data owned by R.E.M, Rust sidecars, pinned binaries in app install dir. Document exact versions + source + license in `docs/` before bundling.
  - User’s npm/Python/system packages must work identically before and after installing/running/uninstalling R.E.M. Verify this in testing (record check in DONE).
  - Uninstall must remove ONLY what R.E.M owns, leave user packages untouched.
- Violation = REJECT (same as secrets/scope violations). When in doubt, isolate + document + ask (cite Q-tools-*).

## 5. ASK UNCLEAR THINGS + PROPOSE IDEAS FOR YES/NO (binding)

- The whiteboard is THIN (names only for Sessions/MCPS/Skills, etc.). You MUST ask rather than guess. See `docs/12_OPEN_QUESTIONS.md` — full Q-list with IDs (`Q-session-*`, `Q-mcp-*`, ...).
- How to ask: cite `Q-<id>` + what you need + why it blocks + your proposal (if any). Wait for owner answer before implementing that area, OR build explicit `out/` PROTOTYPE marked `PROTOTYPE — pending Q-...` (never in `main/` as final).
- Propose ideas in `docs/13_IDEAS_PROPOSALS.md` format (`IDEA-XXX`, PENDING). Owner replies YES / NO / YES-WITH-CHANGES. Do NOT implement PENDING ideas as final.
- We scope a BIG ONE: proposals should serve the full app (Sessions + Dashboard + Providers + GUI + Plugins/MCPs/Skills), not shrink it to one MCP. Reject scope-shrinking suggestions with link here.

## 6. FOLDER DISCIPLINE (binding)

- `main/` = hand-written source only. `docs/` = specs only. `out/` = generated only (never hand-edit as source). See `docs/11_FOLDERS_MAIN_DOCS_OUT.md`.
- Local `D:\TheOniProject\` is NOT yet a git repo (verified 2026-09-21); GitHub has only LICENSE. Do NOT `git init/clone/push/force-push` without owner answer to Q-repo.

## 7. DEFINITION OF DONE (all must hold — else NOT done)

- [ ] Docs updated (list files + changes)
- [ ] Code double-checked (commands + outputs, or `UNVERIFIED: <reason>`)
- [ ] Split applied (list files; none huge; no silent simplification)
- [ ] Fully-local respected (network documented, keys safe)
- [ ] Self-owned tools respected (no user packages touched, own runtimes documented + uninstall clean)
- [ ] Open Qs: answered (with owner sign-off + date) OR listed as still-pending with IDs

Copy this checklist into your final message for every task. If any box is unchecked, start your message with `NOT DONE:` + reason.

## 8. VIOLATION EXAMPLES (will be rejected)

- “Done, code works (didn’t update docs)” → REJECT: docs-before-done violated.
- “Simplified session schema to just {id, text} for now” → REJECT: simplified instead of split.
- “Assumed Skills = OpenCode skills, implemented runner” → REJECT: guessed OPEN question (Q-skill-*).
- “Made it an MCP server to keep it simple” → REJECT: scope violation (big, not MCP).
- “Logged full API key for debugging” → REJECT: fully-local/secrets violation.
- “Committed out/bundle.exe + usage.db” → REJECT: folder discipline violation.
- “pip install scrapling into system Python / npm i -g rem-plugin” → REJECT: self-owned-tools violation (must bundle in R.E.M-owned isolated location).

---

*If this file conflicts with any other doc, THIS FILE’s process rules win; `docs/00_`’s FACTS win on product content. Ask on any conflict (cite Q-id).*
