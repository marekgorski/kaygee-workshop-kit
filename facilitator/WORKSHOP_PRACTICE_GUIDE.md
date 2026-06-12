# Workshop Practice Guide

**How to prepare. What will go wrong. How to recover.**

---

## Why Practice Matters

You can read the session plans 10 times and still get surprised on the day.

**The only way to find friction is to feel it yourself.**

When you practice solo:
- You'll hit the same errors participants will hit
- You'll discover which steps take longer than the plan suggests
- You'll build muscle memory for the demos
- You'll know which parts need helpers circulating

**Timeline:** Block 3-4 hours, ideally 3 days before the workshop.

---

## How to Practice

### Step 1: Set Up Like a Participant

**Don't use your existing setup.** Create a fresh environment to simulate the participant experience.

**Option A: Fresh directory**
```bash
mkdir workshop-practice
cd workshop-practice
```

**Option B: GitHub Codespaces** (simulates a clean machine)
- Go to your workshop repo on GitHub
- Click "Code" → "Codespaces" → "Create codespace"
- Work in the browser-based VS Code

**Why:** You've already customized your machine. Participants haven't. Practice on a clean slate.

---

### Step 2: Run Sessions 1-3 (The Critical Path)

These are the highest-friction sessions. If you nail these, the rest flows.

#### Session 1: Protocol (45 min target)

**Practice checklist:**
- [ ] Clone the workshop repo
- [ ] Run `npm install` — **Time this.** How long did it take?
- [ ] Run `npm run dev` — Does it start without errors?
- [ ] Open Claude Code in the repo directory
- [ ] Give the rest timer prompt (from ../sessions/SESSION_01.md)
- [ ] Did Claude generate working code? How long did it take?
- [ ] Test the feature in the browser

**What you'll learn:**
- If npm install takes 5+ min, WiFi might be a bottleneck on the day
- If Claude Code doesn't read CLAUDE.md automatically, you need to troubleshoot
- If the feature doesn't work, you'll practice debugging with Claude

**Debrief:**
- How long did this actually take? (Plan says 45 min)
- Where did you slow down?
- What would a beginner struggle with?

---

#### Session 2: Git (45 min target)

**Practice checklist:**
- [ ] Run `git status` — See the changes from Session 1
- [ ] Run `git add .`
- [ ] Run `git commit -m "Add rest timer"`
- [ ] Create a new repo on GitHub (via `gh repo create` or web UI)
- [ ] Push to GitHub
- [ ] Make another small change
- [ ] Commit and push again

**What you'll learn:**
- If `gh repo create` fails, participants will hit it too → prepare HTTPS fallback
- If `git push` says "Permission denied," you'll practice the SSH vs HTTPS pivot
- How long this sequence actually takes

**Debrief:**
- Did authentication work smoothly? If not, default to HTTPS in your instructions.
- How comfortable are you explaining `git add`, `commit`, `push`?
- Can you explain it without saying "staging area" or "HEAD"? (Beginners don't need that vocabulary.)

---

#### Session 3: Deploy (45 min target)

**Practice checklist:**
- [ ] Go to vercel.com, sign in with GitHub
- [ ] Click "Add New Project"
- [ ] Import your repo from Session 2
- [ ] Deploy (watch the build logs)
- [ ] Visit the live URL — does it work?
- [ ] Make a change locally (e.g., change header color)
- [ ] Commit and push
- [ ] Watch Vercel auto-deploy
- [ ] Refresh the live URL — did the change appear?

**What you'll learn:**
- If the build fails, you'll see the error first (better than 25 people seeing it)
- If auto-deploy doesn't trigger, you'll troubleshoot the GitHub → Vercel connection
- How long this actually takes (often faster than planned, but errors can add 10 min)

**Debrief:**
- How would you explain build errors to a beginner?
- Can you narrate the deploy process while it's happening? (Don't just wait in silence.)
- What would you say when someone's deploy fails?

---

### Step 3: Skim Sessions 4-6 (Lower Priority)

