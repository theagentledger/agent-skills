# Legal Professional

**Subtitle:** Configure Your AI as a Law Practice Assistant

**Version:** 1.0.0  
**Author:** The Agent Ledger  
**License:** CC-BY-NC-4.0

---

## What It Does

Turn Claude or ChatGPT into a jurisdiction-aware legal research, drafting, and client communication assistant. Designed for attorneys who want to leverage AI for research and document drafting without expensive SaaS subscriptions — while maintaining proper ethical guardrails and client confidentiality.

- **Legal research** with proper citations and risk assessment
- **Document drafting** with customizable templates and AI disclaimers  
- **Matter tracking** with jurisdiction awareness and deadline management
- **Client communication** automation (status letters, intake responses)
- **Conflict detection** and ethics compliance protocols
- **Multi-jurisdiction support** with jurisdiction-specific rules

---

## Quick Start

1. Copy the engagement letter and NDA templates from `SKILL.md`
2. Add the legal research protocol to your `SOUL.md` or system instructions
3. Create `legal-state.md` to track matters and deadlines
4. Test with: "Draft a [jurisdiction]-compliant NDA for [business type]"

---

## Files Included

- **SKILL.md** (25KB) — Complete setup guide, legal protocols, templates, integration patterns
- **references/advanced-patterns.md** (18KB) — Multi-jurisdiction workflows, conflict detection, litigation support, firm-level implementation

---

## Who This Is For

✅ **Perfect for:**
- Solo practitioners using Claude/ChatGPT for research and drafting
- In-house counsel managing multiple matters
- Contract-heavy practices (M&A, IP, corporate)
- Attorneys wanting to improve research efficiency without subscriptions to Westlaw/LexisNexis
- Multi-state practitioners needing jurisdiction awareness

❌ **Not ideal for:**
- Practices with zero AI experience (start with simpler skills)
- Highly regulated environments without AI ethics approval
- Attorneys uncomfortable with AI disclaimers/verification protocols

---

## Key Features

### Matter Tracking Template

Track active matters, deadlines, and key dates in one place:

```markdown
| Matter ID | Client | Practice Area | Status | Key Dates |
|-----------|--------|---------------|--------|-----------|
| 001 | Acme Corp | Contract review | Active | Deadline: 3/15 |
```

### Legal Research Protocol

Ask AI for research, get:
1. Primary authority (statutes, cases)
2. Secondary sources (treatises, law review)
3. Jurisdictional analysis
4. Risk assessment
5. Recommendation for further research

### Document Templates

- Client engagement letter
- Non-disclosure agreement (NDA)
- Contract redline checklist
- Legal research summary format
- Matter status letter

### Integration

Works seamlessly with other Agent Ledger skills:
- **financial-tracker** — Track billable hours and revenue by matter
- **time-tracker** — Log legal work sessions with matter codes
- **project-tracker** — Manage complex litigation as projects
- **decision-log** — Document strategic legal decisions
- **goal-tracker** — Set and track matter completion targets

---

## Customization

### By Practice Area

Add jurisdiction-specific configurations for:
- Corporate law
- Litigation
- Contract review
- Family law
- IP law
- Real estate

### By Firm Size

- **Solo practitioners:** Focus on matter tracking and deadline management
- **Small firms (2-10 attorneys):** Implement conflict checking and shared templates
- **In-house counsel:** Simplify for longer-running matters, emphasize compliance

---

## Ethical Use

This skill includes:
- ✅ Prominent legal disclaimers on all outputs
- ✅ Emphasis on attorney review before using any AI work product
- ✅ Confidentiality protocols (when to keep data local vs. cloud)
- ✅ Guidance on when NOT to use AI (strategic decisions, novel legal issues)
- ✅ State bar compliance checklist

**Always review:**
- Your state bar's guidance on AI in law practice
- Your malpractice insurance requirements
- Your firm's ethics policies

---

## What You'll Need

**Before using:**
- Subscription to Claude (claude.ai) or ChatGPT Plus
- Basic familiarity with structuring legal research questions
- Commitment to reviewing all AI work before client delivery
- Workspace directory for matter tracking (`legal-state.md`)

**Recommendations:**
- Read your state bar's AI ethics guidance
- Have a colleague review your first few AI-drafted documents
- Start with Tier 1 matters (high-volume, simple tasks) before complex work

---

## How It Works

### The Research Loop

1. **Ask the question:** "Research current law on [topic] in [jurisdiction]"
2. **AI researches:** Provides citations, cases, statutes
3. **You verify:** Check primary sources via Westlaw/LexisNexis
4. **You decide:** Make the legal call based on verified research
5. **You document:** Note that AI assisted in file

### The Drafting Loop

1. **Request template:** "Draft [document type] for [scenario]"
2. **AI generates draft:** Includes [[BLANK FIELD]] markers and disclaimers
3. **You customize:** Fill in blanks, modify for specific deal terms
4. **You review:** Verify jurisdiction-specific requirements
5. **You send:** Client gets clean document with AI attribution removed (if appropriate)

---

## Installation

### OpenClaw

```bash
clawhub install agentledger-legal-professional
```

Then add to your SOUL.md/custom instructions per the setup guide in SKILL.md.

### Claude AI / ChatGPT

Paste the legal research protocol from SKILL.md into your custom instructions. Use templates as-is for reference.

### Manual Installation

1. Copy `SKILL.md` to your reference materials
2. Create `legal-state.md` in your workspace
3. Add legal research protocol to your system prompt
4. Save document templates as local files

---

## Support & Next Steps

**Questions?** Review the troubleshooting section in SKILL.md.

**Want more?** Check out:
- **memory-os** — Set up long-term memory for client details
- **project-tracker** — Organize complex litigation workflows
- **decision-log** — Document strategic decisions for matters

**Have ideas?** The Agent Ledger is iterating based on user feedback. Reply to [theagentledger.com](https://theagentledger.com) newsletter.

---

## License

CC-BY-NC-4.0 — You can use and modify this skill for personal or firm use. Cannot commercialize without permission.

---

Built by The Agent Ledger — production-grade agent blueprints for modern practice.

Subscribe at [theagentledger.com](https://theagentledger.com)

---

**⚠️ DISCLAIMER:** This skill is guidance for setting up AI assistance for legal work. It does not constitute legal advice, does not create attorney-client relationships, and does not authorize practice of law. All AI-generated work requires attorney review. Compliance with state bar rules is your responsibility.
