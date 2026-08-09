# Clarifying Question Bank
 
Organized by round and topic. Pick the ones relevant to the project — don't ask all of these. Questions marked **[buttons]** work well with the `ask_user_input_v0` tool (small, natural option sets); the rest are open-ended and should be asked as plain chat text.
 
## Round 1 — Shape of the document
 
- **[buttons]** Is this replacing/improving something that already exists, or is it a new (greenfield) capability? → determines whether Current State / Future State sections are needed.
- **[buttons]** How formal does this need to be — a full sign-off-ready BRD (document control, approvers, distribution list) or a lighter internal version?
- **[buttons]** Do you have a house priority scheme (MoSCoW / P0-P1-P2 / other), or should I default to MUST/SHOULD/COULD HAVE?
- **[buttons]** Should this include Non-Functional Requirements (performance, security, availability targets), or is that out of scope for this doc?
- What's the project called, and who's the sponsoring team or organization?
## Round 2 — Substance
 
- What business problem is this solving? What happens today that's costly, slow, error-prone, or missing entirely?
- Who are the key stakeholders — sponsor, technical owner, operations/support, compliance or risk (if relevant), and who will actually use or consume this?
- **[buttons]** Does the thing being built have distinct user roles with different permissions (e.g. admin vs. regular user), or is it single-role?
- What's explicitly in scope? What's explicitly out of scope — and if something's out of scope, is it covered by another project/document?
- What are the 3-6 headline business objectives — the outcomes that justify doing this at all?
- Are there other systems this connects to, calls, or is called by? (useful for an architecture/position table)
## Round 3 — Requirements detail
 
- Walk me through the actual requirements in your own words — I'll formalize them into ref-ID'd statements with business justification afterward.
- For each requirement area: what's the business reason it matters? (if not obvious, tie back to the problem statement)
- **[buttons]** For NFRs (if included): does this need specific performance, uptime, or security targets, or should I draft reasonable defaults for you to adjust?
- Are there known risks that could sink approval or cause problems later? (security, compliance, vendor dependency, operational disruption)
- What does this depend on that's outside this project's control (other systems going live, vendor APIs, regulatory approval)?
- How will you know this was successfully delivered — what are the concrete acceptance criteria?
## Round 4 — Loose ends (only if needed)
 
- Are there specific approver names/roles I should list, or should I use placeholders for now?
- Is there a related document set (architecture overview, PRD, other BRDs) this should reference in the Appendices?
- Any regulatory or legal framework this operates under that should be named explicitly (industry-specific — e.g. financial services, healthcare, data protection law)?
- Anything from an uploaded file that seemed important but I should double check I understood correctly?
## Handling "I don't know" / "you decide"
 
Don't stall. Use a bracketed placeholder consistent with the rest of the document (`[Name]`, `[TBD]`, `[Confirm with Legal]`) and move on. Flag placeholders in your final delivery message so the user has a clear punch-list of what to fill in before circulating the document.