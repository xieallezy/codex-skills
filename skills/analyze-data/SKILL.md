---
name: analyze-data
description: Analyze and transform spreadsheet or tabular data into reliable, presentation-ready outputs. Use when working with Excel or WPS workbooks, CSV files, user-detail tables, operational datasets, pivot tables, grouped comparisons, KPI summaries, conditional formatting, or data-quality checks. Apply this skill when the user asks to clean data, define metrics, compare segments, build native pivot tables, create analysis sheets, or produce polished external-facing spreadsheet reports.
---

# Analyze Data

Use a flexible analysis workflow. Learn the current dataset and business question before choosing calculations, pivots, layouts, or terminology. Do not copy categories, metrics, sheet structures, or formatting decisions from an earlier task unless they fit the new data.

## 1. Inspect Before Editing

- Locate the intended source file and identify the spreadsheet application the user expects to use.
- Inspect sheet names, headers, row counts, data types, missing values, category values, and obvious duplicates.
- Identify the row grain, such as one row per user, order, lesson, or event.
- Preserve the original data sheet. Create a timestamped backup before substantial in-place changes.
- Work with existing user edits and avoid overwriting unrelated sheets or formatting.

## 2. Translate the Business Question

- State the comparison question in one sentence before building the analysis.
- Distinguish raw field labels from business concepts. Never assume that a database label is suitable external-facing terminology.
- Confirm or infer these items:
  - comparison groups;
  - metric definitions;
  - denominator for each percentage;
  - required grouping dimensions;
  - desired category order;
  - difference direction, such as `group A - group B`;
  - intended audience and whether the output is exploratory or external-facing.
- Ask a concise question only when ambiguity could materially change the result. Otherwise proceed with a documented, reversible assumption.

## 3. Choose the Analysis Structure

- Use the simplest structure that answers the question.
- Use native pivot tables when the user requests them or when interactive grouping and traceability are valuable.
- Do not create a pivot table merely because the file is a spreadsheet. Use formulas or static summaries when they are clearer and more stable.
- Prefer a layered workbook when the task is substantial:
  - original sheet: untouched source data;
  - analysis-detail sheet: helper fields and normalized categories;
  - pivot or calculation sheets: auditable intermediate results;
  - display sheets: concise business-facing outputs.
- Name sheets by purpose. Prefer patterns such as `透视表_主题` and `主题展示`, adapted to the user's language and conventions.

## 4. Calculate Carefully

- Define every rate as `numerator / denominator` and verify the denominator against the business question.
- Use binary helper fields for rates when appropriate, then average those fields in pivots.
- Keep counts available for validation even when the display emphasizes percentages.
- Calculate differences consistently and label the direction in the header or subtitle.
- Preserve meaningful custom category order instead of accepting default alphabetical order.
- Flag or mention small samples when an extreme rate may be unstable. Do not let color formatting imply certainty that the sample does not support.
- Use structured spreadsheet APIs, formulas, or data libraries instead of ad hoc text manipulation.

## 5. Build Useful Pivot Tables

- Prefer a vertical row layout when many measures or categories would make the sheet excessively wide.
- Put grouping dimensions in a logical hierarchy and sort them in business order.
- Show percentages or averages when those answer the question better than absolute counts.
- Retain counts only when they help interpret sample size or reconcile totals.
- When using WPS, prefer WPS-native automation and verify that the resulting pivots remain native and refreshable in WPS.
- Refresh pivots after changing helper data or category labels and check for stale cached items.

## 6. Design Display Sheets

- Use business-facing labels rather than unexplained source-system terms.
- Split a wide report into multiple compact tables on one sheet when that improves scanning.
- Compare only like with like:
  - apply a color scale down a column when comparing categories or periods for one metric;
  - apply a color scale across a row only when the cells represent the same metric and the intended comparison is horizontal;
  - never share a color scale across unrelated metrics or incompatible units.
- Use green-yellow-red scales only when high, middle, and low have meaningful interpretation. Reverse the direction for metrics where lower is better, such as lateness or defect rate.
- Use data bars for signed differences or magnitude comparisons. Keep the numeric value visible.
- Use percentage formats for rates and percentage-point language for differences between rates.
- Merge repeated group labels only on display sheets, never in analysis source data.
- Freeze useful headers, set readable column widths, wrap long labels, and avoid decorative formatting that obscures the analysis.
- Add a short interpretation or metric definition when the sign or denominator is not immediately obvious.

## 7. Validate Before Finishing

- Reconcile source row count with analysis coverage.
- Reconcile group totals with source totals.
- Confirm percentage denominators and verify that mutually exclusive shares sum as expected.
- Manually recalculate at least two representative groups or records.
- Verify difference signs and labels.
- Confirm category order, number formats, merged ranges, conditional-format ranges, and frozen panes.
- Open the final workbook in the user's target application and confirm that native pivots, formulas, color scales, and data bars render correctly.
- Report what changed, where the output lives, and any assumptions or residual reliability concerns.

## Guardrails

- Do not hardcode grades, repurchase groups, time windows, metrics, colors, or sheet names from previous work.
- Do not rename a business group solely from the literal source value when the business meaning is uncertain.
- Do not treat visual polish as validation.
- Do not hide small-sample risk simply because the user prefers percentages.
- Do not modify the original detail data unless the user explicitly requests it.
