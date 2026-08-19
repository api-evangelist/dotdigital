---
name: Send transactional email through Dotdigital
description: Send single and batched transactional emails, use a triggered campaign as the template, and read send statistics.
api: openapi/dotdigital-transactional-email-openapi.yml
operations: [send-transactional-email, send-batch-transactional-email, send-transactional-email-using-a-triggered-campaign, send-batch-transactional-email-using-a-triggered-campaign, get-transactional-email-statistics]
generated: '2026-08-13'
method: generated
source: openapi/dotdigital-transactional-email-openapi.yml + conventions/dotdigital-conventions.yml
---

# Send transactional email through Dotdigital

Transactional email lives on the **v2** framework. Paths are under `/v2/email` on the account's
regional host (`https://{region}-api.dotdigital.com`). Authenticate with HTTP Basic using API
user credentials.

## Choose the shape of the send

| Need | Operation | Path |
|---|---|---|
| One message, content supplied inline | `send-transactional-email` | `POST /v2/email` |
| Many messages in one call | `send-batch-transactional-email` | `POST /v2/email/batch` |
| One message rendered from a triggered campaign | `send-transactional-email-using-a-triggered-campaign` | `POST /v2/email/triggered-campaign` |
| Many messages from a triggered campaign | `send-batch-transactional-email-using-a-triggered-campaign` | `POST /v2/email/triggered-campaign/batch` |

Use the triggered-campaign variants when marketing owns the template in EasyEditor and you only
supply the personalisation values. Use the plain variants when your system owns the content.

## Rate limiting

Message-sending calls sit in the **unlimited** tier of the tiered rate-limit scheme and are also
listed as exempt under the deprecated flat-rate scheme. That means a send will not normally be
throttled by the same budget your data calls consume — but the exemption is stated per operation
in the reference docs, so do not generalise it to anything that is not a send.

## Retry safety — read this before you build a retry

Dotdigital publishes **no idempotency key** for sends. A retried `POST /v2/email` after a
timeout can deliver a second message. Because a client timeout is only advisory at 121 seconds,
build your queue so that:

- a send is attempted once, and
- on an ambiguous failure (timeout, 5xx, connection reset) you record it as *unknown*, and
- you reconcile using `get-transactional-email-statistics`
  (`GET /v2/email/stats/since-date/{date}`) or the delivery webhooks rather than by re-sending.

## Attach correlation data

Where the API accepts a `metadata` facility, populate it with your own message id. Dotdigital
echoes those values back on the resulting webhook events, which is the only reliable way to
reconcile a receipt to a send. See `asyncapi/dotdigital-webhooks.yml`.

## Errors

v2 returns an `ERROR_*` token in the response body. The ones you will actually hit on this path:

- `ERROR_INVALID_EMAIL` — malformed recipient address
- `ERROR_EMAIL_BANNED` — address is on a ban list
- `ERROR_CONTACT_SUPPRESSED` — recipient is suppressed on the account
- `ERROR_CAMPAIGN_NOT_FOUND` / `ERROR_CAMPAIGN_SENDNOTPERMITTED` — triggered-campaign variants
- `ERROR_INVALID_PERSONALISATION_VALUES` — the values do not match the template's placeholders
- `ERROR_SEND_LIMITEXCEEDED` — account send allowance exhausted

The full registry is in `errors/dotdigital-error-codes.yml`. `ERROR_CONTACT_SUPPRESSED` and
`ERROR_EMAIL_BANNED` are terminal — never retry them.

## Statistics

`GET /v2/email/stats/since-date/{date}` → `get-transactional-email-statistics`. The date is a
UTC ISO 8601 value; align it to the API clock with `ApiAccount_GetServerTime`
(`GET /v2/server-time`) rather than to your own host's clock.
