# Literature Analysis 가이드 (v0.1.0)

> 등록된 참고문헌을 **구조화된 분석 산출물**로 전환하는 Phase 1.5 가이드
> Phase 1(문헌 수집·등록)과 Phase 3(draft plan) 사이에서 수행한다.

---

## 개요

evidence.md에 논문을 등록하는 것만으로는 원고를 쓸 수 없다. 등록된 문헌을 **지도화(map) → 갭(gap) → 논쟁(debate) → 모순(contradiction) → 합성(synthesis)** 순으로 구조화해야 Introduction의 gap statement와 Discussion의 비교 논점이 근거를 갖는다.

이 가이드는 그 과정을 10개의 재현 가능한 분석 레시피(LA-1 ~ LA-10)로 정의한다.

```
Phase 1 (evidence 등록)
   ↓
Phase 1.5 (Literature Analysis)  ← 이 가이드
   ├── knowledge/analysis/01_lit_map.md
   ├── knowledge/analysis/02_research_gaps.md
   ├── ...
   └── knowledge/analysis/10_research_questions.md
   ↓
Phase 3 (draft_plan.md)  ← 분석 산출물을 근거로 key message·outline 확정
   ↓
Phase 4 (Draft)          ← Introduction gap, Discussion 비교 논점의 출처
   ↓
Phase 6 (QC Round 2+)    ← LA-9로 draft claim을 corpus에 재대조
```

---

## 대원칙 (Non-negotiable)

> CLAUDE.md **Critical Rule 10 (Literature Analysis Integrity)** 과 동일한 내용이다.

| # | 원칙 | 의미 |
|---|------|------|
| 1 | **Closed-corpus rule** | 분석은 정의된 corpus **안에서만** 수행한다. corpus 밖의 지식(모델의 사전 지식, 기억, 추측)으로 claim을 만들지 않는다. |
| 2 | **Source tag 필수** | 모든 문장에 `[N]` (evidence.md 번호) 또는 `[N, p.12]` / `[N, Discussion]` 형태의 위치 정보를 붙인다. |
| 3 | **Not Found 라벨** | corpus에서 확인되지 않으면 "확인되지 않음"으로 **명시**한다. 비워두거나 일반 지식으로 채우지 않는다. |
| 4 | **인용 조작 금지** | 존재하지 않는 논문·페이지·인용문을 만들지 않는다. 인용문(quote)은 원문에서 **글자 그대로** 옮긴다. |
| 5 | **산출물 ≠ 원고** | `knowledge/analysis/`의 결과물은 원고 초안이 아니라 **재료**다. 그대로 복사해 Introduction/Discussion에 붙여넣지 않는다. |
| 6 | **corpus 고정 기록** | 각 산출물 머리말에 분석 시점의 corpus 범위(evidence 번호 범위, 논문 수, 날짜)를 기록한다. corpus가 바뀌면 재실행한다. |
| 7 | **"없음"의 범위 구분** | corpus에 없다는 것과 학계에 연구가 없다는 것은 다른 진술이다. 아래 표를 따른다. |
| 8 | **출처 유형 표기** | 저자가 직접 쓴 것 / 여러 논문을 묶어 우리가 종합한 것 / 모델의 추론을 구분해 표기한다. |

### 원칙 7 — "없음"을 말하는 법

가장 흔한 문헌 분석 오류는 **corpus에 없는 것을 세상에 없는 것으로 쓰는 것**이다.

| 표기 | 의미 | 원고에서 쓸 수 있는 문장 |
|------|------|--------------------------|
| `Not found in corpus` | 이 분석의 corpus에 없음. 학계 전체는 확인하지 않음. | (그대로는 쓸 수 없음 — 아래 절차 필요) |
| `Searched, none found` | corpus 밖까지 검색(PubMed 등)했고 결과 없음. 검색식·날짜·DB 기록 필요. | "To our knowledge, no study has …" |
| `Reported as absent` | corpus의 논문 저자가 "선행 연구가 없다"고 명시함. | "Previous authors have noted the absence of … [N]" |

