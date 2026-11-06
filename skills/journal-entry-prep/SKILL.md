---
name: journal-entry-prep
description: Prepare balanced, documented journal entries (accruals, prepayments, reclassifications, corrections, payroll, recurring entries) from source documents or a description, ready for review and upload. Use when the user says "prepare a journal entry", "book this", "accrue", "reclass", "إعداد قيد", "قيد يومية", "قيد تسوية", "قيد استحقاق".
---

# Journal Entry Preparation

## Purpose
Produce journal entries a reviewer can approve quickly: balanced, correctly classified, with the reason and the evidence attached to each line.

## Inputs to ask for (only if missing)
1. What happened (description) and the supporting document (invoice, contract, payroll sheet, calculation).
2. Chart of accounts. Use the user's account codes exactly.
3. Posting date and period.
4. Entity and currency; exchange rate if foreign currency.
5. Upload template of the accounting system, if the user wants an import file.

## Steps
1. Identify the entry type: accrual, prepayment/deferral, reclassification, correction of error, payroll, depreciation, FX revaluation, intercompany, recurring.
2. Apply the right logic:
   - Accrual: expense or revenue in this period, no invoice yet → include auto-reversal date (first day of next period).
   - Prepayment: paid in advance → asset now, release monthly; build the release schedule.
   - Reclassification: same amount out of one account into another; no P&L effect unless it moves between P&L and balance sheet — say so.
   - Correction: show the original wrong entry and the net correcting entry.
   - Intercompany: both sides, one per entity, with matching amounts and references.
3. Build each entry: line no., account code, account name, debit, credit, cost center/department if used, description, reference.
4. Check before showing:
   - Total debits = total credits.
   - No line has both debit and credit.
   - Accounts exist in the chart provided.
   - Period is correct and not obviously closed.
   - VAT lines only when a valid invoice supports them.
5. Write a one-paragraph memo per entry: why it is needed, how the amount was calculated, which document supports it, and whether it reverses.

## Output
- Entries in a table in chat, and an Excel file with: Entries (in the system import format if given), Calculations, Memo.
- A reviewer checklist at the end: approver, date, document attached (Y/N).

## Rules
- Entries are proposals. Never say an entry was posted.
- If the accounting treatment is a judgement call (e.g. capitalize vs expense, revenue timing), present the options with the effect of each and ask, instead of choosing silently.
- Show your calculation for every computed amount.
- Reply in the user's language.
