# Subscription Auditor — Client Setup Guide

A 10-minute guide to running your subscription audit. No installation, no account, no upload.

---

## What this is

`subscription-auditor.html` is a single file that runs **entirely inside your web browser**. It reads your bank, card, and UPI transaction data, finds every recurring charge, flags the money drains, and shows you exactly what to cancel and how.

**Your data never leaves your computer.** There is no server, no login, and no internet connection required once the file is open. Close the tab and your data is gone (unless you explicitly tick *"Remember my data on this device"*).

---

## Step 1 — Open the tool

1. Save `subscription-auditor.html` anywhere on your computer (Desktop or Downloads is fine).
2. **Double-click it.** It opens in your default browser (Chrome, Edge, Safari, or Firefox — all work).
3. That's it. There is nothing to install.

> Prefer a specific browser? Right-click the file → *Open with* → pick your browser.

---

## Step 2 — Gather your statements

You want **as much history as you can get — 12 months is ideal, 3 months is the minimum.** More history means more accurate cadence detection and price-hike spotting.

| Source | Where to get it | Format |
|---|---|---|
| **Bank account statement** | Net banking → *Accounts → Statement* → export for the last 12 months. Or the mobile app's *Download statement*. | CSV / Excel preferred; PDF works too |
| **Credit / debit card statement** | Card issuer's portal or app → *Statements* → download each month | CSV or PDF |
| **UPI AutoPay / mandates** | Your UPI app (GPay, PhonePe, Paytm, BHIM) → *Autopay / Mandates*, plus your SMS/email debit alerts | Paste the lines directly |

**Why include cards and UPI separately?** Many subscriptions bill a card or a UPI AutoPay mandate, not your bank account directly. If you only load the bank statement, you'll miss them.

---

## Step 3 — Add your data

On the **Add data** screen you have three options — use any or all:

- **Paste** — copy the rows from your statement (or a PDF) and paste into the big box.
- **Upload CSV file** — click *Upload CSV file…* and pick your exported file.
- **Load sample data** — click this first if you just want to see how it works before using your own numbers.

After pasting or uploading:

1. The tool shows a **column check** — it auto-detects which columns are the Date, Description, and Amount. Fix any that look wrong using the dropdowns. The *"Example →"* line shows you a sample row so you can confirm it read correctly.
2. Click **Add this source.** It'll say how many debits it read.
3. Repeat for each statement (bank, then each card, then UPI). They all get audited together.
4. Click **Detect subscriptions →**.

> **Tip on formats:** Dates are read as DD/MM/YYYY (Indian default). The tool only counts **debits** (money going out) and ignores credits/income automatically.

---

## Step 4 — Work through the screens

The tool walks you through six numbered steps along the top:

1. **Add data** — done above.
2. **Review subscriptions** — the cleaned-up list. Merchant names are de-mangled (e.g. `UPI/NETFLIX COM/Payment/HDFC` becomes *Netflix*). **Check anything flagged *"cadence estimated"*** — those are charges seen only once, so the billing frequency is a best guess. You can edit the name, change the cadence, or mark a row as *"not a sub"* right in the table.
3. **Money drains** — the charges worth a second look, ranked by annual rupee cost: price hikes, new subscriptions, duplicate tools, free trials that went paid.
4. **Usage check** *(optional)* — if you run a team, add seat and active-user counts (`Tool, seats paid, active users` — one per line) to find unused seats and dead tools.
5. **Dashboard** — the full picture: monthly spend, annual spend, spend by category, and every subscription with its next renewal date.
6. **Cancel & save** — pick what to cancel. For each one you get step-by-step cancellation instructions, a ready-to-send email, and how to kill the UPI AutoPay / card mandate. **You tick the sign-off box yourself — nothing is ever cancelled automatically.**

---

## Step 5 — Keep the results

- **Download report (JSON)** on the Dashboard saves a structured file of everything found.
- **Print / save as PDF** gives you a clean printout to share with your accountant or team.
- **Download action plan** on the Cancel screen gives you a checklist of what to cancel and how.

These files save to your normal *Downloads* folder.

---

## Privacy — the important part

- **Nothing is uploaded.** Open your browser's developer tools → Network tab while you use it: you'll see zero requests. There is no server to send to.
- **No memory by default.** Refresh or close the tab and the data is cleared.
- **Opt-in saving:** ticking *"Remember my data on this device"* stores it in this browser's local storage **on this computer only** — never anywhere else. Untick it or click *Clear everything* to wipe it.
- Because it's one self-contained file, you can run it on an offline laptop if you want maximum assurance.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| "No debit transactions could be read" | Check the column mapping — make sure the *Amount* column points at the debit/withdrawal column, and *Date* at a real date column. |
| A subscription is missing | Its statement probably isn't loaded. Add the card or UPI source that bills it. |
| Merchant name looks garbled | Edit it directly in the *Review* table — just click the name and type. |
| Cadence looks wrong | The tool flags single-charge guesses as *"cadence estimated."* Change it in the *Review* table dropdown; the annual cost recalculates. |
| Amounts look 100× too big/small | Your statement may use a different decimal format — check the *Amount* column preview before adding. |
| PDF won't paste cleanly | Open the PDF, select just the transaction rows (not headers/footers), copy, and paste. The free-text parser reads one transaction per line. |

---

## FAQ

**Do I need the internet?** Only to receive the file. Running it needs no connection.

**Will it cancel things for me?** No — by design. It drafts the email and lists the exact steps, but you review and act. This keeps you in control and avoids cancelling something you actually need.

**Is my login/banking password involved?** Never. You export statements yourself and feed the tool text. It never touches your bank login.

**Can I run it again next quarter?** Yes — re-export fresh statements and repeat. Running it every quarter is how you catch new creep early.
