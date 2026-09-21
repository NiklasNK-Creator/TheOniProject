# 04 — Sessions (Native Feature)

## 1. FACT

- Board has a box labeled `Sessions` under `Nativ Fetures`. No children, no arrows out, no schema on board.

That's ALL that is fact. Everything below is OPEN and must be asked, not assumed.

## 2. Explicitly NOT decided (do not guess)

- What is a session? Chat thread? Agent run? Window state? Provider connection? All of the above?
- Data model: id format? title? created/updated? model + provider? messages? token counts? attachments? working directory? environment?
- Storage: SQLite in app-data? JSON files in `out/sessions/`? Both? Encryption at rest?
- Lifecycle: create / rename / fork / archive / delete / export / import? Auto-save interval?
- Isolation: does switching sessions isolate context, plugins, MCPs, skills? Or shared?
- Search / filter / tags? Pinning?
- Token Dashboard link: does Sessions feed `05_`? Almost certainly yes, but NOT on board — needs confirmation.
- Multi-window: can two sessions be open side by side?

## 3. Minimal non-misleading direction (proposal, needs yes/no)

Until owner answers (see `12_` Q-session-*), any prototype MUST:

1. Store sessions locally only (fully local rule).
2. Use a trivial, inspectable format (e.g. `out/sessions/<id>/session.json` + `messages.jsonl` — PROPOSAL, not decided).
3. Never delete user data without explicit confirm + backup.
4. Generate IDs with timestamp + random suffix (e.g. `sess_20260921T201900_abc123`) — PROPOSAL.
5. Document the chosen schema in this file BEFORE marking work done (AGENTS.md).

## 4. How to help immediately (without misinterpreting)

- You CAN: propose a session schema (JSON example, 2–3 sample sessions), propose lifecycle state machine diagram, propose storage location table with pros/cons for fully-local.
- You CANNOT: lock in a schema, build full UI, or claim “sessions work like X” without owner sign-off. Mark all work `DRAFT — pending Q-session-*`.

## 5. Checklist before implementation

- [ ] Q-session-definition answered
- [ ] Q-session-storage answered
- [ ] Q-session-lifecycle answered
- [ ] This file updated with decided schema + examples
- [ ] Code split into small files (e.g. `session_model.rs`, `session_store.rs`, `session_commands.rs` — PROPOSAL names)
