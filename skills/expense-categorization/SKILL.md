---
name: expense-categorization
description: Categorize raw transactions (bank or card exports, expense lists, petty cash) into chart-of-accounts codes with VAT treatment and a confidence level. Use when the user says "categorize these expenses", "code these transactions", "map to chart of accounts", "تصنيف المصروفات", "ترميز الحركات", or uploads an uncoded transaction list.
---

# Expense Categorization

## Purpose
Turn an uncoded list of transactions into a coded list ready to post or import, with every uncertain line clearly flagged for a human.

## Inputs to ask for (only if missing)
1. The transaction list (CSV, Excel, PDF statement).
2. The chart of accounts (list of account codes and names). If none, offer a standard SME chart and say it is a default.
3. Optional: previously coded transactions or vendor-to-account rules. These take priority over your own judgement.
4. VAT/sales tax regime and rate if VAT treatment is wanted (e.g. KSA 15%, UAE 5%, Türkiye KDV).

## Steps
1. Read the list. Report row count, date range and total value before coding.
2. Clean the payee/description: remove card numbers, terminal IDs, city codes, so the vendor name is clear.
3. Assign an account to each line using this priority:
   a. User-provided vendor rules or history.
   b. Clear vendor identity (e.g. airline → Travel, utility company → Utilities, software subscription → Software).
   c. Description keywords.
   d. Amount pattern (same vendor, same amount, monthly → recurring subscription or rent).
4. Give each line a confidence level:
   - High: rule or history match, or unambiguous vendor.
   - Medium: reasonable inference from description.
   - Low: guess. Write the reason and the question a human must answer.
5. Flag separately:
   - Possible personal expenses on a company account.
   - Possible capital items (single purchase above the capitalization threshold; ask for it, default 1,000 in local currency) that should not be expensed.
   - Duplicates (same vendor, amount and date within 3 days).
   - Transfers between own accounts (not an expense).
6. VAT: if requested, split gross into net and VAT only where the vendor is likely VAT-registered and the item is not exempt. Mark VAT as "to confirm with invoice" — never treat it as recoverable without an invoice.

## Output
- Excel with columns: Date, Original description, Clean vendor, Amount, Account code, Account name, VAT, Net, Confidence, Flag, Question for reviewer.
- A summary tab: totals by account, count of Low-confidence lines, list of flags.
- In chat: 3–5 lines on what needs human review first.
- At the end, offer a vendor-to-account rules table the user can save and reuse next month.

## Rules
- Never create new account codes silently. If nothing fits, use "Suspense / To review" and say why.
- Keep the original description untouched in its own column.
- Reply in the user's language.
