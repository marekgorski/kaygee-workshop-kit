# uno — Delegate Protocol

**AI works FOR you.** You define WHAT, AI handles HOW.

---

## When To Use uno

You have work that needs doing, but it's not code. You want to delegate clearly and track progress.

| Good Fit | Not The Right Fit |
|----------|-------------------|
| Planning a trip | Building a web app |
| Tracking a 90-day onboarding | Writing production code |
| Maintaining documentation | Automating workflows |
| Managing personal projects | Collaborative coding |

---

## Pick Your Extension

When you start a uno project, AI asks which extension fits:

| Extension | Best For | Creates |
|-----------|----------|---------|
| **ea** | Work projects with deadlines, stakeholders, learning curve | UPDATES.md, GLOSSARY.md, KNOWLEDGE.md, SYSTEMS.md |
| **pa** | Personal logistics — trips, events, moves, finances | ITINERARY.md, BOOKINGS.md, BUDGET.md, NOTES.md |
| **km** | Documentation, archives, recurring tasks | LOG.md, PLANNED.md |
| **none** | Simple delegation, no domain tracking | (core files only) |

---

## Personalization Layer

After picking your extension, AI asks **persona questions** to learn how you think and what you care about. This creates `PERSONA.md` — your AI's training data.

### What Persona Captures

| Aspect | What AI Learns | How It's Used |
|--------|----------------|---------------|
| **Decision style** | How you prefer choices presented | Structures recommendations |
| **Signal watch** | What to always surface | Filters briefings |
| **Noise filter** | What to skip or minimize | Reduces clutter |
| **Interests/constraints** | What matters to you | Shapes suggestions |

### Example: EA Persona

```markdown
## Decision Style
Options with trade-offs. Always include "do nothing" option.

## Signal Watch
- Budget concerns
- Anything from CEO
- Timeline slips on critical path

## Noise Filter
- Technical implementation details
- Historical background
```

### Example: PA Persona

```markdown
## Priority Signals
1. Local/authentic experience
2. Value for money
3. Avoiding crowds

## Constraints
- Vegetarian options required
- Nothing before 9am
- Budget: $150-250/night

## Interests
Local food markets, street art, live music, coastal walks

## Avoid
Chain restaurants, tourist traps, hop-on hop-off tours
```

See `CHEATSHEET_PERSONAS.md` for full persona setup details.

---

## Core Files

Every uno project has these:

```
my-project/
├── CLAUDE.md      # Protocol + project reference (ground truth)
├── PERSONA.md     # Your preferences and signals (filters hallucinations)
├── TODO.md        # Tasks with acceptance criteria
├── PROGRESS.md    # Session log
├── TASKS/         # Human-only tasks (file-per-task)
├── README.md      # Project description
└── _archive/      # Old entries
```

Plus extension-specific files based on your choice.

### Why These Files Prevent Hallucinations

- **CLAUDE.md**: Facts about your project. Without it, AI invents context.
- **PERSONA.md**: Your actual preferences. Stops AI from guessing what matters to you.
- **TODO.md with AC**: Testable criteria prevent "I think it's done" hallucinations.

When AI reads your files each session, it works from your truth—not assumptions.

---

## Commands

| Command | What It Does |
|---------|--------------|
| `..start` | Load context, apply persona filters, show personalized briefing |
| `..end` | Verify tasks complete, update docs, commit |
| `..hygiene` | Archive old entries when files get large |

---

## Task Ownership

Location encodes ownership — no markers needed:

