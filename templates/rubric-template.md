# Rubric Template

Copy this file and fill it in for your own prompt. Delete the notes in *italics* as you go.

---

## Task summary

*One or two sentences: what does the prompt ask the model to do, and what is the final deliverable?*

## Prompt type

- [ ] Closed-ended (one correct answer)
- [ ] Open-ended (several valid answers possible)

## Ground-truth answer

*The verified correct answer(s). For calculations, show the final numbers. This is what your positive criteria are checked against.*

---

## Positive criteria

*What a correct answer must contain. Weights 1-40. Highest weights on accuracy of results.*

| # | Weight | Criterion | Category |
|---|--------|-----------|----------|
| P1 | +__ | States that ... | Accuracy |
| P2 | +__ | Includes a ... | Instruction-following |
| P3 | +__ | Reports ... | Accuracy |

## Negative criteria

*Common, predictable mistakes. Weights -1 to -40. Written in positive language; the minus sign carries the penalty. Never larger in absolute value than the matching positive criterion.*

| # | Weight | Criterion | Category |
|---|--------|-----------|----------|
| N1 | -__ | Reports ... (a known wrong value) | Accuracy |
| N2 | -__ | Claims ... (a common over-interpretation) | Reasoning |

---

## Chart criteria (if the prompt asks for a plot)

| # | Weight | Criterion |
|---|--------|-----------|
| C1 | +__ | Displays a [chart type]. |
| C2 | +__ | Shows [axis / range] on the [x/y]-axis. |
| C3 | +__ | Uses distinct colours/shapes for each [series]. |

---

## Final self-check

- [ ] Every explicit ask in the prompt has at least one criterion.
- [ ] Every criterion is atomic (one idea each).
- [ ] Every criterion is self-contained (answer included, no need for the prompt).
- [ ] Every criterion can be scored pass/fail objectively.
- [ ] No two criteria test the same thing.
- [ ] Weights reflect importance (results > formatting).
- [ ] All stated answers are fact-checked and correct.
