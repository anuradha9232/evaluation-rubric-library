# Evaluation Rubric Library

<p>
  <img src="https://img.shields.io/badge/Markdown-Docs-000000?style=flat-square&logo=markdown&logoColor=white" alt="Markdown" />
  <img src="https://img.shields.io/badge/Rubric-Design-1F4E78?style=flat-square" alt="Rubric Design" />
  <img src="https://img.shields.io/badge/Task%20types-4-2E75B6?style=flat-square" alt="Task types" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License MIT" />
</p>

A working library of **evaluation rubrics** for grading the outputs of large language models (LLMs), plus short guides on how to write rubrics that a human or an LLM judge can apply consistently.

I built this because rubric design is the part of AI-training and model-evaluation work I do most often, and I wanted one clean, reusable reference for it. A rubric is just a checklist of clear, testable criteria that define what a correct, high-quality response looks like. Good rubrics are what make model evaluation *objective* instead of a matter of opinion - which is really a form of quality assurance.

## What's inside

| Folder | What it holds |
|---|---|
| `guides/` | How to write rubrics, and the mistakes I've learned to avoid |
| `rubrics/` | Ready-to-use rubrics for four common task types |
| `templates/` | A blank rubric template to start from |
| `examples/` | A worked example: prompt -> response -> rubric -> scoring |

## The four rubrics

1. **Data-analysis rubric** - for prompts that ask a model to clean data, calculate statistics, and produce a chart.
2. **Spreadsheet-output rubric** - for prompts whose answer must be a structured spreadsheet (tabs, cell values, formatting).
3. **Factual Q&A rubric** - for closed-ended questions with a single correct answer.
4. **Multimodal rubric** - for prompts that take images, audio, or documents as input.

## The core idea I follow

Every rubric here is built on the same principles:

- **Atomic** - each criterion checks exactly one thing.
- **Self-contained** - the judge can score it using only the criterion and the response, without needing the original prompt.
- **Objective** - it can be marked pass/fail without a personal opinion.
- **Positive criteria** reward what a correct answer must contain; **negative criteria** penalise common, predictable mistakes.
- **Weights** reflect importance: accuracy of results matters more than formatting.

The full reasoning is in [`guides/how-to-write-rubrics.md`](guides/how-to-write-rubrics.md). The traps I see most often are in [`guides/common-rubric-mistakes.md`](guides/common-rubric-mistakes.md).

## How to use it

Pick the rubric closest to your task, copy it, and adapt the criteria to your specific prompt. Or start from [`templates/rubric-template.md`](templates/rubric-template.md) and build from scratch. The worked example in [`examples/`](examples/) shows the whole loop end to end.

---

*Written and maintained by Anuradha Rani. These rubrics are general, reusable references written from scratch - they do not reproduce any client's confidential material.*
