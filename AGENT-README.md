# ForgeVista UAP (Agent Technical Reference)

This document provides comprehensive technical context for AI agents operating within the UAP ecosystem.

## Architecture Overview

UAP (User-Agent Pair) is a tiered system for progressively adding data engineering capabilities to consulting workflows.

```
┌─────────────────────────────────────────────────────────────┐
│                    UAP Progression                          │
├─────────────┬─────────────┬─────────────┬─────────────────┤
│   Core      │  Analytics  │  Platform   │   Enterprise    │
│  (Tier 1)   │  (Tier 2)   │  (Tier 3)   │    (Tier 4)     │
├─────────────┼─────────────┼─────────────┼─────────────────┤
│ Claude Code │ + DuckDB    │ + Docker    │ + Dedicated     │
│ Python 3.11+│ + Evidence  │ + Dagster   │   Infrastructure│
│ WSL (Win)   │             │ + dbt       │                 │
└─────────────┴─────────────┴─────────────┴─────────────────┘
```

## Repository Structure

| Repository | Pattern | Purpose |
|------------|---------|---------|
| `fv-uap-hub` | Documentation | Umbrella repo - tier selection, migration guides |
| `fv-uap-core` | Clone + Init | Machine bootstrap - run once to set up environment |
| `fv-uap-analytics` | Template | Fork per project - DuckDB + Evidence.dev dashboards |
| `fv-uap-platform` | Template | Fork per project - Dagster + dbt pipelines |

## Bootstrap Pattern

All tiers follow the same bootstrap philosophy:

1. **Check** what's already installed
2. **Install** only what's missing
3. **Don't conflict** with existing tools
4. **Idempotent** - safe to re-run

### Core Bootstrap (fv-uap-core)

```bash
# Required
- Python 3.11+
- Claude Code CLI

# Optional (Claude can manage)
- uv
- Node.js

# Windows-specific
- WSL (Windows Subsystem for Linux)
```

### Analytics Bootstrap (fv-uap-analytics)

```bash
# Required
- Git
- Node.js 16+
- npm
- DuckDB CLI

# Installed by bootstrap
- Evidence.dev (@evidence-dev/evidence)
```

### Platform Bootstrap (fv-uap-platform)

```bash
# Required
- Docker
- Docker Compose

# Containerized (no local install needed)
- Dagster
- dbt
- PostgreSQL
```

## Log Format Standard

All bootstrap scripts use consistent log format:

```bash
info() { echo "[INFO] $*"; }
warn() { echo "[WARN] $*"; }
ok()   { echo "[ OK ] $*"; }
fail() { echo "[FAIL] $*"; exit 1; }
```

## CLI Flags

Bootstrap scripts support:

| Flag | Purpose |
|------|---------|
| `--yes` | Non-interactive mode (auto-yes to prompts) |
| `--check-only` | Validation only, no installations |
| `-h`, `--help` | Show usage information |

## Exit Codes

| Code | Meaning |
|------|---------|
| 0 | Success - all requirements met |
| 1 | Failure - missing required components |
| 2 | Invalid arguments |

## File Organization

Each repo follows the two-README pattern:

```
repo/
├── README.md          # Non-technical users (consultants)
├── AGENT-README.md    # AI agents (this file pattern)
├── CLAUDE.md          # Claude Code context
├── bootstrap.sh       # Setup script
└── scripts/
    └── check-installed.sh  # Validation-only script
```

## IT Security Considerations

These repos are designed for IT approval:

- **Minimal dependencies** - only essential tools
- **Transparent installations** - no hidden software
- **Auditable scripts** - shell scripts are readable
- **No admin rights** - user-level installs where possible
- **Open source** - all components are OSS

## Cross-Repo Consistency Requirements

When modifying any UAP repo, maintain:

1. **Naming conventions**: `fv-uap-*` prefix
2. **Log format**: Bracketed format `[INFO]`, `[WARN]`, `[ OK ]`, `[FAIL]`
3. **CLI flags**: `--yes` and `--check-only` where applicable
4. **Documentation**: README.md + AGENT-README.md + CLAUDE.md
5. **Scripts directory**: `scripts/check-installed.sh` for validation

## Tier Migration

### Core to Analytics

1. Core remains as base (machine setup)
2. Clone fv-uap-analytics for project
3. Run analytics bootstrap
4. DuckDB + Evidence added to project

### Analytics to Platform

1. Keep existing analytics dashboards
2. Clone fv-uap-platform for project
3. Run platform bootstrap (Docker)
4. Add Dagster pipelines that feed dashboards

## Environment Variables

| Variable | Repo | Purpose |
|----------|------|---------|
| `CLAUDE_INSTALL_CMD` | Core | Custom Claude Code install command |
| `DBT_PROFILES_DIR` | Platform | dbt profiles location |
| `DAGSTER_HOME` | Platform | Dagster configuration directory |
| `POSTGRES_*` | Platform | Database connection settings |

## Common Troubleshooting

### Python version issues
```bash
# Check version
python3 --version

# Must be 3.11+
# If older, bootstrap will attempt to install
```

### Claude Code not found
```bash
# Verify installation
which claude
claude --version

# If missing, use org-approved install method
# Set CLAUDE_INSTALL_CMD for custom installs
```

### Docker issues (Platform tier)
```bash
# Check Docker running
docker info

# Check compose
docker compose version
```

## Related Documentation

- [Tier Selection Guide](docs/tier-selection.md) - Decision matrix
- [Migration Paths](docs/migration-paths.md) - Upgrade procedures
- [IT Security Guide](docs/it-security.md) - Approval talking points
- [Enterprise](docs/enterprise.md) - Tier 4 inquiries
