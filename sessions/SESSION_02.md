# Session 2: Git

**Duration:** 45 minutes
**Problem:** Can't track changes, context gets lost
**Solution:** GitHub as source of truth
**Output:** Code in your own GitHub repo

---

## The Problem

You just built something. But:

- What if you break it and want to go back?
- What if you close your laptop and lose the chat history?
- What if someone else needs to continue where you left off?

Right now, your code exists only on your laptop. That's fragile.

---

## The Solution

**GitHub** — version control that tracks every change.

- Every change is saved with a message explaining what you did
- You can go back to any previous version
- Your code lives in the cloud, not just your laptop
- Engineers already work here — now you do too

---

## Structure

### Part 1: The Problem Demo (5 min)

**Show what happens without version control:**

Make a change to your app. Break something on purpose (delete a component, mess up styling).

> "Oops. How do I get back to where I was?"

Options without Git:
- Cmd+Z repeatedly (hope it works)
- Re-generate with AI (might not be the same)
- Panic

**Narrate:**

> "Without version control, you're one mistake away from starting over. Every experienced developer has lost work this way — once. Then they learned Git."

---

### Part 2: Git Basics (15 min)

**Explain the core loop:**

```
Work → Stage → Commit → Push
```

| Step | Command | What It Does |
|------|---------|--------------|
| Work | (you coding) | Make changes |
| Stage | `git add .` | Select what to save |
| Commit | `git commit -m "message"` | Save a snapshot |
| Push | `git push` | Upload to GitHub |

**Everyone does this together:**

First, check what changed:

```bash
git status
```

> "See all those modified files? That's your rest timer feature from Session 1."

Stage everything:

```bash
git add .
```

Commit with a message:

```bash
git commit -m "Add rest timer feature"
```

> "Now you have a checkpoint. If anything breaks, you can come back here."

---

### Part 3: Push to Your Own GitHub (15 min)

**The repo you cloned is read-only.** You need your own copy.

**Option A: GitHub CLI (Recommended)**

```bash
gh repo create my-gym-tracker --public --source=. --push
```

This creates a new repo in your GitHub account, sets it as the remote, and pushes — all in one command.

**Option B: Manual (If gh not installed)**

1. Go to github.com/new
2. Create repo called `my-gym-tracker`
3. Copy the "push an existing repository" commands
4. Run them in your terminal

**Check-in:** "Raise your hand when you can see your code on GitHub."

**Show them what's there:**
- All your files
- The commit message you wrote
- The green "Initial commit" from the original clone

---

### Part 4: Make Another Change & Push (5 min)

**Reinforce the loop:**

Ask Claude Code to make a small change:

> "Change the rest timer default from 90 seconds to 60 seconds."

Now the full loop:

```bash
git add .
git commit -m "Change default rest time to 60 seconds"
git push
```

Refresh GitHub. See the new commit.

**Narrate:**

> "Every change you push is saved. Go back to any version anytime. And now your code lives somewhere permanent — not just your laptop."

---

### Part 5: Update PROGRESS.md (5 min)

**Introduce the habit:**

Protocol files aren't just for AI. They're for you and your team.

Open `PROGRESS.md` and add an entry:

```markdown
## Session: [Today's Date]

### What Changed
- Added rest timer feature
- Changed default rest time to 60 seconds
- Pushed to personal GitHub repo

### What's Next
- Deploy to Vercel (Session 3)
```

Commit and push:

```bash
git add .
git commit -m "Update progress log"
git push
```

> "This is how context survives. When you come back tomorrow, or when a teammate picks up, they read PROGRESS.md and know exactly where things stand."

---

## What They Just Learned

| Before Git | After Git |
|------------|-----------|
| Code only on laptop | Code in the cloud |
| Can't undo mistakes | Every version saved |
| "What did I change?" | Commit history shows everything |
| Solo work | Ready for collaboration |

---

## Git Commands Reference

### The Core Loop (memorize these)

| Command | What It Does |
|---------|--------------|
| `git status` | See what changed |
| `git add .` | Stage all changes |
| `git commit -m "msg"` | Save a snapshot |
| `git push` | Upload to GitHub |

> "You only need these four for 90% of your work."

### When You Need More Context

| Command | What It Does |
|---------|--------------|
| `git log` | See commit history |
| `git diff` | See exact changes (before staging) |
| `git diff <file>` | See changes in specific file |
| `git diff --staged` | See what you're about to commit |

---

## Success Criteria

By the end of Session 2:

- [ ] Everyone has their own GitHub repo with the gym app
- [ ] Everyone has pushed at least two commits
- [ ] Everyone has updated PROGRESS.md
- [ ] Everyone understands the Work → Stage → Commit → Push loop

---

## Facilitator Notes

**Git is intimidating.** Keep it simple.

Don't explain branching, merging, rebasing, or anything beyond the basic loop. That's for later. Today they learn: changes are saved, and they live on GitHub.

**Common issues:**

- `git push` rejected → They might not have set the remote. Use `gh repo create` or check `git remote -v`.
- Authentication failed → They need to log into `gh` or set up SSH keys. Have helpers assist.
- "Everything is red" → That's normal. `git status` shows modified files in red before staging.

**Energy goal:**

End this session with: "My code is safe. I can't lose it now."

---

## Going Deeper: When Things Go Wrong

*This section is reference material for after the workshop. Don't cover it during the 45-minute session.*

### The "Pocket" (git stash)

Sometimes you have uncommitted work but need a clean slate — maybe to pull updates, or because you got yourself into a messy state. Stash hides your changes temporarily.

| Goal | Command |
|------|---------|
| Hide uncommitted work | `git stash` |
| Hide with a name (recommended) | `git stash push -m "description"` |
| See what's stashed | `git stash list` |
| Bring it back | `git stash pop` |

**When to use:**
- You need to `git pull` but have uncommitted changes
- You have "ghosts of sessions past" (changes you're not sure about)
- You want to quickly test something with a clean slate

### Undoing Mistakes

| Goal | Command | ⚠️ Danger |
|------|---------|-----------|
| Unstage (undo `git add`) | `git reset` | Safe |
| Discard changes in one file | `git restore <file>` | Permanent |
| Discard ALL uncommitted changes | `git restore .` | Permanent |

> "If you're not sure, use `git stash` first. You can always get it back with `git stash pop`."

### Common "Oops" Scenarios

**"I committed but meant to include another file"**
```bash
git add forgotten-file.md
git commit --amend --no-edit
```

**"I want to see what I changed before staging"**
```bash
git diff
```

**"I want to see what I'm about to commit"**
```bash
git diff --staged
```

**"I have weird uncommitted changes I don't recognize"**
```bash
git status              # See what files changed
git diff TASKS/         # Look at specific folder
git stash push -m "investigate later" TASKS/  # Hide it for now
```

---

**Next:** [Session 3 - Deploy](./SESSION_03.md)