**절차:** `Not found in corpus` 항목을 원고의 gap 주장으로 쓰려면 반드시 Phase 1으로 돌아가 실제 검색(`/search-evidence`, `scripts/search_pubmed.py`)을 수행하고, 검색식·검색일·결과 수를 `knowledge/evidence.md`의 Search Log에 기록한 뒤 `Searched, none found`로 승격시킨다. 승격 없이 "no prior study exists" 류의 문장을 쓰지 않는다.

### 원칙 8 — 출처 유형(provenance) 태그

모든 분석 산출물의 각 항목에 다음 중 하나를 붙인다.

| 태그 | 정의 | 검증 방법 |
|------|------|-----------|
| `REPORTED` | 논문 저자가 직접 서술한 내용 | 원문 문장으로 확인 가능해야 함 |
| `SYNTHESIZED` | 여러 논문의 보고를 우리가 묶어 도출한 진술 | 근거 논문 2편 이상이 명시되어야 함 |
| `INFERRED` | 문헌에 없는 것을 근거로 한 추론 (부재 추론 포함) | 원고에서는 hedging 필수, gap 주장으로 쓰려면 원칙 7 절차 |

`INFERRED` 항목은 Discussion에서 단정형으로 쓰지 않는다 (`may`, `might`, `suggests` — writing_guide.md Hedging Language 참조).

---

## Corpus 정의

**Corpus** = 이번 분석에서 근거로 삼는 논문 집합. 분석 시작 전에 반드시 확정한다.

| 표면 (Surface) | Corpus 정의 | 확인 방법 |
|----------------|-------------|-----------|
| Claude Code | `knowledge/evidence.md` 등록 항목 + `knowledge/pdf/` 원문 + `knowledge/summaries/` | evidence.md의 `### [N]` 개수 |
| Codex (AGENTS.md) | 동일 | 동일 |
| Workspace (Cowork) | 동일 (클론된 프로젝트) + 세션에 업로드한 파일 | 업로드 파일은 evidence.md에 먼저 등록 |
| Chat (claude.ai) | 대화에 업로드한 PDF 파일 | 업로드 파일 목록 |

**Corpus 머리말 템플릿** (모든 산출물 최상단):

```markdown
> **Corpus:** knowledge/evidence.md [1]–[24] (24 papers) + knowledge/pdf/ 18 files
> **Analysis date:** 2026-08-23
> **Excluded:** [7] (PDF 미확보, abstract only), [19] (언어 접근 불가)
> **Full-text available:** 18/24 — 나머지 6편은 abstract 기반 분석이므로 신뢰도 낮음으로 표기
```

> **Abstract-only 논문 취급:** full text가 없으면 method/limitation 관련 셀은 `Abstract only — not assessable`로 적는다. 추정해서 채우지 않는다.

---

## Surface Matrix (코드 / 코덱스 / 워크스페이스 / 챗)

같은 레시피를 4개 환경에서 동일한 결과가 나오도록 실행하는 방법.

| 항목 | Claude Code | Codex | Workspace (Cowork) | Chat (claude.ai) |
|------|-------------|-------|--------------------|------------------|
| 규칙 로드 | `CLAUDE.md` 자동 로드 | `AGENTS.md` → `CLAUDE.md` 순으로 읽기 | 세션 시작 시 `CLAUDE.md` 명시적으로 읽기 | `CLAUDE.md`·이 가이드를 Project knowledge로 업로드 |
| 실행 방법 | `/lit-analyze`, `/lit-audit`, `/lit-questions` | 이 가이드의 프롬프트 블록을 그대로 사용 | 프롬프트 블록 사용 (슬래시 커맨드 미작동) | 프롬프트 블록 + PDF 업로드 |
| Corpus 접근 | 파일 시스템 | 파일 시스템 | 파일 시스템 | 업로드 파일만 |
| 산출물 저장 | `knowledge/analysis/*.md` | 동일 | 동일 | 대화 출력 → 사용자가 수동 저장 |
| 검증 | 파일 대조 가능 | 파일 대조 가능 | 파일 대조 가능 | 업로드 원문 내에서만 대조 |
| 제약 | 없음 | 슬래시 커맨드·훅 없음 | 훅 없음 | 파일 영속성·스크립트 실행 없음 |

**표면 공통 규칙**

