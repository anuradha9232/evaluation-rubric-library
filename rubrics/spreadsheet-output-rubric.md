# Rubric: Spreadsheet-Output Task

For prompts whose answer must be a structured spreadsheet — the model has to build tabs, place values in the right cells, and apply formatting. These tasks need extra criteria for structure and layout, not just the numbers.

---

## Task summary

The prompt gives a "Population" spreadsheet of quarterly risk metrics and asks the model to produce a new workbook named "Sample" with two tabs: Tab 1 = the selected sample rows with a flag in column K, Tab 2 = the sample-size calculation. It also asks for a quarter-on-quarter variance column and percentage formatting on that column.

## Prompt type

- [x] Closed-ended (one correct answer)

## Ground-truth answer

- Required sample size (90% confidence, 10% tolerable error): **68**
- Number of rows flagged with "1" in column K: **68**
- Variance column J = (Q3 − Q2) / Q2, formatted as a percentage
- Workbook has exactly two tabs: "Sample" and "Sample Size Calculation"

---

## Positive criteria

| # | Weight | Criterion | Category |
|---|--------|-----------|----------|
| P1 | +30 | Includes a tab named "Sample" (or semantically equivalent). | Instruction-following |
| P2 | +30 | Includes a tab named "Sample Size Calculation" (or semantically equivalent). | Instruction-following |
| P3 | +40 | States that the required sample size is 68. | Accuracy |
| P4 | +35 | Flags exactly 68 rows with the value "1" in column K. | Accuracy |
| P5 | +30 | Includes a variance column that computes (Q3 − Q2) / Q2 for each row. | Accuracy |
| P6 | +15 | Formats the variance column as a percentage. | Formatting |
| P7 | +10 | Uses a live formula for the variance column rather than hard-coded numbers. | Instruction-following |

## Cell-value spot checks

*Used when many rows must be filled; check a few instead of all.*

| # | Weight | Criterion |
|---|--------|-----------|
| S1 | +8 | Reports a variance of 24.0% for the row "CB Cash Italy". |
| S2 | +8 | Reports a variance of -12.5% for the row "PB EMEA UAE". |
| S3 | +8 | Reports a variance of 31.7% for the row "CB Trade Finance Brazil". |

## Negative criteria

| # | Weight | Criterion | Category |
|---|--------|-----------|----------|
| N1 | -40 | Produces a single-tab workbook, missing the required second tab. | Instruction-following |
| N2 | -30 | States a sample size other than 68 (e.g. rounds down instead of up). | Accuracy |
| N3 | -20 | Computes variance as (Q3 − Q2) without dividing by Q2. | Accuracy |
| N4 | -15 | Hard-codes variance values instead of using a formula. | Instruction-following |
| N5 | -10 | Applies currency formatting to the variance column instead of percentage. | Formatting |

---

## Notes

- Spreadsheet tasks need **tab-presence** and **layout** criteria that a plain-text task wouldn't — P1, P2, and N1 exist only because the output format is a workbook.
- Add "or semantically equivalent" to tab/column names when the prompt doesn't fix an exact name.
- The spot checks (S1–S3) replace writing one criterion per row when the sample has dozens of rows.
