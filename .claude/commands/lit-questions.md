---
description: Derive, justify, and rank next research questions from the corpus (LA-10)
args: topic
---

# Research Question Generation (LA-10)

Topic: **$ARGUMENTS**

## Instructions

Follow `docs/literature_analysis_guide.md` section **LA-10**.

### Step 1: Load inputs

Read `knowledge/evidence.md`, and if present `knowledge/analysis/02_research_gaps.md` and `knowledge/analysis/06_contradictions.md`. Write the corpus header into the output.

### Step 2: Generate 10 questions

Each question must originate from an identifiable **gap, contradiction, methodological weakness, neglected population, unexplored variable, or under-tested theory**. Name the origin and cite the papers involved.

For each question provide:

- Evidence behind the opportunity (cited)
- Which papers reveal it
- Why it is worth studying
- A suitable research approach (design, population, primary outcome)

### Step 3: Rank

Score each question 1–5 on **novelty**, **feasibility**, and **strength of justification from the literature**, then rank. State the ranking rationale in one sentence per question.

Novelty here means novelty **within this corpus only**. Say so explicitly in the output.

### Step 4: Write and gate

1. Write `knowledge/analysis/10_research_questions.md`.
2. Report the top 3.
3. **Gate — do not skip:** state clearly that these questions must not go into `data/analysis_plan.md` or a new paper folder until:
   - an expanded literature search has been run for the specific question (`/search-evidence`, `scripts/search_pubmed.py`),
   - newly found papers are registered in `knowledge/evidence.md`,
   - and the user has confirmed the direction.

Offer to run that expanded search for the top-ranked questions. Do not create `analysis_plan.md` or a new paper subfolder in this command.
