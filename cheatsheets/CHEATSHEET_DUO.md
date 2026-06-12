# duo — Collaborate Protocol

**AI works WITH you.** You design together. AI implements. You guide.

---

## When To Use duo

You're building something with code. You want AI as a collaborator, not just a task-runner.

| Good Fit | Not The Right Fit |
|----------|-------------------|
| Building a web app | Planning a trip |
| Refactoring a codebase | Tracking onboarding |
| Creating a product from scratch | Maintaining documentation |
| Prototyping and deploying | Simple delegation |

---

## The Key Insight: Two Roles

duo separates planning from implementation:

| Role | Purpose | Context Loaded | Token Budget |
|------|---------|----------------|--------------|
| **Architect** | Design, strategy, planning | Full (~30KB) | ~15% |
| **Builder** | Write code, execute tasks | Lean (~12KB) | ~5% |

**Why separate?**
- Architect sees the big picture (PRFAQ, DECISIONS, CONSTRAINTS)
- Builder stays focused (just CLAUDE.md, TODO.md, TASKS/)
- Prevents scope creep during implementation
- Mirrors how humans work: plan first, then execute

---

## Core Files

```
my-project/
├── CLAUDE.md           # Technical reference (ground truth)
├── PRFAQ.md            # Product vision (Press Release / FAQ)
├── TODO.md             # Prioritized task list
├── PROGRESS.md         # Session-by-session log
├── DECISIONS.md        # Architecture Decision Records (prevents repeated mistakes)
├── CONSTRAINTS.md      # Principles, rejected approaches (stops hallucinations)
├── WORKFLOW.md         # Development process
├── ROLE_PROTOCOL.md    # AI workflow commands
├── TASKS/              # Human-only tasks (file-per-task)
└── README.md           # User-facing docs
```

### Why These Files Matter

These files aren't just documentation—they're **hallucination prevention**:

- **CLAUDE.md**: Ground truth for your tech stack. Without it, AI guesses (often wrong).
- **DECISIONS.md**: "Why we chose X over Y." Stops AI from re-suggesting rejected approaches.
- **CONSTRAINTS.md**: "Never do X." Hard boundaries that prevent drift.

Each file anchors AI to facts, reducing assumptions and increasing consistency across sessions.

---

## Commands

### Scope Modifiers

| Command | What It Does |
|---------|--------------|
| `..architect` | Enter planning scope (full context) |
| `..builder` | Enter implementation scope (lean context) |

### Architect Commands

| Command | What It Does |
|---------|--------------|
| `..start` | Load context, show priorities, flag stale tasks |
| `..make` | Design a feature, write specs with AC |
| `..hygiene` | Archive old content |
| `..exit` | Fossilize context for handoff *(automatic in v1.0)* |

### Builder Commands

| Command | What It Does |
|---------|--------------|
| *(build)* | Execute top task from TODO.md *(automatic in builder scope)* |
| *(save)* | Verify AC, update docs, commit *(automatic after every interaction)* |
| `..recover` | Emergency recovery from crash |

---

## Workflow

### Design Flow

```
..architect → ..start → ..make → ..exit
```

1. Enter Architect mode
2. Load context, see priorities
3. Design feature, AI writes specs to files
4. Exit with context fossilized

### Build Flow

```
..builder → ..go → ..end
```

1. Enter Builder mode
2. Execute top task
3. Verify, update docs, commit

### Maintenance Flow

```
..architect → ..hygiene → ..exit
```

1. Enter Architect mode
2. Archive old content
3. Exit clean

---

## Task Ownership

Same as uno — location encodes ownership:

