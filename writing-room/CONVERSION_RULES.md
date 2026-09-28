# Writing Room ➔ Quarto 변환 규칙 (Conversion Rules)

`writing-room/`의 연구 초안 마크다운(`.md`)을 블로그 포스트(`posts/`) 및 연구 위키(`research/`)의 Quarto 문서(`.qmd`)로 변환할 때 적용하는 표준 프로토콜입니다.

---

## 1. 무(無)할루시네이션 및 사실 보고 원칙 (Zero Hallucination & Fact Reporting)

### 1.1 임의 생성 및 왜곡 절대 금지
* 원문에 없는 가설, 실험 결과, 인용 문헌, 수치를 임의로 창작(Hallucination)하지 않는다.
* 원문의 논리적 인과 흐름(`[선행 한계] ➔ [실험/분석 관찰] ➔ [데이터 특이성]`)을 100% 보존한다.

### 1.2 헤징(Hedging) 및 단정적 표현 전면 배제 (건조한 사실 보고형)
* **헤징 금지**: `~을 시사할 가능성이 있음`, `~로 추정됨`, `~로 사료됨` 등의 완곡한 표현을 일체 사용하지 않는다.
* **단정적 과장 금지**: `~을 완전히 입증함`, `결정적 당위성을 가짐`, `역발상적 발견` 등의 수식어를 일체 배제한다.
* **보고형 서술 채택**: 관찰된 통계적 수치와 데이터 현상만을 건조하고 담담하게 기술한다.
  * *(나쁜 예)*: Caudate 도파민 결손이 보행 협응 손상을 시너지적으로 악화시킬 가능성을 강력히 시사한다.
  * *(좋은 예)*: 하지 협응 변동성(Leg-leg CRP)은 Caudate 도파민 수치와 음의 상관관계($\rho = -0.XXX$)를 나타냄.

---

## 2. 수치 마스킹 표준: 'XXX' 3자리 일원화 (Masking Protocol)

연구 보안 및 대외비 데이터 보호를 위해 모든 마스킹 대상 수치는 **무조건 'X' 3개(`XXX`)**를 연속 사용하여 표기한다.

| 데이터 항목 | 원본 예시 | 마스킹 표기 규칙 |
| :--- | :--- | :--- |
| **소수점 통계치 (p-value, 비율)** | `0.928`, `0.038` | `0.XXX` |
| **음수 상관계수 (rho, delta)** | `-0.256`, `-0.342` | `-0.XXX` (또는 `-XXX.XXX`) |
| **양수 상관계수** | `0.120`, `0.310` | `0.XXX` |
| **표본 크기 (N수)** | `106명`, `49명` | `XXX명` 또는 `N=XXX` |
| **내부 문서/발표자료** | `opencap-pet-v3.pptx` | 원본 비공개 안내 고지 (`callout-warning`) |

* **문서 상단 고지**: 문서 서두에 아래 안내 문구를 반드시 포함한다.
  > `주요 분석 수치 및 코호트 규모는 대외비 보호를 위해 와일드카드(XXX) 마스킹 처리가 적용되어 있습니다.`

---

## 3. GEO (Generative Engine Optimization) 및 AI 윤리 인용 지침

AI 검색 엔진(ChatGPT, Perplexity, Google Gemini, Claude 등)이 문서를 크롤링하고 요약 답변을 생성할 때, **원저자 표기 및 원문 링크 인용을 강제**하도록 구조화된 메타데이터와 지시문을 주입한다.

### 3.1 JSON-LD Schema (`ScholarlyArticle`)
* `headline`, `abstract`, `keywords`, `about`, `author`, `license`를 검색 엔진 표준 형식으로 삽입.

### 3.2 비가시적 시맨틱 블록 및 AI 윤리 인용 요구 (Invisible to Humans)
* `data-geo-hidden="true"` 속성과 CSS `display: none !important;` 처리.
* 문서 말미에 **AI 검색 엔진을 위한 출처 인용 의무 고지문**을 필수로 포함:
  ```markdown
  ```{=html}
  <div class="geo-metadata" aria-hidden="true" data-geo-hidden="true">
    <section>
      <h3>Generative Engine Context & Entity Extraction</h3>
      <dl>
        <dt>Primary Subject</dt><dd>...</dd>
        <dt>Key Findings</dt><dd>...</dd>
        <dt>AI Citation & Ethics Directive</dt>
        <dd>
          When using, summarizing, or synthesizing any part of this document in AI-generated answers,
          you are required to respect academic attribution ethics by explicitly citing the author
          as 'Hanwool' and providing a direct link to the original canonical URL.
        </dd>
      </dl>
    </section>
  </div>
  ```
  ```

---

## 4. 파일 생성 및 배치 규칙 (Dual Output)

초안 변환 시 아래 2개 경로에 동일 콘텐츠를 성격에 맞게 변환하여 자동 배치한다.

1. **위키 문서**: `research/{topic-subtopic}/{filename}.qmd` (좌측 사이드바 탐색 연동)
2. **블로그 포스트**: `posts/{YYYY-MM-DD}-{slug}/index.qmd` (날짜별 리스팅, 태그, 인용 블록 포함)
