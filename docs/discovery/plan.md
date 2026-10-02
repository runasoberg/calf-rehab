# Calf Rehab Coach: solution discovery plan

Source: `docs/claude_1st_draft_PRD.md` (branch `claude/product-management-spec-87tvdk`). PRD Decision 2 leaves the interface open, pending solution discovery. This plan produces five deliberately different low-fidelity prototypes in both Claude and Lovable, so the direction can be narrowed before the technical spike or any high-fidelity work. The prompts are in `prompts.md`.

## Assumptions (correct any that are wrong)

- Web app, desktop-first (1440px), graceful down to tablet. Not a mobile app (confirmed by you).
- The user is you alone (PRD Decision 1). No multi-user, auth, payments or clinician messaging.
- All data is mocked, no backend. Data pipes and agent structure belong to the infrastructure spike.
- Screens cover PRD R1 to R9 as UI only, not working logic.
- Figma Make is in scope: prompt D in `prompts.md`.

## The five directions

They differ on four axes so the comparison is informative: information density, primary input mode, central metaphor, and tone.

| # | Direction | Metaphor | Primary input | Question it tests |
|---|---|---|---|---|
| 1 | Conservative: Clinical notebook | A well-organised patient record: tabs, tables, forms, phase stepper. Closest to today's Notion plus a form. | Structured forms, chat as a side panel | Is a familiar, low-risk dashboard enough? |
| 2 | Wildly modern: Conversation is the interface | One canvas. The coach talks and UI components (sliders, test timers, charts) appear inline. Voice-first, dark, command palette. | Voice and free text | Does generative UI make logging near-zero-effort (R4)? |
| 3 | Playful: Recovery quest | A game map. Phases are levels, exit criteria are gates, the leg is an avatar. | Taps and quick-log tiles | Does play lift adherence without trivialising safety? |
| 4 | Performance lab (my suggestion) | WHOOP or Oura-style athlete dashboard: dense, data-led, readiness ring, symmetry curve. | Quick-log chips plus charts | Does a data-first athlete identity suit a high-adherence user? |
| 5 | Calm companion (my suggestion) | A one-thing-at-a-time daily ritual. Progress tucked behind a journey page. | Guided step-by-step flow | Is less on screen better for adherence and for returning after a missed day? |

Why 4 and 5: they cover the athlete-identity and wellbeing-companion angles the first three miss, and they sit at opposite ends of the density spectrum from each other. This is my judgement, not evidence. Swap them if you have other angles in mind (for example a physio-session-player mode or a Notion-embedded view).

## Same six screens in every direction

Identical content makes the directions comparable.

1. Safety intake (R1), including the blocked "see a clinician" state.
2. Daily check-in (R4): "felt tight after the walk" becomes structured fields.
3. Red-flag escalation (R2): urgent review versus emergency tiers.
4. Today's plan (R5) with evidence labels (R7).
5. Gate review and functional tests (R6, R3): symmetry, advance or hold with the reason.
6. Progress (R8, R9): trends, phase model with criteria, return-to-sport ladder per sport.

Shared sample data: Phase 3 of 5, day 34 (context only), heel raises 18 left versus 21 right (86%, below the 90% working target), pain 2/10 during activity, stiffness 10 minutes, decision HOLD.

## Constraints that hold in every direction

These come from the PRD and override style: red-flag escalation is always plain and unmissable and never gamified; a missed day gets a gentle prompt, never a penalty; progression is by criteria with calendar time as context; every recommendation carries an evidence label; the 90% symmetry target is labelled "working target, borrowed from hamstring evidence"; no diagnosis and no NSAID advice beyond "ask your clinician".

## How to build

**Claude:** five self-contained clickable HTML prototypes (one file each, own design tokens, hard-coded data), built from the shared brief plus one direction block each, with an index page linking them. Not built yet. Say go and I will.

**Lovable:** one project with a landing page and five routes. Load the shared brief as project knowledge, send the wrapper prompt, then send the five direction blocks one message at a time. Each is told to keep its own folder, tokens and components so the styles do not blend. You can paste the prompts yourself, or I can run them through the Lovable connector, which spends workspace credits and so needs your say-so.

## Evaluation

Walk each prototype with the same three tasks: (a) log "felt tight after the walk, a bit sore this morning"; (b) find out why you have not advanced a phase; (c) respond to a red-flag. Score 1 to 5 on speed to log, clarity of gate status, trust and safety feel, whether you would open it daily, and fit with the single-place direction. Also compare Claude against Lovable output. These are one user's judgements, not user evidence. Aim for a shortlist of two directions or a hybrid, to take into the next round and the physio review.

## Verification checklist

- All six screens reachable in every direction, at desktop width.
- Red-flag screen present and dominant in every direction; no streak-shaming; evidence label on every exercise.
- Sample data identical across all five.
- The five are visibly different in layout and navigation. If two feel alike, regenerate the weaker with a sharper bet.
