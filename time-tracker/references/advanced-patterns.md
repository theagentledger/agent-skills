# Time Tracker — Advanced Patterns
*by [The Agent Ledger](https://theagentledger.com)*

Advanced usage patterns for power users who want to squeeze more insight from their time data.

---

## Pattern 1: Pomodoro-Style Session Tracking

Track work in structured 25-minute blocks. The agent logs each Pomodoro and tracks your session count toward daily/weekly goals.

**Setup:**
Add to AGENTS.md:
```
When I say "pomodoro start: [task]", log a 25-minute session start.
When I say "pomodoro done", stop the timer and log a short break (5 min non-billable).
After 4 pomodoros, log a long break (15-30 min) and ask what's next.
Track daily pomodoro count in time-state.json under today.pomodoros.
```

**Weekly Pomodoro report:**
```
Total pomodoros: 38 (15h 50m focused work)
Best day: Wednesday (11 pomodoros)
Avg per work day: 7.6
```

---

## Pattern 2: Revenue-Per-Hour Analysis

Cross-references logged hours against actual revenue from financial-tracker to surface your most and least efficient income streams.

**Prompt:**
```
revenue per hour analysis — compare financial-tracker income logs against time-tracker hours by project for this month
```

**Output format:**
```
💰 Revenue-Per-Hour Analysis — March 2026

Project          | Hours  | Revenue  | $/hr   | vs Goal
-----------------|--------|----------|--------|---------
client-acme      | 18.5h  | $5,550   | $300   | ✅ on target
client-beta      | 12.0h  | $1,800   | $150   | ⚠️ below $200 goal
newsletter       | 8.0h   | $0       | $0     | Investment (list growth)
admin/planning   | 5.5h   | —        | —      | Overhead

Effective hourly rate (all paid work): $213/hr
Goal: $250/hr
Gap: $37/hr → close by shifting 3h from client-beta to client-acme
```

---

## Pattern 3: Context Switching Cost Tracker

Research shows context switching costs 20–40 minutes per switch. Track how often you switch projects in a day and flag high-switch days.

**How it works:**
Count project transitions in a day's session log. Flag days with more than 5 transitions.

**End-of-day report addition:**
```
🔄 Context switches today: 7 (HIGH — optimal is ≤4)
Fragmented work periods: 3 (sessions < 30 min)
Recommendation: Tomorrow, block morning for client-acme before opening communication.
```

---

## Pattern 4: Client Billing Report (Invoice-Ready)

Generate a formatted billable hours table for any client, any period — ready to paste into your invoice.

**Prompt:**
```
generate invoice data for [client] for [month]
```

**Output:**
```
BILLABLE HOURS — CLIENT ACME — MARCH 2026
Prepared: 2026-03-31

Date       | Hours | Description
-----------|-------|-------------
2026-03-03 | 1.75  | Discovery document review
2026-03-04 | 2.50  | Motion drafting
2026-03-05 | 2.50  | Client conference + preparation
2026-03-07 | 3.50  | Research and brief writing
2026-03-10 | 2.25  | Deposition preparation
2026-03-14 | 4.00  | Hearing preparation and attendance
           |       |
TOTAL      | 16.50 hrs @ $300/hr = $4,950.00

Payment terms: Net 30
```

---

## Pattern 5: Capacity Planning

Understand how much available time you have for new projects based on your committed hours.

**Monthly capacity check:**
```
capacity check for next month
```

**Output:**
```
📐 Capacity Check — April 2026

Work days available: 22 (× 8h = 176h total capacity)
Committed hours (recurring):
├─ client-acme retainer: 20h/mo
├─ client-beta: ~12h/mo (est. based on March avg)
└─ admin/overhead: ~10h/mo (est.)

Total committed: ~42h
Available for new work: ~134h (76% uncommitted)

⚠️ Caution: March average was 38h/week (152h/mo) — near full capacity.
Recommendation: New client intake would require dropping non-billable marketing time
or raising rates to justify reduced availability.
```

---

## Pattern 6: Deep Work Streak Monitoring

Track consecutive days with at least one deep work session (≥90 min uninterrupted). Useful for building consistency habits.

**Integration with habit-tracker:**
```json
{
  "id": "deep-work",
  "name": "Deep Work Block",
  "description": "At least one 90+ minute uninterrupted focus session",
  "target_days": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
  "linked_goal": "Q2-G1-productivity"
}
```

**Heartbeat check (daily):**
```
Review time-state.json. Did today include at least one deep work session (≥90 min, 0 interruptions)?
If yes, log habit completion for "deep-work" in habit-state.json.
If no and it's before 5 PM, send a nudge: "No deep work block yet today — protect the next 90 minutes."
```

---

## Pattern 7: Time Allocation Drift Detection

Compare actual time allocation (from logs) against your intended allocation (goals). Flag when you're drifting.

**Weekly drift check:**
```
time allocation drift check — compare actual hours by category this week against my stated priorities
```

If your goal is 60% billable / 20% marketing / 20% admin, but actual was 40% billable / 10% marketing / 50% admin:

```
⚠️ Allocation Drift Detected — Week of March 2

Target    → Actual
Billable: 60% → 40% (-20% | -8h)
Marketing: 20% → 10% (-10% | -4h)
Admin:     20% → 50% (+30% | +12h)

Root cause (estimated): 12 extra admin hours logged
Largest admin items: email/comms (4h), contract review (5h), tools setup (3h)

Recommendation: Batch admin to Friday afternoons. Block Tue/Wed mornings for
deep client work before opening email.
```

---

## Pattern 8: Automated Monday Morning Planning

Every Monday, the agent reviews last week's time data and helps you allocate the coming week intentionally.

**Cron setup:**
```bash
openclaw cron add \
  --name "monday-time-planning" \
  --cron "0 8 * * 1" \
  --model "anthropic/claude-sonnet-4-6" \
  --session isolated \
  --tz "America/Chicago" \
  --message "Read time-state.json. Summarize last week's hours by project and category. Check weekly goals and flag any misses. Then propose a rough time allocation for this week based on known commitments and stated goals. Post a planning brief to the General topic."
```

**Output (Monday 8AM):**
```
🗓️ Week Planning Brief — March 9, 2026

Last week recap:
├─ Total: 36h (goal: 40h) — 4h short
├─ Billable: 22h (goal: 24h) — close
├─ Deep work sessions: 6 (goal: 8) — short 2
└─ Big time sink: admin (9h vs typical 5h)

This week priorities (based on goals):
├─ client-acme: Target 20h (retainer + deadline Fri)
├─ Newsletter Issue #4: Target 4h (Wed deadline)
├─ Admin: Cap at 5h (batch to Fri PM)
└─ Deep work: 2 sessions/day minimum

Protected blocks to schedule:
• Tue + Wed 9-11:30 AM: client-acme deep work
• Thu 9-11 AM: newsletter draft
• Fri PM: admin batch + weekly review
```

---

## Pattern 9: Energy-Time Correlation

Track when you do your best work, not just how much. Add an optional energy rating (1-5) to sessions.

**Enhanced session log:**
```json
{
  "id": "sess_20260308_002",
  "start": "14:00",
  "end": "16:30",
  "duration_minutes": 150,
  "project": "newsletter",
  "energy_at_start": 3,
  "energy_at_end": 4,
  "output_quality": 4,
  "notes": "Surprisingly good session despite post-lunch timing"
}
```

**Monthly energy analysis:**
```
analyze my energy-time patterns from this month's sessions
```

**Output:**
```
📈 Energy-Time Patterns — March 2026

Best focus windows:
├─ 9:00–11:30 AM: avg energy 4.2/5 (best deep work window)
├─ 3:00–5:00 PM: avg energy 3.8/5 (good for creative work)
└─ 1:00–2:30 PM: avg energy 2.6/5 (post-lunch dip — use for admin)

Highest output-quality sessions: 9-11 AM
Recommendation: Protect morning slots for revenue-generating work.
Schedule calls, email, admin for 1-3 PM.
```

---

## Pattern 10: Annual Time Audit + Year-End Archive

At year-end (or mid-year), review how your time allocation matched your business goals.

**Year-end archive:**
```
archive 2026 time data and generate annual summary
```

Creates `time-archive-2026.json` and resets state for new year.

**Annual summary:**
```
📅 Annual Time Summary — 2026

Total hours logged: 1,847h
├─ Billable: 1,124h ($281,000 estimated revenue)
├─ Non-billable investment: 723h
   ├─ Marketing/newsletter: 210h
   ├─ Learning/development: 180h
   ├─ Admin: 195h
   └─ Planning: 138h

Effective hourly rate: $250/hr (target: $250/hr ✅)
Deep work sessions: 312 (avg 6/week)
Best quarter: Q3 (314 billable hours)

Biggest time shifts vs prior year:
├─ +45h on marketing (newsletter growth investment)
└─ -30h on admin (automation wins)

Recommendation for next year: Continue newsletter investment;
explore raising rates for client-acme to $325/hr (strong relationship, high value).
```

---

*These patterns build on the core Time Tracker skill. For the full system including multi-agent orchestration and business automation playbooks, visit [The Agent Ledger](https://theagentledger.com).*
