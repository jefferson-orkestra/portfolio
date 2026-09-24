<img src="assets/jefferson-round.png" width="96" align="left" alt="Jefferson Alves">

# Portfolio · Jefferson Alves

**AI Systems Architect · Founder, Orkestra** · Lisbon · [the system](https://orkestra.systems) · [the proof](https://orkestra.systems/jefferson) · [how it starts](https://orkestra.systems/map) · [LinkedIn](https://www.linkedin.com/in/jefferson-orkestra) · [Upwork](https://www.upwork.com/freelancers/jeffersonalves)

I build AI operating systems for businesses: beyond automations, one system your whole operation runs on. The AI prepares; a person dispatches. One measure: productivity. I find the task a team repeats most, measure it before touching anything, automate the bulk of it, and leave the final call with a person. Then I measure again. The difference between those two numbers is the work.

Every case here follows the same structure: the **task**, the **baseline** measured before anything changed, what the machine **does on its own**, what **stays with a person**, and the **result measured after**. No number without a source.

> Screenshots are from the demo tenant (same software, synthetic names) unless marked otherwise.

<br clear="left">

<a href="https://orkestra.systems"><img src="assets/orkestra-cover.jpg" width="100%" alt="Orkestra: one system for an operation that used to live across tools that never talked to each other"></a>

---

## In production

### 🧭 [Live Portugal: the system that runs the day](case-studies/live-portugal-ai-os.md)

**In production every day since May 2026.** A Lisbon tour operator used to build its week by hand in a spreadsheet, export it as a picture and post it in the drivers' WhatsApp group. Bookings lived in a calendar, the accounts in other spreadsheets, and customer reminders were typed one at a time, in six languages.

Today one system runs that day. It started with one question, how to stop typing every reminder by hand, and grew module by module into the system that runs the whole operation. The managers still build the week themselves; they build it on a screen made for it and publish it in one click, to the group and into each driver's own app. Assigning a tour no longer means checking who is working. Every driver's balance settles as the day closes, every partner's commission is ready at month end. Customer messages write themselves in the right language at the right time, and sending stays one tap, deliberately.

**Measured (August 2026):** around **20 hours of manual work removed per month** · **414 messages** in six languages, **404 delivered** · **6,499 bookings** synced.

*Full disclosure: I am employed by this company. I built the system it runs on and I use it every day, so I live with its failures.*

`Next.js 15` · `TypeScript` · `Supabase` · `n8n` · `Claude API` · `WhatsApp Business` · `Google Calendar`

#### Four tasks, four before-and-afters

| Task | Before | After | Back per month | Watch |
|---|---|---|---|---|
| **Customer messages** | each booking copied into ChatGPT, pasted into WhatsApp, in six languages | written automatically, sent with one tap | **≈ 6 h** | [▶ 1:48](https://cdn.jsdelivr.net/gh/jefferson-orkestra/portfolio@main/videos/v2-comms.mp4) |
| **The weekly schedule** | spreadsheet → picture → WhatsApp group; a dead end | built by the managers on a screen made for it; published in one click; feeds dispatch | **≈ 3 h** | [▶ 1:41](https://cdn.jsdelivr.net/gh/jefferson-orkestra/portfolio@main/videos/v3-escala.mp4) |
| **Dispatch and the driver's app** | five phone calls to find who is free; briefings typed by hand | one screen shows who can take it; the driver's app buzzes | **≈ 4 h** | [▶ 1:10](https://cdn.jsdelivr.net/gh/jefferson-orkestra/portfolio@main/videos/v4-ops.mp4) |
| **The money** | balances and commissions in spreadsheets; an afternoon to close the month | settles as each tour closes; close in half an hour | **≈ 6 h** | [▶ 1:03](https://cdn.jsdelivr.net/gh/jefferson-orkestra/portfolio@main/videos/v5-money.mp4) |

<p align="center">
  <a href="https://cdn.jsdelivr.net/gh/jefferson-orkestra/portfolio@main/videos/v2-comms.mp4"><img src="videos/v2-comms-cover.png" width="32%" alt="Five times a day, a booking was retyped into ChatGPT"></a>
  <a href="https://cdn.jsdelivr.net/gh/jefferson-orkestra/portfolio@main/videos/v3-escala.mp4"><img src="videos/v3-escala-cover.png" width="32%" alt="The schedule stopped being a picture and became data"></a>
  <a href="https://cdn.jsdelivr.net/gh/jefferson-orkestra/portfolio@main/videos/v4-ops.mp4"><img src="videos/v4-ops-cover.png" width="32%" alt="A last-minute tour used to mean five phone calls"></a>
  <a href="https://cdn.jsdelivr.net/gh/jefferson-orkestra/portfolio@main/videos/v5-money.mp4"><img src="videos/v5-money-cover.png" width="32%" alt="Nobody reconciles a spreadsheet at the end of the month"></a>
</p>

<p align="center">
  <img src="case-studies/assets/tours.jpg" width="49%" alt="Every booking in one list">
  <img src="case-studies/assets/roster-builder.jpg" width="49%" alt="The roster builder">
</p>

---

## Earlier work (retired)

| Project | What it did | Stack | Ran |
|---|---|---|---|
| **[Daily AI Reporting Agent](case-studies/daily-ai-reporting-agent.md)** | Daily ad-spend report for a paid-media manager in Brazil: about 40 min of manual reporting a day, cut to roughly zero on routine days | n8n · Claude API · Telegram | Apr–Aug 2026 |
| **[Cockpit LX](case-studies/cockpit-lx.md)** | Real-time operational alerts for tuk-tuk drivers: rules over live feeds, deliberately no model in the loop except for filtering news | n8n · Telegram Bot & Mini App · real-time feeds | May–Aug 2026 |

---

## How I decide where the model goes

| Layer | What it needs | Example |
|---|---|---|
| Structured, rule-shaped data | Deterministic code. No model, no per-event cost, nothing to hallucinate | Balances, commissions, cruise arrivals, weather |
| Writing for a human reader | A model generating; a person deciding when it goes out | Customer messages in six languages, written automatically, sent with one tap |
| Interpretation of messy input | A model, with a person reviewing the output | Filtering raw news into driver-relevant alerts |
| Judgment about people, money going out, anything that leaves the building | A person, always | Who works when, who takes which tour, every WhatsApp send |

Half the job is saying where AI does not belong: money going out, decisions about people, the reply to an angry customer, anything whose source cannot be traced. Knowing where to stop is what keeps an operation from getting more fragile as it gets more automated.

---

## How an engagement starts

Fixed price, one to two weeks: **the map and the first module**. I map every tool your operation lives in and every jump between them, find the most expensive jump, time it before anything changes, write down what the AI will never touch, build the first module of the system, and come back at 30 days to measure. You end up with the map, one working module built so the next one fits, and a number you can trust, whether or not you continue with me.

📫 [LinkedIn](https://www.linkedin.com/in/jefferson-orkestra) · [Upwork](https://www.upwork.com/freelancers/jeffersonalves) · [jefferson@orkestra.systems](mailto:jefferson@orkestra.systems)
