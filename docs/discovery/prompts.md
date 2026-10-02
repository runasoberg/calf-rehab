# Prototype prompts (Claude and Lovable)

Use A as the shared brief (Lovable: paste into Project Knowledge; Claude: put at the top of every prototype prompt). Then add one block from B per prototype. C is the Lovable-only wrapper, sent first.

## A. Shared brief

```
You are a product designer and front-end prototyper. We are doing SOLUTION DISCOVERY for "Calf Rehab Coach", a web app for a recreational multi-sport athlete recovering from a calf (gastrocnemius) strain. I am the only user for now. I want to compare five very different interface directions, so each prototype must be bold and distinct, not a variation on a common template.

PRODUCT IN ONE PARAGRAPH
A conversational, criteria-gated recovery coach. It replaces four things that currently live in separate tools: a source of truth for data, a daily input/logging screen, a coach chat, and a plan overview. Progression through rehab phases is gated on pain trend, functional tests and limb symmetry, never on elapsed time alone. The real friction is adherence and logging effort, not content quality, so logging must be near-zero effort. It coaches and never diagnoses.

LOW-FIDELITY MEANS
Clickable, mobile-first (390px) and usable on desktop. All data is hard-coded sample data, no backend, no auth, no real AI. Placeholder icons and illustration are fine. Pixel polish is NOT the goal. Layout, information hierarchy, input mode, metaphor and tone ARE the goal. Keep each prototype's code small and readable. Mark anything faked with a subtle "prototype" tag.

SIX SCREENS (every direction must include all six, reachable by navigation)
1. Safety intake: confirm a clinician has assessed the injury; capture mechanism, onset, DVT risk factors, Achilles-rupture signs. If incomplete or if red flags are present, BLOCK plan creation and show a "see a clinician" path. Include this blocked state.
2. Daily check-in: pain at rest (0-10), pain during activity (0-10), next-day soreness, walking quality, morning stiffness. Show the sample utterance "felt tight after the walk, a bit sore this morning" being turned into those structured fields, with the coach asking a clarifying question only if a safety- or progression-critical field is missing.
3. Red-flag escalation: a triggered state with two tiers: URGENT REVIEW (e.g. worsening pain after 48-72h, new sharp pain, visible defect) and EMERGENCY (e.g. whole-leg swelling with warmth/redness, tight/pale/tingling leg). Plain, serious, unmissable. The plan stops. The app records that escalation occurred.
4. Today's plan: one session of 4-6 exercises (e.g. seated and standing heel raises, isometric holds, single-leg balance, eccentric lowers). Each exercise carries an EVIDENCE LABEL: "Calf-specific", "Extrapolated (from hamstring/tendon research)" or "General", and where relevant "No female-specific research found".
5. Gate review and functional tests: guide through heel-raise-to-failure (both legs), single hop and triple hop, then a pain check. Compute limb symmetry and show the result against the phase gate: ADVANCE or HOLD, with the reason. The 90% symmetry target is always labelled "working target, borrowed from hamstring evidence".
6. Progress: trends for pain, strength and symmetry; the five-phase model with the current phase and which exit criteria are met or outstanding; and a return-to-sport ladder where basketball and tag rugby are cleared separately (never two high-demand contact sports cleared in the same week).

PHASES (draft, awaiting physio review): 1 Protect, 2 Early loading, 3 Progressive strengthening, 4 Plyometric, 5 Sport-specific and contact.

SHARED SAMPLE DATA (use exactly, so all five prototypes tell the same story)
Currently Phase 3 of 5. Day 34 since injury (shown only as context: "typical range, not a promise"). Single-leg heel raises: left (injured) 18, right 21, so 86% symmetry, below the 90% working target. Pain during activity 2/10, at rest 0/10. Morning stiffness 10 minutes. Exit criteria for Phase 3: pain <=2/10 during activity (MET), morning stiffness <15 min (MET), heel-raise symmetry >=90% (NOT MET), single-leg hop pain-free (NOT YET TESTED). Today's decision: HOLD in Phase 3, retest in 5-7 days.

NON-NEGOTIABLE SAFETY AND TONE RULES (these override any style choice)
- Red-flag escalation is never gamified, softened, animated for delight or buried. No reward or streak is ever attached to it. The product never reassures through a red flag.
- A missed day gets a gentle, neutral prompt. No penalties, no shaming, no lost-streak language.
- Never diagnose. Never contradict a clinician. No NSAID advice beyond "ask your clinician".
- Progression is by criteria. Calendar time is context only.
- Every recommendation shows its evidence label.
- Be explicit about uncertainty. Use plain British English.

DELIVERABLE FORMAT
Own your direction fully: its own layout system, type, colour tokens, navigation model, copy voice. Do not reuse patterns from the other directions. End with a short "What this direction is betting on" note (3 lines) in the prototype's about/footer area.
```