| Location | Owner | Purpose |
|----------|-------|---------|
| **TODO.md** | AI | Tasks AI works on |
| **TASKS/** | You | Tasks only a human can do (account setup, approvals, decisions) |

---

## TODO Format

Every task needs acceptance criteria:

```markdown
- [ ] Implement user authentication
  - AC: Login returns JWT token
  - AC: Logout invalidates session
  - AC: Tests pass
```

Human tasks go in TASKS/ as file-per-task briefs:

```markdown
# TASKS/record-demo-video.md
- AC: 2-min walkthrough uploaded to YouTube
- AC: URL shared in TODO.md when done
- Blocks: VideoWalkthrough.tsx
```

---

## Quick Start

### 1. Clone the template

```bash
git clone https://github.com/marekgorski/protocol-duo.git my-app
cd my-app
rm -rf .git && git init
```

### 2. Open with Claude

Claude sees `[PLACEHOLDER]` markers and runs onboarding:
1. Asks 5 discovery questions (what, who, problem, success, constraints)
2. Reflects understanding back
3. Populates PRFAQ, TODO, DECISIONS, etc.
4. You're ready to build

### 3. Start building

```
..architect         → Enter planning mode
..start             → See priorities
..make "Add login"  → Design the feature
..exit              → Save context

..builder           → Enter build mode
..go                → Execute top task
..end               → Verify and commit
```

---

## Safety Features

### Context Drift Check

Before executing, Builder checks:
- `git status` — Any uncommitted changes?
- `git pull` — Any remote changes?

If drift detected: **STOP.** Refresh context first.

### Verification at ..end

Builder doesn't just mark tasks done. It:
1. Checks each acceptance criterion explicitly
2. If AC not met: Notes what's missing, does NOT mark complete
3. If AC met: Marks complete, updates PROGRESS.md

**Transparency in verification:** Builder should explicitly state confidence levels and assumptions. Don't hedge with "This seems to work"—say "AC met: Login returns JWT token (tested)" or "AC unclear: No test written, marking incomplete." See CHEATSHEET_101.md "Transparency as Collaboration Principle" for details.

---

## Multi-Tool Handoffs

When switching between tools (Claude Code → Figma Make → Cursor):

**Problem:** Each tool has its own copy of files. They don't sync automatically.

**Solution:** AI prepares a handoff package:

```
Files Changed This Session
| File | What Changed |
|------|--------------|
| DECISIONS.md | Added DEC-023 |
| TODO.md | Added 3 tasks |

For Figma Make:
1. Open each file in code view
2. Paste updated content (below)
3. Prompt: "Read DECISIONS.md and TODO.md to get new context."

[Content to paste...]
```

---

## Anti-Patterns

| Don't Do This | Do This Instead |
|---------------|-----------------|
| Mix roles (plan while building) | Architect designs, Builder implements |
| Skip `..end` | Always verify and close sessions |
| Ignore context drift | Check git status before building |
| Giant PROGRESS.md | Run `..hygiene` monthly |
| TODO without AC | Every task needs testable criteria |

---

## Recovery

If something breaks:

**Level 1: Git Reset**
```bash
git log --oneline -10
git reset --hard [last-good-commit]
```

**Level 2: Full Reset**
```bash
rm -rf node_modules
npm install
npm run dev
```

After recovery: Run `..builder` to resume.

---

## Example Session

```
You: ..architect
AI: 🏗️ ARCHITECT MODE ACTIVE. Ready to plan.

You: ..start
AI: Context loaded.
    Top priority: Add user settings page
    - AC: Settings accessible from nav
    - AC: Theme toggle works
    Stale human tasks: TASKS/record-demo.md (10 days)

You: ..make "Add dark mode toggle"
AI: ✅ Spec written.
    📄 DECISIONS.md: ADR-015 added
    📋 TODO.md: 3 tasks added
    Builder can run ..go

You: ..builder
AI: 🔨 BUILDER MODE ACTIVE. Ready to build.

You: ..go
AI: 🎯 Building: Add theme context provider
    [implements...]
    ✅ Task complete. 2 commits made.
    Run ..end to verify.

You: ..end
AI: ✅ Session closed.
    Completed: Theme context provider (AC verified)
    Next: Add toggle component
    Changes pushed.
```

---

*duo Protocol v1.3 — May 2026 | For v1.3 (Structural Discipline), see the [full protocol](https://kayg.ee/protocol) and [kayg.ee/learn/structural-discipline](https://kayg.ee/learn/structural-discipline)*
