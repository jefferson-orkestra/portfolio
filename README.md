# Portfolio — Jefferson Alves

**AI Operating Systems Architect** · [orkestra.systems/jefferson](https://orkestra.systems/jefferson)

*I design, build, and embed AI Operating Systems into existing operations.* Production systems below — each case study follows the same structure: the **problem**, the **architecture**, what runs **autonomously**, what **escalates to a human**, and the **result**.

> Client names are anonymized for confidentiality. Architecture and results are real.

---

## Case studies

### 🧭 [Live Portugal AI OS — an Operating System for a Tour Operator](case-studies/live-portugal-ai-os.md)
A Lisbon tuk-tuk operator ran the whole day by hand across disconnected tools. I designed, built, and embedded an **AI Operating System** into their operation: an installable mobile **cockpit** (Next.js PWA) for the daily run and driver assignment; an **AI weekly roster** that reads a *photo* of the schedule grid and assigns each tuk to its driver; a **WhatsApp send queue**; and an autonomous **multilingual pipeline** (n8n + Claude + WhatsApp Business) for D-1/D+1 messages in five languages. Runs as a native app, in the client's own brand. In production.
`Next.js` · `Supabase` · `n8n` · `Claude API` · `WhatsApp Business` · `Google Calendar` · `Vision / image-to-data`

### 🚦 [Cockpit LX — Real-time Operational Dashboard](case-studies/cockpit-lx.md)
Tuk-tuk drivers in Lisbon were missing demand spikes and reacting late to traffic restrictions. I built a deterministic multi-source pipeline (n8n) that aggregates maritime traffic, road restrictions, weather, and city events, then pushes contextual alerts to a Telegram driver group — with an inline **Telegram Mini App** dashboard. No app install, no LLM cost per alert.
`n8n` · `Telegram Bot API` · `Telegram Mini App` · `Real-time data pipelines`

### 📊 [Daily AI Reporting Agent](case-studies/daily-ai-reporting-agent.md)
A traffic manager spent ~40 minutes every morning consolidating ad spend across client accounts. I built a single agentic pipeline: n8n fetches the data, Claude API flags anomalies and writes a narrative summary, Telegram delivers it by 8 AM. **40 min/day → 0** on routine days. 37+ reports in production with zero missed days.
`n8n` · `Claude API` · `Telegram Bot API` · `Supabase`

---

## How I think about agentic systems

| Tier | Pattern | Example |
|---|---|---|
| **Tier 0** | Single agent + tools + scheduled trigger | Daily AI Reporting Agent |
| **Tier 1** | Sequential / multi-source pipeline | Cockpit LX, Live Portugal WhatsApp pipeline |
| **System** | An AI OS embedded into the operation — many capabilities, one product | Live Portugal AI OS |

The principle: **agentic infrastructure means choosing the right tool for each layer** — not applying AI uniformly. Deterministic where rules suffice; LLM where interpretation is required; a system, not a script, when it has to run the operation.

---

📫 **Get in touch:** [orkestra.systems](https://orkestra.systems) · [Website](https://orkestra.systems/jefferson)