| Location | Owner | Purpose |
|----------|-------|---------|
| **TODO.md** | AI | Tasks AI works on |
| **TASKS/** | You | Tasks only a human can do (account setup, approvals, decisions) |

AI tasks live in TODO.md. Human tasks live in TASKS/ as file-per-task briefs.

---

## TODO Format

Every task needs acceptance criteria (AC):

```markdown
BAD:
- [ ] Write intro section

GOOD:
- [ ] Write intro section
  - AC: Explains problem in <100 words
  - AC: Includes one concrete example
```

Without AC, "done" is meaningless. With AC, you can verify.

---

## Quick Start

### 1. Clone the template

```bash
git clone https://github.com/marekgorski/protocol-uno.git my-project
cd my-project
rm -rf .git && git init
```

### 2. Open with Claude

Claude sees `[PLACEHOLDER]` markers and runs onboarding:

**Phase 1: Extension**
1. Asks which extension (ea, pa, km, none)

**Phase 2: Discovery**
2. Asks 5 project questions (what, who, problem, success, constraints)

**Phase 3: Persona** (NEW)
3. Asks persona questions based on extension
4. Creates PERSONA.md with your preferences

**Phase 4: Setup**
5. Populates your files
6. You're ready to work

### 3. Use session commands

```
..start    → See personalized briefing
[do work]
..end      → Verify AC, update docs, commit
```

---

## Personalized Briefings

### Without Persona

```
## Daily Briefing

Here's what's happening...
[Generic summary of everything]
```

### With Persona (EA)

```
## Daily Briefing — Day 15/90

### Signals Detected
⚠️ Budget: Q2 spend tracking 15% over
⚠️ CEO: Mentioned project in all-hands (positive)

### Decisions Needed
| Option | Trade-off |
|--------|-----------|
| Approve overspend | Keeps timeline, budget pressure Q3 |
| Cut scope | Saves budget, feature delay |
| Do nothing | Compounds next week |

### Filtered Out (per your preferences)
- 3 technical updates (implementation details)
- Background context (you know this)
```

### With Persona (PA)

```
## Trip Briefing — Jan 15

### Matches Your Interests
🎵 The Lansdowne — Live music, local bands
📚 Gertrude & Alice — Independent bookshop café

### Filtered Out
- Sydney Opera House tour (tourist trap)
- Darling Harbour (chains, crowds)

### Constraints Check
✓ All have vegetarian options
✓ Nothing before 9am
✓ Within budget range
```

---

## Extension Briefings

### uno/ea — Executive Assistant

`..start` gives you a persona-filtered daily briefing:

```
## Daily Briefing — Day 15/90

**Status:** Onboarding | 75 days left | 3 meetings/week pace

### Signals Detected
[Items matching your Signal Watch list]

### Decisions Needed
[Structured per your Decision Style preference]

### This Week
| Day | Priority | Deliverable Due |
|-----|----------|------------------|

### Pace Check
- Meetings: 12/30 complete — need 2.4/week

### Filtered Out
[Items matching your Noise Filter]

### Today's #1 Priority
> [Single most important thing]
```

---

### uno/pa — Personal Assistant

`..start` gives you a persona-filtered trip briefing:

```
## Trip Briefing — Jan 15, 2026

**Timeline:** Leg 2 (Sydney) | 3 days until Melbourne

### Matches Your Interests
[Items matching your Interest tags]

### Coming Up (Next 7 Days)
| Date | Event | Status |
|------|-------|--------|

### Constraints Check
[Verification against your stated constraints]

### Filtered Out
[Items matching your Avoid tags]

### Today's Priority
> [Most important logistics task]
```

---

### uno/km — Knowledge Manager

`..start` checks documentation health with persona filtering:

```
## Documentation Check — Jan 15

### Priority Domains
[Filtered to your stated focus areas]

### Pending in LOG.md
- Items awaiting categorization

### Learning Queue
[Structured per your Learning Style preference]

### Stale Documentation
- Files not updated in 30+ days

### Today's Priority
> [Based on your depth preference]
```

---

## Persona Evolution

Your persona isn't frozen. Update it as you learn what works:

**Explicit:** Edit PERSONA.md directly

**Prompted:** AI may ask:
> "I noticed you've skipped museum recommendations 3 times.
> Should I add 'museums' to your Avoid list?"

---

## Handoff Protocol

### When AI finishes a task that needs your action

1. AI creates the deliverable (draft email, research doc, etc.)
2. AI creates task file in TASKS/ marked "Ready for You"
3. You review and execute when ready

### When you complete a human task

1. Mark complete in TASKS/ with output (URL, file path, decision)
2. AI picks it up on next `..start`
3. AI unblocks dependent tasks

---

## Anti-Patterns

| Don't Do This | Do This Instead |
|---------------|-----------------|
| TODO without AC | Always include testable acceptance criteria |
| Skip `..end` | Always close sessions properly |
| Let human tasks rot | Flag stale tasks in TASKS/, split if possible |
| Huge context files | Run `..hygiene` when files grow large |
| Ignore persona setup | Take 5 minutes to configure — it compounds |
| Never update persona | Refine as you learn what works |

---

## Example Projects

| Project | Extension | Persona Focus |
|---------|-----------|---------------|
| 90-day onboarding | ea | Stakeholder signals, decision options |
| Holiday trip planner | pa | Local experiences, dietary preferences, pacing |
| Team knowledge base | km | Domain focus, learning depth |

---

*uno Protocol v1.3 — May 2026 | For v1.3 (Structural Discipline), see the [full protocol](https://kayg.ee/protocol) and [kayg.ee/learn/structural-discipline](https://kayg.ee/learn/structural-discipline)*
