# Dotdigital (dotdigital)

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
