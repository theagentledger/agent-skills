---
name: time-tracker
version: 1.0.0
description: >
  AI-native time tracking for solopreneurs. Log work sessions, track billable vs non-billable hours,
  generate daily and weekly time reports, monitor deep work streaks, and surface revenue-per-hour
  insights. Integrates with financial-tracker, project-tracker, and goal-tracker for a full
  picture of where your time actually goes.
tags: [time, productivity, billing, deep-work, tracking, focus, solopreneur]
platforms: [openclaw, cursor, windsurf, generic]
category: productivity
author: The Agent Ledger
license: CC-BY-NC-4.0
---

# Time Tracker
*by [The Agent Ledger](https://theagentledger.com)*

Stop guessing where your time goes. This skill turns your AI agent into a time-tracking partner that logs sessions, surfaces patterns, and helps you protect your most valuable asset.

---

## What This Skill Does

- Logs work sessions with project, category, and notes
- Tracks billable vs non-billable hours separately
- Generates daily summaries and weekly reports
- Monitors deep work streaks (uninterrupted focus blocks)
- Calculates revenue-per-hour by project or client
- Flags time allocation drift from your stated goals
- Integrates with financial-tracker, project-tracker, and goal-tracker

---

## Setup

### 1. Create the state file

Create `time-state.json` in your workspace:

```json
{
  "config": {
    "work_day_hours": 8,
    "deep_work_threshold_minutes": 90,
    "billable_rate_default": 0,
    "week_start": "Monday",
    "timezone": "America/Chicago"
  },
  "active_session": null,
  "today": {
    "date": "YYYY-MM-DD",
    "sessions": [],
    "total_minutes": 0,
    "billable_minutes": 0,
    "deep_work_minutes": 0
  },
  "weekly_totals": {
    "week_of": "YYYY-MM-DD",
    "total_hours": 0,
    "billable_hours": 0,
    "non_billable_hours": 0,
    "by_project": {},
    "by_category": {}
  },
  "projects": {},
  "categories": [
    "client-work",
    "admin",
    "marketing",
    "learning",
    "deep-work",
    "planning",
    "communication",
    "other"
  ]
}
```

### 2. Add to AGENTS.md

```markdown
## Time Tracking (standing instructions)

- When I say "start timer" or "starting [task]", log a session start to time-state.json
- When I say "stop timer" or "done with [task]", log the end time and update totals
- At end of day (or when asked), generate a daily time summary
- Flag if more than 3 hours pass with no logged activity (possible untracked time)
- Mark sessions as billable if they involve client work; non-billable otherwise
- Deep work = sessions ≥ 90 minutes with no interruption notes
```

### 3. (Optional) Set a daily end-of-day prompt

Add to HEARTBEAT.md:
```markdown
- If after 5 PM and no stop-time logged on active session: prompt to stop timer and log what was accomplished
- Weekly on Fridays: generate weekly time report before logging off
```

---

## Session Log Format

Each session entry in `time-state.json`:

```json
{
  "id": "sess_20260308_001",
  "date": "2026-03-08",
  "start": "09:00",
  "end": "10:45",
  "duration_minutes": 105,
  "project": "client-acme",
  "category": "client-work",
  "billable": true,
  "rate": 250,
  "notes": "Drafted contract addendum and reviewed prior correspondence",
  "deep_work": true,
  "interruptions": 0
}
```

**Field notes:**
- `deep_work`: true if duration ≥ `deep_work_threshold_minutes` and interruptions = 0
- `rate`: hourly rate for this session (0 = non-billable); override from config default
- `project`: matches project slugs from project-tracker (optional but useful)
- `interruptions`: self-reported count; keeps your deep work score honest

---

## Usage Patterns

### Start a timer
```
start timer: [project] — [brief description]
```
Example: `start timer: client-acme — reviewing discovery documents`

Agent response:
```
⏱️ Timer started
Project: client-acme
Category: client-work (assumed — correct?)
Start: 09:00 AM
Billable: yes (default rate: $250/hr)
```

---

### Stop timer
```
stop timer
```
or
```
done with [task]
```

Agent response:
```
✅ Session logged
Project: client-acme
Duration: 1h 45m
Billable: 1h 45m @ $250/hr = $437.50
Deep work: YES (no interruptions, ≥90 min)
Running today: 3h 20m (2h 15m billable)
```

---

### Log a completed session (retroactive)
```
log time: [project], [start time] to [end time], [category], billable/non-billable, notes: [description]
```

Example: `log time: newsletter, 7:00 AM to 8:30 AM, marketing, non-billable, notes: wrote issue #4 draft`

---

### Today's time summary
```
time summary today
```

Agent generates:

```
📊 Time Summary — March 8, 2026

Total logged: 5h 30m
├─ Billable: 3h 45m (~$937.50 @ default rate)
└─ Non-billable: 1h 45m

Deep work blocks: 2
└─ Longest: 1h 45m (client-acme)

By project:
├─ client-acme: 3h 45m (billable)
├─ newsletter: 1h 30m (non-billable)
└─ admin: 0h 15m (non-billable)

Unlogged time today: ~2h 30m (work day = 8h)
```

---

### Weekly time report
```
weekly time report
```

Agent generates:

```
📅 Weekly Report — March 2–8, 2026

Total hours: 38h 15m
├─ Billable: 24h 30m
├─ Non-billable: 13h 45m
└─ Billable %: 64%

Revenue earned: $6,125.00 (estimated)

Deep work sessions: 9 (avg 1h 52m)

By project:
├─ client-acme: 18h 00m
├─ client-beta: 6h 30m
├─ newsletter/marketing: 8h 15m
└─ admin/planning: 5h 30m

By category:
├─ client-work: 24h 30m (64%)
├─ marketing: 8h 15m (22%)
├─ admin: 3h 30m (9%)
└─ planning: 2h 00m (5%)

Goals check:
├─ Billable hours target: 24h ✅ (24h 30m)
└─ Deep work target: 8 sessions ✅ (9 sessions)
```

---

### Billable hours report (for invoicing)
```
billable hours for [client/project] this [week/month]
```

Agent generates a clean table:
```
💰 Billable Hours — client-acme — March 2026

Date       | Start | End   | Duration | Notes
-----------|-------|-------|----------|-------
2026-03-03 | 09:00 | 10:45 | 1h 45m   | Reviewed discovery docs
2026-03-04 | 13:00 | 15:30 | 2h 30m   | Drafted motion
2026-03-05 | 09:30 | 12:00 | 2h 30m   | Client call + prep
2026-03-07 | 10:00 | 13:30 | 3h 30m   | Research and writing
           |       |       |          |
TOTAL      |       |       | 10h 15m  | $2,562.50 @ $250/hr
```

---

### Project time breakdown
```
time by project [this week/this month/all time]
```

---

### Revenue per hour analysis
```
revenue per hour analysis
```

Compares actual revenue earned (from financial-tracker if integrated) against hours invested by project. Surfaces your most and least efficient revenue streams.

---

### Add a project with billing rate
```
add time-tracking project: [name], rate: [$X/hr or 0 for non-billable], category: [default category]
```

---

### Weekly time goals
```
set weekly time goals: [X] billable hours, [Y] deep work sessions
```

Goals stored in `time-state.json` config. Checked automatically in weekly reports.

---

## Report Formats

### Daily summary (compact)
Delivered via heartbeat if configured:
```
📊 Today (so far): 4h 15m total | 3h billable | 1 deep work block
Projects: client-acme (2h), newsletter (1h 15m), admin (1h)
```

### Weekly digest (full)
Best as a Friday end-of-day prompt. Includes hours, revenue, deep work count, and goals progress.

### Monthly invoice prep
Run: `billable hours for [client] this month` — generates invoice-ready table with dates, descriptions, and totals.

---

## Heartbeat Integration

Add to HEARTBEAT.md (sample):

```markdown
### Time Tracking
- Active session running? If yes, check duration and remind to stop if > 4 hours
- End of work day (after 6 PM): prompt for daily time summary if not already done
- Friday after 4 PM: generate weekly time report and compare to goals
- Monday morning: clear daily totals, start fresh week tracking
```

---

## Cron Alternative

For a scheduled weekly report (if you prefer cron over heartbeat):

```bash
openclaw cron add \
  --name "weekly-time-report" \
  --cron "0 16 * * 5" \
  --model "anthropic/claude-sonnet-4-6" \
  --session isolated \
  --tz "America/Chicago" \
  --message "Read time-state.json in the workspace. Generate a full weekly time report covering Mon-Fri of the current week. Include total hours, billable vs non-billable breakdown, project allocation, deep work sessions, and goals progress. Post summary to the General topic."
```

---

## Customization

**Different billing rates by project:**
Add per-project rates to `time-state.json` under `projects`:
```json
"projects": {
  "client-acme": {"rate": 300, "category": "client-work"},
  "client-beta": {"rate": 200, "category": "client-work"},
  "newsletter": {"rate": 0, "category": "marketing"}
}
```

**Non-hourly work (flat fee or retainer):**
Log hours normally. Mark the project with `"billing_type": "flat"` — sessions are tracked for time awareness but excluded from revenue calculations.

**Multiple timer support:**
For parallel work (rare, but possible), log sessions retroactively rather than using start/stop. Keeps state file clean.

**Deep work threshold:**
Default is 90 minutes. Change `deep_work_threshold_minutes` in config. Some people use 60 minutes (Pomodoro practitioners) or 120 minutes (Cal Newport-style).

**Weekend tracking:**
Optional — some solopreneurs track weekend hours, others don't. Set `weekend_tracking: false` in config to have reports only count Mon-Fri.

---

## Integration Map

| Skill | Integration |
|-------|-------------|
| **financial-tracker** | Cross-reference billable hours vs actual invoices logged; revenue-per-hour analysis |
| **project-tracker** | Time allocated per project; effort vs progress comparison |
| **goal-tracker** | Billable hours goal, deep work sessions goal — checked in weekly reports |
| **solopreneur-assistant** | Weekly review includes time allocation vs business priorities |
| **habit-tracker** | Deep work as a tracked daily habit; log consistency streaks |
| **client-relationship-manager** | Time logged per client; feeds into relationship value calculations |

---

## Troubleshooting

**Q: I forgot to log a session — can I add it retroactively?**
Yes. Use the "log time" command with explicit start/end times. The agent will insert it into the correct date's records and recalculate totals.

**Q: What if my timer ran overnight?**
Stop the timer and note the actual end time. The agent will split sessions at midnight if needed and log them to the correct dates.

**Q: How do I handle unpaid calls that turn billable?**
Log normally as non-billable, then edit the session: `edit session [id]: billable yes, rate [$X]`.

**Q: I work in multiple time zones — which one does this use?**
The `timezone` config field sets your reporting zone. Log times are stored as entered (your local time at the moment of entry).

**Q: How do I clear the state at year-end?**
Ask the agent to archive the year's data to `time-archive-YYYY.json`, then reset `time-state.json` for the new year. Annual totals should be preserved before reset.

---

## Privacy Note

All time data stays local in your workspace. No time logs, client names, or billing rates are transmitted anywhere. This skill does not auto-send reports or invoices — all sharing is explicitly initiated by you.

---

*Time Tracker is part of the [Agent Ledger Skills Library](https://github.com/theagentledger/agent-skills). Free and open-source under CC-BY-NC-4.0.*

*Want the full system — multi-agent orchestration, business automation playbooks, and production-grade configurations? → [The Agent Ledger](https://theagentledger.com)*
