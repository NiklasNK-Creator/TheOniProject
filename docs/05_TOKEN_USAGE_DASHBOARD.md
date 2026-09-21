# 05 — Token Usage Dashboard (Native Feature)

## 1. FACT

- Board: `Token usage / Dashboard` → `5h/1d/7d/30d/60d/all`.
- That is: a dashboard showing token usage with time-range selectors 5 hours, 1 day, 7 days, 30 days, 60 days, all.

## 2. NOT decided (OPEN)

- Which tokens? Input / output / cached / reasoning? Cost in USD/local currency? Requests count? Errors? Latency?
- Scope filters? Per session? Per model? Per provider? Per plugin/MCP/skill? Global total?
- Data source? Counted locally from actual requests/responses? Or trusted from provider headers? Both + reconciliation?
- Storage & retention? How long to keep raw events to support `60d/all`? Aggregation strategy (raw events + hourly/daily rollups)?
- UI? Table + charts? Export CSV/JSON to `out/`? Real-time update?
- “5h” meaning? Last 5 hours rolling? Calendar? Timezone handling?

## 3. Minimal direction (proposal, needs yes/no)

- Event = one model call: `{ ts, session_id, provider, model, input_tokens, output_tokens, cached_tokens?, cost?, latency_ms, status }` stored locally append-only (`out/usage/usage.jsonl` PROPOSAL).
- Dashboard queries local events, aggregates by selected range. No network needed to view.
- Ranges exactly as on board: `5h, 1d, 7d, 30d, 60d, all` — do not rename until owner approves.
- If provider doesn’t return usage, estimate locally + mark `estimated:true` (never present estimate as exact).

## 4. How to help

- Propose event schema + 5 example rows + aggregation queries (SQL or Rust pseudo-code) as DRAFT.
- Propose dashboard wireframe (text/ASCII, not final UI) showing filters + chart + table.
- Mark everything pending Q-tokens-* in `12_`.

## 5. Checklist

- [ ] Q-tokens-metrics answered
- [ ] Q-tokens-storage answered
- [ ] This file updated with final schema
- [ ] Code split: `usage_event.rs`, `usage_store.rs`, `usage_aggregate.rs`, `dashboard_commands.rs` (proposal)
