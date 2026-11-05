# Elite Créatif — AI Lead Generation & Outreach SaaS

**Mohamed Abdelaty · AI & Software Engineer**

I built AI and backend workflows that connect business discovery, company enrichment,
personalized email and WhatsApp content, and campaign operations in one platform.

**[View the product walkthrough](https://www.linkedin.com/feed/update/urn:li:activity:7412500377901719552/)** · **[Read the engineering case study](docs/engineering-case-study.md)** · **[Architecture and source evidence](docs/architecture.md)** · **[LinkedIn](https://www.linkedin.com/in/mohamed-abdelaty22/)**

## The product

The platform brings a sales workflow into one application: find relevant businesses, enrich
their context, prepare tailored messages, manage campaigns, and inspect activity and results.
I built this work at **Elite Créatif**, spanning AI integration, Python services, data workflows,
and the application interfaces around them.

| Product capability | Engineering work behind it |
|---|---|
| Business discovery and import | Google Maps integration, LinkedIn/Instagram search connectors, and CSV/Excel batch workflows |
| AI-assisted personalization | Company context, configurable instructions, and Qwen-based email/WhatsApp generation |
| Tenant-aware campaign management | FastAPI authentication dependencies, tenant-scoped campaign queries, and campaign/lead APIs |
| Operational workflows | Templates, exports, sending integrations, dashboards, and activity reporting |

## Review the work in one minute

1. **[Open the original four-screen walkthrough](docs/product-walkthrough.md)** for the lead-generation, dashboard, campaign, and email-analytics interfaces.
2. **[Read the case study](docs/engineering-case-study.md)** for my implementation scope, integration decisions, and tradeoffs.
3. **[Inspect the source map](docs/architecture.md)** for links pinned to the reviewed application snapshot.

## Stack

**Python · FastAPI · SQLAlchemy · Qwen / Transformers · Gradio · pandas · SQL · Docker**

The product gallery shows the web dashboard. The reviewed public source contains a Gradio
interface and a FastAPI backend; it does not include the gallery's web frontend. The two
artifacts demonstrate different parts of the project. This repository is the engineering
showcase; the [original application snapshot](https://github.com/mohamedabdelaty74/AI-leads-Saas-gradio/tree/22e66e25c2d89fc72fe989534a9c8aa11758eaf1)
is linked for inspection.

## What the evidence establishes

The artifacts show the product workflow and implementation of source connectors,
personalization, tenant-aware campaign APIs, and sending/reporting interfaces. Source review
does not establish live tenant isolation, delivery to recipients, production capacity, or
conversion uplift. [Validation scope and next checks](docs/validation.md).

For collaboration or AI/software engineering opportunities, connect with me on
**[LinkedIn](https://www.linkedin.com/in/mohamed-abdelaty22/)**.
Engineering case study of the AI lead-generation and outreach SaaS I built at Elite Creatif: tenant-aware APIs, LLM personalization, campaign workflows, and product walkthrough.
