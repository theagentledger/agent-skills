---
name: email-sequence-manager
description: Build, test, and automate multi-step email campaigns with conversion tracking. Templates for onboarding, nurture, product launch, re-engagement. Integrate with CRM, financial-tracker, and analytics.
version: 1.0.0
author: The Agent Ledger
license: CC-BY-NC-4.0
tags: ["email", "marketing", "automation", "funnel", "conversion"]
platforms: ["OpenClaw", "Cursor", "Windsurf", "Generic"]
category: "Sales & Marketing"
---

# Email Sequence Manager

**Master email automation as your AI Chief of Staff.** Design high-converting sequences, test performance, track revenue impact, and integrate with your entire business system.

## Overview

Most solopreneurs send emails without a system. This skill gives you:

- **5 core sequence templates** (Onboarding, Nurture, Product Launch, Re-engagement, Upsell) with proven structures
- **Sequence state file** tracking all active campaigns, performance metrics, and A/B tests
- **Per-email tracking:** open rates, click rates, conversions, revenue tied to each message
- **Integration hooks** into CRM, financial-tracker, goal-tracker, and solopreneur-assistant
- **Automation-ready structure** for scheduling, segment logic, and trigger events

## Getting Started

### Step 1: Create Your Email Sequence State File

Create `email-sequences/email-state.md` in your workspace:

```markdown
# Email Sequence Manager — Active Campaigns

## Sequence Inventory

| Name | Type | Status | Subscribers | Sent | Open Rate | Click Rate | Conv Rate | Revenue | Started | Notes |
|------|------|--------|-------------|------|-----------|-----------|-----------|---------|---------|-------|
| Welcome Onboarding | Onboarding | Active | 245 | 980 | 48% | 12% | 8% | $1,240 | 2026-01-15 | 5-email sequence |
| Post-Purchase | Onboarding | Active | 89 | 356 | 52% | 15% | 12% | $680 | 2026-02-20 | Product delivery + upsell |
| Weekly Nurture | Nurture | Active | 156 | 624 | 38% | 8% | 3% | $180 | 2026-02-01 | Thought leadership |
| Summer Course Promo | Product Launch | Scheduled | 0 | 0 | — | — | — | $0 | 2026-03-20 | Pre-launch 3 weeks before go-live |
| Abandoned Cart | Re-engagement | Active | 0 | 0 | — | — | — | $0 | 2026-01-10 | Nightly trigger for 24h cart abandonment |

## Performance Benchmarks (Your Baseline)

- **Onboarding open rate target:** 45-60% (higher engagement = new relationship building)
- **Nurture click rate target:** 5-12% (thought leadership should drive engagement)
- **Product launch conversion target:** 5-15% (depends on price point and positioning)
- **Re-engagement open rate floor:** 20% (if below, sequence needs refresh)

## A/B Tests In Flight

| Sequence | Test | Variant A | Variant B | Started | Status | Winner |
|----------|------|-----------|-----------|---------|--------|--------|
| Welcome Onboarding | Subject line | "Welcome to [Product]" | "Here's Your First Step" | 2026-02-15 | Active (50% split) | TBD |
| Post-Purchase | CTA button | "Unlock Your Course" | "Get Started Now" | 2026-02-20 | Active (50% split) | TBD |

## Monthly Performance Summary

### February 2026

- **Total emails sent:** 1,960
- **Total opens:** 887 (45.2% avg)
- **Total clicks:** 204 (10.4% avg)
- **Total conversions:** 132 (6.7% avg)
- **Revenue generated:** $2,100
- **Cost per click:** $0 (organic)
- **Revenue per email sent:** $1.07
- **Best performer:** Post-Purchase sequence (52% open rate, 15% click rate)
- **Needs work:** Weekly Nurture (38% open, low engagement)

---

## Sequence Templates (Copy & Customize)

### Template: Onboarding Sequence (5 Emails)

**Goal:** Help new customer/subscriber succeed in first 14 days. Drive product adoption and early engagement.

**Timing:** Day 0 (immediate), Day 1, Day 3, Day 7, Day 14

**Email 1 (Day 0 — Hour 0):** Welcome + Quick Win
```
Subject: "Welcome to [Product] — Your First Step Inside"

