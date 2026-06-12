# Facilitator Guide: Running Your Own Workshop

**Hey, you must be clever if you're reading this.**

It means you're about to run a workshop for folks. Bad news: you'll likely expect they're as clever as you. But they aren't — that's why they need you to run it. They're not as clever because some of this is still more foreign and scary to them than it is for you.

**Lead with kindness and explain the basics to them, even though you think they already know.** Losing them early means you'll lose them for the entire workshop day.

Next, find your friends — the other clever ones who are just more shy than you and happy for you to lead while they support. Those are your helpers. Brief them. Position them around the room. When someone falls behind, they swoop in while you keep the group moving.

---

## The Panama Canal Locks: Managing Mixed-Skill Groups

**The biggest facilitator fear:** "There are advanced people in my room. They'll think this is too basic."

**The reframe:** You're not running one workshop. You're running parallel experiences in the same room.

### The Metaphor

The Panama Canal has locks that raise and lower ships to different water levels. You can't lift all ships at once — you bring up the bottom first, then level everyone.

**In practice:**

1. **Acknowledge the spread early:**
   > "Some of you have deployed apps before. Some of you have never opened a terminal. Both are fine. We're going to move together."

2. **Promise the top you'll get to them:**
   > "If you're already comfortable with Git, you'll be our helpers this morning. This afternoon, when we get to Protocol patterns, you'll be learning with everyone else."

3. **Deputize the fast ones:**
   > "If you finish early, find someone who's stuck. Help them catch up. That's how real teams work."

### Why This Works

- **Beginners** feel safe, not embarrassed
- **Advanced users** feel useful, not bored
- **You** don't have to choose between audiences

### The Facilitator's Secret

You don't need to know more than everyone. You need to have **lived it**.

A common facilitator concern: "But there will be developers in the room who know more than me."

The answer: "They know more about code. You know more about making AI sessions compound. You've done this. They've read about it. That's the difference."

---

## The "Accidental vs Intentional" Hook

**An alternative opening for Session 1:**

> "You already have an AI workflow. Raise your hand if you copy-paste prompts, start fresh every session, or re-explain your project to AI every time. That's a workflow — it's just the one you built by accident."

