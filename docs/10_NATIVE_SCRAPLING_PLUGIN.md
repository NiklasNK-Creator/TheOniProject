# 10 — Native Plugin: Scrapling (via Native > Plugins > Nativ)

## 1. FACT

- Chain: `PLugins` → `Nativ` → `Scrapling` with link `( https://github.com/d4vinci/Scrapling )` in the Scrapling box.
- Spelling `Scrapling` as on board (upstream repo is also named Scrapling — so NOT a typo for the repo name; may still be wordplay on Scraping).

## 2. What upstream is (to verify, NOT yet inspected)

- `https://github.com/d4vinci/Scrapling` — needs inspection (language? Python? license? API?). No inspection done yet in this scaffold. Contributor task: read upstream README + license + examples, record FACTS here.
- Board placement says: Scrapling is a NATIVE plugin (ships with R.E.M, fully local).

## 3. OPEN questions (Q-scrap-*)

- Why Scrapling? Web scraping for agents? What use cases? (Q-scrap-usecase)
- How to embed? Python sidecar? Rust binding? Subprocess? WASM? Version pinning? Offline install? (Q-scrap-integration — critical for fully-local + Tauri+Rust.)
- Permissions? Which URLs allowed? Robots.txt respected? Rate limits? User confirmation per domain? Storage of scraped data? (Q-scrap-security)
- UI? “Scrape URL” action in session? Skill tool? MCP tool? All three?
- Updates? Track upstream releases? Vendor or depend?

## 4. Rules

- Do NOT `pip install` or vendor anything until license + integration are approved (fully-local + supply-chain safety).
- SELF-OWNED (OWNER DECISION 2026-09-21, binding): Scrapling + Python run in R.E.M-owned venv/sidecar (`%LOCALAPPDATA%/R.E.M/` or `<install>/resources/`). NEVER install into system Python, NEVER `pip install` globally, NEVER modify user site-packages. See `AGENTS.md` §4b + `13_` IDEA-013 + `12_` Q-tools-python.
- Any scraping must be user-initiated, logged, domain-visible, cancellable, rate-limited. No hidden crawling.
- Document upstream license + version pinned + why chosen, in this file, before coding.

## 5. Safe help now

- Summarize upstream repo (purpose, language, license, minimal example — link, don’t paste large code).
- Propose integration options table (sidecar vs binding vs CLI) with pros/cons for Tauri+Rust+fully-local.
- Mark all PROPOSAL pending Q-scrap-*.
