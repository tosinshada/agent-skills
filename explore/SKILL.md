---
name: explore
description: Explore an implementation problem with the human developer before code is written. Investigate the codebase, clarify requirements, compare approaches, expose constraints and risks, and turn uncertainty into settled implementation decisions. Use when the developer says "help me think this through", "explore options", "investigate before implementing", "I'm not sure how this should work", or otherwise has unresolved questions about the design or implementation; use before the `implementation-playbook` skill whenever the developer is not yet certain how a large change should be implemented. Also use to reassess a decision when implementation reveals unexpected complexity. Do NOT use to write application code, when all material decisions are already settled (use `implementation-playbook` for a large change), or for a routine small change that can be implemented directly.
---

# Explore

## What this does

Act as a thinking partner for a developer who has a problem but does not yet have a sufficiently
settled implementation direction. Ground the discussion in the actual repository, make tradeoffs
concrete, and help the developer decide what should happen before an implementation guide or code
is written.

Treat exploration as a stance, not a rigid workflow. Follow promising threads, revise the frame
when evidence changes it, and leave room for the developer to keep thinking. Do not force every
conversation through the same questions or require an artifact.

Exploration precedes an implementation playbook when the developer is uncertain about any
material implementation choice. The handoff is ready only when the remaining work is translation
and execution rather than design.

## Boundaries

- Read files, search the repository, inspect history, trace call sites, and run non-mutating
  diagnostics when useful.
- Do not write application code, refactor files, or start implementing the change.
- Do not disguise unresolved design questions as choices for the implementing agent.
- Do not create a document by default. Capture findings only when the developer asks.
- If the developer asks to implement while material choices remain open, explain what is still
  unresolved and continue exploring. If the choices are settled, offer to move to an
  implementation playbook for a large change or direct implementation for a small one.

## Process

### 1. Establish the question

Identify what the developer is trying to decide, why the decision matters, and what would make an
answer useful. Ask only questions that materially change the investigation. Prefer a few open
threads over a questionnaire.

Challenge the current framing when needed. A request framed as a library choice may actually be a
question about deployment, ownership, compatibility, or migration risk.

### 2. Establish ground truth

Inspect the repository before making code-specific claims:

- Find the repository root and read its contributor or agent instructions.
- Locate the current implementation by symbol and behavior, not guessed paths.
- Trace callers, types, data flow, tests, configuration, and external boundaries relevant to the
  decision.
- Read installed, vendored, or generated source when a third-party API detail affects the answer.
- Distinguish verified facts from inferences and assumptions.

Name the exact files and symbols that support important conclusions. If something cannot be
verified locally, say what is unknown and what evidence would resolve it.

### 3. Map the problem

Build the smallest useful model of the current and desired behavior. Depending on the question,
surface:

- invariants that must survive the change;
- constraints imposed by existing architecture or dependencies;
- integration points and affected packages;
- behaviors that should be preserved, translated, or deleted;
- hidden complexity, failure modes, and migration concerns;
- assumptions the developer is making, including assumptions that may be wrong.

Use a compact diagram, flow, state machine, or comparison table only when it makes relationships
materially easier to understand.

### 4. Explore viable approaches

Compare approaches against the actual constraints. For each serious option, explain:

- how it fits the current system;
- what it simplifies and complicates;
- what changes and what stays invariant;
- its operational, compatibility, and maintenance consequences;
- what evidence supports or weakens it;
- whether it introduces work outside the intended scope.

Discard non-viable options explicitly and explain why. When one option clearly dominates, say so
and make a recommendation. When the tradeoff depends on a developer-owned priority, present that
decision plainly instead of manufacturing certainty.

### 5. Resolve uncertainty

Keep the conversation open while important choices remain. Use targeted repository investigation,
small non-mutating experiments, or a proposed spike to close evidence gaps. A spike is an explicit
follow-up when answering the question would require implementation work; do not perform the spike
inside this skill.

Before declaring the direction settled, check for:

1. a material "should we" question the implementing agent would have to answer;
2. an unstated invariant or compatibility expectation;
3. an ambiguous deletion, fallback, feature flag, or migration path;
4. an unclear scope boundary or deferred improvement;
5. an unverified external API claim that could change the approach.

If any remains, continue exploring or record it as an explicit blocker. Do not pass it downstream
as implementer discretion.

### 6. Hand off when ready

When the implementation direction has crystallized, summarize:

- **Problem:** the concrete problem being solved;
- **Settled approach:** the chosen direction and why it won;
- **Fixed decisions:** choices that should not be re-litigated;
- **Invariants:** behavior and packages that must not change;
- **Scope:** what is included, excluded, and deferred;
- **Code map:** important files, symbols, and integration points;
- **Risks and verification needs:** what the implementation must prove;
- **Remaining unknowns:** ideally none; otherwise explain why a playbook is premature.

For a large change with no material implementation questions left, offer to use the
`implementation-playbook` skill next. Give it the exploration summary and any captured notes as
source context so it can produce a directive execution guide. Do not write the playbook while
still in exploration.

For a small, settled change, recommend direct implementation instead of manufacturing a playbook.

## Conversation style

- Be curious and adaptive rather than prescriptive.
- Make claims concrete and evidence-based.
- Surface multiple promising threads without turning them into an interrogation.
- Recommend a path when the evidence supports one.
- Let tangents continue when they expose a relevant constraint or assumption.
- Do not rush to an artifact or a conclusion merely to create a tidy ending.

## Non-negotiables

- **Do not implement.** Exploration changes understanding, not application code.
- **Ground repository-specific advice in the repository.** Do not reason from generic patterns
  when local evidence is available.
- **Separate fact, inference, and assumption.** Never present an unverified API or behavior claim
  as established truth.
- **Keep decisions with the developer.** Recommend firmly, but make developer-owned tradeoffs
  explicit.
- **Do not hand unresolved design to the implementer.** Continue exploration until the playbook
  can state decisions as settled.
- **Do not force a playbook.** Use it only for a large, already-decided change; keep exploring when
  uncertainty remains and implement small changes directly once settled.
