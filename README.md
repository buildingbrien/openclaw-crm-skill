# 🤖 OpenClaw CRM Skill

An open-source OpenClaw skill that turns your AI agent into a full CRM operator — contact management, lead scoring, automated follow-ups, and pipeline tracking.

## Why This Exists

CRM is the #1 use case enterprises ask about when evaluating OpenClaw. There's no production-ready open-source skill for it. This project changes that.

Built by [Brien Collier](https://linkedin.com/in/briencollier) at [Lucaryin LLC](https://lucaryin.com), extracted from a production agentic CRM deployed to paying clients.

## Features

- **Contact Management** — Create, update, search, and organize contacts with full conversation history
- **Lead Scoring** — Automated lead scoring based on engagement signals, response patterns, and custom criteria
- **Pipeline Tracking** — Visual pipeline stages with automated stage transitions and deal tracking
- **Automated Follow-ups** — Smart follow-up scheduling based on contact activity and pipeline position
- **Multi-CRM Integration** — HubSpot, Zoho CRM, and custom database backends (Supabase/Postgres)
- **Proactive Outreach** — Agent-initiated outreach based on triggers (new lead, stale deal, milestone)

## Architecture

```
┌─────────────────────────────────────┐
│           OpenClaw Agent            │
│  (Calendar, Email, Messaging, etc.) │
└──────────────┬──────────────────────┘
               │
       ┌───────▼────────┐
       │   CRM Skill    │
       │  ┌───────────┐ │
       │  │ Contacts   │ │
       │  │ Pipeline   │ │
       │  │ Scoring    │ │
       │  │ Follow-ups │ │
       │  └───────────┘ │
       └───────┬────────┘
               │
    ┌──────────┼──────────┐
    ▼          ▼          ▼
 HubSpot    Zoho     Supabase
```

## Quick Start

```bash
# Install the skill
clawhub install buildingbrien/openclaw-crm-skill

# Or clone and install manually
git clone https://github.com/buildingbrien/openclaw-crm-skill.git
cd openclaw-crm-skill
# Follow setup in SKILL.md
```

## Configuration

```toml
# config.toml
[crm]
backend = "supabase"  # or "hubspot", "zoho"
scoring_model = "engagement"  # or "custom"

[crm.supabase]
url = "your-supabase-url"
key = "your-service-key"

[crm.hubspot]
api_key = "your-hubspot-key"

[crm.follow_ups]
default_interval_days = 3
max_attempts = 5
quiet_hours = ["22:00", "08:00"]
```

## Current Status

🟡 **Active Development** — Core contact management and pipeline tracking are production-tested. Lead scoring and multi-CRM adapters are being extracted from production deployments.

### Roadmap

- [x] Contact CRUD with conversation history
- [x] Pipeline stages and deal tracking
- [x] Automated follow-up scheduling
- [x] Supabase/Postgres backend
- [ ] HubSpot adapter (in progress)
- [ ] Zoho CRM adapter (in progress)
- [ ] Configurable lead scoring models
- [ ] ClawHub publishing
- [ ] Email campaign integration
- [ ] Analytics dashboard skill

## Production Background

This skill is extracted from a production agentic CRM system that:
- Manages a live client's sales pipeline (going live Feb 2026)
- Handles automated outreach and follow-ups
- Integrates with email, calendar, and messaging via OpenClaw
- Has been tested across 12+ concurrent OpenClaw agent deployments

## Contributing

PRs welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Key areas we need help:
- CRM platform adapters (Salesforce, Pipedrive, etc.)
- Lead scoring model improvements
- Test coverage
- Documentation

## License

MIT — use it, fork it, ship it.

## About

Built by **Brien Collier** at **Lucaryin LLC**
- 🌐 [lucaryin.com](https://lucaryin.com)
- 📧 brien@lucaryin.com
- 𝕏 [@buildingbrien](https://x.com/buildingbrien)

5 years at Comcast building agentic sales frameworks at enterprise scale. Now deploying OpenClaw agents as production employees for businesses.
