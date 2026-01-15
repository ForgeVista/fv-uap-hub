# Tier Selection Guide

Use this guide to determine which UAP tier fits your project.

## Quick Decision Matrix

| Question | Core | Analytics | Platform | Enterprise |
|----------|:----:|:---------:|:--------:|:----------:|
| Working with Excel files? | Yes | Yes | Yes | Yes |
| Need AI coding assistance? | Yes | Yes | Yes | Yes |
| Building recurring reports? | - | Yes | Yes | Yes |
| Interactive dashboards? | - | Yes | Yes | Yes |
| Data files over 10GB? | - | - | Yes | Yes |
| Multiple data sources? | - | - | Yes | Yes |
| Scheduled pipelines? | - | - | Yes | Yes |
| Dedicated infrastructure? | - | - | - | Yes |
| Custom compliance needs? | - | - | - | Yes |

## Tier Details

### Tier 1: Core

**Best for**: Getting started with AI-assisted work

**You need Core if you:**
- Want to try Claude Code
- Work primarily with Excel and simple scripts
- Need quick answers, not complex systems
- Are comfortable with command line basics

**What you get:**
- Claude Code CLI on your machine
- Python 3.11+ environment
- Ability to write and run scripts

**You DON'T need Core if you:**
- Already have Claude Code installed
- Need dashboards or databases

---

### Tier 2: Analytics

**Best for**: Client reports and data visualization

**You need Analytics if you:**
- Build recurring reports for clients
- Want interactive dashboards
- Work with CSV, Excel, or JSON files
- Have data under 10GB total

**What you get:**
- Everything in Core, plus:
- DuckDB (fast local database)
- Evidence.dev (dashboard framework)
- Pre-configured project template

**Example use cases:**
- Monthly client performance reports
- Sales pipeline dashboards
- Financial trend visualizations
- Survey result summaries

**You DON'T need Analytics if you:**
- Only need one-off analysis (use Core)
- Have data over 10GB (consider Platform)
- Need real-time data updates (consider Platform)

---

### Tier 3: Platform

**Best for**: Data pipelines and automation

**You need Platform if you:**
- Process data from multiple sources
- Need scheduled, automated pipelines
- Work with datasets over 10GB
- Want data transformations tracked in version control

**What you get:**
- Everything in Analytics, plus:
- Docker containerized environment
- Dagster (pipeline orchestration)
- dbt (data transformations)
- PostgreSQL database

**Example use cases:**
- Daily data ingestion from multiple APIs
- Complex multi-step data transformations
- Large dataset processing (10GB+)
- Audit trails for data changes

**You DON'T need Platform if you:**
- Data fits in Excel (use Analytics)
- Updates are manual/ad-hoc (use Analytics)
- Don't need version-controlled transformations

---

### Tier 4: Enterprise

**Best for**: Data center scale and custom requirements

**Contact us about Enterprise if you:**
- Require dedicated infrastructure
- Have strict security or compliance needs
- Process data at data center scale
- Need custom integrations

**What you get:**
- Technology partner recommendation
- Custom infrastructure design
- Dedicated support options
- Compliance documentation

---

## Decision Flowchart

```
Start
  │
  ▼
Do you have Claude Code installed?
  │
  ├─ No ──► Start with CORE
  │
  ▼ Yes
  │
Do you need recurring reports or dashboards?
  │
  ├─ No ──► CORE is enough
  │
  ▼ Yes
  │
Is your data over 10GB?
  │
  ├─ No ──► Use ANALYTICS
  │
  ▼ Yes
  │
Do you need automated pipelines?
  │
  ├─ No ──► Use ANALYTICS (for now)
  │
  ▼ Yes
  │
Do you need dedicated infrastructure?
  │
  ├─ No ──► Use PLATFORM
  │
  ▼ Yes
  │
Contact us about ENTERPRISE
```

## Common Questions

**Can I start with Core and upgrade later?**
Yes. Each tier builds on the previous. You won't lose any work when upgrading.

**Do I need Platform just because I use Docker?**
No. If you're comfortable with Docker, you can use it with any tier. Platform is for when you need the full pipeline orchestration stack.

**What if my data is exactly 10GB?**
Try Analytics first. If performance becomes an issue, upgrade to Platform.

**Can I skip tiers?**
Yes, but Core is always recommended as the foundation. You can go directly to Platform if you know you need it.

## Next Steps

- [Core Setup](https://github.com/ForgeVista/fv-uap-core) - Start here
- [Analytics Template](https://github.com/ForgeVista/fv-uap-analytics) - Add dashboards
- [Platform Template](https://github.com/ForgeVista/fv-uap-platform) - Add pipelines
- [Migration Paths](migration-paths.md) - How to upgrade
