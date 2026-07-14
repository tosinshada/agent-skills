---
name: explore-idea
description: Interactively explore an idea from product, tech, and growth perspectives, culminating in a structured markdown document that captures the problem, solution space, open questions, and next steps. Use when the user wants to think through a new feature, product concept, or startup idea before writing specs or starting implementation.
---

# explore-idea

Guides the user through a structured but conversational exploration of an idea — covering product thinking, technical feasibility, and growth/business angle — and produces a markdown document that can seed requirement gathering, technical design, and implementation planning.

## Overview

This skill is a thinking partner, not a form-filler. The goal is to surface what's known, what's assumed, and what still needs answering before any spec or code is written. It works by asking probing follow-up questions at each stage, surfacing alternatives, and challenging weak assumptions — all in dialogue with the user.

The output document is intentionally rough: it captures the current state of thinking, not a final answer.

## Process

Work through four phases in sequence. Each phase is a conversation — ask, listen, probe deeper, then move on. Do not rush to the next phase until the current one feels sufficiently explored.

---

### Phase 1 — The Idea (5 min)

Start here. Ask the user to describe the idea in their own words, then probe:

- What problem does this solve? Who has it? How do they live with it today?
- What made you think of this now? Is there a trigger or trend?
- What does success look like in 6 months? In 2 years?
- What's the one thing this must do well?

**Dig deeper if:** the problem statement is vague, the user conflates the solution with the problem, or the target user isn't clear. Push back with: *"If you couldn't build this specific solution, what would the user do instead?"*

---

### Phase 2 — Product Thinking

Explore the shape of the solution and its user experience:

- Who is the primary user? What's their context when they need this?
- Walk me through the core user journey — what do they do, step by step?
- What's the simplest version of this that still delivers value? (Avoid scope creep early.)
- What are the obvious alternatives or competitors? Why would a user choose this instead?
- What assumptions are baked into the design that could be wrong?

**Prompt alternatives:** If the user has a strong opinion on the solution shape, offer at least one meaningfully different approach and ask what they'd lose or gain. Example: *"You described a dashboard — have you considered a notification-push model instead? What would change?"*

**Dig deeper if:** the MVP isn't clearly separable from nice-to-haves, or the differentiation is weak.

---

### Phase 3 — Technical Perspective

Explore what it would take to build:

- What are the core technical components or services needed?
- Where does complexity live — data, integrations, real-time requirements, scale?
- What's technically novel or risky here? What would you prototype first?
- What existing systems or third-party services could you lean on vs. build?
- What data do you need, and where does it come from? Who owns it?
- Are there compliance, privacy, or security concerns?

**Probe assumptions:** If the user hand-waves a hard problem (e.g., "we'd use AI for that"), ask: *"What specifically would the model need to do? What happens when it's wrong?"*

**Identify the riskiest bet:** At the end of this phase, name the single biggest technical unknown and ask how they'd de-risk it.

---

### Phase 4 — Growth & Business Angle

Explore how the idea creates and captures value:

- Who pays, and why? What's the pricing intuition?
- How does the first user find this? How do you get to 100 users? 10,000?
- Is there a natural network effect or data flywheel?
- What does the competitive moat look like over time?
- What are the failure modes — why might this not work?

**Challenge assumptions:** If the user says "word of mouth" or "viral growth," push: *"What specifically triggers someone to share this? Have you seen that happen in similar products?"*

---

### Synthesis

After all four phases, summarize what you've heard and ask the user to confirm before writing the document:

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

## Growth & Business
[Who pays, go-to-market intuition, moat, failure modes.]

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
