# Live Portugal AI OS — an Operating System for a Tour Operator

**Status:** In production · **Domain:** Tour operations — Lisbon, Portugal
**Stack:** Next.js 15 (PWA) · Supabase · n8n (self-hosted) · Claude API · Evolution API (WhatsApp Business) · Google Calendar API
**Pattern:** AI Operating System — Design · Build · Embed

<p align="center">
  <img src="assets/live-portugal-splash.png" width="32%" alt="Splash — Live Portugal AI OS" />
  <img src="assets/live-portugal-hoje.png" width="32%" alt="Hoje — daily cockpit" />
</p>
<p align="center">
  <img src="assets/live-portugal-escala.png" width="24%" alt="Escala — AI reads the schedule photo" />
  <img src="assets/live-portugal-drivers.png" width="24%" alt="Drivers — live availability" />
  <img src="assets/live-portugal-envios.png" width="24%" alt="Envios — WhatsApp send queue" />
  <img src="assets/live-portugal-reserva.png" width="24%" alt="Reserva — booking detail" />
</p>
<p align="center">
  <img src="assets/live-portugal-calendario.png" width="24%" alt="Calendário — week view" />
  <img src="assets/live-portugal-definicoes.png" width="24%" alt="Definições — integrations" />
  <img src="assets/live-portugal-mais.png" width="24%" alt="Mais — menu" />
  <img src="assets/live-portugal-driver-perfil.png" width="24%" alt="Driver profile" />
</p>

---

## Problem

Live Portugal runs daily tuk-tuk tours across Lisbon for international clients. The whole operation lived in disconnected tools and in people's heads: bookings in Google Calendar, driver coordination over WhatsApp, the weekly roster on a printed grid, and reminders and reviews typed one by one in five languages. There was no single place to see the day — and the work that needed no judgment was eating the operator's hours.

The goal was not one automation. It was an **operating system for the operation**: one place to run the day, with the AI doing the repetitive work and the humans deciding direction.

---

## What I built

An AI OS embedded into the operation — an installable, mobile-first PWA backoffice, backed by autonomous workflows, running in the client's own brand (*powered by Orkestra*).

- **Cockpit (Hoje)** — the daily home: today's tours, confirmed vs. unassigned, a send-queue alert, and driver assignment in two taps.
- **AI weekly roster (Escala)** — the operator uploads a *photo* of the schedule grid; Claude reads the image, detects the week, and assigns each tuk to its driver — then it's review and apply.
- **Drivers** — the team with live availability ("free now"), per-driver profiles, languages, vehicle, and history.
- **Send queue (Envios)** — driver briefings, D-1 reminders, and D+1 review requests, each one tap to WhatsApp.
- **Multilingual WhatsApp pipeline** — n8n + Claude generate personalised D-1/D+1 messages in the client's language (PT/EN/ES/DE/FR), delivered via WhatsApp Business, logged to Supabase.
- **Native on the phone** — installs and runs as a real full-screen app on the operator's smartphone.

---

## The standout: an AI that reads the roster

The weekly roster was a printed grid no system could parse. Instead of forcing the operator to re-type it, the operator simply **photographs the grid** and uploads it. Claude reads the image, detects the week, and proposes the tuk↔driver assignment for every day. The operator reviews and applies — minutes instead of an hour of manual entry, with the human always in the loop on the final call.

---

## Multilingual WhatsApp pipeline

One capability inside the OS: the autonomous customer-communications pipeline.

```
[Google Calendar — booking source]
        ↓
[n8n — D-1 at 17:00 UTC · D+1 at 09:00 UTC]
        ↓
[Claude API — personalised message in the client's language]
        ↓
[Evolution API — WhatsApp Business delivery]
        ↓
[Supabase — message + delivery-status log]
```

![The production pipeline in n8n: scheduled trigger → fetch bookings (Google Calendar) → generate a personalised message with Claude → send via WhatsApp Business → log the send.](assets/whatsapp-pipeline.png)

![Automated messages: the D-1 reminder (left) and the D+1 follow-up with review request (right), each generated in the client's language. Personal data redacted.](assets/whatsapp-messages.png)

Multi-tenant from day one: one workflow set serves every operator tenant — a new operator is a database row, not a new deployment.

---

## What runs autonomously · what escalates

**Autonomous:** reads bookings from Google Calendar; reads the weekly-roster photo and proposes driver↔tuk assignments; generates D-1 reminders and D+1 review requests in the client's language; delivers via WhatsApp Business; logs every message and delivery status to Supabase.

**Escalates to the operator:** any cancellation or change request; delivery failures; replies outside expected patterns; roster assignments are always reviewed before they apply. Agents inform — the human decides direction.

---

## What this demonstrates

The full **Design → Build → Embed** of an AI OS into a live operation — not a single script, but a system the operator runs the day on, in their own brand. Built on the same AI OS I run on my own operation (dogfooding as proof). The multilingual WhatsApp pipeline is one capability inside a broader system that also covers the cockpit, the AI roster, driver management, and the send queue.

The pattern is replicable to any service operation with scheduling and field staff: tour operators, clinics, salons, property management, field services.