Body:
- Genuine welcome (1 para)
- Immediate value: "Here's the ONE thing to do in the next 2 hours" (1 actionable task)
- CTA button: "Get Started Now"
- Footer: "This is email 1 of 5 in your onboarding series"
```

**Email 2 (Day 1):** Core Concept
```
Subject: "The [One Concept] You Need to Know"

Body:
- Build on Email 1 (what they did = good)
- Explain the core framework/concept (2 para max)
- Real example: "Here's how [name] used this..."
- CTA: "Try It Yourself Here"
```

**Email 3 (Day 3):** Overcome First Obstacle
```
Subject: "Stuck? Here's the Fix"

Body:
- Address the common first mistake
- Troubleshooting guide (3-5 bullet points)
- Case study: "When [customer] hit this, here's what worked..."
- CTA: "See the Detailed Guide"
```

**Email 4 (Day 7):** Social Proof + Momentum
```
Subject: "[Customer Name] Did This in 7 Days"

Body:
- One customer win story (3 para narrative)
- Specific metric: "Result: [specific number]"
- "You can do this too" re-engagement
- CTA: "See More Success Stories"
```

**Email 5 (Day 14):** Next Level + Graduation
```
Subject: "You've Mastered the Basics — Here's What's Next"

Body:
- Celebrate progress
- Introduce advanced feature/next module
- Positioning: "Only 20% of users get here"
- CTA: "Unlock Advanced Content" (or upsell link)
- Transition message: "You're now on our weekly newsletter"
```

### Template: Nurture Sequence (Ongoing Weekly)

**Goal:** Build relationship, establish authority, keep top-of-mind, drive occasional conversions.

**Frequency:** 1 email per week, same day/time

**Email Structure:**
```
Subject: "[Value Proposition] — [Curiosity Hook]"
Example: "The One Metric That Predicts Revenue — [Industry] Ignored It"

Body:
- Hook: Why this matters (1 sentence)
- Core idea: 300-400 words
- Real example or case study
- Reflection question: "What's YOUR [relevant metric]?"
- CTA: Soft (link to blog/resource, not hard sell)
- P.S.: Teaser for next week's topic

Signature:
[First Name]
[Title]
P.P.S. Reply with YOUR biggest [challenge]. I read every email.
```

### Template: Product Launch Sequence (7 Days Pre → 7 Days Post)

**Day -7 (Week Before):** Teaser
```
Subject: "Something Big Is Coming Next Week"
- Curiosity (no details yet)
- Pre-launch waitlist signup (if not already)
```

**Day -4:** Problem Deep-Dive
```
Subject: "The [Problem] Keeping You From [Outcome]"
- Establish the pain
- Frame the solution (your new product)
```

**Day -1 (Day Before Launch):** Countdown + Preview
```
Subject: "Tomorrow: [Product Name] Launches"
- Preview of main features
- Early bird pricing (if applicable)
- CTA: "Get Early Access"
```

**Day 0 (Launch Day):** Go Live
```
Subject: "[Product Name] Is Now Live"
- Announce publicly
- Share the 2-3 main benefits
- CTA: "Get It Now"
```

**Day 1:** Success Stories
```
Subject: "The First [Number] People Who Got [Product]"
- Early wins from beta users
- Testimonials
```

**Day 3:** Answer Objections
```
Subject: "Is [Product] Right for You?"
- FAQ addressing common hesitations
- Pricing clarification
```

**Day 7:** Last Chance (Scarcity)
```
Subject: "[Optional] Special Pricing Ends Tonight"
- Create urgency (if applicable)
- Final CTA
```

### Template: Re-engagement Sequence (Post-Abandonment)

**Trigger:** 24 hours after event (cart abandonment, demo signup not converted, white paper download but no follow-up)

**Email 1 (Hour 24):** Gentle Reminder
```
Subject: "Did You Forget? [Product/Offer] Is Still Waiting"
- No guilt ("Inboxes are crazy, we get it")
- Remind what they abandoned
- Easy CTA to resume
```

**Email 2 (Day 3):** Remove Obstacles
```
Subject: "Questions? Let's Clear Them Up"
- FAQ specific to their abandoned action
- Live chat link or reply-to-email
- Alternative CTA (book call, request discount)
```

**Email 3 (Day 7):** Last Chance + Move On
```
Subject: "Last Chance: [Offer] Expires Tomorrow"
- Final attempt with urgency (if applicable)
- Alternative offer (lower friction version)
- Soft unsubscribe if not interested
```

### Template: Upsell Sequence (Triggered After Purchase)

**Trigger:** Day 7 post-purchase (after they've had time to get value)

**Email 1:** Celebrate Success
```
Subject: "Here's What Our Best Customers Did Next"
- Celebrate their purchase
- Early wins story
- "The next logical step is..." (intro to upsell)
```

**Email 2:** Deep Dive Feature
```
Subject: "Most People Miss This [Premium Feature]"
- Explain the upgraded tier/product
- Specific ROI calculation
```

**Email 3:** Social Proof
```
Subject: "[Customer Name] Upgraded — Here's Why"
- Case study of upsell beneficiary
- Specific results metric
- CTA: "Upgrade Now"
```

---

## 10 Usage Patterns

### Pattern 1: Launch a New Sequence

**When:** You have a new audience segment or business goal.

**Steps:**
1. Choose a template above
2. Customize subject lines, copy, CTAs for your product/audience
3. Create sequence file: `email-sequences/[sequence-name].md`
4. List in email-state.md Inventory table
5. Schedule send times (stick to same day/time for consistency)
6. Set A/B test if testing two subject lines or CTAs

**Sequence File Format:**
```markdown
# [Sequence Name] Sequence

