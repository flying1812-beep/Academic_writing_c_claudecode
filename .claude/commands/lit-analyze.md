---
description: Run a literature analysis recipe (map/gaps/debates/synthesis/methods/contradictions/theory/matrix) over the evidence corpus
args: mode [topic]
---

# Literature Analysis (Phase 1.5)

Requested mode: **$ARGUMENTS**

## Instructions

Follow `docs/literature_analysis_guide.md`. It is authoritative — read it before running.

### Step 1: Resolve the mode

| Mode keyword | Recipe | Output file |
|--------------|--------|-------------|
| `map` | LA-1 Literature Review Map | `knowledge/analysis/01_lit_map.md` |
| `gaps` | LA-2 Research Gaps | `knowledge/analysis/02_research_gaps.md` |
| `debates` | LA-3 Academic Debates | `knowledge/analysis/03_debates.md` |
| `synthesis` | LA-4 Evidence Synthesis | `knowledge/analysis/04_synthesis_[topic].md` |
| `methods` | LA-5 Methods Comparison | `knowledge/analysis/05_methods_comparison.md` |
| `contradictions` | LA-6 Contradictions | `knowledge/analysis/06_contradictions.md` |
| `theory` | LA-7 Theory / Framework Map | `knowledge/analysis/07_theory_map.md` |
| `matrix` | LA-8 Evidence Matrix | `knowledge/analysis/08_evidence_matrix.md` |

If no mode is given, ask which one — do not guess. If the user asks for several, run them **one at a time** in the order given in the guide; combining recipes in one pass degrades the source tagging.

### Step 2: Fix the corpus

1. Read `knowledge/evidence.md` — count entries, note the number range.
2. List `knowledge/pdf/` and `knowledge/summaries/` — determine which entries have full text.
3. Multi-paper project: confirm which paper subfolder this analysis belongs to (`knowledge/analysis/paper{N}_xxx/`).
4. Write the corpus header at the top of the output file:

```markdown
> **Corpus:** knowledge/evidence.md [1]–[N] (N papers) + knowledge/pdf/ M files
> **Analysis date:** YYYY-MM-DD
> **Excluded:** [x] (reason)
> **Full-text available:** M/N — remaining entries analysed from abstract only
```

If evidence.md has fewer than 10 registered entries, say so and ask whether to continue or to search more references first (`/search-evidence`).

### Step 3: Run the recipe

Use the prompt block for that recipe in `docs/literature_analysis_guide.md` verbatim, with every `[BRACKET]` placeholder replaced by the actual topic/question. Read the underlying PDFs or summaries for any claim you tag `REPORTED`.

### Step 4: Apply the integrity rules (CLAUDE.md Rule 10)

- Every claim carries `[N]` or `[N, p.12]` / `[N, Section]`
- Every item carries a provenance tag: `REPORTED` / `SYNTHESIZED` / `INFERRED`
- Absence is written as `Not found in corpus` — never as "no research exists"
- Abstract-only entries get `Abstract only — not assessable` in method/limitation fields
- Quotes are verbatim with a locator; if no locator is available, write `locator unavailable`
- No claim from outside the corpus, including well-known papers you remember

### Step 5: Write and report

1. Create `knowledge/analysis/` (or the paper subfolder) if it does not exist.
2. Write the output file with the corpus header.
3. Report to the user: entries analysed, entries excluded, counts by provenance tag, and any theme/gap marked thin or `Not found in corpus` that needs a follow-up search.

Do not draft manuscript text in this command. The output is source material for `drafts/draft_plan.md`, not prose for the manuscript.
