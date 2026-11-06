---
name: fixed-asset-depreciation
description: Build or roll forward a fixed asset register and depreciation schedule (straight-line or reducing balance), including part-period additions and disposals, and produce the monthly depreciation journal. Use when the user says "depreciation schedule", "fixed asset register", "roll forward the FAR", "جدول الإهلاك", "سجل الأصول الثابتة", "احتساب الاستهلاك".
---

# Fixed Asset Depreciation

## Purpose
Give an accurate depreciation charge for the period and a register that ties to the trial balance.

## Inputs to ask for (only if missing)
1. Asset list: description, category, acquisition date, cost, useful life (or rate), residual value, method. Prior accumulated depreciation if the register already exists.
2. Additions and disposals in the period (date, cost, sale proceeds).
3. Period to calculate (month, quarter or year) and the financial year start.
4. Policy choices — confirm, do not assume:
   - Depreciation convention: full month from acquisition month (default), from the following month, or daily.
   - Useful lives by category if not given per asset. Offer typical defaults (buildings 20–50 yrs, vehicles 4–5, IT 3–4, furniture 5–10) and label them as defaults.
   - Tax depreciation needed separately? (Yes/No)

## Steps
1. Validate the register: missing dates, zero cost, residual value above cost, life of zero, assets already fully depreciated.
2. For each asset compute for the period:
   - Straight-line: (Cost − Residual) / Life in months × months in use this period.
   - Reducing balance: Opening NBV × rate × (months in use / 12).
   - Stop at residual value. Never depreciate below it.
   - Land: no depreciation.
3. Disposals: depreciation up to disposal date per convention, remove cost and accumulated depreciation, gain/loss = proceeds − NBV at disposal.
4. Roll forward per category: Opening cost + additions − disposals = closing cost; same for accumulated depreciation; closing NBV.
5. If the user provides the trial balance, tie closing cost and accumulated depreciation by category to the GL. Show any difference.

## Output
- Excel tabs: Register (one row per asset with opening, charge, closing), Roll-forward by category, Disposals (with gain/loss), Journal entries, Assumptions.
- Use formulas in Excel, not hard-coded results, so the user can change a life or date and see the effect.
- Journal: Dr Depreciation expense (by category) / Cr Accumulated depreciation (by category); disposal entry separately.
- In chat: total charge for the period, any tie-out difference, assets that became fully depreciated, and every assumption you used.

## Rules
- State every policy assumption in the Assumptions tab.
- Do not change lives or methods of existing assets without being asked; flag anything that looks unusual instead.
- Reply in the user's language.
