---
name: variance-analysis
description: Compare actuals against budget, forecast or prior period, apply materiality thresholds, decompose the main drivers (price, volume, mix, timing, one-offs) and draft management commentary tied to the numbers. Use when the user says "variance analysis", "budget vs actual", "BvA", "flux analysis", "explain the variances", "why did we miss", "تحليل الانحرافات", "الفعلي مقابل الموازنة", "تعليق الإدارة على النتائج".
---

# Variance Analysis and Commentary

## Purpose
Explain what moved, why, and what to do about it — in commentary that is traceable to the data and not invented.

## Inputs to ask for (only if missing)
1. Actuals for the period (P&L, or trial balance by account/department).
2. Comparison base: budget, forecast, or prior period / prior year. Ask which one if several are provided.
3. Materiality thresholds. Default: flag a line if the variance is above 10% AND above a fixed amount (ask; for example 5,000 in reporting currency). Both conditions, not either.
4. Drivers if available: units, headcount, prices, customers, FX rates.
5. Notes from department owners. Commentary uses these first.

## Steps
1. Align the two datasets: same accounts, same mapping, same currency, same sign convention. Report any line that exists on one side only.
2. Compute for Month and YTD: Actual, Base, Variance (amount), Variance %. Mark Favourable/Unfavourable correctly (revenue above base = F; cost above base = U).
3. Apply thresholds. Only flagged lines get commentary.
4. For each flagged line, decompose where data allows:
   - Revenue: volume = (Actual units − Budget units) × Budget price; price = (Actual price − Budget price) × Actual units; mix if several products.
   - Costs: rate vs usage, headcount vs cost per head.
   - Timing: costs or revenue moved between months but unchanged for the year.
   - One-offs: non-recurring items, named.
5. Write commentary per flagged line, max 3 sentences:
   what moved (amount, %) → main driver with its number → whether it is timing or permanent → action or owner.
6. Build a bridge from Base result to Actual result (EBITDA or net profit) using the main drivers.

## Output
- Excel: Variance table (Month and YTD) with flags, Driver decomposition, Bridge (waterfall chart), Commentary.
- In chat: a 5-line executive summary — overall result vs base, top 3 drivers, items that are timing only, items that need a decision.

## Rules
- Every sentence of commentary must point to a number in the table or to a note the user provided. If the cause is unknown, write "Cause not identified — ask [owner]". Never invent a reason.
- Do not comment on lines below threshold unless the user asks.
- Avoid filler like "due to various factors".
- Reply in the user's language.
