---
name: gl-subledger-reconciliation
description: Reconcile general ledger control accounts to their subledgers or supporting schedules (AR aging, AP aging, inventory, fixed assets, payroll liabilities, intercompany, prepaid, accruals) and explain every difference with root cause. Use when the user says "reconcile AR to GL", "GL recon", "balance sheet reconciliation", "subledger doesn't match", "مطابقة الأستاذ العام مع المساعد", "مطابقة حسابات الميزانية", "تسوية الذمم".
---

# GL to Subledger Reconciliation

## Purpose
Prove each balance sheet account is supported, and explain every difference with a cause and a fix.

## Inputs to ask for (only if missing)
1. Trial balance or GL balance for the account(s) at period end.
2. The subledger or supporting schedule at the same date (AR/AP aging, inventory listing, asset register, payroll report, etc.).
3. GL transaction detail for the period (needed to trace differences).
4. Prior period reconciliation, if any.
5. Materiality threshold for investigation. Default: differences above 0.5% of the balance or a fixed amount the user gives.

## Steps
1. Confirm both sides are at the same date and currency. State GL balance, subledger balance, difference.
2. If there is a difference, trace in this order:
   a. Timing / cut-off: transactions in GL dated in the period but in subledger next period, or the reverse.
   b. Manual journals posted directly to the control account (they never hit the subledger). List them.
   c. Unposted or unbatched subledger items.
   d. FX: revaluation in GL but not in subledger, or different rates.
   e. Classification: items in the subledger mapped to a different GL account.
   f. Duplicates and reversals that only hit one side.
   g. Carry-forward: unexplained difference in the prior reconciliation still sitting there.
3. For each reconciling item record: description, amount, category (timing / error GL / error subledger / FX / classification), age, owner, proposed fix (adjusting entry or subledger correction).
4. Review the subledger itself for quality:
   - AR/AP: credit balances in AR, debit balances in AP, items over 90/180/365 days.
   - Inventory: negative quantities, zero-cost items.
   - Intercompany: both sides match in each entity.
5. Status per account: Reconciled / Reconciled with items / Not reconciled.

## Output
- Excel: Summary (one row per account: GL, subledger, difference, explained, unexplained, status), one tab per account with the reconciling items, Proposed adjustments, Quality flags.
- In chat: accounts not reconciled, the largest unexplained amounts, items aged more than 90 days.

## Rules
- Unexplained difference stays visible. Never plug.
- Recurring reconciling items from last period are flagged as "repeat" — they need a permanent fix.
- Proposed adjustments are for review only.
- Reply in the user's language.
