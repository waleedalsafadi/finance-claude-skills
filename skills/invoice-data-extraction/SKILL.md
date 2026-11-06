---
name: invoice-data-extraction
description: Extract structured data from supplier or customer invoices (PDF, scans, photos) into a clean table ready for posting or import, with validation of totals and tax. Use when the user says "extract invoice data", "read these invoices", "enter these bills", "استخراج بيانات الفواتير", "إدخال الفواتير", or uploads one or more invoices.
---

# Invoice Data Extraction

## Purpose
Read invoices and produce one validated row per invoice (and optionally per line item), so nobody retypes them.

## Inputs to ask for (only if missing)
1. The invoices (PDF, image, or a folder of them).
2. Header-only or line-item detail? Default: header-only.
3. Optional: the target import template (ERP/accounting system columns). If given, match its column names exactly.

## Fields to extract (header)
Supplier name, supplier tax number (VAT/TRN/VKN), invoice number, invoice date, due date, currency, subtotal (net), tax amount, tax rate, total, PO number, buyer name, payment terms, bank details (IBAN) if shown.

## Steps
1. For each file, identify the document type: invoice, credit note, proforma, receipt, statement. Only invoices and credit notes go to the main table; list the rest separately.
2. Extract the fields. Dates to YYYY-MM-DD. Amounts as numbers. Credit notes as negative.
3. Validate every invoice:
   - Subtotal + tax = total (tolerance 0.05).
   - Tax amount ≈ subtotal × stated rate.
   - Sum of line items = subtotal (if lines extracted).
   - Due date is after invoice date.
   - Tax number present when tax is charged.
4. Check across the batch:
   - Duplicates: same supplier + same invoice number, or same supplier + amount + date.
   - Same supplier with a different IBAN than on its other invoices. Flag this clearly as a possible fraud risk.
5. Mark any field you could not read clearly as "UNCLEAR" with the file name and page. Do not guess numbers.

## Output
- Excel: tab "Invoices" (one row per invoice + Status column: OK / Check), tab "Lines" (if requested), tab "Exceptions" (each failed check with the reason), tab "Not invoices".
- In chat: number of files read, number OK, number needing a check, and any duplicate or bank-detail warnings first.

## Rules
- Never fill a missing value with an estimate. UNCLEAR is better than wrong.
- Keep the source file name on every row.
- Handwritten or low-quality scans: extract what is readable and say the quality was low.
- Reply in the user's language; keep supplier names as written on the invoice (Arabic or Latin).
