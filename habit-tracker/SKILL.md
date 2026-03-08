---
name: habit-tracker
version: 1.0.0
description: >
  Daily habit tracking skill for solopreneurs. Use when tracking recurring
  behaviors (writing, exercise, outreach, deep work), checking in on streaks,
  logging habit completions, reviewing weekly averages, or setting up automated
  habit accountability via heartbeat or cron. Distinct from goal-tracker:
  habits are daily behaviors; goals are quarterly outcomes.
tags: [habits, productivity, accountability, daily-review, streaks, solopreneur]
platforms: [openclaw, cursor, windsurf, generic]
category: productivity
author: The Agent Ledger (theagentledger.com)
license: CC-BY-NC-4.0
---

# Habit Tracker

**By [The Agent Ledger](https://theagentledger.com) — AI workflows for solopreneurs.**

> Goals tell you where you're going. Habits determine whether you actually get there.

This skill gives your agent a persistent, structured framework for tracking daily habits — logging completions, maintaining streaks, calculating weekly averages, and surfacing accountability nudges before behaviors erode.

---

## What This Skill Does

- Logs daily habit completions in a structured state file
- Tracks streaks and calculates 7-day / 30-day completion rates
- Surfaces overdue habits during heartbeat checks
- Generates weekly habit reports with trend analysis
- Integrates with goal-tracker (habits → outcomes), solopreneur-assistant (weekly review), and financial-tracker (revenue-correlated habits)

---

## Quick Setup (5 Minutes)

### Step 1: Add to AGENTS.md

Paste this into your `AGENTS.md` standing instructions:

```
## Habit Tracking
- State file: `habit-state.json` (habit definitions + daily log)
- Log completions when I report them (e.g., "did my writing today", "workout done")
- During heartbeat: check for habits not yet logged today; surface any that are overdue by >2 hours past their usual time
- On Sundays: generate a weekly habit report automatically
- Never nag more than once per session per habit
- Use the habit-tracker skill for all habit-related commands
```

### Step 2: Create Your State File

Ask your agent: **"Set up my habit tracker with the following habits: [list them]"**

The agent will create `habit-state.json`:

```json
{
  "habits": [
    {
      "id": "writing",
      "name": "Daily Writing",
      "description": "500+ words of focused writing",
      "target_days": ["mon","tue","wed","thu","fri"],
      "usual_time": "08:00",
      "category": "creative",
      "linked_goal": "publish-newsletter-weekly"
    },
    {
      "id": "exercise",
      "name": "Exercise",
      "description": "30+ min movement",
      "target_days": ["mon","tue","wed","thu","fri","sat","sun"],
      "usual_time": "07:00",
      "category": "health",
      "linked_goal": null
    },
    {
      "id": "outreach",
      "name": "1 Outreach",
      "description": "Send 1 meaningful outreach message (partnership, collab, sales)",
      "target_days": ["mon","tue","wed","thu","fri"],
      "usual_time": "10:00",
      "category": "business",
      "linked_goal": "grow-revenue-q2"
    }
  ],
  "log": {},
  "streaks": {},
  "last_weekly_report": null
}
```

**Fields:**
| Field | Description |
|---|---|
| `id` | Unique slug (used in commands) |
| `name` | Human-readable label |
| `description` | What "done" looks like (be specific) |
| `target_days` | Days this habit applies |
| `usual_time` | Expected completion time (for overdue detection) |
| `category` | creative / health / business / learning / other |
| `linked_goal` | Optional goal-tracker goal id |

---

## Daily Log Format

Completions are stored in `habit-state.json` under `"log"` by date:

```json
"log": {
  "2026-03-08": {
    "writing": { "done": true, "note": "wrote intro for issue #4", "logged_at": "08:42" },
    "exercise": { "done": true, "note": "30 min run", "logged_at": "07:15" },
    "outreach": { "done": false, "note": "skipped — travel day" }
  }
}
```

**Note field:** Optional but valuable. The agent captures what you actually did — useful for weekly review and for correlating habits with outcomes.

---

## Usage Patterns

### Log a Completion
> "Writing done — finished the draft introduction."
> "Mark exercise complete, 45 min bike ride."
> "Outreach done — emailed [name redacted] about collab."

Agent response format:
```
✅ Writing logged (08:42)
Streak: 5 days 🔥
7-day rate: 86%
```

### Log a Skip (with Context)
> "Skipping outreach today — traveling."
> "No exercise — sick day."

Agent logs `done: false` with your note. Skips with context don't break streaks on non-target days.

### Check Today's Status
> "Habit status for today."

Agent response format:
```
📋 Habit Status — Sunday, March 8

✅ Exercise (07:15) — 30 min run
✅ Writing (08:42) — draft intro
⏳ Outreach — not logged yet (target: by 10:00)

Today: 2/3 done (67%)
```

### Check Your Streaks
> "What are my current streaks?"

Agent response format:
```
🔥 Current Streaks

Writing:   ████████░ 8 days
Exercise:  ████░░░░░ 4 days
Outreach:  ██░░░░░░░ 2 days

Longest ever: Writing — 23 days (Jan 2026)
```

### Weekly Habit Report
> "Give me my weekly habit report."

Or triggered automatically on Sunday by heartbeat. See [Weekly Report Format](#weekly-report-format) below.

### Add a New Habit
> "Add a new habit: 'Read 20 pages' every day, target time 9pm, category learning."

### Pause/Resume a Habit
> "Pause the outreach habit for this week — I'm on vacation."
> "Resume outreach habit starting Monday."

Agent sets `"paused_until": "2026-03-15"` in the habit definition.

### Edit a Habit
> "Change writing habit to target Mon/Wed/Fri only."
> "Update exercise description to '20+ min minimum.'"

---

## Weekly Report Format

Generated every Sunday (or on-demand). Agent formats as:

```
📊 Weekly Habit Report — Week of March 2–8, 2026

COMPLETION RATES
Writing:   ████████░░  5/5 (100%) ↑ from 80%
Exercise:  ██████░░░░  5/7 (71%)  ↓ from 86%
Outreach:  ████░░░░░░  3/5 (60%)  → same

STREAKS (as of Sunday)
Writing:   8 days 🔥
Exercise:  4 days
Outreach:  2 days

PATTERNS
- Writing: perfect week. Best: mornings before 9am.
- Exercise: missed Tue + Thu. Pattern: skips on high-meeting days.
- Outreach: trailing off mid-week. Consider batching Mon/Wed/Fri.

LINKED GOALS
- Writing → publish-newsletter-weekly: on track ✅
- Outreach → grow-revenue-q2: below pace ⚠️

NEXT WEEK FOCUS
1 thing to protect: Writing streak (8 days — don't break it)
1 thing to fix: Outreach — schedule 3 specific slots in calendar
```

---

## Streak Calculation Rules

| Situation | Streak Effect |
|---|---|
| Habit done on a target day | Streak +1 |
| Habit not done on a target day | Streak resets to 0 |
| Habit not done on a non-target day | No effect |
| Habit paused | Streak frozen (not broken) |
| Skip logged with a note | Resets streak (honesty policy) |

**Philosophy:** The streak system is honest. A skip is a skip — no "rest day" loopholes on target days. But pausing for a vacation is legitimate and streak-safe.

---

## Heartbeat Integration

Add to `HEARTBEAT.md`:

```markdown
## Habits
- Check `habit-state.json` for any habits not yet logged today
- If any target habit is >2 hours past its usual_time and not logged: surface it once
- On Sundays: generate and send the weekly habit report
- Never nag about the same habit twice in one session
```

**Example heartbeat output:**
```
⏰ Outreach habit not logged yet (target: by 10:00, now 12:15)
Today: Writing ✅ | Exercise ✅ | Outreach ⏳
```

---

## Cron Alternative

For a scheduled daily check-in (instead of heartbeat):

```bash
openclaw cron add \
  --name "habit-evening-check" \
  --cron "0 20 * * *" \
  --model "anthropic/claude-haiku" \
  --session isolated \
  --message "Check habit-state.json. List any target habits not logged today. Keep it brief — just the unlogged ones and today's streak status." \
  --announce \
  --to "YOUR_TELEGRAM_CHAT_ID" \
  --tz "America/Chicago"
```

---

## Customization Options

### Flexible Target Definitions
Beyond specific days, you can use natural patterns:
- `"target_days": "weekdays"` — Mon–Fri
- `"target_days": "daily"` — all 7 days
- `"target_days": ["mon","wed","fri"]` — specific days

### Completion Windows
Add `"window_hours": 2` to a habit definition to allow a grace period after `usual_time` before it's flagged overdue.

### Habit Categories (Custom)
Default categories: creative, health, business, learning, other. Add yours by editing the `categories` array in `habit-state.json`:
```json
"categories": ["creative", "health", "business", "learning", "mindfulness", "social", "other"]
```

### Minimum Viable Habits
If tracking 6+ habits feels like another to-do list, try the 3-habit rule: pick exactly 3 habits — one creative, one health, one business. Track those until they're automatic, then expand.

### Linking Habits to Goals
Use the `linked_goal` field to connect habits to your goal-tracker goal IDs. The weekly report will show whether your habit pace supports your goal timeline.

### Multi-Context Tracking
If you run multiple businesses, use category prefixes:
```
"id": "biz1-writing"
"id": "biz2-outreach"
```
Weekly reports can then break down by category.

---

## Integration Map

| Skill | How It Connects |
|---|---|
| **goal-tracker** | Habits link to goals; weekly report flags goal pace alignment |
| **solopreneur-assistant** | Weekly review includes habit completion rates |
| **financial-tracker** | Correlate revenue habits (outreach, content) with income data |
| **decision-log** | Log habit system design decisions (why these 3 habits?) |
| **content-calendar** | Writing habit powers content pipeline; completion log is proof-of-work |
| **daily-briefing** | Morning brief can include today's habit targets |

---

## Troubleshooting

| Problem | Fix |
|---|---|
| Habit log getting unwieldy | Ask agent to archive entries older than 90 days to `habit-archive-YYYY.json` |
| Streaks feel punitive | Switch to a 7-day rolling average as your primary metric instead |
| Agent not detecting overdue habits | Verify `usual_time` is set and heartbeat instructions include the habit check |
| Too many habits, not tracking | Apply the 3-habit rule — reduce to 3, track for 30 days, then expand |
| Paused habit still flagged | Confirm `paused_until` date is in the future in `habit-state.json` |
| Linked goal not found | Verify the goal ID matches exactly what's in your goal-tracker state file |

---

## Privacy Note

All habit data stays in `habit-state.json` — local to your workspace. The agent never:
- Sends habit data to external services
- Posts completions publicly without explicit instruction
- Shares your habit log with other sessions or agents

Your consistency is your business.

---

*Habit Tracker by [The Agent Ledger](https://theagentledger.com)*
*Building AI-native workflows for solopreneurs.*
*Subscribe for weekly skills, playbooks, and automation ideas →*

**License:** [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/) — Free for personal use. Not for resale or redistribution in paid products.
