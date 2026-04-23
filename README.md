# Prompt Forge

> Turn messy ideas into production-ready AI prompts.

Prompt Forge is a **Claude Code skill** that transforms unstructured, plain-English requests into structured, executable prompts for any AI — Claude, ChatGPT, Codex, Gemini, and beyond.

---

## What It Does

You type a half-formed idea like:

> *"every morning i want an email summary of my github notifications"*

Prompt Forge analyzes it, classifies the intent, and outputs a complete structured prompt with:
- Clear role and goal
- Step-by-step instructions
- Tool specifications (MCP, APIs)
- Error handling
- Success criteria
- Platform-specific hardening

---

## Installation

### For Claude Code

1. Clone this repo:
```bash
git clone https://github.com/Srimi1/Prompt-Forge.git
cd Prompt-Forge
```

2. Open Claude Code in this directory:
```bash
claude
```

3. Use the skill:
```
/forge every morning check my github prs and send me a summary email
```

---

## How It Works

```
Listen    →  You give messy English
Analyze   →  Extract goal, platform, trigger, constraints
Classify  →  Schedule / Automation / Agent / Analysis / Codegen / General
Build     →  Generate structured prompt using the unified template
Harden    →  Add platform tweaks (Claude, Codex, Generic)
Validate  →  Check 6 quality gates
Deliver   →  Output prompt + metadata + offer to save
```

---

## The Unified Template

Every prompt is built using this 11-section template:

```markdown
## ROLE
## GOAL
## CONTEXT
## TRIGGER / SCHEDULE
## INPUTS
## INSTRUCTIONS
## TOOLS
## CONSTRAINTS
## OUTPUT FORMAT
## ERROR HANDLING
## SUCCESS CRITERIA
```

For simple tasks, optional sections are omitted. For automations and schedules, every section is filled.

---

## Supported Platforms

| Platform | Hardening Applied |
|----------|------------------|
| **Claude** | XML tags, Scheduled Runs, MCP tools, Artifacts, Computer Use safety |
| **Codex** | Workspace context, test commands, shell constraints, `.codex/instructions.md` format |
| **ChatGPT / Gemini** | Self-contained markdown, few-shot examples |
| **Generic** | Universal template, works on any LLM |

---

## Project Structure

```
.
├── README.md
├── LICENSE
└── .claude/
    ├── skills/
    │   └── prompt-forge/
    │       └── SKILL.md          ← Core skill logic
    └── commands/
        └── forge.md              ← /forge slash command
```

---

## Example

**Input:**
> "i want something that summarizes long emails into 3 bullet points"

**Output:**
```markdown
## ROLE
Expert Executive Assistant specializing in concise business communication.

## GOAL
Distill long emails into 3 actionable bullet points.

## CONTEXT
The user receives lengthy emails and needs rapid triage without reading everything.

## INPUTS
Full email body as plain text.

## INSTRUCTIONS
1. Read the entire email.
2. Extract the main point.
3. Identify any required action.
4. Note the deadline or urgency.

## CONSTRAINTS
- Do NOT exceed 3 bullets.
- Do NOT invent information not present in the email.
- Always preserve the sender's original intent.

## OUTPUT FORMAT
**Summary**
- Main point: {one sentence}
- Action needed: {specific task or "None"}
- Urgency: {deadline or "No deadline"}

## ERROR HANDLING
If the email is empty or unreadable, return: "Unable to summarize — invalid input."

## SUCCESS CRITERIA
User can triage the email in under 5 seconds.
```

---

## Origin

Prompt Forge merges two skill architectures:
- **Prompt-Forge** — Deep template rigor, platform-specific hardening, validation gates
- **Universal Prompt Architect (UPA)** — Friendly UX, simple workflow, iteration loop

The result: a single skill that is both approachable and production-grade.

---

## License

MIT
