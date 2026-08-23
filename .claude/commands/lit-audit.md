---
description: Audit manuscript claims against the evidence corpus (LA-9)
args: file path or pasted section
---

# Claim Audit (LA-9)

Target: **$ARGUMENTS**

## Instructions

Follow `docs/literature_analysis_guide.md` section **LA-9**. This is the extension of QC Round 2 in `docs/qc_guide.md`.

### Step 1: Load the target and the corpus

1. Read the target section (a file under `drafts/`, or the text the user pasted). If no target is given, ask which section — do not audit the whole manuscript by default.
2. Read `knowledge/evidence.md` and any relevant PDFs/summaries.
3. Read `knowledge/analysis/08_evidence_matrix.md` if it exists — it speeds up locating support.

### Step 2: Claim-by-claim comparison (9-A)

Split the section into substantive claims (one row each). For each claim assign exactly one label:

| Label | Meaning | Required action |
|-------|---------|-----------------|
| Strongly Supported | corpus states it directly | quote the supporting sentence + locator |
| Partially Supported | corpus supports a narrower version | propose a narrowed sentence |
| Contradicted | corpus states the opposite | quote the contradicting sentence |
| Not Found in Corpus | no basis in the corpus | delete, or search and register new evidence |

Never label a claim "probably supported". If you cannot locate it, it is **Not Found in Corpus**.

### Step 3: Overclaiming scan (9-B)

Flag, with a proposed corrected sentence for each:

- Overgeneralizations beyond the evidence
- Association written as causation
- Contradicting corpus papers that the section fails to acknowledge
- Statements that would be stronger with an additional citation — name which corpus entry

Do not invent citations. Apply `docs/writing_guide.md` Hedging Language when narrowing a sentence.

### Step 4: Output

1. Write `knowledge/analysis/09_claim_audit_[section].md` with the corpus header, the claim table, and the overclaiming flags.
2. Record the round in `review/qc_log.md`.
3. Report counts per label.

**Gate:** do not record a QC PASS while any claim is still labelled `Contradicted` or `Not Found in Corpus`. List those items as blocking and propose the fix (delete / narrow / search for evidence via `/search-evidence`).
