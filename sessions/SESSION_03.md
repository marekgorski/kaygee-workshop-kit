# Session 3: Deploy

**Duration:** 45 minutes
**Problem:** Your work lives on your laptop, isolated from everyone
**Solution:** Vercel + GitHub
**Output:** Work that lives where engineers work

---

## The Problem

Your app works on `localhost:5173`. Great.

But:
- It only exists on your laptop
- Engineers can't see what you built
- When you share a Figma link, they rebuild from scratch anyway
- Your context lives in one place (Figma, Confluence), their work lives in another (GitHub)

This is the isolation problem. You're on an island. Engineers are on the mainland. Sharing a link doesn't bridge that gap — they still rebuild.

---

## The Solution

**Vercel + GitHub** — your work lives where engineers work.

- Your code is in GitHub (where engineers already are)
- Vercel auto-deploys when you push
- Anyone can see it running, but more importantly: anyone can **build on it**
- You're not handing off a spec — you're sharing a codebase

---

## Structure

### Part 1: The Problem Demo (5 min)

**Show the limitation:**

> "Open your phone. Try to visit `localhost:5173`."

It doesn't work. localhost is your laptop only.

**But that's not the real problem. Go deeper:**

> "Okay, so you could share a Figma link instead. But what happens when you share a Figma link with engineering?"

Let them answer. Common answers:
- "They rebuild it"
- "They ask a bunch of questions"
- "It takes weeks"

**Narrate:**

> "Right. Sharing a link isn't the problem. The problem is your work lives in a different place than their work. You're in Figma. They're in GitHub. Sharing a Figma link doesn't change that — they still rebuild from scratch.
>
> Today we fix that. Your work goes to GitHub. Same place engineers work."

---

### Part 2: Connect GitHub to Vercel (15 min)

**Everyone does this:**

1. Go to [vercel.com](https://vercel.com)
2. Sign in with GitHub (or create account → sign in with GitHub)
3. Click "Add New Project"
4. Find your `my-gym-tracker` repo in the list
5. Click "Import"

**Vercel detects the framework automatically** (Vite/React).

Click "Deploy".

**Wait.** Watch the build logs. This takes 30-60 seconds.

When it finishes, Vercel shows:
- A preview of your app
- A `.vercel.app` URL

**Check-in:** "Raise your hand when you have a live URL."

---

### Part 3: Click Your Live URL (5 min)

**The moment:**

Click the URL. See your app running on the internet.

**Try it on your phone.** Open the URL. It works.

**Share it.** Post your URL in the workshop chat. Click someone else's.

**Narrate:**

> "This is real. Anyone with this link can see what you built. You just deployed to production — in under a minute."

---

### Part 4: Auto-Deploy (15 min)

**The magic:** Vercel watches your GitHub repo. When you push, it auto-deploys.

**Everyone tests this:**

Make a change in Claude Code:

> "Change the header color to blue."

Push to GitHub:

```bash
git add .
git commit -m "Change header color"
git push
```

Now watch Vercel:
- Go to your Vercel dashboard
- See a new deployment starting automatically
- Wait for it to finish (30-60 seconds)
- Refresh your live URL

**Narrate:**

> "You didn't click anything on Vercel. It watched GitHub and deployed automatically. This is the loop: Code → Push → Live. No waiting for someone else to deploy."

---

### Part 5: The Full Loop (5 min)

**Recap what they've built:**

```
Protocol Files ─→ Claude Code ─→ Working App
                      │
                      ▼
                 Git Commit
                      │
                      ▼
                  GitHub ← Engineers work here too
                      │
                      ▼
                Vercel (auto)
                      │
                      ▼
                 Live URL
```

> "Your code is in GitHub now. Same place engineers work. When they look at your repo, they see working code — not a Figma link to interpret. They can build on what you built. You're not handing off a spec. You're collaborating."

---

## What They Just Learned

| Before | After |
|--------|-------|
| Work lives on your laptop | Work lives in GitHub |
| Share Figma link → engineers rebuild | Share repo → engineers collaborate |
| "Here's the spec, give me a URL" | "Here's the code, let's build together" |
| Isolated from engineering | Same place engineers work |

---

## Success Criteria

By the end of Session 3:

- [ ] Everyone has a live `.vercel.app` URL
- [ ] Everyone has tested auto-deploy (push → see change live)
- [ ] Everyone has shared their URL with someone else
- [ ] Everyone understands the Code → Push → Live loop

---

## Facilitator Notes

**This is the peak moment of the morning.**

They just shipped something to the internet. Make sure they feel it. Celebrate.

**Common issues:**

- Vercel can't find the repo → Make sure they signed into Vercel with the same GitHub account that owns the repo.
- Build fails → Check Vercel logs. Usually a missing dependency or TypeScript error. Have them ask Claude: "My Vercel deploy failed with this error: [paste error]. How do I fix it?"
- Auto-deploy doesn't trigger → Make sure Vercel is connected to the right repo and branch.

**If someone's build keeps failing:**

Don't spend 10 minutes debugging one person's issue. Have a helper assist them while you keep the group moving. They can catch up during the break.

**Energy goal:**

End this session with: "I shipped something to the internet. I can do this."

---

**Next:** [Session 4 - Data](./SESSION_04.md)

---

## BREAK (15 min)

After Session 3, take the morning break. People need to:
- Process what just happened
- Use the bathroom
- Get coffee
- Troubleshoot with helpers if stuck

**Helpers:** Check in with anyone whose deploy didn't work. Get them caught up before Session 4.
