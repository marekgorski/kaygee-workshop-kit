# AI Basics 101

A beginner's guide to working with AI tools effectively.

---

## The Memory Myth

**What you might think:** "AI remembers our conversations and learns about me over time."

**What's actually happening:** Every time you start a new chat, you're talking to someone who has never met you. LLMs (Large Language Models) like Claude, GPT, and Gemini don't have persistent memory. They read your message, generate a response, and forget everything.

**Why this matters:** If you spent 2 hours explaining your project yesterday, today's AI has no idea. You're starting from zero.

### You Already Have a Workflow

Here's the thing: you already have an AI workflow. It's just the one you built by accident.

**Accidental workflow looks like:**
- Copy-paste the same context into every chat
- Re-explain your project to AI every session
- Start from scratch when the chat expires
- Hope you remember what worked last time

**Intentional workflow looks like:**
- AI reads your context files at the start of every session
- Your decisions, constraints, and progress are documented
- Every session builds on the last
- A repeatable system that compounds

**Protocol is the intentional version.** It replaces your accidental workflow with one you build on purpose.

---

## Files Are Memory

Here's the trick: AI can't remember, but files can.

When you write context into a file:
- AI reads it at the start of each session
- It knows what you're building, what you've decided, where you left off
- You don't re-explain; you just continue

| Without Files | With Files |
|---------------|------------|
| "So what are we building?" | "I see we're building X. Last session you completed Y. Ready to tackle Z?" |
| You re-explain every session | You pick up where you left off |
| AI makes wrong assumptions | AI follows your documented decisions |

---

## The Hallucination Problem

**What you might think:** "AI sometimes makes things up, but I can catch it."

**What's actually happening:** LLMs generate text probabilistically. Without ground truth, they'll confidently invent facts, make assumptions, or misremember earlier context.

### Common Hallucinations

