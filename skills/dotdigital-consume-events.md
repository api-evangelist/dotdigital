---
name: Consume Dotdigital events with a durable subscription
description: Create an event subscription with filters, poll it with a checkpoint cursor, retrieve oversized payloads, and import your own custom events.
api: openapi/dotdigital-events-openapi.yml
operations: [createSubscription, listSubscriptions, getSubscription, updateSubscription, deleteSubscription, exportEvents, retrieveLob, importEvents]
generated: '2026-08-13'
method: generated
source: openapi/dotdigital-events-openapi.yml + https://marketing.developer.dotdigital.com/reference/export-events
---

# Consume Dotdigital events

The Events API is the **pull** half of Dotdigital's event surface: one service returns activity
from across the whole platform instead of you polling each product's own reporting endpoints.
The push half is webhooks — see `skills/dotdigital-receive-webhooks.md`.

Base: `https://{region}-api.dotdigital.com/events/v3`. HTTP Basic with API user credentials.

## 1. Create the subscription

`POST /events/v3/export/subscriptions` → `createSubscription`.

- `name` must be unique within the account's subscriptions.
- Filters are **ANDed**: if you attach filters to an event type, *all* of them must match for
  the event to be captured.
- To OR across different filter sets, **add the same event type to the subscription more than
  once**, each with its own filters. There is no OR operator.

Manage subscriptions with `listSubscriptions`, `getSubscription`, `updateSubscription` and
`deleteSubscription` (`GET/PUT/DELETE /events/v3/export/subscriptions/{subscriptionId}`).

## 2. Poll with the checkpoint cursor

`GET /events/v3/export/{subscriptionId}` → `exportEvents`.

- On the **first** call, pass **no** `checkPoint`. You get the earliest queued events.
- On every call after that, pass the `checkPoint` from the previous response. That value is your
  acknowledgement — sending it is what tells Dotdigital you received the previous page.
- An empty `events` array means you are caught up.
- **Maximum call duration is 30 seconds.** Set your client timeout accordingly; this is the one
  operation in the estate that does not get the 121-second budget.

## 3. Do not let the subscription go stale

A subscription that is not read within **30 days** is automatically set to `inactive` for
non-usage. If your consumer is scheduled, schedule it more often than monthly, and alarm on
"no successful poll in N days" rather than only on errors.

## 4. Fetch oversized fields separately

Some event fields are too large to travel inside the event. Those arrive as a large-object
reference; fetch the content with `GET /events/v3/lob/{lobId}` → `retrieveLob`. Do this lazily —
only for the events you actually process.

## 5. Push your own events in

`POST /events/v3/import` → `importEvents` imports a batch of contact-associated events so they
show on the single customer view and become available to segmentation and personalisation.
Events are associated to contacts by identifier, using the same identifier-type model as the v3
contacts service (`contactId`, `email` or mobile number).

## Ordering, duplication and errors

- The checkpoint model gives **at-least-once** delivery. There is no dedupe on Dotdigital's side
  and no idempotency key, so key your sink on the envelope's `eventId` and make your handler
  idempotent yourself.
- Errors use the v3 envelope `{errorCode, description, details[]}`.
- Rate limits: polling calls sit in the **unlimited** tier, so a tight poll loop will not
  consume your data-call budget — but a 30-second call ceiling still bounds how much you can
  drain per request.
