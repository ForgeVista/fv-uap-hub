# IT Security Guide

Talking points for IT approval conversations.

## Summary for IT

| Concern | UAP Answer |
|---------|------------|
| Admin rights needed? | No (for Core and Analytics) |
| Data leaves machine? | Only if you choose to send it |
| What gets installed? | Open source tools only |
| Network access? | Internet for initial install only |
| Audit trail? | Git tracks all changes |

---

## Tier-by-Tier Security Profile

### Core (Lowest Risk)

**What gets installed:**
- Python (programming language)
- Claude Code (AI assistant CLI)

**Network activity:**
- Initial download of Python packages
- Claude API calls when you explicitly ask questions
- No background network activity

**Data handling:**
- Your data stays on your machine
- Claude only sees what you paste or reference
- No automatic data upload

**Admin rights:**
- Not required on most systems
- Uses user-space installation

---

### Analytics (Low Risk)

**Additional installs:**
- DuckDB (embedded database, no server)
- Evidence.dev (dashboard framework)
- Node.js (JavaScript runtime)

**Network activity:**
- Same as Core, plus:
- npm packages during initial setup
- No ongoing network requirements

**Data handling:**
- Database runs entirely local
- Dashboards served from localhost only
- No external data connections unless you add them

**Admin rights:**
- Not required

---

### Platform (Medium Risk)

**Additional installs:**
- Docker Desktop
- PostgreSQL (in container)
- Dagster (in container)
- dbt (in container)

**Network activity:**
- Docker image downloads during setup
- Container images from Docker Hub
- No ongoing external connections by default

**Data handling:**
- All data stays in Docker volumes on your machine
- External connections only if you configure them
- Pipeline outputs stored locally

**Admin rights:**
- May require admin for Docker Desktop installation
- Docker itself runs without admin after install

---

## Common IT Questions

### "What data does Claude see?"

Claude Code only processes:
- Text you explicitly type or paste
- Files you explicitly reference with `@filename`
- Nothing is sent automatically

You control what goes to the API.

### "Is this approved software?"

All components are:
- Open source with public code
- Widely used in enterprise settings
- Auditable (you can inspect every line)

| Component | License | Used by |
|-----------|---------|---------|
| Python | PSF License | Most enterprises |
| DuckDB | MIT | MotherDuck, many analytics teams |
| Evidence | MIT | Data teams globally |
| Docker | Apache 2.0 | Standard infrastructure |
| Dagster | Apache 2.0 | Data engineering teams |
| dbt | Apache 2.0 | 30,000+ companies |

### "What about Claude Code itself?"

Claude Code is:
- Made by Anthropic (established AI company)
- Runs locally on your machine
- Sends only what you choose to send
- Uses standard HTTPS encryption

### "Can we audit what's happening?"

Yes:
- All code changes tracked in Git
- Claude conversations can be logged
- Network traffic is standard HTTPS
- No hidden processes or services

### "What ports does this open?"

| Tier | Ports | Exposure |
|------|-------|----------|
| Core | None | N/A |
| Analytics | 3000 | localhost only |
| Platform | 3000, 5432, 8080 | localhost only |

All services bind to `localhost` by default. Nothing is exposed to the network.

---

## Data Classification

### Recommended for UAP

- Internal working documents
- Non-sensitive client data
- Aggregated metrics
- Public information

### Requires Additional Review

- PII (personally identifiable information)
- Financial records
- Healthcare data (PHI)
- Data subject to specific regulations

### Not Recommended

- Classified information
- Critical infrastructure data
- Data with strict residency requirements

---

## Compliance Considerations

### SOC 2

- All processing happens locally
- Audit trails via Git
- No third-party data storage (except Claude API calls)

### GDPR

- Data stays on your machine
- You control what's sent to Claude
- No automatic data transfers

### HIPAA

- Not recommended for PHI without additional safeguards
- Consider Enterprise tier for healthcare data

---

## Requesting IT Approval

### Suggested Email Template

```
Subject: Request to Install UAP Development Tools

Hi [IT Contact],

I'd like to install the UAP (User-Agent Pair) toolkit for [brief use case].

What it includes:
- Python (standard programming language)
- Claude Code (AI coding assistant by Anthropic)
- [DuckDB/Evidence if Analytics tier]
- [Docker if Platform tier]

Security notes:
- No admin rights required [or: Docker requires one-time admin install]
- All data stays on my machine
- Open source, auditable components
- No network services exposed

Documentation: https://github.com/ForgeVista/fv-uap-hub

Happy to discuss or provide additional details.

Thanks,
[Your name]
```

---

## Contact

For Enterprise security requirements or custom compliance needs:
- See [Enterprise Guide](enterprise.md)
- Contact ForgeVista for dedicated support options
