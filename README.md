# Dotdigital

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Dotdigital is a UK-headquartered customer engagement platform (LSE: DOTD) whose Marketing product combines email, SMS, MMS, WhatsApp, push, app messaging, chat and web personalization behind one contact database. Its API estate is unusually large and unusually well published: 42 OpenAPI descriptions are served from a public catalog at developer.dotdigital.com/openapi and enumerated in an RFC 9727 api-catalog linkset, spanning contacts, lists, segments, preferences and consent, email and SMS campaigns, transactional email, programs, pages and forms, insight data, ecommerce, product recommendations, scoring, and the whole CPaaS omnichannel messaging stack. Two frameworks run side by side — legacy v2 at /v2/* and the current v3 services at /<service>/v3/* built around unified contacts — and most integrations need both. Everything authenticates with HTTP Basic API-user credentials against a mandatory regional host (r1 Europe, r2 North America, r3 Asia Pacific). Dotdigital also runs a remote MCP server over its developer hub and publishes webhooks, a durable Events in/out API and a Data Firehose for streaming engagement data to cloud storage.

**Areas:** Marketing Automation · Email Marketing · SMS · MMS · WhatsApp · Contacts · Campaigns · Push Notifications · Transactional Email · Engagement · Automation · CPaaS

## Dotdigital on APIs.io

Everything profiled for Dotdigital is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/dotdigital/](https://apis.io/providers/dotdigital/)** — or go straight to one of the APIs or properties below.

### APIs (58)

- [Dotdigital Marketing Developer Hub MCP Server](https://apis.io/apis/dotdigital/dotdigital-marketing-developer-hub-mcp-server/) — A remote MCP server that exposes the Dotdigital OpenAPI corpus and the developer-hub documentation to AI coding tools. Seven read-only tools (list-specs,…
- [Dotdigital Accounts and Utilities API](https://apis.io/apis/dotdigital/dotdigital-accounts-and-utilities-api/) — The Accounts and Utilities API from Dotdigital — 3 operation(s) for accounts and utilities.
- [Dotdigital API Account API](https://apis.io/apis/dotdigital/dotdigital-apiaccount-api/) — The ApiAccount API from Dotdigital — 8 operation(s) for apiaccount.
- [Dotdigital API Address Book API](https://apis.io/apis/dotdigital/dotdigital-apiaddressbook-api/) — The ApiAddressBook API from Dotdigital — 6 operation(s) for apiaddressbook.
- [Dotdigital API Campaign API](https://apis.io/apis/dotdigital/dotdigital-apicampaign-api/) — The ApiCampaign API from Dotdigital — 11 operation(s) for apicampaign.
- [Dotdigital API Campaign From Address API](https://apis.io/apis/dotdigital/dotdigital-apicampaignfromaddress-api/) — The ApiCampaignFromAddress API from Dotdigital — 1 operation(s) for apicampaignfromaddress.
- [Dotdigital API Campaign Reporting API](https://apis.io/apis/dotdigital/dotdigital-apicampaignreporting-api/) — The ApiCampaignReporting API from Dotdigital — 24 operation(s) for apicampaignreporting.
- [Dotdigital API Campaign Send API](https://apis.io/apis/dotdigital/dotdigital-apicampaignsend-api/) — The ApiCampaignSend API from Dotdigital — 3 operation(s) for apicampaignsend.
- [Dotdigital API Contact API](https://apis.io/apis/dotdigital/dotdigital-apicontact-api/) — The ApiContact API from Dotdigital — 43 operation(s) for apicontact.
- [Dotdigital API Contact Import API](https://apis.io/apis/dotdigital/dotdigital-apicontactimport-api/) — The ApiContactImport API from Dotdigital — 8 operation(s) for apicontactimport.
- [Dotdigital API Data Field API](https://apis.io/apis/dotdigital/dotdigital-apidatafield-api/) — The ApiDataField API from Dotdigital — 2 operation(s) for apidatafield.
- [Dotdigital API Ecommerce API](https://apis.io/apis/dotdigital/dotdigital-apiecommerce-api/) — The ApiEcommerce API from Dotdigital — 4 operation(s) for apiecommerce.
- [Dotdigital API Preference API](https://apis.io/apis/dotdigital/dotdigital-apipreference-api/) — The ApiPreference API from Dotdigital — 14 operation(s) for apipreference.
- [Dotdigital API Product Recommendations API](https://apis.io/apis/dotdigital/dotdigital-apiproductrecommendations-api/) — The ApiProductRecommendations API from Dotdigital — 1 operation(s) for apiproductrecommendations.
- [Dotdigital API Program API](https://apis.io/apis/dotdigital/dotdigital-apiprogram-api/) — The ApiProgram API from Dotdigital — 6 operation(s) for apiprogram.
- [Dotdigital API Segment API](https://apis.io/apis/dotdigital/dotdigital-apisegment-api/) — The ApiSegment API from Dotdigital — 2 operation(s) for apisegment.
- [Dotdigital API Sms API](https://apis.io/apis/dotdigital/dotdigital-apisms-api/) — The ApiSms API from Dotdigital — 4 operation(s) for apisms.
- [Dotdigital Apispaces API](https://apis.io/apis/dotdigital/dotdigital-apispaces-api/) — The Apispaces API from Dotdigital — 2 operation(s) for apispaces.
- [Dotdigital API Survey API](https://apis.io/apis/dotdigital/dotdigital-apisurvey-api/) — The ApiSurvey API from Dotdigital — 6 operation(s) for apisurvey.
- [Dotdigital API Template API](https://apis.io/apis/dotdigital/dotdigital-apitemplate-api/) — The ApiTemplate API from Dotdigital — 2 operation(s) for apitemplate.
- [Dotdigital API Transactional Email API](https://apis.io/apis/dotdigital/dotdigital-apitransactionalemail-api/) — The ApiTransactionalEmail API from Dotdigital — 6 operation(s) for apitransactionalemail.
- [Dotdigital App Messaging API](https://apis.io/apis/dotdigital/dotdigital-app-messaging-api/) — The App Messaging API from Dotdigital — 2 operation(s) for app messaging.
- [Dotdigital Bulk validation API](https://apis.io/apis/dotdigital/dotdigital-bulk-validation-api/) — The Bulk validation API from Dotdigital — 3 operation(s) for bulk validation.
- [Dotdigital Channels API](https://apis.io/apis/dotdigital/dotdigital-channels-api/) — The Channels API from Dotdigital — 1 operation(s) for channels.
- [Dotdigital Chat API](https://apis.io/apis/dotdigital/dotdigital-chat-api/) — The Chat API from Dotdigital — 2 operation(s) for chat.
- [Dotdigital Contacts API](https://apis.io/apis/dotdigital/dotdigital-contacts-api/) — The Contacts API from Dotdigital — 6 operation(s) for contacts.
- [Dotdigital Cpaas API](https://apis.io/apis/dotdigital/dotdigital-cpaas-api/) — The Cpaas API from Dotdigital — 41 operation(s) for cpaas.
- [Dotdigital Custom identifiers API](https://apis.io/apis/dotdigital/dotdigital-custom-identifiers-api/) — The Custom identifiers API from Dotdigital — 2 operation(s) for custom identifiers.
- [Dotdigital Data Firehose API](https://apis.io/apis/dotdigital/dotdigital-data-firehose-api/) — The Data Firehose API from Dotdigital — 3 operation(s) for data firehose.
- [Dotdigital Documents API](https://apis.io/apis/dotdigital/dotdigital-documents-api/) — The Documents API from Dotdigital — 3 operation(s) for documents.
- [Dotdigital Email Campaigns API](https://apis.io/apis/dotdigital/dotdigital-email-campaigns-api/) — The Email Campaigns API from Dotdigital — 39 operation(s) for email campaigns.
- [Dotdigital Email contacts API](https://apis.io/apis/dotdigital/dotdigital-email-contacts-api/) — The Email contacts API from Dotdigital — 18 operation(s) for email contacts.
- [Dotdigital Export events API](https://apis.io/apis/dotdigital/dotdigital-export-events-api/) — The Export events API from Dotdigital — 1 operation(s) for export events.
- [Dotdigital Images API](https://apis.io/apis/dotdigital/dotdigital-images-api/) — The Images API from Dotdigital — 3 operation(s) for images.
- [Dotdigital Import events API](https://apis.io/apis/dotdigital/dotdigital-import-events-api/) — The Import events API from Dotdigital — 1 operation(s) for import events.
- [Dotdigital Insight and transactional data API](https://apis.io/apis/dotdigital/dotdigital-insight-and-transactional-data-api/) — The Insight and transactional data API from Dotdigital — 9 operation(s) for insight and transactional data.
- [Dotdigital Insight Data API](https://apis.io/apis/dotdigital/dotdigital-insightdata-api/) — The InsightData API from Dotdigital — 17 operation(s) for insightdata.
- [Dotdigital Large objects API](https://apis.io/apis/dotdigital/dotdigital-large-objects-api/) — The Large objects API from Dotdigital — 1 operation(s) for large objects.
- [Dotdigital Lists / Address books API](https://apis.io/apis/dotdigital/dotdigital-lists-address-books-api/) — The Lists / Address books API from Dotdigital — 14 operation(s) for lists / address books.
- [Dotdigital Lists / Address books - Deprecated API](https://apis.io/apis/dotdigital/dotdigital-lists-address-books-deprecated-api/) — The Lists / Address books - Deprecated API from Dotdigital — 3 operation(s) for lists / address books - deprecated.
- [Dotdigital Marketing Emails API](https://apis.io/apis/dotdigital/dotdigital-marketing-emails-api/) — The Marketing Emails API from Dotdigital — 2 operation(s) for marketing emails.
- [Dotdigital Messaging API](https://apis.io/apis/dotdigital/dotdigital-messaging-api/) — The Messaging API from Dotdigital — 2 operation(s) for messaging.
- [Dotdigital Omnichannel API](https://apis.io/apis/dotdigital/dotdigital-omnichannel-api-api/) — The Omnichannel API API from Dotdigital — 6 operation(s) for omnichannel api.
- [Dotdigital Preferences and subscriptions API](https://apis.io/apis/dotdigital/dotdigital-preferences-and-subscriptions-api/) — The Preferences and subscriptions API from Dotdigital — 13 operation(s) for preferences and subscriptions.
- [Dotdigital Programs API](https://apis.io/apis/dotdigital/dotdigital-programs-api/) — The Programs API from Dotdigital — 7 operation(s) for programs.
- [Dotdigital Scoring API](https://apis.io/apis/dotdigital/dotdigital-scoring-api/) — The Scoring API from Dotdigital — 4 operation(s) for scoring.
- [Dotdigital Single number API](https://apis.io/apis/dotdigital/dotdigital-single-number-api/) — The Single number API from Dotdigital — 1 operation(s) for single number.
- [Dotdigital SMS API](https://apis.io/apis/dotdigital/dotdigital-sms-api/) — The SMS API from Dotdigital — 7 operation(s) for sms.
- [Dotdigital SMS campaigns API](https://apis.io/apis/dotdigital/dotdigital-sms-campaigns-api/) — The SMS campaigns API from Dotdigital — 4 operation(s) for sms campaigns.
- [Dotdigital Subscriptions API](https://apis.io/apis/dotdigital/dotdigital-subscriptions-api/) — The Subscriptions API from Dotdigital — 2 operation(s) for subscriptions.
- [Dotdigital Transactional email API](https://apis.io/apis/dotdigital/dotdigital-transactional-email-api/) — The Transactional email API from Dotdigital — 5 operation(s) for transactional email.
- [Dotdigital Webhooks API](https://apis.io/apis/dotdigital/dotdigital-webhooks-api-api/) — The Webhooks API API from Dotdigital — 4 operation(s) for webhooks api.
- [Dotdigital WhatsApp configurations API](https://apis.io/apis/dotdigital/dotdigital-whatsapp-configurations-api/) — The WhatsApp configurations API from Dotdigital — 1 operation(s) for whatsapp configurations.
- [Dotdigital WhatsApp numbers API](https://apis.io/apis/dotdigital/dotdigital-whatsapp-numbers-api/) — The WhatsApp numbers API from Dotdigital — 2 operation(s) for whatsapp numbers.
- [Dotdigital WhatsApp templates API](https://apis.io/apis/dotdigital/dotdigital-whatsapp-templates-api/) — The WhatsApp templates API from Dotdigital — 2 operation(s) for whatsapp templates.
- [Dotdigital API / Document API](https://apis.io/apis/dotdigital/dotdigital-api-document-api/) — The API / Document API from Dotdigital — 5 operation(s) for api / document.
- [Dotdigital API Image API](https://apis.io/apis/dotdigital/dotdigital-api-image-api/) — The API Image API from Dotdigital — 3 operation(s) for api image.
- [Dotdigital Whats App API](https://apis.io/apis/dotdigital/dotdigital-whats-app-api/) — The Whats App API from Dotdigital — 2 operation(s) for whats app.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Dotdigital Webhooks](https://apis.io/asyncapis/dotdigital/dotdigital-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [dotdigital-api](https://apis.io/servers/dotdigital/dotdigital-api/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Dotdigital Agentic Access](https://apis.io/agentic-access/dotdigital/dotdigital-agentic-access/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Dotdigital Context](https://apis.io/jsonld/dotdigital/dotdigital-context/)

#### Collections (43)

Postman and Open Collection request collections.

- [Accounts and Utilities](https://apis.io/collections/dotdigital/open-dotdigital-accounts-and-utilities/)
- [Analytics API](https://apis.io/collections/dotdigital/open-dotdigital-analytics/)
- [Campaign Templates](https://apis.io/collections/dotdigital/open-dotdigital-campaign-templates/)
- [Chat API](https://apis.io/collections/dotdigital/open-dotdigital-chat/)
- [Chat Config API](https://apis.io/collections/dotdigital/open-dotdigital-chat-config/)
- [Chat Message API](https://apis.io/collections/dotdigital/open-dotdigital-chat-message/)
- [Chat Presence API](https://apis.io/collections/dotdigital/open-dotdigital-chat-presence/)
- [Dotdigital Configuration Service](https://apis.io/collections/dotdigital/open-dotdigital-configuration-service/)
- [Contact data fields](https://apis.io/collections/dotdigital/open-dotdigital-contact-data-fields/)
- [Contacts](https://apis.io/collections/dotdigital/open-dotdigital-contacts/)
- [Content API](https://apis.io/collections/dotdigital/open-dotdigital-content/)
- [Conversation API](https://apis.io/collections/dotdigital/open-dotdigital-conversation/)
- [Conversation Message API](https://apis.io/collections/dotdigital/open-dotdigital-conversation-message/)
- [CPaaS API](https://apis.io/collections/dotdigital/open-dotdigital-cpaas/)
- [Data Firehose](https://apis.io/collections/dotdigital/open-dotdigital-data-firehose/)
- [Documents](https://apis.io/collections/dotdigital/open-dotdigital-documents/)
- [Ecommerce](https://apis.io/collections/dotdigital/open-dotdigital-ecommerce/)
- [Email campaigns](https://apis.io/collections/dotdigital/open-dotdigital-email-campaigns/)
- [Email contacts](https://apis.io/collections/dotdigital/open-dotdigital-email-contacts/)
- [Events](https://apis.io/collections/dotdigital/open-dotdigital-events/)
- [Images](https://apis.io/collections/dotdigital/open-dotdigital-images/)
- [Insight and transactional data](https://apis.io/collections/dotdigital/open-dotdigital-insight-and-transactional-data/)
- [Insight data service](https://apis.io/collections/dotdigital/open-dotdigital-insight-data-service/)
- [Lists / Address books](https://apis.io/collections/dotdigital/open-dotdigital-lists-address-books/)
- [Marketing Email API](https://apis.io/collections/dotdigital/open-dotdigital-marketing-email/)
- …and 18 more published on APIs.io

#### Overlays (43)

OpenAPI overlays, including conversational phrasing for each operation.

- [Dotdigital Accounts And Utilities Overlay](https://apis.io/overlays/dotdigital/dotdigital-accounts-and-utilities-overlay/)
- [Dotdigital Analytics Overlay](https://apis.io/overlays/dotdigital/dotdigital-analytics-overlay/)
- [Dotdigital Campaign Templates Overlay](https://apis.io/overlays/dotdigital/dotdigital-campaign-templates-overlay/)
- [Dotdigital Chat Config Overlay](https://apis.io/overlays/dotdigital/dotdigital-chat-config-overlay/)
- [Dotdigital Chat Message Overlay](https://apis.io/overlays/dotdigital/dotdigital-chat-message-overlay/)
- [Dotdigital Chat Overlay](https://apis.io/overlays/dotdigital/dotdigital-chat-overlay/)
- [Dotdigital Chat Presence Overlay](https://apis.io/overlays/dotdigital/dotdigital-chat-presence-overlay/)
- [Dotdigital Configuration Service Overlay](https://apis.io/overlays/dotdigital/dotdigital-configuration-service-overlay/)
- [Dotdigital Contact Data Fields Overlay](https://apis.io/overlays/dotdigital/dotdigital-contact-data-fields-overlay/)
- [Dotdigital Contacts Overlay](https://apis.io/overlays/dotdigital/dotdigital-contacts-overlay/)
- [Dotdigital Content Overlay](https://apis.io/overlays/dotdigital/dotdigital-content-overlay/)
- [Dotdigital Conversation Message Overlay](https://apis.io/overlays/dotdigital/dotdigital-conversation-message-overlay/)
- [Dotdigital Conversation Overlay](https://apis.io/overlays/dotdigital/dotdigital-conversation-overlay/)
- [Dotdigital Cpaas Overlay](https://apis.io/overlays/dotdigital/dotdigital-cpaas-overlay/)
- [Dotdigital Data Firehose Overlay](https://apis.io/overlays/dotdigital/dotdigital-data-firehose-overlay/)
- [Dotdigital Documents Overlay](https://apis.io/overlays/dotdigital/dotdigital-documents-overlay/)
- [Dotdigital Ecommerce Overlay](https://apis.io/overlays/dotdigital/dotdigital-ecommerce-overlay/)
- [Dotdigital Email Campaigns Overlay](https://apis.io/overlays/dotdigital/dotdigital-email-campaigns-overlay/)
- [Dotdigital Email Contacts Overlay](https://apis.io/overlays/dotdigital/dotdigital-email-contacts-overlay/)
- [Dotdigital Events Overlay](https://apis.io/overlays/dotdigital/dotdigital-events-overlay/)
- [Dotdigital Images Overlay](https://apis.io/overlays/dotdigital/dotdigital-images-overlay/)
- [Dotdigital Insight And Transactional Data Overlay](https://apis.io/overlays/dotdigital/dotdigital-insight-and-transactional-data-overlay/)
- [Dotdigital Insight Data Service Overlay](https://apis.io/overlays/dotdigital/dotdigital-insight-data-service-overlay/)
- [Dotdigital Lists Address Books Overlay](https://apis.io/overlays/dotdigital/dotdigital-lists-address-books-overlay/)
- [Dotdigital Marketing Email Overlay](https://apis.io/overlays/dotdigital/dotdigital-marketing-email-overlay/)
- …and 18 more published on APIs.io

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Dotdigital Authentication](https://apis.io/security/dotdigital/dotdigital-authentication/)
- [Dotdigital Domain Security](https://apis.io/security/dotdigital/dotdigital-domain-security/)
- [Dotdigital Trust Center](https://apis.io/security/dotdigital/dotdigital-trust-center/)
- [Dotdigital Vulnerability Disclosure](https://apis.io/security/dotdigital/dotdigital-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Dotdigital Plans Pricing](https://apis.io/plans/dotdigital/dotdigital-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Dotdigital Rate Limits](https://apis.io/rate-limits/dotdigital/dotdigital-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Dotdigital Finops](https://apis.io/finops/dotdigital/dotdigital-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://dotdigital.com)
- [Documentation](https://marketing.developer.dotdigital.com/docs/getting-started-with-the-api)
- [Getting started](https://marketing.developer.dotdigital.com/docs/getting-started-with-the-api)
- [API reference](https://marketing.developer.dotdigital.com/reference/)
- [Pricing](https://dotdigital.com/get-started/)
- [Support](https://support.dotdigital.com/en/)
- [Blog](https://dotdigital.com/blog/)
- [Security](https://dotdigital.com/trust-center/)
- [Compliance](https://dotdigital.com/trust-center/)
- [Terms of service](https://dotdigital.com/terms/)
- [Privacy policy](https://dotdigital.com/privacy-policy/)
- [GitHub](https://github.com/dotmailer)
- [Status](https://dotdigitalstatus.com)

## API Evangelist rating

**Kin Score 60.4** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 80.0 |
| Contract quality | 63.7 |
| Contract governance | 4.5 |
| Operational transparency | 52.6 |
| Developer ergonomics | 47.0 |
| Access clarity | 75.0 |

**Agent readiness 38.9** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | platform (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | yes |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | mostly |

**Regulatory alignment 34.2** — Telecommunications

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/dotdigital/](https://apis.io/providers/dotdigital/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Dotdigital: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/dotdigital/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
