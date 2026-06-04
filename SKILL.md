---
name: generate-test-xlsx
description: Generate `测试条件.xlsx` and final `测试用例.xlsx` from requirement PDFs and developer test-case workbooks. Use when asked to analyze Chinese requirement documents and development test cases to produce workbook-based test conditions, final test cases, or traceable Excel outputs.
---

# Generate Test Xlsx

## Workflow

1. Read the requirement PDF and the developer test-case workbook together.
2. Extract only explicit, testable requirements and design points.
3. Draft `测试条件.xlsx` first, using the standard six-sheet structure in `references/workbook-schema.md`.
4. Then draft the final `测试用例.xlsx` sheet with step-by-step execution rows.
5. Keep traceability notes tied to requirement text or developer cases.
6. Prefer conservative coverage. Do not invent unsupported flows, accounts, or business rules.
7. If the PDF is scanned, inspect page images and use visible text rather than assuming OCR output.
8. Save the files in the current workspace and verify that the workbooks open cleanly.
9. If the user only asks for `测试条件.xlsx`, stop after step 3.
10. For the final test case sheet, vertically merge the case-level columns across the step rows of each case and center the merged content.
11. Format the `案例描述` field as `测试目的：<正文>` followed by a new line with `测试数据：` and any case-specific data lines.
12. Include a `需求` sheet before the SIT/test-case sheet, using the reference template columns and one traceable requirement row.

## Output Rules

- Use Chinese filenames and Chinese workbook content.
- Preserve the established sheet names and column order.
- Put source notes in `说明` or `备注说明` fields when available.
- When a source only supports part of a method, keep the sheet minimal instead of fabricating extra rows.
- For final test cases, keep the first row of each case populated and leave continuation rows blank except for step fields.
- In the final test case workbook, merge the case-level fields in the same visual pattern as the reference template.
- Keep the `案例描述` merged cell left-aligned and wrapped, matching the reference template.
- Name the execution case sheet `SIT` when following the reference template.
