# 08 — Skills (Native Feature — almost fully OPEN)

## 1. FACT

- Board has a box `Skills` under `Nativ Fetures`. No children, no notes.

## 2. What we do NOT know

- What is a Skill in R.E.M? Agent skill (prompt + tools + scripts, e.g. OpenCode/Claude skills)? User skill? Model skill? (Q-skill-definition — critical.)
- Format? Markdown `SKILL.md` + scripts? Where stored? How versioned?
- Built-in vs installable? (Parallels plugins? Or distinct?)
- Scope? Global vs per-session vs per-model?
- Execution? Who runs skill code — Rust backend? Frontend? Sandboxed? Which permissions?
- Relationship to `MCPS` and `PLugins`? Overlap or distinct? Board lists all three separately, so treat as distinct until owner merges them.

## 3. Hypothesis (NOT fact)

Likely similar to agent-skills convention (markdown + optional scripts/tools) managed natively and fully local. Do NOT assume — needs Q-skill-* answers.

## 4. Safe next steps

- Propose skill folder layout draft (proposal):
```
(requires approval)
main/skills/<skill-id>/SKILL.md
main/skills/<skill-id>/scripts/...
main/skills/<skill-id>/skill.json  // metadata: name, version, permissions
```
- Propose 1 example skill (`hello-skill`) as DRAFT text, not code, in `13_`.
- Do NOT implement skill runner until definition is confirmed.

## 5. Checklist

- [ ] Q-skill-definition, Q-skill-format, Q-skill-execution answered
- [ ] This file updated with final spec + 1 full example (unsimplified)
- [ ] Code split: `skill_model.rs`, `skill_loader.rs`, `skill_runner.rs` (proposal)
