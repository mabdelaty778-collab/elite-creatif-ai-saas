# Elite Créatif: connecting lead discovery, AI personalization, and campaign operations

**Mohamed Abdelaty · AI & Software Engineer**  
Source and product walkthrough reviewed: **5 November 2026**

**[Product walkthrough](product-walkthrough.md)** · **[Architecture and source map](architecture.md)** · **[Evidence scope](validation.md)**

## The problem I worked on

Finding prospects, understanding their businesses, preparing relevant messages, and managing
outreach usually involves several tools and repeated spreadsheet work. At Elite Créatif,
I built AI and backend workflows for a SaaS platform that brings those stages into one
application, with campaign organization and dashboards around the workflow.

The implementation connects business discovery and imported data to company enrichment,
personalized email/WhatsApp content, campaign records, and sending operations. The product
walkthrough shows lead generation, a campaign dashboard, campaign management, and email analytics.

## My engineering scope

My work spanned Python application logic, AI personalization, backend integration, and the
data handoffs between stages:

- Connected Google Maps and LinkedIn/Instagram search-based discovery paths, plus spreadsheet-based batch workflows.
- Built company-context and prompt-driven content-generation flows for email and WhatsApp.
- Implemented FastAPI account, tenant, campaign, and lead workflows, including tenant-scoped campaign access.
- Connected application interfaces to campaign creation, lead upload, exports, templates, and activity reporting.
- Integrated email/WhatsApp sending modules and Docker packaging for the application.

This describes my implementation contribution. It does not assign me an unverified team size,
management title, revenue result, or sole ownership of every product component.

## How the workflow fits together

The product accepts a search or an imported batch, collects business information, and uses
that context to prepare tailored content. Campaign and lead records organize the work;
templates, exports, sending actions, and reporting make it usable by an operator.

The reviewed source exposes both local, file-based operations and SaaS API operations.
The Gradio application can coordinate source collection, enrichment, content preparation,
and sending as staged actions. Its API client maps those UI operations onto the backend's
campaign and lead endpoints. [Detailed component map](architecture.md).

## Decisions and tradeoffs

| Decision | Why I used it | Engineering consequence |
|---|---|---|
| Company context and instructions in generation prompts | Give personalization business-specific inputs and a controllable tone | Factual accuracy, relevance, and style need review; generated text alone does not establish better response rates |
| Local Qwen initialization in the application | Bring generation into the Python workflow and control model configuration | GPU memory, startup time, model availability, and batch throughput become application concerns |
| A client adapter between collection-oriented UI flows and campaign APIs | Keep existing collection workflows usable as the backend data model changes | Field names, identifiers, empty results, and failed uploads need contract tests |
| Tenant identity resolved by backend dependencies | Bind campaign operations to the authenticated user's organization | Isolation must be verified across every read/write route and concurrent session, beyond seeing a tenant filter in source |
| Spreadsheet exports between stages | Let operators inspect and reuse intermediate work | Local files and backend records can diverge; each handoff needs a clear receipt and status |
| Separate email and WhatsApp sender modules | Support two channels with different payloads and error behavior | API/SMTP acceptance, recipient delivery, replies, and sales are separate events |

## A concrete integration challenge: changing the API model

The application client still offers collection-oriented operations such as creating a lead
collection and adding leads to it. The reviewed backend represents this work through campaigns
and campaign-associated leads. I connected the two through an adapter that maps source/search
parameters into campaign creation and normalizes collected rows into bulk lead uploads.

That boundary matters because creating a campaign is not the same as collecting leads or
persisting the resulting batch. The UI includes branches for an empty result or pending/failed
upload, and the client retains a local spreadsheet path when upload fails. The next verification
step is to assert those outcomes independently and reconcile the local artifact with the
backend's committed lead count.

**[Client mapping](https://github.com/mohamedabdelaty74/AI-leads-Saas-gradio/blob/22e66e25c2d89fc72fe989534a9c8aa11758eaf1/saas_api_client_minimal.py#L79)** · **[Campaign API](https://github.com/mohamedabdelaty74/AI-leads-Saas-gradio/blob/22e66e25c2d89fc72fe989534a9c8aa11758eaf1/backend/main.py#L338)**

## What I can demonstrate

The source and product gallery establish substantial application scope: discovery,
personalization, tenant-aware campaign APIs, and operational interfaces. They show the software
around an AI model, including authentication, data modeling, integration contracts, and
operator workflows.

The gallery is a product walkthrough, not a recorded end-to-end test or a verified analytics
dataset. The public source snapshot also needs a completeness and runtime pass before a
reviewer can reproduce the full application: imported database/model modules are absent from
the visible tree, and generation-module wiring and per-session UI state need verification.
I keep those limits separate from the implementation demonstrated by the artifacts.

I have not published a verified conversion improvement, delivery rate, user count, throughput
gain, or production uptime result for this case. Those figures require campaign records,
delivery receipts, operating conditions, and a stated comparison method.

## What I would validate next

I would restore a complete, isolated setup and test tenant access with two organizations,
concurrent sessions, and every campaign/lead endpoint. I would then trace a synthetic batch
from import through generation to committed rows, retries, and channel-specific delivery
receipts. Model quality and performance need their own evaluation: factual consistency,
review effort, cold/warm timings, cost, and failure recovery.

The public artifacts make the engineering work inspectable today. The validation plan makes
clear what additional evidence is needed before presenting the implementation as a measured
production result.
