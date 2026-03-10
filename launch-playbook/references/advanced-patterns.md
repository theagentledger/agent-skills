# Launch Playbook — Advanced Patterns
**by [The Agent Ledger](https://theagentledger.com)**

---

## Pattern 1: The Pre-Mortem
**What:** Before launch day, imagine it failed. Work backwards to prevent it.
**When to use:** 1 week before any significant launch.

Prompt your agent:
```
Run a pre-mortem on the [launch name] launch.
Imagine it's 2 weeks after launch day and the results were disappointing.
List the 5 most likely reasons it failed. For each, what can we do NOW to prevent it?
```
Document output in the launch record under a `## Pre-Mortem` section.

**Why it works:** Surfacing failure modes before launch is far cheaper than diagnosing after. Most launch failures are predictable.

---

## Pattern 2: The Audience Warmup Tracker
**What:** Track pre-launch audience engagement signals to predict launch success.
**When to use:** 2-4 weeks before launch for any product or newsletter launch.

Add to your launch record:
```markdown
## Audience Warmup Signals
| Week | Email open rate | Social engagement | Waitlist size | DM/replies | Warmth Score (1-5) |
|------|-----------------|-------------------|---------------|------------|---------------------|
| W-4 | | | | | |
| W-3 | | | | | |
| W-2 | | | | | |
| W-1 | | | | | |
```

A "cold" audience (low opens, no replies, no waitlist) in the week before launch is a signal to delay or add a warmup sequence — not push forward.

---

## Pattern 3: Multi-Launch Sequencing
**What:** Plan dependent launches in a deliberate sequence to maximize leverage.
**When to use:** When you have 2+ launches within 90 days.

Rules of thumb:
- **No two major launches within 21 days.** Audience and personal bandwidth both need recovery time.
- **Sequence complementary launches.** Free lead magnet → email list growth → paid product launch captures the flywheel.
- **Never run concurrent launches.** Pick one primary launch per period; others are maintenance.

Map launches in `launches/launch-state.md`:
```markdown
## Launch Sequence Map
Q1 2026:
- Jan 15: Free lead magnet (build list)
- Feb 28: Newsletter growth push (build audience)
- Mar 20: Paid product launch (monetize)
```

---

## Pattern 4: Email Sequence Blueprint
**What:** A reusable 5-email launch sequence structure that works for most product launches.
**When to use:** Any paid product launch with an email list.

```markdown
## Standard 5-Email Launch Sequence

Email 1 (10 days before): THE STORY
- Hook: A problem your audience knows too well
- Your journey through that problem
- Tease: "I built something that changed this for me"
- CTA: "Stay tuned" (no sell yet)

Email 2 (7 days before): THE SOLUTION PREVIEW
- Announce what you're launching (high level)
- 3 specific results it creates
- Early-access / waitlist CTA (if using)
- Reply engagement CTA: "What's your biggest struggle with [topic]?"

Email 3 (Launch Day): THE OPEN
- Subject: [Product] is live
- Full offer details: what, price, for whom
- Urgency or scarcity (honest only — if you have a deadline, use it)
- Clear CTA + link

Email 4 (2 days after): THE OBJECTION HANDLER
- Address the top 2-3 hesitations (price, time, "is this for me?")
- Social proof or results story (if available)
- Restate CTA

Email 5 (Last chance): THE CLOSE
- Subject: Closing [tonight / Friday / this week]
- Recap the offer in 3 bullets
- What happens after it closes
- Final CTA

After: ONBOARDING EMAIL
- Delivery + access instructions
- What to do first
- Where to get help
- Set expectations for what comes next
```

Store this template in `launches/templates/5-email-sequence.md` and adapt per launch.

---

## Pattern 5: Pricing Validation Before Launch
**What:** Test pricing sensitivity before committing to a price.
**When to use:** Any launch where you're unsure about pricing.

Simple approaches (before building):
1. **Mention the approximate price to 5 warm contacts** and note their reaction. "Sounds reasonable" = green light. Silence or hesitation = revisit.
2. **Run a quick survey** (Typeform, Twitter/X poll): "If I built X, what would you pay?" Offer ranges, not open-ended.
3. **Look at 3 comparable products** in your market. Your price should anchor to the value delivered, not just competitor prices — but knowing the market range prevents obvious mispricings.

Document in your launch record:
```markdown
## Pricing Validation
Price point: $[X]
Comparable products: [list 3 with prices]
Validation method: [survey / conversations / research]
Feedback: [what you heard]
Decision: [final price and rationale]
```

---

## Pattern 6: Launch Debrief Chain (Multi-Skill Integration)
**What:** A comprehensive post-launch review that chains 4 skills together.
**When to use:** Within 7 days of completing any significant launch.

Full debrief chain:
```
Step 1 — Financial review (financial-tracker):
"Summarize revenue from [launch name] launched on [date].
Log final revenue and compare to target."

Step 2 — Goal progress (goal-tracker):
"The [launch name] achieved [result]. Update the relevant Q[X] KR progress."

Step 3 — Content performance (content-calendar / social-media-manager):
"Review the content we published for [launch name].
What was the best-performing piece? What would I cut next time?"

Step 4 — Decision retrospective (decision-log):
"Log a decision review for [launch name]:
Key decisions made, what worked, what I'd change."
```

Then close with the launch-playbook retrospective to tie it all together.

---

## Pattern 7: The Minimum Viable Launch (MVL)
**What:** A stripped-down launch protocol for testing ideas with minimal prep.
**When to use:** Launching an unproven idea, testing a new audience, or under time pressure.

MVL principles:
- **Ship before perfect.** If your landing page isn't live, the launch isn't happening. Done beats polished.
- **One email, one post.** Don't need a 5-email sequence to test demand.
- **Short window.** 48-72 hour launch window forces urgency and fast data.
- **Manual first.** If you can't sell it manually (email, DM, phone), don't automate it yet.

MVL checklist:
```markdown
- [ ] Offer can be described in 2 sentences
- [ ] Buyer can pay (Stripe link, Gumroad page, invoice — doesn't matter)
- [ ] 1 announcement email written
- [ ] 1 social post written
- [ ] You have 10+ warm people to tell personally
- [ ] You know what "success" looks like for this test
```

If the MVL doesn't get traction, you've learned something in days, not weeks.

---

## Pattern 8: Launch Friction Audit
**What:** Identify and remove every step between "interested" and "bought/signed up."
**When to use:** 48 hours before any paid product launch.

Walk through your purchase flow as a stranger:
```
Ask your agent: Walk me through the complete purchase journey for [launch name].
From first hearing about it to completed purchase — what does the buyer experience?
Flag every step that requires effort, creates confusion, or could cause drop-off.
```

Common friction points:
- Too many clicks between CTA and checkout
- Price hidden until late in flow
- Payment processor not trusted or unfamiliar
- Mobile-unfriendly landing page
- Confusing CTA copy ("Learn more" vs "Get instant access")
- No clear "what happens next after I buy" messaging

Each friction point removed typically lifts conversion by 5-15%.

---

## Pattern 9: Quarterly Launch Retrospective
**What:** Review all launches in the quarter as a portfolio.
**When to use:** End of every quarter.

```
Review my launch library for Q[X] YYYY.
For each completed launch:
- Final results vs target
- Overall rating

Then answer:
1. Which launch performed best? Why?
2. Which launch underperformed? What was the root cause?
3. What's the single biggest change I should make to my launch process?
4. What type of launch should I prioritize next quarter based on this data?
```

Use the output to update your launch strategy for the next quarter and brief new launches with the accumulated learnings.

---

## Pattern 10: Launch → Newsletter Pipeline
**What:** Turn every launch into content that grows your audience.
**When to use:** After every completed launch (whether it succeeded or failed).

Content types you can extract from any launch:
1. **"Here's what I learned"** post — authentic, drives engagement
2. **"Behind the scenes"** breakdown — process, timeline, tools used
3. **Results case study** — if strong, use as social proof; if weak, use as honest story
4. **"What I'd do differently"** thread — high engagement, positions you as thoughtful
5. **Repurposed launch copy** — your best email subject lines → social hooks

Pair with writing-assistant:
```
I just completed the [launch name] launch. Results: [brief summary].
Draft a behind-the-scenes newsletter issue about what I learned.
Focus on [specific angle: what worked / what failed / process breakdown].
Keep my voice: [tone description].
```

A well-documented failure story often outperforms a success story in engagement. Don't waste either.

---

*Advanced Patterns — Launch Playbook Skill v1.0.0*
*by [The Agent Ledger](https://theagentledger.com) — CC-BY-NC-4.0*
