---
name: month-end-close
description: Run and track the month-end close — build the close checklist with owners and deadlines, run completeness, cut-off and tie-out checks on the trial balance, list blockers and produce a close status report and sign-off log. Use when the user says "month-end close", "closing the month", "close checklist", "is the data ready", "close status", "إقفال الشهر", "قائمة الإقفال", "الإقفال الشهري", "هل الأرقام جاهزة".
---

# Month-End Close

## Purpose
Close the books on time with evidence that each step was done and checked, and show what is blocking the close.

## Inputs to ask for (only if missing)
1. Period being closed and the target close day (e.g. working day 5).
2. Trial balance for this period and the prior period.
3. The team: names/roles who own tasks. If none, assign by role (Accountant, Senior, Finance Manager).
4. Status of key inputs: bank reconciliations, AR/AP, payroll, inventory count, fixed assets, intercompany, accruals.
5. Existing close checklist, if the company has one. Use it as the base and add missing steps.

## Steps
1. Build or update the checklist, grouped by day (WD-1 to WD+5) and area:
   - Cut-off: sales and purchase cut-off, goods received not invoiced, unbilled revenue.
   - Cash: all bank accounts reconciled.
   - Receivables / payables: subledgers closed and tied to GL.
   - Payroll and statutory liabilities.
   - Accruals and prepayments posted; prior accruals reversed.
   - Fixed assets: additions, disposals, depreciation run.
   - Inventory: count/valuation, provisions.
   - FX revaluation.
   - Intercompany: matched and eliminated.
   - Tax: VAT return reconciliation, income tax provision.
   - Review: flux analysis, management review, sign-off.
   Each task: ID, task, owner, reviewer, due day, status, evidence link.
2. Run data checks on the trial balance:
   - TB balances (debits = credits).
   - Suspense, clearing and "to be classified" accounts should be zero; list any balance.
   - Accounts with an abnormal sign (e.g. credit balance in cash, debit in revenue).
   - Accounts that moved more than the threshold vs prior month with no explanation.
   - Retained earnings opening = prior year closing.
   - Balance sheet accounts with no reconciliation evidence.
3. List blockers: task, why blocked, who must act, impact if late.
4. Produce the status report.
5. Keep a sign-off log: who approved what, when.

## Output
- Excel: Checklist (filterable by owner and status), TB checks with results, Blockers, Sign-off log.
- In chat: % of tasks done, what is late, top blockers with owner, and a clear statement — "ready for reporting" or "not ready" with reasons.

## Rules
- Do not mark a task done without evidence the user provided or confirmed.
- Never approve the close yourself. Final sign-off belongs to the finance manager or CFO.
- Keep checks factual; no commentary on people.
- Reply in the user's language.
