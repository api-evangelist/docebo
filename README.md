# Docebo

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Docebo is an AI-powered learning management system (LMS) platform providing a REST API for managing courses, users, learning plans, certifications, custom reports, gamification data, and e-commerce transactions. It serves enterprise and mid-market organizations with 250+ learners across employee, customer, and partner training use cases.

## API

- **Developer Portal**: https://developer.docebo.com
- **API Documentation**: https://developer.docebo.com/docs/api-general-information
- **Status Page**: https://status.docebo.com
- **Blog (APIs & Webhooks)**: https://www.docebo.com/learning-network/blog/integration-type/apis-and-webhooks/
- **Community (Integrations & APIs)**: https://community.docebo.com/integrations-apis-45
- **Changelog**: https://help.docebo.com/hc/en-us/articles/17920441206034-Deprecated-and-changed-API-calls

## Authentication

Docebo uses OAuth 2.0 `client_credentials` grant. Obtain a Bearer token via POST to:

```
POST https://{domain}.docebosaas.com/oauth2/token
```

Include the token as `Authorization: Bearer <token>` in all subsequent API requests. Tokens expire after 3600 seconds.

## API Services

| Service | Coverage |
|---------|----------|
| Learn | E-learning, vILT courses/sessions, external training |
| Skill | User skill management, Manager/My Team, talent integrations |
| Share | Coach & Share assets, channels, Q&A, experts, gamification |
| Manage | User management, enrollment rules, background jobs, mobile app |
| Notifications | Notification endpoints and DKIM configuration |
| E-commerce | Transactions, billing, e-commerce configuration |
| Marketplace | Content provider integrations (GO1, LinkedIn Learning, OpenSesame) |
| Report | Dashboard data, custom reports, Query Builder Reports |
| Pages | Menu and page management |
| OTJ | Observation checklists and approval workflows |
| Audittrail | Audit trail queries and logs |
| Course | E-learning/ILT courses, events, sessions, thumbnails |
| Analytics | Query builder, custom reports, dashboards |
| Audiences | Group and user management |
| Poweruser | Power user permissions and profiles |
| Learningplan | Learning plan management and enrollment |
| Certification | Awarded certification endpoints |

## Pricing

Docebo offers two main tiers — **Elevate** and **Enterprise** — both with custom (contact-sales) pricing, starting around $25,000/year. Pricing is based on active learners (MAU, YAU, or RAU model). See [plans/docebo-plans-pricing.yml](plans/docebo-plans-pricing.yml) for details.

## Rate Limits

Enterprise plans include 100 API calls/minute. Elevate plans have standard limits (not publicly specified). HTTP 429 responses indicate rate limit exceeded; exponential backoff is recommended. See [rate-limits/docebo-rate-limits.yml](rate-limits/docebo-rate-limits.yml) for details.

## FinOps

Key cost drivers include active user count, integration count, AI content credits, and API rate limit tier. See [finops/docebo-finops.yml](finops/docebo-finops.yml) for optimization strategies.
