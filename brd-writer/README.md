# BRD Writer

A skill that helps draft formal Business Requirements Documents (BRDs) by combining existing project context (uploaded notes, transcripts, prior docs) with a structured interview, then producing a polished, sign-off-ready document.

See [SKILL.md](SKILL.md) for the full workflow, and [references/](references/) for the BRD template and clarifying question bank used during drafting.

## What's included

| File | Purpose |
|---|---|
| [SKILL.md](SKILL.md) | Skill instructions and workflow (the file agents read) |
| [references/brd_template.md](references/brd_template.md) | Adaptive BRD section structure and drafting guidance |
| [references/clarifying_questions.md](references/clarifying_questions.md) | Question bank used to fill gaps in the requirements |
| [brd-writer.skill](brd-writer.skill) | Packaged bundle of the skill (zip), for tools that install skills from a single file |

## Installation

Choose whichever method matches the tool you use.

### Option 1: Claude Code

Copy (or symlink) this folder into your skills directory so Claude Code can discover it.

**Project-level** (available only in this repository):

```bash
mkdir -p .claude/skills
cp -r brd-writer .claude/skills/brd-writer
```

**Personal-level** (available across all your projects):

```bash
mkdir -p ~/.claude/skills
cp -r brd-writer ~/.claude/skills/brd-writer
```

Restart Claude Code (or start a new session) and the skill will be picked up automatically based on its `description` frontmatter.

### Option 2: Claude.ai / Claude Desktop

1. Go to **Settings → Capabilities → Skills** (or the equivalent Skills upload area).
2. Upload the packaged [brd-writer.skill](brd-writer.skill) file directly — no need to unzip it.
3. Enable the skill for your workspace/project if prompted.

### Option 3: Other agent-skill-compatible tools

Many tools (Cursor, other Agent Skills-compatible clients) follow the same open `.agents/skills/<name>/SKILL.md` convention. Copy the folder into that location for the tool you're using:

```bash
mkdir -p .agents/skills
cp -r brd-writer .agents/skills/brd-writer
```

Consult your tool's documentation if it expects a different path.

## Usage

Just ask for a BRD in natural language (e.g., "write a BRD for X", "help me document business requirements for Y"). The skill will:

1. Read any context you've already provided (uploads, prior conversation).
2. Ask clarifying questions to fill gaps (scope, stakeholders, requirements, priorities, NFRs, risks).
3. Confirm whether you want the output as `.docx` or Markdown.
4. Draft the full document and flag any placeholders that still need your input before it's ready for sign-off.
