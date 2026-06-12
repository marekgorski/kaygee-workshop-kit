# Session 1: Protocol

**Duration:** 45 minutes
**Problem:** 95% of time re-explaining context to AI
**Solution:** Protocol files — AI reads context automatically
**Output:** Working local app with new feature
**Core message:** This is how you make every AI session build on the last

---

## The Problem

Every time you start a new AI conversation, you're talking to someone who has never met you.

- "What framework are we using?"
- "What's the file structure?"
- "What styling conventions?"
- "What have we already decided?"

You end up copying the same context into every prompt. That's 95% of your time wasted on setup, 5% on actual work.

---

## The Solution

**Protocol files** — markdown files that live in your repo and tell AI what it needs to know.

When AI reads these files automatically, you skip the setup. Your first prompt becomes actual work.

---

## Structure

### Part 1: Setup (10 min)

**Everyone clones the gym starter repo:**

```bash
git clone https://github.com/[facilitator]/gym-starter.git
cd gym-starter
npm install
```

*Note: The facilitator generates this repo before the workshop using `build-this/BUILD_GYM.md` with Claude Code.*

**Verify it works:**

```bash
npm run dev
```

Open `localhost:5173`. You should see a basic workout logging form.

**Check-in:** "Raise your hand when you see the app running."

*Helpers: Assist anyone with clone/install issues.*

---

### Part 2: The Problem Demo (5 min)

**Show what happens WITHOUT protocol:**

Open a fresh Claude chat (not Claude Code). Paste this prompt:

> "Add a rest timer feature to my app."

**Watch what happens:**
- Claude asks clarifying questions
- Or makes wrong assumptions
- Or generates code for the wrong framework

**Narrate:**

> "Claude doesn't know anything about our app. It's guessing. This is the 95% problem — you'd now spend time explaining the project, then get back incomplete code, then explain again."

---

### Part 3: The Solution Demo (10 min)

**Now show Protocol:**

```bash
claude
```

Claude Code starts and automatically reads the protocol files in the repo.

**Same prompt:**

> "Add a rest timer feature. When I finish a set, I should be able to start a countdown timer (default 90 seconds) that alerts me when rest is over."

**Watch what happens:**
- Claude knows the tech stack (React, Vite, Tailwind)
- Claude follows existing patterns
- Claude generates code that fits

**Narrate:**

> "Same prompt. Different result. Claude read CLAUDE.md automatically. It knows the stack, the patterns, the current state. That's Protocol."

---

### Part 4: Everyone Tries (15 min)

**Activity:**

Everyone opens Claude Code in their cloned repo and gives the same prompt:

> "Add a rest timer feature. When I finish a set, I should be able to start a countdown timer (default 90 seconds) that alerts me when rest is over."

**Wait.** Let Claude generate. Let participants accept the changes.

**Test it:**

```bash
npm run dev
```

Refresh the browser. Try the rest timer.

**Check-in:** "Raise your hand when your rest timer works."

---

### Part 5: The Key Moment — Non-Determinism (5 min)

**Stop the room. This is the teaching moment.**

> "Look around. You all cloned the same repo. Gave the same instruction. Look at each other's screens."

Have 3-4 people show their implementations:
- One might have a modal timer
- One might have inline timer
- One might have different styling
- All work, all different

**Script:**

> "This is the nature of the tool. It's non-deterministic. The same input doesn't guarantee the same output.
>
> That's not a bug — it's why we work WITH AI, not delegate TO it.
>
> Protocol reduces variance. Without it, Claude would have guessed the framework too. With Protocol, the variance is in implementation details, not fundamentals.
>
> Think of it like working with a colleague who read the project docs: you give them context, they bring their own perspective. Protocol is how you share that context — so every session builds on the last instead of starting from scratch."

---

## What They Just Learned

| Before Protocol | After Protocol |
|-----------------|----------------|
| 95% setup, 5% work | 5% setup, 95% work |
| "What framework?" | AI reads CLAUDE.md |
| Guessing | Grounded |
| High variance | Reduced variance |

---

## Protocol Files Explained (Quick Reference)

Show them the files they cloned:

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Project context — what is this, tech stack, patterns |
| `TODO.md` | What's done, what's next |
| `DECISIONS.md` | Why we made certain choices |
| `PROGRESS.md` | Session log (they'll use this in Session 2) |

> "You don't need to memorize these. They're here. AI reads them. That's the point."

---

## Success Criteria

By the end of Session 1:

- [ ] Everyone has the app running locally
- [ ] Everyone has added the rest timer feature
- [ ] Everyone understands that Protocol = AI reads context automatically
- [ ] Everyone has seen non-determinism in action

---

## Facilitator Notes

**The non-determinism moment is critical.**

If you skip it, they'll think AI is magic. If you land it, they'll understand why Protocol matters.

**Common issues:**

- `npm install` fails → Usually network or permissions. Try `npm cache clean --force`.
- Claude Code not reading files → Make sure they're in the repo directory, not parent.
- Timer doesn't work → Have them ask Claude to debug: "The timer isn't working. Here's the error: [paste error]"

**Energy goal:**

End this session with: "That was fast. And it worked. I want to do more."

---

**Next:** [Session 2 - Git](./SESSION_02.md)
