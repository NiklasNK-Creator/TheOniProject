# 13 — Ideas / Proposals (owner says yes / no)

> Each idea needs explicit `YES`, `NO`, or `YES-WITH-CHANGES`. Until then, do NOT implement. Proposing agent: record date + rationale. Owner decision: append date + decision.
> Owner answers round 2 recorded 2026-09-21 (all ticked = APPROVED, unticked = NO for now).

## Format for each idea

```
### IDEA-XXX: <title>
- Date proposed: 2026-09-21
- Related Q: Q-...
- Proposal: ...
- Why: ...
- Cost/risk: ...
- Decision: PENDING / APPROVED <date> / NOT APPROVED <date + reason>
```

---

### IDEA-001: TypeScript + React (Vite) for Tauri frontend
- Date proposed: 2026-09-21
- Related Q: Q-gui-framework
- Proposal: Use Tauri v2 + Vite + React + TypeScript. Reason: largest ecosystem, easy charts for dashboard, easy plugin UI.
- Alternative: Svelte (smaller bundle, simpler). Needs owner pick.
- Decision: APPROVED 2026-09-21 — owner chose `React + TS + Vite`.

### IDEA-002: SQLite (via rusqlite) for sessions + usage events, JSON export to out/
- Related Q: Q-session-storage, Q-tokens-storage, Q-app-data
- Proposal: SQLite in Tauri app-data for speed (`sessions.db`, `usage.db`); export JSON/CSV to `out/` on demand for inspection. Raw usage events kept 90d, hourly/daily rollups kept forever to support `all`.
- Why: supports `60d/all` without huge files, still fully local, inspectable.
- Decision: APPROVED 2026-09-21 — owner ticked YES. Implement per spec when building; keep exports in `out/` (git-ignored).

### IDEA-003: Provider/model sync — on-startup + manual button + last-synced label
- Related Q: Q-router-ids-source
- Proposal: On startup pull IDs from fork GitHub (cache fallback offline); Settings shows `last synced HH:MM + diff count`; manual Sync button; never blocks startup.
- Decision: APPROVED 2026-09-21 — owner ticked YES.

### IDEA-004: Plugin manifest `rem.plugin.json` + prefix `rem-plugin-*` for npm
- Date proposed: 2026-09-21
- Related Q: Q-npm-spec, Q-plugin-api
- Proposal: npm package must contain `rem.plugin.json` (`{ id, version, entry, permissions[] }`) + package name starts `rem-plugin-`. Loader validates, shows permission prompt, installs to local app-data (not `main/`).
- Why: makes “must be made for R.E.M” enforceable.
- Self-owned note (binding): runs on R.E.M-owned portable Node (IDEA-013), never system Node / `npm i -g`.
- Decision: APPROVED 2026-09-21 — owner ticked YES.

### IDEA-005: MCP manager — local stdio first, remote opt-in with warning
- Related Q: Q-mcp-role, Q-mcp-transport, Q-mcp-security
- Proposal: v0 supports local stdio MCPs only; remote HTTP MCPs behind explicit opt-in + red warning + per-tool allowlist + full local logging to `out/mcp-logs/`.
- Decision: APPROVED 2026-09-21 — owner ticked YES.

### IDEA-006: Skills as folders `main/skills/<id>/SKILL.md + skill.json + scripts/`
- Related Q: Q-skill-format
- Proposal: Mirror Claude/OpenCode skills convention for familiarity; loader reads `skill.json` for permissions/version; runner in Rust backend sandboxed; 1 example `hello-skill` ships as docs, not enabled by default.
- Decision: APPROVED 2026-09-21 — owner ticked YES.

### IDEA-007: Usage event schema (first draft)
- Related Q: Q-tokens-metrics
- Proposal: `{ ts, session_id, provider, model, input_tokens, output_tokens, cached_tokens?, cost?, latency_ms, status, estimated }`. Dashboard aggregates by `5h/1d/7d/30d/60d/all` + filters by session/model/provider.
- Decision: APPROVED 2026-09-21 — owner ticked YES. Finalize field types at implementation; estimates always marked `estimated:true`.

