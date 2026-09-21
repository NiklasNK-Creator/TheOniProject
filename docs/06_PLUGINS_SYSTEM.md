# 06 — Plugins System (TWO paths — do not confuse)

There are TWO distinct plugin boxes on the board. They are different. Do not merge them.

## A. Path 1 — Native Features > PLugins (upper)

FACT (board):
- `PLugins` [capital P,L] → `Installabel` [likely Installable — CONFIRM] AND `Nativ` [likely Native — CONFIRM].
- `Nativ` → `Scrapling` (`https://github.com/d4vinci/Scrapling`) — see `10_`.

Bounded interpretation:
- `Nativ` plugins = ship with R.E.M, maintained by us, fully local.
- `Installabel` plugins = user can add/remove, but still curated for R.E.M. Mechanism NOT on board — OPEN (marketplace? folder drop? npm? see Path 2?).

OPEN (Q-plugin-*):
- Plugin API surface? (Tauri commands? JS sandbox? Rust ABI? WASM?)
- Permissions / sandboxing? (Full FS/network or scoped?)
- Install source? Signed? Versioning? Updates? Uninstall cleanup?
- Settings UI? Enable/disable per session?

## B. Path 2 — R.E.M > Plugins (lower-left, npm)

FACT (board, exact transcription):
```
Spacial npm
packages can be
installed as plugin
(must be made for R.E.M)
```
Plus npm card (pasted screenshot) with arrow up to that box.

Bounded interpretation:
- Some npm packages can BE plugins, but ONLY if explicitly made for R.E.M. Normal random npm packages do NOT automatically work.
- npm here = JavaScript package manager (Node.js). How npm (JS) talks to Tauri/Rust backend is NOT on board — OPEN.

OPEN:
- What makes an npm package “made for R.E.M”? Manifest file? Naming convention (`rem-plugin-*`)? Required exports? Type definitions?
- Install location? `main/plugins/`? App-data? `out/`? (Proposal: source in `main/`, installed copies in local app-data, build artifacts never in git — needs yes/no.)
- Security: audit? Allowlist? Sandbox? Permissions prompt? (Fully-local still needs supply-chain safety.)
- Version pinning + offline reinstall? (Fully local should work offline after install.)
- SELF-OWNED (OWNER DECISION 2026-09-21, binding): npm plugins run on R.E.M-owned portable Node, installed to R.E.M-owned app-data/install dir. NEVER `npm i -g`, NEVER touch user global `node_modules`, NEVER require user Node. See `AGENTS.md` §4b + `13_` IDEA-013 + `12_` Q-tools-node.

## C. Relationship between Path 1 and Path 2 (OPEN)

Hypothesis (NOT fact, needs confirmation): Path 1 `Installabel` MAY be implemented via Path 2 npm mechanism (i.e. installable plugins ARE npm packages made for R.E.M), while Path 1 `Nativ` are Rust-built-ins (e.g. Scrapling). This is plausible but NOT on board. Listed as Q-plugin-relationship. Do not code as if confirmed.

## D. Rules (AGENTS.md applies double here)

1. No plugin system code until Q-plugin-api + Q-plugin-security are answered, OR build explicit throwaway prototype marked `PROTOTYPE — pending` in `out/` only.
2. Document plugin manifest + 1 minimal example plugin (e.g. `hello-rem`) in this file once decided — with full code, not simplified.
3. Split code: `plugin_manifest.rs`, `plugin_loader.rs`, `plugin_permissions.rs`, `plugin_commands.rs`, `npm_adapter.*` (proposal names).
4. Every plugin install/uninstall must be logged locally + reversible.

## E. How to help now

- Draft a plugin manifest proposal (JSON example) + permission list + 1 hello-world npm plugin skeleton — mark DRAFT.
- Draft threat model for npm plugins (what can a malicious plugin do? how to contain?) — mark DRAFT.
- Do NOT publish any plugin spec as final.
