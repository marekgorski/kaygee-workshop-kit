# KayGee Workshop Kit

## What This Is

A DIY workshop kit that teaches anyone to compound their efforts with AI. The kit serves **both single players (solo learners) and multiplayer groups (facilitated workshops)** with the same materials.

**The kit is generative, not pre-built.** It contains build files (like `BUILD_GYM.md`) that, when run with Claude Code, generate complete starter projects with protocol files. See Decision 12 in DECISIONS.md.

## The Core Concept: Sessions That Compound

> AI has no memory. But YOU can give it one.

**The Compound Effect:** You invest a small percentage of your context window in structured markdown files. In return, every session builds on the last instead of starting from scratch.

Files persist context in Git so your AI never forgets your decisions, patterns, or constraints. Without that trade, you spend 30% of every session re-explaining. With it, each session compounds.

### Transparency as Default

AI should explicitly state confidence levels, assumptions, when it doesn't have access, and what needs verification. Vague hedging wastes time. Transparent uncertainty speeds collaboration.

See cheatsheets/CHEATSHEET_101.md "Transparency as Collaboration Principle" section for full details.

## Workshop Structure

**Pedagogy:** Problem/Solution — each session introduces discomfort, then resolves with a tool.

**Throughline:** Gym app case study (Sessions 1-4), then pivot to own idea (Sessions 5-6).

| Session | Problem | Solution | Output |
|---------|---------|----------|--------|
| 1: Protocol | 95% time re-explaining | AI reads context files | Working local app |
| 2: Git | Can't track changes | GitHub | Code versioned |
| 3: Deploy | Can't share localhost | Vercel | Live URL |
| 4: Data | Nothing persists | Supabase | Data saved |
| 5: Recovering from Failures | Prototype ≠ Figma | Figma Make + own idea | Own project started |
| 6: Building Shared Context | Solo isn't enough | Protocol for collaboration | Hackathon-ready |

**Pedagogical Principles:**
1. Pain before relief
2. Non-determinism framing (Session 1)
3. Progressive complexity (each session adds one layer)
4. Rails then freedom (gym app → own idea)
5. Hackathon starts at hackathon (workshop teaches skills)

## Kit Architecture

```
kaygee-workshop-kit/
├── build-this/              ← Generator files (the core of the kit)
│   └── BUILD_GYM.md         ← Run with Claude Code to generate gym app
├── sessions/                ← Session guides (for instructors OR self-guided)
│   └── SESSION_01-06.md
├── facilitator/             ← Facilitator materials
│   ├── FACILITATOR_GUIDE.md  ← Pedagogy and principles
│   ├── FACILITATOR_RUNBOOK.md ← Emergency protocols
│   ├── WORKSHOP_PRACTICE_GUIDE.md ← How to practice before running
│   └── DAY_SCHEDULE.md       ← Minute-by-minute timeline
├── cheatsheets/             ← Reference material for participants
│   └── CHEATSHEET_*.md
├── PREREQUISITES.md         ← Setup checklist for learners
├── DECISIONS.md             ← Pedagogical decisions
├── TODO.md                  ← Improvements backlog
└── PROGRESS.md              ← Workshop run log
```

**Key principle:** The kit has no protocol files for learners to clone. BUILD files generate them at runtime, customized to the project being built.

## Audience

The same materials serve two audiences:

| Audience | How They Use It |
|----------|-----------------|
| **Solo learner** | Copies BUILD_GYM.md, runs it, follows session guides solo |
| **Workshop group** | Facilitator uses session guides, participants use BUILD_GYM.md |

## Graduation

The kit teaches a **simplified subset** of the full duo protocol — enough to build and ship. When learners hit limitations (token limits, context drift), they're ready for [protocol-duo](https://github.com/marekgorski/protocol-duo).

## Other Ways to Learn

This kit is free for everyone. For guided options, see [kayg.ee/workshops](https://kayg.ee/workshops).