- 프롬프트의 `[대괄호]` 자리표시자는 실행 전에 **전부** 치환한다. 치환되지 않은 자리표시자가 남은 채로 분석을 실행하지 않는다.
- Chat에서는 산출물 파일 경로가 없으므로, 출력 앞에 corpus 머리말을 반드시 포함시켜 나중에 프로젝트로 옮길 때 추적 가능하게 한다.
- 어떤 표면에서든 **corpus 밖 지식으로 보완하지 않는다**. 모델이 알고 있는 유명 논문이라도 corpus에 없으면 인용하지 않는다.

---

## 산출물 목록

| ID | 레시피 | 산출물 | 주 사용처 |
|----|--------|--------|-----------|
| LA-1 | Literature Review Map | `knowledge/analysis/01_lit_map.md` | draft_plan 개요, Introduction 구조 |
| LA-2 | Research Gaps | `knowledge/analysis/02_research_gaps.md` | Introduction gap statement, 연구 정당화 |
| LA-3 | Academic Debates | `knowledge/analysis/03_debates.md` | Discussion 논점 |
| LA-4 | Evidence Synthesis | `knowledge/analysis/04_synthesis_[topic].md` | Introduction 배경, Discussion 종합 |
| LA-5 | Methods Comparison | `knowledge/analysis/05_methods_comparison.md` | Methods 설계 근거, Limitation |
| LA-6 | Contradictions | `knowledge/analysis/06_contradictions.md` | Discussion 상반된 결과 설명 |
| LA-7 | Theory / Framework Map | `knowledge/analysis/07_theory_map.md` | 개념 틀, Introduction 이론적 배경 |
| LA-8 | Evidence Matrix | `knowledge/analysis/08_evidence_matrix.md` | 모든 섹션 인용 근거, Supplement 후보 |
| LA-9 | Claim Audit | `knowledge/analysis/09_claim_audit_[section].md` | QC Round 2 확장 |
| LA-10 | Research Questions | `knowledge/analysis/10_research_questions.md` | Conclusion future work, 차기 논문 기획 |

> **최소 세트:** 시간이 부족하면 **LA-1 → LA-2 → LA-8 → LA-9** 만이라도 수행한다. 이 4개가 Introduction gap과 인용 신뢰도를 지탱한다.

---

## LA-1. Literature Review Map (문헌 지도)

**목적:** corpus 전체를 주제별로 묶고, 어느 논문이 서로 동의/불일치하는지 한눈에 본다.
**언제:** evidence.md에 10편 이상 등록된 직후, 다른 모든 분석보다 먼저.
**입력:** corpus 전체
**출력:** `knowledge/analysis/01_lit_map.md`

```
Analyze ONLY the papers in the defined corpus (knowledge/evidence.md entries [1]-[N]
and the matching PDFs in knowledge/pdf/) about [RESEARCH TOPIC].

Create a literature map showing:
1. Major themes (3-7 themes; name each theme in 5 words or fewer)
2. Key findings under each theme
3. Papers that disagree with each other, and on what specific point
4. Papers that agree with each other, and on what specific point

For every claim, cite the evidence number and, when a PDF is available, the section
or page (e.g. [4, Results] or [4, p.312]). If a paper is abstract-only, mark it as
"abstract only".

Do not add any information that is not supported by the corpus. If a theme is thin
(supported by only one paper), say so explicitly rather than padding it.
```

**출력 형식**

```markdown
## Theme 1: [테마명]
**Papers:** [2], [5], [11], [14]
**Consensus:** ...  [2, Results], [5, p.88]
**Disagreement:** [11]은 X를 보고했으나 [14]는 반대 [11, Table 2] vs [14, Results]
**Strength:** strong (5 papers, 3 with full text) / thin (1 paper, abstract only)
```

**검증:** 모든 evidence 번호가 evidence.md에 실재하는가 / 어떤 테마에도 속하지 않은 논문이 있는가(있다면 목록으로 남긴다).

---

## LA-2. Research Gaps (연구 갭)

**목적:** "more research is needed" 수준이 아닌, **방어 가능한** 갭 5개를 도출한다.
**언제:** LA-1 이후. draft_plan.md 작성 전 필수.
**입력:** LA-1 산출물 + corpus
**출력:** `knowledge/analysis/02_research_gaps.md`

