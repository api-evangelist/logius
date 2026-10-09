---
name: logius-notification-subscriptions
description: Define a domain, subscribe to notifications and publish CloudEvents with the draft Logius Notification API.
api: logius:notificatieservices
generated: '2026-10-09'
method: generated
source: openapi/logius-notificatieservices-openapi.yml
operations:
- domains_list
- domains_post
- domains_get
- subscriptions_post
- subscriptions_list
- subscription_get
- subscription_put
- subscription_patch
- subscription_delete
- events_post
---
# Notification subscriptions and events (draft, Notificatieservices)

Draft standard (v0.1.5); implementers host it (relative server /api/v1).

1. `domains_list` / `domains_get` — find the event domain; `domains_post` to define one.
2. `subscriptions_post` (POST /subscriptions) — subscribe to a domain; keep the returned uuid.
3. `subscriptions_list`, `subscription_get` — inspect subscriptions.
4. `subscription_put` (full replace) or `subscription_patch` (partial) to change one; `subscription_delete` to unsubscribe.
5. `events_post` (POST /events) — publish an event using the NL GOV profile for CloudEvents.

Rules: PUT and DELETE on /subscriptions/{uuid} are idempotent; POST is not, so do not retry subscriptions_post blindly.
