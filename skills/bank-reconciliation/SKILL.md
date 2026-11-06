---
name: bank-reconciliation
description: Reconcile a bank statement against the cash ledger (cash book / GL cash account) for a period. Use when the user says "bank rec", "reconcile the bank", "match my statement", "مطابقة البنك", "تسوية بنكية", or uploads a bank statement together with a ledger or cash book export.
---

# Bank Reconciliation

## Purpose
Produce a standard bank reconciliation that explains every difference between the bank balance and the book balance at period end, and lists what needs an adjusting entry.

## Inputs to ask for (only if missing)
1. Bank statement for the period (PDF, CSV or Excel).
2. Cash ledger / GL cash account detail for the same period.
3. Opening reconciled balance, or last month's reconciliation if available.
4. Currency. If more than one currency appears, ask which is the account currency.

## Steps
1. Read both files. Confirm period dates, opening and closing balances on each side. State them before matching.
2. Normalize: dates to one format, amounts as signed numbers (receipts positive, payments negative), trim descriptions.
3. Match in this order, and record which rule matched each pair:
   a. Exact amount + same date.
   b. Exact amount + date within 5 days.
   c. Exact amount + matching reference (cheque no., invoice no., transfer ref.).
   d. One-to-many: one bank line equal to the sum of several ledger lines (or the reverse) with the same reference or same date.
   Never match on amount alone when two or more candidates share that amount; flag them instead.
4. Classify every unmatched item:
   - In bank, not in books: bank charges, interest, direct debits, unrecorded receipts, errors.
   - In books, not in bank: outstanding cheques/payments, deposits in transit, errors.
   - Possible errors: transposed digits (difference divisible by 9), duplicate entries, sign reversals.
5. Build the reconciliation statement:
   - Balance per bank
   - + Deposits in transit
   - − Outstanding payments
   - ± Bank errors
   - = Adjusted bank balance
   - Balance per books
   - + Receipts recorded by bank only (interest, collections)
   - − Charges recorded by bank only
   - ± Book errors
   - = Adjusted book balance
   The two adjusted balances must be equal. If not, show the unexplained difference as its own line. Never force it to zero.
6. Propose adjusting journal entries only for the book-side items (debit/credit, account, amount, description).

## Output
- An Excel file with tabs: Summary (the reconciliation statement), Matched, Unmatched-Bank, Unmatched-Books, Proposed JEs.
- A short summary in chat: closing balances, number of items matched, total unmatched, unexplained difference, and the 3 items that most need attention.

## Rules
- Do not post or invent entries. Proposed JEs are for review only.
- Outstanding items older than 90 days are flagged as stale.
- Show amounts with thousand separators and two decimals.
- Reply in the user's language.