```
Review the corpus on [TOPIC] and identify 5 specific, defensible research gaps.
Do not write "more research is needed."

For each gap, state:
- What researchers already know (with citations)
- What is still unknown
- Which papers reveal the gap (cite the specific finding or limitation section)
- Why the gap matters clinically or scientifically
- One research question that could investigate it

Rank the gaps from strongest to weakest based on how directly the corpus supports
them. Tag each gap:
- REPORTED — a paper's authors explicitly call for this work (quote the sentence)
- SYNTHESIZED — several papers together imply it (name at least two)
- INFERRED — your inference from what is absent in the corpus

For an INFERRED gap, write "Not found in corpus", not "no research exists". Absence
from this corpus is not evidence of absence in the field.
```

**출력 형식**

```markdown
### Gap 1 — [한 줄 요약]  (rank 1/5, REPORTED)
- **Known:** ... [3], [8]
- **Unknown:** ...  `Not found in corpus` / `Searched, none found (PubMed, 2026-08-23, 0 hits)`
- **Revealed by:** [8, Limitations] "…" (저자 직접 인용), [12, Discussion]
- **Why it matters:** ...
- **Research question:** ...
```

**검증:** REPORTED로 표시된 갭은 원문에 해당 문장이 실재해야 한다. 한 개라도 확인 실패 시 SYNTHESIZED 또는 INFERRED로 강등. 원고에 "no prior study" 류 문장을 쓸 갭은 원칙 7의 승격 절차를 거쳤는지 확인한다.
**연결:** 상위 1–2개 갭이 Introduction의 gap statement와 draft_plan.md의 key message가 된다.

---

## LA-3. Academic Debates (학술적 논쟁)

**목적:** 분야 내 경쟁하는 입장과 그 근거를 대조한다.
**언제:** LA-1 이후, Discussion 구상 전.
**출력:** `knowledge/analysis/03_debates.md`

```
Analyze the corpus on [TOPIC/QUESTION] and identify the main scholarly disagreements
or competing explanations.

Create a table with these columns:
Debate | Position A | Evidence for A | Position B | Evidence for B | Why findings may differ | Papers involved

Pay special attention to differences in methods, samples, locations, time periods,
definitions, and theoretical assumptions that could explain conflicting conclusions.

Only include a debate if at least one paper on each side exists in the corpus. If a
position is represented by a single paper, mark it as "single-source".
```

**검증:** 각 행의 Papers involved가 evidence.md 번호로 채워졌는가 / 양쪽 근거가 corpus 내에 실재하는가.
**연결:** Discussion 논점 3–5개 중 상당수가 여기서 나온다 (draft_plan.md의 Discussion outline).

---

## LA-4. Evidence Synthesis (근거 합성)

**목적:** 논문을 한 편씩 요약하지 않고 **주제 단위로** 근거를 합성한다.
**언제:** LA-1~LA-3 이후, Introduction/Discussion 초안 직전.
**출력:** `knowledge/analysis/04_synthesis_[topic].md`

```
Using only the corpus, synthesize the evidence answering this question:
[RESEARCH QUESTION]

Do NOT summarize papers one by one. Organize the response by themes or findings
across studies.

For each theme, give:
- The overall conclusion supported by the corpus
- Supporting studies (cite)
- Contradictory studies (cite)
- Strength of evidence (number of studies, designs, sample sizes, consistency)
- Important limitations affecting the conclusion

Finish with a 150-200 word synthesis paragraph suitable as a starting point for a
literature review. Every sentence in that paragraph must carry a citation tag.
```

**Strength of evidence 등급 (이 프로젝트 기준)**

| 등급 | 기준 |
|------|------|
| Strong | 3편 이상, 설계 일관, 결과 방향 일치 |
| Moderate | 2–3편, 설계 이질적이나 방향 일치 |
| Weak | 1편, 또는 결과 방향 불일치 |
| Insufficient | corpus에서 직접 다루지 않음 |

**검증:** 마지막 문단은 **초안이 아니라 재료**다. Phase 4에서 writing_guide.md 규칙을 적용해 다시 쓴다.

---

## LA-5. Methods Comparison (방법론 비교)

