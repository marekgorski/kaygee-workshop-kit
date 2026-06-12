# Session 5: Recovering from Failures

**Duration:** 45 minutes
**Problem:** Prototype doesn't match Figma file
**Solution:** Figma Make + understanding the handoff
**Output:** Design-aligned code (and pivot to your own idea)

---

## The Problem

You built something. It works. But it doesn't look like the Figma mockup you started with.

The designer's vision and the AI's output don't match. Colors are off. Spacing is wrong. Components don't look right.

This is the "design drift" problem — and it's why engineers often rebuild what designers already prototyped.

---

## The Solution

**Figma Make** — turns Figma designs into code automatically.

But there's a catch: Figma Make has its own rigid protocol files. You can't easily customize them. So we need to understand when to use Figma Make, and when to use what you've learned in Sessions 1-4.

---

## Structure

### Part 1: The Problem Demo (10 min)

**Show the gym app vs. a Figma mockup:**

If you have a Figma file for the gym app, show it side-by-side with what participants built.

Differences you might see:
- Different colors
- Different spacing
- Different font sizes
- Different button styles

> "AI generated something functional. But it doesn't match the design spec. In your job, this gap creates friction between design and engineering."

**Alternative demo (if no Figma file):**

Show any Figma design, then ask Claude Code to build it. Notice how the output is close but not exact.

---

### Part 2: Figma Make Demo (15 min)

**Show Figma Make in action:**

1. Open a simple Figma design (a button, a card, a form)
2. Use Figma Make to generate code
3. Download the code
4. Show what you get

**What Figma Make does well:**
- Exact colors, spacing, typography from Figma
- Component structure matches the design
- CSS/Tailwind classes are generated

**What Figma Make doesn't do:**
- State management
- API connections
- Complex logic
- Custom functionality

**Narrate:**

> "Figma Make is great for turning static designs into static code. But it doesn't know about your Supabase database, your business logic, or your custom features.
>
> The handoff point: Use Figma Make to get the visual foundation, then use Claude Code + Protocol to add the intelligence."

---

### Part 3: The Handoff Point (5 min)

**When to use what:**

| Task | Tool |
|------|------|
| Design → Static Code | Figma Make |
| Static Code → Working App | Claude Code + Protocol |
| Adding features | Claude Code + Protocol |
| Fixing design drift | Ask Claude to match specific styles |

**The key insight:**

> "Figma Make gives you a starting point with exact design specs. But its protocol files are locked — you can't customize them like you can with your own CLAUDE.md.
>
> Once you download code from Figma Make, you bring it into your Protocol workflow. That's the handoff."

---

### Part 4: Pivot to Your Own Idea (15 min)

**This is the freedom moment.**

Sessions 1-4 were on rails — everyone built the gym app together. Now you apply what you learned to your own idea.

**Activity:**

> "Think about the hackathon. What do you want to build?
>
> It doesn't need to be complex. One screen. One feature. Something you'd want to show at the end of the hackathon."

**Examples:**
- A feedback collector for your team
- A simple dashboard for a metric you care about
- A tool that solves a small annoyance in your workflow
- A prototype of a feature you've been thinking about

**Give them 5 minutes to:**
1. Write down one idea
2. Describe the one core feature
3. Think about what data it needs

**Then:**
- Open a new folder
- Start a new Claude Code session
- Initialize with Protocol files
- Build the first version

> "You have 10 minutes. Don't try to finish. Just start. Get the first screen working."

**Check-in at end:** "Show your neighbor what you started."

---

## What They Just Learned

| Before Session 5 | After Session 5 |
|------------------|-----------------|
| Design and code drift apart | Know when to use Figma Make |
| Only built the gym app | Started their own project |
| Following instructions | Making decisions |
| Rails | Freedom |

---

## Success Criteria

By the end of Session 5:

- [ ] Everyone understands when to use Figma Make vs. Claude Code + Protocol
- [ ] Everyone has started their own project idea
- [ ] Everyone has at least one screen of their own app working locally

---

## Facilitator Notes

**This session is a transition.**

Morning = guided learning on shared project.
Afternoon = applying learning to own ideas.

The energy shifts here. Some people will love the freedom. Some will feel lost without rails.

**For those who feel lost:**

> "Start with something tiny. A form that saves data. A list that displays items. You can make it more complex later."

**Common issues:**

- "I don't have an idea" → Prompt them: "What's something annoying you do at work every day? Build a tool to make it easier."
- "My idea is too big" → Help them scope: "What's the one screen that proves the concept?"
- "Figma Make isn't working" → It requires Figma paid plan or Figma Make subscription. If blocked, skip to manual approach.

**Energy goal:**

End this session with: "I have my own thing now. I know how to build it."

---

**Next:** [Session 6 - Building Shared Context](./SESSION_06.md)
