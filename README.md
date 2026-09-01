# Portfolio — Jefferson Alves

**Applied AI Engineer** · [orkestra.systems/jefferson](https://orkestra.systems/jefferson)

I build the operational software a business opens every morning — dispatch, the app the field worker uses, and the money that has to reconcile at month end. Each case study below follows the same structure: the **problem**, the **architecture**, what the system does **on its own**, what it **hands back to a person**, and the **measured result**.

> Personal data in the screenshots is redacted. Architecture and results are real, and every number here comes from the running system.

---

## Case studies

### 🧭 [Live Portugal — the system that runs the day](case-studies/live-portugal-ai-os.md)
**In production every day since May 2026.**
A Lisbon tuk-tuk operator ran the whole day by hand across disconnected tools: bookings in Google Calendar, driver coordination over WhatsApp, the weekly roster on a printed grid taped to a wall, and customer messages typed one at a time in six languages.

No scheduling form was ever going to beat that grid, so I did not replace it — the operator photographs it, Claude reads the image, and it becomes a real, editable schedule. From there the day runs itself: 15 drivers dispatched, each seeing only their own work in an installable phone app; every driver's balance settling as each tour closes; every partner hotel's commission ready at month end; and customer messages written in the right language at the right time, in a queue that sends with one tap.

**Measured:** 6 hours of manual work removed per week · first customer response down from about 2 hours to under 1 minute · 279 of 281 messages delivered (99.3%) across 6 languages · 6,183 bookings synced · 83 driver dispatches across 76 tours.

*Full disclosure: I am employed by this company. I built the system it runs on and I use it every day, so I live with its failures.*

`Next.js 15` · `TypeScript` · `Supabase` · `n8n` · `Claude API` · `WhatsApp Business` · `Google Calendar` · `Vision / image-to-data`

### 📊 [Daily AI Reporting Agent](case-studies/daily-ai-reporting-agent.md)
**Ran in production from April 2026 until the client engagement ended in August 2026.**
A paid-media manager in Brazil spent about 40 minutes every morning consolidating ad spend across client accounts. A single scheduled pipeline replaced it: n8n fetches the data, Claude flags anomalies and writes the narrative summary, Telegram delivers it before the working day starts. **About 40 min/day → roughly zero** on routine days. A different client, a different country — the smallest useful shape of automation, and usually the first one a small business needs.
`n8n` · `Claude API` · `Telegram Bot API` · `Supabase`

### 🚦 [Cockpit LX](case-studies/cockpit-lx.md)
**Pilot ran May–August 2026. Retired.**
Tuk-tuk drivers in Lisbon were missing demand spikes and reacting late to road restrictions. The tempting build was an AI agent. The correct build was rules over live feeds — maritime traffic, road restrictions, weather, city events — delivered inside Telegram, which the drivers already had. Deterministic, fast, and incapable of inventing a cruise ship that isn't coming. A model appears in exactly one place: filtering noisy news into driver-relevant alerts, where a fixed rule does poorly. **325 alerts delivered (~5/day) and 50 cruise arrivals tracked** during the pilot.
`n8n` · `Telegram Bot API` · `Telegram Mini App` · `Claude Haiku (filtering only)` · `Real-time data pipelines`

---

## How I decide where the model goes

| Layer | What it needs | Example |
|---|---|---|
| Structured, rule-shaped data | Deterministic code. No model, no per-event cost, nothing to hallucinate | Cruise arrivals, weather, road restrictions (Cockpit LX) |
| Interpretation of messy input | A model, with a person reviewing the output | Reading a photographed roster grid; filtering raw news into relevant alerts |
| Writing for a human reader | A model, generating — but a person deciding when it goes out | D-1 and D+1 customer messages, written automatically, sent with one tap |
| Anything that leaves the building | A person, always | WhatsApp sends, roster assignments, cancellations |

Knowing which layer needs a model and which needs plain deterministic code is most of the engineering. The principle underneath all three systems is the same: **agents inform, humans decide direction** — and nothing reaches a customer without someone choosing to send it.

---

📫 **Get in touch:** [LinkedIn](https://www.linkedin.com/in/jefferson-orkestra) · [jefferson@orkestra.systems](mailto:jefferson@orkestra.systems)
