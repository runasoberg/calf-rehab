# CLAUDE.md: how Claude works in this repository

## Project
Calf Rehab Coach: a criteria-gated, conversational recovery coaching product, currently a personal tool plus portfolio case study (owner: Runa). It coaches; it never diagnoses and is positioned as wellness, not a medical device. The source of truth for scope and decisions is `supporting_documentation/claude_1st_draft_PRD.md`, including its decision log.

## Folder map and where things go
- `problem_discovery/`: problem definition, interviews, injury and competitor research. Evidence only; no solutions.
- `solution_discovery/`: options exploration. `plan.md`, `prompts.md`, and `prototypes/` (single-file HTML, hard-coded data, low fidelity).
- `final_product/`: the chosen solution once decided: specs, code, product docs.
- `supporting_documentation/`: cross-cutting reference (PRD drafts, protocols, templates, decision records).
- Put new files in the folder that matches the stage of work. If unsure, ask rather than guess. Do not create new top-level folders without asking.
- Folder and file names are lowercase snake_case. Keep `README.md` and `CLAUDE.md` in upper case so tools find them.
- Each folder has a `README.md` saying what belongs there. Update it when you add or move files.

## Working rules
- Read the PRD before proposing product, scope or design changes. Do not contradict a recorded decision; if you think one is wrong, say so and ask.
- Never fabricate research, studies or statistics. Label claims as evidence, inference or assumption (the PRD uses **[Assumption]**). If there is no evidence, say so. Calf-specific return-to-sport criteria are low-certainty and are working targets, not validated cut-offs.
- Health content: no diagnosis, no contradicting a clinician, no NSAID advice beyond "ask your clinician". Red-flag escalation is never softened or gamified. Progression is by criteria, with calendar time as context only. Every recommendation carries an evidence label (calf-specific, extrapolated, general).
- Phase names and exit criteria are drafts until the physio review (PRD decision 3).
- Personal health data stays in Notion for now (PRD decision 6). Do not commit real health data to this repo; use sample data.
- Ask when a gap would change the answer (who it is for, which sport, which stage). State any assumption you make.
- Use British English. Keep answers direct, without padding or opening affirmations.

## Prototype conventions (solution_discovery)
- All prototypes use the shared brief and sample data in `solution_discovery/prompts.md` (Phase 3 of 5, 86% symmetry, HOLD) so directions stay comparable.
- Prototypes are web apps, desktop-first (1440px), with hard-coded data and no backend.
- Keep each direction's styles and components separate. Do not blend directions.
- Lovable project: "Calf Rehab Discovery". The Figma connector cannot create Make files; the Make prompt is section D of `prompts.md` and is pasted by the user.

## Git and GitHub
- Develop on the branch you are assigned for the session. Commit with clear messages and push to that branch.
- Do not open a pull request unless asked. Do not push to `main` directly. Do not force-push or rewrite history without explicit permission.
- Use `git mv` for moves and renames so history is kept. Check no links or paths are left pointing at the old location.
- After a branch's pull request is merged, fast-forward the branch to the latest `main` before starting follow-up work.
- Check for a pull request template before opening a PR, and keep descriptions short and factual.

## Tools
- Notion: current source of truth for logging, exercise library and weekly reviews. Read from it; do not write to it unless asked.
- Lovable and other credit-based tools: confirm before spending credits, and stop and report if credits run out.
