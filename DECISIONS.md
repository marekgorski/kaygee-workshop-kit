# Workshop Decisions

Pedagogical and technical decisions that shape how the workshop works. Reference these when making content changes.

---

## Decision 14: Session 1-2 Pedagogical Reframe — Mental Model Gap First

**Date:** January 19, 2026
**Status:** Active

**Context:** Observing how non-expert users actually approach AI coding workflows (browser AI tools → GitHub → Claude Code) revealed our workshop starts one step too advanced. We assume baseline comfort with local dev, terminal, Git. The real barrier isn't tooling—it's the mental model gap between "Google thinking" and "LLM thinking."

**The Problem We Missed:**

Users bring "Google thinking" to LLMs:
- Google: Type "dog" → Index match → Results
- Claude: Type "dog" → No index → "What about dogs?"
- **Gap**: Searching database ≠ talking to intelligence

Current Session 1 asks participants to accept 5 new concepts in 10 minutes (Git, clone, npm, localhost, Claude Code) before they experience the "aha" of Protocol files working.

**The Reframe:**

### Session 1: Initialize, Don't Clone

**Old approach:**
```bash
git clone gym-starter  # Assumes Git knowledge
npm install            # Assumes Node knowledge
npm run dev           # Assumes localhost understanding
```

**New approach:**
```bash
mkdir my-gym && cd my-gym && claude  # Empty folder
# Claude detects no .md files, triggers onboarding Q&A
# Generates personalized gym app + Protocol files
# Output: Working MVP in 5 minutes, no prerequisites
```

**Key shifts:**
1. **Mental model first**: Chapter 0 explains Google vs Claude (4 slides, Anthropic-style)
2. **.md files = "your personal index"**: Not "context files" (too abstract)
3. **Personalized MVP**: Claude asks "Cardio or weights?" → Generates relevant app
4. **Git moved to Session 2**: Decouple complexity, progressive layers

### Session 2: "Add the Undo Button"

**The catchphrase:** "Add the Undo Button" (not "Learn Git")

**The hook:**
> "Your app works. What if you break it? Git = undo button for your entire project."

**The flow:**
1. **Demo breaking moment**: Facilitator breaks working app, fumbles to fix
2. **Git as undo**: `git reset --hard` → App restored instantly
3. **Everyone tries**: Safe break → Undo → Check-in
4. **Secondary reveal**: "Git history = backup of your .md files (TODO, DECISIONS, PROGRESS)"
5. **Push to GitHub**: "Your undo button now works from anywhere"

### Chapter 0: The Language Barrier (New Content)

4 slides, Anthropic onboarding style:

**Slide 1: How Google Works**
- Search bar + index + results
- "Google built an index. You type 'dog,' it finds matching pages."

**Slide 2: How Claude Works (Without Context)**
- Chat bubble + "???" + confused face
- "Claude has no index. 'Dog' could mean anything."

**Slide 3: .md Files = Your Index**
- File icon + brain icon
- "Protocol files tell Claude what your project is. Like Google's index, but for YOUR work."

**Slide 4: The Cost (Token Awareness)**
- Token meter (like gas gauge)
- ".md files cost tokens. But building your index upfront saves time later."

---

## Decision 15: Transparency as Core Collaboration Principle

**Date:** January 19, 2026
**Status:** Active

**Context:** A recurring pattern across chat assistants: a model that can't see an attached image hedges with vague questions instead of transparently stating "I don't have access to the image contents." This is a tooling + handoff failure that wastes time and breaks trust.

**Core Principle:** "Transparency as default, not lies to make us feel better" — we optimize for clear collaboration.

### The Problem: Polite Uncertainty

AI models are trained to be helpful. When uncertain, they hedge instead of saying "I don't know."

| Bad Transparency | Why It's Bad | Good Transparency |
|------------------|--------------|-------------------|
| "I'll add error handling." | Vague about what/where/why | "I'll add try-catch around the API call. I'm assuming you want to retry on network errors—verify that strategy." |
| "This might work..." | Hides confidence level | "I'm 70% confident this works, but I haven't seen your exact setup. Test it." |
| "Let me check that image..." | Pretends to have access | "I don't have access to the image contents. Paste the specs or product name." |