**목적:** 선행 연구의 설계를 표로 비교해, 우리 연구 설계의 정당화 근거와 Limitation 대응 논리를 확보한다.
**언제:** Phase 2(analysis_plan.md) 작성 전이면 더 좋다.
**출력:** `knowledge/analysis/05_methods_comparison.md`

```
Compare the methodologies used in the corpus on [TOPIC].

Extract for each study: research design, sample/population, sample size, data source,
variables/measures, analysis method, location/context, follow-up duration, and major
methodological limitations.

Then explain:
- Which methods appear strongest for answering [MY RESEARCH QUESTION]
- Where methodological weaknesses repeatedly occur across the corpus
- What methodology could improve on the existing literature

For any field you cannot fill from the available text, write "not reported" (if the
paper omits it) or "abstract only" (if full text is unavailable). Never estimate.
```

**연결:** `data/analysis_plan.md`의 검정법 선택 근거, `drafts/06_discussion.md`의 Limitation 대응, Methods의 설계 정당화.

---

## LA-6. Contradictions (모순 탐지)

**목적:** 서로 재현되지 않거나 반대되는 결과를 찾아, **진짜 모순**과 **조건이 다른 연구**를 구분한다.
**언제:** LA-1 이후. LA-3(논쟁)과 짝으로 수행.
**출력:** `knowledge/analysis/06_contradictions.md`

```
Search the corpus for findings that contradict, challenge, or fail to replicate each
other regarding [TOPIC].

For every contradiction, show:
- Study A's conclusion and the evidence it used
- Study B's conclusion and the evidence it used
- Plausible methodological or contextual reasons for the difference

Clearly distinguish between:
(a) a genuine contradiction — same population, same outcome definition, comparable
    design, opposite result
(b) heterogeneity, not conflict — different populations, definitions, timeframes,
    devices, or conditions; the studies answer different questions
(c) undetermined — the text does not report enough to tell (a) from (b)

Before labelling anything (a), list the population, outcome definition, and design of
both studies side by side and show that they match. Effect sizes that differ in
magnitude but agree in direction are not contradictions. A non-significant result in a
small study does not contradict a significant result in a larger one; report it as
heterogeneity in power.

Cite the relevant papers and sections. Do not manufacture a contradiction from
differences in wording alone.
```

**검증:** (a)로 분류된 항목은 outcome 정의·population·설계가 실제로 동일한지 원문에서 나란히 확인한다. 확인 불가 시 (c) `undetermined`로 내린다. 방향이 같고 크기만 다른 결과, 표본이 작아 유의하지 않은 결과는 모순이 아니라 이질성으로 분류한다.
**연결:** Discussion에서 "our findings differ from X because…" 논리의 근거.

---

## LA-7. Theory / Framework Map (이론·개념틀 추적)

**목적:** corpus가 사용하는 이론·모델·개념틀을 정리하고, 우리 연구에 맞는 틀을 고른다.
**적용 대상:** 기전(mechanism) 가설·분류체계·개념 모델이 있는 연구. 순수 기술적(descriptive) 임상 시리즈에서는 생략 가능.
**출력:** `knowledge/analysis/07_theory_map.md`

```
Analyze how the corpus uses theories, mechanisms, or conceptual frameworks to explain
[TOPIC].

Identify each major theory/model/framework and give:
- Which papers use it
- What variables or relationships it explains
- Evidence supporting it (cite)
- Evidence challenging it (cite)
- Its limitations

Then state which framework appears most suitable for studying
[MY SPECIFIC RESEARCH PROBLEM] and why, based only on the corpus. If the corpus
does not contain enough basis to choose, say so instead of choosing.
```

---

## LA-8. Evidence Matrix (근거 매트릭스)

**목적:** corpus 전체를 한 장의 구조화된 표로 만든다. 인용 시 매번 원문을 다시 뒤지지 않게 하는 **작업 테이블**.
**언제:** LA-1 이후 어느 시점이든. 논문 수가 15편을 넘으면 사실상 필수.
**출력:** `knowledge/analysis/08_evidence_matrix.md`

