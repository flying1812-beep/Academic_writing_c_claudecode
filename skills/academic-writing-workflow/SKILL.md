---
name: academic-writing-workflow
description: Use for medical or academic manuscript projects that need evidence-bound literature synthesis, drafting gates for analysis and draft plans, manuscript QC, or reviewer-response verification. Do not use for a one-off prose edit with no project workflow.
---

# Academic Writing Workflow

A gated, evidence-bound workflow for medical and academic manuscripts. The project template lives at [Academic_writing_c_claudecode](https://github.com/flying1812-beep/academic_writing_c_claudecode).

## Start in a manuscript project

- If the target project contains `AGENTS.md` and `CLAUDE.md`, read `AGENTS.md` and then `CLAUDE.md` in full before planning, drafting, analysing, or changing workflow files. `CLAUDE.md` is authoritative.
- If no project exists, clone the template into an empty directory (`git clone https://github.com/flying1812-beep/academic_writing_c_claudecode.git <target>`), then set topic, target journal, and study design in that project's `CLAUDE.md`.
- Configure the project's own `CLAUDE.md`. Do not edit an installed template clone as a substitute for project configuration.

## Runtime compatibility

Claude Code loads `CLAUDE.md`, `.claude/commands/` (`/search-evidence`, `/import-doi`, `/lit-analyze`, `/lit-audit`, `/lit-questions`), and any hooks in `.claude/settings.json` natively when the project folder is the working directory.

| Surface | How to run this workflow |
|---------|--------------------------|
| Claude Code | Native — slash commands and hooks active |
| Codex / other CLI agents | Read `AGENTS.md`, then `CLAUDE.md`; invoke the documented scripts and prompt blocks explicitly |
| Cowork / workspace | Clone the project; hooks and slash commands do not fire — run `python3 scripts/search_pubmed.py …` and the prompt blocks explicitly |
| claude.ai chat | No persistent filesystem. Upload the source PDFs, use [research-synthesis-modes.md](references/research-synthesis-modes.md) prompt blocks directly, and treat the uploaded files as the corpus |

## Non-negotiable workflow safeguards

- Do not invent citations, statistics, journal requirements, or study findings. `knowledge/evidence.md` is the citation source of truth; never cite entries marked unverified or `[TODO]`.
- Do not run statistical analyses before an approved `data/analysis_plan.md`; do not draft sections before an approved `drafts/draft_plan.md`.
- Draft in order: Methods, Results, Introduction, Discussion, Conclusion, Abstract, Title.
- Use values from `results/` only, and re-check every number that appears in more than one place.
- A gate, submission, external email, data deletion, or publication is a human decision point. Prepare the evidence and a draft, then ask.

## Literature synthesis (Phase 1.5)

Between reference registration and the draft plan, structure the corpus using the ten modes in [research-synthesis-modes.md](references/research-synthesis-modes.md): literature map, research gaps, academic debates, evidence synthesis, methods comparison, contradictions, theory map, evidence matrix, claim audit, and research questions. Read that file before running any of them.

Run one mode at a time and write each result to `knowledge/analysis/`. Minimum set when time is short: map → gaps → matrix → claim audit.

Four safeguards apply to every mode:

1. **Closed corpus.** Analyse only the defined corpus. Never supplement it with papers you remember.
2. **Scope of absence.** `Not found in corpus` ≠ "no research exists." Upgrade to `Searched, none found` only after an actual search whose query, database, and date are logged.
3. **Provenance.** Tag each item `REPORTED` (the authors' own statement), `SYNTHESIZED` (your reading across papers), or `INFERRED` (your inference). `INFERRED` items are hedged, never asserted.
4. **Heterogeneity is not contradiction.** A genuine contradiction requires matching population, outcome definition, and design. Same-direction effects of different magnitude, and null results from underpowered studies, are heterogeneity.

Generated research questions are candidates only. Before one enters `data/analysis_plan.md`, run an expanded literature search, register the new papers, and get the user's confirmation.

## Verification

Run the project's own checks before recording a gate PASS: number consistency across Abstract/Methods/Results/Tables, citation verification against `knowledge/evidence.md` (extended by the claim-audit mode), and the study-type checklist in `docs/checklist_guide.md`. Record only PASS results you actually verified, in `review/qc_log.md`, and re-run checks after changes that can make an earlier PASS stale.
