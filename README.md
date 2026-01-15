# ForgeVista UAP

Your path from spreadsheets to data-driven consulting.

## What is UAP?

UAP (User-Agent Pair) is a progression system that grows with your projects.
Start simple. Add capabilities when you need them.

## Four Tiers

| Tier | What You Get | Best For |
|------|--------------|----------|
| **Core** | Claude Code on your machine | Getting started, simple automation |
| **Analytics** | Dashboards + local database | Client reports, data visualization |
| **Platform** | Full data pipelines + Docker | Large datasets, scheduled processing |
| **Enterprise** | Custom infrastructure | Data center scale, dedicated support |

## Which Tier Is Right for You?

**Start with Core if you:**
- Want to try AI-assisted coding
- Work mainly with Excel and simple scripts
- Need quick answers, not complex systems

**Move to Analytics when you:**
- Build recurring client reports
- Need interactive dashboards
- Work with data files under 10GB

**Consider Platform when you:**
- Process data from multiple sources daily
- Need scheduled, automated pipelines
- Work with datasets over 10GB

**Contact us about Enterprise when you:**
- Require dedicated infrastructure
- Need custom security or compliance
- Have data center-scale workloads

See [Tier Selection Guide](docs/tier-selection.md) for detailed criteria.

## Getting Started

### Core (Start Here)

1. Clone the Core repository
2. Run the setup script
3. Start using Claude Code

```bash
git clone https://github.com/ForgeVista/fv-uap-core
cd fv-uap-core
./bootstrap.sh
```

[Go to Core Setup](https://github.com/ForgeVista/fv-uap-core)

### Analytics (When Ready)

1. Use Core as your base
2. Clone the Analytics template for your project
3. Build dashboards with your data

[Go to Analytics Template](https://github.com/ForgeVista/fv-uap-analytics)

### Platform (Advanced)

1. Use Core as your base
2. Clone the Platform template for your project
3. Set up data pipelines with Docker

[Go to Platform Template](https://github.com/ForgeVista/fv-uap-platform)

## Upgrading Between Tiers

You don't lose work when you upgrade. Each tier builds on the previous.

- Core to Analytics: Add dashboards to your existing setup
- Analytics to Platform: Keep your dashboards, add pipelines

See [Migration Paths](docs/migration-paths.md) for step-by-step guides.

## IT Approval

These tools are designed to be transparent and auditable.

- No hidden software
- No admin rights required for most installs
- Open source components

See [IT Security Guide](docs/it-security.md) for talking points.

## Need Help?

- **Technical issues**: Open an issue in the relevant repository
- **Tier questions**: See [Tier Selection Guide](docs/tier-selection.md)
- **Enterprise inquiries**: [Contact ForgeVista](docs/enterprise.md)

## Related Repositories

| Repository | Purpose |
|------------|---------|
| [fv-uap-core](https://github.com/ForgeVista/fv-uap-core) | Machine setup for Claude Code |
| [fv-uap-analytics](https://github.com/ForgeVista/fv-uap-analytics) | Dashboard + database template |
| [fv-uap-platform](https://github.com/ForgeVista/fv-uap-platform) | Data pipeline + Docker template |
