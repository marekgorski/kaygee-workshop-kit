# Personas — Personalized AI Assistants

**Configure once during setup. Every interaction adapts automatically.**

---

## The Concept

Instead of telling AI how to summarize each time, you train it during setup:
- What matters to you
- What you're watching for
- How you think and decide

Then every briefing, summary, and interaction filters through YOUR lens.

---

## How It Works

### During Onboarding

After selecting your extension (ea/pa/km), AI asks persona questions:

```
"Now let's personalize how I work for you.

I'll ask a few questions about what you care about,
how you make decisions, and what signals matter to you.

This shapes how I summarize, what I surface, and
how I structure information for you."
```

### After Setup

Your persona config lives in `PERSONA.md`. AI reads it every session and:
- Filters information through your priorities
- Surfaces signals you've told it to watch for
- Structures output in your preferred format
- Skips what you've marked as noise

---

## EA Persona Setup

### Questions Asked

**1. Decision Style**
> "When you make decisions, what do you need?
> - Bottom-line recommendation with reasoning
> - Options with trade-offs (you choose)
> - Data first, then implications
> - Risks and downsides highlighted"

**2. Information Diet**
> "What types of information do you need to track?
> - Metrics and numbers
> - Stakeholder sentiment and politics
> - Timeline and deadline pressure
> - Competitive landscape
> - [Add your own]"

**3. Signal Watch**
> "What signals should I always surface when I see them?
>
> Examples: 'budget concerns', 'executive pushback',
> 'timeline risk', 'team morale issues', 'competitor moves'"

**4. Noise Filter**
> "What should I skip or minimize?
>
> Examples: 'technical implementation details',
> 'historical background', 'theoretical frameworks'"

**5. Output Preferences**
> "How do you prefer information structured?
> - Bullet points (scannable)
> - Narrative (context-rich)
> - Tables (comparative)
> - Layered (headline → details)"

---

### Example EA Persona Config

```markdown
# PERSONA.md — Executive Assistant

## Decision Style
Options with trade-offs. I want to see choices, not just recommendations.
Always include the "do nothing" option and its consequences.

## Information Diet
Priority signals (always surface):
- Budget implications
- Timeline risk
- Stakeholder blockers
- Anything from [CEO name] or [key stakeholder]

Track but don't lead with:
- Team capacity
- Technical constraints

## Signal Watch
Surface immediately when detected:
- "budget" + negative sentiment
- "delay" or "slip" on critical path items
- Any mention of [competitor name]
- Escalation requests

## Noise Filter
Minimize or skip:
- Technical architecture details (just tell me if it works)
- Historical context (I know the background)
- Industry trends (unless directly relevant)

## Output Format
Default: Layered (headline first, details available)
For decisions: Table comparing options
For updates: Bullet points, max 5 items
```

---

### How It Changes Behavior

**Without persona:**
```
## Daily Briefing

Here's what happened yesterday...
[Generic summary of all activity]
```

**With persona configured:**
```
## Daily Briefing

### Signals Detected
⚠️ Budget: Engineering flagged Q2 spend tracking 15% over
⚠️ Timeline: Design review pushed to next week (critical path)

### Your Decisions Needed
| Option | Trade-off | Risk |
|--------|-----------|------|
| Approve overspend | Keeps timeline | Budget pressure in Q3 |
| Cut scope | Saves budget | Feature delay |
| Do nothing | Defer decision | Compounds next week |

### Skip Today (noise filtered)
- 3 technical PRs merged (implementation details)
- Team standup notes (no signals detected)
```

---

## PA Persona Setup

### Questions Asked

**1. Planning Style**
> "How do you approach planning?
> - Detailed itineraries (hour by hour)
> - Loose structure (key anchors only)
> - Spontaneous (just logistics, no activities)
> - Research-heavy (options for everything)"

**2. Priority Signals**
> "What factors matter most in recommendations?
> - Cost/value
> - Time efficiency
> - Experience quality
> - Convenience/ease
> - [Add your own]"

**3. Constraints to Track**
> "What constraints should I always factor in?
>
> Examples: 'dietary restrictions', 'mobility needs',
> 'budget ceiling', 'must include kids activities'"

**4. Interest Tags**
> "What are you drawn to? What should I surface?
>
> Examples: 'local food', 'architecture', 'hiking',
> 'live music', 'off-the-beaten-path'"

