# GHL OpsOS Automation Skill
## GoHighLevel Operations Orchestration via Claude Code

---

## Overview

This skill enables Claude Code to operate as **OpsOS (Operations Orchestration System)** — a senior management and operations specialist that designs, builds, and optimizes GoHighLevel (GHL) workflows for service businesses.

When connected to GHL via MCP, this skill provides direct CRM automation capabilities including contact management, pipeline orchestration, appointment booking, messaging, and retention automation.

---

## Setup

### Prerequisites
1. Active GoHighLevel account (any plan)
2. Claude Code CLI, Desktop App, or Web App
3. Private Integration Token (PIT) from GHL

### Connect GHL MCP Server

1. In GHL: **Settings → Integrations → Private Integrations → Create New**
2. Name: `OpsOS - Claude Code`
3. Select scopes: contacts (r/w), opportunities (r/w), calendars (r/w), conversations (r/w), workflows (r), users (r), locations (r), tags (r/w), custom fields (r/w), custom values (r/w)
4. Generate and copy the token

5. Add to Claude Code settings (`.claude/settings.json`):

```json
{
  "mcpServers": {
    "ghl": {
      "type": "streamable-http",
      "url": "https://services.leadconnectorhq.com/mcp/",
      "headers": {
        "Authorization": "Bearer YOUR_PIT_TOKEN"
      }
    }
  }
}
```

6. Restart Claude Code

---

## Capabilities

### When Connected via MCP (Direct Implementation)
- **Contacts:** Create, update, search, tag, and segment contacts
- **Pipelines:** Create pipeline stages, move opportunities, track velocity
- **Calendars:** Read availability, book appointments, manage schedules
- **Conversations:** Send SMS, email, read replies, manage threads
- **Tags:** Create, apply, remove tags for workflow logic
- **Custom Fields:** Create and manage data architecture
- **Opportunities:** Create, update, move through pipeline stages
- **Reporting:** Pull pipeline metrics, conversation analytics, contact data

### Without MCP (Blueprint Mode)
- Design complete workflow architectures
- Generate GHL build specifications
- Create SMS/email/VM copy libraries
- Produce SOPs and operational documentation
- Define custom field/tag/pipeline architectures

---

## Usage

### Invoke the Skill

```
/ghl-opsos-automation
```

Or reference in conversation:
```
"Use the OpsOS skill to build a lead nurture workflow for my business"
```

### Example Commands

**Audit current GHL setup:**
```
Review my GHL pipelines, contacts, and active workflows. Identify gaps and optimization opportunities.
```

**Build a workflow:**
```
Build a lead nurture workflow for [business type] with speed-to-lead automation, follow-up sequences, and no-show recovery.
```

**Create contacts from data:**
```
Import these leads into GHL with proper tagging and pipeline placement: [data]
```

**Pipeline health check:**
```
Show me all stalled leads, at-risk members, and pipeline bottlenecks.
```

**Generate copy:**
```
Write SMS and email templates for my [workflow type] in my brand voice.
```

---

## Workflow Library

OpsOS includes pre-built blueprints for 5 core lifecycle workflows:

| # | Workflow | Description |
|---|----------|-------------|
| 01 | Lead Nurture + Appointment Setting | Speed-to-lead, multi-channel follow-up, reminders, no-show recovery |
| 02 | Sales Pipeline Optimization | Stage automation, hygiene, stalled lead detection, deal velocity |
| 03 | Client Onboarding | Welcome sequence, session booking, milestone tracking, app setup |
| 04 | Retention & Reactivation | 3-tier churn prevention, block renewal, quarterly win-back |
| 05 | Referral Engine | Athlete referrals, parent ambassadors, coach partnerships |

Each includes: trigger logic, condition trees, timing, copy, edge cases, QA plan, KPIs, and rollback procedures.

---

## Operating Rules

1. **Approval Required** — Never publish/activate workflows without explicit user approval
2. **Safety-First** — All changes reversible with documented rollback steps
3. **Read-Only Default** — When connected via MCP, default to read operations. Write operations require explicit authorization.
4. **Evidence-Driven** — Every workflow defines KPIs and measurement
5. **GHL-Native First** — Platform tools first; external integrations only when necessary

---

## Five-Phase Development Process

1. **Discovery** — Clarify goals, audience, success metrics, current state
2. **Design** — Triggers, conditions, logic flows, timing, channels
3. **Build** — Workflow blueprint with full trigger → condition → action mapping
4. **QA** — Test cases, edge cases, validation before activation
5. **Deploy** — Staged rollout with monitoring and iteration

---

## Compatibility

- **GHL Plans:** All (Starter, Unlimited, SaaS Pro)
- **MCP Server:** Official HighLevel MCP (`services.leadconnectorhq.com/mcp/`)
- **Claude Code:** CLI, Desktop, Web App
- **Industries:** Service businesses, fitness/sports, agencies, coaching, healthcare, real estate

---

## Security

- Never store PIT tokens in repositories
- Tokens go in local Claude Code settings only
- Revoke tokens immediately if compromised
- All write operations logged and auditable
- DNC/compliance checks built into all messaging workflows
