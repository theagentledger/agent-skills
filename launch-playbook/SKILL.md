---
name: launch-playbook
version: 1.0.0
description: >
  Structured launch management system for solopreneurs. Manage multi-stage launch
  pipelines (product, newsletter, course, campaign, service) with checklists, asset
  tracking, countdown timers, and post-launch retrospectives. Integrates with
  content-calendar, writing-assistant, social-media-manager, financial-tracker,
  and project-tracker skills. Prevents launch-day chaos with repeatable, agent-native
  workflows.
tags: [launch, marketing, product, campaign, solopreneur, planning, checklist]
platforms: [openclaw, cursor, windsurf, generic]
category: business
author: The Agent Ledger (theagentledger.com)
license: CC-BY-NC-4.0
---

# Launch Playbook Skill
**by [The Agent Ledger](https://theagentledger.com)**

> A repeatable launch management system for solopreneurs. Plan, execute, and learn from every launch — product, newsletter, course, campaign, or service offering.

---

## What This Skill Does

This skill turns your agent into a launch manager. It gives you:
- A standardized launch record format for any launch type
- Stage-gated checklists that prevent skipping critical steps
- Asset tracking (copy, graphics, links, sequences)
- Countdown integration via heartbeat or cron
- A post-launch retrospective system for compounding improvement
- A launch library so every future launch gets smarter

---

## Setup

### Step 1: Create the launch state file

Create `launches/launch-state.md` in your workspace:

```markdown
# Launch State

## Active Launches
| ID | Name | Type | Stage | Target Date | Status |
|----|------|------|-------|-------------|--------|
| — | — | — | — | — | — |

## Completed Launches
| ID | Name | Type | Launch Date | Result | Retrospective |
|----|------|------|-------------|--------|---------------|
| — | — | — | — | — | — |

## Launch Library
Total launches: 0
Average pre-launch prep time: —
Most common failure mode: —
```

### Step 2: Create your first launch record

When starting a new launch, create `launches/[YYYY-MM-DD]-[launch-name].md` using the template below.

### Step 3: Add to AGENTS.md (optional, recommended)

```markdown
## Launch Management
Launch records live in `launches/`. Use the launch-playbook skill for all launches.
Active launch state: `launches/launch-state.md`
Check for active launches in daily briefings.
```

---

## Launch Record Template

```markdown
# Launch: [Name]
**ID:** L-[YYYY-MM]-[###]
**Type:** [product | newsletter | course | campaign | service | event | other]
**Status:** [planning | pre-launch | live | complete | cancelled]
**Target Date:** YYYY-MM-DD
**Actual Date:** —
**Owner:** [your name or "me"]

---

## What We're Launching
[1-3 sentence description. What is it, who is it for, what problem does it solve?]

**Offer:**
**Price:** $[price] (or free)
**Target audience:**
**Primary CTA:**
**Landing page URL:** —

---

## Success Metrics
| Metric | Target | Actual |
|--------|--------|--------|
| Revenue / sign-ups | | |
| Email list growth | | |
| Social reach | | |
| Conversion rate | | |
| [Custom metric] | | |

---

## Launch Assets
| Asset | Status | Owner | Link/Path |
|-------|--------|-------|-----------|
| Landing page | [ ] | | |
| Email sequence (pre-launch) | [ ] | | |
| Email sequence (launch day) | [ ] | | |
| Email sequence (last chance) | [ ] | | |
| Social announcement post | [ ] | | |
| Social follow-up posts (3-5) | [ ] | | |
| Product/offer itself | [ ] | | |
| Thank-you page / onboarding | [ ] | | |
| FAQ document | [ ] | | |

---

## Stage Checklists

### 🔵 PLANNING (4+ weeks out)
- [ ] Offer defined (what it is, price, who it's for)
- [ ] Success metrics set (be specific: numbers)
- [ ] Target launch date confirmed
- [ ] Launch type categorized (see Launch Types reference)
- [ ] Key assets listed
- [ ] Dependencies identified (other launches, external events)
- [ ] Competitive landscape reviewed
- [ ] Positioning statement written

### 🟡 PRE-LAUNCH (1-3 weeks out)
- [ ] Landing page live (draft or full)
- [ ] Email sequences drafted
- [ ] Social content calendar blocked out
- [ ] All assets assigned and in progress
- [ ] Waitlist / early-access mechanism live (if using)
- [ ] Pricing finalized
- [ ] Payment processor tested (if applicable)
- [ ] Analytics / tracking set up
- [ ] Launch announcement drafted
- [ ] FAQ drafted
- [ ] Edge cases reviewed (refunds, overages, sold-out state)

### 🟠 LAUNCH WEEK (-7 to 0 days)
- [ ] All assets finalized and reviewed
- [ ] Launch email queued / scheduled
- [ ] Social posts queued / scheduled
- [ ] Thank-you page tested
- [ ] Payment flow tested end-to-end
- [ ] Team / collaborators briefed
- [ ] Contingency plan noted (what if page goes down, payment fails, etc.)
- [ ] "Launch day" calendar block set

### 🔴 LAUNCH DAY
- [ ] Launch email sent (time: ___)
- [ ] Social posts published (time: ___)
- [ ] Announcement confirmed live and working
- [ ] Initial response monitored
- [ ] First sales / sign-ups confirmed
- [ ] Issues log started (any bugs, confusion, feedback)

### ✅ POST-LAUNCH (1-14 days after)
- [ ] Final metrics collected
- [ ] Revenue / results tallied
- [ ] Customer feedback gathered
- [ ] Retrospective completed (use retrospective section below)
- [ ] Launch state file updated
- [ ] Learnings filed to launch library

---

## Issues Log
| Date | Issue | Impact | Resolution |
|------|-------|--------|------------|
| | | | |

---

## Post-Launch Retrospective

**Launch Date:**
**Duration active:**
**Final results vs targets:**

### What Worked
1.
2.
3.

### What Didn't Work
1.
2.
3.

### Surprises
(Anything you didn't expect — good or bad)

### What I'd Do Differently
1.
2.
3.

### Reusable Assets
(List anything that can be templated or reused for future launches)

### Key Learnings for Launch Library
(1-3 bullets that future-you should know)

**Overall rating:** [1-5] — [one-line summary]
```

---

## Launch Types Reference

| Type | Typical Timeline | Key Assets | Primary Success Metric |
|------|-----------------|------------|----------------------|
| **Digital product** | 4-8 weeks | Sales page, email sequence, checkout | Revenue |
| **Newsletter launch** | 2-4 weeks | Landing page, announcement posts, welcome email | Subscribers |
| **Course / cohort** | 6-12 weeks | Sales page, curriculum outline, waitlist, Zoom/platform | Enrollments |
| **Service offering** | 2-4 weeks | Service page, intake form, proposal template | Booked clients |
| **Free lead magnet** | 1-2 weeks | Download page, delivery email, thank-you sequence | Email opt-ins |
| **Campaign / promo** | 1-2 weeks | Promo email, social posts, coupon/landing page | Conversions |
| **Event / webinar** | 3-6 weeks | Registration page, reminder emails, slide deck | Registrations + attendance rate |
| **Community launch** | 4-8 weeks | Community platform, onboarding, invitation emails | Active members |

---

## Usage Patterns

### 1. Start a New Launch
```
I'm planning a [product/course/newsletter/campaign] launch. Target date: [DATE].
Brief description: [what it is].
Create a launch record and populate the planning checklist.
```
The agent will create `launches/YYYY-MM-DD-[name].md` and update launch-state.md.

---

### 2. Launch Status Check
```
Give me a status update on the [launch name] launch.
What stage are we in, what's checked off, and what's next?
```
Useful for weekly check-ins or before working on launch assets.

---

### 3. Complete a Checklist Item
```
Mark "[checklist item]" as complete for the [launch name] launch.
[Optional: add any notes, links, or context.]
```

---

### 4. Countdown Briefing
```
How many days until the [launch name] launch?
What items are still incomplete? What's most urgent?
```
Use in your daily briefing or as a heartbeat trigger.

---

### 5. Launch Day Brief
```
Today is launch day for [launch name].
Walk me through the launch day checklist and confirm everything is ready.
```

---

### 6. Log an Issue
```
Log an issue for the [launch name] launch:
Issue: [what happened]
Impact: [who was affected, how severely]
```

---

### 7. Post-Launch Retrospective
```
The [launch name] launch is complete. Final results:
- [metric 1]: [actual vs target]
- [metric 2]: [actual vs target]
Run a post-launch retrospective and update the launch library.
```

---

### 8. Review Launch Library
```
Review my launch library.
What patterns do I see? What's working across launches?
What should I prioritize improving for my next launch?
```
Works best after 3+ completed launches.

---

### 9. Build a Launch Calendar
```
I have these upcoming launches planned:
- [launch 1]: [target date]
- [launch 2]: [target date]
Build a launch calendar and flag any conflicts or overlap risks.
```

---

### 10. Asset Generation Request
```
I need to draft the launch announcement email for [launch name].
Key offer: [offer]. Price: [price]. Audience: [who].
Draft this using my writing voice. [Optional: reference existing brand voice file.]
```
Pairs with the writing-assistant skill.

---

## Heartbeat Integration

Add to `HEARTBEAT.md` to get launch countdown reminders:

```markdown
## Launch Monitoring
Check `launches/launch-state.md` for active launches.
If any active launch has a target date within 14 days:
- Show days remaining
- List top 3 incomplete checklist items
- Flag any overdue items (items that should have been done by now based on stage)
If no active launches, skip this section.
```

---

## Cron Setup (Alternative to Heartbeat)

For a daily 8 AM launch brief:
```
openclaw cron add \
  --name "launch-brief" \
  --cron "0 8 * * *" \
  --model "anthropic/claude-sonnet-4-6" \
  --session isolated \
  --message "Check launches/launch-state.md for active launches. For each active launch within 14 days of its target date: show days remaining, list 3 most urgent incomplete checklist items, flag any overdue items. Keep it brief." \
  --announce \
  --to "[your-channel-id]" \
  --tz "America/Chicago"
```

---

## Integration Map

| Skill | How They Connect |
|-------|----------------|
| **content-calendar** | Block out launch content in the calendar; sync launch dates to content pipeline |
| **writing-assistant** | Draft all launch copy: emails, landing page, social posts, announcements |
| **social-media-manager** | Queue and track social launch content across platforms |
| **financial-tracker** | Log launch revenue; compare actual vs projected; track ROI |
| **project-tracker** | Track launch as a project with milestones and task breakdown |
| **goal-tracker** | Tie launch to quarterly goals; update KR progress when launch completes |
| **research-assistant** | Competitive research, audience research, pricing validation pre-launch |
| **decision-log** | Log major launch decisions (pricing, timing, scope) for future reference |
| **habit-tracker** | Track daily launch prep activities during runway |
| **solopreneur-assistant** | Include launch status in weekly business review |

---

## Customization

### Multiple Launch Tracks
If you're running multiple concurrent launches, maintain separate records and use the launch-state.md dashboard to track all at once. Add a "track" field to each record (e.g., Track A: products, Track B: services).

### Launch Templates
After 2-3 launches of the same type, create a reusable template:
```markdown
## Template: [Type] Launch
Based on L-[ID] and L-[ID].
Average prep time: X weeks.
Standard asset list: [...]
Watch out for: [common failure mode]
```
Store in `launches/templates/`.

### Minimal Launch Mode
For small promos or quick campaigns (under 1 week), use a simplified checklist:
```markdown
## Quick Launch Checklist
- [ ] Offer clear and compelling
- [ ] CTA / link confirmed working
- [ ] Email drafted and reviewed
- [ ] 1-2 social posts ready
- [ ] Results will be measured by: [metric]
```

### Team / Collaborator Use
Add an "Owner" column to each checklist item. Route completion updates through a shared channel or use sessions to coordinate.

---

## Troubleshooting

**"I don't know what stage I'm in."**
Read the Stage Checklists section. Count completed items — the stage with the most completions but incomplete items is your current stage.

**"The launch is in 3 days and nothing is done."**
Use the Launch Day Brief pattern and triage: mark all non-critical items as deferred. Focus only on: landing page, payment flow, launch email, and one social post.

**"I keep launching the same way and getting mediocre results."**
Run a launch library review (Pattern 8). Look for systemic issues: Are you launching too fast? Is your email list warm? Are you tracking the right metrics?

**"My launch files are getting messy."**
Archive completed launches to `launches/archive/YYYY/` after retrospective. Keep active launches in `launches/` root.

---

## Privacy Note
All launch records are stored locally in your workspace. No data is sent anywhere automatically. The agent will never publish, email, or post on your behalf — you confirm every external action.

---

*Launch Playbook Skill v1.0.0 — by [The Agent Ledger](https://theagentledger.com)*
*Free for personal use under CC-BY-NC-4.0. For commercial redistribution, contact us.*
*Subscribe at theagentledger.com for new skills, guides, and automation playbooks.*
