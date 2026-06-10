# Portfolio — Jefferson Alves

**AI Operations Architect** · [orkestra.systems/jefferson](https://orkestra.systems/jefferson)

Production agentic systems I designed and built. Each case study follows the same structure: the **problem**, the **architecture**, what runs **autonomously**, what **escalates to a human**, and the **measurable result**.

> Client names are anonymized for confidentiality. Architecture and results are real.

---

## Case studies

### 🚦 [Cockpit LX — Real-time Operational Dashboard](case-studies/cockpit-lx.md)
Tuk-tuk drivers in Lisbon were missing demand spikes and reacting late to traffic restrictions. I built a deterministic multi-source pipeline (n8n) that aggregates maritime traffic, road restrictions, weather, and city events, then pushes contextual alerts to a Telegram driver group — with an inline **Telegram Mini App** dashboard. No app install, no LLM cost per alert.
`n8n` · `Telegram Bot API` · `Telegram Mini App` · `Real-time data pipelines`

### 📊 [Daily AI Reporting Agent](case-studies/daily-ai-reporting-agent.md)
A traffic manager spent ~40 minutes every morning consolidating ad spend across client accounts. I built a single agentic pipeline: n8n fetches the data, Claude API flags anomalies and writes a narrative summary, Telegram delivers it by 8 AM. **40 min/day → 0** on routine days. 37+ reports in production with zero missed days.
`n8n` · `Claude API` · `Telegram Bot API` · `Supabase`

### 💬 [Multilingual WhatsApp Pipeline](case-studies/whatsapp-automation.md)
A Lisbon tour operator was manually sending booking reminders and post-tour follow-ups to international clients. I built a sequential pipeline that reads bookings from Google Calendar, generates personalized messages in the client's language (PT/EN/ES/DE/FR) via Claude API, and delivers them over WhatsApp Business. **Multi-tenant from day one** — a new client is one database row, not a new deployment.
`n8n` · `Claude API` · `WhatsApp Business` · `Google Calendar` · `Supabase`

---

## How I think about agentic systems

| Tier | Pattern | Example |
|---|---|---|
| **Tier 0** | Single agent + tools + scheduled trigger | Daily AI Reporting Agent |
| **Tier 1** | Sequential / multi-source pipeline | WhatsApp Pipeline, Cockpit LX |

The principle: **agentic infrastructure means choosing the right tool for each layer** — not applying AI uniformly. Deterministic where rules suffice; LLM where interpretation is required.

---

📫 **Get in touch:** [orkestra.systems](https://orkestra.systems) · [Website](https://orkestra.systems/jefferson)
