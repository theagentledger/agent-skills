---
name: idea-vault
version: 1.0.0
description: >
  Systematic business idea capture, scoring, and lifecycle management for solopreneurs and builders.
  Use when: capturing a new idea, reviewing your idea backlog, evaluating a specific idea, graduating an
  idea to active project, or running a monthly idea audit. NOT for: task management, project execution
  tracking (use project-tracker), or goal setting (use goal-tracker).
tags: [ideas, ideation, strategy, solopreneur, productivity, decision-making]
platforms: [openclaw, cursor, windsurf, generic]
category: strategy
author: The Agent Ledger
license: CC-BY-NC-4.0
---

# Idea Vault

*by [The Agent Ledger](https://theagentledger.com) — The newsletter on building AI-native businesses.*

Every solopreneur has more ideas than hours. The problem isn't the idea — it's that ideas live in your head, your notes app, a dozen open browser tabs, and the shower. They compete for attention equally, whether they're worth $0 or $100K/year.

The Idea Vault gives your ideas a home with a lifecycle. Capture them fast. Score them honestly. Review them systematically. Graduate the winners. Kill the rest with dignity.

---

## What This Skill Does

- **Captures** new ideas in a structured format (quick or detailed)
- **Scores** ideas across 4 dimensions: revenue potential, effort, alignment, novelty
- **Tracks** ideas through a 5-stage pipeline: Raw → Researched → Validated → Active / Parked / Killed
- **Reviews** your backlog on a weekly quick-scan and monthly deep-review cadence
- **Graduates** validated ideas to project-tracker with a handoff brief
- **Resurrects** parked ideas on a schedule (some ideas are just early)
- **Surfaces** patterns across your idea history (what do you keep returning to?)

---

## Setup

### 1. Create the Vault File

Create `ideas/idea-vault.md` in your workspace with this structure:

```markdown
# Idea Vault

## Active Pipeline

### Raw (unscored captures)
<!-- New ideas land here first -->

### Researched (scored, needs validation)
<!-- Ideas that have been scored and deserve a closer look -->

### Validated (ready to build or launch)
<!-- Evidence gathered, worth committing to -->

## Parking Lot
<!-- Good ideas, wrong timing. Check quarterly. -->

## Archive
### Graduated → Active Projects
<!-- Ideas that became real projects -->

### Killed
<!-- Ideas you evaluated and consciously rejected. Record why. -->
```

### 2. Create the Scoring Reference

Save this in your working notes or at the top of `idea-vault.md`:

```
IDEA SCORE DIMENSIONS (rate each 1-5):
  R — Revenue Potential: Can this make meaningful money? (5 = $100K+ path)
  E — Effort Inverse: How easy to build/launch? (5 = hours, 1 = months)
  A — Alignment: Fits your skills, audience, and goals? (5 = perfect fit)
  N — Novelty: Is this defensibly different? (5 = clear gap in market)

Total = R + E + A + N (max 20)
  16-20: Prioritize immediately
  11-15: Research before committing
  6-10: Park with a review date
  1-5: Kill unless there's a specific reason to keep
```

### 3. Add AGENTS.md Standing Instructions (Optional)

Add to your AGENTS.md or HEARTBEAT.md:

```
## Idea Vault
- When I say "idea:" followed by anything, capture it to ideas/idea-vault.md under Raw
- During weekly review, flag any Raw ideas older than 14 days that haven't been scored
- During monthly review, check Parking Lot ideas with "revisit by" dates that have passed
```

---

## Usage Patterns

### 1. Quick Capture

> "Idea: subscription box for solopreneurs — curated AI tools + resources, $29/month"

The agent captures this to the Raw section with a timestamp and no further friction. Scoring happens later.

**Capture format:**
```
**[IDEA-###] Title**
Captured: YYYY-MM-DD
Source: shower / conversation / competitor / market gap / other
One-liner: [What it is in one sentence]
Status: Raw
Notes: [Optional initial context]
```

### 2. Score an Idea

> "Score IDEA-042 — AI newsletter tools bundle"

The agent walks through each scoring dimension and fills in the rubric, producing:

```
**IDEA-042 Score**
R (Revenue): 4/5 — Newsletter tools have clear willingness to pay; bundle could do $500-2K MRR at scale
E (Effort): 3/5 — Curation work upfront, but no code needed; 2-4 weeks to MVP
A (Alignment): 5/5 — Perfect fit: AI tools, newsletter audience, solopreneur focus
N (Novelty): 3/5 — Bundle concept exists, but AI-specific + editorial curation is differentiator

Total: 15/20 — RESEARCH
Next step: Interview 5 newsletter subscribers about their AI tool spend. Set revisit: 2 weeks.
```

Move to Researched.

### 3. Research Update

> "Update IDEA-042: talked to 8 newsletter readers, 6 said they'd pay $19-29/month for curated stack"

The agent logs the research finding, recalculates if score changes, and notes what validation step comes next.

### 4. Full Idea Review Session

> "Run my idea review"

The agent goes through the pipeline systematically:

```
📦 IDEA VAULT REVIEW — [Date]

RAW (unscored): 6 ideas
  ⚠️ 2 ideas > 14 days old — flag for scoring or kill
  Oldest: IDEA-039 (23 days) — "AI-powered Etsy listing optimizer"
  
RESEARCHED: 4 ideas
  1 idea ready to validate (score 15+): IDEA-042
  2 ideas stalled (no activity 21+ days): IDEA-037, IDEA-040
  
VALIDATED: 1 idea
  IDEA-038: "Daily briefing cron template pack" — 18/20, waiting on capacity

PARKING LOT: 9 ideas
  3 ideas past revisit date — surfacing for review
  
KILLED (last 90 days): 12 ideas
  Pattern detected: 3 killed ideas involved physical products → possible blind spot

ACTION ITEMS:
  1. Score IDEA-039 or kill it — it's been sitting
  2. Advance IDEA-042 to Validated (validation evidence gathered)
  3. Review IDEA-037, IDEA-040 — stalled in Researched
  4. Revisit parked ideas #034, #031, #027 (past their review dates)
```

### 5. Graduate Idea to Project

> "Graduate IDEA-042 to project-tracker"

The agent creates a handoff brief:

```
**IDEA-042 → PROJECT HANDOFF**
Idea: AI Newsletter Tools Bundle
Final Score: 16/20
Validation: 8 reader interviews, 75% positive; comparable product research done
Revenue Model: $19-29/month subscription, targeting 50 subs at launch
Launch Scope: Curation-only v1 (no code), biweekly drops, Google Doc delivery
Next Step: Outline curation criteria → select first 10 tools → write intro email

→ Create project file: projects/ai-newsletter-tools-bundle.md
→ Link to decision-log entry for the go/no-go decision
→ Archive IDEA-042 to Graduated section with graduation date
```

### 6. Kill an Idea Properly

> "Kill IDEA-031 — I've looked at this 4 times and never start it"

```
**IDEA-031 KILLED — [Date]**
Reason: Repeatedly deprioritized; lack of genuine motivation despite good score
Lesson: High score ≠ high desire. Execution requires wanting to, not just calculating that I should.
Future signal: If this resurfaces in 6+ months, that's genuine pull — recapture then.
```

Killed ideas stay in the archive. The kill reasons are often the most valuable part of the vault.

### 7. Resurrect a Parked Idea

> "Check parking lot — what's overdue for review?"

The agent surfaces parked ideas past their revisit date, with a brief context refresh and a binary prompt: **keep parking, promote, or kill**.

### 8. Idea Pattern Analysis

> "What patterns do you see in my idea history?"

The agent reviews the vault (including killed ideas) and surfaces:
- What categories do you keep returning to? (content, tools, services, physical)
- What scores consistently high but never gets built? (motivation gap vs capacity gap)
- What kills most often? (market risk, effort, misalignment)
- Time between capture and kill/graduation (your natural evaluation pace)

---

## Idea Pipeline Reference

| Stage | Description | Trigger to Advance | Trigger to Kill |
|---|---|---|---|
| **Raw** | Just captured, unscored | Score it | Still here in 30 days with no interest |
| **Researched** | Scored, initial research done | Score 11+, validation plan exists | Score drops below 8 after research |
| **Validated** | Evidence gathered, go/no-go decision point | Committed to build | Evidence doesn't support the thesis |
| **Active** | Graduated to project-tracker | — | Project killed (archive in decision-log) |
| **Parked** | Good idea, wrong time | Revisit date arrives, timing changed | Revisited 3+ times with no action |
| **Killed** | Consciously rejected | — (permanent) | — |

---

## Idea Score Quick Reference

```
R — Revenue Potential
  5: Clear $100K+/year path with reasonable effort
  4: $10K-100K/year plausible
  3: $1K-10K/year, modest ceiling
  2: Revenue possible but unclear how to monetize
  1: Essentially non-commercial

E — Effort Inverse (how EASY, not how hard)
  5: Can launch in hours or days (template, guide, curation)
  4: Launch in 1-2 weeks
  3: Launch in 1-2 months
  2: Launch in 3-6 months
  1: Year+ or requires co-founder/funding

A — Alignment (skills + audience + goals)
  5: You have the skills, it serves your audience, it fits your goals
  4: Strong in 2 of 3
  3: Strong in 1, workable in others
  2: You're stretching significantly
  1: Outside your wheelhouse entirely

N — Novelty / Differentiation
  5: Clear gap, no obvious competitor, strong point of view
  4: Crowded space but meaningfully differentiated
  3: Similar to existing solutions, defensible niche
  2: Similar to many competitors, differentiation unclear
  1: Undifferentiated commodity
```

---

## Heartbeat Integration

Add to HEARTBEAT.md for periodic idea maintenance:

```markdown
## Idea Vault Check (weekly)
- Flag any Raw ideas older than 14 days
- Surface Researched ideas with no activity in 21+ days
- Note any Parking Lot ideas past their revisit date
- Report: [# Raw] [# Researched] [# Validated] [# Parked]
```

For a monthly deep review, add a cron:

```
openclaw cron add \
  --name "monthly-idea-review" \
  --cron "0 10 1 * *" \
  --model "anthropic/claude-sonnet-4-6" \
  --session isolated \
  --message "Run a full Idea Vault review: score any unscored Raw ideas, flag stalled Researched ideas, surface Parking Lot items past their revisit dates, and identify any patterns in killed ideas from the past quarter. Report findings." \
  --announce \
  --to "[YOUR_TELEGRAM_CHAT_ID]" \
  --tz "America/Chicago"
```

---

## Integration with Other Agent Ledger Skills

| Skill | How They Connect |
|---|---|
| **decision-log** | Log go/no-go decisions when graduating or killing an idea |
| **project-tracker** | Graduated ideas become projects — handoff brief creates the project file |
| **goal-tracker** | Validate that an idea serves your current quarter's goals before advancing |
| **research-assistant** | Use for deep-dive on Researched ideas (market sizing, competitor analysis) |
| **financial-tracker** | Track revenue from graduated ideas; compare projected vs actual |
| **solopreneur-assistant** | Weekly business review includes Idea Vault status summary |
| **content-calendar** | Ideas can spawn content (newsletter angle, tutorial) even if not built |

---

## Customization

**Adjust scoring weights:**
If revenue is your primary filter, weight R × 2 in your total. If you're optimizing for learning, weight A higher. The default equal-weight rubric is a starting point.

**Add custom dimensions:**
Some builders add a 5th dimension: **P (Personal Enjoyment)** — would you actually enjoy building and running this? A score of 1 is a silent project killer.

**Idea categories:**
Tag ideas with a category (product, service, content, tool, community, other) to spot patterns over time.

**Team use:**
If you have a collaborator, add a "Submitted by" field and a "Champion" field (who owns evaluation). Ideas without a champion stall.

**Kill threshold:**
Default is to kill ideas scored below 8. If you're early-stage and still exploring, lower to 6. If you're focused, raise to 12.

---

## Troubleshooting

**"My vault is full of Raw ideas and nothing gets scored"**
→ Set a rule: no new captures without scoring one existing Raw idea first. Or batch-score every Sunday (15 minutes max).

**"I score ideas high but never build them"**
→ Add the P (Personal Enjoyment) dimension. A 4 REAM score that feels like work is a trap. Also check your goal-tracker — are ideas competing with committed goals?

**"I keep resurrecting the same idea without making progress"**
→ Treat the third resurface as a forcing function: either commit to a validation step with a deadline, or kill it permanently. Endless parking is just soft avoidance.

**"My scores feel arbitrary"**
→ Calibrate against your track record. Look at your graduated projects and their original scores. Adjust the rubric until past scores match what you now know about those projects.

---

## Privacy Note

The Idea Vault stores everything locally. No content is transmitted externally unless you explicitly instruct your agent to share it. Your un-built ideas are competitively sensitive — treat this file accordingly (don't share it in group chats or multi-agent contexts with external access).

---

*[The Agent Ledger](https://theagentledger.com) — Building AI-native businesses, one system at a time.*
*Subscribe for weekly insights on agent setup, automation, and solopreneur strategy.*

---

**See also:** `references/advanced-patterns.md` for idea tournament protocols, opportunity cost tracking, seasonal idea batches, and validation sprint frameworks.

**License:** CC-BY-NC-4.0 — Free to use and adapt for non-commercial purposes. Please credit The Agent Ledger.