**Type:** [Onboarding / Nurture / Product Launch / Re-engagement / Upsell]
**Status:** [Active / Scheduled / Paused / Archived]
**Created:** 2026-03-14
**Target Audience:** [Who gets this]
**Goal:** [What you want to happen]

## Email 1: [Subject Line]
- Content here
- CTA: [Link or action]

## Email 2: [Subject Line]
- Content here

... (etc)
```

### Pattern 2: Track Performance & Conversions

**Daily/Weekly:** Segment by sequence, track these metrics:

```markdown
## [Sequence Name] — Weekly Report

| Metric | Week Ending | Value | Target | Status |
|--------|-------------|-------|--------|--------|
| Emails Sent | 2026-03-14 | 245 | — | ✅ |
| Unique Opens | 2026-03-14 | 118 | 120+ | ⚠️ |
| Click Rate | 2026-03-14 | 8% | 10%+ | ⚠️ |
| Conversions | 2026-03-14 | 6 | 8+ | ⚠️ |
| Revenue | 2026-03-14 | $480 | $600+ | ⚠️ |
| Unsubscribes | 2026-03-14 | 1 | <3 | ✅ |
| Complaints | 2026-03-14 | 0 | 0 | ✅ |
```

**Actions:**
- Below target? → Check subject line, CTA clarity, timing
- Rising unsubscribes? → Frequency too high or content mismatch
- No opens? → Subject line is the lever

### Pattern 3: A/B Test Subject Lines

**Setup:**
```markdown
## A/B Test: [Sequence Name] Subject Line

**Hypothesis:** Curiosity hook subject lines get 10%+ higher open rates than direct benefit

**Variant A:** "The [Benefit] You're Missing"
**Variant B:** "New [Feature] — Available Today"

**Split:** 50/50 random assignment
**Sample Size Goal:** 500 sends each (need 1,000 total)
**Test Duration:** 2 weeks
**Metric:** Open rate

**Results:**
- Variant A: 42% open rate (210 opens / 500)
- Variant B: 38% open rate (190 opens / 500)
- **Winner:** Variant A (4 point lift)
```

### Pattern 4: Segment Email Lists

**If using external tool (Mailchimp, ConvertKit, etc.):**

Create segments based on:
- **Onboarding stage** ("New" = sent day 0-3, "Active" = day 7+)
- **Engagement level** ("Engaged" = opened in last 7 days, "Inactive" = no opens in 30 days)
- **Product purchased** (who bought what, triggers upsell)
- **Behavior** (clicked certain link, downloaded resource, visited pricing page)

**In email-state.md:**
```markdown
## List Segments

| Segment | Size | Last Sent | Open Rate | Notes |
|---------|------|-----------|-----------|-------|
| New Subscribers | 42 | 2026-03-14 | 65% | Onboarding sequence |
| Active Nurture | 128 | 2026-03-12 | 42% | Weekly sends |
| Product A Buyers | 76 | 2026-03-10 | 38% | Upsell to B |
| Inactive (30+ days) | 89 | 2025-12-01 | — | Re-engagement candidate |
```

### Pattern 5: Automate Triggers

**Email platform integrations** (Zapier, Make, direct API):

```markdown
## Automation Triggers

