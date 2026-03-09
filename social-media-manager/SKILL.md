---
name: Social Media Manager
version: 1.0.0
description: >
  AI-native social media management system. Tracks posting schedules across platforms
  (Twitter/X, LinkedIn, Instagram, Threads, Reddit, TikTok), manages content queues,
  tracks engagement metrics, suggests optimal posting times, handles repurposing workflows,
  and runs weekly performance reviews. Designed for solopreneurs who want consistent
  social presence without hiring a social media manager. Integrates with content-calendar,
  writing-assistant, and research-assistant skills.
tags:
  - social-media
  - marketing
  - content
  - scheduling
  - analytics
  - engagement
platforms:
  - openclaw
  - cursor
  - windsurf
  - generic
category: marketing
author: The Agent Ledger
license: CC-BY-NC-4.0
---

# Social Media Manager

**By [The Agent Ledger](https://theagentledger.com)** — AI-native social media system for solopreneurs.

> Your agent manages your social presence across platforms — scheduling, repurposing, tracking engagement, and telling you what's actually working.

---

## What This Does

Most solopreneurs know they should post consistently but can't sustain it. This skill turns your AI agent into a social media manager that:

- Maintains a **posting queue** per platform with scheduled dates
- Tracks **engagement metrics** (likes, comments, shares, clicks) per post
- Identifies **what's working** through weekly performance analysis
- **Repurposes content** across platforms (one idea → 5 posts)
- Suggests **optimal posting times** based on your engagement data
- Monitors **reply/DM triage** priorities
- Runs **weekly social media reviews** with actionable insights

---

## Setup

### Step 1: Create State File

Create `social-media/social-state.md` in your workspace:

```markdown
# Social Media State

## Platforms
| Platform | Handle | Status | Posting Cadence | Best Times |
|----------|--------|--------|-----------------|------------|
| Twitter/X | @yourhandle | Active | 5x/week | 9am, 12pm, 5pm |
| LinkedIn | /in/yourname | Active | 3x/week | 8am, 12pm Tue-Thu |
| Reddit | u/yourname | Active | 2x/week | 10am, 7pm |

## Content Pillars
1. [Your expertise topic] — educational, how-to
2. [Your story/journey] — behind-the-scenes, lessons learned
3. [Industry commentary] — opinions, trends, reactions
4. [Community engagement] — questions, polls, responses

## Voice Notes
- Tone: [casual/professional/witty/authoritative]
- Emoji usage: [none/minimal/moderate/heavy]
- Hashtag strategy: [none/1-2 per post/platform-specific]
```

### Step 2: Create Queue File

Create `social-media/queue.md`:

```markdown
# Social Media Queue

## Drafts (Ready to Post)
| # | Platform | Content | Pillar | Scheduled | Status |
|---|----------|---------|--------|-----------|--------|
| 1 | Twitter | [draft text] | Education | Mon 9am | Ready |
| 2 | LinkedIn | [draft text] | Journey | Tue 8am | Ready |

## Ideas (Need Drafting)
- [Topic idea from article/conversation/trend]
- [Repurpose from newsletter #X]
- [React to [trending topic]]

## Posted (Last 7 Days)
| Date | Platform | Content Preview | Likes | Comments | Shares | Clicks |
|------|----------|----------------|-------|----------|--------|--------|
```

### Step 3: Add to AGENTS.md

```markdown
## Social Media
- Check `social-media/queue.md` when I ask about social content
- Draft posts matching my voice profile in `social-media/social-state.md`
- Track engagement metrics when I share them
- NEVER auto-post — always draft and wait for approval
- Repurpose long-form content (newsletters, blogs) into platform-native posts
```

---

## Usage Patterns

### "Draft this week's social posts"
Agent reviews content pillars, recent posts, upcoming content calendar items, and drafts a week of posts across all active platforms. Balances pillars and varies formats (text, thread, question, hot take).

### "Log engagement for [post]"
Agent updates the Posted table with metrics. Over time, builds a dataset of what performs.

### "What's working on [platform]?"
Agent analyzes recent engagement data:
- Top-performing post types (threads vs. single, questions vs. statements)
- Best posting times (actual data vs. assumptions)
- Which content pillars get most engagement
- Follower growth trends
- Engagement rate calculations

### "Repurpose [content] for social"
Agent takes a newsletter, blog post, or long-form piece and creates platform-native versions:
- **Twitter/X:** Thread (5-8 tweets) + standalone hook tweet
- **LinkedIn:** Professional narrative version (~200 words)
- **Reddit:** Discussion-style post with genuine question angle
- **Instagram:** Carousel concept (slide-by-slide text)

### "Social media review"
Weekly performance review format:

```markdown
## Weekly Social Review — [Date Range]

### Performance Summary
| Platform | Posts | Avg Likes | Avg Comments | Best Post | Worst Post |
|----------|-------|-----------|-------------|-----------|------------|

### What Worked
- [Specific post] got [X] engagement because [analysis]

### What Didn't
- [Specific post] underperformed because [analysis]

### Recommendations
1. Post more [type] on [platform] — consistently 2x avg engagement
2. Reduce [type] — below average 3 weeks running
3. Test [new approach] based on [trend/data]

### Next Week's Focus
- Pillar emphasis: [based on what's working]
- Experiments to run: [one new format/time/topic]
```

### "Batch-create content from [source]"
Agent takes one source (podcast, article, experience) and generates a full content batch:
- 3 tweets (different angles)
- 1 LinkedIn post
- 1 Reddit discussion
- 3 Instagram caption options
- 1 thread outline

### "Triage my replies/DMs"
Agent reviews pending social interactions and prioritizes:
- 🔴 **Respond now:** Potential leads, partnership offers, direct questions
- 🟡 **Respond today:** Meaningful comments, community engagement
- 🔵 **Optional:** Generic likes, simple agreements
- ⚫ **Skip:** Spam, trolls, no-value interactions

---

## Posting Time Optimization

After 2+ weeks of engagement data, agent can analyze optimal times:

```markdown
## Optimal Posting Times (Based on [X] posts)

### Twitter/X
| Day | Best Time | Avg Engagement | Sample Size |
|-----|-----------|---------------|-------------|
| Mon | 9:15 AM | 47 interactions | 8 posts |
| Tue | 12:30 PM | 62 interactions | 6 posts |
...

### Confidence Level
- High (20+ data points): Mon, Wed, Thu
- Medium (10-19): Tue, Fri
- Low (<10): Sat, Sun — need more data
```

---

## Content Pillar Rotation

Prevent repetitive content by tracking pillar distribution:

```markdown
## Pillar Distribution (Last 30 Days)
| Pillar | Posts | % | Target % | Status |
|--------|-------|---|----------|--------|
| Education | 12 | 40% | 35% | ✅ On track |
| Journey | 6 | 20% | 25% | ⚠️ Slightly under |
| Commentary | 8 | 27% | 25% | ✅ On track |
| Community | 4 | 13% | 15% | ⚠️ Slightly under |
```

---

## Platform-Specific Notes

### Twitter/X
- Threads outperform single tweets 2-3x on average
- Hook tweet is everything — spend 50% of effort on first line
- Quote tweets with commentary > plain retweets
- Reply-to-self threads keep engagement in one place

### LinkedIn
- First line appears in feed preview — make it a hook
- Personal stories outperform corporate content
- Formatting matters: short paragraphs, line breaks, occasional emoji
- Best engagement: Tue-Thu mornings

### Reddit
- Genuine discussion > self-promotion (communities detect and punish shilling)
- Build karma with valuable comments before posting own content
- Match subreddit culture and norms exactly
- Never cross-post the same content to multiple subs simultaneously

### Instagram
- Carousel posts get 3x more engagement than single images
- Caption structure: hook → value → CTA → hashtags
- Stories for behind-the-scenes, posts for polished content
- Reels algorithm favors consistent posting cadence

---

## Customization

### Multi-Account Management
Track separate accounts (personal + business, multiple brands):
```markdown
## Accounts
| Account | Platform | Purpose | Voice | Cadence |
|---------|----------|---------|-------|---------|
| @personal | Twitter | Thought leadership | Casual, witty | 3x/week |
| @business | Twitter | Product updates | Professional | 5x/week |
| @personal | LinkedIn | Career/networking | Professional | 2x/week |
```

### Engagement Goals
Set measurable targets:
```markdown
## Monthly Goals — [Month]
| Platform | Metric | Target | Current | Status |
|----------|--------|--------|---------|--------|
| Twitter | Followers | +200 | +147 | 🟡 73% |
| Twitter | Avg likes/post | 25 | 31 | ✅ 124% |
| LinkedIn | Post impressions | 5,000 | 3,200 | 🟡 64% |
```

### Content Templates
Save reusable post structures:
```markdown
## Templates
### Hot Take
"Unpopular opinion: [contrarian view]\n\n[3 supporting points]\n\nHere's why this matters: [one sentence]"

### Thread Hook
"I [did X] and learned [Y].\n\nHere are [N] lessons (thread 🧵):"

### Question Post
"Genuine question for [audience]:\n\n[question]\n\nI'll go first: [your answer]"
```

---

## Integration with Other Skills

| Skill | Integration |
|-------|-------------|
| **content-calendar** | Pull scheduled posts into social queue; social metrics inform content strategy |
| **writing-assistant** | Draft posts using voice profile; edit for platform-specific constraints |
| **research-assistant** | Find trending topics, competitor analysis, hashtag research |
| **solopreneur-assistant** | Social media as a business growth channel; weekly review feeds into business dashboard |
| **habit-tracker** | Track daily posting consistency as a habit |
| **financial-tracker** | Attribute revenue to social-sourced leads |

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Posts sound generic | Update voice notes in social-state.md with specific examples of your style |
| Same pillar every week | Check pillar distribution table; explicitly request underrepresented pillars |
| No engagement data | Manually log metrics for 2 weeks to build baseline |
| Queue always empty | Set up weekly batch session (every Sunday, draft next week's posts) |
| Platform voice mismatch | Add per-platform voice notes (casual on Twitter, professional on LinkedIn) |

---

## Privacy & Safety

- **Never auto-post.** All content is drafted for your review.
- **No API credentials stored in state files.** Posting happens manually or through your own connected tools.
- **Engagement data stays local.** Your analytics are in your workspace only.
- **No competitor data scraping.** Research uses public web search only.

---

*Part of the [Agent Skills Collection](https://github.com/theagentledger/agent-skills) by The Agent Ledger.*
*Subscribe at [theagentledger.com](https://theagentledger.com) for the premium guide and new skills.*
