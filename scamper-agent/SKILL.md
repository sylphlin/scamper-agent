---
name: SCAMPER Agent
description: >
  A structured 4-stage innovation workflow that combines SCAMPER brainstorming with ICE scoring
  to systematically generate, screen, and prioritize ideas into an actionable strategic report.
  Use this skill whenever a user wants to brainstorm improvements to a product, service, or process,
  explore creative alternatives to a problem, evaluate and prioritize innovation ideas, or produce
  a structured innovation recommendation. Trigger on phrases like "brainstorm ideas for",
  "innovate on", "find creative solutions to", "evaluate which ideas to pursue", "SCAMPER",
  or any request that involves generating many ideas and narrowing them down.
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

**Pause here.** Before generating any ideas, ask the user to confirm:

- **Primary goal** — What core problem or opportunity does this idea address?
- **Budget** — Rough range or category (e.g., minimal / moderate / unconstrained)
- **Timeline** — Expected execution window (e.g., 2 weeks / 3 months / 1 year)
- **Known constraints** — Technical limitations, regulatory requirements, team capacity, etc.

Do not proceed to Stage 2 until the user has responded and you have confirmed their answers.

---

## Stage 2: SCAMPER Brainstorming

Generate 1–2 ideas per dimension using the context from Stage 1. Each idea gets a unique ID
starting from 1 within its dimension (e.g. S-1, S-2, C-1, C-2) for tracking through Stage 3.

Cover all 7 dimensions in order:

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
> - C-2: [Idea name] — [One-sentence description]
>
> *(repeat for all 7 dimensions)*

---

## Stage 3: Idea Screening

Process **every single ID from Stage 2** through both tiers. Skipping IDs or using phrases like
"and the rest follow the same pattern" is not allowed.

### Tier 1 — Constraint Filter

Compare each idea against the budget, timeline, and constraints from Stage 1. The total count
of Removed + Retained must equal the total number of ideas generated in Stage 2 — do not
leave any ID unaccounted for.

**Output format:**

> **Removed** (explain why each fails a constraint):
> - **S-2: Name** — Exceeds budget: requires enterprise GPU cluster
>
> **Retained** (passed all constraint checks):
> - **S-1: Name**, **C-1: Name**, ...

### Tier 2 — ICE Scoring

For every retained idea, score on three dimensions (1–10) and provide a brief rationale for each score:

| Dimension | What to evaluate |
|-----------|-----------------|
| **Impact** | Value delivered if successful; alignment with Stage 1 goals |
| **Confidence** | Probability it works based on existing knowledge and evidence |
| **Ease** | Implementation simplicity given available resources and timeline |

Calculate **ICE Score = Impact × Confidence × Ease** and rank retained ideas by ICE Score descending.

**Output format:**

> | Idea | ICE Score | Impact | Confidence | Ease | Notes |
> |------|-----------|--------|------------|------|-------|
> | S-1: Name | 432 | 6 | 9 | 8 | Easy win; well-understood technology that fits within current sprint |
> | C-3: Name | 280 | 8 | 7 | 5 | High impact but requires cross-team coordination; proven in adjacent domain |
> | *(all retained ideas, sorted by ICE Score descending)* | | | | | |

---

## Stage 4: Strategic Recommendation Report

Synthesize all prior stages into a structured report using the template below.

**Output format:**

> # Innovation Sprint Report: [Idea / Topic]
>
> ## 1. Innovation Insights
> [2–3 sentences on the most creative or unexpected breakthroughs from Stage 2]
>
> ## 2. Execution Roadmap
> [Based on ICE ranking: which ideas to pursue first, second, and why. Address risk mitigation
> for high-Impact but low-Confidence ideas.]
>
> ## 3. Integrated Recommendation Solution
>
> ### Recommended Solution
> [Description of the optimal proposal balancing Impact and Ease. May combine multiple ideas.]
>
> ### Resource Allocation
> [Specific guidance on budget and time distribution across recommended ideas]
>
> ### MVP / Downgraded Compromise
> [A minimum viable version prioritizing high-Ease ideas that can launch quickly,
> with a path to evolve toward the full solution]

---

## Execution Rules Summary

- **Never skip Stage 1 clarification** — brainstorming without constraints wastes everyone's time
- **Every idea gets an ID** — makes tracking unambiguous across all stages
- **Exhaustive screening** — if an idea has an ID, it gets processed; no exceptions
- **ICE rationale required** — a score without explanation is not useful
- **Report integrates all stages** — don't introduce new ideas in Stage 4; synthesize what's there