```
Turn the corpus into a structured research evidence matrix.

Columns:
Citation | Research Question | Context/Population | Method | Sample | Key Variables |
Main Finding | Limitations | Relevant Theme | Useful Quote/Passage + Page

Keep each cell concise but specific. Numbers must be copied exactly from the source;
do not round, convert, or recompute. Quotes must be verbatim, in quotation marks, with
a page or section locator. If a locator is unavailable, write "locator unavailable"
and do not invent a page number.

After the matrix, identify 3-5 patterns across the studies that matter for the
literature review.
```

**형식 주의**

- Citation 열은 `[N] First-author Year` 형식으로 evidence.md 번호와 **반드시** 연결한다.
- 표가 지나치게 넓어지면 `Citation | Method | Sample | Main Finding | Theme` 핵심 5열 요약본을 별도로 만든다.
- 이 매트릭스는 원고 Table이 아니다. Supplement로 낼 경우에만 docx_guide.md 서식을 적용한다.

**검증:** 인용문(quote)은 무작위로 3개를 골라 원문 대조한다. 하나라도 불일치하면 전체 quote 열을 재작성한다.

---

## LA-9. Claim Audit (초안 주장 감사)

**목적:** 작성된 원고 문장을 corpus에 되돌려 대조한다. **Phase 6 QC Round 2의 확장판**.
**언제:** Introduction/Discussion 초안 완료 직후, 그리고 revision 시 재수행.
**출력:** `knowledge/analysis/09_claim_audit_[section].md`

**9-A. 주장별 근거 대조**

```
Below is a section of my manuscript. Compare every substantive claim against the corpus.

[PASTE SECTION TEXT]

For each claim, label it:
- Strongly Supported — corpus states it directly
- Partially Supported — corpus supports a narrower or related version
- Contradicted — corpus states the opposite
- Not Found in Corpus — no basis in the corpus

Show which paper supports or challenges each claim, with page or section where
possible. Quote the supporting sentence when the label is Strongly Supported or
Contradicted. Do not invent citations. A claim you cannot locate is
"Not Found in Corpus", never "probably supported".
```

**9-B. 과잉 주장 탐지**

```
On the same section, flag:
- Overgeneralizations (claims broader than the evidence supports)
- Unsupported causal claims (association written as causation)
- Missing counterarguments (contradicting corpus papers that are not acknowledged)
- Statements that would be stronger with an additional citation, naming which corpus
  paper could be added

Do not invent citations. For each flag, propose a corrected sentence that stays within
what the corpus supports.
```

**처리 규칙**

| 라벨 | 조치 |
|------|------|
| Strongly Supported | 인용 번호 확인 후 유지 |
| Partially Supported | 문장 범위를 근거에 맞게 축소 (hedging 적용, writing_guide.md 참조) |
| Contradicted | 삭제하거나 반대 근거를 함께 제시 |
| Not Found in Corpus | 삭제, 또는 Phase 1로 돌아가 근거 논문을 확보 후 재작성 |

**연결:** 결과를 `review/qc_log.md` Round 2 항목에 기록한다. `Not Found in Corpus`가 남은 채로 QC PASS를 기록하지 않는다.

---

## LA-10. Research Questions (차기 연구 질문 도출)

**목적:** corpus에서 논리적으로 확장되는 연구 질문을 만들어 Conclusion의 future work와 차기 논문 기획에 쓴다.
**언제:** LA-2·LA-6 이후. 논문 마무리 단계 또는 다음 과제 기획 시.
**출력:** `knowledge/analysis/10_research_questions.md`

```
Based only on the corpus about [TOPIC], generate 10 research questions that logically
extend the existing literature.

Each question must originate from an identifiable: gap, contradiction, methodological
weakness, neglected population, unexplored variable, or under-tested theory.
Name which of these six origins applies, and cite the papers involved.

For each question, provide:
- The evidence behind the opportunity (cite)
- Which papers reveal it
- Why it is worth studying
- A suitable research approach (design, population, primary outcome)

Then rank the final questions by novelty, feasibility, and strength of justification
from the literature. Give each a 1-5 score on the three axes and state the ranking
rationale in one sentence.
```

**연결:** 상위 2–3개는 `drafts/07_conclusion.md`의 future direction 문장 근거. 멀티 논문 기획 시 `paper2_yyy` 후보가 된다.

