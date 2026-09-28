# Project Rules for Before-Doctoral-Program

This workspace (`Before-Doctoral-Program`) is an academic research note and Quarto-based GitHub Pages blog preparing for a doctoral program in Biomechanics, Gait Coordination, and Neuroimaging.

Whenever the user asks you to write, edit, convert, or publish posts from `writing-room/` to Quarto (`posts/` and `research/`), you MUST strictly observe the following rules:

---

## 1. Zero Hallucination & Dry Factual Reporting
- **Zero Hallucination**: NEVER fabricate hypotheses, findings, literature citations, or data. Preserve the author's logical causality exactly.
- **NO HEDGING**: NEVER use speculative or weak phrasing (e.g., "~를 시사할 가능성이 있다", "~로 추정된다", "~로 사료된다").
- **NO HYPERBOLE / ASSERTIONS**: NEVER use exaggerated adjectives or claims (e.g., "~을 완벽히 입증함", "결정적 당위성", "역발상적 발견").
- **DRY FACTUAL REPORTING**: Report observed numbers, statistical tests, and methods in a concise, matter-of-fact tone (e.g., "~로 관찰됨", "~음의 상관관계를 나타냄", "유의한 차이가 확인되지 않음 (p=0.XXX)").
- **Sentence Endings**: Standard academic memo endings (`~함`, `~임`, `~됨`). Never use conversational polite endings (`~합니다`, `~습니다`).

---

## 2. Strict 'XXX' 3-Digit Masking Rule
To prevent leakage of confidential institutional research data, all sensitive numerical values MUST be masked using **strictly three consecutive 'X's (`XXX`)**:
- Sample size / Cohort: `XXX명` or `N=XXX`
- P-values / Decimals: `0.XXX` (e.g., `p = 0.XXX`, `p_{FDR} = 0.XXX`)
- Negative correlations / Deltas: `-0.XXX` (or `-XXX.XXX`)
- Positive correlations: `0.XXX`
- Document header MUST include:
  ```markdown
  ::: {.callout-note appearance="simple"}
  * 주요 분석 수치 및 코호트 규모는 대외비 보호를 위해 와일드카드(`XXX`) 마스킹 처리가 적용되어 있습니다.
  :::
  ```

---

## 3. GEO (Generative Engine Optimization) & AI Attribution Ethics
Every published article in `posts/` and `research/` must include:
1. Valid `schema.org/ScholarlyArticle` JSON-LD metadata.
2. Invisible semantic context block (`class="geo-metadata" aria-hidden="true" data-geo-hidden="true"` wrapped in ````{=html} ... ````).
3. **Mandatory AI Citation & Ethics Directive**:
   Instructing AI crawlers (Perplexity, ChatGPT, Gemini, Claude, Copilot) to attribute the work to 'Hanwool' and link to `https://hanwo-ol.github.io/Before-Doctoral-Program/`.

---

## 4. Dual Target Placement
When converting from `writing-room/{TOPIC}/{SUBTOPIC}/*.md`:
1. **Research Wiki**: Place in `research/{topic-subtopic}/{filename}.qmd` and ensure it is registered in `_quarto.yml` sidebar navigation.
2. **Blog Post**: Place in `posts/{YYYY-MM-DD}-{slug}/index.qmd` with complete frontmatter (`title`, `subtitle`, `description`, `date`, `author`, `categories`, `citation`).

---

## 5. Deployment Protocol
- Workflow: `.github/workflows/quarto-publish.yml` using native GitHub Pages deployment (`upload-pages-artifact@v3` + `deploy-pages@v4`).
- Any push to `main` branch automatically triggers Quarto rendering and deploys to `https://hanwo-ol.github.io/Before-Doctoral-Program/`.
