---
name: Sync contacts into Dotdigital (v3 unified contacts)
description: Create, look up, bulk-import and delete contacts using the Dotdigital v3 unified contacts service, addressing people by contact id, email or mobile number.
api: openapi/dotdigital-contacts-openapi.yml
operations: [getContacts, createContact, getContact, replaceContact, importContact, deleteContact, importContacts, getImportStatus, deleteContacts, getDeleteStatus]
generated: '2026-08-13'
method: generated
source: openapi/dotdigital-contacts-openapi.yml + conventions/dotdigital-conventions.yml
---

# Sync contacts into Dotdigital

Use the **v3 unified contacts** service, not the v2 email-contacts service. Twenty of the v2
contact operations are marked `deprecated: true` in Dotdigital's own spec
(`openapi/dotdigital-email-contacts-openapi.yml`).

## Before the first call

1. **Pick the region host.** Dotdigital accounts are pinned to a region and calling the wrong
   host returns `403 Forbidden: Access is denied`. Hosts are `r1-api.dotdigital.com` (Europe),
   `r2-api.dotdigital.com` (North America), `r3-api.dotdigital.com` (Asia Pacific). If you do
   not know the region, call `ApiAccount_GetCurrentAccountInfo`
   (`GET /v2/account-info`) against `r1-api.dotdigital.com` — the response names the correct
   endpoint. Cache it; do not re-discover per request.
2. **Authenticate with HTTP Basic** using an API user's generated username and password. There
   is no OAuth and no API key. Use one API user per integrating system so it can be revoked
   independently.
3. Send and expect JSON. All datetimes are UTC ISO 8601.

## Addressing a contact

Every single-contact route takes `{identifier}/{value}`, where `identifier` is the identifier
*type*. That is the whole point of unified contacts: the same route serves all three.

- `GET /contacts/v3/{identifier}/{value}` → `getContact`
- `PUT /contacts/v3/{identifier}/{value}` → `replaceContact` — **replaces the whole contact**
- `PATCH /contacts/v3/{identifier}/{value}` → `importContact` — merges only the fields you send
- `DELETE /contacts/v3/{identifier}/{value}` → `deleteContact`

Prefer `importContact` (PATCH) for routine syncs. `replaceContact` (PUT) will blank any field
you omit.

## Creating one contact

`POST /contacts/v3` → `createContact`. This fails with **409** if the identifiers you pass
already match a contact. That 409 is the signal to switch to `importContact` — Dotdigital has no
upsert flag and no `Idempotency-Key`, so a retried `createContact` after a network timeout can
legitimately return 409 for a contact your first attempt actually created. Treat 409 as
"already exists, go patch it", not as an error to surface.

## Bulk import (the normal path for a sync)

1. `PUT /contacts/v3/import` → `importContacts`. Creates contacts that do not exist and updates
   those that do.
2. The call is **asynchronous**. It returns an import id.
3. Poll `GET /contacts/v3/import/{importId}` → `getImportStatus` until it reports completion.
4. **Read the failures in the result.** Contacts can be created or updated while an associated
   data set fails; those per-record failures only appear in the import status response, never
   as a non-2xx on the original call.

## Bulk delete

1. `POST /contacts/v3/delete` → `deleteContacts` (async, any identifier type).
2. Poll `GET /contacts/v3/delete/{deleteId}` → `getDeleteStatus`.
   This is destructive and not reversible.

## Listing

`GET /contacts/v3` → `getContacts`. v3 uses **seek pagination**: pass `limit` (0–10,000,
default 5,000) and, from the second page on, the `marker` returned in the response's `_links`.
Do not pass pagination parameters on the first call. Items are in `_items`. Data is returned in
ascending order.

## Rate limits and backoff

Contact reads are typically a **high** tier call and bulk imports a **low** tier call; the tiers
are counted separately per minute, per account, across the whole API estate. Read
`X-RateLimit-Remaining` and `X-RateLimit-Reset` (lowercase under HTTP/2 — match
case-insensitively). On **429**, sleep until `X-RateLimit-Reset` minus now, in seconds. Retrying
sooner returns 429 again until the window rolls.

## Errors

v3 returns a structured envelope:

```json
{ "errorCode": "contacts:invalidContacts",
  "description": "Invalid contact data",
  "details": [ { "item": "email", "error": "You must specify a value" } ] }
```

Branch on `errorCode`, show `description`, and map `details[].item` back to your source record's
fields. This is not RFC 9457 — there is no `type`/`title`/`status`, and the content type is
`application/json`, not `application/problem+json`.

Allow **121 seconds** before treating a call as timed out.