You don't need to practice these as deeply, but **read through them** and note:

- **Session 4 (Data):** Do you have a Supabase account? Can you create a project quickly?
- **Session 5 (Recovering from Failures):** Do you have a simple Figma file to demo Figma Make?
- **Session 6 (Building Shared Context):** Do you understand the collaboration exercise? (Read someone else's Protocol files and continue their work.)

**Why skim, not practice:** Morning sessions (1-3) have the highest technical friction. Afternoon sessions (4-6) have lower risk if you've briefed helpers.

---

## What Will Go Wrong (Guaranteed)

These WILL happen. Practice how you'll respond.

### 1. "npm install is stuck"

**Cause:** Slow WiFi, corporate firewall, antivirus blocking npm.

**Your response (practiced):**
> "If npm install is taking more than 2 minutes, raise your hand. Helpers will come to you. Everyone else, keep going."

**Backup plan:**
- Distribute a pre-downloaded `node_modules` folder via USB stick
- Or: Help them switch to GitHub Codespaces (cloud-based, no local install)

**Practice:** Run `npm install` on a slow network. How long does it actually take?

---

### 2. "git push says Permission denied"

**Cause:** SSH keys not set up.

**Your response (practiced):**
> "If git push failed, try this command:
> ```
> git remote set-url origin https://github.com/USERNAME/REPO.git
> ```
> Then push again. You'll be asked for your GitHub username and password."

**Why this works:** Switches from SSH to HTTPS (easier for beginners).

**Practice:** Deliberately break your SSH setup. Practice the HTTPS fix. Time how long it takes.

---

### 3. "Claude Code says 'Rate limit exceeded'"

**Cause:** 20+ people hitting Claude API simultaneously.

**Your response (practiced):**
> "Claude is rate-limited because we all hit Enter at the same time. Wait 60 seconds and try again. Left side of the room, wait an extra 30 seconds to spread out the load."

**Backup plan:**
- Have pre-generated code snippets ready
- Paste them while narrating: "Here's what Claude would generate..."

**Practice:** Trigger a rate limit (send 10 requests quickly). See the error. Practice your calm response.

---

### 4. "Vercel build failed"

**Cause:** Missing dependency, wrong build command, TypeScript error.

**Your response (practiced):**
> "Let's read the error together. See this line? It says 'Module not found.' That means we forgot to install a package. Let's ask Claude how to fix it."

**Then demonstrate:**
> "Claude, my Vercel deploy failed with this error: [paste error]. How do I fix it?"

**Why this works:** Models real developer behavior. Shows debugging is normal.

**Practice:** Break your Vercel build on purpose. Practice reading the error log. Practice Googling the error.

---

### 5. "I'm running 20 minutes behind"

**Cause:** Demos too long, or a session had too many issues.

**Your decision tree (practiced):**

**Option A: Compress Session 4**
- Skip the "create table in Supabase" walkthrough
- Have helpers assist individually while you keep moving
- Or: Use a pre-created Supabase project everyone shares

**Option B: Combine Sessions 5 & 6**
- Session 5: Demo Figma Make only (10 min), skip hands-on
- Session 6: "Here's a CLAUDE.md template, copy it" (10 min)

**Option C: Cut afternoon break**
- Risky (people need breaks), but saves 10-15 min

**What NOT to cut:**
- ❌ Session 3 (Deploy) — this is the emotional peak
- ❌ Session 6 (Building Shared Context) — the whole workshop leads to this

**Practice:** Time your demos. Are you running over? Where can you trim?

---

## Your Practice Checklist

**Before you call it "practiced":**

- [ ] I've run Sessions 1-3 start to finish
- [ ] I've timed each session (Do they fit in 45 min?)
- [ ] I've hit at least one error and practiced recovering
- [ ] I've tested the WiFi with multiple devices running npm install
- [ ] I know how to switch from SSH to HTTPS for Git
- [ ] I have backup code snippets ready (in case Claude rate-limits)
- [ ] I've tested Vercel deploy end-to-end
- [ ] I've briefed my helpers (or scheduled the briefing)
- [ ] I've sent PREREQUISITES.md to participants (1 week before minimum)

---

## How to Brief Your Helpers

**When:** 1 week before (ideal) or 1 day before (minimum).

**Format:** 30-min call or in-person meeting.

**What they need to know:**

### 1. The Schedule
Show them DAY_SCHEDULE.md.

> "Here's when breaks are. Here's when you'll be most needed (Sessions 2-4)."

### 2. Their Role
> "You're not teaching. You're troubleshooting. When someone looks stuck, go to them. Don't wait for raised hands. Pull them aside, help one-on-one, let me keep the group moving."

### 3. Common Errors & Fixes
Walk through the "What Will Go Wrong" section above.

> "If you see 'Permission denied,' here's the fix..."

### 4. Positioning in the Room
> "During my demos, sit in the back and watch for confused faces.
> During hands-on, move around. Especially the back rows."

### 5. Give Them This Guide
Send them:
- FACILITATOR_GUIDE.md (so they understand the pedagogy)
- FACILITATOR_RUNBOOK.md (especially the "Common Emergencies" section)

### 6. Practice One Scenario
Pick one likely issue (e.g., npm install stuck). Have them walk through the fix with you.

---

## Day-Before Checklist

**The night before, or morning of:**

- [ ] Projector/screen sharing tested
- [ ] WiFi tested with 10+ devices running npm install
- [ ] Helpers briefed and positioned
- [ ] Backup facilitator confirmed (if you get sick)
- [ ] Pre-generated code snippets ready (in a shared doc)
- [ ] Schedule printed or on second monitor
- [ ] Water bottle
- [ ] This guide open on laptop
- [ ] FACILITATOR_RUNBOOK.md open on laptop

---

## The Mental Game

**You will forget something.** That's okay.

**Something will break.** That's okay.

**Someone will ask a question you don't know the answer to.** That's okay.

**Your script:**
> "I don't know off the top of my head. Let's Google it together."

Then:
1. Read the error out loud
2. Google it
3. Show the first Stack Overflow result
4. Try the fix

**This is teaching too.** You're modeling real developer behavior: Googling is normal. Errors are normal. Debugging is normal.

---

## After the Workshop

**While it's fresh (same day or next morning), write down:**

### What took longer than expected?
> "Session 2 took 55 min instead of 45. Why? Git authentication issues."

### What went faster than expected?
> "Session 3 took 30 min. People were energized after lunch."

### What questions came up repeatedly?
> "Everyone asked 'Why do I need Git if I have Claude Code?' Need better framing in Session 1."

### What would you cut next time?
> "Skip the Figma Make demo in Session 5. It confused more than it helped."

### What would you add next time?
> "Add a 5-min 'what we've built so far' recap after lunch. People forgot what they did in the morning."

---

## Share Your Feedback

**This is the first DIY workshop.** Your experience shapes v2 of these materials.

**Send your notes to:** workshops@kayg.ee (or open a GitHub issue on the kaygee-workshop-kit repo)

**What we need:**
- What was unclear in the docs?
- What did you practice that wasn't in the practice guide?
- What emergency happened that wasn't in the runbook?
- What would the next facilitator need to know?

**Your feedback becomes the next facilitator's advantage.**

---

## You're Ready

You've read the guide. You've practiced the sessions. You've briefed your helpers. You've got backup plans.

**The last thing to practice: confidence.**

When something breaks (and it will), your participants will look to you. Not for perfection — for calm.

Your energy sets the room's energy.

If you're stressed, they're stressed.
If you're calm, they're calm.

**Practice saying:**
> "Interesting. Let's figure this out together."

Not:
> "Oh no, this shouldn't be happening."

You've got this.

See you on the other side.

—The KayGee Community

---

*Version 1.0 — January 2026*
*Feedback? workshops@kayg.ee*
