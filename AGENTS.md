# AGENTS.md — Academic Paper Writing Project

Entry point for coding agents that do not auto-load `CLAUDE.md` (Codex, Cowork/workspace sessions, and any non-Claude-Code runtime).

**Read `CLAUDE.md` in full before planning, drafting, analysing, or changing workflow files. `CLAUDE.md` is authoritative; this file only explains how to run the same workflow where Claude Code hooks and slash commands are unavailable.**

---

## Non-negotiable rules

1. **Never fabricate** references, statistics, journal requirements, or study findings. `knowledge/evidence.md` is the citation source of truth; do not cite entries that are unverified or still marked `[TODO]`.
2. **No analysis before a plan.** Do not run statistics until `data/analysis_plan.md` exists and the user has approved it (CLAUDE.md Rule 7).
3. **No drafting before a plan.** Do not write manuscript sections until `drafts/draft_plan.md` exists and the user has approved it (CLAUDE.md Rule 8).
4. **Closed corpus.** Literature analysis uses only the registered corpus. Absence from the corpus is not absence from the field (CLAUDE.md Rule 10).
5. **Numbers come from `results/`**, never from memory or recomputation in prose.
6. **Draft order:** Methods → Results → Introduction → Discussion → Conclusion → Abstract → Title.
7. **Human decision points:** gate approvals, submission, external email, data deletion, and publication are the user's call. Prepare the evidence and a draft, then ask.

---

## Phase map

| Phase | What it produces | Gate before moving on |
|-------|------------------|-----------------------|
| 1 Setup | `knowledge/evidence.md`, PDFs, summaries | ≥10 verified references |
| 1.5 Literature Analysis | `knowledge/analysis/*.md` | Corpus header recorded; LA-1, LA-2, LA-8 done |
| 2 Analysis | `data/analysis_plan.md`, `data/py/`, `results/` | Plan approved by user |
| 3 Draft Plan | `drafts/draft_plan.md` | 9 required items complete, user approved |
| 4 Draft | `drafts/0*.md` | Numbers match `results/` and tables |
| 5 Style Polish | same files, polished | `docs/writing_guide.md` rules applied |
| 6 QC | `review/qc_log.md` | ≥3 rounds (6 recommended) |
| 7 Finalize | `output/*.docx` | Versioned filenames, user approved |
| 8 Revision | `drafts/revision/REV{N}/`, `output/revision/REV{N}/` | Response letter matches manuscript edits |

---

## Command mapping (no slash commands available)

| Claude Code command | Equivalent here |
|---------------------|-----------------|
| `/search-evidence [query]` | `python3 scripts/search_pubmed.py search "[query]" --max 20`, then register verified hits in `knowledge/evidence.md` per `docs/evidence_guide.md` |
| `/import-doi [doi]` | `python3 scripts/search_pubmed.py doi [doi]`, then register |
| `/lit-analyze [mode]` | Read `docs/literature_analysis_guide.md`, run the matching LA-N prompt block, write `knowledge/analysis/<file>.md` |
| `/lit-audit [section]` | Run LA-9 (9-A then 9-B), write `knowledge/analysis/09_claim_audit_[section].md`, log in `review/qc_log.md` |
| `/lit-questions [topic]` | Run LA-10, write `knowledge/analysis/10_research_questions.md`, then stop at the expansion gate |

Claude Code hooks in `.claude/settings.json` (if present) do not run in these environments. Perform the equivalent check manually at the point the hook would have fired, and only record a PASS you actually verified.

---

## Phase 1.5 — Literature Analysis

Full recipes: `docs/literature_analysis_guide.md`. Ten modes, run **one at a time**:

| ID | Mode | Output |
|----|------|--------|
| LA-1 | Literature map | `knowledge/analysis/01_lit_map.md` |
| LA-2 | Research gaps | `knowledge/analysis/02_research_gaps.md` |
| LA-3 | Academic debates | `knowledge/analysis/03_debates.md` |
| LA-4 | Evidence synthesis | `knowledge/analysis/04_synthesis_[topic].md` |
| LA-5 | Methods comparison | `knowledge/analysis/05_methods_comparison.md` |
| LA-6 | Contradictions | `knowledge/analysis/06_contradictions.md` |
| LA-7 | Theory / framework map | `knowledge/analysis/07_theory_map.md` |
| LA-8 | Evidence matrix | `knowledge/analysis/08_evidence_matrix.md` |
| LA-9 | Claim audit (after drafting) | `knowledge/analysis/09_claim_audit_[section].md` |
| LA-10 | Research questions | `knowledge/analysis/10_research_questions.md` |

Minimum set when time is short: **LA-1 → LA-2 → LA-8 → LA-9**.

Every output must carry:

- a corpus header (evidence range, paper count, date, exclusions, full-text coverage);
- a source tag on every claim — `[N]`, `[N, p.12]`, or `[N, Section]`;
- a provenance tag on every item — `REPORTED` (author's own words) / `SYNTHESIZED` (across papers) / `INFERRED` (your inference);
- `Not found in corpus` for absence, upgraded to `Searched, none found` only after an actual search logged in evidence.md;
- `Abstract only — not assessable` where full text is unavailable.

Genuine contradictions require matching population, outcome definition, and design. Differing effect size in the same direction, or a null result in a smaller study, is heterogeneity — not a contradiction.

LA-10 questions are candidates only. Before any of them reaches `data/analysis_plan.md`: run an expanded search, register the new papers, and get the user's confirmation.

---

## Verification before claiming completion

- Cross-check every number that appears in more than one place (Abstract ↔ Methods ↔ Results ↔ Tables) — `docs/qc_guide.md` Round 1.
- Check every citation against `knowledge/evidence.md` — Round 2, extended by LA-9.
- Re-run the checks after any change that can make an earlier PASS stale.
- Record what you actually ran in `review/qc_log.md`. Do not record a PASS you did not verify.
