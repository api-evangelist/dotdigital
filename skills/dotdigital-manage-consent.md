---
name: Manage consent, preferences and suppression in Dotdigital
description: Create preference categories, set a contact's opt-ins, unsubscribe and resubscribe correctly, and pull suppression deltas.
api: openapi/dotdigital-preferences-and-subscriptions-openapi.yml
operations: [create-preference, get-preferences, update-preference, delete-preference, get-modified-preferences-since-date, set-preferences-for-contact, get-preferences-for-contact, get-contacts-opted-into-a-preference, get-contacts-with-modified-preference-opt-in-since-date, unsubscribe-contact, resubscribe-contact, resubscribe-contact-with-no-challenge, bulk-suppress-contacts, get-suppressed-contacts-since-date, get-unsubscribed-contacts-since-date, get-subscriptions-for-contact]
generated: '2026-08-13'
method: generated
source: openapi/dotdigital-preferences-and-subscriptions-openapi.yml + errors/dotdigital-error-codes.yml
---

# Manage consent, preferences and suppression

This is the compliance-critical surface. It lives on **v2** at `/v2/preferences` and
`/v2/contacts/...` on the account's regional host. HTTP Basic with API user credentials.

## The two different things

Dotdigital separates **subscription state** (is this contact contactable at all, or on a given
address book) from **preferences** (which topics they opted into). Do not conflate them: a
contact can be subscribed and opted out of every preference, or opted into preferences while
globally suppressed — in which case they receive nothing.

## Preference categories

- `POST /v2/preferences` → `create-preference`
- `GET /v2/preferences` → `get-preferences`
- `PUT /v2/preferences/{id}` → `update-preference`
- `DELETE /v2/preferences/{id}` → `delete-preference`
- `GET /v2/preferences/modified-since/{date}` → `get-modified-preferences-since-date`

## A contact's opt-ins

- `PUT /v2/contacts/{contactIdentifier}/preferences` → `set-preferences-for-contact`
- `GET /v2/contacts/{contactIdentifier}/preferences` → `get-preferences-for-contact`
- `GET /v2/contacts/with-preference/{preferenceId}` → `get-contacts-opted-into-a-preference`
- `GET /v2/contacts/with-preference/{preferenceId}/opt-ins-since/{date}` →
  `get-contacts-with-modified-preference-opt-in-since-date`

Prefer the `*-since/{date}` variants for scheduled syncs — they are deltas, and they keep you in
a cheaper rate-limit tier than re-reading whole populations.

## Unsubscribe and suppression

- `POST /v2/contacts/unsubscribe` → `unsubscribe-contact`
- `PUT /v2/contacts/suppress-contacts` → `bulk-suppress-contacts`
- `GET /v2/contacts/unsubscribed-since/{date}` → `get-unsubscribed-contacts-since-date`
- `GET /v2/contacts/suppressed-since/{date}` → `get-suppressed-contacts-since-date`
- `GET /v2/contacts/{email}/subscriptions` → `get-subscriptions-for-contact`

Address-book-scoped equivalents live in
`openapi/dotdigital-lists-address-books-openapi.yml`:
`unsubscribe-contact-from-address-book`, `resubscribe-contact-to-address-book`,
`get-unsubscribed-contacts-from-address-book-since-date`.

## Resubscribe — the one that needs a decision

There are two operations and they are not interchangeable:

| Operation | Behaviour |
|---|---|
| `resubscribe-contact` (`POST /v2/contacts/resubscribe`) | Sends the contact a challenge/confirmation before they are resubscribed |
| `resubscribe-contact-with-no-challenge` (`POST /v2/contacts/resubscribe-with-no-challenge`) | Resubscribes immediately, no confirmation |

Default to the **challenge** version. Only use `-with-no-challenge` when you hold a documented,
auditable consent record captured elsewhere, because it re-enables sending to someone who
previously opted out with no confirming interaction. The same pairing exists on the address-book
routes.

## Errors that matter here

From `errors/dotdigital-error-codes.yml`:

- `ERROR_CONTACT_SUPPRESSED` — the contact is suppressed account-wide
- `ERROR_CONTACT_SUPPRESSEDFORADDRESSBOOK` — suppressed only for that book
- `ERROR_CONTACT_RESUBSCRIPTION_INVALID` — resubscription not permitted for this contact
- `ERROR_PREFERENCE_NOT_FOUND` / `ERROR_PREFERENCE_INVALID`
- `ERROR_EMAIL_BANNED` — terminal; never retry, never re-add

Treat every suppression error as **terminal state, not a transient failure**. Write it back to
your own system so you stop attempting the contact, rather than retrying and re-learning it.

## Delta cadence

All the `since-date` routes take a UTC ISO 8601 date. Take "now" from
`ApiAccount_GetServerTime` (`GET /v2/server-time`), not from your own clock, and store the
watermark you actually processed so a failed run resumes rather than re-reads.
