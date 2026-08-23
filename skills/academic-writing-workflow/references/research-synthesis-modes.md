# Research Synthesis Modes

Ten reusable modes for turning a fixed set of papers into structured, citable analysis. Portable across Claude Code, Codex, workspace, and chat.

In a cloned project these map to `docs/literature_analysis_guide.md` (recipes LA-1 – LA-10) and write to `knowledge/analysis/`. In chat, the uploaded files are the corpus and the output stays in the conversation — keep the corpus header so the result can be filed later.

---

## Before any mode: fix the corpus

State this header at the top of every output.

```
Corpus: <source list — evidence.md [1]-[N], or the uploaded filenames> (N papers)
Analysis date: YYYY-MM-DD
Excluded: <paper + reason>
Full text available: M/N — the remainder are analysed from abstract only
```

**Four safeguards apply to every mode.**

| Safeguard | Rule |
|-----------|------|
| Closed corpus | Analyse only these papers. Never add a paper you remember but that is not in the corpus. |
| Scope of absence | `Not found in corpus` means only that. Write `Searched, none found` only after a real search whose query, database, and date you log. Never write "no research exists" from corpus absence alone. |
| Provenance | Tag every item `REPORTED` (author's own statement), `SYNTHESIZED` (across papers), or `INFERRED` (your inference). Hedge `INFERRED` items. |
| Heterogeneity ≠ contradiction | A contradiction requires matching population, outcome definition, and design. Different magnitude in the same direction, or a null result in a smaller study, is heterogeneity. |

Cite every claim with a paper identifier plus a locator where available (`[4, p.312]`, `[4, Results]`). Quote verbatim or not at all; if you cannot locate a passage, write `locator unavailable` rather than inventing a page. Where full text is missing, write `Abstract only — not assessable` instead of estimating.

Run **one mode per pass**. Combining modes degrades source tagging.

---

## Mode 1 — Literature map

```
Analyze ONLY the papers in the corpus about [RESEARCH TOPIC].

Create a literature map showing:
1. Major themes (3-7; name each in five words or fewer)
2. Key findings under each theme
3. Papers that disagree with each other, and on what specific point
4. Papers that agree with each other, and on what specific point

Cite every claim with paper and locator. Mark abstract-only papers. Mark any theme
supported by a single paper as "thin" rather than padding it. List any paper that
fits no theme. Add no information the corpus does not support.
```

Feeds: the manuscript outline, and the list of thin themes needing more references.

---

## Mode 2 — Research gaps

```
Review the corpus on [TOPIC] and identify 5 specific, defensible research gaps.
Do not write "more research is needed."

For each gap state: what is already known (cited), what is still unknown, which papers
reveal the gap (cite the finding or limitation passage), why it matters, and one
research question that could investigate it.

Tag each gap REPORTED (the authors themselves call for this work — quote it),
SYNTHESIZED (several papers together imply it — name at least two), or INFERRED
(your inference from what is absent). For INFERRED gaps write "Not found in corpus",
never "no research exists".

Rank the gaps from strongest to weakest by how directly the corpus supports them.
```

Feeds: the gap statement in the introduction and the paper's key message. A gap that will be written as "no prior study has…" must first be upgraded by a real search.

---

## Mode 3 — Academic debates

```
Analyze the corpus on [TOPIC/QUESTION] and identify the main scholarly disagreements
or competing explanations.

Table columns: Debate | Position A | Evidence for A | Position B | Evidence for B |
Why findings may differ | Papers involved

Pay special attention to differences in methods, samples, locations, time periods,
definitions, and theoretical assumptions that could explain conflicting conclusions.

Include a debate only if the corpus contains at least one paper on each side; mark a
one-paper position as "single-source".
```

Feeds: discussion talking points.

---

## Mode 4 — Evidence synthesis

```
Using only the corpus, synthesize the evidence answering: [RESEARCH QUESTION]

Do not summarize papers one by one. Organize by themes or findings across studies.
For each theme give: the overall conclusion, supporting studies (cited), contradictory
studies (cited), strength of evidence (number of studies, designs, sample sizes,
consistency), and limitations affecting the conclusion.

Finish with a 150-200 word synthesis paragraph suitable as a starting point for a
literature review. Every sentence in it must carry a citation.
```

Strength grades: **Strong** (≥3 studies, consistent design and direction) · **Moderate** (2–3, heterogeneous design, same direction) · **Weak** (1 study, or inconsistent direction) · **Insufficient** (not directly addressed).

The closing paragraph is source material, not manuscript prose — rewrite it under the project's style rules before it enters a draft.

---

## Mode 5 — Methods comparison

```
Compare the methodologies used in the corpus on [TOPIC].

For each study extract: research design, sample/population, sample size, data source,
variables/measures, analysis method, location/context, follow-up duration, and major
methodological limitations.

Then explain which methods are strongest for answering [MY RESEARCH QUESTION], where
methodological weaknesses recur across the corpus, and what methodology would improve
on the existing literature.

Write "not reported" where the paper omits a field and "abstract only" where full text
is unavailable. Never estimate a value.
```

Feeds: justification of the study design, statistical test selection, and the limitations section.

---

## Mode 6 — Contradictions

```
Search the corpus for findings that contradict, challenge, or fail to replicate each
other regarding [TOPIC].

For each, show Study A's conclusion and evidence, Study B's conclusion and evidence,
and plausible methodological or contextual reasons for the difference.

Classify each as:
(a) genuine contradiction — same population, same outcome definition, comparable
    design, opposite result
(b) heterogeneity, not conflict — different populations, definitions, timeframes,
    devices, or conditions
(c) undetermined — the text does not report enough to tell (a) from (b)

Before labelling anything (a), list both studies' population, outcome definition, and
design side by side and show that they match. Effects differing in magnitude but not
direction are not contradictions, and a null result in a small study does not
contradict a significant result in a larger one.
```

Feeds: the discussion passage explaining why this study's findings differ from prior work.

---

## Mode 7 — Theory and framework map

```
Analyze how the corpus uses theories, mechanisms, or conceptual frameworks to explain
[TOPIC].

For each framework: which papers use it, what variables or relationships it explains,
evidence supporting it (cited), evidence challenging it (cited), and its limitations.

Then state which framework is most suitable for studying [MY RESEARCH PROBLEM] and
why, based only on the corpus. If the corpus gives insufficient basis to choose, say
so instead of choosing.
```

Skip this mode for purely descriptive clinical series with no mechanistic or conceptual model.

---

## Mode 8 — Evidence matrix

```
Turn the corpus into a structured research evidence matrix.

Columns: Citation | Research Question | Context/Population | Method | Sample |
Key Variables | Main Finding | Limitations | Relevant Theme | Useful Quote + Locator

Keep each cell concise but specific. Copy numbers exactly — do not round, convert, or
recompute. Quotes must be verbatim with a locator; write "locator unavailable" rather
than inventing one.

After the matrix, identify 3-5 patterns across the studies that matter for the
literature review.
```

Verify by spot-checking at least three quotes against the source; one mismatch means rewriting the whole quote column. This is a working table, not a manuscript table — apply manuscript table formatting only if it becomes a supplement.

---

## Mode 9 — Claim audit

Run after a draft section exists, and again at revision.

**9-A — claim-by-claim**

```
Below is a section of my manuscript. Compare every substantive claim against the corpus.

[PASTE SECTION]

Label each claim: Strongly Supported / Partially Supported / Contradicted /
Not Found in Corpus. Show which paper supports or challenges it, with locator, and
quote the sentence for Strongly Supported and Contradicted labels.

Do not invent citations. A claim you cannot locate is "Not Found in Corpus", never
"probably supported".
```

**9-B — overclaiming scan**

```
On the same section, flag overgeneralizations, unsupported causal claims (association
written as causation), missing counterarguments from corpus papers, and statements
that an additional corpus citation would strengthen — naming which paper.

Do not invent citations. For each flag, propose a corrected sentence that stays within
what the corpus supports.
```

Handling: Strongly Supported → keep · Partially Supported → narrow the claim and hedge · Contradicted → remove or present both sides · Not Found in Corpus → remove, or find and register real evidence. Do not record a QC pass while any `Contradicted` or `Not Found in Corpus` item remains.

---

## Mode 10 — Research questions

```
Based only on the corpus about [TOPIC], generate 10 research questions that logically
extend the existing literature.

Each must originate from an identifiable gap, contradiction, methodological weakness,
neglected population, unexplored variable, or under-tested theory. Name the origin and
cite the papers involved.

For each question give: the evidence behind the opportunity (cited), which papers
reveal it, why it is worth studying, and a suitable research approach (design,
population, primary outcome).

Rank the questions by novelty, feasibility, and strength of justification from the
literature. Score each axis 1-5 and give a one-sentence ranking rationale. Novelty
means novelty within this corpus only — state that limitation in the output.
```

**Gate.** These are candidates, not a research plan. Before a question becomes an analysis plan or a new paper: run an expanded literature search for that specific question, register any new papers found, and obtain the user's confirmation. Corpus-internal novelty is not novelty.

---

## Suggested order

```
Mode 1 (map)
  ├─ Mode 2 (gaps) ────────────┐
  ├─ Mode 3 (debates)          │
  ├─ Mode 6 (contradictions)   ├─ Mode 4 (synthesis) → draft plan → draft
  ├─ Mode 5 (methods)          │
  ├─ Mode 7 (theory)           │
  └─ Mode 8 (matrix) ──────────┘
                                        draft → Mode 9 (claim audit) → QC
                                                Mode 10 (next questions) → gate
```

Minimum set when time is short: **1 → 2 → 8 → 9**.
