# Habit Tracker — Advanced Patterns

**By [The Agent Ledger](https://theagentledger.com)**

These patterns extend the base habit-tracker skill. Add what's useful; skip what isn't.

---

## Pattern 1: Habit Stacking (Chain-Triggered Logging)

Habit stacking is James Clear's idea: anchor a new habit to an existing trigger. You can replicate this in your agent:

**Define a stack in `habit-state.json`:**
```json
{
  "id": "meditation",
  "name": "5-Min Meditation",
  "stacked_after": "exercise",
  "target_days": "daily",
  "usual_time": null
}
```

**Agent behavior:** When you log `exercise`, the agent automatically prompts:
> "Exercise logged ✅. Meditation is stacked after this — did you do it?"

This mirrors the psychological mechanism: reduce friction by removing the "when do I do it?" question.

---

## Pattern 2: Minimum Viable Completion (MVC)

Full habits fail on bad days. Define a minimum that still counts:

```json
{
  "id": "writing",
  "name": "Daily Writing",
  "description": "500+ words focused writing",
  "mvc": "100 words or 10 minutes — anything counts",
  "target_days": "weekdays"
}
```

When you log less than the full habit:
> "Writing done — only 150 words today."

Agent logs it as `done: true` with note, marks `partial: true`. Streak continues. MVC completions are tracked separately in the weekly report:

```
Writing: 5/5 (100%) — 3 full, 2 MVC
```

**Philosophy:** Showing up imperfectly beats not showing up. The habit is the behavior, not the performance.

---

## Pattern 3: Revenue-Correlated Habit Tracking

Link high-leverage business habits directly to your financial-tracker data.

**Setup in `AGENTS.md`:**
```
During monthly financial snapshot: compare months where outreach habit rate was
>80% vs <60%. Pull from habit-state.json and cross-reference with financial-state.json.
Report the correlation as part of the monthly review.
```

**Example monthly insight output:**
```
📊 Habit-Revenue Correlation (Q1 2026)

Outreach habit >80%: avg $4,200/month revenue
Outreach habit <60%: avg $2,800/month revenue
Implied value per outreach habit: ~$47

Writing habit >80%: newsletter growth +12%/month avg
Writing habit <60%: newsletter growth +4%/month avg
```

This turns abstract habits into ROI — useful for motivation and prioritization.

---

## Pattern 4: Context-Aware Habit Suspension

Life has seasons. Some habits should pause automatically:

**Add to `AGENTS.md`:**
```
If I mention I'm traveling, sick, or on vacation: suggest which habits to pause
vs. which to keep (at minimum viable completion). Ask before pausing — don't auto-pause.
```

**Manual trigger:**
> "I'm flying tomorrow and Wednesday. Suggest which habits to adjust."

Agent response:
```
Travel days (Tue-Wed) — suggested adjustments:
- Exercise: switch to MVC (hotel gym / 20 min walk counts)
- Writing: pause (no dedicated time in travel days)
- Outreach: keep at 1 message — easy to do from phone

Want me to set these as your travel-week config?
```

---

## Pattern 5: Habit Retrospective (Monthly)

Run this at the end of each month for system-level review:

**Prompt:**
> "Run my monthly habit retrospective for [month]."

**Agent output format:**
```
📋 Habit Retrospective — March 2026

COMPLETION RATES
Writing:   89% (24/27 target days) — Personal best ⭐
Exercise:  71% (20/28 days)
Outreach:  64% (14/22 days)

STREAK HIGHS
Writing:   23 days (personal best)
Exercise:  11 days
Outreach:  6 days

PATTERNS DETECTED
- Exercise: 3 of 8 misses on Thursdays. Scheduling conflict?
- Outreach: Steady first 2 weeks, trailing off week 3-4. Month-end fatigue?
- Writing: Best month ever — correlation with moving it to mornings (March 2 change)

WHAT WORKED
- Morning writing block (implemented March 2): drove 8% improvement
- Habit stacking meditation after exercise: 100% compliance once exercise done

WHAT DIDN'T
- Evening outreach attempt: success rate 40%. Morning batching better.
- 6 habits at once: overwhelm in week 2, dropped to 3, much better

NEXT MONTH INTENTION
1 habit to add: [none — consolidate current wins]
1 habit to change: Outreach → batch Mon/Wed/Fri instead of daily
1 habit to celebrate: Writing — best month ever
```

---

## Pattern 6: Accountability-to-Newsletter Pipeline

Turn your habit data into newsletter content (without exposing private details):

**Monthly prompt:**
> "Draft a newsletter segment about my habits this month — anonymized, focusing on what worked and what I learned. Keep it to 200 words."

**Agent output (ready to edit and publish):**
```
This month I ran an experiment: I moved my writing habit from evening to morning.

The result? Best writing month I've had since starting this newsletter.

Here's what I learned:
- Willpower is a finite resource. Morning me is a better writer than evening me.
- Habit stacking works. I chained meditation after exercise — and meditation went from 40% to 95% compliance just by removing the "when" question.
- The 3-habit rule is real. I tried tracking 6. Week 2 was chaos. I cut to 3 and consistency doubled.

None of this is novel advice. But tracking it, with data, makes it stick differently.

[This is what the habit-tracker skill does in practice — it turns vague intentions into evidence.]
```

**This creates dual value:** improves your own habits, generates authentic newsletter content.

---

## Pattern 7: Habit-to-Goal Pace Check

Run this weekly alongside your goal-tracker review:

**Prompt:**
> "Check whether my current habit completion rates are on pace to hit my goals."

**Agent logic:**
1. Pull current habit completion rates from `habit-state.json`
2. Pull linked goals from `goal-tracker` state
3. Calculate whether habit pace maps to goal trajectory

**Example output:**
```
🎯 Habit-Goal Pace Check — Week of March 8

Goal: Grow newsletter to 500 subscribers (Q2)
Linked habit: Writing (content pipeline)
Current writing rate: 89%
Pace assessment: ON TRACK ✅ (89% > 80% needed)

Goal: $5k MRR by end of Q2
Linked habit: Outreach (1 per day, weekdays)
Current outreach rate: 64%
Pace assessment: BELOW PACE ⚠️
At current rate: ~13 outreach/month vs 22 needed
Gap: 9 outreach messages/month

Recommendation: Focus next week on outreach. Consider Mon/Wed/Fri batching.
```

---

## Pattern 8: Automated Sunday Review (Full Chain)

Chain habit review into your Sunday weekly review:

**`HEARTBEAT.md` entry:**
```markdown
## Sunday (run once on Sunday mornings)
- Check if last_weekly_report in habit-state.json is from this week
- If not: run full weekly habit report and update last_weekly_report timestamp
- Pull open items from goal-tracker and project-tracker
- Combine into a Sunday review message and send to Telegram
```

**Output:** One message every Sunday morning with habits + goals + projects — a complete weekly review in one shot.

---

## Pattern 9: Habit Streaks as Social Proof

If you're building in public or running a newsletter:

**"Accountability corner" in weekly newsletter:**
```
📊 My week in habits (accountability corner):
Writing: ✅✅✅✅✅ (5/5)
Exercise: ✅❌✅✅✅ (4/5)
Outreach: ✅✅❌✅✅ (4/5)

Honest miss on exercise Wednesday — back-to-back calls killed the window.
What are you tracking this week?
```

This builds authentic audience connection and models the behavior you're teaching.

---

## Pattern 10: Emergency Habit Triage (Rebuilding After Slippage)

Streaks break. Systems erode. This pattern is for restarting after a rough period:

**Prompt:**
> "I fell off my habits for the past [2 weeks]. Help me restart."

**Agent protocol:**
1. Pull completion rates for the past 30 days — show the dip without judgment
2. Apply the "2-day rule": never miss the same habit twice in a row going forward
3. Reset streaks to zero (honesty policy)
4. Suggest a 1-week "restart mode": only track the single most important habit, perfect compliance, then add back others

**Agent output:**
```
Fresh start. No shame in the data.

Past 30 days:
Writing: 43% (down from 89%)
Exercise: 29% (down from 71%)
Outreach: 14% (down from 64%)

Restart protocol:
- This week: Writing only. One habit. 100% target.
- Next week: Add Exercise back.
- Week 3: Add Outreach back.

The 2-day rule: you can miss once. Never twice in a row.

Streaks reset. Starting at 0 — which means day 1 is already a win.
```

---

*Advanced Patterns by [The Agent Ledger](https://theagentledger.com)*
*Subscribe for weekly skills, playbooks, and automation ideas →*

**License:** [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)
