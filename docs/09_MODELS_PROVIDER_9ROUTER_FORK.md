# 09 — Models / Provider — Fork of 9router (Backend Only)

## 1. FACT (board, exact)

- `Models/Provider` ← `R.E.M` (curved arrow).
- Child: `( https://github.com/decolua/9router )` + `Fork Of 9router`.
- Three children of fork:
  1. `Fix for Opencode provider (bug: new update made that it only works though opencode anymore fix so the api thinks request comes from opencode` [transcribed, `though` as-is]
  2. `Always pull new proveres/models ids... from github` [`proveres` as-is]
  3. `No webgui only backend`

## 2. Bounded interpretation (allowed, minimal)

> OWNER DECISION 2026-09-21: “for model/ provider we have 9router” — 9router fork is CONFIRMED as the Models/Provider solution for v0 (Windows desktop).

- R.E.M will maintain a FORK of `https://github.com/decolua/9router` for model/provider routing.
- Fork is backend-only: no web GUI of its own; GUI comes from R.E.M Tauri frontend (`02_`).
- Fork must track upstream: always pull new provider/model IDs from GitHub (automation needed, mechanism OPEN).
- Fork must include a fix so the Opencode provider works again: after an update it only works *through* Opencode; fix by making the API think the request comes from Opencode (likely User-Agent / headers / origin spoofing — exact mechanism OPEN, see §4).

## 3. What is NOT decided (OPEN)

- Fork location? Same repo? Separate repo? Submodule? Subtree? Cargo dependency via git? (Q-router-fork-location)
- Which GitHub source is canonical for “new provider/model IDs”? Upstream 9router repo? Another registry? How often to pull? Auto vs manual? Offline fallback? (Q-router-ids-source)
- Language/runtime of 9router? (Need to inspect upstream — not done yet. Must read upstream README/Cargo/package before designing.)
- How does Rust backend call the fork? Sidecar process? Library? HTTP localhost? (Q-router-integration)
- API key handling? Per-provider keys, local-only storage, never logged. (Q-router-keys)
- Local models? Ollama/LM Studio support? Or only cloud APIs via router? (Q-router-local-models)

## 4. Opencode-provider bug — careful handling (do NOT guess the fix)

Board says: new update made it only work through Opencode anymore; fix so API thinks request comes from Opencode.

What to do (correct process, per AGENTS.md — double-check, don’t simplify):

1. Reproduce: record exact provider, endpoint, request, response, error, versions (Opencode version, 9router version, date). Save evidence to `out/repro/` (local only, redact keys).
2. Inspect upstream 9router + Opencode changelog for the breaking change (headers? auth? origin? client identification?).
3. Propose MINIMAL fix in fork (e.g. set `User-Agent`, `X-Requested-With`, `Origin`, `Referer` to Opencode values — HYPOTHESIS ONLY, verify by capture).
4. Test matrix: direct vs via-Opencode vs via-fork-with-fix. Document all three.
5. Never commit keys. Never log full keys. Log redacted (`sk-...abcd`).

Do NOT implement header spoofing blindly. Some providers forbid it — check ToS + document risk. Listed as Q-router-opencode-fix.

## 5. “Always pull new provider/model IDs from GitHub” — proposal (needs yes/no)

Proposal (NOT decided):
- Nightly or on-startup pull of `models.json`/`providers.json` (exact filenames TBD after inspecting upstream) from fork’s GitHub (which mirrors upstream + our additions).
- Local cache in app-data + `out/provider-cache/` for inspection. Works offline from cache.
- UI shows “last synced” + manual “Sync now” + diff of added/removed models.
- If GitHub unreachable, use cache + warn, never break startup.

Needs Q-router-ids-source + Q-router-offline answers.

## 6. How to help now (safe tasks)

- [ ] Inspect `https://github.com/decolua/9router`: language, structure, how IDs are stored, license, how to fork. Summarize in `13_` or update this file with FACTS + links (no code yet).
- [ ] Draft fork maintenance doc: fork URL, sync procedure, branch strategy (proposal).
- [ ] Draft reproduction template for Opencode bug (`out/repro/TEMPLATE.md` proposal).
- Do NOT fork or code until Q-router-* answered, unless owner says “prototype anyway”.

## 7. Checklist

- [ ] Upstream inspected, facts recorded
- [ ] Q-router-fork-location, Q-router-integration, Q-router-ids-source, Q-router-opencode-fix answered
- [ ] This file updated with final integration diagram + file paths
- [ ] Code split into small modules (e.g. `providers/registry.rs`, `providers/sync.rs`, `providers/opencode_fix.rs` — proposal)
