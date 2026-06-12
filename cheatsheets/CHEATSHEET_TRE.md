# tre — Automate Protocol

**AI works AMONG systems.** Automation with judgment, memory, and human approval points.

---

## Status: Coming Soon

tre is in active development. The core philosophy is defined below, but the protocol and extensions are not yet available. Watch the [protocol-tre repo](https://github.com/marekgorski/protocol-tre) for launch updates.

---

## When To Use tre

You have workflows running between systems. You want AI judgment at key decision points, not just blind automation.

| Good Fit | Not The Right Fit |
|----------|-------------------|
| Ticket triage and routing | Building a product |
| Deployment quality gates | Personal task tracking |
| Compliance approval workflows | Trip planning |
| Customer sentiment routing | One-time projects |

---

## The Problem tre Solves

Traditional automation (Make.com, Zapier, n8n) is powerful but brittle:

| Traditional Automation | tre Automation |
|------------------------|----------------|
| If trigger, then action | If trigger, then check, then maybe action, then verify |
| No judgment | AI evaluates context before acting |
| No memory | DECISIONS.md remembers past approvals |
| Same mistakes repeat | Learns from each run |
| Humans start from zero when it fails | Handoff context preserved |

---

## How tre Works

```
Traditional:
Trigger → Action → Action → Done
         (no gates, no judgment)

tre:
Trigger → AI Check → Action → AI Review → Human Approval → Done
              ↓                   ↓
         DECISIONS.md        PROGRESS.md
         (learned rules)     (audit trail)
```

**The insight:** Automation needs memory too.

When AI checks a trigger, it reads DECISIONS.md to know what's been approved before. When it reviews output, it logs to PROGRESS.md. When it escalates, TODO.md captures what needs human decision.

---

## Planned Extensions

| Extension | Mode | Use Case | Status |
|-----------|------|----------|--------|
| **qa** | Quality Assurance | Test automation, deployment gates, regression checks | Planned |
| **rm** | Risk Management | Compliance checks, approval chains, audit trails | Planned |
| **cs** | Customer Success | Ticket triage, escalation rules, sentiment routing | Planned |

---

## Core Files (Same Philosophy)

```
my-automation/
├── CLAUDE.md           # Protocol + automation reference
├── DECISIONS.md        # Approved patterns, rejection rules
├── TODO.md             # Pending human decisions
├── PROGRESS.md         # Run-by-run audit log
├── CONSTRAINTS.md      # Hard rules automation must follow
└── TASKS/              # Human-only tasks (file-per-task)
```

---

## Quality Gates

tre adds judgment points to automation:

### Pre-Action Gate
Before executing, AI asks:
- Does this match an approved pattern? (Check DECISIONS.md)
- Does it violate any constraints? (Check CONSTRAINTS.md)
- Is there precedent for this case?

### Post-Action Gate
After executing, AI asks:
- Did the output match expectations?
- Should this be logged for future reference?
- Does human need to review?

### Escalation Gate
When uncertain, AI:
- Prepares context (what happened, what it recommends)
- Creates task file in TASKS/ or adds to TODO.md for human decision
- Waits for approval before continuing
- Logs the decision so similar cases don't need re-approval

---

## Human Approval Points

tre makes escalation cheap:

1. **AI prepares** — What happened, what options exist, what it recommends
2. **Human decides** — Approve, reject, or modify
3. **AI logs** — Decision goes to DECISIONS.md
4. **System learns** — Similar cases handled automatically next time

**Goal:** Full autonomy for routine cases. Humans only see edge cases.

---

## Example: Ticket Triage (tre/cs)

```
Incoming Ticket
    ↓
AI reads ticket content
    ↓
Check DECISIONS.md: Similar tickets routed where before?
    ├── Pattern found → Route automatically
    └── No pattern
         ↓
    Check CONSTRAINTS.md: Any hard routing rules?
         ├── Rule matches → Apply rule
         └── No match
              ↓
         Escalate to human
              ↓
         Human decides routing
              ↓
         Log to DECISIONS.md: "Tickets about X go to Team Y"
              ↓
         Next similar ticket: Handled automatically
```

---

## Example: Deployment Gate (tre/qa)

```
PR merged to main
    ↓
AI runs test suite
    ↓
Check results against CONSTRAINTS.md
    ├── All green → Proceed to deploy
    └── Failures detected
         ↓
    Compare to known flaky tests (DECISIONS.md)
         ├── Known flaky → Log and proceed
         └── New failure
              ↓
         Block deploy
              ↓
         Add to TODO.md for engineer review
              ↓
         Engineer fixes or marks as flaky
              ↓
         Decision logged for next time
```

---

## When to Use tre vs duo

| Scenario | Protocol | Why |
|----------|----------|-----|
| Building a product | **duo** | Human-AI collaboration, interactive |
| Running a pipeline | **tre** | System-AI integration, automated |
| Writing docs | **uno** | Simple delegation |

**The distinction:**
- duo: AI works WITH you (you're there, iterating together)
- tre: AI works AMONG systems (you're not there, AI handles routine cases)

---

## Philosophy

### Why Files Work for Automation

Automation without memory makes the same mistakes forever.

When you log what failed in a file, the next run knows to check for it. When you track what got approved, similar cases don't need re-approval. When you document edge cases, the system handles them next time.

**Same files, same philosophy, different application.**

### Why Quality Gates?

Make.com thinking: "If this, then that."
tre thinking: "If this, then evaluate, then maybe that, then verify."

The extra steps aren't overhead — they're where judgment lives.

### Progressive Autonomy

Day 1: AI escalates most cases
Week 2: AI handles routine, escalates edge cases
Month 2: AI handles almost everything, humans see only truly novel situations

Each decision teaches the system. The more you use it, the smarter it gets.

---

## Getting Started

tre is in active development. If you're working on:

- Make.com / Zapier / n8n with AI judgment
- Quality assurance automation
- Compliance or approval workflows
- Customer support automation

Watch the [protocol-tre repo](https://github.com/marekgorski/protocol-tre) for updates.

---

*tre Protocol — Coming Soon*