**게이트 (중요):** LA-10의 질문을 **그대로 `analysis_plan.md`의 연구 질문으로 넘기지 않는다.** corpus는 이 논문을 위해 모은 것이라 차기 주제를 대표하지 않는다. 다음 순서를 반드시 거친다.

1. 후보 질문에 대해 **확장 문헌 검색**을 새로 수행한다 (`/search-evidence`, `scripts/search_pubmed.py`) — 이미 답이 나와 있는 질문인지 확인
2. 새로 확보한 논문을 `knowledge/evidence.md`에 등록한다
3. 질문·근거·설계 초안을 사용자에게 제시하고 **확인을 받는다**
4. 승인된 질문에 한해 Phase 2(`analysis_plan.md`) 또는 신규 프로젝트로 진행한다

> "novelty 5점"은 corpus 내 신규성일 뿐이다. 확장 검색 전에는 신규성을 단정하지 않는다.

---

## 권장 실행 순서

```
LA-1 (map)
  ├─→ LA-2 (gaps) ──────────┐
  ├─→ LA-3 (debates)        │
  ├─→ LA-6 (contradictions) ├─→ LA-4 (synthesis) ─→ draft_plan.md (Phase 3)
  ├─→ LA-5 (methods)        │
  ├─→ LA-7 (theory)         │
  └─→ LA-8 (matrix) ────────┘
                                    ↓
                            Phase 4 (Draft)
                                    ↓
                            LA-9 (claim audit) → QC Round 2
                                    ↓
                            LA-10 (next questions) → Conclusion / 차기 논문
```

**한 번에 한 레시피.** 여러 레시피를 한 프롬프트에 합치면 근거 태그가 뭉개진다.

---

## draft_plan.md 연동

Phase 3에서 `drafts/draft_plan.md`를 쓸 때 아래 항목은 분석 산출물을 **직접 인용**한다.

| draft_plan.md 항목 | 출처 |
|--------------------|------|
| Key message | LA-2 rank 1 gap |
| Essential references | LA-8 evidence matrix에서 선별 |
| Evidence gap (추가 검색 필요) | LA-1에서 "thin"으로 표시된 테마 |
| Introduction outline | LA-1 테마 구조 + LA-2 gap |
| Discussion outline | LA-3 debates + LA-6 contradictions |
| Limitation points | LA-5 반복 취약점 |

---

## Multi-paper 프로젝트

corpus(`knowledge/`)는 공유하되, 분석 산출물은 논문별로 분리한다.

```
knowledge/
├── evidence.md               ← 공유
├── pdf/                      ← 공유
├── summaries/                ← 공유
└── analysis/
    ├── paper1_infection/     ← 논문1 분석 산출물
    │   ├── 01_lit_map.md
    │   └── 02_research_gaps.md
    └── paper2_outcomes/
        ├── 01_lit_map.md
        └── 02_research_gaps.md
```

같은 corpus라도 연구 질문이 다르면 테마·갭이 달라지므로 **논문별로 재실행**한다.

---

## Phase 1.5 완료 체크리스트

- [ ] corpus 머리말이 모든 산출물에 기록되어 있다 (범위·날짜·제외 논문)
- [ ] 최소 세트(LA-1, LA-2, LA-8)가 완료되었다
- [ ] 모든 claim에 evidence 번호가 붙어 있다
- [ ] evidence.md에 없는 번호를 인용한 곳이 없다
- [ ] abstract-only 논문의 method/limitation 칸이 추정으로 채워지지 않았다
- [ ] LA-8의 quote 중 최소 3개를 원문 대조했다
- [ ] LA-2의 EXPLICIT 갭이 원문 문장으로 확인되었다
- [ ] LA-1에서 "thin"으로 표시된 테마가 draft_plan.md의 Evidence gap에 반영되었다
- [ ] 모든 항목에 provenance 태그(REPORTED / SYNTHESIZED / INFERRED)가 붙어 있다
- [ ] `Not found in corpus`를 `Searched, none found`로 쓴 곳이 없다 (승격 절차를 거친 항목만 허용)
- [ ] LA-6에서 genuine contradiction으로 분류한 항목의 population·outcome 정의가 대조 확인되었다
- [ ] LA-10 질문을 analysis_plan.md로 넘기기 전 확장 검색과 사용자 확인을 거쳤다
