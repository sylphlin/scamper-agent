# SCAMPER Agent

The SCAMPER Agent is an AI-powered innovation facilitator that guides users through a structured brainstorming and evaluation process based on the SCAMPER Technique.

## Overview
When faced with a complex problem, exploring creative alternatives, or seeking improvements to a product, service, or process, it is easy to get lost in unstructured brainstorming. The SCAMPER Agent solves this by taking you through a rigorous, systematic sprint to guarantee every idea is generated, tracked, and systematically evaluated. 

## Methodology
The agent's workflow is built upon two proven frameworks:

### SCAMPER
A creative thinking technique used to generate new ideas by asking targeted questions across 7 dimensions:

| Letter | Dimension | Description |
| :---: | :--- | :--- |
| **S** | **Substitute** | What components, materials, or processes could be replaced? |
| **C** | **Combine** | What unrelated technologies or services could be merged? |
| **A** | **Adapt** | What principles from other fields could be borrowed? |
| **M** | **Modify** | How could features, scale, or frequency be changed? (Includes Magnify/Minify) |
| **P** | **Put to another use**| Where else could the core mechanism be applied? |
| **E** | **Eliminate** | What could be removed to create a leaner, faster version? |
| **R** | **Reverse** | What new approach emerges from reversing the process or structure? |

### ICE Scoring
A prioritization framework that evaluates retained ideas based on three criteria, ensuring consistent ranking:

| Metric | What to evaluate |
| :---: | :--- |
| **Impact** | The potential value delivered if successful; alignment with primary goals. |
| **Confidence** | The probability it works based on existing knowledge and evidence. |
| **Ease** | Implementation simplicity given available resources and timeline. |

Each metric is scored 1–10 using the following calibration anchors:

| Score | Impact | Confidence | Ease |
| :---: | :--- | :--- | :--- |
| 1–2 | Negligible improvement | Pure speculation, no supporting evidence | Requires major new capabilities or infrastructure |
| 3–4 | Minor quality-of-life gain | Theoretically sound but untested | Significant effort; depends on external factors |
| 5–6 | Meaningful, measurable improvement | Plausible with indirect evidence or analogies | Moderate effort within current team capacity |
| 7–8 | Strong strategic advantage | Supported by data, case studies, or prior success | Straightforward with existing tools and skills |
| 9–10 | Game-changing or market-defining | Proven approach with high certainty | Can ship within days using what's already in place |

## How It Works
The SCAMPER Agent uses a 4-stage workflow to turn rough goals into actionable strategies:
1. **Clarify Goals & Constraints:** Infers primary goals, budgets, timelines, and constraints from user input, then presents a proposed configuration for confirmation.
2. **SCAMPER Brainstorming:** Methodically generates indexed ideas mapped strictly to the SCAMPER framework.
3. **Idea Screening:** Filters ideas through a constraint and goal-alignment check (removing, retaining, or flagging as conditional), then rigorously ranks the qualified ones by calculating their ICE scores.
4. **Strategic Recommendation Report:** Synthesizes results into a strategic report with an execution roadmap, resource allocation plan, recommended MVP, and an appendix of excluded ideas.

## Usage
You can integrate this agent configuration into Gemini Gems (using [`gemini-gem.md`](gemini-gem.md)), or if you want to use it as an available skill, you can refer to the [`scamper-agent/`](scamper-agent/) directory. 

Trigger the agent by asking prompts like:
- *"Brainstorm ideas for improving our onboarding process."*
- *"Innovate on our existing mobile app."*
- *"Find creative solutions to reduce customer churn."*
- *"Use SCAMPER to evaluate which marketing ideas we should pursue."*