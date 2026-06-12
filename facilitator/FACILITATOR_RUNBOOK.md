# Facilitator Runbook

**Your reference guide for running a smooth workshop.**

Print this or keep it open on a second screen. Most sessions will run smoothly, but when something goes sideways, this is your playbook.

---

## Pre-Workshop Setup

### Day Before

- [ ] **Test the network:** Can 25+ devices npm install simultaneously? If not, pre-download node_modules for the demo app and distribute via USB stick.
- [ ] **Test the projector:** Can participants see code clearly from the back of the room? Increase font size if needed.
- [ ] **Brief your helpers:** Meet with 2-3 helpers who can pull stuck participants aside. See "Helper Briefing" section below.
- [ ] **Confirm backup facilitator:** Make sure your backup knows where materials are (see "Backup Facilitator" section).
- [ ] **Pre-create repos (optional):** If GitHub is likely to be blocked, create template repos participants can fork.
- [ ] **Load demo app:** Have your Session 1 demo app ready to go (don't build it live for the first time).

### Day Of (30 min before start)

- [ ] Verify projector/screen sharing works
- [ ] Connect to WiFi and test npm install speed
- [ ] Open all the tools you'll demo (Claude Code, VS Code, GitHub, Vercel)
- [ ] Have the schedule visible (printed or on a side screen)
- [ ] Put your phone on silent

---

## Common Emergencies & Fixes

### 🚨 Emergency: Network Is Down

**Symptoms:** npm install times out, GitHub won't load, Vercel can't deploy

**Immediate fix:**
1. Switch to phone hotspot (warn participants this is temporary)
2. If multiple people hotspot, distribute load (5-6 people per hotspot max)
3. Skip Vercel deployments temporarily, focus on local builds
4. Resume deploys when network is back

**Long-term fix:**
- Pre-download node_modules for common packages
- Use offline-capable demos (no API calls)

---

### 🚨 Emergency: 5+ People Can't Install Node/Git

**Symptoms:** "I don't have admin privileges" or "Installation failed"

**Immediate fix:**
1. Pair them with someone whose setup works (peer programming)
2. Have them watch for now, catch up during lunch with helper assistance
3. If more than 30% of the room is affected, pause and address it as a group

**Prevention:**
- Send PREREQUISITES.md 1 week early with IT contact info
- Require a "setup verification" email 2 days before workshop

---

### 🚨 Emergency: GitHub SSH Keys Aren't Working

**Symptoms:** `git push` says "Permission denied (publickey)"

**Immediate fix:**
1. Switch everyone to HTTPS authentication instead:
   ```bash
   git remote set-url origin https://github.com/USERNAME/REPO.git
   ```
2. They'll be prompted for username/password (or personal access token)

**Long-term fix:**
- Default to HTTPS in all instructions (easier for beginners)
- Make SSH optional for advanced users

---

### 🚨 Emergency: Vercel Won't Deploy (Build Fails)

**Symptoms:** Vercel logs show "Command failed" or "Module not found"

**Common causes:**
1. Missing dependency in package.json → Add it and push again
2. Build command is wrong → Check Vercel settings, should be `npm run build`
3. Environment variable missing → Add it in Vercel dashboard under Settings → Environment Variables

**Immediate fix:**
- Show the error log on screen
- Read it out loud together
- Google the error if needed
- Ask Claude Code: "This Vercel deploy failed with [error]. How do I fix it?"

---

### 🚨 Emergency: Claude Code Rate Limited or API Error

**Symptoms:** "Too many requests" error, "Rate limit exceeded", or Claude stops responding

**This will happen** with 25 people hitting Claude simultaneously. Plan for it.

**Immediate fix:**
1. Have participants wait 60 seconds and retry
2. Stagger requests: "Everyone on the left side of the room, wait 30 seconds before hitting Enter"
3. If persistent, switch to Claude Web Chat ([claude.ai](https://claude.ai)) for the demo portion
4. Worst case: Pre-generate the code snippets and have participants copy-paste while you narrate

**Prevention:**
- Don't have everyone hit "Enter" at the same time
- Build in natural delays: "Before you run this, let me explain what it does..."
- Have the backup code snippets ready in a shared doc

---

### 🚨 Emergency: You're Running 20+ Minutes Behind

**Symptoms:** It's 10:45 and you're still in Session 2

**Triage options:**

**Option 1: Compress Session 4**
- Skip the "build a new app" part
- Just add one small feature to the existing app
- Skip the deploy step (they already did it in Session 3)

**Option 2: Combine Sessions 5 & 6**
- Session 5: Demo only (10 min), skip hands-on breaking
- Session 6: "Here's a CLAUDE.md template, copy it" (10 min)
- Total: 20 min saved

**Option 3: Cut the afternoon break**
- Risky (people need breaks), but saves 15 min

**What NOT to cut:**
- ❌ Session 3 (deployment) — this is the peak moment
- ❌ Session 6 (shared context) — the whole workshop builds to this

---

### 🚨 Emergency: Someone's Laptop Is Completely Broken

**Symptoms:** Can't install anything, admin blocked, hardware failure

**Immediate fix:**
1. **Try GitHub Codespaces first** - they can work entirely in a browser
   - Go to the workshop repo on GitHub
   - Click the green "Code" button → "Codespaces" tab → "Create codespace"
   - A full VS Code environment opens in the browser with Node.js, Git, and npm pre-installed
   - Takes about 2 minutes to spin up
   - Free tier gives 60 hours/month (plenty for the workshop)
2. If Codespaces isn't an option, pair them with a neighbor (two people, one laptop)
3. Have them take notes and watch as last resort
4. During lunch, try to get a loaner laptop from IT

**Do NOT:**
- Spend 30 minutes debugging their specific machine while 24 people wait
- Let them leave (they'll feel defeated)

---

## Session-Specific Troubleshooting

### Session 1: The Demo

**If Claude Code doesn't respond:**
- Restart the app
- Check internet connection
- Have a pre-recorded backup demo video ready

**If the demo deploy fails:**
- Keep going. Say: "This is actually useful — you'll see errors in real projects. We'll debug this together in Session 5."

---

### Session 2: First Build

**If npm install is taking 10+ minutes:**
- Don't wait for everyone. Help the slow ones individually while others move on.
- Consider: Did someone's antivirus block npm? Corporate firewall issue?

**If 50%+ of the room is stuck:**
- Stop. Address the common issue as a group.
- Likely causes: Wrong directory, typo in command, npm not installed.

---

### Session 3: Deployment Loop

**If git push fails for many people:**
- Check: Are they authenticated with GitHub?
- Switch to HTTPS if SSH isn't working.
- Walk through the web UI flow as a backup.

**If Vercel builds are taking 5+ minutes:**
- Network congestion. Have people wait, move on to the next step, and check back later.

---

### Session 4: Second Build

**If people finish way too fast (10 min instead of 25):**
- Give them a second challenge: "Add another feature."
- Or: "Help someone next to you who's stuck."

**If people are stuck and calling you constantly:**
- You're solving too many problems yourself. Redirect:
  - "What does the error say?"
  - "Try asking Claude to fix it."
  - "Check with your neighbor."

---

### Session 5: Recovering from Failures

**If the merge conflict demo is too confusing:**
- Skip it. Focus on syntax errors and deploy failures only.
- Say: "Merge conflicts are rare in solo projects. We'll cover them later if needed."

**If participants are afraid to break things:**
- Normalize it: "Every developer breaks things. The skill is knowing how to recover."
- Demo the recovery yourself first — break something, show the fix live.

**If Figma Make output doesn't match expectations:**
- This IS the teaching moment: "Tools generate a starting point, not a finished product."
- Show how protocol files help Claude fix the gaps.

---

### Session 6: Building Shared Context

**If people don't understand why CLAUDE.md matters:**
- Emphasize: "Close your laptop, come back tomorrow. Claude forgets. This file reminds it."

**If Claude Code still ignores the CLAUDE.md:**
- Clarify: "Claude can see the file, but it won't always follow it perfectly. The file is a guide, not a guarantee."

**If team formation is chaotic:**
- Set a timer: "You have 5 minutes to form teams."
- Have a "solo track" for people who don't find a team.

**If teammates can't work on the same project:**
- This is the protocol's moment: "CLAUDE.md IS the shared context. One person writes it, everyone benefits."
- Show how TODO.md (AI tasks) and TASKS/ folder (human tasks) divides work clearly.

---

## Participant Personas & How to Help Them

### The Speedster
- Finishes every exercise in 5 minutes
- Gets bored, pulls out their phone

**How to help:**
- Give them bonus challenges
- Ask them to help neighbors
- Say: "Try adding [advanced feature] to your app"

---

### The Struggler
- Falls behind in Session 2 and never catches up
- Quietly disengages

**How to help:**
- Assign a helper to sit with them during a break
- Give them a pre-built version of the app to catch up
- Pair them with the Speedster

---

### The Skeptic
- "Why do we need AI for this? I could code it myself faster."

**How to help:**
- Validate their skills: "You probably could. But in a hackathon, speed matters. Claude lets you prototype 10 ideas instead of 1."
- Show them a complex example they couldn't build in 4 hours solo.

---

### The Lost
- Doesn't know what a terminal is, never used Git before

**How to help:**
- Be patient. Narrate every step slowly.
- Pair them with someone more experienced.
- After Session 2, check in: "Are you following, or should we slow down?"

---

## What to Do When You're Stuck

**As the facilitator, you will encounter errors you can't solve in real-time.**

**Script:**

> "I don't know the answer off the top of my head. Let's Google it together."

Then:
1. Read the error out loud
2. Google it
3. Show the first Stack Overflow result
4. Try the fix

**Why this works:**
- Models real developer behavior (Googling is normal)
- Shows vulnerability (you don't know everything, and that's okay)
- Teaches participants to solve their own problems

---

## Energy Management

**Workshops are exhausting. Here's how to sustain energy:**

### For You (Facilitator)
- Drink water between sessions
- Stand during demos (sitting makes you sleepy)
- Take the breaks seriously (don't work through them)
- If you're losing your voice, use the mic

### For Participants
- Call breaks on time
- If energy is low, do a 1-minute stand-and-stretch
- Celebrate small wins: "Everyone who deployed, give yourself a hand!"

---

## Post-Workshop Debrief

**After the workshop, while it's fresh, write down:**

1. What took way longer than expected?
2. What went faster than expected?
3. What questions came up repeatedly?
4. What would you cut next time?
5. What would you add next time?

**Share this with the next facilitator (or use it to revise the sessions).**

---

## Red Flags to Watch For

🚩 **More than 5 people leave during lunch and don't come back**  
→ Morning was too hard or too boring. Adjust pacing.

🚩 **People are on their phones during hands-on sessions**  
→ They're either done (give them more to do) or lost (check in with them).

🚩 **You're consistently 10+ min behind schedule**  
→ Your demos are too long. Practice beforehand and time yourself.

🚩 **Participants ask "When do we get to build something real?"**  
→ They don't see the value yet. Emphasize: "These small apps teach the loop. The hackathon is where you build something real."

🚩 **No one asks questions**  
→ Either they're too intimidated, or they're lost. Prompt: "What's confusing so far?"

---

## Backup Facilitator

**What if you get sick the night before?**

Identify a backup facilitator before the workshop. Make sure they have:

- [ ] Access to all workshop materials (this repo, slides, demo apps)
- [ ] Login credentials for the demo Vercel/GitHub accounts (if using shared ones)
- [ ] A copy of this runbook
- [ ] Your phone number (in case they have questions)

**Backup facilitator prep:**

If you're the backup, spend 30 minutes reviewing:
1. DAY_SCHEDULE.md — know the flow
2. ../sessions/SESSION_01.md through SESSION_03.md — the critical morning sessions
3. This runbook — especially the "Common Emergencies" section

**Worst case fallback:**

If no backup is available and you can't facilitate:
- Postpone the workshop
- Or: Have participants work through the session files self-paced with helper support only

---

## Helper Briefing

**You need 2-3 helpers for a 25-person workshop.** Brief them the day before or morning of.

### Helper Responsibilities

1. **Roam during hands-on sessions** — don't wait for raised hands, look for confused faces
2. **Pull stuck participants aside** — help them one-on-one without disrupting the group
3. **Watch for stragglers** — if someone falls behind in Session 2, they need extra attention
4. **Monitor the chat/Slack** — if using a backchannel, answer questions there

### What Helpers Should Know

- The schedule (when are breaks, when can they catch people up)
- The common errors and fixes (see "Common Emergencies" above)
- The verification commands (`node --version`, `git --version`, etc.)
- That it's okay to say "I don't know, let's ask the facilitator"

### Helper Positioning

- **During demos:** Sit in the back, watch for people who look lost
- **During hands-on:** Move around the room, especially the back rows
- **During breaks:** Be available for 1-on-1 help, but also take breaks yourself

### Quick Helper Checklist

- [ ] Know the schedule
- [ ] Have this runbook open on your laptop
- [ ] Know where the facilitator is (in case you need to escalate)
- [ ] Have your own setup working (so you can demo fixes)

---

## Final Checklist

Before you walk into the room:

- [ ] Printed schedule (or on second monitor)
- [ ] Demo app ready to go
- [ ] Helpers briefed and positioned
- [ ] Backup facilitator confirmed
- [ ] Backup plan if network fails
- [ ] Water bottle
- [ ] This runbook

**You've got this. Good luck.**
