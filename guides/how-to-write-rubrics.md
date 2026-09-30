# How to Write a Rubric

A rubric is a checklist of criteria that defines an ideal response to a prompt. When you evaluate a model, you go criterion by criterion and mark each one **pass** or **fail**. A well-written rubric lets two different people — or a person and an LLM judge — reach the same score on the same response. That consistency is the whole point.

This guide is the method I use.

## 1. Start from the prompt, not the answer

Read the prompt and list everything it explicitly asks for, plus the things it implies. Each of those becomes one or more criteria. If the prompt says *"clean the data, report the average sale price, and draw a bar chart,"* that is at least three separate asks — and each ask usually splits into several criteria.

## 2. Write two kinds of criteria

**Positive criteria** describe what a correct answer must contain. These are usually the explicit asks — most often specific numbers or required elements.

> [+35] States that the average sale price is ₹4,52,000.
> [+30] Includes a bar chart with one bar per product category.

**Negative criteria** penalise common, predictable mistakes. You write these after you've seen where models actually go wrong.

> [-20] Reports the median as if it were the mean.
> [-10] Claims a causal link based only on a correlation.

Both are written in **positive, present-tense language** — you describe the element being present, and the *weight's sign* (plus or minus) makes it positive or negative. Do not write "Fails to..." or "Does not...".

## 3. Make every criterion atomic

One criterion checks one thing. If a criterion bundles two ideas, split it.

- Bad: *"Provides the top 3 and bottom 3 products by revenue."*
- Good: *"Provides the top 3 products by revenue: A, B, C."*
- Good: *"Provides the bottom 3 products by revenue: X, Y, Z."*

If a model gets one half right and one half wrong, a bundled criterion can't record that.

## 4. Make every criterion self-contained

The judge should be able to score a criterion using only the criterion text and the response — without the original prompt, the dataset, or outside knowledge. Put the expected answer *inside* the criterion.

- Bad: *"Identifies the first president of the USA."*
- Good: *"Identifies the first president of the USA as George Washington."*

- Bad: *"Reports the correct correlation."*
- Good: *"Reports the Pearson correlation between revenue and market cap as 0.55."*

## 5. Be specific, not vague

Precision is what makes a criterion objective.

- Bad: *"Reports a reasonable number."*
- Good: *"Reports the p-value as p = 0.0001."*

- Bad: *"Has good formatting."*
- Good: *"Includes a title row with column headers."*

## 6. Do not grade the process — grade the result

The customer usually cares about the final answer, not the steps taken to get there.

- Avoid: *"Filters the data to Fridays before averaging."*
- Avoid: *"Uses the formula average = sum ÷ count."*
- Keep: *"States that the average attendance on Fridays is 80%."*

If the prompt only asks for the average, only grade the average.

## 7. Assign weights by importance

Every criterion gets a weight. Accuracy of the actual result should carry the most weight; formatting and phrasing carry less. I use a consistent scale, for example:

| Kind of criterion | Weight range |
|---|---|
| Critical result / core calculation | 26–40 |
| Core factual or method step | 17–25 |
| Clarity or completeness detail | 9–16 |
| Formatting or style | 1–8 |

A negative criterion should never have a larger absolute weight than its matching positive one.

## 8. Cover charts explicitly

If the prompt asks for a plot, the rubric needs criteria for it — separated into what the plot *is* and what it *contains*:

> [+30] Displays a line chart.
> [+20] Shows all six years (2019–2024) on the x-axis.
> [+15] Uses a distinct colour for each product line.

## 9. Handle long lists with spot checks

If the prompt asks for 50+ values in a list, don't write 50 criteria. Spot-check about 20% of them — some from the start, some from the middle, some from the end — plus one criterion for the total count.

> [+10] Includes 22 countries in the output table.
> [+5] Includes an index value of 0.1134 for the Philippines. *(spot check)*
> [+5] Includes an index value of -0.4835 for Spain. *(spot check)*

## 10. Check the whole rubric

Before you finish, confirm the rubric as a whole is:

- **Comprehensive** — covers every explicit ask, no gaps.
- **Non-redundant** — no two criteria test the same thing (that double-penalises).
- **Relevant** — nothing that the prompt didn't ask for.
- **Accurate** — every stated answer is fact-checked and correct.

---

See [`common-rubric-mistakes.md`](common-rubric-mistakes.md) for the specific errors that break these rules.
