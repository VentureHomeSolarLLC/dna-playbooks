# COMPANY.md — Venture Home Company Context

<!-- FORGE:MANAGED:company-context v2.0 -->

## Venture Home Solar

- **Full name:** Venture Home Solar, LLC (dba "Venture Home")
- **Previously:** Venture Solar (rebranded February 2026, 11th year in business)
- **Founded:** 2015
- **Co-Founder & CEO:** Alex Yackery
- **HQ:** Stamford, CT
- **Coverage:** Northeast and Mid-Atlantic (11+ states)
- **Customers served:** 15,000+
- **Mission:** Home electrification partner for life. Helping customers generate and store power, gain control over their energy, reduce costs, shrink their footprint, and live better.

### What We Do

Solar is foundational but we are not just a solar company. We are a home electrification company. Our services include solar installation (residential), battery storage (Tesla Powerwall, others), EV charging with vehicle-to-home (Tesla Powershare), smart electrical panels (SPAN) and smart breakers (Eaton), system expansions for existing customers, and ongoing monitoring and support.

### How We Work

Our business runs from lead to lifetime relationship: sales appointments, contract signing, permitting (across 11 states), installation, inspection, interconnection, and ongoing service. We currently use Salesforce with Field Service Lightning, Five9 for phone, and Customer.io for marketing automation. We are building **Canopy**, our own AI-native CRM to replace Salesforce, with a property-centric architecture on PostgreSQL + BigQuery on Google Cloud.

### AI Infrastructure

Venture Home runs local AI infrastructure: Mac Studios with M3 Ultra processors for heavy inference, Mac Minis for agent execution, connected via 10GbE networking with LiteLLM as a unified routing proxy. Three model tiers: fast (small local models), medium (MoE models), heavy (large local models). Cloud APIs (Anthropic, OpenAI) are available as fallback. The goal is maximum capability at minimal ongoing cost.

### The AI Workforce

We are building an AI workforce managed through **Forge** (forge.venturehome.com), a control plane built on top of OpenClaw. Forge manages agent DNA (the 9 standard markdown files), a centralized skills library, version-managed updates via zero-token bash sync, and full project management. Agents share organizational DNA through Forge's managed block system while maintaining individual personalities, memories, and specializations.

<!-- /FORGE:MANAGED:company-context -->
