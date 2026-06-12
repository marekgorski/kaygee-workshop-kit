# Session 6: Building Shared Context

**Duration:** 45 minutes
**Problem:** Solo mastery isn't enough
**Solution:** Protocol enables collaboration
**Output:** Hackathon-ready team with shared context
**Core message:** Protocol connects humans too, not just you + AI

---

## The Problem

You can build alone now. But hackathons are teams.

- How does your teammate know what you built?
- How do they continue where you left off?
- How do you avoid stepping on each other's work?
- What happens when you go to lunch and someone else picks up?

Working alone doesn't prepare you for working together.

---

## The Solution

**Protocol connects humans too.**

The same files that help AI understand your project also help humans understand it.

- CLAUDE.md → What is this project?
- TODO.md → What's done, what's next?
- PROGRESS.md → What happened in each session?
- DECISIONS.md → Why did we make these choices?

When a teammate reads these files, they can pick up exactly where you left off — without asking you "so what are we building?" That's the power of persistent context: it travels with the project, whether the next session is you + AI or you + teammate.

---

## Structure

### Part 1: Team Formation (10 min)

**Form hackathon teams.**

Options for team formation:

**Option A: Self-selected by idea**
- Anyone with an idea from Session 5 stands up and pitches in 30 seconds
- Others join the team that interests them
- Aim for 2-4 people per team

**Option B: Pre-assigned teams**
- If teams are already set, use this time for intros
- Each person shares: "Here's what I built in Session 5"

**Option C: Random assignment**
- Count off: 1, 2, 3, 4... all 1s are a team

**Check-in:** "Is everyone on a team? Does everyone know their teammates' names?"

---

### Part 2: The Collaboration Exercise (15 min)

**Practice reading someone else's Protocol files.**

**Activity:**

1. Pair up with someone NOT on your hackathon team
2. Clone their Session 5 project (or gym app if they didn't start one)
3. Read only the Protocol files (CLAUDE.md, TODO.md)
4. Try to add one small feature WITHOUT asking them any questions

**The point:**

If the Protocol files are good, you can continue without the original person explaining anything.

If you're confused, the Protocol files need improvement.

**Debrief (5 min):**

> "What was missing? What would have helped you understand faster?"

Common answers:
- "I didn't know what tech stack they used" → Needs to be in CLAUDE.md
- "I didn't know what was already tried" → Needs to be in DECISIONS.md
- "I didn't know what to work on" → Needs to be in TODO.md

---

### Part 3: Hackathon Project Setup (15 min)

**Teams set up their hackathon project.**

**Every team does this:**

1. **Pick one idea** (or combine ideas from team members)
2. **Create a new repo** with Protocol files
3. **Write CLAUDE.md** together:
   - What is this?
   - Who is it for?
   - What's the MVP feature?
   - Tech stack (React, Supabase, etc.)
4. **Write TODO.md**:
   - What's the first thing to build?
   - What's the demo moment?
   - What's explicitly out of scope?

**Prompt for CLAUDE.md:**

```markdown
# [Project Name]

## What This Is
[One sentence]

## Who It's For
[Target user]

## MVP Feature
[The one thing it does]

## Tech Stack
- React + Vite
- Tailwind CSS
- Supabase (if data persistence needed)

## Out of Scope (for hackathon)
- [Thing we won't build]
- [Another thing we won't build]

## Demo Moment
[What we show at the end to prove it works]
```

**Check-in:** "Does every team have a CLAUDE.md written?"

---

### Part 4: Closing (5 min)

**Recap the day:**

> "This morning you started with nothing. Now you have:
>
> - Protocol files that tell AI what you're building
> - Git that tracks every change
> - Vercel that deploys automatically
> - Supabase that persists your data
> - Figma Make that bridges design to code
> - A team and a project ready for the hackathon"

**The transformation:**

| Before Today | After Today |
|--------------|-------------|
| Context in Confluence (goes stale) | Context in Git (versioned, growing) |
| Answers in Slack (disappear) | Answers in protocol files (travel with code) |
| Share Figma link → engineers rebuild | Share repo → engineers collaborate |
| "Here's the PRD, give me a URL" | Working together in the same codebase |
| On an island | On the mainland with engineering |

**For the hackathon:**

> "Start building immediately. When you get stuck, use the tools you learned today:
>
> - Ask Claude Code
> - Check the error message
> - Push to GitHub (save your work)
> - Read each other's Protocol files
>
> You have everything you need."

---

## What They Just Learned

| Before Session 6 | After Session 6 |
|------------------|-----------------|
| Solo builder | Sessions that compound (with AI and teammates) |
| Protocol for AI | Protocol connects everyone |
| My project | Our project |
| Workshop done | Hackathon ready |

---

## Success Criteria

By the end of Session 6:

- [ ] Everyone is on a hackathon team
- [ ] Everyone has experienced Protocol as collaboration tool (not just AI tool)
- [ ] Every team has a shared repo with CLAUDE.md and TODO.md
- [ ] Every team knows what they're building on hackathon day

---

## Facilitator Notes

**This session is about confidence.**

They've learned the skills. Now they need to believe they can use them without you.

**If teams are struggling to pick an idea:**

> "You don't need a perfect idea. You need a buildable idea. What's the simplest version that proves the concept?"

**If Protocol files are weak:**

Walk through an example together. Show what a good CLAUDE.md looks like vs. a vague one.

**Energy goal:**

End this session with: "We're ready. Let's build something."

---

## Workshop Complete

**What happens next:**

1. Hackathon day — teams build their projects
2. Demo/pitch at end of hackathon
3. Post-hackathon: Teams continue or hand off to engineering

**Post-workshop:**
- Debrief after hackathon
- Document what worked / what to improve

---

## Final Message to Participants

> "Today you went from 'I can't code' to 'I deployed an app.'
>
> But that's not the real transformation.
>
> The real transformation is HOW you work now:
>
> - Your context is in Git — versioned, searchable, growing. Not in Confluence where it goes stale. Not in Slack where it disappears.
> - Your code is in GitHub — same place engineers work. Not a Figma link they have to interpret and rebuild.
> - When context changes, everyone sees it — AI and humans alike.
>
> You're not starting from scratch every session anymore.
> Your context lives in files. AI reads them on boot. Every session builds on the last.
>
> That's the habit. That's the plumbing. That's what compounds.
>
> See you at the hackathon."