## B. Direction blocks (one per prototype)

```
DIRECTION 1: CLINICAL NOTEBOOK (conservative)
Bet: a familiar, trustworthy dashboard is enough, and it is the lowest-risk replacement for Notion plus a form.
Metaphor: a well-organised patient record. Left sidebar (bottom tab bar on mobile): Today, Check-in, Tests, Progress, Log. Neutral palette, one calm accent, system or humanist sans, generous whitespace, tables and cards, standard form controls (sliders, radio groups, checkboxes). Phase shown as a horizontal stepper with a criteria checklist beneath. Chat is a collapsible side panel, secondary to forms. Tone: professional, plain, reassuring without over-promising. Avoid illustration, gradients and animation beyond basic transitions.
```

```
DIRECTION 2: CONVERSATION IS THE INTERFACE (wildly modern)
Bet: a single conversational canvas with generative UI makes logging near-zero-effort.
Metaphor: one endless thread with the coach. There are no pages. UI components materialise inline in the thread when needed: pain sliders, a hop-test timer, a symmetry chart, the phase gate card, the red-flag card. Voice-first: a large push-to-talk control, live transcript, text as fallback. Dark, high-contrast, large type, fluid motion, a command palette (/ or cmd-K) to jump to progress, tests or plan. Structured fields visibly "crystallise" from the transcript. Tone: concise, direct, curious. Push this far past what a normal health app would dare, while keeping the red-flag card the most visually dominant element anywhere in the app.
```

```
DIRECTION 3: RECOVERY QUEST (playful)
Bet: play lifts adherence, and lowers the dread of rehab, without trivialising safety.
Metaphor: a side-scrolling game map. Phases are levels, exit criteria are gates, the functional tests are boss challenges, the injured leg is a friendly avatar that visibly strengthens. Bright, chunky, rounded, sticker-like, bouncy micro-animation, XP for logging and completing sessions. Quick-log is big tappable emoji-style tiles. Tone: warm, jokey, on your side. Constraints: XP rewards consistency of honest logging, never pushing through pain; HOLD at a gate is shown as "not yet, here is what's left", not failure; the red-flag screen drops the playfulness completely and goes plain and serious.
```

```
DIRECTION 4: PERFORMANCE LAB (data-led athlete dashboard)
Bet: a high-adherence athlete is motivated by numbers and readiness, like WHOOP, Oura or a training log.
Metaphor: a mission-control readout. Dense, dark or graphite, tight grid, monospace numerals. Hero element: a readiness/gate ring showing criteria met (2 of 4). Symmetry curve over time with the 90% working-target line. Pain and stiffness sparklines. Return-to-sport ladder as a stacked progress bar per sport. Logging is quick: preset chips, steppers, one-tap "same as yesterday". Chat is a small command-line style box. Tone: terse, analytical, coach-like. Show confidence/uncertainty on every metric.
```

```
DIRECTION 5: CALM COMPANION (one thing at a time)
Bet: showing less on screen improves adherence, especially when returning after a missed day.
Metaphor: a daily ritual with a gentle guide. The app is essentially one screen at a time: a single next action, big, with a quiet progress dot trail for the day (check-in, session, reflect). Soft earthy palette, serif or rounded type, lots of space, slow easing, optional ambient sound toggle (non-functional). Progress, phase and tests live behind a "My journey" page as a calm timeline, not a dashboard. Missed-day return screen: "Welcome back. No catching up needed." Tone: kind, unhurried, grounded. The red-flag state must still be unambiguous and drop the calm styling entirely.
```

## C. Lovable wrapper (send first)

```
Create a project "Calf Rehab: discovery" (React, Tailwind, shadcn/ui, no backend).
1. Add the SHARED BRIEF as project knowledge.
2. Create a landing page at "/" with five large cards linking to /1 to /5, each showing the direction name and its one-line bet. Add a small "prototype" tag.
3. I will send each direction as a separate message. Build ONLY the route named in that message, inside its own folder (src/directions/dN/), with its own components, its own Tailwind theme tokens (CSS variables scoped to that folder) and its own sample data file. Do NOT share components, styles or layout with other directions, and do not restyle any existing route. Stop after each direction and wait for the next.
Start by setting up the landing page and the empty routes only.
```

Lovable sequence: set Project Knowledge to A, send C, then send each B block (prefix with "Build route /N now:") one message at a time, reviewing the preview between each.

Claude sequence: for each prototype, send A followed by one B block and ask for a single self-contained HTML file. Run the five in separate chats or subagents so the styles do not bleed together.
