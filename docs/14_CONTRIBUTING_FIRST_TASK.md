# 14 — Contributing: How Anyone Can Immediately Help (without misinterpreting)

## 1. 5-minute onboarding

1. Read `docs/README.md` (index) + `00_WHITEBOARD_SOURCE_OF_TRUTH.md` (literal board).
2. Read `01_PROJECT_OVERVIEW_REM.md` + `AGENTS.md` (root) — especially “fully local”, “big not MCP”, “docs-before-done”.
3. Read `12_OPEN_QUESTIONS.md` — find questions for your area. If unanswered, you must ASK, not guess.
4. Pick a task below. Work in small files. Update docs BEFORE done.

## 2. Safe first tasks (no guessing needed)

### A. Inspect upstream repos (FACT-finding only, zero code)
- [ ] Read `https://github.com/decolua/9router`: language, structure, license, where model/provider IDs live, how to run backend-only. Append FACTS to `09_` (with links + commit hash inspected). Answers Q-router-inspect.
- [ ] Read `https://github.com/d4vinci/Scrapling`: language, license, minimal example, install size. Append FACTS to `10_`. Answers part of Q-scrap-license.
- [ ] Read Tauri v1 vs v2 docs (official): 1-page comparison table for our needs (fully local, Windows-first, Rust backend, plugin sidecars). Append to `13_` as new IDEA. Helps Q-tauri-version.

### B. Draft schemas (mark DRAFT + pending Q)
- [ ] Draft session JSON example (2 sample sessions) in `04_` style — mark `DRAFT pending Q-session-*`.
- [ ] Draft usage-event JSONL (5 rows) + aggregation pseudo-code — mark `DRAFT pending Q-tokens-*`.
- [ ] Draft `rem.plugin.json` manifest + hello-world npm plugin skeleton (text only) — mark `DRAFT pending Q-npm-spec`.
- [ ] Draft MCP config + skill folder examples — mark `DRAFT pending Q-mcp-*/Q-skill-*`.

### C. Process / docs
- [ ] Answer any Q in `12_` you know (owner only for decisions; contributors can add evidence/links).
- [ ] Propose a new IDEA in `13_` format (numbered, with cost/risk, PENDING).
- [ ] Fix typos in docs ONLY if you preserve board quotes in `00_` (never “fix” board spellings there — add `[likely means X]` instead).

## 3. What NOT to do (will be rejected)

- Do NOT scaffold `main/` code until Q-gui-framework + Q-main-scaffold are YES (or build explicitly-labeled `out/` prototype).
- Do NOT fork 9router / vendor Scrapling / publish plugin spec as final without owner YES.
- Do NOT simplify long code/docs to “make it shorter”. SPLIT into smaller pieces instead (AGENTS.md).
- Do NOT commit secrets, keys, usage DBs, binaries, or `out/` contents (except templates with `!` override).
- Do NOT present proposals as decided. Cite `00_` for facts, `12_` for open, `13_` for proposals.

## 4. Definition of Done (binding)

From `AGENTS.md` — every task is done ONLY when:

1. Docs updated (list which `docs/*.md` + what changed).
2. Code double-checked (build + run + test commands + outputs pasted or in `out/build-info.json`).
3. Long/complicated work split (list files, none huge).
4. Fully-local respected (no hidden network, no leaked keys).
5. Open questions either answered (with owner sign-off) or explicitly listed as still-pending.

If any is missing, the task is NOT done — say so explicitly.
