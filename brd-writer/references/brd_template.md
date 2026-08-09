# BRD Section Template
 
A full-scope BRD has 16 sections. Not every project needs all of them at full weight — use the guidance below to decide what to include, shrink, or cut. When in doubt, include the section but keep it short rather than omitting it; reviewers expect to see the full skeleton even if some parts are brief.
 
## Cover page
 
Title, one-line description, "Business Requirements Document", version, date, confidentiality classification if relevant (many corporate BRDs mark this "Confidential — Internal Use Only" even without a strict requirement to). Skip classification for informal/internal-only documents if the user doesn't want the formality.
 
## 1. Document Control
 
- **1.1 Version History** — table: Version / Date / Author / Description of Change. Always include, even if it's just one row ("0.1 — Initial draft").
- **1.2 Reviewers & Approvers** — table: Name / Role / Action Required / Date. Include for any BRD that needs formal sign-off. Skip or shrink for informal/internal drafts.
- **1.3 Distribution List** — table: Name / Role / Organisation. Optional — include for multi-party or cross-organization projects, skip for small internal efforts.
## 2. Executive Summary
 
2-4 paragraphs, readable by a non-technical sponsor. Cover: what this is, why it's being built, what it connects to / doesn't connect to (its boundaries), and the headline business value. This is the section most likely to be read in full by senior approvers — make it stand alone.
 
## 3. Background & Context
 
Why now. Typically includes:
- How things work today (briefly — full detail goes in Current State if that section exists)
- Limitations of the current approach
- Market/competitive/regulatory pressure driving the change, if relevant
- Where this fits in a broader program, if it's one project among several
Compress into 1-2 subsections for smaller projects.
 
## 4. Problem Statement
 
Table: `# / Problem / Business Impact`. Each row is a distinct problem, stated as a fact about the world, paired with the concrete cost of leaving it unsolved. This table is what every later requirement should trace back to — a reviewer should be able to ask "which problem does BR-X solve?" and get an answer.
 
## 5. Stakeholder Analysis
 
- **5.1 Stakeholder Register** — table: Stakeholder / Role / Organisation / Interest-Involvement. Use `[Name]` placeholders freely; role and involvement matter more than names at BRD stage.
- **5.2 User Roles Within the Service** — only if the thing being built has distinct user roles/permission levels (e.g., Admin vs. Customer, Approver vs. Requester). Describe what each role can do. Skip if there's only one type of user or the project isn't a system with roles at all.
## 6. Scope
 
- **6.1 In Scope** — bullet list of capabilities being delivered.
- **6.2 Out of Scope** — table: `# / Item / Where It Is Covered (if elsewhere)`. Explicitly naming what's *not* included prevents scope creep disputes later — don't skip this even if the list is short.
- **6.3 Assumptions** — conditions the project depends on being true (e.g., "the upstream service is live before go-live").
- **6.4 Constraints** — hard boundaries on the solution (regulatory, technical, contractual) that requirements must respect.
## 7. Current State (As-Is)
 
Only include if this project replaces, automates, or improves something that already exists. Skip entirely for genuinely greenfield builds — don't manufacture a fake "current state" for something that's never existed.
 
- Narrative summary of how it works today (a short blockquoted "AS-IS:" summary works well)
- Bullet list of the actual step-by-step current process
- **Pain Points table**: `# / Pain Point / Business Impact` — same shape as the Problem Statement table but more granular/operational.
## 8. Future State (To-Be)
 
Pairs with Current State — include if 7 is included, or standalone for greenfield builds framed as "how this will work."
 
- Narrative "TO-BE:" summary
- **Architecture/Position table**, if the project sits among other systems: `Layer / Component / Role` — shows what this project calls, what calls it, and what's explicitly out of its hands. Very useful for integration-heavy projects; skip for standalone tools.
- **Key use cases** — 2-4 concrete scenarios written as short narratives (UC-1, UC-2...), showing the future state from a user's point of view end to end. These earn their place because they make abstract requirements concrete for reviewers.
## 9. Business Objectives
 
Table: `# / Objective / Description`. 3-6 objectives, each a short punchy name plus a sentence of description. These should be outcomes ("reduce processing time," "capture new revenue segment"), not features.
 
## 10. Business Requirements
 
The core of the document. Organize into subsections by functional area (10.1, 10.2, ...) — group related requirements rather than one flat numbered list. For each subsection, a table:
 
`Ref ID / Requirement / Business Justification / Priority`
 
- **Ref ID**: short domain prefix + section number + sequence, e.g. `BR-AUTH-2.1`. Agree the prefixes with the user or pick sensible ones from the functional areas identified during scoping.
- **Requirement**: stated as a system/process obligation in business language — "must," "must be able to." Precise enough to be testable, but not an implementation spec.
- **Business Justification**: ties back to a Problem Statement row or Business Objective. Never leave this generic.
- **Priority**: state the key once at the top of the section, e.g. *"MUST HAVE = non-negotiable for go-live. SHOULD HAVE = high value, include if feasible. COULD HAVE = desirable, post go-live."* MoSCoW is the default; use the user's preferred scheme if they have one (e.g. P0/P1/P2).
## 11. Non-Functional Requirements
 
Only include categories that are actually relevant — don't pad. Table: `Ref ID / Category / Requirement / Specification`. Common categories: Performance, Availability, Security, Scalability, Compliance/Regulatory, Usability. A purely internal tool might need only Performance and Security; a public-facing financial API needs most of them.
 
## 12. Risks & Mitigations
 
Table: `Risk / Likelihood / Impact / Mitigation`. 3-6 risks worth flagging to a sponsor — not an exhaustive project-management risk register, just the ones that would change someone's mind about approving the project if unaddressed.
 
## 13. Dependencies
 
Table: `Dependency / Description / Owner`. External systems, teams, or decisions this project's success depends on. Skip if the project is fully self-contained.
 
## 14. Success Criteria
 
Grouped bullet lists (by theme, e.g. "Payment Processing," "Governance") stating what must be true for the project to be considered successfully delivered. These should be checkable against the requirements and NFRs already stated — don't introduce new unstated requirements here.
 
## 15. Glossary & Acronyms
 
Table: `Term/Acronym / Definition`. Include any term used in the document that a first-time reader (especially a non-technical approver) might not know. Build this from what actually appears in the document, don't paste a generic industry glossary.
 
## 16. Appendices
 
- **Related Documents** — table: `# / Document Title / Description`. Other docs this BRD references or is referenced by (architecture overviews, PRDs, related BRDs).
- **Governing Regulatory Instruments** — only for regulated industries (finance, healthcare, etc.) — bullet list of the specific laws/regulations/standards in play.
---
 
## Adapting for smaller or informal BRDs
 
For a lightweight internal BRD, a reasonable minimal skeleton is: Executive Summary, Problem Statement, Scope (in/out), Stakeholders, Business Requirements, Success Criteria. Drop Document Control formality, Current/Future State, and the Glossary if the audience is small and already knows the domain. Always ask, don't assume — some organizations require the full formal shape even for small projects because it's their standard template.