**Why this works:**
- Immediate recognition (everyone does this)
- Non-judgmental (it's not "you're doing it wrong")
- Creates desire for the alternative ("what's the intentional version?")

**The bridge to protocol:**

> "Protocol is the intentional version. Instead of starting from scratch, AI reads your context files. Instead of re-explaining, you continue where you left off. Your workflow compounds instead of resetting."

**When to use:**
- Opening of Session 1 (before the non-determinism demo)
- Alternative to "95% of time wasted re-explaining" stat
- When audience includes skeptics who think "I don't have a workflow"

---

## The "Throwaway Work" Reframe

**The moment that changes everything:**

> "What you build today is throwaway work. You're not learning to build apps. You're learning to compress feedback loops."

**The pitch:**

> "45 minutes of throwaway work to reduce delivery time from five weeks to one. Is that good throwaway work? Yes."

**Why this matters:**

- Participants stop worrying about "production quality"
- They understand the output is for decision-making, not deployment
- The skill is durable even when the artifact is disposable

**Use this framing in Session 1 intro.** It depressurizes the room.

---

## The Pedagogy: How People Actually Learn

### 1. Put the Question in Their Head First

People don't remember answers to questions they didn't ask.

**Bad facilitation:**
> "Git is a version control system. It tracks changes to your code."

(Nobody cared. They're not asking "what is Git?")

**Good facilitation:**
> "Make a change to your app. Break something on purpose. Now try to get back to where you were. How? Cmd+Z? Hope? This is why you need Git."

NOW they're asking "what is Git?" and the answer lands.

**The pattern:**
1. **Create discomfort** (the problem)
2. **Let them feel it** (don't rescue immediately)
3. **Introduce the solution** (relief)

Every session follows this: Problem → Solution. Pain before relief.

---

### 2. Show, Don't Tell (Then Let Them Do)

You'll be tempted to explain concepts. Resist.

**Bad:**
> "Protocol files give AI persistent memory. CLAUDE.md contains the tech stack. TODO.md has tasks. When AI reads these files..."

(You lost them at "persistent memory.")

**Good:**
> "Open Claude Code without the protocol files. Ask it to add a feature. Watch it guess wrong. Now open it WITH the protocol files. Same prompt. Watch it get it right. That's the difference."

Then let them try it themselves.

**The pattern:**
1. **Demo the problem** (AI guessing wrong)
2. **Demo the solution** (AI reading context)
3. **They try it** (hands-on immediately)

---

### 3. Celebrate Small Wins Publicly

When someone deploys for the first time, make noise about it.

> "Raise your hand if you have a live URL. Look around — you all just shipped to the internet in 45 minutes. That's real."

People need permission to feel proud. Give it to them. Vocally.

---

### 4. Normalize Struggle

When something breaks (and it will), narrate it.

> "My deploy just failed. Cool. Let's read the error together. This is what real development looks like — you read errors, you fix them, you move on."

**Never hide errors.** Show them how you debug. Google the error. Read Stack Overflow. Model the behavior they'll need on Monday.

---

### 5. Answer the "Why Should I Care?" Before the "How"

Every session must answer **"Why does this matter to ME?"** before you teach the mechanics.

**Session 2 (Git):**
- ❌ "Git tracks changes. Here's how to commit."
- ✅ "You just built something. What if you break it? What if your laptop dies? Git is the safety net."

**Session 3 (Deploy):**
- ❌ "Vercel deploys your app. Let's connect GitHub."
- ✅ "Right now your work is invisible. Engineers can't see it. When you share a Figma link, they rebuild anyway. Let's put your work where they already are."

Lead with the pain. Then introduce the tool.

---

## Where This Workshop Fits: The Uno/Duo/Tre Landscape

**Participants will ask:** "Is this the only way to work with AI?"

**The answer:** No. There are three modes. We teach one.

| Protocol | Mode | What It Means | Example |
|----------|------|---------------|---------|
| **Uno** | Delegate | AI works FOR you. Clear task, trust output. | "Book my flights." |
| **Duo** | Collaborate | AI works WITH you. Iterative, scope modifiers. | "Let's build this app together." |
| **Tre** | Automate | AI works AMONG systems. Quality gates, approvals. | "Review all PRs, flag risks." |

**This workshop teaches Duo.**

Why? Because collaboration requires practice. Delegation and automation you can figure out alone. But working *with* AI — switching between architect and builder roles, accumulating constraints, maintaining shared context — that takes guided practice.

**When they ask "why not Uno?":**
> "Uno is for assistants. You give a task, you get a result. No iteration. Duo is for building — you're co-creating, not delegating."

**When they ask "why not Tre?":**
> "Tre is enterprise workflow automation. Multiple AI agents, approval gates, handoffs. That's phase 2. First, you learn to collaborate with one."

---

## Why Files Are Split: The Economic Reason

**Participants will notice:** "There are a lot of files. CLAUDE.md, TODO.md, DECISIONS.md, PROGRESS.md..."

**The surface answer:** "Organization."

**The real answer:** **Token economics.**

### The Constraint

Every AI conversation has a context window — a limit on how much text it can "see" at once. When you hit that limit:
- AI forgets earlier context
- Responses get slower and more expensive
- Quality drops

### The Solution

**Split memories into buckets.** Each file has a job:

| File | What It Holds | When It's Loaded |
|------|---------------|------------------|
| `CLAUDE.md` | Project identity, tech stack, patterns | Always |
| `TODO.md` | Current work items | When planning |
| `DECISIONS.md` | Architectural choices | When designing |
| `PROGRESS.md` | Session history | Rarely (archival) |
| `CONSTRAINTS.md` | Rules AI must follow | Always |

**The pattern:**
- Small, focused files = cheaper, faster, more accurate
- One giant file = expensive, slow, forgetful

**The trade-off to explain to participants:** "Yes, these files cost tokens every session — about 5% of your context window. But without them, you spend 30% re-explaining what you already know. You're trading a small slice of context for a reliable memory. After two or three sessions, you're way ahead."

**For facilitators:** This isn't just organizational preference. It's an economic design decision. The protocol is a deliberate token trade — small upfront cost, compounding returns. Explain it when someone asks "why so many files?"

### Teaching Tip: Saving is Automatic

When participants ask "what happens if I forget to save?" — the answer is: **AI saves automatically.** Every interaction, AI updates the relevant files and commits. No ceremony needed.

Frame it as: "You don't need to remember to save. The protocol does it for you. That's what makes it a system, not a habit."

This is one of the first "aha" moments — especially for experienced developers used to manual save points.

---

## The Workshop Agenda (And Why It's Ordered This Way)

### Session 1: Protocol (45 min)
**The problem:** 95% of time wasted re-explaining context to AI.

**Why first:** They need to see AI work WITH context files before they understand why the rest of the day matters.

**The "aha" moment:** Non-determinism demo. Everyone gives the same prompt. Results differ. "That's the tool. Protocol reduces variance."

**Energy goal:** "That was fast. And it worked."

---

### Session 2: Git (45 min)
**The problem:** Can't undo mistakes. Can't track changes. Code only exists on your laptop.

**Why second:** Now that they've built something, they need to protect it.

**The "aha" moment:** Break something on purpose. Can't undo it. Git saves you.

**Energy goal:** "My code is safe now."

**Common mistake:** You'll want to explain branching, merging, rebasing. DON'T. Today they learn: `git add`, `git commit`, `git push`. That's it.

---

### Session 3: Deploy (45 min)
**The problem:** Work lives on your laptop, isolated from engineers.

**Why third:** This is the peak moment. They ship something to the internet.

**The "aha" moment:** Click the live URL. It works. Share it. Click someone else's.

**Energy goal:** "I shipped something to the internet. I can do this."

**Common mistake:** Treating this as a technical exercise. It's not. It's about **visibility**. Frame it as "your work now lives where engineers work."

---

### Session 4: Data (45 min)
**The problem:** App has amnesia. Refresh = everything disappears.

**Why fourth:** They've built, versioned, deployed. Now make it remember.

**The "aha" moment:** Log data. Refresh. It's still there.

**Energy goal:** "My app is real now."

**Common mistake:** Getting bogged down in Supabase setup. If someone is stuck, have them pair-share a Supabase project. Catch up during lunch.

---

### LUNCH (60 min)

**Why lunch here:** Morning is high-intensity learning. They need to decompress.

**Helpers:** Use lunch to catch up stragglers. By Session 5, everyone should have a working app.

---

### Session 5: Recovering from Failures (45 min)
**The problem:** Prototype doesn't match Figma. Things break. Engineers rebuild from scratch.

**Why fifth:** They've mastered the basics. Now learn to recover when things go wrong and bridge design to code.

**The "aha" moment:** Pivot to their own idea. "You've been on rails (gym app). Now build something YOU care about."

**Energy goal:** "I have my own thing now."

**Common mistake:** Overcomplicating Figma Make. It's a 10-minute demo. The real work is them starting their own project.

---

### Session 6: Building Shared Context (45 min)
**The problem:** Solo mastery isn't enough. Teams need shared understanding.

**Why last:** Everything leads to this. They learn Protocol connects humans too, not just AI.

**The "aha" moment:** Read someone else's Protocol files. Try to continue their work without asking questions.

**Energy goal:** "We're ready to build — and every session will compound."

**Common mistake:** Skipping the collaboration exercise because you're running behind. DON'T. This is why the whole day exists.

---

## The Emotional Arc of the Day

| Time | Session | Emotional State | What They Need From You |
|------|---------|-----------------|-------------------------|
| 9:00 | Session 1 | Nervous, skeptical | Confidence. Quick wins. |
| 9:50 | Session 2 | Curious, focused | Clarity. Simple instructions. |
| 10:50 | Session 3 | **PEAK** excitement | Celebration. Public wins. |
| 11:35 | Session 4 | Tired, caffeinated | Energy. Helpers circulating. |
| 12:20 | Lunch | Exhausted relief | Space. Don't work through lunch. |
| 1:20 | Session 5: Recovering from Failures | Renewed (own idea!) | Freedom. Permission to experiment. |
| 2:15 | Session 6: Building Shared Context | Energized, ready | Confidence. "You got this." |

**The dip happens after Session 4.** Plan for it. Lunch saves you.

**The second peak happens in Session 5** when they pivot to their own idea. Lean into it.

---

## What Will Go Wrong (And How to Recover)

### 1. "npm install is taking 10 minutes"

**Why:** Corporate firewall, antivirus blocking, slow WiFi.

**Fix:**
- Don't wait. Help individually while others move on.
- If 50%+ stuck: pause, address as group (likely a shared WiFi issue).

**Prevention:** Pre-download `node_modules` and distribute via USB stick as backup.

---

### 2. "git push says Permission denied"

**Why:** SSH keys not set up.

**Fix:**
- Switch everyone to HTTPS immediately:
  ```bash
  git remote set-url origin https://github.com/USERNAME/REPO.git
  ```
- They'll be prompted for username/password.

**Prevention:** Default to HTTPS in all instructions. SSH is optional for advanced users.

---

### 3. "Claude Code is rate-limited"

**Why:** 25 people hitting Claude simultaneously.

**Fix:**
- Have them wait 60 seconds and retry.
- Stagger requests: "Left side of room, wait 30 seconds."
- Worst case: Have pre-generated code snippets ready. Paste while you narrate.

**Prevention:** Don't have everyone hit Enter at the same time. Build in natural delays.

---

### 4. "Vercel deploy failed"

**Why:** Missing dependency, wrong build command, environment variable issue.

**Fix:**
- Show the error log on screen.
- Read it out loud together.
- Ask Claude Code: "This Vercel deploy failed with [error]. How do I fix it?"

**Prevention:** Test the full deploy flow yourself the day before.

---

### 5. "I'm running 20+ minutes behind"

**Why:** Demos too long, or one session had too many issues.

**Fix (choose one):**
- **Option A:** Compress Session 4 (skip walkthrough, helpers assist individually).
- **Option B:** Combine Sessions 5 & 6 (demo only, skip hands-on).
- **Option C:** Cut afternoon break (risky, people need breaks).

**DON'T cut:**
- ❌ Session 3 (deployment) — this is the peak moment.
- ❌ Session 6 (shared context) — the whole workshop builds to this.

**Prevention:** Practice your demos. Time yourself. Aim for 60% of allotted time.

---

### 6. "Someone's laptop is completely broken"

**Why:** Admin permissions locked, hardware failure, incompatible OS.

**Fix:**
- Try **GitHub Codespaces** first (full VS Code in browser, free tier).
- If that fails: pair them with a neighbor (two people, one laptop).
- Last resort: they take notes and watch.

**DON'T:** Spend 30 minutes debugging one person's machine while 24 people wait.

---

### 7. "No one is asking questions"

**Why:** Too intimidated, or completely lost.

**Fix:**
- Prompt: "What's confusing so far?"
- Or: "Turn to your neighbor. What's one thing you don't understand?"

**Prevention:** Ask a question yourself, then answer it. Models the behavior.

---

## Build Verification (Before Workshop)

Before the workshop, generate the gym app using `BUILD_GYM.md` and verify:

- [ ] `npm install` completes in < 60 seconds
- [ ] `npm run dev` starts without errors
- [ ] App runs on localhost:5173
- [ ] Form submits and displays workout
- [ ] `npm run build` succeeds (for Vercel)
- [ ] Claude Code can read CLAUDE.md and add features coherently

### What's Intentionally Out of Scope

| Feature | Why Out |
|---------|---------|
| Data persistence | Session 4 adds Supabase |
| User authentication | Out of scope for workshop |
| Multiple screens/routing | Unnecessary complexity |
| Environment variables | Would complicate Vercel deploy |
| Testing setup | Not teaching testing |
| ESLint/Prettier config | Distraction |

### Session 1 Non-Determinism Prompt

Everyone uses the same prompt to demonstrate non-determinism:

> "Add a rest timer feature. When I finish a set, I should be able to start a countdown timer (default 90 seconds) that alerts me when rest is over."

Expected variance:
- Some will add timer as modal
- Some will add inline below form
- Some will use different UI patterns
- All should work, all will look different

**This variance is the teaching moment.** Same input, different output. That's AI. Protocol reduces variance.

---

## How to Practice

### 1. Run the Full Workshop Solo

**Timeline:** 3 days before the workshop.

**What to do:**
1. Clone the repo.
2. Go through every session as if you're a participant.
3. Time each session. Where do you run over?
4. Note where you got stuck. Those are your helpers' hot zones.

**Goal:** Know where friction happens BEFORE 25 people hit it.

---

### 2. Dry-Run Your Demos

**What to practice:**
- Session 1: Protocol demo (AI without context vs. with context)
- Session 2: Breaking code on purpose, then using Git to recover
- Session 3: Deploy to Vercel, test auto-deploy
- Session 4: Supabase setup, data persistence

**Goal:** No surprises. You've seen every error before.

---

### 3. Brief Your Helpers

**When:** Morning of, or night before.

**What they need to know:**
- The schedule (when are breaks, when can they catch people up).
- Common errors and fixes (see "What Will Go Wrong" above).
- Their role: roam during hands-on, pull stuck people aside, don't wait for raised hands.

**Give them:** A copy of this guide and the FACILITATOR_RUNBOOK.md.

---

## Your Pre-Workshop Checklist

**Day before:**
- [ ] Run the full workshop solo (practice)
- [ ] Test venue WiFi (can 25+ devices npm install simultaneously?)
- [ ] Brief your helpers (30-min call or meeting)
- [ ] Confirm backup facilitator (if you get sick)
- [ ] Have pre-generated code snippets ready (in case Claude rate-limits)

**Day of (30 min before start):**
- [ ] Test projector/screen sharing
- [ ] Connect to WiFi, test npm install speed
- [ ] Open all tools (Claude Code, VS Code, GitHub, Vercel)
- [ ] Schedule visible (printed or on side screen)
- [ ] Water bottle
- [ ] This guide open on laptop

---

## The Secret to Great Facilitation

**Meet them where they are, not where you are.**

You understand Git. They don't. You've debugged a thousand errors. They haven't. You know why Protocol matters. They don't (yet).

Your job isn't to show how much you know. Your job is to walk beside them and make them feel capable.

**The best facilitators:**
- Say "I don't know, let's figure it out together."
- Show their own mistakes publicly.
- Celebrate every small win loudly.
- Never make someone feel dumb for asking a basic question.

You're not the expert on stage. You're the guide walking with them.

### Transparency Works Both Ways

The same principle applies when working WITH AI during the workshop:

**Model transparent communication:**
- "I'm 80% sure this is right, but let's test it."
- "I made an assumption here—let me explain it."
- "This approach has a risk: X. We should account for it."
- "I don't know why that failed. Let's read the error together."

**Why this matters:**
- Participants learn transparency by watching YOU practice it
- AI learns patterns from how you communicate
- Transparent uncertainty builds trust faster than false confidence
- "I don't know" is more powerful than vague hedging

When you model honest collaboration with AI, participants see what good collaboration looks like—both with AI and with each other.

---

## When You Finish

**After the workshop, while it's fresh, write down:**
1. What took way longer than expected?
2. What went faster than expected?
3. What questions came up repeatedly?
4. What would you cut next time?
5. What would you add next time?

**Share it with the KayGee community.** The next facilitator learns from you.

That's the model: we run our own workshops, we share what works, we make it better together.

---

**Ready?**

You've got this. Your participants are lucky to have you.

See you on the other side.

—The KayGee Community

---

*Version 1.0 — January 2026*
*Feedback? Improvements? Open an issue on GitHub or email workshops@kayg.ee*
