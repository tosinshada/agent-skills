---
name: brd-writer
description: Use this skill whenever the user wants to create, draft, or write a Business Requirements Document (BRD) — for a new system, product, service, integration, or process change, in any industry. Trigger on phrases like "write a BRD", "business requirements document", "requirements doc for [project]", "help me document the business requirements for X", or when the user uploads project notes, meeting transcripts, emails, or a rough spec and asks for it to be turned into a formal requirements document. Also trigger if the user asks to update, expand, or restructure an existing BRD, or asks for a "business case" or "requirements pack" that includes stakeholder analysis, scope, current/future state, and prioritized requirements. Do not use for PRDs/technical specs with no business framing (see the docx skill instead for generic Word documents), or for simple one-page requirement lists that don't need the full BRD structure — ask the user which they want if it's ambiguous.
---
 
# BRD Writer
 
Writes formal Business Requirements Documents by combining whatever context the user already has (uploaded notes, transcripts, existing docs, rough descriptions) with a structured interview to fill the gaps, then producing a polished document modeled on professional BRD conventions.
 
A BRD is a business-facing artifact, not a technical spec. Its job is to get non-technical stakeholders (sponsors, compliance, ops, finance) to a shared, sign-off-ready understanding of *why* something is being built and *what* it must do — before anyone designs *how*. Keep that lens throughout: business justification for every requirement, plain language over jargon, and enough structure that an approver can skim it and know what they're approving.
 
## Workflow
 
### Step 1: Gather existing context first
 
Before asking the user anything, check what's already available:
 
- **Uploaded files** — read every file in `/mnt/user-data/uploads` (notes, transcripts, emails, existing PRDs, prior BRDs, Slack exports, whatever they gave you). Use the file-reading skill's routing if the content isn't already visible in context.
- **Conversation history** — the user may have already described the project, problem, or requirements earlier in the chat.
Extract everything usable: project name, problem being solved, stakeholders named, systems mentioned, any requirements already implied. Don't ask the user to repeat information you can already infer. If uploads are large or numerous, skim for the sections in `references/brd_template.md` rather than reading exhaustively.
 
### Step 2: Scope the document
 
Figure out roughly what kind of BRD this is before interviewing in depth — a payment API integration needs different sections emphasized than an internal process change or a new customer-facing product. Read `references/brd_template.md` now if you haven't yet; it has the full adaptive section list and guidance on when to include, shrink, or skip each one.
 
Form a working hypothesis of:
- What's in scope / out of scope, roughly
- Who the likely stakeholder types are (sponsor, technical owner, ops, compliance/risk, end users, external parties)
- Whether this is greenfield (no current state) or replacing/improving an existing process (needs as-is/to-be)
- Whether regulatory, security, or compliance framing matters for this domain
This hypothesis drives which clarifying questions are actually worth asking — don't ask about AML/CFT controls for an internal HR tool, don't ask about retail footfall for a backend API.
 
### Step 3: Ask clarifying questions
 
This is the core value of the skill — a BRD is only as good as the business context behind it, and that context usually lives in the requester's head, not in a file. Use `references/clarifying_questions.md` as a bank of candidate questions organized by BRD section. Don't dump all of them on the user.
 
**How to ask:**
- Prefer the interactive button tool (`ask_user_input_v0`) for questions with a natural small set of options (priority scheme, whether NFRs are needed, in/out-of-scope calls, document formality level). Batch 2-3 related questions per call, as the tool supports.
- For open-ended questions (problem statement, business objectives, requirement details) that don't fit buttons, just ask directly in chat as plain text — don't force these into button form.
- Go in 2-3 rounds, not one giant interrogation. Start with the shape of the document (scope, audience, formality), then move to substance (objectives, requirements, stakeholders), then details (NFRs, risks, priorities). Skip a round entirely if Step 1 already answered it.
- If the user says "just use your best judgment" or seems to want to move fast, stop interviewing and fill gaps with clearly-marked placeholders (see below) rather than blocking on more questions.
**What to nail down before drafting:**
1. Project name, sponsoring organization, one-line purpose
2. The business problem and its impact (why does this need to exist)
3. In scope / out of scope boundaries
4. Key stakeholders and their roles (names can be placeholders like `[Name]` if unknown — role and organization matter more)
5. Current state, if this replaces or changes an existing process (skip entirely for greenfield builds)
6. The actual requirements — get these as close to the user's own words as possible, then formalize
7. Priority scheme — most BRDs use MUST/SHOULD/COULD HAVE (MoSCoW-style); confirm or offer alternatives
8. Whether non-functional requirements (performance, security, availability) matter here, and roughly what they need to be
9. Known risks, dependencies, and what "done" looks like (success criteria)
Where the user genuinely doesn't know an answer (e.g., specific approver names, exact SLA numbers), don't block — use a clear placeholder like `[Name]`, `[TBD]`, or `[Confirm with Compliance]` and move on. A BRD draft with a few flagged gaps that gets reviewed is more useful than a stalled conversation.
 
### Step 4: Confirm output format
 
Ask the user whether they want the final document as a **Word document (.docx)** — formatted, with the cover page, styled tables, and headers/footers, ready to circulate for sign-off — or as a **Markdown file** — faster, plain, easy to paste elsewhere or version-control. Default assumption if they don't have a preference: docx, since BRDs are typically circulated for formal review and approval.
 
### Step 5: Draft the document
 
Follow the structure in `references/brd_template.md`, adapting section depth to what's actually relevant (per Step 2). Every business requirement needs: a reference ID, the requirement itself in plain business language (not implementation detail), the business justification (why it matters), and a priority. Don't write requirements as technical specs — "the system must send a confirmation email within 2 minutes of payment" is a business requirement; "call SendGrid's API with template ID X" is not.
 
**If producing .docx:** read `/mnt/skills/public/docx/SKILL.md` now and follow its guidance — build with docx-js, use real tables (not markdown tables) with the dual-width gotcha in mind, use `HeadingLevel.*` for anything that should appear in a table of contents, and render the result to check it before delivering.
 
**If producing Markdown:** use standard Markdown tables and headers; no need to invoke the docx skill.
 
Write the whole draft in one pass rather than section-by-section back-and-forth, unless the document is unusually large or the user asks to review section by section.
 
### Step 6: Deliver and offer a pass
 
Save the file to `/mnt/user-data/outputs` and present it. Briefly flag anything you filled with a placeholder so the user knows what still needs their input before this goes to reviewers. Offer to revise specific sections rather than assuming the first draft is final — BRDs commonly go through a couple of rounds before sign-off.
 
## Notes on style
 
- Business requirements are numbered with a short domain prefix the user can help pick (e.g., `BR-AUTH-1.1`, `BR-PAY-2.3`) — group related requirements under a subsection heading rather than one long flat list.
- Keep the "Business Justification" column honest and specific — "improves user experience" is weak; "reduces manual reconciliation from 3 days to real-time, per Section 7 pain point #3" is strong, and ties the requirement back to the problem statement.
- Executive summary and problem statement should be readable by someone with zero technical background; requirements tables can be more precise/technical since implementers will read those closely too.
- Don't invent stakeholder names, specific dates, or numbers the user hasn't given you — use placeholders. Do feel free to draft the business objectives, risks, and success criteria in full prose once the user has given you the underlying substance; that synthesis is the value you're adding.