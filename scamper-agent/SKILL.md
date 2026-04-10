---
name: scamper-agent
description: >
  Generates and prioritizes innovation ideas using SCAMPER brainstorming + ICE scoring, producing
  a strategic recommendation report. Use this skill whenever the user wants to brainstorm, improve,
  or find creative alternatives for a product, service, or process — or needs to evaluate and rank
  multiple ideas. Also trigger on "SCAMPER", "ICE scoring", "innovate on", "generate ideas",
  "which idea should I pursue", or any request to systematically explore and narrow down options.
---

# SCAMPER Agent

A 4-stage workflow for turning a rough idea into a prioritized, actionable strategic recommendation.
The workflow guarantees every idea gets evaluated — no skipping, no vague "and so on" shortcuts.

## Stages at a Glance

1. **Clarify Goals & Constraints** — Understand goals and constraints before brainstorming
2. **SCAMPER Brainstorming** — Generate indexed ideas across all 7 SCAMPER dimensions
3. **Idea Screening** — Filter by constraints, then score retained ideas with ICE
4. **Strategic Recommendation Report** — Synthesize into an integrated strategic recommendation

---

## Stage 1: Clarify Goals & Constraints

**Pause here.** Before generating any ideas, infer reasonable defaults from the user's initial
input and present a proposed configuration for confirmation. Do not ask four open-ended questions
and wait — instead, do the thinking for the user and let them correct what's wrong.

### What to infer

First, extract any information the user has already stated explicitly — adopt it as-is rather
than re-inferring or paraphrasing. Then deduce plausible defaults only for the dimensions the
user did not address:

- **Primary goal** — What core problem or opportunity does this idea address?
- **Budget** — Rough range or category (e.g., minimal / moderate / unconstrained)
- **Timeline** — Expected execution window (e.g., 2 weeks / 3 months / 1 year)
- **Known constraints** — Technical limitations, regulatory requirements, team capacity, etc.

### How to present

Output a single proposed configuration block and ask the user to confirm or adjust:

> Based on your input, here is my proposed configuration:
> - **Primary Goal:** [inferred]
> - **Budget:** [inferred, e.g., "Moderate — no large infrastructure rebuild"]
> - **Timeline:** [inferred, e.g., "1–3 months"]
> - **Known Constraints:** [inferred, or "None identified — let me know if there are any"]
>
> Does this look right? Adjust anything that's off; otherwise I'll move to SCAMPER.

If the user's input is too vague to infer even a rough goal (e.g., just "brainstorm something"),
ask a single focused question about the goal rather than listing all four dimensions.

Do not proceed to Stage 2 until the user has confirmed or adjusted the configuration.

---

## Stage 2: SCAMPER Brainstorming

Generate 1–3 ideas per dimension using the context from Stage 1. Adjust density to the topic:
lean toward 1 idea for straightforward dimensions where forced generation would produce filler,
and up to 3 for dimensions with genuinely rich possibilities. Quality over quantity — every idea
must be actionable and distinct, not a rephrased variant of another. Each idea should go beyond
the obvious first-association answer — if an idea feels like the first thing anyone would suggest,
push further. The value of SCAMPER is in the non-obvious connections.

Each idea gets a unique ID starting from 1 within its dimension (e.g. S-1, S-2, C-1, C-2)
for tracking through Stage 3.

Cover all 7 dimensions in order. Keep the SCAMPER letter as-is but append a translated label
when the user's language is not English (e.g., "S — 替代 (Substitute)", "C — 結合 (Combine)"):

- **S — Substitute**: What components, materials, or processes could be replaced?
- **C — Combine**: What unrelated technologies or services could be merged?
- **A — Adapt**: What principles from other fields could be borrowed?
- **M — Modify / Magnify / Minify**: How could features, scale, or frequency be changed?
- **P — Put to Another Use**: Where else could the core mechanism be applied?
- **E — Eliminate**: What could be removed to create a leaner, faster version?
- **R — Reverse**: What new approach emerges from reversing the process or structure?

**Output format:**

> **S — Substitute**
> - S-1: [Idea name] — [One-sentence description]
> - S-2: [Idea name] — [One-sentence description]
>
> **C — Combine**
> - C-1: [Idea name] — [One-sentence description]
>
> *(repeat for all 7 dimensions; number of ideas per dimension may vary)*
>
> *(Example shown in English. For non-English users, apply translated labels per the rule above.)*

---

## Stage 3: Idea Screening

Process **every single ID from Stage 2** through both tiers. Skipping IDs or using phrases like
"and the rest follow the same pattern" is not allowed.

### Tier 1 — Constraint Filter

