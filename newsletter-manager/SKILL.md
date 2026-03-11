---
name: newsletter-manager
version: 1.0.0
description: >
  Full newsletter operations management for solopreneurs and indie creators. Track subscriber growth,
  log issue performance (open rates, clicks, replies), manage sponsorship pipeline, run growth
  experiments, and synthesize what's working across your publication. Built for creators who treat
  their newsletter as a business asset, not a hobby. Part of the Agent Ledger skill suite.
tags:
  - newsletter
  - email-marketing
  - content-creator
  - growth
  - solopreneur
  - publishing
platforms:
  - openclaw
  - cursor
  - windsurf
  - generic
category: content-and-growth
author: The Agent Ledger (theagentledger.com)
license: CC-BY-NC-4.0
---

# Newsletter Manager

> Built by [The Agent Ledger](https://theagentledger.com) — AI systems for solopreneurs who build in public.
> Subscribe for more skills, guides, and automation playbooks.

A complete newsletter operations system for your AI agent. Track every issue, measure growth, manage sponsors, and run experiments — all in structured files your agent can read, update, and report on.

---

## What This Skill Does

Your agent becomes your newsletter COO:
- **Issue tracking** — log every issue with performance metrics after send
- **Subscriber growth log** — weekly snapshots with source attribution
- **Sponsorship pipeline** — from prospect to invoiced, all in one place
- **Growth experiments** — structured A/B tracking with outcome logging
- **Synthesis** — what's working, what's not, what to try next

---

## Setup (5 Minutes)

### Step 1: Create Your Newsletter State File

Create `newsletter-state.md` in your workspace root (or a `newsletter/` subdirectory):

```markdown
# Newsletter State

## Publication Info
- **Name:** [Your Newsletter Name]
- **Platform:** [Beehiiv / ConvertKit / Substack / Ghost / other]
- **Niche:** [One-sentence description]
- **Frequency:** [Weekly / Bi-weekly / Monthly]
- **Launch Date:** [YYYY-MM-DD]
- **Monetization:** [Sponsorships / Paid tier / Products / None]

## Current Stats (as of [YYYY-MM-DD])
- **Total Subscribers:** 0
- **Active / Confirmed:** 0
- **30-Day Open Rate:** 0%
- **30-Day Click Rate:** 0%
- **Avg Replies Per Issue:** 0
- **Monthly Revenue:** $0

## Growth Targets
- **Q[N] Subscriber Goal:** 0
- **Q[N] Revenue Goal:** $0
- **Target Open Rate:** 0%

## Issue Counter
- **Total Issues Published:** 0
- **Last Issue Number:** 0
- **Last Issue Date:** —

## Active Experiments
- None

## Notes
[Anything the agent should remember about this newsletter]
```

### Step 2: Create the Issues Log

Create `newsletter/issues-log.md`:

```markdown
# Issues Log

| # | Date | Subject Line | Subscribers at Send | Open Rate | Click Rate | Replies | Revenue Tied | Notes |
|---|------|-------------|--------------------|-----------|-----------|---------|-----------|----|
```

### Step 3: Create the Growth Log

Create `newsletter/growth-log.md`:

```markdown
# Subscriber Growth Log

| Date | Total Subs | Week-over-Week | Source Breakdown | Notes |
|------|-----------|---------------|-----------------|-------|
```

### Step 4: Create the Sponsorship Pipeline

Create `newsletter/sponsorships.md`:

```markdown
# Sponsorship Pipeline

## Active Sponsors
| Sponsor | Issues | Rate | Status | Invoice Due | Notes |
|---------|--------|------|--------|-------------|-------|

## Pipeline
| Company | Contact | Status | Rate Asked | Issues | Next Step | Follow-Up Date |
|---------|---------|--------|-----------|--------|-----------|----------------|

## Completed / Past Sponsors
| Sponsor | Total Issues | Total Revenue | Date Range | Notes |
|---------|-------------|--------------|------------|-------|

## Rates & Packages
- **Primary Placement (top):** $[X]/issue
- **Secondary Placement (bottom):** $[X]/issue
- **Dedicated Send:** $[X]
- **Bundle (4 issues):** $[X]
```

### Step 5: Create Experiments Log

Create `newsletter/experiments.md`:

```markdown
# Growth Experiments Log

## Active Experiments
[None yet]

## Completed Experiments

| # | Hypothesis | Test | Start | End | Result | Adopted? |
|---|-----------|------|-------|-----|--------|----------|
```

### Step 6: Add to AGENTS.md

Add this standing instruction to your `AGENTS.md`:

```markdown
## Newsletter Manager

newsletter-state.md tracks publication health.
After every send: log issue to newsletter/issues-log.md, update newsletter-state.md.
Weekly: update newsletter/growth-log.md with new subscriber count.
On any sponsorship development: update newsletter/sponsorships.md.
Keep growth experiments in newsletter/experiments.md.
```

---

## Usage Patterns

### 1. Log a Published Issue

After sending an issue, once metrics are available (typically 48–72 hours):

> "Log newsletter issue #[N]: subject '[Subject Line]', sent [date], [X] subscribers, [X]% open rate, [X]% click rate, [X] replies, revenue tied: $[X]"

Your agent will:
- Add a row to `newsletter/issues-log.md`
- Update `newsletter-state.md` (last issue date, total issues, rolling averages)
- Flag any notable performance (above/below average open rate, high reply count)

### 2. Weekly Subscriber Update

> "Update subscriber count: [X] total, [X] new this week. Main sources: [organic / referral / promo / social]"

Your agent will:
- Add a row to `newsletter/growth-log.md`
- Update `newsletter-state.md` current stats
- Calculate week-over-week change and trend
- Flag if you're on/off pace for your quarterly goal

### 3. Newsletter Performance Dashboard

> "Give me a newsletter performance dashboard"

Your agent will return:

```
📰 [Newsletter Name] — Performance Dashboard

Subscribers: [X] (+[N] this week / [%] toward Q[N] goal)
30-Day Open Rate: [X]% (platform avg: ~[benchmark]%)
Click Rate: [X]%
Avg Replies/Issue: [X]
Last Issue: #[N] — "[Subject Line]" — [date]

📈 Growth Trend (last 4 weeks):
Week 1: [X] → Week 2: [X] → Week 3: [X] → Week 4: [X]
Net: +[X] subs | Pace: [on/off] track for Q[N] goal

📊 Best Performing Issues (by open rate):
1. #[N] — "[Subject]" — [X]%
2. #[N] — "[Subject]" — [X]%
3. #[N] — "[Subject]" — [X]%

💰 Revenue:
- Active sponsors: [X]
- Monthly sponsor revenue: $[X]
- Pipeline value: $[X]
```

### 4. Add a Sponsorship Prospect

> "Add [Company] to sponsor pipeline. Contact: [name/email]. Asking $[X] for [N] issues. Follow up [date]."

Your agent will:
- Add a row to the Pipeline section of `newsletter/sponsorships.md`
- Set status to "Outreach"
- Set next-step and follow-up date

### 5. Log Sponsorship Progress

> "Update [Company] sponsor status: they said yes to [N] issues at $[X]. Issues [#N–#N]. Invoice due [date]."

Your agent will:
- Move to Active Sponsors section
- Log rate, issue range, invoice due date
- Update monthly revenue in `newsletter-state.md`

### 6. Sponsorship Revenue Report

> "Give me a sponsorship revenue report"

Your agent will return:
```
💼 Sponsorship Revenue Report

Active Sponsors: [X]
Current Monthly Revenue: $[X]
Issues Sold (next 30 days): [X]
Pipeline Value (if all convert): $[X]

Active:
- [Sponsor]: Issues #[N-N] | $[X] | Invoice due [date]

Pipeline:
- [Company]: [status] | Asked $[X] | [N] issues | Follow up [date]

YTD Sponsorship Revenue: $[X]
```

### 7. Start a Growth Experiment

> "Start experiment: hypothesis that [X] will improve open rates. Testing [specific change]. Starting [date]."

Your agent will:
- Add to Active Experiments in `newsletter/experiments.md`
- Assign an experiment ID
- Set start date and expected end date
- Note baseline metric

### 8. Close Out an Experiment

> "Close experiment [#ID]: result was [metric change]. [Adopting / Not adopting]."

Your agent will:
- Move to Completed Experiments table
- Log outcome and adoption decision
- Update `newsletter-state.md` if adopted (e.g., new open rate baseline)
- Add lesson learned

### 9. Subject Line Analysis

> "Which subject lines performed best? Give me patterns I should replicate."

Your agent will analyze `newsletter/issues-log.md` and return:
- Top 5 issues by open rate with subject lines
- Common patterns (length, question vs. statement, numbers, personal vs. broad)
- Worst performers for contrast
- 3 hypotheses for what's driving performance

### 10. Monthly Newsletter Review

> "Run the monthly newsletter review"

Your agent will return a full synthesis:
- Growth: subs added, pace to goal, best/worst acquisition source
- Content: top performing issues, reply-generating topics
- Revenue: sponsorship MRR, pipeline health
- Experiments: what was tested, what was adopted
- Outlook: what to prioritize next month

---

## Performance Benchmarks (Reference)

Use these to calibrate expectations — your numbers will vary by niche and platform.

| Metric | Cold Start | Growing | Established |
|--------|-----------|---------|-------------|
| Open Rate | 30–45% | 40–55% | 50–65%+ |
| Click Rate | 1–3% | 2–5% | 4–8%+ |
| Replies/Issue | 0–2 | 3–10 | 10–30+ |
| Weekly Growth Rate | 1–3% | 3–5% | 5–10%+ |

> **Note:** Beehiiv/ConvertKit open rates tend to skew lower than Substack (email client differences). Use your own trend over time, not absolute benchmarks.

---

## Issue Performance Scoring

Use this rubric when reviewing each issue:

| Score | Criteria |
|-------|---------|
| 🟢 **Standout** | Open rate 10%+ above your average AND replies > average |
| 🟡 **Good** | Open rate within 5% of average, clicks normal |
| 🟠 **Below Average** | Open rate 5–15% below average |
| 🔴 **Miss** | Open rate 15%+ below average OR zero engagement signals |

Log the score in the Notes column of `issues-log.md`. After 20+ issues, your agent can use this to pattern-match what drives standout performance.

---

## Heartbeat Integration

Add to your `HEARTBEAT.md`:

```markdown
## Newsletter Check (Weekly, Fridays)
- Check if subscriber count has been updated this week
- Check if any issues were sent without being logged
- Flag any sponsorship follow-ups overdue
- If Q-goal pace is off by >15%, surface a warning
```

---

## Cron Alternative (Optional)

For a weekly automated Sunday performance brief:

```bash
openclaw cron add \
  --name "newsletter-weekly-brief" \
  --cron "0 9 * * 0" \
  --model "anthropic/claude-sonnet-4-6" \
  --session isolated \
  --message "Read newsletter-state.md and newsletter/issues-log.md and newsletter/growth-log.md. Produce a weekly newsletter performance brief: subscriber pace vs goal, last issue performance vs average, any standout or miss issues flagged, sponsor pipeline status, and one recommendation for this week's issue." \
  --announce \
  --to "[YOUR_TELEGRAM_CHAT_ID]" \
  --tz "America/Chicago"
```

---

## Integration Map

| Skill | Integration |
|-------|-----------|
| **content-calendar** | Link newsletter issues to content pipeline; track issues in scheduling queue |
| **financial-tracker** | Sync sponsorship revenue to income log |
| **social-media-manager** | Cross-post issue announcements; track social-to-subscriber conversion |
| **writing-assistant** | Draft issue content, subject lines, and sponsor copy |
| **goal-tracker** | Link subscriber and revenue goals to quarterly OKRs |
| **idea-vault** | Pull newsletter topic ideas from idea pipeline |
| **launch-playbook** | Use for paid newsletter tier launch, course launch tied to list, etc. |
| **research-assistant** | Research competitors, industry trends for issue content |

---

## Customization

**Multi-publication tracking:**
Create separate state files — `newsletter-state-[name].md` and `newsletter/[name]/` directories. Prefix agent instructions with publication name.

**Paid tier tracking:**
Add a Paid Subscribers section to `newsletter-state.md` with MRR, churn rate, and conversion rate from free.

**Referral program:**
Add a Referral Program table to `growth-log.md` with top referrers, referral count per period, and reward status.

**Platform migration:**
Log a migration event in `growth-log.md` with before/after metrics. Track list hygiene loss separately from organic churn.

**Minimal setup:**
If you just want to track subscribers and issues without sponsorships or experiments, only create `newsletter-state.md` and `newsletter/issues-log.md`.

---

## Troubleshooting

| Problem | Solution |
|---------|---------|
| Agent doesn't know last issue metrics | Check that issues-log.md exists and you've run the "log issue" pattern after each send |
| Open rate tracking is inconsistent | Some email clients block tracking pixels; treat rates as directional, not absolute |
| Subscriber count doesn't match platform | Log only confirmed/active subscribers (not unconfirmed or churned) |
| Agent gives generic growth advice | Add more context to newsletter-state.md (niche, audience, current hypothesis) |
| Experiments aren't being tracked | Make sure you explicitly "start" and "close" experiments via the usage patterns above |

---

## Privacy Note

This skill is fully local. No subscriber data, email addresses, or platform credentials are stored or transmitted. All metrics are aggregate numbers you manually log. Never store individual subscriber PII in these files.

---

*Newsletter Manager — by [The Agent Ledger](https://theagentledger.com)*
*Free skill. CC-BY-NC-4.0. For more skills, premium guides, and automation playbooks, subscribe at theagentledger.com.*
