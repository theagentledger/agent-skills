---
name: Learning Journal
version: 1.0.0
description: >
  AI-native learning and knowledge management system. Tracks what you're studying,
  manages reading lists and course progress, implements spaced repetition review
  prompts, captures key takeaways from books/articles/courses/podcasts, and runs
  weekly knowledge reviews. Designed for autodidacts and professionals who learn
  constantly but struggle to retain and apply what they learn. Integrates with
  goal-tracker, research-assistant, and content-calendar skills.
tags:
  - learning
  - knowledge-management
  - study
  - reading
  - retention
  - self-improvement
platforms:
  - openclaw
  - cursor
  - windsurf
  - generic
category: productivity
author: The Agent Ledger
license: CC-BY-NC-4.0
---

# Learning Journal

**By [The Agent Ledger](https://theagentledger.com)** — AI-native learning system for people who consume more than they retain.

> Your agent tracks what you're learning, prompts you to review key concepts, and makes sure knowledge actually sticks — and gets applied.

---

## The Problem

You read 30 articles a week. You listen to podcasts. You take courses. But 3 months later, you can't recall the key insight from that book that "changed everything." The consumption-to-retention ratio for most people is terrible.

This skill turns your AI agent into a learning partner that captures, organizes, reviews, and connects knowledge over time.

---

## Setup

### Step 1: Create State File

Create `learning/learning-state.md` in your workspace:

```markdown
# Learning State

## Active Learning Tracks
| Track | Type | Source | Started | Progress | Priority |
|-------|------|--------|---------|----------|----------|
| [Topic] | Book | [Title by Author] | YYYY-MM-DD | 35% | High |
| [Topic] | Course | [Course name — platform] | YYYY-MM-DD | 60% | Medium |
| [Topic] | Self-directed | [Description] | YYYY-MM-DD | Ongoing | Low |

## Learning Goals (This Quarter)
1. [Finish X] — deadline: [date]
2. [Understand Y well enough to Z] — no deadline, but priority
3. [Build skill in Z] — measurable: [what would prove it]

## Review Schedule
- Daily: Quick review of yesterday's captures (2 min)
- Weekly: Full review + connect to existing knowledge (15 min)
- Monthly: Retention check on older material
```

### Step 2: Create Captures Directory

Create `learning/captures/` for individual learning notes. One file per source:

```markdown
# [Source Title]
**Type:** Book / Article / Course / Podcast / Video / Experience
**Author/Creator:** [name]
**Date captured:** YYYY-MM-DD
**Status:** Reading / Completed / Abandoned
**Rating:** [1-5] how valuable

## Key Takeaways
1. [Most important insight]
2. [Second most important]
3. [Third]

## Memorable Quotes
> "[Quote]" — [context/page]

## How This Applies to My Work
- [Specific application to your projects/business]
- [Connection to something you already know]

## Questions It Raised
- [Things you want to explore further]

## Review History
| Date | Recall Score | Notes |
|------|-------------|-------|
| YYYY-MM-DD | 4/5 | Remembered core thesis, fuzzy on details |
```

### Step 3: Add to AGENTS.md

```markdown
## Learning
- When I share an article, book note, or learning, capture it in `learning/captures/`
- During weekly reviews, prompt me on items due for review
- Connect new learnings to existing captures when relevant
- Track my learning goals in `learning/learning-state.md`
- Suggest review when I haven't revisited a high-value capture in 30+ days
```

---

## Usage Patterns

### "I just read [article/book/watched video]"
Agent creates a capture file, asks targeted questions to extract key takeaways:
- "What was the single most important idea?"
- "How does this relate to what you're working on?"
- "What would you do differently based on this?"

### "Add [book/course] to my reading list"
Agent updates learning-state.md with new entry, suggests priority based on current goals and active tracks.

### "What should I review?"
Agent checks review dates across captures and surfaces:
- Items never reviewed (captured but never revisited)
- Items due for spaced repetition (7 days → 30 days → 90 days)
- High-value captures (rating 4-5) that haven't been reviewed in 30+ days

### "Connect this to what I already know"
Agent searches existing captures for related concepts and shows connections:
```markdown
## Connections Found
- **[New capture]** relates to **[Existing capture]**
  - Shared concept: [what they have in common]
  - Tension: [where they disagree or offer different perspectives]
  - Combined insight: [what you get from both together]
```

### "Learning review"
Weekly format:

```markdown
## Weekly Learning Review — [Date]

### This Week's Captures
| Source | Type | Rating | Key Insight |
|--------|------|--------|-------------|
| [Title] | Article | 4/5 | [One-liner] |

### Review Prompts (Spaced Repetition)
1. **[Capture from 7 days ago]:** Can you recall the main argument? [Y/N → update recall score]
2. **[Capture from 30 days ago]:** What was the key takeaway? [Y/N]
3. **[Capture from 90 days ago]:** How has this influenced your thinking? [Reflect]

### Learning Track Progress
| Track | Last Week | This Week | Notes |
|-------|-----------|-----------|-------|
| [Topic] | 35% | 42% | Read chapters 8-10 |

### Applications This Week
- Applied [concept from X] to [project/decision]
- [Concept from Y] contradicted my assumption about [Z]

### Next Week Focus
- Priority reading: [what to focus on]
- Review due: [N items need revisiting]
```

### "Quiz me on [topic/capture]"
Agent generates questions from a capture to test retention:
- Recall questions ("What were the 3 types of X?")
- Application questions ("How would you apply X to your current project?")
- Synthesis questions ("How does X relate to Y that you learned last month?")

### "What have I learned about [topic]?"
Agent searches all captures for a topic and synthesizes:
```markdown
## Knowledge Summary: [Topic]

### Sources (chronological)
1. [Source 1] — [date] — Key point: [...]
2. [Source 2] — [date] — Key point: [...]

### Synthesized Understanding
[What you know about this topic, combining all sources]

### Evolution of Thinking
- Initially thought: [earlier captures]
- Now believe: [later captures, updated views]

### Gaps
- Still unclear on: [questions that remain]
- Should read: [suggested next sources]
```

---

## Spaced Repetition Schedule

The skill uses a simple spaced repetition system:

| Review | After | Purpose |
|--------|-------|---------|
| First | 1 day | Immediate recall check |
| Second | 7 days | Short-term retention |
| Third | 30 days | Medium-term retention |
| Fourth | 90 days | Long-term retention |
| Ongoing | 180 days | Refresh if still relevant |

Each review updates the recall score (1-5):
- **5:** Perfect recall, can explain to others
- **4:** Good recall, minor details fuzzy
- **3:** Partial recall, needed prompting
- **2:** Vague recall, couldn't explain it
- **1:** No recall, basically learning it fresh

Items scoring 1-2 get moved to a shorter review cycle. Items scoring 5 consistently can be marked "internalized" and removed from active review.

---

## Reading List Management

```markdown
## Reading List

### Currently Reading
| # | Title | Author | Type | Started | Progress | Priority |
|---|-------|--------|------|---------|----------|----------|
| 1 | [Book] | [Author] | Book | 3/1 | 45% | 🔴 High |
| 2 | [Course] | [Platform] | Course | 2/15 | 80% | 🟡 Medium |

### Up Next (Prioritized)
| # | Title | Author | Type | Why | Added |
|---|-------|--------|------|-----|-------|
| 1 | [Book] | [Author] | Book | [Reason/recommendation] | 2/28 |
| 2 | [Course] | [Platform] | Course | [Reason] | 3/1 |

### Completed (Last 90 Days)
| Title | Type | Rating | Capture? | Key Insight |
|-------|------|--------|----------|-------------|
| [Book] | Book | 4/5 | ✅ | [One-liner] |

### Abandoned
| Title | Type | Why Abandoned | Worth Revisiting? |
|-------|------|--------------|-------------------|
| [Book] | Book | Too basic for current level | No |
```

---

## Customization

### Learning Styles
Adapt capture format to how you learn:
- **Visual learner:** Include diagram descriptions, spatial relationships
- **Practical learner:** Emphasize "How to apply" section, include exercises
- **Conceptual learner:** Focus on frameworks, mental models, principles
- **Social learner:** Note who recommended it, discussion points, teaching opportunities

### Domain-Specific Templates
Create capture templates for common source types:
- **Technical books:** Code examples section, implementation notes
- **Business books:** Framework summary, when-to-use guide
- **Research papers:** Methodology notes, limitations, replication potential
- **Podcasts:** Timestamped highlights, guest background

### Knowledge Areas
Track breadth across learning domains:
```markdown
## Knowledge Map
| Domain | Captures | Last Active | Depth |
|--------|----------|-------------|-------|
| Business strategy | 12 | 2 days ago | Deep |
| Machine learning | 3 | 45 days ago | Surface |
| Writing | 7 | 10 days ago | Moderate |
| Finance | 15 | 1 day ago | Deep |
```

---

## Integration with Other Skills

| Skill | Integration |
|-------|-------------|
| **goal-tracker** | Learning goals as quarterly OKRs; capture progress as KR updates |
| **research-assistant** | Research findings auto-captured as learning entries |
| **content-calendar** | Turn high-value captures into content (teach what you learn) |
| **writing-assistant** | Use captures as source material for articles and posts |
| **decision-log** | Reference relevant learnings when making decisions |
| **habit-tracker** | Track daily reading/learning as a habit |

---

## Heartbeat Integration

Add to `HEARTBEAT.md`:
```markdown
## Learning Check
- Any captures due for spaced repetition review?
- Has it been >7 days since last capture? (consumption without capture = waste)
- Any learning tracks stalled for >14 days?
```

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Captures too long | Limit to 3 key takeaways max; depth goes in references |
| Never reviewing | Set up cron for weekly review prompt; start with just 3 items |
| Too many active tracks | Cap at 3 simultaneous; finish or pause before starting new ones |
| Captures feel useless | Focus "How This Applies" section — if you can't fill it, the source may not be valuable |
| Reading list growing forever | Monthly prune: remove anything added 60+ days ago that you haven't started |
| Can't recall anything | Normal for first 30 days; spaced repetition needs 2-3 cycles to work |

---

## Privacy & Safety

- All learning data stays in your local workspace
- No external API calls for tracking (pure file-based)
- Captures may contain copyrighted quotes — keep for personal use only
- Agent never auto-shares your reading list or learning notes

---

*Part of the [Agent Skills Collection](https://github.com/theagentledger/agent-skills) by The Agent Ledger.*
*Subscribe at [theagentledger.com](https://theagentledger.com) for the premium guide and new skills.*