| Trigger | Action | Platform | Status |
|---------|--------|----------|--------|
| New CRM contact added | Send Welcome Onboarding Email 1 | [Platform] | Active |
| Product purchased | Send Post-Purchase Email 1 after 24h | [Platform] | Active |
| Demo scheduled | Send Pre-Demo Prep Email | [Platform] | Active |
| 24h cart abandonment | Send Abandoned Cart Email 1 | [Platform] | Active |
| Newsletter signup (not customer) | Send Nurture Sequence (weekly) | [Platform] | Active |
```

### Pattern 6: Revenue Tracking

**Integration with financial-tracker.**

**Per sequence, track:**
```markdown
## [Sequence Name] — Revenue Impact

| Metric | Jan | Feb | Mar | Q1 Total | YTD |
|--------|-----|-----|-----|----------|-----|
| Emails Sent | 980 | 1,240 | 1,560 | 3,780 | 3,780 |
| Total Conversions | 52 | 82 | 98 | 232 | 232 |
| Total Revenue | $2,080 | $3,280 | $3,920 | $9,280 | $9,280 |
| Conversion Rate | 5.3% | 6.6% | 6.3% | 6.1% | 6.1% |
| Revenue per Send | $2.12 | $2.64 | $2.51 | $2.45 | $2.45 |
| Revenue per Click | $10.20 | $16.10 | $14.30 | $13.40 | $13.40 |
```

**Quarterly review:** Which sequence is your revenue engine? Over-invest there.

### Pattern 7: Monthly Email Audit

**First Monday of month, run this check:**

```markdown
## March 2026 Email Audit

### Health Check
- [ ] All active sequences sent on schedule (0 missed sends)
- [ ] Unsubscribe rate <0.5% (2/400 = 0.5%)
- [ ] Spam complaints 0 (0/400)
- [ ] No broken links in last month's sends
- [ ] All CTAs pointing to correct URLs

### Performance vs Target
- [ ] Welcome Onboarding: 48% open (target 45%) ✅
- [ ] Weekly Nurture: 38% open (target 38%) ✅
- [ ] Product Launch: 52% click (target 50%) ✅
- [ ] Overall revenue: $2,100 (target $2,000) ✅

### What Worked This Month
1. "Here's What Our Best Customers Did" subject line (58% open)
2. Video CTA button over text link (18% click)
3. Case study email format (8% conversion)

### What Needs Work
1. Weekly Nurture open declining (42% → 38%) — test new subject lines
2. Re-engagement sequence ROI negative (send cost > revenue) — pause until redesign
3. Post-Purchase upsell converting at 3% (target 8%) — need stronger positioning

### Next Month's Focus
1. Fix 2 underperforming sequences (Nurture + Re-engagement)
2. Launch Product Launch sequence for [New Product]
3. Test send time optimization (current time: Tue 10am, test Thu 2pm)
```

### Pattern 8: Build a Sequence Library

**Reusable templates by business type:**

```markdown
## Email Sequence Library

### Onboarding Sequences (5 emails, 14 days)
- **Product Onboarding** — Generic product template
- **Course Onboarding** — For digital course/membership
- **Service Onboarding** — For SaaS or service business
- **Community Onboarding** — For community/membership

### Nurture Sequences (Weekly ongoing)
- **Educational Nurture** — Thought leadership focus
- **Social Proof Nurture** — Heavy case studies
- **Problem-Agitation Nurture** — Pain point focus

### Launch Sequences (7 days pre, 7 days post)
- **Product Launch** — Generic
- **Course Launch** — Urgency + cohort feel
- **Offer Launch** — Limited-time positioning

### Re-engagement Sequences (3 emails, 7 days)
- **Cart Abandonment** — E-commerce specific
- **Nurture Re-engagement** — Win back inactive
- **Demo No-Show** — SaaS specific
```

### Pattern 9: Calculate Email ROI & Cost

**Quarterly review:**

```markdown
## Email Program ROI — Q1 2026

### Costs
- Email platform fee: $99/mo × 3 = $297
- Design/copywriting (your time): 40 hrs × $100/hr = $4,000
- **Total Q1 Cost:** $4,297

### Revenue
- Onboarding sequences: $3,500
- Nurture sequences: $1,200
- Product launch: $2,100
- Upsell sequences: $1,800
- **Total Q1 Revenue:** $8,600