### Connection to Protocol

**Files force transparency:**
- Conversation allows hedging (AI can be vague, you won't notice until later)
- Files force clarity (when AI writes "Tech stack: [TBD]" you immediately see the gap)
- Ground truth prevents speculation (CLAUDE.md says "Next.js 14" so AI can't hedge)

Markdown files create a **shared record** where vague language is visible and fixable.

---

## Decision 13: BUILD File Authoring Style — Instructions, Not Documentation

**Date:** January 19, 2026
**Status:** Active
**Context:** First attempt at BUILD_GYM.md was written as documentation ABOUT what would happen. When tested, Claude read it and waited for instructions. The file didn't trigger execution.

**The Fundamental Insight:**

BUILD files must be written as **instructions TO Claude**, not documentation ABOUT what happens.

| Wrong (Documentation) | Right (Instructions) |
|-----------------------|----------------------|
| "Step 1: Create the App" | "Run: `npm create vite...`" |
| "The app will be created" | "Say: 'I'm creating a React app...'" |
| Describes what happens | Tells Claude what to do |
| User reads and waits | Claude executes step-by-step |

**Style Guide for BUILD Files:**

1. **Use "Say:" prompts** — Tell Claude what to communicate to the user
2. **Use "Run:" or code blocks** — Tell Claude what commands to execute
3. **Include "Wait for confirmation"** — Create natural pause points
4. **Offer clear choices** — Not open-ended questions
5. **Explain the WHY** — Each step should teach, not just execute

**Technical Gotchas Discovered:**

| Issue | Cause | Solution |
|-------|-------|----------|
| Vite fails with "Operation cancelled" | Non-empty folder | Move BUILD file to PARENT folder, not just rename |
| Tailwind init fails | Tailwind v4 changed setup | Pin to `tailwindcss@3` |
| User confused by first prompt | Claude asks folder permission | Document in README: "Allow it" |

**Testing Protocol:**

When creating or modifying BUILD files:
1. Create a test folder
2. Copy the BUILD file there
3. Run `claude` and prompt "read and follow [filename]"
4. Verify Claude executes (not just reads)
5. Verify output is correct
6. Clean up test folders

---

## Decision 12: Build Files Architecture — Generative, Not Pre-Built

**Date:** January 19, 2026
**Status:** Active
**Context:** Designing how the workshop kit delivers starter projects. The model is generative — BUILD files are instructions Claude follows to create projects at runtime.

**How It Works:**
1. User copies BUILD_GYM.md to empty folder
2. Opens Claude Code in that folder
3. Prompts: "read and follow BUILD_GYM.md"
4. Claude runs guided build flow
5. Output: Complete app with protocol files, ready to use

**Key Principles:**

| Principle | Implication |
|-----------|-------------|
| **Self-contained** | BUILD_GYM.md works in isolation (no dependencies on kit repo) |
| **Generative** | Kit has no protocol files — they're created at runtime |
| **Scalable** | New build files = new workshop variants |
| **Contributable** | Community can PR new build files |
| **Single + Multiplayer** | Same file works for solo learners AND workshop groups |

**Which Protocol?**

BUILD_GYM.md generates a **duo-style project** (collaboration protocol). After completing the workshop, learners can use full protocol-duo for their own projects.

---

## Decision 8: Session Structure — Problem/Solution Pedagogy

**Date:** December 29, 2024
**Status:** Active

**The Pivot:** 6 sessions using problem/solution pedagogy:
- Each session introduces a **problem** (discomfort)
- Then provides a **solution** (tool + confidence)
- Gym app as throughline case study (not fragmented projects)
- Sessions 1-4 on rails (everyone same app), Sessions 5-6 freedom (own idea)

**Key Pedagogical Principles:**

1. **Pain before relief.** They must feel the problem to value the solution.
2. **Non-determinism framing.** "You all did the same thing. Results differ. That's the tool. Protocol reduces variance."
3. **Progressive complexity.** Each session adds one layer.
4. **Rails then freedom.** Sessions 1-4: everyone on gym app. Sessions 5-6: own idea.
5. **Hackathon starts at hackathon.** Workshop teaches skills, not hackathon projects.

---

*Last updated: February 19, 2026*
