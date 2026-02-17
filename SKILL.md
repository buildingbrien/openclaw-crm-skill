# OpenClaw CRM Skill

Agentic CRM management for OpenClaw — contacts, pipeline, scoring, follow-ups.

## Prerequisites

- OpenClaw gateway running
- One of: Supabase project, HubSpot API key, or Zoho CRM API key
- (Optional) Email skill configured for automated outreach

## Installation

```bash
clawhub install buildingbrien/openclaw-crm-skill
```

## Commands

### Contact Management
- `crm contact add <name> <email> [phone] [company]` — Add a new contact
- `crm contact search <query>` — Search contacts by name, email, or company
- `crm contact update <id> <field> <value>` — Update contact fields
- `crm contact history <id>` — View interaction history

### Pipeline
- `crm pipeline list` — Show all deals by stage
- `crm pipeline move <deal_id> <stage>` — Move deal to new stage
- `crm pipeline add <contact_id> <deal_name> <value>` — Create new deal
- `crm pipeline stats` — Pipeline analytics (conversion rates, avg deal time)

### Follow-ups
- `crm followup schedule <contact_id> <date> <message>` — Schedule follow-up
- `crm followup list` — Show pending follow-ups
- `crm followup auto` — Run automated follow-up engine

### Lead Scoring
- `crm score <contact_id>` — Get current lead score
- `crm score recalculate` — Recalculate all scores based on recent activity

## Proactive Behaviors

When installed, the CRM skill enables proactive agent behaviors:
- Alerts when a deal has been stale for >N days
- Suggests follow-ups based on engagement patterns
- Flags high-score leads for immediate attention
- Summarizes pipeline changes during heartbeat checks

## Backend Adapters

### Supabase (default)
Full schema provided in `migrations/`. Run:
```bash
supabase db push --db-url <your-connection-string>
```

### HubSpot
Set `HUBSPOT_API_KEY` in your environment. The adapter maps OpenClaw CRM concepts to HubSpot objects automatically.

### Zoho CRM
Set `ZOHO_CRM_TOKEN` in your environment. Requires Zoho CRM API v2 access.
