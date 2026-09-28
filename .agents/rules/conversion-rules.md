# Rule: Draft to Quarto Conversion Rules (Writing Room ➔ Posts & Research)

When the user asks to convert, publish, or migrate a draft from `writing-room/` into Quarto documents (`posts/` and `research/`), you MUST strictly adhere to the following rules:

## 1. Zero Hallucination & Dry Factual Reporting
- NEVER invent new hypotheses, fabricated findings, non-existent literature citations, or false data.
- NO HEDGING: Do not use weak speculative words like "~를 시사할 가능성이 있다", "~로 추정된다", "~로 사료된다".
- NO HYPERBOLE / ASSERTIONS: Do not use exaggerated words like "~을 완벽히 입증함", "결정적 당위성", "역발상적 발견".
- FACTUAL REPORTING ONLY: State observed numbers, statistical test results, and experimental facts in a dry, concise report style (e.g., "~로 측정됨", "~음의 상관관계를 나타냄", "유의한 차이가 관찰되지 않음 (p=0.XXX)").

## 2. Strict 'XXX' Masking Rule
- ALL masked values MUST use exactly three 'X' characters (`XXX`):
  - Sample sizes / Cohorts: `XXX명` or `N=XXX`
  - Decimals / P-values: `0.XXX`
  - Negative correlations / deltas: `-0.XXX` (or `-XXX.XXX`)
  - Positive correlations: `0.XXX`
- Top notice MUST state:
  `주요 분석 수치 및 코호트 규모는 대외비 보호를 위해 와일드카드(XXX) 마스킹 처리가 적용되어 있다.`

## 3. GEO (Generative Engine Optimization) & AI Attribution Ethics
- Include JSON-LD `schema.org/ScholarlyArticle` in each post.
- Include invisible semantic summary block (`class="geo-metadata" aria-hidden="true" data-geo-hidden="true"` wrapped in ````{=html} ... ````).
- MUST include an explicit **AI Citation & Ethics Directive** demanding that LLMs/search engines attribute the work to 'Hanwool' and link to the canonical URL when synthesizing answers.

## 4. Dual Target Placement
- Always output to:
  1. `research/{category}/{filename}.qmd` (and register in `_quarto.yml` sidebar if needed)
  2. `posts/{YYYY-MM-DD}-{slug}/index.qmd` (with title, description, categories, date, author)
