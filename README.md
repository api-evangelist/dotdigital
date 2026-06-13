# Dotdigital (dotdigital)

Dotdigital is a marketing automation platform with a REST API for managing contacts, email campaigns, SMS, automation programs, pages, and accessing engagement data. The platform provides v2 and v3 REST API frameworks alongside a CPaaS API for omnichannel messaging including email, SMS, MMS, WhatsApp, push notifications, and Facebook Messenger. Trusted by over 4,000 brands globally, Dotdigital enables marketers to build hyper-personalized, cross-channel customer experiences at scale.

APIs.json: https://raw.githubusercontent.com/api-evangelist/dotdigital/refs/heads/main/apis.yml

Naftiko: https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=dotdigital-api-evangelist&utm_content=repo

## Tags

- Marketing Automation
- Email Marketing
- SMS
- WhatsApp
- Contacts
- Campaigns
- Push Notifications
- Transactional Email
- Engagement
- Automation

## APIs

- **Dotdigital v2 API** - The legacy v2 REST API providing access to contacts, campaigns, SMS, programs, pages, forms, data fields, and engagement reporting. Base URL: `https://r1-api.dotdigital.com/v2`
- **Dotdigital v3 API** - The newer v3 REST API framework with unified contacts, improved REST practices, omnichannel communications, and advanced marketing automation features. Base URL: `https://r1-api.dotdigital.com/v3`
- **Dotdigital CPaaS API** - Communications Platform as a Service API for omnichannel messaging including SMS, MMS, WhatsApp, and push notifications. Docs: https://docs.cpaas.dotdigital.com/

## Plans / Rate Limits / FinOps

- **Plans**: [plans/dotdigital-plans-pricing.yml](plans/dotdigital-plans-pricing.yml) — Dotdigital uses a fully custom quote-based pricing model. Costs are driven by contact database size, email/SMS/WhatsApp send volume, and channels enabled. No public tier pricing is available; contact sales for a personalized quote.
- **Rate Limits**: [rate-limits/dotdigital-rate-limits.yml](rate-limits/dotdigital-rate-limits.yml) — Tiered per-minute rate limiting with four tiers (Low, Medium, High, Unlimited). Actual numeric limits are account-package dependent. Throttle responses return HTTP 429. Rate limit state is exposed via `X-RateLimit-*` headers.
- **FinOps**: [finops/dotdigital-finops.yml](finops/dotdigital-finops.yml) — Primary cost drivers are contact count and send volume. Use rate limit headers for API consumption visibility. Prune inactive contacts and use demo/trial accounts for development to reduce costs.

## Timestamps

- created: 2026-06-13
- modified: 2026-06-13

## Common

| Type | URL |
|---|---|
| Website | https://dotdigital.com |
| Documentation | https://developer.dotdigital.com/ |
| GitHub Org | https://github.com/dotmailer |
| LinkedIn | https://www.linkedin.com/company/dotdigital |
| Blog | https://dotdigital.com/blog/ |
| Pricing | https://dotdigital.com/pricing/ |
| Status Page | https://dotdigitalstatus.com |
| X | https://x.com/dotdigital |

## Maintainers

- Kin Lane (kin@apievangelist.com)
