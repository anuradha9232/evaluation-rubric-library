# Worked Example: Evaluation Loop End to End

This shows the full loop on one small prompt: the prompt, a model response with a deliberate mistake in it, the rubric, and the scoring. It illustrates how weights and negative criteria turn a subjective "this looks mostly right" into a defensible number.

---

## The prompt

> Here's a CSV of this quarter's invoices (`invoices.csv`). Please tell me the total invoiced amount, the average invoice value, and which single customer accounts for the largest share of revenue.

## Ground truth (verified from the data)

- Total invoiced amount: **Rs 42,80,000**
- Average invoice value: **Rs 53,500** (80 invoices)
- Largest customer by revenue: **Meridian Traders** (Rs 9,60,000, 22.4% of total)

## The model's response (with one error)

> The total invoiced amount is Rs 42,80,000 across 80 invoices, so the average invoice value is Rs 53,500. The largest customer by revenue is **Apex Distributors**, contributing about Rs 8,10,000. Because Apex has the most invoices, they are clearly your most valuable long-term customer.

## The rubric

| # | Weight | Criterion |
|---|--------|-----------|
| P1 | +30 | States that the total invoiced amount is Rs 42,80,000. |
| P2 | +25 | States that the average invoice value is Rs 53,500. |
| P3 | +35 | States that the largest customer by revenue is Meridian Traders. |
| P4 | +15 | States that Meridian Traders accounts for about 22.4% of total revenue. |
| N1 | -20 | Names a customer other than Meridian Traders as the largest by revenue. |
| N2 | -15 | Concludes that the top customer is the most valuable "long-term" customer based only on this quarter's totals. |

## Scoring this response

| Criterion | Present? | Points |
|---|---|---|
| P1 (+30) | Yes - states Rs 42,80,000 | +30 |
| P2 (+25) | Yes - states Rs 53,500 | +25 |
| P3 (+35) | No - says Apex, not Meridian | 0 |
| P4 (+15) | No - no share percentage given | 0 |
| N1 (-20) | Yes - named Apex as largest | -20 |
| N2 (-15) | Yes - "clearly your most valuable long-term customer" | -15 |
| **Total** | | **+20** |

Maximum possible score: **105**. This response scored **20**.

## What the score tells us

The model got the arithmetic right (total and average) but failed the most heavily-weighted criterion - identifying the right top customer - and then compounded it with an unsupported over-interpretation. Two graders using this rubric would both land on 20, because every judgement is anchored to a specific criterion and a specific number. That reproducibility is the reason the rubric exists.