### ROI
- Net profit: $8,600 - $4,297 = $4,303
- ROI %: ($4,303 / $4,297) × 100 = **100%**
- Payback period: 2 weeks

### Benchmarks
- Cost per email sent: $0.001 (nearly free)
- Revenue per email: $2.28
- Conversion rate: 6.1% (industry avg ~2%)
```

### Pattern 10: Segment by Lifecycle & Automate

**Advanced:** Use segments + automation to send right message at right time

```markdown
## Lifecycle Automation Map

**Stage: New (Day 0-14)**
- Sequence: Onboarding (5 emails)
- Goal: Product adoption + quick win
- Success metric: 60%+ open, 15%+ click

**Stage: Active (Day 15+, opened last 7 days)**
- Sequence: Weekly Nurture
- Goal: Engagement + relationship
- Success metric: 40%+ open, 8%+ click

**Stage: Customer (Purchased)**
- Sequence: Post-Purchase (3 emails)
- Then: Upsell sequence (triggered 7 days post-purchase)
- Goal: Adoption + upgrade
- Success metric: 50%+ open, 10%+ click, 8%+ conversion to upsell

**Stage: Inactive (No open in 30 days)**
- Sequence: Re-engagement (3 emails)
- Goal: Rekindle interest or clean list
- Success metric: 25%+ open or unsubscribe

**Stage: Inactive After Re-engagement (No action in 30 days)**
- Action: Remove from mailing list
- Document: "Inactive—unsubscribed for list hygiene"
```

---

## Heartbeat Integration

Add to your `HEARTBEAT.md`:

```markdown
## Email Sequences Check

**Every Friday afternoon (15 min):**
1. Check weekly performance: emails sent, open rate, click rate vs. target
2. Any sequences underperforming? Flag for Monday action
3. Any A/B tests ready to call a winner? Move winner to production
4. Any unsubscribe spikes? Investigate (frequency, content, targeting)
5. Any customer complaints/feedback from replies? Document in email-state.md

**First Monday of month (30 min):**
1. Full monthly audit (checklist in Pattern 7 above)
2. Calculate month-over-month revenue
3. Identify 1 sequence to improve next month
```

---

## Cron Setup (Optional)

Schedule a weekly email performance report to Telegram:

```bash
openclaw cron add \
  --name "Email Sequences Weekly Report" \
  --every 168h \
  --model "anthropic/claude-sonnet-4-6" \
  --session isolated \
  --message "Generate this week's email sequence performance report. Read email-state.md (weekly metrics), calculate open rates, click rates, conversions, revenue for each active sequence. Highlight any underperforming sequences (below target). Recommend actions for next week. Format as concise bullet list." \
  --announce \
  --to "-1003853954380" \
  --tz "America/Chicago"
