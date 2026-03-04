# Enterprise Guide

For organizations requiring dedicated infrastructure, custom compliance, or data center scale.

## When to Consider Enterprise

| Requirement | Standard Tiers | Enterprise |
|-------------|----------------|------------|
| Data volume | Up to ~100GB | Unlimited |
| Users | Individual/small team | Organization-wide |
| Infrastructure | Local machine/Docker | Dedicated servers |
| Compliance | Standard | Custom (SOC 2, HIPAA, etc.) |
| Support | Community/docs | Dedicated |

---

## What Enterprise Includes

### Infrastructure Options

- **Dedicated cloud deployment** - Your own AWS/Azure/GCP resources
- **On-premises installation** - Within your data center
- **Hybrid setup** - Mix of cloud and on-prem components

### Security & Compliance

- Custom security configuration
- Compliance documentation for audits
- Data residency controls
- SSO/SAML integration options
- Network isolation options

### Support

- Dedicated technical contact
- Priority issue resolution
- Architecture consultation
- Training sessions

---

## Common Enterprise Use Cases

### Multi-Team Data Platform

**Scenario**: Multiple consulting teams need shared data infrastructure

**Solution**:
- Central PostgreSQL cluster
- Team-specific Dagster workspaces
- Shared data catalog
- Role-based access control

### Regulated Industry Analytics

**Scenario**: Financial services firm needs compliant analytics

**Solution**:
- Air-gapped deployment option
- Audit logging for all data access
- Encryption at rest and in transit
- Compliance documentation package

### High-Volume Processing

**Scenario**: Processing TB-scale datasets daily

**Solution**:
- Distributed Dagster workers
- Scalable PostgreSQL (or Snowflake/BigQuery)
- Resource scheduling and optimization
- Monitoring and alerting

---

## Technology Partners

For Enterprise deployments, we work with:

| Need | Partner Options |
|------|-----------------|
| Cloud infrastructure | AWS, Azure, GCP |
| Data warehousing | Snowflake, Databricks, BigQuery |
| Orchestration | Dagster Cloud, Prefect Cloud |
| BI/Dashboards | Evidence Cloud, Metabase, Looker |

We help you choose the right combination for your requirements.

---

## Engagement Process

### 1. Discovery Call

- Understand your requirements
- Assess current data landscape
- Identify compliance constraints
- Define success criteria

### 2. Architecture Proposal

- Recommended technology stack
- Infrastructure design
- Security architecture
- Cost estimation

### 3. Pilot Implementation

- Small-scale proof of concept
- Validate approach with real data
- Refine based on feedback

### 4. Full Deployment

- Production infrastructure
- Team onboarding
- Documentation and training
- Ongoing support setup

---

## Pricing

Enterprise pricing depends on:

- Deployment model (cloud/on-prem/hybrid)
- Data volume and processing requirements
- Number of users
- Compliance requirements
- Support level

Contact us for a custom quote.

---

## Getting Started

### Ready to Explore Enterprise?

1. **Try the standard tiers first** - Most teams can start with Core or Analytics
2. **Document your requirements** - What specific needs drive Enterprise consideration?
3. **Contact us** - We'll schedule a discovery call

### Contact Information

**Email**: enterprise@forgevista.ai

**What to include**:
- Your organization name
- Brief description of use case
- Approximate data volume
- Key requirements (compliance, users, timeline)

---

## FAQ

### Do we have to start with Enterprise?

No. Most organizations start with Core or Platform. Enterprise is for when you outgrow self-managed infrastructure or have specific compliance needs.

### Can we migrate from Platform to Enterprise?

Yes. The technology stack is the same - Enterprise primarily adds managed infrastructure and support.

### What's the minimum commitment?

We offer flexible engagement models. Contact us to discuss options that fit your organization.

### Do you offer training?

Yes. Enterprise includes onboarding and training. Additional workshops available on request.
