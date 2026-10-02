# Spec: Calf Rehab Coach (criteria-gated, conversational recovery coaching)

**Status:** Draft v0.1 · 2 Oct 2026
**Owner:** Runa
**Source:** Notion, "Reverse engineer calf rehab programme" (Problem Definition, with User interviews, Injury definition & research, Competitive Landscape and Calf rehab project pages). The Solution, Execution, GTM and Post-launch sections of that page are empty, so this spec fills the Solution section.

> **Evidence caveat.** Everything below rests on a single-user case (the owner's own Grade 2 medial gastrocnemius strain, Feb–Apr 2026) and desk research. There are no external users yet, and market size is unquantified. Items marked **[Assumption]** are my inferences, not findings. Decisions are recorded in the Decision log (section 9).

## 1. Why now / problem

A person recovering from a calf strain cannot get continuous guidance adapted to their injury, history, sport and progress. Generic guidance ignores the individual risk factors that drive re-injury. Full definition and evidence are on the Notion page. The points that shape this spec:

- Grade does not reliably predict recovery time (one Munich Consensus category spans 3–132 days). Progression should follow clinical and functional re-assessment, not the calendar.
- The first two months carry the highest re-injury risk. The strongest predictors of a future strain are age and a prior calf strain.
- Calf-specific return-to-sport (RTP) criteria, such as ≥90% symmetry, are borrowed from hamstring research and have low-to-very-low certainty evidence. They are working targets, not validated cut-offs.
- Competitive gap: no product combines conversational AI with calf-specific, criteria-gated progression. SportsRehab.App has the gating without personalisation. Sword, Exakt and WHOOP personalise without a calf-specific RTP pathway.
- The user interview points to **adherence and speed to a first professional opinion** as the real friction, not content quality.

## 2. Goals and non-goals

**Goals**
1. Give an injured athlete a day-by-day plan that adapts to logged pain, function and sport demands.
2. Gate progression on objective criteria (pain trend, functional tests, symmetry), never on elapsed weeks alone.
3. Make logging near-zero-effort, turning vague updates ("felt tight after the walk") into structured records.
4. Apply safety guardrails: red-flag escalation, and no diagnosis.
5. Support safe return to sport (basketball, tag rugby, running, cycling, skiing) with no re-injury in the following 3 months.
6. Double as a credible case study for the owner's job applications and AI-product skills (stated project goal).

**Non-goals** (from the problem definition)
- A multi-injury MSK platform.
- Diagnosis or triage. Ruling out Achilles rupture and DVT stays with A&E, GP or physio. The product starts after that.
- A substitute for a clinician.
- Medical-device certification. Decided: positioned as wellness (Decision log 4).

## 3. Users

**Primary (v1):** the owner, a high-adherence, well-resourced recreational multi-sport athlete with a home gym, using the product for a new or repeat injury.

**Secondary (future, no pilot planned; Decision log 5):** recreational athletes (basketball, tag rugby, running) with a clinician-confirmed calf strain who want self-serve guidance. **[Assumption]** The segment is broader than basketball, since basketball-specific incidence data is too thin to size.

## 4. Scope

### Existing foundation (already built, from the Calf rehab project)
- Claude project with protocols and a "women-specific research first" standard.
- Notion logging: Gastrocnemius Rehab Tracker (daily log), exercise library, weekly reviews, phased programmes.
- KPIs already in use: pain 0–10, pain-free activity checklist, morning stiffness, single-leg heel raise, single and triple hop, depth jump, limb symmetry.

### v1 requirements

| # | Requirement | Priority |
|---|---|---|
| R1 | **Safety intake.** Before any plan, confirm a clinician has assessed the injury. Capture mechanism, onset, DVT risk factors and Achilles-rupture signs. Block plan generation and show a "see a clinician" path if intake is incomplete or shows red flags. | P0 |
| R2 | **Red-flag monitor.** Every check-in screens for the warning signs in the Injury definition page: worsening pain after 48–72 h, whole-leg swelling, warmth or redness, a new sharp pain, a visible defect, or tight, pale or tingling symptoms. Escalate by urgency tier (urgent review versus emergency). The product never reassures through a red flag. | P0 |
| R3 | **Phase model with exit criteria.** Phases advance only when criteria are met. Time since injury is context, not a trigger. Suggested phases follow the literature: protect, early loading, progressive strengthening, plyometric, sport-specific and contact. **[Assumption]** The final phase names and criteria are drafted from the evidence pages and the owner's programme, then reviewed by a physio (a friend who is also a basketball coach; Decision log 3). | P0 |
| R4 | **Conversational check-in.** Free-text or voice update converted to structured fields (pain at rest, pain during activity, next-day soreness, walking quality, morning stiffness). Ask clarifying questions only when a field that gates safety or progression is missing. | P0 |
| R5 | **Adaptive daily plan.** Generate the session from the current phase, last check-in and personal risk profile (age, prior strain, ankle instability or hypermobility, sport, equipment). | P0 |
| R6 | **Functional test protocol.** Guide the user through heel-raise-to-failure, hop tests and the pain check. Compute symmetry and record the result against the phase gate. | P0 |
| R7 | **Evidence labelling.** Each recommendation states whether it is calf-specific, extrapolated (for example from hamstring or tendon research), or general. It flags when no female-specific research exists. | P0 |
| R8 | **Progress view.** Trend lines for pain, strength and symmetry, plus the current phase and which exit criteria are met or outstanding. | P1 |
| R9 | **Return-to-sport ladder.** Staged, individually cleared reintroduction per sport. No two high-demand contact sports in the same week before each is cleared. | P1 |
| R10 | **Nutrition and recovery adherence nudges.** Reminders and low-friction logging only. Target calculation is already solved and is out of scope. | P2 |
| R11 | **Post-RTP maintenance.** Ongoing eccentric calf work and a re-injury watch for the first 2 months after return. | P2 |
| R12 | **Clinician share.** Exportable summary of the log and test results for a physio visit. | P2 |

### Out of scope for v1
Multi-injury support, wearables or camera movement tracking, imaging interpretation, in-app clinician messaging, payments.

## 5. Key flows

1. **Onboarding.** Safety intake (R1), then risk profile and goals, then a clinician-assessment confirmation, then the starting phase.
2. **Daily loop.** Check-in (R4), then red-flag screen (R2), then adaptive session (R5), then post-session log. A missed day triggers a gentle prompt, not a penalty.
3. **Gate review.** When the user reports being ready, or the criteria data suggests it, run the tests (R6) and either advance or hold with a reason.
4. **Escalation.** A red flag stops the plan and gives clear next steps by tier, and the app records that escalation occurred.

## 6. Guardrails and design principles

- The product coaches. It does not diagnose, and it never overrides a clinician's instruction.
- Pain and function lead the progression. Calendar timelines are shown only as typical ranges, never as promises.
- Be explicit about uncertainty. RTP thresholds such as ≥90% symmetry are labelled "working target, borrowed from hamstring evidence".
- Women-specific research is the first source. If none exists, say so (the existing project standard).
- Avoid NSAID advice in the first 24–72 hours beyond "ask your clinician". The evidence is mixed, and the bleeding-risk concern is the better-supported one.

## 7. Success metrics

From the Problem Definition. **Targets are not yet set.**

| Metric | Definition | Target |
|---|---|---|
| Primary (single user) | Full, unrestricted return to sport inside the clinically estimated window with no re-injury | Met or missed per user, so qualitative |
| Primary (pilot) | % of cohort completing a criteria-gated RTP progression within or sooner than their clinically suggested time, without re-injury in the following 3 months | TBD |
| Safety | Red-flag escalations shown when a flag was logged | 100% (should be a hard requirement, not a KPI) |
| Adherence | Daily check-in completion rate | TBD |
| Friction | Time from install to first clinician-confirmed intake | TBD |
| Quality | Share of recommendations carrying an evidence label | 100% |

**Future-user metric (Decision log 7):** recovery earlier than or on time with the clinical projection, given the plan adherence target is met, with no re-injury in the agreed window. The adherence target and window are still to be defined.

**Counter-metric:** a premature phase advance, meaning an advance followed by a pain increase or a re-injury within 2 weeks.

## 8. Risks

- **Medical and liability.** An AI coach near a clinical decision. Mitigate with clear non-diagnostic positioning, escalation tiers and physio review of phases and criteria. Positioned as wellness (Decision log 4); keep claims and wording consistent with that.
- **Weak evidence base.** Calf RTP criteria are low-certainty, so the gating logic is partly a judgement call and must be presented as one.
- **n = 1.** Fast recovery (single-leg heel raise on day 6, ≥90% symmetry around week 6) may not generalise. The owner's profile (high adherence, same-week hospital care, unlimited time) is atypical.
- **Competitive response.** Exakt could add calf depth. Sword or Hinge could unbundle a consumer product. Both are flagged as threats in the landscape scan.
- **Unsized market.** Do not build the pitch on a TAM figure. None can be supported yet.

## 9. Decision log

1. **[Decision made]** Is v1 a personal tool plus portfolio case study, or a pilot with outside users? This changes R1, R12 and the regulatory stance.
   1. Personal v1 tool.
2. **[Decision made]** Which interface: the existing Claude project and Notion, or a new app?
   1. Depends on solution discovery. Prototype via Lovable, Claude and Figma Make.
   2. Infrastructure needs are a source of truth for data (currently Notion), an input GUI (currently Claude), chat (Claude) and a plan overview (Notion). The direction is for all user interfaces to sit in one place (a web app, e.g. built in Lovable). Data pipes and agent structure are to be confirmed, which needs a technical infrastructure spike (added to the milestones).
3.  **[Decision made]** Which physio reviews the phase definitions and exit criteria?
   1. A friend who is a physio and a basketball coach, so has specific knowledge of this use case. He will review.
4.  **[Decision made]** What regulatory position (wellness coaching versus medical-device claim)?
   1. Wellness.
5. **[Decision made]** How many pilot users, and what recruitment route?
   1. No pilot is planned currently.
   2. **Still open:** whether a future pilot stays calf-only or lets people choose from a few common sports injuries.
6. **[Decision made]** Data handling: where health data lives, retention, and GDPR basis if any external user is added.
   1. **[Decision made]** Lives in Notion for now.
   2.  **Still open:** A future version depends on the technical infrastructure spike.
7. **[Partially open]** Success-metric targets (adherence, time to first intake).
   1. **[Decision made]** For any future injury and any future user: recovery earlier than or on time with the clinical projection, if the user has met the plan adherence target, with no re-injury within a set period.
   2. **Still open:** the adherence target and the re-injury window (x) are not yet defined.

## 10. Rough milestones

No dates have been given, so none are asserted.

1. Technical infrastructure spike: single-place UI, source of truth for data, data pipes and agent structure, with prototypes in Lovable, Claude and Figma Make (Decision log 2 and 6).
2. Physio review of the phase model and criteria (Decision log 3).
3. Prototype R1-R6 on the stack chosen after the spike.
4. Dogfood on a new injury or the maintenance phase.
5. Define the adherence target and re-injury window (Decision log 7).
6. If a pilot is ever planned, decide calf-only versus a few common injuries (Decision log 5), then scope R8-R12.
7. Post-launch review (feeds the empty Post-launch section on Notion).
