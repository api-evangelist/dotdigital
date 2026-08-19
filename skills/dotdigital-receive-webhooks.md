---
name: Receive and verify Dotdigital webhooks
description: Register a CPaaS webhook, discover the available event types, verify the HMAC signature correctly, and survive the retry schedule.
api: openapi/dotdigital-webhook-openapi.yml
operations: ['GET /cpaas/webhooks', 'POST /cpaas/webhooks', 'GET /cpaas/webhooks/availableevents', 'GET /cpaas/webhooks/availabletemplates', 'GET /cpaas/webhooks/{webhookId}', 'PUT /cpaas/webhooks/{webhookId}', 'DELETE /cpaas/webhooks/{webhookId}']
generated: '2026-08-13'
method: generated
source: openapi/dotdigital-webhook-openapi.yml + https://marketing.developer.dotdigital.com/reference/webhooks
---

# Receive and verify Dotdigital webhooks

> The Webhook API spec declares no `operationId`s, so operations here are named by method and
> path exactly as they appear in `openapi/dotdigital-webhook-openapi.yml`.

Base: `https://{region}-api.dotdigital.com/cpaas/webhooks`. HTTP Basic with API user credentials.

## 1. Discover the event types from the API, not from the docs

`GET /cpaas/webhooks/availableevents` returns the event types available to *this* account, and
`GET /cpaas/webhooks/availabletemplates` returns their payload templates. There is no public
enumeration of the full list — call these first and register only what you will process. The
documented families are `message.*`, `interaction.click`, `profile.*`, `chat.*`, and the app
messaging conversation/message/session families
(see `asyncapi/dotdigital-webhooks.yml`).

## 2. Register the webhook

`POST /cpaas/webhooks` with your HTTPS URL, the event selection, a secret, and the batch
settings. Manage with `GET /cpaas/webhooks`, `GET/PUT/DELETE /cpaas/webhooks/{webhookId}`.

**Choose batching.** Batch delivery is strongly recommended by Dotdigital and is what your
receiver should be built for:

- `maximum events per batch`: 1–500
- `batch timeout`: 1–60 seconds
- A batch ships when it is full **or** the timeout since the last batch elapses.
- A batch is simply a JSON **array** of the same envelopes. Handle both an object and an array
  if you ever switch modes.

**Choose a strong secret**: at least 16 characters, 36 or more recommended.

## 3. Verify the signature — the three traps

The signature arrives in the header **`X-Comapi-Signature`**. The `Comapi` prefix is a legacy of
the acquired platform; searching for `X-Dotdigital-Signature` finds nothing.

1. Compute **HMAC-SHA1** (not SHA-256) with your configured secret.
2. Compute it over the **raw HTTP body**, UTF-8. Most frameworks hand you a parsed object;
   re-serialising it changes bytes and the hash will never match. Capture the raw body first.
3. The result is **not base64 encoded**. Many stock HMAC helpers base64 by default — compare hex.

On mismatch, return **401** and drop the payload.

## 4. Answer correctly — your status code is a control signal

| You return | Dotdigital does |
|---|---|
| 200, 201, any 2xx | Marks accepted |
| 400 | Gives up — **never retried**, the event is lost |
| 401 | Treats as auth/HMAC failure |
| anything else | Retries |

Never return 400 for a transient problem: that is a permanent discard.

## 5. Respond in under 10 seconds

Your receiver has **10 seconds**. Validate the HMAC, enqueue, return 2xx. Do not process
inline — the docs are explicit that 10 seconds is not enough to reliably process events.

## 6. Understand the retry budget

Backoff runs for up to **24 hours**, then the event is dropped:
5s, 10s, 30s, 1m, 2m, 5m, 10m, 15m, 30m, 1h, 2h, 4h, 4h, 4h, 4h, 4h.
Downtime longer than a day is data loss, not delay.

## 7. Route on the envelope

Every event, whatever its type, arrives in the same envelope:

```json
{ "eventId": "...", "accountId": 123, "apiSpaceId": "...",
  "name": "message.sent", "payload": { }, "revision": 2,
  "etag": "...", "timestamp": "2026-08-13T08:19:48.494Z" }
```

Dispatch on `name`. Deduplicate on `eventId` — delivery is at-least-once and retries are real.
Use `revision` to discard an out-of-order older state for the same entity. Correlate back to
your own send by reading the `metadata` you supplied at send time.