| Hallucination Type | Example | Why It Happens |
|--------------------|---------|----------------|
| **False memory** | "As we discussed last week..." (you never discussed it) | No actual memory, fills gaps with plausible text |
| **Invented facts** | "Your API uses OAuth 2.1" (you never mentioned auth) | Guesses common patterns |
| **Assumed context** | Changes code you didn't ask to change | Assumes "improvements" are wanted |
| **Phantom features** | "The login system already has password reset" (it doesn't) | Confabulates from similar projects |

### Why Hallucinations Happen

AI doesn't "know" things. It predicts the next most likely token based on patterns from training. Without explicit context:
- It fills gaps with "reasonable" guesses
- It blends your project with patterns from millions of others
- It confidently states assumptions as facts
- Each new session increases drift (no memory = fresh start = new assumptions)

---

## Transparency as Collaboration Principle

**What you might think:** "AI hedges because it's being careful and thoughtful."

**What's actually happening:** Vague hedging ("This might work...", "You could try...") is a form of dishonesty. It sounds careful but actually hides whether AI is certain, making educated guesses, or completely speculating.

### The Problem with "Polite Uncertainty"

AI models are trained to be helpful. When uncertain, they often hedge instead of saying "I don't know." This wastes your time and breaks collaboration.

| Bad Transparency | Why It's Bad | Good Transparency |
|------------------|--------------|-------------------|
| "I'll add error handling." | Sounds confident but is vague about what/where/why | "I'll add try-catch around the API call. I'm assuming you want to retry on network errors—you'll need to verify that strategy." |
| "This might work..." | Hides confidence level | "I'm 70% confident this works, but I haven't seen your exact setup. Test it and let me know." |
| "You could try X or Y..." | Makes you do the thinking AI should do | "I don't have enough context to recommend. Can you tell me: [specific question]?" |
| "Let me check that image..." | Pretends to have access it doesn't have | "I don't actually have access to the image contents. If you paste the specs or product name, I can evaluate it." |

### Why This Matters for Collaboration

**Transparent uncertainty speeds you up:**
- You know exactly what to verify
- You know when AI is guessing vs. certain
- You can make informed decisions about what to trust

**Vague hedging slows you down:**
- You waste time testing uncertain approaches
- You don't know what AI made up vs. what it knows
- You lose trust when "might work" doesn't work

### How to Demand Transparency

When AI gives vague answers, push back:

**You:** "Are you certain, making educated guesses, or speculating?"

**AI (good response):** "I'm making an educated guess based on common patterns. I haven't seen your codebase structure, so verify the file path is correct."

**AI (bad response):** "This should work in most cases..." (Still hedging—push again!)

### The "I Don't Know" Rule

The best AI collaborators say "I don't know" when they don't know.

**Example: Missing Visual Input**

```
Bad AI: "Can you specify which product you're asking about?"
(Pretends it can see, doesn't explain why it's asking)

Good AI: "I don't actually have access to the image contents—the vision
pipeline didn't reach me. If you paste the product name or specs, I can
evaluate it."
(Transparent about limitation, explains why, offers solution)
```

**Example: Unfamiliar Codebase**

```
Bad AI: "I'll refactor this for better performance."
(Sounds confident, might break things)

Good AI: "I see performance issues in the loop, but I don't know if this
code path is critical. Refactoring could improve speed 30% but risks
breaking edge cases I can't see. Want me to proceed or investigate first?"
(States confidence, identifies risk, asks for direction)
```

### Connection to Protocol

**Why files force transparency:**

- **Conversation allows hedging** — AI can be vague, and you won't notice until later
- **Files force clarity** — When AI writes "Tech stack: [TBD]" you immediately see the gap
- **Ground truth prevents speculation** — CLAUDE.md says "Next.js 14" so AI can't hedge with "probably Next or React"

Markdown files create a **shared record** where vague language is visible and fixable.

### Confidence Levels You Should Expect

| Confidence Level | What AI Should Say | What You Should Do |
|------------------|--------------------|--------------------|
| **Certain** | "This will work because [specific reason]." | Trust and verify anyway |
| **High confidence** | "This should work based on [pattern]. Verify [specific thing]." | Test the specific thing |
| **Educated guess** | "I'm guessing X based on [assumption]. Confirm [assumption] first." | Confirm assumption before proceeding |
| **Speculating** | "I don't have enough context. Can you provide [specific info]?" | Provide info or decide differently |
| **Don't know** | "I don't know. Let me research [specific thing] or you can tell me." | Appreciate the honesty, help AI learn |

### Red Flags (AI Avoiding Transparency)

Watch for these signs AI is hedging instead of being honest:

- "This might work..."
- "You could try..."
- "In some cases..."
- "Depending on your setup..."
- Asking clarifying questions without explaining WHY it's asking

**When you see these:** Ask "How confident are you? What are you assuming?"

---

## Markdown Files as Ground Truth

Here's the solution: **Files are the single source of truth that prevents hallucinations.**

### How Files Reduce Hallucinations

| Without Files | With Files |
|---------------|------------|
| AI guesses your tech stack | CLAUDE.md: "Tech: Next.js 14, Supabase, Tailwind" |
| AI assumes features exist | PRFAQ.md: "What we're building, what's done, what's not" |
| AI invents past decisions | DECISIONS.md: "DEC-001: Why we chose X over Y" |
| AI contradicts itself | CONSTRAINTS.md: "Never use library X (reason)" |

### The Grounding Effect

When you write context into files, you **anchor AI to facts**:

1. **Explicit beats implicit** — "Use OAuth" in a file is stronger than 50 conversational messages about auth
2. **Files persist** — Every session starts with the same ground truth
3. **You can verify** — Read the file to check what AI "knows"
4. **Corrections compound** — Fix a hallucination in the file, it stays fixed

**Example: Preventing Tech Stack Hallucination**

```markdown
BAD (no ground truth):
You: "Build a login page"
AI: [assumes Express + MongoDB, builds wrong stack]
You: "No, we use Next.js and Supabase"
AI: [rebuilds, but might assume other Next.js patterns incorrectly]

GOOD (ground truth in CLAUDE.md):
CLAUDE.md says:
## Tech Stack
- Framework: Next.js 14 (App Router)
- Database: Supabase (PostgreSQL)
- Auth: Supabase Auth (not NextAuth, not custom)
- UI: Tailwind + shadcn/ui

AI reads file, builds correctly from the start.
No assumptions, no hallucinations.
```

### Predictable Outcomes

With files as ground truth:

**Consistency:** Same prompt + same files = same result
- Session 1: "Add login" → OAuth implementation
- Session 5: "Add signup" → OAuth implementation (not password-based)
- Session 10: "Add password reset" → AI reminds you: "CONSTRAINTS.md says OAuth-only"

**Catch drift early:** When AI contradicts a file, you spot it immediately
- AI suggests MongoDB → You see CLAUDE.md says Supabase → Correct before code is written

**Accumulating knowledge:** Each documented decision makes future sessions smarter
- DECISIONS.md grows with each "why we chose X"
- TODO.md captures acceptance criteria
- CONSTRAINTS.md captures rejected approaches

---

## Building Your Ground Truth System

### Start Small

You don't need 50KB of documentation. Start with three essentials:

**1. CLAUDE.md — Technical Facts**
```markdown
## Tech Stack
- [Exact versions and tools]

## Architecture
- [How things connect]

## Current State
- [What exists, what doesn't]
```

**2. TODO.md — What's Next**
```markdown
## Active
- [ ] Feature X
  - AC: Specific, testable criteria
```

**3. CONSTRAINTS.md — Never Do This**
```markdown
## Rejected Approaches
- ❌ Don't use library X (reason: Y)
- ❌ Don't implement feature Z (decided: DEC-015)
```

### Grow Incrementally

Each time AI hallucinates:
1. Catch it
2. Document the truth in the relevant file
3. Next session reads the correction
4. Same mistake won't repeat

**Example workflow:**
```
Session 1: AI assumes Express
→ Add to CLAUDE.md: "Framework: Next.js 14"

Session 2: AI suggests class components
→ Add to CONSTRAINTS.md: "React: Functional components only"

Session 3: AI tries to add MongoDB
→ Add to CONSTRAINTS.md: "Database: Supabase only (PostgreSQL)"

Session 10: AI confidently works within all documented constraints
→ Zero hallucinations about stack
```

### Verification Points

Files enable verification loops:

**Before AI acts:**
```
AI: "I see from CLAUDE.md we're using Supabase.
     I'll add the auth logic using Supabase Auth."
You: ✓ Correct
```

**When something seems wrong:**
```
AI: "I'll add Prisma for the database layer"
You: Check CLAUDE.md → Says Supabase direct
You: "No, CLAUDE.md says we use Supabase client directly"
AI: "You're right. Let me use Supabase client instead."
```

---

## Why Edit a File Instead of Re-Prompting?

When context lives in a prompt, it's invisible. You type it, hit send, and it disappears into the conversation.

When context lives in a file:

1. **You can see errors.** AI misunderstood something? You'll spot it when you read the file.
2. **You can fix before the next call.** Correct the misunderstanding in the file, not through another round of "no, I meant..."
3. **It compounds.** Each correction makes the file more accurate. Prompts don't compound — they're one-and-done.

**Example:**

```
BAD (re-prompting):
You: "Build a login page"
AI: [builds something wrong]
You: "No, I meant with OAuth, not email/password"
AI: [rebuilds]
You: "And it should match our design system"
AI: [rebuilds again]

GOOD (file-based):
CLAUDE.md says: "Auth: OAuth only. Design system: Tailwind + shadcn."
AI reads file, builds it right the first time.
```

---

## Token Economics

### What Are Tokens?

Tokens are how AI measures text. Roughly:
- 1 token ≈ 4 characters (English)
- 1 token ≈ ¾ of a word
- This sentence is about 10 tokens

Every interaction costs tokens:
- **Input tokens:** What you send (your message + context files)
- **Output tokens:** What AI generates back

### Why This Matters

| Pricing Model | How It Works | Example Tools |
|---------------|--------------|---------------|
| **Per-token** | Pay for each token in/out | Claude API, OpenAI API |
| **Per-request** | Fixed cost per message (tokens abstracted) | Cursor, some Claude plans |
| **Subscription** | Monthly fee, usage limits | Claude Pro, ChatGPT Plus |

**The trap:** If you're on a token-based plan, large context files drain your budget fast. If you're on a request-based plan, you might hit daily limits.

### Practical Implications

1. **Know your limits.** Check your plan. How many requests/tokens per day? When does it reset?
2. **Keep context lean.** Don't load 50KB of files if you only need 5KB for this task.
3. **Archive old content.** Move completed work to archive folders so it's not loaded every session.
4. **Batch your work.** One focused 30-minute session beats ten 3-minute sessions (less overhead).

---

## Context Budget

Think of AI like a person with a whiteboard. The whiteboard has limited space.

- **Small whiteboard = short context window** (older/cheaper models)
- **Large whiteboard = long context window** (newer/premium models)

Everything must fit on the whiteboard:
- Your current message
- The files AI is reading (CLAUDE.md, TODO.md, etc.)
- The conversation so far
- Room for AI's response

If you fill the whiteboard with context, there's less room for AI to think and respond well.

**The protocol's solution:** Different roles load different amounts of context.

| Role | What It Loads | Why |
|------|---------------|-----|
| Architect | Full context (~15%) | Needs big picture for planning |
| Builder | Lean context (~5%) | Needs focus for implementation |

---

## Which Protocol Is For You?

Ask yourself: **"What's AI's role in my work?"**

### AI works FOR you → uno (Delegate)

You define WHAT needs doing. AI handles HOW.

**Examples:**
- "Plan my trip to Australia"
- "Track my 90-day onboarding"
- "Maintain this documentation"

**Best for:** Personal projects, executive assistance, knowledge management

---

### AI works WITH you → duo (Collaborate)

You and AI build together. AI designs, you approve. AI implements, you guide.

**Examples:**
- "Build this web app with me"
- "Refactor this codebase"
- "Create this product from scratch"

**Best for:** Software projects, complex builds, anything with code

---

### AI works AMONG systems → tre (Automate)

AI operates between your tools, with quality gates and human approval points.

**Examples:**
- "Triage incoming tickets automatically"
- "Run deployment checks before release"
- "Route customer requests by sentiment"

**Best for:** Workflows, automation, pipelines (Note: tre is still in development)

---

## Quick Decision Tree

```
Do you need AI to write code?
├── Yes → duo (Collaborate)
└── No
    ├── Is this an automation/workflow?
    │   ├── Yes → tre (Automate) [coming soon]
    │   └── No → uno (Delegate)
    └── What kind of delegation?
        ├── Work project with deadlines → uno/ea
        ├── Personal logistics (travel, events) → uno/pa
        └── Documentation/knowledge → uno/km
```

---

## Glossary

| Term | Meaning |
|------|---------|
| **LLM** | Large Language Model — the AI that powers tools like Claude, GPT, Gemini |
| **Context** | Everything AI can "see" — your message, files, conversation history |
| **Context window** | Maximum context size (measured in tokens) |
| **Token** | Unit of text (~4 characters). Bigger context = more tokens = more cost |
| **Handoff** | Structured transfer of context, like a shift change briefing |
| **Session** | One working period with AI. Progress is saved automatically after each interaction |
| **AC** | Acceptance Criteria — how you know a task is actually done |
| **Fossilize** | Save current state to files so the next session can pick up. Happens automatically after each interaction |

---

## Common Mistakes

| Mistake | Why It Hurts | Fix |
|---------|--------------|-----|
| Treating AI like it remembers | You re-explain, waste tokens, get inconsistent results | Use files for persistent context |
| Relying on conversational context | AI hallucinates, invents facts, makes assumptions | Document ground truth in files |
| Not documenting tech stack | AI guesses wrong tools, builds incompatible code | CLAUDE.md with explicit stack details |
| Letting hallucinations slide | Same wrong assumptions repeat across sessions | Catch and document corrections in files |
| Giant context files | Eats your token budget, slower responses | Archive old content regularly |
| No acceptance criteria | "Done" but actually broken | Every task needs testable AC |
| Not checking files before closing | Files out of sync, next session confused | Verify files are up to date before ending your session |
| Not knowing your limits | Surprised when you're locked out | Check plan, track usage |

---

## Next Steps

1. **Pick your protocol** — uno, duo, or tre based on your work
2. **Clone the template** — Get the starter files
3. **Run onboarding** — AI will ask 5 questions and set up your project
4. **Start working** — AI reads your files automatically and saves progress after each interaction

See the protocol-specific cheat sheets for detailed commands.

---

*KayGee Protocol Family — January 2026*