### IDEA-008: out/build-info.json on every build
- Related Q: Q-out-git
- Proposal: Every local build writes `out/build-info.json` (`{ version, git_sha, tauri_version, os, timestamp }`) for double-checking. Ignored by git by default.
- Decision: APPROVED 2026-09-21 — owner ticked YES.

### IDEA-009: Session ID format `sess_YYYYMMDDTHHMMSS_rand6`
- Related Q: Q-session-definition
- Proposal: Human-sortable + unique, e.g. `sess_20260921T201900_a1b2c3`. Folders `out/sessions/<id>/` for exports (if JSON-export chosen).
- Decision: APPROVED 2026-09-21 — owner ticked YES.

### IDEA-010: Scrapling via Python sidecar (pin version, user-initiated only)
- Related Q: Q-scrap-integration, Q-scrap-security
- Proposal: Ship pinned Python + Scrapling as sidecar called by Rust backend; UI button “Scrape URL” with domain confirm + robots respect + rate limit + log. No background crawling.
- Alternative: Rust-native scraper (no Python) if license/bundle too heavy — needs evaluation.
- Decision: NOT APPROVED 2026-09-21 — owner left unticked (NO for now). DO NOT implement. Re-propose with license/size evaluation (IDEA-014+) before any work. Scrapling stays listed as native-plugin intent in `10_` but with no approved integration.

### IDEA-011: Repro template `out/repro/TEMPLATE.md` for Opencode bug
- Related Q: Q-router-opencode-fix
- Proposal: Standard template (provider, endpoint, versions, redacted request/response, expected vs actual, 3-way test matrix). All repros local, keys redacted.
- Decision: APPROVED 2026-09-21 — owner ticked YES. Template may be committed to git via `out/.gitignore` `!` override when created.

### IDEA-012: Docs-first CI check (even without CI server, manual checklist)
- Related Q: none (process)
- Proposal: Before any “done”, agent must show: docs updated (which files), code double-checked (build/test commands + outputs), split applied (list new files). Owner can reject “done” if missing.
- Decision: APPROVED 2026-09-21 — owner ticked YES (mirrors AGENTS.md §7).

### IDEA-013: Self-owned runtimes — portable Node + owned Python venv + sidecar binaries (OWNER PRINCIPLE 2026-09-21)
- Date proposed: 2026-09-21
- Related Q: Q-tools-node, Q-tools-python, Q-tools-router, Q-tools-verify, Q-tools-uninstall
- Proposal:
  - Ship portable Node (pinned, e.g. Node 22 LTS — TBD) inside R.E.M install for npm-plugin execution; never use system Node or `npm i -g`.
  - Ship owned Python venv (`%LOCALAPPDATA%/R.E.M/python-env/` or `<install>/resources/python/`) with pinned Scrapling version for native scrape plugin; never `pip install` into user Python.
  - Ship 9router fork as Rust library or localhost sidecar binary owned by R.E.M (TBD per Q-tools-router).
  - Installer + first-run + tests assert user `npm root -g` and `pip list` are unchanged; uninstall removes only R.E.M-owned dirs.
  - Every owned tool documented in `docs/` (version + source URL + license) before bundling.
- Why: honors owner rule “selfowned so we dont affect the users installed packages”.
- Cost/risk: bigger installer (Node+Python add ~50-150MB); need pinning + update story. Alternative (rejected by owner): reuse system Node/Python (smaller but pollutes user packages).
- Decision: PRINCIPLE + DETAILS APPROVED 2026-09-21 — owner ticked Node + Python + verify. Open: exact versions, install paths, router library-vs-sidecar (Q-tools-*).

---

## How to propose a new idea

1. Copy the format above, next number `IDEA-014`, etc.
2. Link related Q from `12_`.
3. Never implement before decision. Prototype in `out/` only, marked PROTOTYPE.
