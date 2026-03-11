---
name: prompt-library
version: 1.0.0
description: >
  Manage a personal prompt library: capture, categorize, version, rate, and reuse
  high-performing prompts across all your AI workflows. Includes prompt templates
  with variable substitution, quality scoring, A/B testing log, and integrations
  with other Agent Ledger skills. Trigger on: "save this prompt", "prompt library",
  "find a prompt for", "my best prompts", "prompt review", "add to prompt library",
  "update prompt", "version prompt", "prompt score", "prompt template", "what prompts
  do I have for", "build a prompt for", "test this prompt".
tags: [prompts, ai-workflows, productivity, templates, knowledge-management]
platforms: [openclaw, cursor, windsurf, generic]
category: ai-productivity
author: The Agent Ledger (theagentledger.com)
license: CC-BY-NC-4.0
---

# Prompt Library

*by [The Agent Ledger](https://theagentledger.com) — practical AI systems for solopreneurs*

> "Your best prompts are assets. Treat them like code."

Most people write a great prompt, use it once, and never find it again. This skill gives your agent a structured system for capturing, versioning, and retrieving your highest-leverage prompts — so every good prompt compounds instead of disappearing.

---

## What This Skill Does

- Captures prompts with context, variables, and performance notes
- Organizes prompts by category, use case, and quality score
- Versions prompts so you can track what changed and why
- Surfaces the right prompt when you need it
- Tracks which prompts perform and which need work

---

## Setup

### Step 1: Create Your Prompt Library File

Create `prompt-library.md` in your workspace root (or project folder):

```markdown
# Prompt Library

## Stats
- Total prompts: 0
- Last reviewed: —
- Top category: —

## Index

| ID | Name | Category | Score | Last Used | Tags |
|----|------|----------|-------|-----------|------|
| — | — | — | — | — | — |
```

### Step 2: Choose Your Category Set

Default categories (customize freely):

| Category | What It Covers |
|----------|----------------|
| `research` | Web search, deep dives, competitive analysis, summarization |
| `writing` | Drafts, edits, rewrites, tone adjustments, newsletter content |
| `analysis` | Data interpretation, pattern finding, decision support |
| `planning` | Project plans, roadmaps, goal setting, scheduling |
| `coding` | Code generation, debugging, review, documentation |
| `brainstorm` | Idea generation, creative exploration, alternatives |
| `review` | Editing, critique, quality checks, feedback |
| `ops` | Summarizing meetings, logging context, filing updates |
| `meta` | Prompts about prompts — testing, iteration, calibration |

### Step 3: Add AGENTS.md Standing Instruction (Optional)

Add to your `AGENTS.md`:

```markdown
## Prompt Library

When I say "save this prompt" or "add to prompt library", immediately
capture the current prompt with full context into `prompt-library.md`.
When I ask for a prompt for a task, search the library before generating
a new one — and suggest updating or versioning it after we test it.
```

### Step 4: Initial Capture Session

In your first session, run:

> "Review this conversation and extract any prompts or prompt patterns worth saving. Add them to the prompt library with initial scores and categories."

---

## Prompt Record Format

Each saved prompt follows this structure:

```markdown
### [PL-###] Prompt Name
**Category:** research | writing | analysis | planning | coding | brainstorm | review | ops | meta
**Score:** 1–10 (see scoring rubric below)
**Version:** 1.0
**Last Used:** YYYY-MM-DD
**Tags:** tag1, tag2, tag3

**Template:**
```
[The full prompt text here. Use {{VARIABLE}} for substitution points.]
```

**Variables:**
- `{{VARIABLE}}` — Description of what to substitute

**Best Used For:**
- Specific use case 1
- Specific use case 2

**Model Notes:**
- Works well with: (model types or sizes that perform best)
- Avoid with: (models that underperform on this prompt)

**Performance Notes:**
- What makes it work
- Known failure modes or edge cases

**Version History:**
- v1.0 (YYYY-MM-DD) — Initial capture
```

---

## Prompt Scoring Rubric

Score each prompt 1–10 across three dimensions, then average:

| Dimension | What It Measures | 1 | 5 | 10 |
|-----------|------------------|---|---|-----|
| **Clarity** | How unambiguous the prompt is | Vague, requires guessing | Usually clear, occasional confusion | Crystal clear, zero ambiguity |
| **Reliability** | Consistency of output quality | Hit or miss | Good most of the time | Consistently excellent |
| **Versatility** | Range of situations it works for | Single narrow use | A few use cases | Reusable across many contexts |

**Final Score = (Clarity + Reliability + Versatility) / 3**

Score thresholds:
- **8–10 → Core Prompt** — High-value, use confidently, version carefully
- **6–7.9 → Solid Prompt** — Works well, refine over time
- **4–5.9 → Draft Prompt** — Functional but needs iteration
- **Below 4 → Retire** — Not pulling its weight; archive or kill

---

## Usage Patterns

### 1. Save a New Prompt

> "Save this prompt to the library: [paste prompt]. Category: writing. Notes: works great for newsletter intros."

Agent assigns the next ID (PL-001, PL-002, etc.), fills the record template, sets initial score as "unrated," and adds to the index.

---

### 2. Find a Prompt for a Task

> "I need a prompt for [task description]. Check the library first."

Agent searches by category and tags, surfaces relevant matches with their scores, and either returns the best match or drafts a new one if nothing fits.

---

### 3. Rate or Update a Prompt

> "Update PL-012 — the output was shallow. Score it a 5 for reliability. Add a note: needs more explicit output format instructions."

Agent updates the record, bumps the version to v1.1, adds a version history entry, and notes the date.

---

### 4. Version a Prompt

> "Version PL-007. Here's the updated version: [new prompt text]. Reason: added chain-of-thought instruction."

Agent archives the old version in version history, replaces the template with the new version, and increments version number.

---

### 5. Library Dashboard

> "Give me a prompt library overview."

Agent returns:

```
📚 PROMPT LIBRARY — [Date]

Total: [N] prompts
Core (8+): [N] | Solid (6-8): [N] | Draft (<6): [N] | Unrated: [N]

By Category:
  research: [N]  writing: [N]  analysis: [N]  planning: [N]
  coding: [N]    brainstorm: [N]  review: [N]  ops: [N]  meta: [N]

Most Used: [Top 3 by last-used date]
Highest Scored: [Top 3 by score]
Needs Attention: [Drafts that haven't been revised in 30+ days]

Last reviewed: [date]
```

---

### 6. Category Deep Dive

> "Show me all my writing prompts sorted by score."

Agent returns a table of all prompts in the category with ID, name, score, version, and last-used date.

---

### 7. Build a Prompt from Scratch

> "Help me build a prompt for [task]. I want it to [goals]. Add it to the library when we're done."

Agent iterates with you, tests variations, and saves the final version with initial score and your notes.

---

### 8. Prompt A/B Log

> "Log an A/B test: tested PL-003 vs PL-015 for competitor analysis. PL-015 won — more structured output."

Agent adds to the A/B test log section of the library file.

---

### 9. Review Stale Prompts

> "Which prompts haven't been used in 60+ days? Flag ones worth retiring."

Agent scans last-used dates, flags candidates, and asks for your decision: keep, retire, or update.

---

### 10. Export Prompt Set

> "Export all my research prompts as a clean list I can share."

Agent generates a shareable markdown list (IDs stripped, personal notes removed, variables labeled clearly).

---

## Prompt Library File Structure

```
workspace/
├── prompt-library.md        # Main library (index + all records)
└── prompt-library/
    ├── ab-tests.md          # A/B test log (optional)
    └── retired/
        └── archive.md       # Retired prompts (for reference)
```

Alternatively, split by category for large libraries:

```
workspace/
└── prompt-library/
    ├── README.md            # Index and stats
    ├── research.md
    ├── writing.md
    ├── analysis.md
    └── ...
```

---

## A/B Test Log Format

```markdown
## A/B Tests

### [Date] — [Task Description]
- **Prompt A:** PL-###
- **Prompt B:** PL-###
- **Test:** [What you asked both to do]
- **Result:** [Which won and why]
- **Action:** [Updated scoring / versioned winner / retired loser]
```

---

## Heartbeat Integration

Add to `HEARTBEAT.md`:

```markdown
## Prompt Library
- If I've mentioned saving a prompt this week but the library hasn't
  been updated, remind me to capture it.
- Weekly: flag any Draft prompts (score < 6) that are over 14 days old
  with no updates — should be improved or retired.
```

---

## Cron: Weekly Prompt Review (Optional)

Schedule a weekly prompt health check:

```
openclaw cron add \
  --name "prompt-library-review" \
  --cron "0 9 * * 1" \
  --model "anthropic/claude-sonnet-4-6" \
  --session isolated \
  --message "Review prompt-library.md. Flag: (1) prompts scored below 5 that haven't been updated in 14+ days, (2) prompts last used 60+ days ago worth retiring, (3) unrated prompts that should be scored. Deliver a brief action list." \
  --announce \
  --tz "America/Chicago"
```

---

## Integrations

| Skill | How It Connects |
|-------|----------------|
| `writing-assistant` | Save voice profile prompts, editing prompts, subject line formulas |
| `research-assistant` | Save research brief templates, source evaluation prompts |
| `content-calendar` | Save content batch prompts, ideation prompts, repurposing formulas |
| `newsletter-manager` | Save issue drafting prompts, subject line templates, CTA variations |
| `social-media-manager` | Save platform-specific caption formulas, hook patterns |
| `meeting-assistant` | Save meeting prep prompts, action item extraction prompts |
| `financial-tracker` | Save analysis prompts for interpreting financial data |
| `security-hardening` | Save audit prompts, review checklists |

---

## Customization

**Custom categories:** Replace or add to the default set. Common additions: `client-comms`, `legal-review`, `product`, `seo`, `ads`.

**Team use:** Shared prompt libraries work well in collaborative workspaces. Add a `contributor` field to records and use the export pattern to share high-value prompts.

**Model-specific libraries:** If you work across multiple models, add a `model` field to records and filter by model when searching.

**Prompt chaining:** Some tasks are multi-step prompt chains. Use a `chain` tag and document the sequence in performance notes.

**Minimal setup:** You don't need the full structure. Start with a single `prompt-library.md` and just the template. Add scoring and versioning once you have 20+ prompts.

---

## Troubleshooting

**"The library is getting too long to search"**
Split into per-category files and use a master index in `README.md`. Tell your agent to always check the index first.

**"I keep forgetting to save prompts"**
Add the AGENTS.md standing instruction (Step 3). Also useful: end-of-session habit of asking "did we use any prompts worth saving?"

**"My scores feel arbitrary"**
Use the A/B test log to calibrate. After 10 tests, your score intuitions become more consistent.

**"Some prompts are too context-specific to generalize"**
That's fine — keep them. Use specific tags (project name, client name) so they're findable without polluting general searches. Note context requirements in "Best Used For."

**"How do I handle prompts with lots of variables?"**
Document each variable clearly. If there are more than 5 variables, consider splitting into a simpler base prompt plus a specialization layer.

---

## Privacy Note

Your prompt library may contain context-specific language, internal business logic, or sensitive framing. It is local by default. Before exporting or sharing any prompt:
- Strip business-specific context
- Remove variable examples that contain private data
- Review for inadvertent information disclosure

The export pattern (Usage Pattern #10) is designed to help you share clean versions.

---

*The Agent Ledger publishes practical AI systems for solopreneurs and creators.*
*Get new skills and guides at [theagentledger.com](https://theagentledger.com)*
*→ Subscribe to the newsletter for weekly AI workflow breakdowns*
