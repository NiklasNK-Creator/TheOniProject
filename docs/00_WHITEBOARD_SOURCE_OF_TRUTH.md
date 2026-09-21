# 00 — Whiteboard Source of Truth (literal transcription)

Source image: `shapes at 26-09-21 20.19.00.png` in repo root.
Tldraw link (same board, may need JS to view): `https://www.tldraw.com/f/DDV-H64LKaqOiPo_roWok?d=v-372.-779.3839.2306.page`
Date of image: 26-09-21 20.19.00 (from filename).

> Purpose of this file: prevent false interpretation. If any other doc conflicts with this file, THIS FILE WINS until the owner explicitly changes the whiteboard.

## 1. Central node

Box text (three lines):
```
(our software)
R.E.M
```

## 2. Upper branch: Nativ Fetures [spelling as in image]

Box text: `Nativ Fetures`
Arrow: `R.E.M` -> `Nativ Fetures` (upward arrow).

From `Nativ Fetures`, 6 curved arrows fan out upward to:

### 2.1 `And more`
- Text: `And more` (with `And` + `more` in red, rest black in image).
- Meaning: placeholder / extensibility. No further detail on board.

### 2.2 `Sessions`
- Text: `Sessions`
- No child boxes on board.

### 2.3 `Token usage Dashboard` (two lines)
```
Token usage
Dashboard
```
- Child: one box to the right: `5h/1d/7d/30d/60d/all`
- Arrow: `Token usage Dashboard` -> `5h/1d/7d/30d/60d/all`

### 2.4 `PLugins` [spelling: capital P, L, lowercase ugins]
- Text: `PLugins`
- Two outgoing arrows to:
  - `Installabel` [spelling as in image, likely means Installable — CONFIRM]
  - `Nativ` [spelling as in image, likely means Native — CONFIRM]
- Chain: `Nativ` -> box `Scrapling` [spelling as in image, likely means Scraping — CONFIRM]
  - `Scrapling` box contains a small blue hyperlink text at top: `( https://github.com/d4vinci/Scrapling )` and large text `Scrapling`.

### 2.5 `MCPS`
- Text: `MCPS` (all caps).
- No child boxes.

### 2.6 `Skills`
- Text: `Skills`
- No child boxes.

## 3. Middle-right branch: GUI-interface

- Small box: `GUI-interface`
- Arrow: `R.E.M` -> `GUI-interface` (straight horizontal arrow).
- Curved arrow: `R.E.M` (top edge) arcs over `GUI-interface` to:
```
Taurin frontend
Rust backend
```
  - Spelling `Taurin` as in image [likely means Tauri — CONFIRM].
  - Two lines in one box.

Interpretation strictly allowed: R.E.M has a GUI-interface built as Taurin/Tauri frontend + Rust backend. No framework named on board.

## 4. Lower-middle branch: Models/Provider

- Box: `Models/Provider`
- Arrow: `R.E.M` -> `Models/Provider` (curved arrow from bottom of R.E.M).
- Child box:
```
( https://github.com/decolua/9router )
Fork Of 9router
```
  - Top line is blue hyperlink in image, bottom line is large text.
- From `Fork Of 9router`, three outgoing arrows:
  - Up-right to large box:
```
Fix for Opencode provider
(bug: new update made that it only works though opencode
anymore fix so the api thinks request
comes from opencode
```
    - Transcribed line breaks as visible. `though` as in image [likely means through — CONFIRM].
    - `opencode` lowercase as in image.
  - Down-left to:
```
Always pull new proveres/models ids...
from github
```
    - Spelling `proveres` as in image [likely means providers — CONFIRM].
  - Down-right to:
```
No webgui only backend
```
    - Spelling `webgui` as one word, as in image.

## 5. Lower-left branch: Plugins (second plugin path)

- Box: `Plugins` (normal capitalization, distinct from upper `PLugins`).
- Arrow: `R.E.M` -> `Plugins` (diagonal down-left arrow).
- Child:
```
Spacial npm
packages can be
installed as plugin
(must be made for R.E.M)
```
  - Spelling `Spacial` as in image [likely means Special — CONFIRM].
- Below that, separate dark box with npm logo:
```
npm
A package manager for JavaScript, included with
Node.js. npm makes it easy for developers to share
and reuse code.
Learn more
```
  - This appears to be a pasted screenshot/card, not handwritten.
  - Arrow: from npm dark box upward to `Spacial npm packages...` box.

## 6. Owner-stated facts NOT on board but given in chat (2026-09-21)

- `fully local the tool` — R.E.M is fully local.
- `we dont scop a mcp we scop a big one` — scope is a big application, NOT a small MCP server.
- GitHub: `https://github.com/NiklasNK-Creator/TheOniProject/`
- Requested folders: `main`, `docs`, `out` + `agents.md` with strict rules (always update docs before done, double-check code, don't simplify, split long/complicated into smaller pieces, ask unclear things, propose ideas for yes/no).

## 7. What is NOT on the board (do not assume)

- No tech stack beyond Taurin/Tauri + Rust + npm + fork of 9router + Scrapling link.
- No data schemas, no file formats, no API endpoints, no auth, no OS targets, no UI mockups.
- No definition of Sessions, Skills, MCPS, Token Dashboard metrics.
- No order/priority, no MVP vs v1, no deadlines.

## 8. Preservation rule

- Do NOT delete or overwrite this file with interpretations. Append corrections only with owner approval + date + reason.
- When quoting the board elsewhere, cite box text exactly, then add `[likely means X — CONFIRM]` if needed.