Compare each idea against the Primary Goal, budget, timeline, and constraints from Stage 1.
An idea should be removed if it violates a hard constraint **or** has no meaningful connection
to the Primary Goal. Classify each idea into one of three categories. The total count of
Removed + Conditional + Retained must equal the total number of ideas generated in Stage 2 —
do not leave any ID unaccounted for.

**Output format:**

> **Removed** (fails a hard constraint or misaligned with Primary Goal):
> - **S-2: Name** — Exceeds budget: requires enterprise GPU cluster with no phased alternative
> - **P-1: Name** — Off-target: addresses brand awareness but Primary Goal is reducing wait time
>
> **Conditional** (viable only if a specific adjustment is made — state the prerequisite):
> - **A-1: Name** — Exceeds timeline as-is; feasible if scoped to a single market first
>
> **Retained** (passed all constraint checks as proposed):
> - **S-1: Name**, **C-1: Name**, ...

### Tier 2 — ICE Scoring

Score every Retained and Conditional idea. For Conditional ideas, score them assuming the stated
prerequisite is met, and note this in the Notes column.

Use these calibration anchors to maintain scoring consistency and differentiation:

| Score | Impact | Confidence | Ease |
|-------|--------|------------|------|
| 1–2 | Negligible improvement | Pure speculation, no supporting evidence | Requires major new capabilities or infrastructure |
| 3–4 | Minor quality-of-life gain | Theoretically sound but untested | Significant effort; depends on external factors |
| 5–6 | Meaningful, measurable improvement | Plausible with indirect evidence or analogies | Moderate effort within current team capacity |
| 7–8 | Strong strategic advantage | Supported by data, case studies, or prior success | Straightforward with existing tools and skills |
| 9–10 | Game-changing or market-defining | Proven approach with high certainty | Can ship within days using what's already in place |

Calculate **ICE Score = Impact × Confidence × Ease** and rank all scored ideas by ICE Score descending.

**Output format:**

> | Idea | ICE Score | Impact | Confidence | Ease | Notes |
> |------|-----------|--------|------------|------|-------|
> | S-1: Name | 432 | 6 | 9 | 8 | Easy win; well-understood technology that fits within current sprint |
> | C-1: Name | 280 | 8 | 7 | 5 | High impact but requires cross-team coordination; proven in adjacent domain |
> | A-1: Name ⚠️ | 210 | 7 | 6 | 5 | **Conditional:** score assumes single-market scoping per Tier 1 |
> | *(all Retained + Conditional ideas, sorted by ICE Score descending)* | | | | | |

---

## Stage 4: Strategic Recommendation Report

Synthesize all prior stages into a structured report using the template below.
Every recommendation must trace back to specific idea IDs from Stage 2 — do not introduce
unnamed concepts. The MVP section should draw from Conditional ideas (with their prerequisites)
and high-Ease Retained ideas to form a viable first step.

**Output format:**

> # Innovation Sprint Report: [Idea / Topic]
>
> ## 1. Innovation Insights
> [2–3 sentences on the most creative or unexpected breakthroughs from Stage 2]
>
> ## 2. Execution Roadmap
> [Based on ICE ranking: which ideas to pursue first, second, and why. Reference idea IDs
> explicitly (e.g., "Begin with S-1 and E-2 as quick wins, then invest in C-1").
> Address risk mitigation for high-Impact but low-Confidence ideas.]
>
> ## 3. Integrated Recommendation Solution
>
> ### Recommended Solution
> [Description of the optimal proposal balancing Impact and Ease. Reference the idea IDs
> being combined (e.g., "Combines S-1 + C-1: ..."). May integrate multiple ideas.]
>
> ### Resource Allocation
> [Specific guidance on budget and time distribution across recommended ideas, referencing IDs]
>
> ### MVP / Downgraded Compromise
> [A minimum viable version built from high-Ease Retained ideas and/or Conditional ideas
> whose prerequisites are achievable. This is a scoped-down subset of existing ideas,
> not a new proposal. Reference IDs and state the path to evolve toward the full solution.]
>
> ## Appendix: Considered but Excluded
> [One-line summary per Removed idea from Stage 3 Tier 1, with the reason for exclusion.
> Supplementary reference for stakeholders — not part of the core recommendation.]

---

## Execution Rules Summary

- **Never skip Stage 1 clarification** — brainstorming without constraints wastes everyone's time
- **Every idea gets an ID** — makes tracking unambiguous across all stages
- **Exhaustive screening** — if an idea has an ID, it gets processed; no exceptions
- **ICE rationale required** — a score without explanation is not useful
- **Report integrates all stages** — don't introduce new ideas in Stage 4; synthesize what's there
- **Language mirroring** — detect the user's language and use it for all structural labels, headers, report titles, and explanatory text