# Common Rubric Mistakes to Avoid

These are the errors I check for before submitting any rubric. Each one quietly breaks the consistency a rubric is supposed to give you.

## 1. Wrong wording (not present tense)

Criteria must start in the simple present tense: *States that…, Includes a…, Provides a…, Reports…*.

- Wrong: *"The response must calculate the p-value of p = 0.0001."*
- Right: *"Calculates a p-value of p = 0.0001 for the correlation."*

## 2. Grading the process instead of the result

The customer wants the answer, not a description of the steps.

- Wrong: *"Identifies the `sale_date` column as the one to filter on."*
- Wrong: *"Uses groupby to aggregate the data."*
- Right: *"Reports total Q3 revenue as ₹18,40,000."*

## 3. Criteria that aren't specific enough

A vague criterion can be scored two different ways by two different judges.

- Wrong: *"Calculates the statistics for every category."*
- Right: *"Calculates the mean revenue for the Electronics category as ₹1,94,900."*

## 4. Combined (non-atomic) criteria

One criterion, one idea. Split anything that bundles.

- Wrong: *"Provides the top 3 and bottom 3 products for each region."*
- Right: *"States the top 3 products in the North region are A, B, and C."*
- Right: *"States the bottom 3 products in the North region are X, Y, and Z."*

## 5. Not self-contained (closed questions)

For a closed question, the answer must be inside the criterion.

- Wrong: *"Includes the capital of France."*
- Right: *"States that the capital of France is Paris."*

## 6. Missing examples (open-ended questions)

Even open-ended criteria need concrete examples of what counts as passing.

- Wrong: *"Recommends suitable shoes for a half marathon."*
- Right: *"Recommends long-distance running shoe models such as the Nike Alphafly 3, Saucony Endorphin Pro 4, or Hoka Cielo X1."*

## 7. Missing essential criteria

If the prompt asks for "two different scripts" and the rubric never checks that two were provided, the rubric is incomplete — a wrong response could still pass.

## 8. Repetitive / overlapping criteria

Two criteria testing the same thing double-penalise the same mistake. Keep one, delete the other. This also applies to a positive criterion and its exact negative opposite — don't include both.

- Redundant pair: *"[+5] States the best player is Messi"* and *"[-5] States the best player is not Messi."*

## 9. Subjective criteria

If scoring it requires an opinion about what's "good" or "appropriate," it isn't objective.

- Wrong: *"The response has good formatting."*
- Right: *"The response includes a title."*

## 10. Over-prescriptive or unnecessary style rules

Don't invent requirements the prompt never stated.

- Wrong (prompt didn't ask for it): *"Is formatted as a table for easier reading."*
- Wrong (prompt said "some scripts," not a number): *"Provides exactly 3 scripts."*

## 11. Overfitting and underfitting

- **Overfitting:** a criterion so specific it would reject a valid alternative answer.
- **Underfitting:** a criterion so broad it would pass an incorrect answer.

Criteria may name a specific answer as an *example* ("such as…", "e.g., …") without forcing only that one answer.

## 12. Poor spelling and grammar

The criteria themselves should be clean: capitalised, punctuated, correctly spelled. A sloppy criterion is harder for a judge to apply.

- Wrong: *"the answer must inclde the 4 suits of a poker deck: hearts spades diamonds and clubs"*
- Right: *"Includes the four suits of a poker deck: hearts, spades, diamonds, and clubs."*
