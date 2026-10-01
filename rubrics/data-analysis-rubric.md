# Rubric: Data-Analysis Task

For prompts that ask a model to clean a dataset, calculate statistics, and produce a chart. This example is written around a finance dataset so the criteria are concrete; adapt the numbers to your own prompt and verified answers.

---

## Task summary

The prompt gives a CSV of used-car listings with messy price fields (e.g. "Rs 3.5 Lakh", "1.2 Cr"). It asks the model to convert prices to plain rupees, drop rows with missing prices, report the average sale price and the correlation between kilometres driven and sale price, and draw a scatter plot of kilometres vs sale price.

## Prompt type

- [x] Closed-ended (one correct answer)

## Ground-truth answer

- Rows remaining after cleaning: **1,842**
- Average sale price: **Rs 5,21,340**
- Pearson correlation (kms_run vs sale_price): **-0.43**
- Scatter plot: kms_run on x-axis, sale_price on y-axis, clear downward trend

---

## Positive criteria

| # | Weight | Criterion | Category |
|---|--------|-----------|----------|
| P1 | +35 | Converts price strings such as "Rs 3.5 Lakh" to 350000 and "1.2 Cr" to 12000000 in plain rupees. | Accuracy |
| P2 | +30 | States that 1,842 rows remain after dropping rows with missing prices. | Accuracy |
| P3 | +40 | Reports the average sale price as Rs 5,21,340. | Accuracy |
| P4 | +40 | Reports the Pearson correlation between kilometres driven and sale price as -0.43. | Accuracy |
| P5 | +25 | Displays a scatter plot with kilometres driven on the x-axis and sale price on the y-axis. | Instruction-following |
| P6 | +15 | States that sale price tends to decrease as kilometres driven increases. | Reasoning |

## Negative criteria

| # | Weight | Criterion | Category |
|---|--------|-----------|----------|
| N1 | -35 | Treats "Lakh" and "Cr" as the same multiplier, producing prices off by a factor of 100. | Accuracy |
| N2 | -25 | Reports a positive correlation between kilometres driven and sale price. | Accuracy |
| N3 | -20 | Reports the median sale price while labelling it as the average. | Accuracy |
| N4 | -15 | States that higher kilometres driven directly *causes* a lower sale price, presenting correlation as causation. | Reasoning |
| N5 | -10 | Includes rows with missing prices in the average calculation. | Accuracy |
| N6 | -8 | Produces a line chart instead of a scatter plot. | Instruction-following |

---

## Notes

- P3 and P4 carry the highest weights because they are the actual results the user asked for.
- N1 mirrors the most common real failure on Indian price formats - this is exactly the kind of predictable mistake negative criteria exist to catch.
- N4 penalises an over-interpretation (causation) that sounds reasonable but is wrong; it's smaller than the positive reasoning criterion P6.
