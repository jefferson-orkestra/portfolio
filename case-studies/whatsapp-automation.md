# Multilingual WhatsApp Automation — Tour Operator Communications

**Status:** Pilot approved for production · **Domain:** Customer communications automation — B2C (Lisbon, Portugal)
**Stack:** n8n (self-hosted) · Claude API · Evolution API (WhatsApp Business) · Google Calendar API · Supabase
**Pattern:** Tier 1 — Sequential pipeline, multi-tenant

![Automated messages: the D-1 reminder (left) and the D+1 follow-up with review request (right), generated in the client's language. Personal data redacted for privacy.](assets/whatsapp-messages.png)

---

## Problem

A Lisbon tuk-tuk tour operator manages bookings across multiple languages and nationalities daily. Two critical communication tasks were being done manually:

- **D-1 reminder:** send a confirmation message to each client the day before their tour — manual, time-consuming, inconsistent.
- **D+1 follow-up:** send a thank-you message and review request the day after — frequently skipped under operational load.

Both tasks require no judgment — only scheduling, personalisation, and language matching. Both directly impact no-show rates and online review volume.

---

## Architecture

```
[Google Calendar — booking source]
        ↓
[Cron trigger — 17:00 UTC daily (D-1)]
[Cron trigger — 09:00 UTC daily (D+1)]
        ↓
[n8n — fetch tomorrow's / yesterday's bookings]
        ↓
[Claude API — generate personalised message in client language]
        ↓
[Evolution API — send via WhatsApp Business]
        ↓
[Supabase — log message + delivery status]
        ↓
[n8n — handler for incoming WhatsApp replies]
```

![The production pipeline in n8n: scheduled trigger → fetch bookings (Google Calendar) → generate a personalised message with the AI agent (Claude) → send via WhatsApp Business → log the send. The same structure runs for both the D-1 reminder (17:00) and the D+1 follow-up (09:00).](assets/whatsapp-pipeline.png)

**Multi-tenant architecture:** a single workflow set serves all operator tenants. Client configuration lives in a database table — adding a new operator requires only a new row, no code changes.

---

## What runs autonomously

- Reads tomorrow's bookings from Google Calendar at 17:00 UTC
- Generates a personalised D-1 reminder in the client's language (PT, EN, ES, DE, FR — detected from booking data)
- Sends via WhatsApp Business through Evolution API
- Reads yesterday's completed tours at 09:00 UTC
- Generates a D+1 thank-you + review request in the client's language
- Handles incoming WhatsApp replies (confirmation, cancellation)
- Logs all messages and delivery status to Supabase

## What escalates to a human

- Client explicitly cancels or requests a change → operator notified
- Message delivery failure → operator alert
- Reply outside expected patterns → operator review queue

---

## Results

- **5 languages** handled automatically with tone-appropriate copy
- **Multi-tenant:** the same 4 workflows serve future operator clients without code changes
- Pilot reviewed and approved by the operator before production cutover

---

## What this demonstrates

A **Tier 1 sequential pipeline**: trigger → data fetch → LLM personalisation → delivery → logging. The same pattern applies to any service business with scheduled appointments — clinics, salons, restaurants, coaches.

**Multi-tenant SaaS architecture from day one:** adding a new client operator is configuration, not development.