**5. Avoid Tags**
> "What should I filter out?
>
> Examples: 'tourist traps', 'long queues',
> 'expensive restaurants', 'guided tours'"

---

### Example PA Persona Config

```markdown
# PERSONA.md — Personal Assistant

## Planning Style
Loose structure. Give me anchors (flights, hotels, key reservations)
but leave room for spontaneity. Don't over-schedule.

## Priority Signals
When recommending, weight these:
1. Local/authentic experience (highest)
2. Value for money
3. Avoiding crowds
4. Kid-friendly when traveling with family

## Constraints
Always factor in:
- Vegetarian options required
- No early mornings (nothing before 9am)
- Budget: mid-range ($150-250/night hotels)
- Max 2 hours driving between stops

## Interest Tags (surface these)
- Local food markets
- Street art / murals
- Live music venues
- Coastal walks
- Independent bookshops

## Avoid Tags (filter out)
- Chain restaurants
- Hop-on hop-off tours
- Shopping malls
- Crowded landmarks (unless truly unmissable)
```

---

### How It Changes Behavior

**Without persona:**
```
## Sydney Recommendations

Here are the top attractions:
1. Sydney Opera House
2. Harbour Bridge
3. Bondi Beach
4. Taronga Zoo
[Generic tourist list]
```

**With persona configured:**
```
## Sydney — Filtered for You

### Matches Your Interests
🎵 **The Lansdowne** — Live music venue, local bands, no cover
📚 **Gertrude & Alice** — Independent bookshop café, Bondi
🎨 **Newtown street art** — Self-guided walk, 2 hours

### Skipped (tourist traps)
- Harbour Bridge climb (queues, expensive)
- Darling Harbour (chains, crowds)

### Food Markets
- **Carriageworks Farmers Market** — Sat 8am-1pm ⚠️ Early start
- **Eveleigh Market** — Sat, less crowded, opens 9am ✓

### Constraints Check
✓ All have vegetarian options
✓ Nothing before 9am selected
✓ Within your budget range
```

---

## Persona Evolution

Your persona isn't static. It learns:

### Explicit Updates
Edit `PERSONA.md` directly when preferences change.

### Implicit Signals
When you consistently:
- Skip certain recommendation types → AI notes pattern
- Ask follow-up questions on specific topics → AI infers interest
- Override suggestions → AI adjusts weighting

AI may ask:
> "I noticed you've skipped museum recommendations 3 times.
> Should I add 'museums' to your Avoid list?"

---

## File Structure

```
my-project/
├── CLAUDE.md       # Protocol + technical reference
├── PERSONA.md      # Your preferences (NEW)
├── TODO.md         # Tasks
├── PROGRESS.md     # Session log
├── TASKS/          # Human-only tasks (file-per-task)
└── [extension files]
```

---

## Persona Questions by Extension

| Extension | Key Persona Questions |
|-----------|----------------------|
| **ea** | Decision style, signals to watch, stakeholders to track, noise to filter |
| **pa** | Planning style, interests, constraints, avoid list |
| **km** | Learning style, domains of focus, depth preference, connection patterns |

---

## Privacy Note

Your persona config is just a markdown file in your repo.
- You control what's in it
- You can edit or delete anytime
- It's not sent anywhere except to AI during your sessions
- If you share the repo, consider `.gitignore`-ing PERSONA.md

---

## Quick Setup Example

```
You: [Clone protocol-uno]

AI: "Welcome! Let's set up your assistant.

     First, which extension?
     - ea (Executive Assistant)
     - pa (Personal Assistant)
     - km (Knowledge Manager)"

You: "ea"

AI: "Great. Now let's personalize.

     When you need to make a decision, what helps most?
     1. Bottom-line recommendation
     2. Options with trade-offs
     3. Data first, then implications
     4. Risks highlighted"

You: "2"

AI: "Options with trade-offs. Got it.

     What signals should I always surface?
     (Examples: budget concerns, timeline risk, competitor moves)"

You: "Budget issues, anything from the CEO, timeline slips"

AI: "Noted. What should I minimize or skip?"

You: "Technical details, historical background"

AI: "Perfect. I've created PERSONA.md with your preferences.

     From now on, briefings and summaries will:
     - Present options, not just recommendations
     - Highlight budget, CEO mentions, timeline risks
     - Skip technical implementation details

     Ready to work. Use ..start for your first briefing."
```

---

*Personas v1.3 — May 2026*
