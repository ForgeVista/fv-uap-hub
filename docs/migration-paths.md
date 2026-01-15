# Migration Paths

Step-by-step guides for upgrading between UAP tiers.

## Overview

| From | To | Effort | Data Loss |
|------|-----|--------|-----------|
| Core | Analytics | Low | None |
| Core | Platform | Medium | None |
| Analytics | Platform | Low | None |

Each tier builds on the previous. You keep all your existing work.

---

## Core to Analytics

**When to upgrade**: You need recurring reports or interactive dashboards.

### Steps

1. **Keep your Core setup** - Analytics adds to it, doesn't replace it

2. **Clone the Analytics template**
   ```bash
   git clone https://github.com/ForgeVista/fv-uap-analytics my-project
   cd my-project
   ./bootstrap.sh
   ```

3. **Add your data files** to the `sources/` directory

4. **Write queries** in the `queries/` directory

5. **Build dashboards** in the `pages/` directory

### What Changes

| Before (Core) | After (Analytics) |
|---------------|-------------------|
| Python scripts only | Python + SQL + Dashboards |
| File-based data | DuckDB database |
| Manual runs | Evidence.dev server |

### Time Required

- Setup: ~15 minutes
- First dashboard: ~1 hour (depends on data complexity)

---

## Core to Platform

**When to upgrade**: You need automated pipelines or have data over 10GB.

### Steps

1. **Install Docker Desktop** if not already installed

2. **Clone the Platform template**
   ```bash
   git clone https://github.com/ForgeVista/fv-uap-platform my-project
   cd my-project
   ./bootstrap.sh
   ```

3. **Start the Docker stack**
   ```bash
   docker compose up -d
   ```

4. **Access the Dagster UI** at http://localhost:3000

5. **Add your first pipeline** in the `dagster/` directory

### What Changes

| Before (Core) | After (Platform) |
|---------------|------------------|
| Local Python | Docker containers |
| Manual runs | Scheduled pipelines |
| File storage | PostgreSQL database |
| No orchestration | Dagster + dbt |

### Time Required

- Setup: ~30 minutes (includes Docker installation)
- First pipeline: ~2 hours (depends on data sources)

---

## Analytics to Platform

**When to upgrade**: Your dashboards need larger datasets or automated refreshes.

### Steps

1. **Export your queries** - Copy your working SQL from Analytics

2. **Clone the Platform template**
   ```bash
   git clone https://github.com/ForgeVista/fv-uap-platform my-project
   cd my-project
   ./bootstrap.sh
   ```

3. **Move queries to dbt**
   - Place your SQL files in `dbt/models/`
   - Add a `schema.yml` for documentation

4. **Configure the pipeline** in Dagster to run dbt

5. **Keep using Evidence** - Platform includes it with PostgreSQL backend

### What You Keep

- All your SQL logic
- Dashboard layouts (may need minor config changes)
- Data transformation patterns

### What Changes

| Analytics | Platform |
|-----------|----------|
| DuckDB (local) | PostgreSQL (Docker) |
| Manual refresh | Dagster schedules |
| Single file queries | dbt models |

### Time Required

- Migration: ~1-2 hours (depends on query complexity)
- Testing: ~30 minutes

---

## Tips for Successful Upgrades

1. **Test with sample data first** - Don't migrate production data until confident

2. **Keep your old setup running** - Upgrade in parallel, then switch over

3. **Start simple** - Get one query or pipeline working before migrating everything

4. **Document as you go** - Note any data transformations you change

---

## Rollback

If something goes wrong, you haven't lost anything:

- **Core setup remains** on your machine
- **Original files** are unchanged
- **Git history** preserves everything

Simply use your previous setup while troubleshooting.

---

## Need Help?

- Check the repository README for troubleshooting
- Open an issue with specific error messages
- See [Tier Selection](tier-selection.md) if unsure about which tier
