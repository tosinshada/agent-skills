---
name: explore-idea
description: Interactively explore an idea from product and tech perspectives, culminating in a structured markdown document that captures the problem, solution space, open questions, and next steps. Use when the user wants to think through a new feature, product concept, or startup idea before writing specs or starting implementation.
---

# explore-idea

Guides the user through a structured but conversational exploration of an idea — covering product thinking and technical feasibility — and produces a markdown document that can seed requirement gathering, technical design, and implementation planning.

## Overview

This skill is a thinking partner, not a form-filler. The goal is to surface what's known, what's assumed, and what still needs answering before any spec or code is written. It works by asking probing follow-up questions at each stage, surfacing alternatives, and challenging weak assumptions — all in dialogue with the user.

The output document is intentionally rough: it captures the current state of thinking, not a final answer.

## Process

Work through three phases in sequence. Each phase is a conversation — ask, listen, probe deeper, then move on. Do not rush to the next phase until the current one feels sufficiently explored.

---

### Phase 1 — The Idea

Start here. Ask the user to describe the idea in their own words, then probe to establish the foundation needed for requirements:

- Who is the target user and what specific problem are they running into?
- What does the user currently do instead? What's broken or missing about that?
- What must this do to be considered a success — what's the non-negotiable outcome?

**Dig deeper if:** the user describes a solution rather than a problem, or the target user and their context aren't concrete. Push: *"Describe the moment when a user would reach for this — what just happened?"*

---

### Phase 2 — Product Requirements

Drive toward concrete requirements by working through the user journey and decision points:

- Walk through the core flow step by step — what does the user do, see, and decide at each step?
- What are the must-have behaviors for the first version? What can be deferred?
- Where do edge cases or exceptions live in this flow — what happens when things go wrong?
- What does the user need to input or configure, and what should the system decide automatically?
- Are there roles or permissions to consider — who can do what?

**Surface requirement gaps:** For each step in the user journey, ask *"What information does the system need here, and where does it come from?"* This often reveals unstated data or integration requirements.

**Dig deeper if:** requirements are described in terms of UI elements rather than behaviors, or it's unclear what the system is responsible for vs. the user.

---

### Phase 3 — Technical Decisions

Surface the key technical decisions that will shape the architecture and implementation:

- What data needs to be stored, and what are the read/write patterns?
- Which parts should be built vs. bought — are there APIs, services, or libraries that handle core functionality?
- What are the integration points with external systems — who owns the data and what does access look like?
- Where are the performance or reliability constraints — does anything need to be real-time or highly available?
- What are the security or compliance requirements that constrain the design?

**Force decisions on ambiguity:** For each uncertain area, name the options and ask the user to pick: *"You could store this client-side or server-side — which matters more, offline access or cross-device sync?"*

**Identify the riskiest bet:** At the end of this phase, name the single biggest technical unknown and what decision needs to be made to resolve it.

---

### Synthesis

After all three phases, summarize what you've heard and ask the user to confirm before writing the document:

- *"Here's what I think the core insight is: [one sentence]. Does that feel right?"*
- *"The biggest open question seems to be [X]. Agree?"*
- *"I'd flag [Y] as the riskiest assumption. Want to address that before we write this up?"*

Only write the document after this check-in.

---

## Output Document

Write a markdown file named after the idea (e.g., `idea-[name].md`) and save it to the user's workspace. Structure:

```markdown
# [Idea Name]

> One-sentence summary of the idea and the problem it solves.

## The Problem
[Who has it, how they experience it, why now.]

## The Idea
[What the solution is, the core user journey, the MVP scope.]

## Alternatives Considered
[Other approaches discussed and why this direction was chosen.]

## Technical Shape
[Core components, key risks, build vs. buy decisions, the riskiest technical bet.]

## Open Questions
[Unresolved assumptions and decisions still to be made, ranked by importance.]

## Next Steps
[What to do next — prototype, user interview, spike, spec — with a clear first action.]
```

Keep each section tight. Prefer bullets over prose for scanability. This document should be readable in under 5 minutes.

## Best Practices

- Stay in dialogue mode throughout — don't dump all questions at once. Ask one or two at a time and respond to what you hear before moving on.
- Name tensions explicitly: *"There's a tension here between X and Y — which would you rather optimize for?"*
- When the user is stuck, offer a concrete example or analogy to unstick them.
- It's fine to revisit an earlier phase if a later question reveals something that changes it.
- Flag when an assumption is load-bearing: *"This whole thing depends on [X] being true — how confident are you in that?"*
- Do not push toward any particular conclusion. The goal is clarity, not validation.
