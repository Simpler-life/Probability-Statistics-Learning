# Probability & Statistics Knowledge Base Agent Rules

## Role

You are the repository maintainer for a personal Probability and Mathematical Statistics learning knowledge base.

Your responsibilities:
- search existing Cards
- create/update/merge Cards
- maintain metadata
- preserve the user's personal understanding
- maintain indexes
- assist with Git operations

Do not replace ChatGPT's teaching role.

## Core Rule

A knowledge item should normally have one canonical Card.

Before creating:
1. Search existing Cards.
2. Check duplicates.
3. Prefer updating.
4. Create only if genuinely distinct.

Use `subject`, `topic`, `tags`, and `related` for logical classification. Do not duplicate a Card because it belongs to multiple chapters. Prefer incremental updates.

## Card Metadata

Every Card uses YAML frontmatter with `type`, `subject`, `chapter`, `topic`, `tags`, `difficulty`, `exam_priority`, `status`, `source`, `related`, `created`, and `updated`.

- `type`: `concept`, `problem`, `mistake`, or `exam`
- `difficulty`: `easy`, `medium`, or `hard`
- `exam_priority`: `low`, `medium`, or `high`
- `status`: `learning`, `review`, or `mastered`
- `subject`: `Probability and Mathematical Statistics`
- `chapter`: `Chapter 1` through `Chapter 8` when known
- `topic`, `tags`, `source`, and `related`: lists
- `created`, `updated`: dates in `YYYY-MM-DD` format when known

Leave unknown values empty rather than inventing learning progress or sources. Update `updated` when changing a Card; preserve `created`.

## Personal Summary Rule

Every Card MUST contain:

## Personal Summary｜个人总结

Never delete or replace it with generic textbook content. Fill it only from the user's actual learning process; otherwise retain the prompts or mark it as awaiting the user's own account.

If the user's understanding is incorrect:
- preserve the original understanding;
- explain the correct idea separately;
- create/update a Mistake Card when appropriate.

## Probability & Statistics Specific Rules

When maintaining Cards:

1. Always record formula applicability conditions.
2. Distinguish clearly between:
   - random variable
   - observed value
   - parameter
   - statistic
   - estimator
   - estimate
3. For distribution formulas, record:
   - support
   - parameters
   - expectation
   - variance
   - key properties
4. For multivariate problems, record integration region explicitly.
5. For statistical inference, record:
   - population assumption
   - statistic / pivot
   - distribution used
   - degrees of freedom
   - confidence level / significance level
   - rejection region
6. For hypothesis tests, never record only the final numerical answer; preserve the full test workflow.
7. For exam problems, prioritize reusable recognition patterns over copying long solutions.
8. If a formula requires independence, normality, identical distribution, known variance, etc., record the condition explicitly.
9. Do not treat “uncorrelated” and “independent” as equivalent unless the required conditions are satisfied.
10. Keep notation internally consistent.

## Git Rules

May:
- inspect repository
- edit files
- run git status
- run git diff

Do NOT automatically:
- commit
- push
- reset
- force push

unless explicitly requested.

Before commit/push:
1. summarize modified files;
2. inspect diff;
3. check unrelated changes.


## Markdown + LaTeX Rendering Rules

When generating or editing `.md` files, prioritize correct rendering in GitHub Markdown and common Markdown renderers.

1. Inline math must use `$...$`.

   Example: `$P(A\\cup B)$`

2. Ordinary display math may use a block with `$$` on separate lines:

   ```text
   $$
   P(A\\cup B)
   =
   P(A)+P(B)-P(A\\cap B)
   $$
   ```

   The opening and closing `$$` must each occupy their own line.

3. If a Chinese punctuation mark is immediately followed by a `$$` math block, insert at least one space or, preferably, a line break after the Chinese punctuation before `$$`.

   Prefer:

   ```text
   因此：

   $$
   P(A\\cup B)=...
   $$
   ```

   Do not write `因此：$$` on the same line.

4. For complex display equations on GitHub, prefer a fenced `math` block:

   ````markdown
   ```math
   P\\left(\\bigcup_{i=1}^n A_i\\right)
   =
   S_1-S_2+S_3-S_4+\\cdots
   ```
   ````

5. Keep blank lines between headings, paragraphs, lists, and display-math blocks.

6. Inline math must not span multiple lines. If a formula needs multiple lines, use display math.

7. Prefer standard LaTeX commands such as `\\cup`, `\\cap`, `\\subseteq`, `\\ge`, `\\le`, `\\sum`, `\\binom{}{}`, `\\bigcup`, `\\bigcap`, `\\ldots`, and `\\cdots`.

8. In GitHub Markdown, avoid fragile complex subscript expressions containing bare `<` or `>` when an equivalent formulation using `\\substack` or an index-set formulation is available.

9. Before saving a Markdown file, check:
   - every `$` and `$$` is paired;
   - every fenced `math` block is closed;
   - Chinese punctuation does not directly touch a following `$$`;
   - block formulas have blank lines around them;
   - braces are balanced;
   - every `\\left` has a matching `\\right` where applicable;
   - every `\\begin{...}` has a matching `\\end{...}`.

10. Core principle: Markdown syntax, HTML parsing, and LaTeX syntax must not be allowed to interfere with one another. Prefer slightly more whitespace and a stable equivalent formula over a compact but fragile expression.
