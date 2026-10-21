# Subscription Auditor

A phone-first, on-device subscription-audit tool for finance teams and business owners — plus the guides to run it and sell it.

**The data never leaves the user's own device.** There is no server, no login, and no upload. It's a single-tenant tool: each buyer runs their own copy, their data stays with them, and reminders fire from their own phone calendar — so the seller never holds anyone's data.

## What's in here

| File | What it is |
|---|---|
| [`index.html`](index.html) | **The app.** Runs in any browser, installable to a phone home screen. No dependencies, works offline, no LLM. |
| [`manifest.webmanifest`](manifest.webmanifest), [`sw.js`](sw.js), [`icon.svg`](icon.svg) | PWA support files — make it installable as a phone app and work offline. Keep them next to `index.html` when hosting. |
| [`SETUP-GUIDE.md`](SETUP-GUIDE.md) | **Client setup guide.** How to open/install it, what data to add, read the results, set up phone reminders, and the privacy guarantees. |
| [`SALES-PLAYBOOK.md`](SALES-PLAYBOOK.md) | **How & where to sell it** as a ₹1L one-time engagement — targeting, outreach, the demo, objections, delivery, and scaling. |

## What the tool does

1. **Intake** — client pastes or uploads bank / card / UPI statements (CSV, Excel, PDF text, or raw alert lines). Flexible parser with column auto-detection.
2. **Detects recurring charges** — cleans messy merchant names (`UPI/NETFLIX COM/Payment/HDFC` → *Netflix*), groups by merchant, works out the cadence (weekly → annual), and flags every subscription. Single-charge rows get a best-guess cadence, clearly marked *estimated*.
3. **Flags money drains** — new subscriptions, price hikes, duplicate tools in the same category, free trials that went paid, and forgotten charges — ranked by annual rupee cost.
4. **Usage check** — optional seat/active-user input flags unused seats, dead tools, and cost per active user.
5. **Cancellation assist** — per-vendor cancellation steps, a drafted cancellation email, and instructions to revoke UPI AutoPay / card e-mandates, with an explicit human sign-off before anything is acted on. **Nothing is cancelled automatically.**
6. **Output & phone reminders** — a dashboard of all subscriptions, spend, renewal dates, and total savings found (exportable to JSON or print/PDF), plus **renewal reminders written to the phone's own calendar** so the user is alerted ~3 days before each charge.

## Phone-first & reminders

- **Installable:** open it on a phone and *Add to Home Screen* — it runs like an app, full-screen and offline.
- **Reminders with zero backend:** the *Cancel & save* screen exports renewal dates as a `.ics` calendar file. The phone's native calendar then fires the notifications — forever, offline, with nothing stored on any server. (Reliable push to a *closed* app always needs a push server; the calendar route deliberately avoids that so nothing leaves the device.)

## Try it in 30 seconds

Open `index.html` and click **Load sample data → Add this source → Detect subscriptions**. Walk the six steps to see the full flow before using real data.

## Put it on the web (free)

It's static files, so hosting is free and takes a minute:

- **Easiest (no account/coding):** go to [app.netlify.com/drop](https://app.netlify.com/drop) and drag the whole `subscription-audit` folder in. You instantly get a live `https://…netlify.app` URL that works on any phone, installs as an app, and you can send to clients.
- **Already on GitHub:** enable **GitHub Pages** in the repo settings (Settings → Pages), pointing at this folder.
- **Also fine:** Vercel, Cloudflare Pages, or any static host.

Serving over `https` (not a double-clicked file) is what unlocks phone-install and offline.

## Privacy by design

- No network calls — open the browser Network tab and you'll see zero requests.
- No data saved unless the user opts in via *"Remember my data on this device"* (browser local storage, that device only).
- No external libraries, fonts, or LLM — everything is inline and deterministic, so it runs fully offline and the "no AI touches your data" claim is literally true.

## Roadmap — the "auto-pull" layer

The current app ingests data by paste/upload/import. The automated connect-and-pull version is the next layer, and it keeps the same on-device, no-central-storage model:

- **Email auto-detect (next):** the buyer connects *their own* inbox (Gmail API / IMAP) so the app reads bank alerts, AutoPay debits, and renewal receipts automatically. Needs a Google API client set-up; the user's email token stays on their device.
- **Bank connect (later):** true bank/card transaction pull in India goes through the **RBI Account Aggregator** framework (consent-based, read-only — the app never sees a bank password). Requires an AA partner (Setu, Finvu, Perfios/Anumati, Saafe) and FIU registration. There is no safe way to do this by collecting net-banking or UPI credentials directly, so that path is intentionally not built.
