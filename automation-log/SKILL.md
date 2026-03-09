---
name: automation-log
version: 1.0.0
description: >
  Track every automation in your stack: crons, webhooks, agent tasks, scripts, and integrations.
  Monitor health, log failures, measure time-saved ROI, and surface stale or broken automations
  before they become invisible liabilities. Your complete automation inventory, always up to date.
tags: [automation, productivity, operations, solopreneur, agent-management, roi-tracking]
platforms: [openclaw, cursor, windsurf, generic]
category: operations
author: The Agent Ledger (theagentledger.com)
license: CC-BY-NC-4.0
---

# Automation Log

**by [The Agent Ledger](https://theagentledger.com)**

> *Track every automation you've built. Know what's running, what's broken, and whether it's actually saving you time.*

---

## Why This Skill Exists

Most solopreneurs and indie builders eventually accumulate a sprawling stack of automations:
cron jobs, Zapier flows, agent tasks, shell scripts, API webhooks, n8n workflows. They get built
one at a time, each solving a real problem. Then, six months later, you have 20+ automations
running in the background and no idea which ones still work.

This skill turns that invisible stack into a managed inventory. You'll know:
- What automations exist and what they're supposed to do
- When each one last ran successfully
- What failed and when
- How much time each automation saves you per month
- Which ones have gone stale or are no longer worth maintaining

---

## Setup

### Step 1: Create your automation registry

Create a file at `automation-log/automation-registry.md` in your workspace:

```markdown
# Automation Registry
Last updated: YYYY-MM-DD

## Active Automations

| ID | Name | Type | Trigger | Status | Last Verified | Time Saved/Month |
|----|------|------|---------|--------|---------------|-----------------|
| A001 | [name] | [type] | [trigger] | ✅ Active | YYYY-MM-DD | Xh |

## Broken / Needs Fix

| ID | Name | Error | Since | Priority |
|----|------|-------|-------|----------|

## Deprecated / Archived

| ID | Name | Reason | Archived On |
|----|------|--------|-------------|

## Planned / In Queue

| ID | Name | Goal | Priority | Estimated Build Time |
|----|------|------|----------|---------------------|
```

### Step 2: Create an automation record for each existing automation

Use the record format below for any automation worth tracking. Start with your top 5 most
important ones — don't try to document everything at once.

### Step 3: Add standing instructions to AGENTS.md

```markdown
## Automation Log Protocol
- When I build or configure a new automation, add it to automation-log/automation-registry.md
- When a cron/agent/script fails, log it in the failure log for the relevant automation
- On weekly review, flag any automations not verified in 7+ days
- Before deprecating any automation, log the reason in the archived section
```

---

## Automation Record Format

Each automation gets its own file at `automation-log/automations/A###-name.md`:

```markdown
# A001 — [Automation Name]

**Type:** cron | webhook | agent-task | script | integration | n8n | zapier | other
**Status:** ✅ Active | ⚠️ Degraded | 🔴 Broken | 🗄️ Deprecated | 📋 Planned
**Owner:** [which agent or person manages this]
**Created:** YYYY-MM-DD
**Last Verified:** YYYY-MM-DD

## What It Does
[One paragraph: what problem this solves, what it produces, who/what depends on it]

## Trigger
- **Type:** schedule | event | manual | webhook | chained
- **Detail:** e.g., "Every Monday 9am CT" or "On new email from X" or "After A002 completes"

## Expected Output
[What success looks like — output file, message sent, action taken]

## Time Saved
- **Per run:** ~X minutes
- **Frequency:** X times/week
- **Monthly total:** ~Xh saved
- **Build time:** ~Xh (one-time)
- **Maintenance:** ~Xmin/month

## Dependencies
- Tools: [list]
- Files: [list]
- APIs: [list]
- Credentials: [list key names only — never paste actual values]

## Failure Log
| Date | Error | Resolution | Fixed On |
|------|-------|------------|----------|

## Notes
[Quirks, edge cases, known limitations]

## Changelog
- YYYY-MM-DD: Created
```

---

## Usage Patterns

### 1. Log a new automation

> "Log a new automation: daily Kalshi PnL cron that runs at 8am CT, sends a summary to Telegram. Saves about 15 minutes of manual checking daily."

Alfred will create a new record at `automation-log/automations/A###.md`, assign the next ID,
set status to ✅ Active, and add it to the registry.

---

### 2. Automation status dashboard

> "Show me my automation dashboard."

Alfred will read the registry and return:

```
AUTOMATION DASHBOARD — March 9, 2026

✅ Active:       14
⚠️ Degraded:     2
🔴 Broken:       1
📋 Planned:      3

🔴 NEEDS ATTENTION:
  A007 — Daily Email Digest: failed 3× this week (API timeout)

⚠️ DEGRADED:
  A012 — Polymarket Alert: partially working (webhook delay 2h+)
  A015 — Weekly Report: running but output quality dropped

📅 NOT VERIFIED IN 7+ DAYS:
  A003 — Etsy Listing Cron (last: Feb 28)
  A009 — Reddit Monitor (last: Mar 1)

📈 TOP TIME SAVERS THIS MONTH:
  A001 — Morning Briefing:     ~8h saved
  A004 — Invoice Generator:    ~6h saved
  A007 — Daily Email Digest:   ~5h saved (when working)
```

---

### 3. Log a failure

> "The Kalshi monitoring cron failed — got a 401 error."

Alfred will append to the failure log for that automation with today's date, error type,
and leave Resolution blank until you follow up.

---

### 4. Mark as fixed

> "A007 is fixed — rotated the API key."

Alfred will update the failure log with the resolution, update Last Verified to today,
and restore status to ✅ Active.

---

### 5. Calculate automation ROI

> "What's my automation ROI for February?"

Alfred will aggregate time-saved data across all active automations and return:

```
AUTOMATION ROI — February 2026

Total automations: 16 active
Total time saved: ~47h/month (~11.75h/week)

At a $150/hr value of time: $7,050/month recovered
Total build investment (all-time): ~68h
Monthly maintenance: ~2.5h

Payback period: Recovered in <2 months
Current ROI multiple: 18.8× (47h saved / 2.5h maintenance)

Highest ROI automations:
  A001 Morning Briefing:      28× (8h saved / 0.3h maintenance)
  A004 Invoice Generator:     22× (6h saved / 0.3h maintenance)
  A011 Content Repurpose:     15× (4h saved / 0.3h maintenance)

Lowest ROI / candidates for review:
  A013 Discord Scraper:       2× (1h saved / 0.5h maintenance)
```

---

### 6. Weekly automation review

> "Run my weekly automation review."

Alfred will:
1. List all automations not verified in 7+ days → flag for manual check
2. Surface any with failure log entries this week
3. Highlight degraded automations
4. Calculate the week's time savings
5. Recommend 1-2 actions (fix, deprecate, build new)

---

### 7. Deprecate an automation

> "Deprecate A013 — the Discord scraper. The Discord server is dead."

Alfred will move A013 to the Deprecated section in the registry, log the reason and date,
and note any downstream dependencies that may be affected.

---

### 8. Automation gap analysis

> "What should I automate next?"

Alfred will review your recent work patterns, open tasks from project-tracker, and
recurring items in inbox-triage to suggest the highest-leverage automation candidates:

```
AUTOMATION GAP ANALYSIS

Based on recent patterns, consider automating:

1. HIGH VALUE: Weekly newsletter metrics pull
   → You manually check stats every Sunday (~45min)
   → Estimated save: 3h/month | Build time: 2-3h | ROI: 1×/month

2. MEDIUM VALUE: New GitHub PR notifications
   → You check manually 2-3×/day
   → Estimated save: 1h/month | Build time: 1h | ROI: quick

3. LOW VALUE: Daily weather check
   → Already available via daily-briefing skill
   → Recommendation: use existing skill instead of building new
```

---

### 9. Pre-deprecation audit

> "Is A005 still worth keeping?"

Alfred will pull the full record and calculate:
- Current time saved vs maintenance cost
- Failure frequency over last 90 days
- Whether anything else depends on it
- Recommendation: keep / refactor / deprecate

---

### 10. Build automation documentation

> "Document all my active crons for handoff."

Alfred will generate a clean summary of all active automations with descriptions,
triggers, and output — formatted for sharing or archival.

---

## Heartbeat Integration

Add to `HEARTBEAT.md`:

```markdown
## Automation Health (weekly)
- Check automation-log/automation-registry.md
- Flag any automations with status ⚠️ or 🔴
- Flag any not verified in 7+ days
- If 3+ issues: escalate to Alfred for triage
```

For more frequent monitoring, add to your daily heartbeat:

```markdown
## Automation Failures
- Quick scan of failure logs for new entries today
- If any 🔴 critical automations broken: alert immediately
```

---

## Cron Setup (Optional)

For a weekly automation health report delivered to Telegram:

```bash
openclaw cron add \
  --name "weekly-automation-review" \
  --cron "0 9 * * MON" \
  --model "anthropic/claude-sonnet-4-6" \
  --session isolated \
  --message "Read automation-log/automation-registry.md and all files in automation-log/automations/. Generate a weekly automation health report: active count, broken/degraded, time savings this week, anything not verified in 7 days, and 1-2 action recommendations. Be concise." \
  --announce \
  --to "YOUR_TELEGRAM_CHAT_ID" \
  --tz "America/Chicago"
```

---

## Automation Types Reference

| Type | Examples | Verification Method |
|------|----------|---------------------|
| cron | OpenClaw cron jobs, shell cron, GitHub Actions | Check last run log |
| agent-task | Heartbeat tasks, scheduled prompts | Check output file/message |
| webhook | Zapier, Make.com, n8n flows | Check trigger history |
| script | Shell scripts, Python scripts | Check exit code/log |
| integration | API polling, IFTTT, platform rules | Check output or API call |

---

## Integration with Other Agent Ledger Skills

| Skill | Integration |
|-------|-------------|
| **solopreneur-assistant** | Include automation ROI in weekly review |
| **financial-tracker** | Log automation-enabled revenue (e.g., automated lead capture) |
| **project-tracker** | Track automation build projects through to deployment |
| **time-tracker** | Log time spent building and maintaining automations |
| **goal-tracker** | Link automation-building goals to time-saved KRs |
| **daily-briefing** | Include critical automation failures in morning briefing |

---

## Customization

**Minimal setup (start here):**
Only track your top 5 automations. Don't fill in every field. Just name, status, and last-verified.

**Full setup:**
One file per automation, complete with ROI tracking and failure logs.

**Team use:**
Add an "Owner" column to the registry. Use separate subdirectories per team member.

**Severity tiers:**
Customize what triggers an alert. By default:
- 🔴 Broken = any failure with no resolution in 24h
- ⚠️ Degraded = working but output quality or timing is off
- 📅 Stale = not verified in 7 days (configurable)

**ROI calculation:**
The default time-value rate is left blank — you fill in your own $/hr or just work in hours.
Add a `time-value` field to the registry header if you want dollar figures.

---

## Troubleshooting

**"I have too many automations to document all at once."**
Start with the ones that matter most: highest time savings, most critical to revenue, or most
recently broken. Add others during weekly reviews. It doesn't have to be complete day one.

**"How do I know if an automation is working without running it?"**
Check the output: does the expected file exist? Did the expected message arrive? Is the log
clean? If you can't verify it passively, add an active check to your next heartbeat.

**"My automation IDs are getting confusing."**
Use a prefix that means something: `C` for crons, `W` for webhooks, `S` for scripts. E.g.,
C001, W001, S001. Reorganize if you have to — it's just markdown.

**"Should I track third-party tools I don't own (Zapier, IFTTT)?"**
Yes — especially the ones your business depends on. Log them as `type: integration` and note
that maintenance = checking the platform's run history.

---

## Privacy Note

All automation records are local markdown files. This skill never:
- Auto-runs or triggers any automation
- Shares automation details externally
- Stores credentials (reference key names only, never values)
- Auto-deprecates or modifies any automation without your instruction

Treat `automation-log/` as sensitive ops documentation. Don't commit it to public repos.

---

*Part of the Agent Ledger Skills collection — practical tools for solopreneurs running AI-powered businesses.*
*Subscribe at [theagentledger.com](https://theagentledger.com) for new skills, blueprints, and the premium guide.*
*License: [CC-BY-NC-4.0](https://creativecommons.org/licenses/by-nc/4.0/) — free to use, not for resale.*
