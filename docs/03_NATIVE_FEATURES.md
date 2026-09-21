# 03 — Native Features Overview (Nativ Fetures)

## 1. FACT (board §2 in 00_)

Box `Nativ Fetures` [spelling as-is] ← `R.E.M`. Six fan-out arrows to:

1. `And more`
2. `Sessions`
3. `Token usage Dashboard` → `5h/1d/7d/30d/60d/all`
4. `PLugins` → `Installabel` + `Nativ` → `Scrapling (https://github.com/d4vinci/Scrapling)`
5. `MCPS`
6. `Skills`

## 2. What “Native” means here (bounded interpretation)

- Native = built-in to R.E.M, ships with the app, works fully local, no extra install needed (contrast with `Installabel` plugins and npm plugins in `06_`).
- Lives in Rust backend + Tauri frontend. Must work offline except where external model APIs are inherently online (still proxied via local backend).
- Each native feature gets its own doc: `04_ Sessions`, `05_ Dashboard`, `06_ Plugins (native part)`, `07_ MCPS`, `08_ Skills`, `10_ Scrapling`. This file is only the index — details live there to avoid duplication and to allow splitting long docs (per AGENTS.md).

## 3. Status per feature

| Feature | Board detail | Doc | Implementation status |
|---------|--------------|-----|-----------------------|
| And more | none — placeholder | this file §4 | OPEN placeholder, do not implement |
| Sessions | name only | `04_` | OPEN — needs definition |
| Token Dashboard | ranges given | `05_` | OPEN — needs metrics definition |
| Plugins (PLugins) | Installabel vs Nativ split | `06_` + `10_` | OPEN — needs API decision |
| MCPS | name only | `07_` | OPEN — needs scope decision |
| Skills | name only | `08_` | OPEN — needs definition |

## 4. “And more” — explicit non-scope

- `And more` is a red-text placeholder for future native features. It is NOT permission to add random features.
- Rule: any new native feature proposed under “And more” must go through `13_IDEAS_PROPOSALS.md` → owner yes/no → new `docs/NN_*.md` file + update this index. Never silently extend scope.

## 5. Contribution rule

- If you work on one native feature, read its dedicated file + `00_` + `12_OPEN_QUESTIONS.md` for that feature. Update that file BEFORE you are done (AGENTS.md). Do not edit this overview for details — link to it.
