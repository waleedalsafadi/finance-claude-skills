---
name: cash-flow-forecast-13-week
description: Build or update a 13-week direct cash flow forecast from opening cash, AR/AP agings, payroll and recurring commitments, with scenarios and a minimum-cash alert. Use when the user says "cash forecast", "13-week cash flow", "will we run out of cash", "runway", "liquidity plan", "توقع التدفق النقدي", "التدفق النقدي ١٣ أسبوع", "السيولة", "هل تكفي السيولة".
---

# 13-Week Cash Flow Forecast

## Purpose
Show week by week how much cash the company will have, when it gets tight, and which levers move it.

## Inputs to ask for (only if missing)
1. Opening cash by bank account and the forecast start date (a Monday).
2. AR aging (customer, amount, due date) and historical collection pattern if known (e.g. customers pay 15 days late on average).
3. AP aging (supplier, amount, due date) and payment policy.
4. Payroll: amount and pay dates. Social insurance / GOSI / SGK and tax payment dates.
5. Fixed commitments: rent, loans (principal + interest), subscriptions, VAT payments, capex.
6. Expected new sales and their collection terms; any financing inflows.
7. Minimum cash buffer the company wants to keep. Default: 4 weeks of fixed costs; state it as a default.

## Steps
1. Build weekly columns W1–W13 with dates.
2. Receipts:
   - Existing AR: place each invoice in the week it is expected to be collected = due date + average delay. Items over 90 days overdue go to a separate "doubtful" line, not into the base case.
   - New sales: by week with the agreed collection lag.
   - Other: loans, capital, asset sales.
3. Payments: AP by due date (or payment policy), payroll on pay dates, taxes and statutory payments on their legal dates, rent, debt service, capex, other.
4. Closing cash each week = opening + receipts − payments. Opening of next week = closing of this week.
5. Scenarios:
   - Base.
   - Downside: collections slip 2 weeks and new sales −20% (adjust if user gives other assumptions).
   - Upside only if the user asks.
6. Flags: any week below the minimum buffer, any week negative, largest single outflow week.
7. Levers: list concrete actions with cash effect and week (chase top 5 overdue customers, delay non-critical capex, negotiate supplier terms, draw facility). Rank by effect.
8. If last week's forecast is provided, add a variance tab: forecast vs actual per line, and note which assumption was wrong.

## Output
- Excel with formulas: Assumptions, Weekly forecast (Base), Downside, Chart of closing cash vs minimum buffer, Levers, Forecast accuracy (if prior version given).
- In chat: lowest cash point (amount and week) in each scenario, weeks below buffer, top 3 levers.

## Rules
- Cash timing, not accrual: VAT, payroll and loans go in the week the cash leaves.
- Every assumption is written in the Assumptions tab and can be changed in one cell.
- Do not include doubtful receivables in the base case.
- Reply in the user's language.
