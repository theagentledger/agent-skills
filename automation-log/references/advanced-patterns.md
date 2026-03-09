# Advanced Automation Log Patterns

**by [The Agent Ledger](https://theagentledger.com)**

Advanced patterns for power users of the automation-log skill. Read the main SKILL.md first.

---

## Pattern 1: Automation Health Score

Track a rolling "health score" for your entire automation stack — useful when you have
15+ automations and need a single number to gut-check operational status.

**Health score formula:**

```
Score = (Active - Broken×3 - Degraded×1.5 - Stale×0.5) / Total × 100
```

Log weekly in a `automation-health-log.md`:

```markdown
## Weekly Health Log

| Week | Active | Broken | Degraded | Stale | Score | Notes |
|------|--------|--------|----------|-------|-------|-------|
| Mar 3 | 16 | 0 | 1 | 2 | 88 | Stable week |
| Mar 10 | 16 | 1 | 1 | 1 | 79 | API key rotation needed |
```

Goal: keep score above 80. Below 70 = triage week.

---

## Pattern 2: Automation ROI Ladder

Rank every automation by ROI multiple (time saved / time to maintain). Use this to
decide what to fix, what to replace, and what to build next.

```markdown
## ROI Ladder — March 2026

TIER 1: Core (ROI 20×+) — never deprecate
  A001 Morning Briefing       32× | 8h saved / 0.25h maint
  A004 Invoice Generator      24× | 6h saved / 0.25h maint

TIER 2: Strong (ROI 10-20×) — maintain, improve
  A003 Research Cron          18× | 3.6h saved / 0.2h maint
  A011 Content Repurpose      14× | 4.2h saved / 0.3h maint

TIER 3: Marginal (ROI 2-10×) — review quarterly
  A008 Discord Digest         8×  | 2h saved / 0.25h maint
  A013 Reddit Monitor         4×  | 1h saved / 0.25h maint

TIER 4: Negative ROI (<2×) — fix or deprecate
  A017 Slack Notifier         1.5× | 0.75h saved / 0.5h maint
```

Review the ROI Ladder quarterly. Move things between tiers as maintenance costs drift.

---

## Pattern 3: Failure Pattern Analysis

If an automation fails repeatedly, log the pattern — not just the individual errors.

```markdown
## A007 — Failure Pattern Analysis

Failure log shows 6 failures in 90 days:
- Jan 15, Feb 3, Feb 19, Mar 2, Mar 7, Mar 8

Pattern detected: 3 of 6 failures on Mondays after weekends
Root cause hypothesis: API rate limit resets at midnight Sunday, first call of week hits spike
Fix: Add 90-second delay at job start on Mondays (via cron time offset)
```

Accumulated failure patterns prevent you from chasing the same bug twice.

---

## Pattern 4: Automation Dependency Map

When you have 15+ automations, some will feed others. Document chains explicitly to
understand blast radius when one fails.

```markdown
## Automation Dependency Map

A001 Morning Briefing
  ← depends on: A002 (email fetch), A003 (calendar pull), A005 (weather fetch)
  → feeds into: nothing (terminal output)

A002 Email Fetch
  ← depends on: Gmail API credentials (oauth-token)
  → feeds into: A001, A009 (inbox triage)

A009 Inbox Triage
  ← depends on: A002 output
  → feeds into: A001 (summary block)
```

When A002 breaks, you instantly know A001 and A009 will also fail.

---

## Pattern 5: Automation Sprint Protocol

Once a quarter, dedicate a "sprint" to improving your automation stack:

**Week 1: Audit**
- Run full automation dashboard
- Calculate ROI for every automation
- Flag Tier 3 and Tier 4 for review

**Week 2: Fix**
- Resolve all 🔴 Broken
- Improve highest-impact ⚠️ Degraded
- Deprecate confirmed negative-ROI automations

**Week 3: Build**
- Run gap analysis
- Build 1-2 new automations from top gaps
- Document them immediately (don't defer)

**Week 4: Stabilize**
- Verify all automations post-sprint
- Update all "Last Verified" dates
- Reset health score baseline

This keeps your stack from silently rotting between quarterly reviews.

---

## Pattern 6: Credential Rotation Tracker

Many automations break because credentials expire. Track rotation schedules alongside automations.

Add a `credentials-rotation.md` to `automation-log/`:

```markdown
# Credential Rotation Schedule

| Key Name | Used By | Last Rotated | Next Rotation | Notes |
|----------|---------|--------------|---------------|-------|
| gmail-oauth | A002, A009 | 2026-02-15 | 2026-05-15 | 90-day expiry |
| kalshi-api-key | A006, A014 | 2026-03-01 | 2026-06-01 | Manual rotation recommended |
| openai-key | A001, A003 | 2026-01-20 | No expiry | Rotate if usage spikes |

## Upcoming Rotations
- gmail-oauth: due May 15 (67 days)
```

Heartbeat instruction:
```markdown
## Credential Rotation
- Check automation-log/credentials-rotation.md
- If any key is due within 14 days: alert Taylor
```

---

## Pattern 7: New Automation Build Checklist

Before marking any new automation as ✅ Active, verify it passes this checklist:

```markdown
## Pre-Launch Checklist: [Automation Name]

- [ ] Dry run completed without errors
- [ ] Output matches expected format
- [ ] Failure behavior tested (what happens if it fails silently?)
- [ ] Alerts configured if critical
- [ ] Dependencies documented (credentials, files, APIs)
- [ ] Time saved estimate logged
- [ ] Added to automation-registry.md
- [ ] Record file created at automation-log/automations/A###.md
- [ ] Responsible agent/owner confirmed
```

Skipping this leads to "ghost automations" — things that were built but never quite worked.

---

## Pattern 8: Automation Changelog by Month

Track the evolution of your automation stack over time. Useful for looking back at
what changed when something starts behaving unexpectedly.

```markdown
## Automation Changelog

### March 2026
- Mar 9: A019 added — automation-log weekly cron
- Mar 7: A014 deprecated — Polymarket v1 API sunset
- Mar 5: A006 fixed — rotated expired Kalshi key
- Mar 2: A013 degraded — Discord API rate limit change

### February 2026
- Feb 28: A012 added — weekly Reddit digest
- Feb 15: A002 fixed — Gmail OAuth token refresh
```

One line per change. Makes debugging much faster when something breaks after a "quiet" week.

---

## Pattern 9: Automation-to-Goal Linking

Every automation should tie back to a goal. If it doesn't, it's a candidate for deprecation.

```markdown
## Goal-Automation Map

Goal: $10k/month revenue by Q2 2026
  Automations supporting this:
  - A004 Invoice Generator — reduces billing friction, faster payments
  - A007 Lead Digest — surfaces warm leads daily
  - A011 Content Repurpose — increases content output without more writing time

Goal: 2h/day deep work blocks
  Automations supporting this:
  - A001 Morning Briefing — eliminates manual morning review (~30min saved)
  - A002 Email Fetch → A009 Inbox Triage — eliminates inbox checking (~45min saved)
  - A015 Daily Shutdown Cron — end-of-day wrap without manual review
```

During goal reviews (goal-tracker integration), scan this map. If a goal slips,
check whether its supporting automations are healthy.

---

## Pattern 10: Automation Stack Handoff Document

If you ever collaborate with someone, bring on a contractor, or just want a clean
"state of ops" snapshot, generate a handoff doc:

```
AUTOMATION STACK OVERVIEW — March 9, 2026
Generated by: Alfred (automation-log skill)

TOTAL: 19 automations (16 active, 2 degraded, 1 planned)
MONTHLY TIME SAVED: ~52 hours
MONTHLY MAINTENANCE: ~3.5 hours

CRITICAL AUTOMATIONS (do not break without a plan):
  A001 Morning Briefing — daily ops awareness
  A004 Invoice Generator — revenue-critical
  A006 Kalshi Monitor — trading decisions

AUTOMATIONS BY TYPE:
  Cron jobs: 11
  Agent tasks: 5
  Webhooks: 2
  Scripts: 1

CREDENTIALS REQUIRED: (see credentials-rotation.md)
  Gmail OAuth, Kalshi API, OpenAI key, Telegram bot token

MAINTENANCE PROTOCOL:
  - Weekly: check dashboard for 🔴/⚠️ status
  - Monthly: review ROI ladder, deprecate Tier 4
  - Quarterly: full sprint (see advanced-patterns.md)
```

---

*Part of the Agent Ledger Skills collection — practical tools for solopreneurs running AI-powered businesses.*
*Subscribe at [theagentledger.com](https://theagentledger.com) for new skills, blueprints, and the premium guide.*
*License: [CC-BY-NC-4.0](https://creativecommons.org/licenses/by-nc/4.0/) — free to use, not for resale.*
