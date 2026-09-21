# out — generated outputs (NEVER source, NEVER hand-edit)

> See `../docs/11_FOLDERS_MAIN_DOCS_OUT.md`.

## What goes here

- Built binaries / bundles (`out/bundles/`)
- `out/build-info.json` (proposal IDEA-008)
- Logs, repro captures (`out/repro/` — redact keys!), usage exports, provider cache, mcp logs, prototypes marked PROTOTYPE

## Rules

1. Everything here is REGENERATABLE. If you hand-edit, your edit will be lost — fix the generator in `../main/` instead.
2. Default git-ignored (see `.gitignore`). Large local artifacts stay local (fully-local rule).
3. To commit a template (e.g. `out/repro/TEMPLATE.md`), add `!` override in `.gitignore` + get owner approval.
4. Never put secrets/keys here in plain text. Redact (`sk-...abcd`).
