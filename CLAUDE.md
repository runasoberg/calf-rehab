# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project
Calf Rehab Coach: a criteria-gated, conversational recovery coaching product, currently a personal tool plus portfolio case study (owner: Runa). It coaches; it never diagnoses and is positioned as wellness, not a medical device. The source of truth for scope and decisions is `supporting_documentation/claude_1st_draft_PRD.md`, including its decision log.

This is a docs-and-prototypes repo. There is no build, lint or test tooling.

## Folder map
- `problem_discovery/`: problem definition, interviews, injury and competitor research. Evidence only; no solutions. Currently empty; the material is in Notion.
- `solution_discovery/`: options exploration (`plan.md`, `prompts.md`, `prototypes/`, and a `README.md` with all prototype links).
- `final_product/`: the chosen solution once decided. Currently empty.
- `supporting_documentation/`: cross-cutting reference (PRD drafts, protocols, templates, decision records).
- Put new files in the folder matching the stage of work; if unsure, ask. Do not create new top-level folders without asking.
- Names are lowercase snake_case, except `README.md` and `CLAUDE.md`. Each folder has a `README.md`; update it when you add or move files.

## Working rules
- Read the PRD before proposing product, scope or design changes. Do not contradict a recorded decision; if you think one is wrong, say so and ask.
- Never fabricate research, studies or statistics. Label claims as evidence, inference or assumption (the PRD uses **[Assumption]**). Calf-specific return-to-sport criteria are low-certainty working targets, not validated cut-offs.
- Health content: no diagnosis, no contradicting a clinician, no NSAID advice beyond "ask your clinician". Red-flag escalation is never softened or gamified. Progression is by criteria; calendar time is context only. Every recommendation carries an evidence label (calf-specific, extrapolated, general).
- Phase names and exit criteria are drafts until the physio review (PRD decision 3).
- Personal health data stays in Notion (PRD decision 6). Do not commit real health data; use sample data.
- Ask when a gap would change the answer; state any assumption you make.
- Use British English.

## Prototype tracks (solution_discovery)
The same brief is built three ways, so changes ripple across all three:
- **Claude HTML:** single-file, hard-coded-data prototypes in `solution_discovery/prototypes/` (`index.html` links all five), published via GitHub Pages.
- **Lovable:** project "Calf Rehab Discovery", built from a copy of the brief stored as Lovable project knowledge (10,000-character limit). The build was paused when credits ran out.
- **Figma Make:** published site at https://phys-prototypes.figma.site/. Make chose its own five directions (Companion, Clinic, Fieldwork, Journal, Navigator), so they do not map one-to-one to the plan. See `solution_discovery/README.md`.

Rules:
- `solution_discovery/prompts.md` is the single source for the shared brief and direction blocks. Change it there first, then re-sync the Lovable knowledge. The Figma Make prompt is section D, pasted into Make by the user (the Figma connector cannot create Make files).
- All tracks use the same sample data (Phase 3 of 5, 86% symmetry, HOLD) and the draft phase names. If either changes, update every track.
- Prototypes are desktop-first web apps (1440px), no backend. Keep each direction's styles and components separate; do not blend directions.

## Running and checking prototypes
- Open any prototype directly in a browser; no server is needed. GitHub Pages is enabled (source `main`, root folder) and serves the prototypes at https://runasoberg.github.io/calf-rehab/solution_discovery/prototypes/.
- To verify a prototype headlessly, use Playwright with the pre-installed Chromium (`PLAYWRIGHT_BROWSERS_PATH=/opt/pw-browsers`; do not run `playwright install`). Check there are no JS errors and that all six screens are reachable.

## Git and GitHub
- Develop on the branch assigned for the session; commit with clear messages and push to it.
- Do not open a pull request unless asked. Do not push to `main` directly. Do not force-push or rewrite history without explicit permission.
- You may merge a pull request without asking again only when all of these hold:
  - you opened it in this session, and the user asked for it to be opened;
  - it has no unresolved review comments and no merge conflict, and any checks that exist have passed;
  - it changes only docs, READMEs or prototypes (not `final_product/`);
  - you use a normal merge commit, not a squash or rebase.
- Before merging, state in one line what you are merging and into which branch. Afterwards, fast-forward the working branch to `main`.
- Never merge a pull request someone else opened, one with a failing or pending check, or one touching `final_product/`, without an explicit "merge it" from the user. Never merge by pushing to `main`.
- Use `git mv` for moves and renames so history is kept, and check no links or paths still point at the old location.
- After a branch's pull request is merged, fast-forward the branch to the latest `main` before follow-up work.

## Tools
- Notion: current source of truth for logging, exercise library and weekly reviews. Read from it; do not write unless asked.
- Lovable and other credit-based tools: confirm before spending credits, and stop and report if credits run out.
