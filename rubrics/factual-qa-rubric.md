# Rubric: Factual Q&A Task

For closed-ended questions that have a single correct answer. These rubrics are short, but the discipline is in making each criterion self-contained (the answer must live inside the criterion) and in anticipating the specific wrong answers a model tends to give.

---

## Task summary

A finance-domain question set. Each question has one verifiable answer. The example below uses Indian GST questions because that is a domain I can fact-check confidently.

## Prompt type

- [x] Closed-ended (one correct answer)

## Ground-truth answers

1. Standard GST slabs in India: **0%, 5%, 12%, 18%, 28%**
2. Full form of GSTIN: **Goods and Services Tax Identification Number**
3. Number of digits in a GSTIN: **15**
4. The tax levied on an intra-state supply: **CGST and SGST** (both)
5. The tax levied on an inter-state supply: **IGST**

---

## Positive criteria

| # | Weight | Criterion | Category |
|---|--------|-----------|----------|
| P1 | +20 | States the standard GST slabs in India as 0%, 5%, 12%, 18%, and 28%. | Accuracy |
| P2 | +15 | States that GSTIN stands for Goods and Services Tax Identification Number. | Accuracy |
| P3 | +15 | States that a GSTIN has 15 digits. | Accuracy |
| P4 | +20 | States that an intra-state supply is taxed under both CGST and SGST. | Accuracy |
| P5 | +20 | States that an inter-state supply is taxed under IGST. | Accuracy |

## Negative criteria

| # | Weight | Criterion | Category |
|---|--------|-----------|----------|
| N1 | -15 | States that intra-state supply is taxed under IGST. | Accuracy |
| N2 | -15 | States that inter-state supply is taxed under CGST and SGST. | Accuracy |
| N3 | -10 | Includes a non-existent GST slab such as 10% or 15%. | Accuracy |
| N4 | -8 | States that a GSTIN has a number of digits other than 15. | Accuracy |

---

## Notes

- Notice that P4/P5 and N1/N2 look related but are **not** exact opposites - the negatives capture the specific, common *swap* (intra vs inter), which is a real failure mode, rather than a lazy "not CGST" negation.
- For a closed question, never write "Includes the correct slabs" - always name them, so the judge doesn't need the answer key.
