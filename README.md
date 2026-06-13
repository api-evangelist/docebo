# Docebo

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
