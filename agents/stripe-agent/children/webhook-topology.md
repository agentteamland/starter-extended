---
knowledge-base-summary: "Stripe webhooks land at `POST /api/billing/webhooks/stripe`: raw body read, signature verified, Redis SETNX dedup by `event.id`, MediatR dispatch, 200 returned regardless of handler result (failures retried via RMQ DLX, not Stripe retry)."
---

# Webhook topology

Stripe webhooks go to `POST /api/billing/webhooks/stripe`. The endpoint:

1. Reads raw body (NOT the parsed model — signature is computed over raw bytes)
2. Verifies `Stripe-Signature` header with the webhook secret from dynamic settings
3. SETNX `stripe:event:{event.id}` in Redis with 24h TTL — returns 200 immediately if key exists (Stripe will retry on non-200, so idempotency is critical)
4. Dispatches to an internal MediatR command based on `event.type` (e.g., `customer.subscription.updated` → `HandleSubscriptionUpdatedCommand`)
5. Returns 200 regardless of downstream handler result (failures retried via RMQ DLX + our own replay machinery — NOT Stripe retry)

Never block the webhook on slow work. Queue it.
