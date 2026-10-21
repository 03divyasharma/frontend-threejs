# Subscription Auditor

A self-contained, in-browser subscription-audit tool for finance teams and business owners — plus the guides to run it and sell it.

**The client's bank data never leaves their browser.** There is no server, no login, and no upload. The whole product is one HTML file.

## What's in here

| File | What it is |
|---|---|
| [`subscription-auditor.html`](subscription-auditor.html) | **The tool.** A single, self-contained HTML file. Double-click to run in any browser. No installation, no dependencies, works offline. |
| [`SETUP-GUIDE.md`](SETUP-GUIDE.md) | **Client setup guide.** How to open it, what statements to gather, how to add data, read the results, and the privacy guarantees. |
| [`SALES-PLAYBOOK.md`](SALES-PLAYBOOK.md) | **How & where to sell it** as a ₹1L one-time engagement — targeting, outreach, the demo, objections, delivery, and scaling. |

## What the tool does

1. **Intake** — client pastes or uploads bank / card / UPI statements (CSV, Excel, PDF text, or raw alert lines). Flexible parser with column auto-detection.
2. **Detects recurring charges** — cleans messy merchant names (`UPI/NETFLIX COM/Payment/HDFC` → *Netflix*), groups by merchant, works out the cadence (weekly → annual), and flags every subscription. Single-charge rows get a best-guess cadence, clearly marked *estimated*.
3. **Flags money drains** — new subscriptions, price hikes, duplicate tools in the same category, free trials that went paid, and forgotten charges — ranked by annual rupee cost.
4. **Usage check** — optional seat/active-user input flags unused seats, dead tools, and cost per active user.
5. **Cancellation assist** — per-vendor cancellation steps, a drafted cancellation email, and instructions to revoke UPI AutoPay / card e-mandates, with an explicit human sign-off before anything is acted on. **Nothing is cancelled automatically.**
6. **Output** — a dashboard of all subscriptions, spend, renewal dates, and total savings found, exportable to JSON or print/PDF.

## Try it in 30 seconds

Open `subscription-auditor.html` and click **Load sample data → Add this source → Detect subscriptions**. Walk the six steps to see the full flow before using real data.

## Privacy by design

- No network calls — open the browser Network tab and you'll see zero requests.
- No data saved unless the user opts in via *"Remember my data on this device"* (browser local storage, that device only).
- No external libraries or fonts — everything is inline, so it runs fully offline.
