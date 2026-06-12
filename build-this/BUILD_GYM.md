# BUILD_GYM.md

**Instructions for AI: Build a gym workout tracker with protocol files.**

When a user opens this file in an AI coding tool and asks you to follow it, execute these instructions step by step.

---

## AI Compatibility Note

This file is designed for **Claude Code**, but works with other AI coding tools:

- **Figma Make / Lovable / Bolt:** These are browser-based — skip terminal commands (npm, git) and focus on generating the React components and files. The user will handle deployment through your built-in systems.
- **Cursor / Windsurf / Continue:** These work like Claude Code — follow all steps as written.
- **Other AI tools:** Adapt as needed. The core output is: a working React app + protocol markdown files (CLAUDE.md, TODO.md, etc.). Generate what your environment supports.

The goal is the same everywhere: **build WITH the user, not FOR them**, and create protocol files for persistent AI memory.

---

## Your Role

You are guiding someone through building their first app with AI. They may be:
- A solo learner trying this for the first time
- A workshop participant following along with a group

Either way, your job is to:
1. Explain the permission model BEFORE running any commands
2. Check they have the prerequisites
3. Build the app WITH them (not FOR them)
4. Create protocol files so future sessions have context

**Important:** This is a teaching moment. When you ask for permission to run commands, explain briefly what the command does. They're learning how to work with you.

---

## Step 1: Explain the Permission Model

**Before running ANY commands**, explain how this works and offer a clear choice:

> "Before we start building, here's how this works: I'll suggest commands to run, and you'll see them before they execute. Read what I'm proposing, then approve if it looks right. This is called 'gradual disclosure of access' — you stay in control, I explain what I want to do, you decide.
>
> Ready to build the gym app?
> 1. Yes, let's go
> 2. I have questions first
> 3. Not yet"

Wait for their choice. If they choose 2, answer their questions. If they choose 3, wait until they're ready. Only proceed to Step 2 when they confirm.

---

## Step 2: Check Prerequisites

Now verify they have the required tools. They'll see their first permission prompts here — they now understand why.

**Run these checks:**

```bash
node --version
```

```bash
git --version
```

**If node is missing:** Stop and say:
> "I notice Node.js isn't installed. You'll need it to build this app. Go to https://nodejs.org, download the LTS version, install it, then come back and we'll continue."

**If git is missing:** Stop and say:
> "I notice Git isn't installed. You'll need it later to save your work. Go to https://git-scm.com/downloads, install it, then come back."

**If both pass:** Continue to Step 3.

---

## Step 3: Check the Folder

**If this folder contains files other than BUILD_GYM.md:**

Say:
> "I see other files in this folder. For a clean start, let's either:
> 1. Move BUILD_GYM.md to an empty folder and start there, or
> 2. Clear this folder first
>
> Which would you prefer?"

Wait for their choice and guide accordingly.

**If the folder only has BUILD_GYM.md:**

Say:
> "Perfect, this folder is ready. First, I'll move this instruction file to the parent folder so Vite has an empty directory to work with. You can delete it later or keep it as reference."

Then move BUILD_GYM.md out:
```bash
mv BUILD_GYM.md ../BUILD_GYM_backup.md
```

---

## Step 4: Create the App

Now build the React app with Vite.

Say:
> "I'm going to create a React app with TypeScript. This command scaffolds the project structure."

Run:
```bash
npm create vite@latest . -- --template react-ts
```

Then say:
> "Now I'll install the dependencies. This downloads the packages the app needs."

Run:
```bash
npm install
```

Then say:
> "Finally, I'll add Tailwind CSS for styling. It makes the app look clean without writing much CSS."

Run:
```bash
npm install -D tailwindcss@3 postcss autoprefixer
npx tailwindcss init -p
```

---

## Step 5: Configure Tailwind

Update the Tailwind config to scan our files.

**Write to `tailwind.config.js`:**
```js
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

**Replace `src/index.css` with:**
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Say:
> "Tailwind is configured. Now let's build the actual workout form."

---

## Step 6: Create the Workout Form

Create the components folder and the main form component.

```bash
mkdir -p src/components
```

**Write to `src/components/WorkoutForm.tsx`:**
```tsx
import { useState } from 'react'

interface Workout {
  id: number
  exercise: string
  sets: number
  reps: number
  weight: number
  unit: 'kg' | 'lbs'
}

