---
name: idea-to-product-theme
description: Transforms a raw idea into a focused product theme — a strategic statement of purpose, target user, core problem, and guiding principles. Use when the user wants to define the strategic direction of a product, establish a product mission, or formulate the north star that will guide specs and implementation.
---

# idea-to-product-theme

Guides the user from a rough idea to a concise, strategic **Product Theme** — a single document that captures what the product is for, who it serves, why it matters, and the principles that shape every decision going forward.

## Overview

A product theme is not a feature list or a spec. It is the strategic goal of the application: the mission-level framing that makes every subsequent product and engineering decision coherent. Without it, specs drift and features conflict. With it, the team has a shared answer to *"does this belong in the product?"*

This skill works by asking focused questions, challenging vague answers, and synthesizing the responses into a `THEME.md` document. The conversation is brief and purposeful — typically 4–6 exchanges — not an open-ended exploration.

> **Related skills:** Use `explore-idea` first if the idea is still very rough and needs broad exploration. Use `write-product-spec` after the theme is set to define individual features.

---

## Process

Work through three stages. Each stage has a goal and a set of probing questions. Move to the next stage only when the current one has a clear, concrete answer.

---

### Stage 1 — The Idea in One Sentence

Ask the user to state the idea in a single sentence. Then probe until it is specific:

- What does it do? For whom? In what situation?
- What exists today that the user would replace or complement?
- What is the trigger — why does this feel like the right moment?

**Challenge vagueness:** If the answer is "it helps people with X," ask: *"What specifically does it do that they cannot do today?"* Push until the sentence is concrete enough to be falsifiable.

**Goal:** One sentence that uniquely identifies the product and its context. Example: *"A scheduling tool that lets freelancers block focus time before clients can book calls."*

---

### Stage 2 — User, Problem, and Stakes

Explore the human problem at the center of the idea:

- Who is the primary user? Describe a specific person, not a demographic.
- What is the exact moment they feel the pain this product addresses?
- What do they do today to cope? Why is that inadequate?
- What changes in their life or work if this product exists?
- Who else is affected — secondary users, stakeholders, payers?

**Probe depth:** If the user describes the problem abstractly (e.g., "people waste time"), ask: *"Walk me through what that person does on a bad day without this product. What goes wrong, step by step?"*

**Goal:** A vivid, specific description of the user and their unsolved problem — concrete enough to use as a test: *"Would this person immediately recognize themselves in our product?"*

---

### Stage 3 — Strategic Goal and Principles

Synthesize the idea and problem into a strategic direction:

- What is the single most important thing this product must do well?
- What should it deliberately **not** do? (Scope boundaries are as important as scope.)
- What is the core insight or bet — the thing that is true about users or the market that others have missed or ignored?
- What are 2–3 principles that should guide every product and design decision?
- How will you know the product has succeeded in 12 months?

**Examples of principles:**
- *"Protect the user's attention — never add a feature that pulls focus."*
- *"Every interaction should take less than 30 seconds."*
- *"Work where the user already works; never require a context switch."*

**Goal:** A strategic framing that a new team member could read and immediately understand what belongs in the product and what does not.

---

## Output: THEME.md

After the conversation, write `THEME.md` to the project root (or `strategy/THEME.md` if a `strategy/` directory exists or the user prefers it).

Use this structure:

```markdown
# Product Theme: <Product Name>

## Mission
One sentence: what the product does, for whom, and why it matters.

## Target User
A specific description of the primary user — their context, goals, and the moment they feel the pain this product addresses.

## Core Problem
The exact problem the product solves. Include what users do today and why that falls short.

## Strategic Goal
What the product must do better than anything else. This is the north star for every product decision.

## Non-Goals
What the product will not do. Explicit scope boundaries prevent scope creep.

## Guiding Principles
2–4 short principles that shape product and design decisions. Each principle should be specific enough to resolve a tradeoff.

## Success Signal
How you will know the product is working in 12 months. Prefer observable, user-centered signals over vanity metrics.
```

Keep each section tight — one short paragraph or a concise list. The whole document should fit on one page. Brevity signals clarity of thinking.

---

## Best Practices

- **Resolve ambiguity before writing.** A vague theme produces a vague document. Keep asking until answers are concrete.
- **One primary user.** If the product serves multiple users, name the primary one first. Secondary users can be noted but should not dilute the mission.
- **Principles must resolve tradeoffs.** A principle like "be simple" is too vague. A principle like "never require the user to leave the current screen" is actionable.
- **Non-goals are not failures.** Explicitly saying what the product won't do is a strategic act, not a limitation.
- **The mission sentence is the hardest part.** Spend extra time on it. If it can describe five different products, it needs more specificity.
