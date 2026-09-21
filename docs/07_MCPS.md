# 07 — MCPS (Native Feature — almost fully OPEN)

## 1. FACT

- Board has a box `MCPS` under `Nativ Fetures`. No children, no links, no notes.

## 2. What we do NOT know (ask, don’t assume)

- Does `MCPS` mean Model Context Protocol servers/clients? Almost certainly yes (context: AI tool + “we dont scop a mcp”), but owner must CONFIRM (Q-mcp-meaning).
- Role in R.E.M: does R.E.M (a) connect to external MCP servers, (b) host/expose its own MCP server, (c) allow users to install/manage MCPs as native features, (d) all of the above?
- Which transport? stdio / HTTP+SSE / WebSocket? Which MCP spec version?
- Local-only? (Must be, per fully-local, except user-configured remote MCPs — needs explicit opt-in + warning.)
- Per-session scoping? Per-plugin scoping? Permissions per tool?
- UI: list / add / enable-disable / logs / tool browser?

## 3. Working hypothesis (NOT fact)

Given “big one, not a MCP” + native-features placement: R.E.M likely *manages* MCPs (install/enable/route) rather than *being* one MCP. So `MCPS` box likely means “native MCP client/manager”. This is INFERENCE — flagged as Q-mcp-role, do not implement as fact.

## 4. Safe next steps (without misinterpreting)

- Propose MCP manager UX in text (add server → list tools → enable per session → view logs) as DRAFT in `13_`.
- Propose config schema draft:
```jsonc
// PROPOSAL — NOT DECIDED — pending Q-mcp-*
{
  "mcp_servers": [
    { "id": "local-files", "transport": "stdio", "command": ["python","-m","my_mcp"], "enabled": true, "allowed_sessions": ["*"] }
  ]
}
```
- Propose storage: local config file + logs to `out/mcp-logs/` (proposal).
- Do NOT implement MCP execution until Q-mcp-* answered. If prototyping, isolate in `out/` prototype, never in `main/` as final.

## 5. Checklist

- [ ] Q-mcp-meaning, Q-mcp-role, Q-mcp-transport, Q-mcp-security answered
- [ ] This file updated with decided semantics + spec version pinned
- [ ] Code split: `mcp_config.rs`, `mcp_process.rs`, `mcp_tools.rs`, `mcp_commands.rs` (proposal)