export function WorkoutForm() {
  const [workouts, setWorkouts] = useState<Workout[]>([])
  const [exercise, setExercise] = useState('')
  const [sets, setSets] = useState(3)
  const [reps, setReps] = useState(10)
  const [weight, setWeight] = useState(0)
  const [unit, setUnit] = useState<'kg' | 'lbs'>('kg')

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault()
    if (!exercise.trim()) return

    const newWorkout: Workout = {
      id: Date.now(),
      exercise: exercise.trim(),
      sets,
      reps,
      weight,
      unit,
    }

    setWorkouts([...workouts, newWorkout])
    setExercise('')
  }

  return (
    <div className="max-w-md mx-auto p-6">
      <h1 className="text-2xl font-bold mb-6">Log Workout</h1>

      <form onSubmit={handleSubmit} className="space-y-4 mb-8">
        <div>
          <label className="block text-sm font-medium mb-1">Exercise</label>
          <input
            type="text"
            value={exercise}
            onChange={(e) => setExercise(e.target.value)}
            placeholder="e.g., Bench Press"
            className="w-full px-3 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
          />
        </div>

        <div className="grid grid-cols-3 gap-4">
          <div>
            <label className="block text-sm font-medium mb-1">Sets</label>
            <input
              type="number"
              value={sets}
              onChange={(e) => setSets(Number(e.target.value))}
              min={1}
              className="w-full px-3 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
          </div>
          <div>
            <label className="block text-sm font-medium mb-1">Reps</label>
            <input
              type="number"
              value={reps}
              onChange={(e) => setReps(Number(e.target.value))}
              min={1}
              className="w-full px-3 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
          </div>
          <div>
            <label className="block text-sm font-medium mb-1">Weight</label>
            <input
              type="number"
              value={weight}
              onChange={(e) => setWeight(Number(e.target.value))}
              min={0}
              className="w-full px-3 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
            />
          </div>
        </div>

        <div>
          <label className="block text-sm font-medium mb-1">Unit</label>
          <div className="flex gap-4">
            <label className="flex items-center">
              <input
                type="radio"
                value="kg"
                checked={unit === 'kg'}
                onChange={() => setUnit('kg')}
                className="mr-2"
              />
              kg
            </label>
            <label className="flex items-center">
              <input
                type="radio"
                value="lbs"
                checked={unit === 'lbs'}
                onChange={() => setUnit('lbs')}
                className="mr-2"
              />
              lbs
            </label>
          </div>
        </div>

        <button
          type="submit"
          className="w-full bg-blue-500 text-white py-2 px-4 rounded-lg hover:bg-blue-600 transition-colors"
        >
          Log Workout
        </button>
      </form>

      {workouts.length > 0 && (
        <div>
          <h2 className="text-xl font-semibold mb-4">Today's Workouts</h2>
          <ul className="space-y-2">
            {workouts.map((w) => (
              <li key={w.id} className="p-3 bg-gray-100 rounded-lg">
                <span className="font-medium">{w.exercise}</span>
                <span className="text-gray-600 ml-2">
                  {w.sets} × {w.reps} @ {w.weight}{w.unit}
                </span>
              </li>
            ))}
          </ul>
        </div>
      )}
    </div>
  )
}
```

---

## Step 7: Update App.tsx

**Replace `src/App.tsx` with:**
```tsx
import { WorkoutForm } from './components/WorkoutForm'

function App() {
  return (
    <div className="min-h-screen bg-gray-50 py-8">
      <WorkoutForm />
    </div>
  )
}

export default App
```

Also delete the default App.css that Vite created (we're using Tailwind instead):
```bash
rm src/App.css
```

---

## Step 8: Create Protocol Files

Now create the files that give AI persistent context. Explain as you create:

> "Now I'll create protocol files. These are markdown files that I (and any AI) will read at the start of each session. They're how you give AI persistent memory."

**Write to `CLAUDE.md`:**
```markdown
# Gym Workout Tracker

## What This Is

A simple workout logging app. Users can log exercises with sets, reps, and weight.

## Tech Stack

- React 18 + TypeScript
- Vite for bundling
- Tailwind CSS for styling
- No backend yet (data lives in component state)

## File Structure

- `src/App.tsx` — Main app, renders WorkoutForm
- `src/components/WorkoutForm.tsx` — Form for logging workouts

## Patterns

- Functional components with hooks
- Tailwind for all styling (no CSS files except index.css for imports)
- TypeScript strict mode

## Current State

- Basic form works
- Data doesn't persist (refreshing loses everything)
- No rest timer yet
```

**Write to `TODO.md`:**
```markdown
# Gym Tracker TODO

## Task Ownership