```

---

## Integration Map

| Skill | How Email Sequences Integrates |
|-------|------------------------------|
| **CRM** | Email sequences trigger from CRM stage changes (new contact → send Welcome) |
| **Financial Tracker** | Track email revenue in monthly P&L; calculate ROI |
| **Solopreneur Assistant** | Weekly review includes email metrics; funnel health = business health |
| **Goal Tracker** | Email revenue targets = quarterly goal; conversion rate = KR |
| **Newsletter Manager** | Your newsletter IS a nurture sequence; track open/click/revenue same way |
| **Social Media Manager** | Email list = owned audience; nurture sequence keeps them warm between posts |
| **Writing Assistant** | Use for drafting email copy; version control in sequence files |
| **Content Calendar** | Email content = part of content calendar; sequence topics tie to content themes |
| **Idea Vault** | Email ideas/tests = ideas to score and track |
| **Decision Log** | Document why you chose sequence structure, timing, segment strategy |

---

## Customization Guide

### Different List Sizes

**Under 100 subscribers:**
- Start with 1 nurture sequence (weekly)
- Add onboarding when you get 1-2 signups/week
- A/B testing: wait until you have 500+ list size

**100-1,000 subscribers:**
- Onboarding (required)
- Weekly Nurture (required)
- Product Launch sequences (as needed)
- Start A/B testing (you have enough volume)

**1,000+ subscribers:**
- Full automation: triggers for onboarding, upsell, re-engagement
- Aggressive A/B testing (subject line, CTA, send time)
- Segment by engagement level + purchase history
- Revenue tracking per segment

### Platform-Specific Notes

**Email platforms (Mailchimp, ConvertKit, Substack, Klaviyo, etc.):**
- Most have native sequence/automation builders
- Export your templates from SKILL.md, rebuild in their UI
- Use their reporting dashboard for metrics
- Link financial data manually to email-state.md

**Self-hosted email (your own SMTP server):**
- Use a self-hosted tool (Mautic, OpenEMM, PostMark)
- Sequences require manual send scheduling or cron jobs
- Tracking requires integration with your CMS/database
- More control, higher setup burden

**No email list yet:**
- Start by building! Add email signup widget to your website/product
- First goal: 100 subscribers (takes 1-3 months if you already have traffic)
- Then launch onboarding sequence
- Then nurture (weekly) once you have 20+ active people

---

## Common Failure Modes

### ❌ Failure: Spammy Subject Lines

**What happens:** High open rate feels good, but clicks + conversions tank. People unsubscribe.

**Root cause:** You're using clickbait. People feel tricked.

**Fix:** Subject line = honest preview of email. If subject is "You won't believe what happened," email better deliver a surprise.

**Test:** Read subject line aloud. Would YOU click it? Does email deliver on the promise?

---

### ❌ Failure: Send Time All Wrong

**What happens:** Great subject, great copy, low open rate.

**Root cause:** Sending when your audience isn't checking email. Test it.

**Fix:** Review open times in your email platform analytics. When do people open? Send 1-2 hours before peak time.

**Common times by audience:**
- B2B professionals: Tue-Thu, 9am-10am (before meetings start)
- Creators/Solopreneurs: Wed-Fri, 10am-11am (after morning work block)
- E-commerce: Sun-Mon, 6pm (evening shopping habit)

---

### ❌ Failure: Sequence Too Long

**What happens:** Onboarding is 10 emails instead of 5. People drop off by email 3.

**Root cause:** You're trying to teach everything at once.

**Fix:** Each email = ONE idea. Can you say it in 1 paragraph? Good. Done. Move to next email.

**Rule:** If your sequence is >7 emails, cut it. Longer ≠ better.

---

### ❌ Failure: No CTA / Unclear CTA

**What happens:** Great email, 0 conversions. People read it and... then what?

**Root cause:** You didn't tell them what to do next.

**Fix:** Every email needs 1-2 CTAs max. Make them obvious. Button is better than link.

Example good CTAs:
- "Try It Free for 14 Days"
- "Book Your Demo"
- "See the Case Study"
- "Download the Template"

---

### ❌ Failure: Same Email to Everyone

**What happens:** Welcome sequence sent to both new prospects AND existing customers. Dissonance.

**Root cause:** No segmentation.

**Fix:** Send different sequence based on segment:
- New subscriber → Onboarding
- Customer → Post-Purchase (not onboarding)
- Inactive → Re-engagement (not nurture)

---

### ❌ Failure: No A/B Testing

**What happens:** You send the same subject line forever. Performance plateaus.

**Root cause:** You're guessing instead of testing.

**Fix:** Once per month, test one element (subject line, CTA text, send time). Document winner. Use winner next month.

---

### ❌ Failure: Tracking Gets Loose

**What happens:** You send lots of emails, but don't know which made money.

**Root cause:** No revenue attribution.

**Fix:** Add a column to each sequence's metrics table: "Revenue This Week." Tie it to a specific campaign/product/offer.

---

## Privacy & Compliance Note

- **GDPR/CASL/CAN-SPAM:** You MUST have explicit consent before sending marketing emails. Use email-state.md to document how consent was obtained.
- **Unsubscribe:** Always include easy unsubscribe link (legal requirement + good practice)
- **List hygiene:** Don't email inactive people forever. After 30 days no open, consider removing them (or send re-engagement, then remove)
- **Personal data:** Never put customer data in sequences (real names, purchase amounts, etc.). Use placeholders like {{first_name}}, {{product}}.

---

## What's Next?

- [ ] Pick your first sequence to automate (recommend: Onboarding)
- [ ] Draft all 5 emails
- [ ] Send to 10-20 people manually (test copy, links, timing)
- [ ] Document performance in email-state.md
- [ ] Move to email platform automation once validated

---

_Built by The Agent Ledger · Learn more at theagentledger.com_

**License:** CC-BY-NC-4.0 — Use, share, and modify freely for non-commercial purposes. Credit The Agent Ledger.

