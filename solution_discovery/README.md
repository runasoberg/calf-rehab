# solution_discovery

Exploring different ways to solve the problem before committing to one.

- `plan.md`: the discovery plan, the five directions and how to evaluate them.
- `prompts.md`: shared brief, direction blocks, Lovable wrapper and Figma Make prompt.
- `opportunity_tree.html`: Teresa Torres-style opportunity solution tree (draft v0.1, 9 Oct 2026), built from the PRD and the Notion research. Single-file HTML, no build.
- `prototypes/`: five low-fidelity, single-file HTML prototypes plus `index.html`.

## Links

- Claude HTML prototypes (GitHub Pages, index of all five): https://runasoberg.github.io/calf-rehab/solution_discovery/prototypes/
- Opportunity tree (GitHub Pages, once merged to `main`): https://runasoberg.github.io/calf-rehab/solution_discovery/opportunity_tree.html
- Figma Make prototypes (published site, five directions; see below): https://phys-prototypes.figma.site/
- Lovable prototype (landing page with routes `/1` to `/5`): https://id-preview--2685ccc9-f51e-4cde-9287-ff774bcc672f.lovable.app
- Lovable editor (owner access needed): https://lovable.dev/projects/2685ccc9-f51e-4cde-9287-ff774bcc672f

GitHub Pages is enabled for this repo (source `main`, root folder).

## Opportunity tree

`opportunity_tree.html` maps a proposed desired outcome (daily check-in completion, with premature phase advances as the counter-metric) to 8 opportunities, 22 sub-opportunities and candidate solutions tagged to PRD requirements R1 to R12. Each node is labelled Evidence, Inference or Assumption.

- All evidence is one person's injury. The Notion interviews were retrospective (Sep 2026), and it is unconfirmed whether the GP, physio and nutritionist interviews were with real clinicians.
- Recommended target (opinion, not data): opportunity 4, staying consistent day to day, starting with logging effort and scattered tools. Red-flag handling (opportunity 2) is treated as a guardrail on every branch.
- Gap found: holding back on good days (opportunity 6) has no PRD requirement. Decision for the owner: whether pace and load caps belong in R5.
- The desired outcome is a proposal. The adherence target and re-injury window are still open (PRD decision 7).
- The four solution options for logging line up with prototype directions 1, 2, 4 and 5, so the prototype walk-through in `plan.md` doubles as the first test.

## Lovable build status

Confirmed by the owner on 8 Oct 2026: routes `/1` to `/3` are built; `/4` and `/5` are not.

| Route | Direction | Status |
|---|---|---|
| `/1` | Clinical notebook | Built |
| `/2` | Conversation is the interface | Built |
| `/3` | Recovery quest | Built and self-tested by Lovable; also fixed `/2` build errors |
| `/4` | Performance lab | Not built (credits ran out before it ran) |
| `/5` | Calm companion | Not built |

Open the preview routes above to see what exists now. Note the Lovable credits ran out twice, and the free plan may do so again. The preview link may change or need access if the project's visibility changes. Lovable's own sample data and exercise doses are placeholders and need physio review.

## Figma Make directions

Figma Make produced its own five directions from the shared brief. Descriptions below come from the landing page of the published site (cards and tags only; I have not reviewed the screens inside each). The landing page says "5 distinct experiences, 6 screens in each" and shows the shared sample data (Day 34, Phase 3 of 5, 86% symmetry, 2/10 pain, HOLD).

| # | Name | Tagline and tags | Look and feel |
|---|---|---|---|
| 01 | The Companion | "A little reassurance. A clear next step." Calm and supportive, daily dashboard. | Warm, sage green, sidebar (Your day, Your plan, Your progress), "Good morning" greeting. |
| 02 | The Clinic | "Clarity you can put your trust in." Clear and clinical, evidence-led. | White and blue clinical workspace, overview metric cards, trend chart. |
| 03 | The Fieldwork | "A considered approach to getting back." Direct and focused, training workspace. | Dark, uppercase headline ("Build the base"), large numerals. |
| 04 | The Journal | "Make space for your recovery." Thoughtful and personal, recovery journal. | Editorial, serif, warm cream, "There's room to take your time". |
| 05 | The Navigator | "See where you are. Know what comes next." Guided and visual, step-by-step pathway. | Purple, five-step pathway (Settle, Restore, Build, Prepare, Return). |

### How they compare with the five directions in `plan.md` (mapping confirmed by the owner)

- The Clinic looks closest to 1 Clinical notebook, The Fieldwork to 4 Performance lab, and The Companion to 5 Calm companion.
- The Journal and The Navigator have no counterpart in the plan: an editorial journal, and a guided phase pathway.
- Nothing in Make's set resembles 2 Conversation is the interface or 3 Recovery quest. Make's five sit in a narrower, calmer range, so the wildly modern and playful ends of the spectrum are only covered by the Claude and Lovable prototypes.
- The Navigator labels the five phases Settle, Restore, Build, Prepare, Return, which differs from the draft phase names in `prompts.md` (Protect, Early loading, Progressive strengthening, Plyometric, Sport-specific and contact). Phase names are still drafts for physio review.
- Names such as "calf & care", "wayforward" and the user "Alex" are invented by Make for the prototype.

Record evaluation results and the chosen direction here.