| Location | Owner |
|----------|-------|
| **TODO.md** | AI tasks |
| **TASKS/** | Human tasks (account setup, API keys, decisions) |

## Done

- [x] Basic workout form
  - AC: Form captures exercise, sets, reps, weight
  - AC: Unit toggle works (kg/lbs)
- [x] Display logged workouts
  - AC: Workouts appear in list after logging

## Next

- [ ] Add rest timer between sets
  - AC: Timer starts at 90 seconds by default
  - AC: Countdown displays remaining time
  - AC: Alert sounds when rest is complete
  - AC: User can dismiss timer early

- [ ] Add workout history view
  - AC: Shows past workouts grouped by date
  - AC: Displays total volume per session

## Future (Out of Scope for Now)

- [ ] User authentication (after Supabase setup)
- [ ] Multiple workout templates
- [ ] Progress charts
```

**Create `TASKS/` folder:**
```bash
mkdir -p TASKS
```

When Claude can't complete a task (needs account setup, API keys, human judgment), it creates a task file here. Example:

```markdown
# TASKS/setup-supabase.md

**Status:** Blocked
**Why human:** Needs account creation and API keys

## Task
Set up Supabase account for data persistence.

## Acceptance Criteria
- [ ] Supabase project created
- [ ] API keys added to .env

## Completed
- [x] Initial project setup — Session 1
  - Ran BUILD_GYM.md to create gym tracker
```
```

**Write to `PROGRESS.md`:**
```markdown
# Progress Log

## Session 1: Initial Build

### What Happened

Built the gym tracker app from scratch using BUILD_GYM.md.

### What's Working

- Workout form (exercise, sets, reps, weight)
- Unit toggle (kg/lbs)
- Display logged workouts

### What's Not Working Yet

- Data doesn't persist (refreshing loses everything)
- No rest timer

### Next

Add rest timer feature.
```

**Write to `DECISIONS.md`:**
```markdown
# Decisions

## DEC-001: Tech Stack — React + Vite + Tailwind

**Date:** Today
**Status:** Active

**Context:** Choosing a tech stack for a simple workout tracker.

**Decision:** React 18 + TypeScript + Vite + Tailwind CSS

**Rationale:**
- React: Familiar to most, good component model
- TypeScript: Catches errors early
- Vite: Fast dev server, simple setup
- Tailwind: Rapid styling without fighting CSS

## DEC-002: No Backend Yet

**Date:** Today
**Status:** Active

**Context:** Do we need data persistence from the start?

**Decision:** No. Start with in-memory state.

**Rationale:**
- Keeps initial setup simple
- Can add Supabase later when needed
- Lets us focus on the UI first
```

---

## Step 9: Verify It Works

Say:
> "Let's test the app. I'll start the dev server."

Run:
```bash
npm run dev
```

Then say:
> "Open http://localhost:5173 in your browser. You should see a 'Log Workout' form. Try adding a workout — enter an exercise name, sets, reps, weight, and click 'Log Workout'. It should appear in a list below."

Wait for them to confirm it works.

Then say:
> "Now let's verify the build works (you'll need this for deployment later)."

Stop the dev server (Ctrl+C) and run:
```bash
npm run build
```

If it succeeds, say:
> "Build passed. You're ready to deploy to Vercel when you get to Session 3."

---

## Step 10: Explain What They Built

End with this teaching moment:

> "You just built an app WITH AI, not by delegating TO it.
>
> Notice what happened:
> - You approved each step
> - You understood what was being created
> - You now have protocol files (CLAUDE.md, TODO.md, etc.)
>
> Those protocol files are the key. Next time you open Claude Code in this folder, I'll read them and know exactly what this project is, what's done, and what's next.
>
> That's how you give AI persistent memory. That's the pattern."

---

## Step 11: What's Next

**If they're doing the workshop:**
> "Session 1 is complete. Next is Session 2: Git — we'll push this to GitHub so your work is saved and versioned."

**If they're solo:**
> "Want to try adding a feature? Say: 'Add a rest timer feature. When I finish a set, I should be able to start a countdown timer (default 90 seconds) that alerts me when rest is over.'
>
> I'll read CLAUDE.md, understand the project, and build on what exists. That's the workflow."

---

## End of BUILD_GYM.md

The instruction file was moved to your parent folder as `BUILD_GYM_backup.md`. You can delete it or keep it as reference.

---

## What You Learned (Simplified Protocol)

This workshop taught you the **foundations**:
- Files as AI memory (CLAUDE.md, TODO.md, PROGRESS.md, TASKS/)
- Task ownership by location (TODO.md = AI, TASKS/ = human)
- Acceptance criteria (testable "done" conditions)
- Automatic progress saving (AI updates files after each interaction)

### Ready for More?

The full **duo protocol** adds:
- **Architect/Builder roles** — Separate planning from implementation
- **Token budget management** — Keep context lean
- **Multi-tool handoffs** — Coordinate between Claude Code, Figma Make, Cursor
- **Save Game Rule** — Micro-commits to prevent work loss
- **Design Phase Rule** — Mockups before specs

See: [protocol-duo](https://github.com/marekgorski/protocol-duo) for the complete workflow.

---

*Part of the KayGee Workshop Kit — https://kayg.ee*
