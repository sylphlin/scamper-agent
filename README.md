# SCAMPER Innovation Sprint Agent

This repository contains the SCAMPER Agent, an AI-powered innovation facilitator designed to guide users through a structured brainstorming and evaluation process. 

## Overview
When faced with a complex problem, exploring creative alternatives, or seeking improvements to a product, service, or process, it is easy to get lost in unstructured brainstorming. The SCAMPER Agent solves this by taking you through a rigorous, systematic sprint to guarantee every idea is generated, tracked, and objectively evaluated. 

## Methodology
The agent's workflow is built upon two proven frameworks:
- **SCAMPER:** A creative thinking technique used to generate new ideas by asking targeted questions across 7 dimensions: **S**ubstitute, **C**ombine, **A**dapt, **M**odify, **P**ut to another use, **E**liminate, and **R**everse.
- **ICE Scoring:** A prioritization framework that evaluates retained ideas based on three criteria: **I**mpact (value delivered), **C**onfidence (probability of success), and **E**ase (implementation simplicity).

## How It Works
The SCAMPER Agent uses a 4-stage workflow to turn rough goals into actionable strategies:
1. **Clarify Goals & Constraints:** Collects primary goals, budgets, timelines, and constraints to ensure all generated ideas are grounded in reality.
2. **SCAMPER Brainstorming:** Methodically generates indexed ideas mapped strictly to the SCAMPER framework.
3. **Idea Screening:** Filters out constraint-breaching ideas and rigorously ranks the remaining ones by calculating their ICE scores. 
4. **Strategic Recommendation Report:** Synthesizes the surviving concepts into a concrete execution roadmap, resource allocation plan, and a recommended MVP (Minimum Viable Product).

## Usage
You can integrate this agent configuration into Gemini Gems (using [`gemini-gem.md`](gemini-gem.md)), or if you want to use it as an available skill, you can refer to the [`scamper-agent/`](scamper-agent/) directory. 

Trigger the agent by asking prompts like:
- *"Brainstorm ideas for improving our onboarding process."*
- *"Innovate on our existing mobile app."*
- *"Find creative solutions to reduce customer churn."*
- *"Use SCAMPER to evaluate which marketing ideas we should pursue."*