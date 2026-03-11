# Prompt Library — Advanced Patterns

*by [The Agent Ledger](https://theagentledger.com)*

Ten advanced patterns for prompt library power users.

---

## Pattern 1: Prompt Genealogy Tree

Track how prompts evolve from a shared ancestor.

When you version a prompt significantly, mark it as a fork rather than a simple update:

```markdown
### [PL-023] Deep Research Brief v3
**Forked from:** PL-004 (Research Brief v1)
**Fork reason:** Specialization for competitive analysis tasks
**Version History:**
- v1.0 → PL-004 (general research brief, score 7.2)
- v2.0 → PL-011 (added source quality rubric, score 8.1)
- v3.0 → PL-023 (specialized for competitive analysis, score 8.9)
```

This makes it easy to see which prompts descended from your best early work, and which branches are gaining vs losing effectiveness over time.

---

## Pattern 2: Prompt Stress Testing Protocol

Before promoting a prompt to Core (score 8+), run a deliberate stress test:

1. **Happy path:** Use it on the exact task it was designed for
2. **Adjacent task:** Use it on a similar but not identical task
3. **Edge case:** Use it on the most extreme version of the task
4. **Adversarial:** Use it on a task where you'd expect it to fail

Score each pass 1–10 and average. Only promote prompts that score 7+ on the adversarial test. Add stress test results to performance notes.

---

## Pattern 3: Prompt-to-Revenue Mapping

For revenue-generating workflows, track which prompts directly contribute to income:

```markdown
### [PL-031] Freelance Proposal Generator
**Revenue Impact:** ~$2,400 in accepted proposals (3 clients × avg $800)
**Conversion Rate:** 67% (4 of 6 proposals using this prompt were accepted)
**vs. non-library proposals:** 40% conversion (pre-library baseline)
```

Over time, this creates a "highest-ROI prompts" list. Use it to decide which prompts deserve the most iteration investment. Integrate with `financial-tracker` to cross-reference income events with prompt usage dates.

---

## Pattern 4: Prompt Bundle Sets

Group prompts that work together as a workflow:

```markdown
## Bundle: Newsletter Production Pipeline
1. PL-008 — Research brief (topic research → source list)
2. PL-019 — Outline generator (source list → structured outline)
3. PL-027 — Draft writer (outline → rough draft)
4. PL-034 — Editor check (rough draft → flagged issues)
5. PL-041 — Subject line generator (draft → 5 subject line options)

**Sequence:** Run in order. Each output feeds the next prompt.
**Time savings:** ~2hr manual work → ~25min with this bundle
**Notes:** Step 3 works best when Step 2 output includes word count target
```

Share bundles with other creators as a higher-level product. A "Newsletter Bundle" or "Client Onboarding Bundle" is a natural Gumroad or ClawHub offering.

---

## Pattern 5: Negative Prompt Log

Track prompts that failed and why. Most people only save what works — but documenting failures prevents repeating them:

```markdown
## Negative Prompt Log

### [FAIL-003] Over-engineered analysis prompt (2026-02-14)
**What it tried to do:** Deep market analysis in a single prompt
**Why it failed:** Too much asked in one pass — agent split focus, outputs were shallow
**Lesson:** Break complex analysis into 3–4 sequential prompts. Never ask for >2 deliverables per prompt.
**Replacement:** See PL-022 (market sizing) + PL-023 (competitive landscape) as a 2-prompt chain
```

After 10+ entries, run a meta-analysis: "What patterns appear in my failed prompts?" Common themes: too long, too vague, mixing instruction types, no output format specified.

---

## Pattern 6: Prompt Quality Decay Monitoring

Prompts age. Model updates, context drift, and your own evolving standards can make a once-great prompt mediocre. Set up a decay check:

Add to `HEARTBEAT.md`:
```markdown
## Prompt Decay Check (Monthly)
- Flag any Core prompts (score 8+) that haven't been used in 45+ days
- Flag any prompts last scored 90+ days ago
- Prompt me to re-test and re-score flagged prompts
```

When a Core prompt drops below 7 on re-test, it gets demoted and queued for revision. This keeps the library honest — it's not a trophy case, it's a living tool.

---

## Pattern 7: Cross-Agent Prompt Sharing

If you run multiple specialized agents (e.g., a trading agent, an e-commerce agent, a writing agent), maintain a shared master prompt library in a location all agents can read:

```
workspace/
└── shared/
    └── prompt-library.md    # Accessible by all agents

workspace-trading/
└── prompt-library.md        # Trading-specific prompts

workspace-ecom/
└── prompt-library.md        # E-commerce-specific prompts
```

Add to each agent's AGENTS.md:
```markdown
## Prompt Library
- Check workspace/prompt-library.md for general-purpose prompts
- Check this workspace's prompt-library.md for domain-specific prompts
- When a domain prompt proves generally useful, promote it to the shared library
```

---

## Pattern 8: Prompt Compilation (Quarterly)

Every quarter, generate a "best of" compilation:

> "Generate a quarterly prompt compilation: top 10 prompts by score, top 5 by usage frequency, 3 most improved (biggest score increase from v1 to current), and 3 that should be retired. Format as a clean report."

This serves multiple purposes:
- Newsletter content ("My top 10 AI prompts this quarter")
- Personal review of what's working
- Input for the next quarter's iteration priorities
- Material for a paid prompt bundle

---

## Pattern 9: Prompt Template Variables — Best Practices

Well-designed variables make prompts dramatically more reusable. Advanced variable patterns:

**Enumerated options:**
```
{{TONE: professional | conversational | direct | storytelling}}
```

**Nested context blocks:**
```
{{CONTEXT_BLOCK}}
[Paste relevant background here — can be 1 sentence or 5 paragraphs]
{{/CONTEXT_BLOCK}}
```

**Optional sections:**
```
{{?EXAMPLES}}
Examples (omit this section if no examples available):
[Examples here]
{{/?EXAMPLES}}
```

**Format flags:**
```
{{OUTPUT_FORMAT: bullet-list | numbered-list | prose | table | JSON}}
```

Document your variable conventions in the library's README so you use them consistently across all prompts.

---

## Pattern 10: Prompt Library as Newsletter Content

Your prompt library is product. Use it:

**"Prompt of the Week"** — Share one high-scoring prompt per newsletter issue with context on when and how to use it. This is low-effort, high-value content that readers can immediately apply.

**"My Prompt Evolution"** — Walk readers through a prompt's version history. Show v1.0 vs v3.0 and explain what changed and why. Authentic, educational, differentiating.

**"Prompt Bundles"** as lead magnets — Export a themed bundle (newsletter writing, client proposals, market research) as a free PDF/markdown download. Requires email sign-up.

**"Annual Prompt Audit"** — Your end-of-year retrospective on your most and least effective prompts. High shareability, positions you as someone who takes AI craft seriously.

Integration with `newsletter-manager`:
```
When drafting newsletter issues, check prompt-library.md for prompts
tagged "newsletter-content" — these are pre-approved to share publicly.
Never share prompts tagged "internal" or "private" without Taylor's review.
```

---

*The Agent Ledger — practical AI systems for solopreneurs and creators.*
*[theagentledger.com](https://theagentledger.com)*
