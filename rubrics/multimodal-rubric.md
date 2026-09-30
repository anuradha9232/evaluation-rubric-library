# Rubric: Multimodal Task

For prompts that take non-text inputs — an image, a scanned document, a PDF, or audio — and ask the model to read information out of them and act on it. The extra risk here is **faithfulness**: the model must report only what is actually in the input, not what it guesses.

---

## Task summary

The prompt attaches a scanned image of a supplier invoice (a PDF/JPG) and asks the model to extract the invoice number, invoice date, taxable amount, GST amount, and total, and return them as a clean table.

## Prompt type

- [x] Closed-ended (one correct answer)

## Ground-truth answer (read from the attached invoice)

| Field | Value |
|---|---|
| Invoice number | INV-2024-0839 |
| Invoice date | 14 March 2024 |
| Taxable amount | ₹84,000 |
| GST amount (18%) | ₹15,120 |
| Total | ₹99,120 |

---

## Positive criteria

| # | Weight | Criterion | Category |
|---|--------|-----------|----------|
| P1 | +30 | Extracts the invoice number as INV-2024-0839. | Accuracy |
| P2 | +25 | Extracts the invoice date as 14 March 2024. | Accuracy |
| P3 | +35 | Extracts the taxable amount as ₹84,000. | Accuracy |
| P4 | +35 | Extracts the GST amount as ₹15,120. | Accuracy |
| P5 | +35 | Extracts the total as ₹99,120. | Accuracy |
| P6 | +15 | Presents the five extracted fields as a table. | Instruction-following |

## Negative criteria

| # | Weight | Criterion | Category |
|---|--------|-----------|----------|
| N1 | -35 | Reports a total that does not equal taxable amount + GST amount (i.e. not ₹99,120). | Accuracy |
| N2 | -30 | Invents a field value that is not legible or not present in the attached invoice. | Faithfulness |
| N3 | -20 | Applies a GST rate other than the 18% shown on the invoice. | Accuracy |
| N4 | -15 | Transposes digits in the invoice number or amounts (e.g. reports ₹48,000 instead of ₹84,000). | Accuracy |

---

## Notes

- N2 is the criterion unique to multimodal work: because the input isn't plain text, models sometimes **hallucinate** a plausible value when a field is blurry. The rubric must penalise "confident but invented" readings.
- N1 is a **consistency check** — the extracted numbers should add up. It catches cases where individual fields are misread but the model doesn't notice they no longer reconcile.
- When the same task is run on audio or a multi-page PDF, keep P-criteria tied to specific extracted values and keep a faithfulness negative like N2.
