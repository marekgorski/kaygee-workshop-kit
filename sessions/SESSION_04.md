# Session 4: Data

**Duration:** 45 minutes
**Problem:** Nothing persists, app forgets everything
**Solution:** Supabase
**Output:** Data that survives refresh

---

## The Problem

Log a workout. Refresh the page.

Gone.

Your app has amnesia. Every time you reload, it forgets everything. Data lives in browser memory only — close the tab, data disappears.

Real apps remember things. Yours doesn't. Yet.

---

## The Solution

**Supabase** — a database you can set up in 5 minutes.

- Free tier is generous (plenty for prototypes)
- Works with any framework
- Has a visual UI to see your data
- No server code needed — works directly from the browser

---

## Structure

### Part 1: The Problem Demo (5 min)

**Everyone does this:**

1. Open your live Vercel URL
2. Log a workout (any exercise, sets, reps, weight)
3. See it appear in the list
4. Refresh the page

**Watch it disappear.**

> "Where did your workout go? Nowhere. It was never saved. It only existed in your browser's memory."

**Narrate:**

> "This is fine for a demo. But if you're validating an idea with real users, they expect their data to persist. Today we fix that."

---

### Part 2: Set Up Supabase (15 min)

**Everyone does this:**

1. Go to [supabase.com](https://supabase.com)
2. Sign up / Sign in (use GitHub if prompted)
3. Click "New Project"
4. Name it `gym-tracker`
5. Set a database password (save this somewhere!)
6. Choose region closest to you
7. Click "Create new project"

**Wait.** Project setup takes 1-2 minutes.

**While waiting, explain:**

> "Supabase gives you a Postgres database — the same thing companies use in production. But you don't need to know SQL or run a server. It handles all of that."

---

### Part 3: Create the Table (10 min)

**In Supabase dashboard:**

1. Go to "Table Editor" (left sidebar)
2. Click "Create a new table"
3. Name it `workouts`
4. Add columns:

| Column Name | Type | Notes |
|-------------|------|-------|
| id | int8 | Primary key (auto-generated) |
| created_at | timestamptz | Default: now() |
| exercise | text | |
| sets | int4 | |
| reps | int4 | |
| weight | float4 | |

5. Click "Save"

**Check-in:** "Raise your hand when you see the `workouts` table in your dashboard."

**Get your connection details:**

1. Go to "Settings" → "API"
2. Copy the "Project URL" (starts with https://...)
3. Copy the "anon public" key

**Keep these handy** — you'll need them in the next step.

---

### Part 4: Connect the App (10 min)

**Ask Claude Code to add Supabase:**

> "Add Supabase to save workouts. Here's my project URL: [paste URL]. Here's my anon key: [paste key]. When I log a workout, save it to the 'workouts' table. When the app loads, fetch all workouts from Supabase."

**Claude will:**
- Install `@supabase/supabase-js`
- Create a Supabase client
- Modify the form to save workouts
- Add a fetch on page load

**Test it:**

```bash
npm run dev
```

1. Log a workout
2. Refresh the page
3. **Data is still there**

**Check-in:** "Raise your hand when your data survives a refresh."

---

### Part 5: Push & Deploy (5 min)

**Complete the loop:**

```bash
git add .
git commit -m "Add Supabase data persistence"
git push
```

Wait for Vercel to auto-deploy.

**But wait — it won't work on Vercel yet.**

The Supabase URL and key are hardcoded. That works locally, but it's not secure for production. Let's fix that.

**Add environment variables in Vercel:**

1. Go to your Vercel project dashboard
2. Settings → Environment Variables
3. Add:
   - `VITE_SUPABASE_URL` = your project URL
   - `VITE_SUPABASE_ANON_KEY` = your anon key
4. Redeploy (or push a small change to trigger auto-deploy)

**Now test the live URL.** Data persists there too.

---

## What They Just Learned

| Before Supabase | After Supabase |
|-----------------|----------------|
| Data disappears on refresh | Data persists |
| Browser memory only | Real database |
| Demo-only app | Production-ready data |
| Can't share data | Data syncs across devices |

---

## The Full Stack

After Session 4, participants have:

```
┌─────────────────────────────────────────────────┐
│ Full Stack:                                     │
│                                                 │
│   Protocol Files → AI understands context       │
│   React App → User interface                    │
│   GitHub → Version control                      │
│   Vercel → Hosting & deployment                 │
│   Supabase → Data persistence                   │
│                                                 │
│   This is a real, deployable product stack.    │
└─────────────────────────────────────────────────┘
```

> "You have everything you need to build, deploy, and persist a real application. No engineer required."

---

## Success Criteria

By the end of Session 4:

- [ ] Everyone has a Supabase project with a `workouts` table
- [ ] Everyone's app saves data to Supabase
- [ ] Everyone's data survives page refresh
- [ ] Everyone's live Vercel URL also persists data

---

## Facilitator Notes

**This session has the most potential for technical issues.**

Supabase setup, API keys, environment variables — lots of places for things to go wrong.

**Common issues:**

- "Data not saving" → Check browser console for errors. Usually the Supabase URL or key is wrong.
- "Works locally but not on Vercel" → Environment variables not set, or named wrong (must be `VITE_` prefix for Vite apps).
- "Permission denied" → Supabase Row Level Security (RLS) is enabled by default. Either disable it for the workshop, or add a policy. For simplicity: in Supabase → Table Editor → workouts → RLS → Disable.

**Helpers:** This is where you earn your keep. Circulate actively.

**If someone is stuck:**

Have them pair with someone whose Supabase is working. They can share the same Supabase project URL/key for now and set up their own later.

**Energy goal:**

End this session with: "My app is real now. It remembers things."

---

**LUNCH BREAK (60 min)**

After Session 4, take lunch.

**Afternoon preview:**
- Session 5: Recovering from Failures
- Session 6: Building Shared Context

**Helpers:** Use lunch to catch up anyone who's behind. By Session 5, everyone should have a working app with data persistence.

---

**Next:** [Session 5 - Recovering from Failures](./SESSION_05.md)
