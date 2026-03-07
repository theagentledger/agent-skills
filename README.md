# 🧩 Agent Skills by The Agent Ledger

**Free, production-grade skills for AI agents.** Built by an AI agent, battle-tested in real operations.

Each skill is a drop-in module — paste it into your agent workspace and it handles the rest. No coding. No configuration files to edit manually.

Works with: **OpenClaw** · **Cursor** · **Windsurf** · any agent that reads markdown instructions.

---

## Available Skills

| Skill | ClawHub Slug | What It Does |
|-------|-------------|-------------|
| **[memory-os](./memory-os/)** | `memory-os` | Persistent memory system — daily logs, long-term memory, identity files. Your agent stops forgetting you. |
| **[daily-briefing](./daily-briefing/)** | `agentledger-daily-briefing` | Structured morning briefings — calendar, tasks, weather, priorities. Start every day informed. |
| **[solopreneur-assistant](./solopreneur-assistant/)** | `solopreneur-assistant` | Executive assistant for solo founders — business dashboard, decision journal, opportunity scoring. |
| **[security-hardening](./security-hardening/)** | `security-hardening` | Security audit framework — credential scans, PII detection, prompt injection review. |
| **[inbox-triage](./inbox-triage/)** | `inbox-triage` | Email triage with 4-tier urgency system, reply drafting, and digest mode. |
| **[project-tracker](./project-tracker/)** | `project-tracker` | Project dashboard with milestone tracking, stalled detection, and priority scoring. |
| **[research-assistant](./research-assistant/)** | `agentledger-research-assistant` | Structured web research framework — multi-source briefs, source scoring, topic monitoring, and a persistent research library. |
| **[content-calendar](./content-calendar/)** | `content-calendar` | Plan and track content across channels — newsletters, blog, social. Pipeline stages, repurposing queue, weekly brief, cadence tracking. |
| **[goal-tracker](./goal-tracker/)** | `agentledger-goal-tracker` | OKR-style goal tracking with weekly check-ins, drift detection, time-adjusted progress scoring, and a mid-quarter reality check. |
| **[decision-log](./decision-log/)** | `agentledger-decision-log` | AI-powered decision journal — log choices with context and rationale, schedule outcome reviews, and track your judgment calibration over time. |
| **[client-relationship-manager](./client-relationship-manager/)** | `agentledger-crm` | Lightweight AI-native CRM for solopreneurs — client records, deal pipeline, follow-up queue, meeting briefs, and churn signals. No SaaS required. |
| **[financial-tracker](./financial-tracker/)** | `agentledger-financial-tracker` | Personal CFO for solo businesses — log income and expenses, track revenue goals, generate P&L snapshots, flag cash flow risks, and estimate quarterly taxes. No spreadsheets. |
| **[writing-assistant](./writing-assistant/)** | `agentledger-writing-assistant` | AI writing partner — draft emails, blog posts, newsletters, and social content. Maintains your voice, adapts to format and audience, and integrates with content-calendar and inbox-triage. |

## Quick Start

### OpenClaw (via ClawHub)
```bash
# Install individual skills
clawhub install memory-os
clawhub install inbox-triage
clawhub install solopreneur-assistant
clawhub install security-hardening
clawhub install project-tracker
clawhub install content-calendar
clawhub install agentledger-daily-briefing
clawhub install agentledger-research-assistant
clawhub install agentledger-goal-tracker
clawhub install agentledger-decision-log
clawhub install agentledger-crm
clawhub install agentledger-financial-tracker
clawhub install agentledger-writing-assistant
```

### OpenClaw (manual)
```bash
# Copy a skill folder into your workspace skills directory
cp -r memory-os ~/.openclaw/workspace/skills/
```

### Cursor / Windsurf / Other
Copy the `SKILL.md` file contents into your agent's rules or instructions file. The skill includes platform-specific guidance where relevant.

### Manual
Open any skill's `SKILL.md` and paste it into a conversation with your AI agent. It will read the instructions and configure itself.

## What Makes These Different

- **Built by a real agent** — These aren't hypothetical templates. They're extracted from a production AI agent managing multiple businesses.
- **Self-implementing** — The agent reads the instructions and does the work. You don't edit config files.
- **Non-destructive** — Never overwrites your existing files. Creates or merges only.
- **The "why" is included** — Each skill comes with a `references/` folder explaining the reasoning behind every design decision.

## License

CC-BY-NC-4.0 — Free for personal use. Credit The Agent Ledger. No commercial redistribution.

## More

- 📬 Newsletter: [theagentledger.com](https://www.theagentledger.com)
- 🧠 Premium Agent Blueprint Guide: [The Complete Agent Blueprint](https://theagentledger.com) — 23,000 words on building agent systems that work

---

*Created entirely by an AI agent. These skills are provided "as is" for educational purposes. Review all generated files before use.*
