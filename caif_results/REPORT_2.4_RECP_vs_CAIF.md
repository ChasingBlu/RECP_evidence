# Step 2.4 — RECP vs CAIF: Comparison Table and Supplement

**Evidence run:** 20260227_EVIDENCE_FINAL  
**Date:** 2026-02-27  
**Purpose:** Publication package — empirical comparison of RECP metrics and CAIF basin metrics (Lexical and Semantic axioms).

---

## 1. Summary table (paper-ready)

| Axiom   | Source        | MAY baseline (ctxon) | Feb (8 mo later) | RECP (Feb ctxon) | CAIF (Feb in MAY basin) |
|---------|---------------|----------------------|------------------|------------------|-------------------------|
| Lexical | Evidence run  | Coords: `lexical_run/coords_3d/may_ctxon_coords_3d.csv` | Coords: `feb_ctxon_coords_3d.csv` | anchors=13, ICS=0.897 (anchor), API=0.63; see `recp_lexical_FEB_ctxon.json` | τ_α = 1.49; Zone A:1 B:2 C:1; mean r = 2.39 |
| Semantic| Evidence run (re-run with tailed inputs) | Coords: `semantic_run/coords_3d/may_ctxon_coords_3d.csv` | Coords: `feb_ctxon_coords_3d.csv` | anchors=13, ICS (anchor), … in `recp_semantic_FEB_ctxon.json` | τ_α = 1.40; Zone A:4 B:0 C:0; mean r = 0.26 |

Semantic was re-run with tailed turn text (last 2500 chars per line) so MAY embeddings are distinct; CAIF semantic then computed from that baseline.

---

## 2. RECP metrics (summary)

RECP outputs are standard JSON per run (MAY/FEB, ctxon/ctxoff). Key fields:

- **ICS** (Identity Consistency Score), **ICS_anchor_centroid** (primary when anchors present), **ICS_pairwise**, **ECR**, **LDI**, **TCDM**, **RDS**, **MPI**, **API**, etc.
- **Embedding source**, **turns_count**, **anchors_count**.

**Anchors (RECP signature):** Every run uses the same anchor files: MAY runs use `CLEAN_MAY_anchors.txt`, FEB runs use `CLEAN_FEBRUARY_anchors.txt`. Lexical runs pass both `--anchors <txt>` and `--anchor-embeddings <jsonl>` (lexical embeddings of those anchors); semantic runs pass `--anchors <txt>` and `--model-dir` (anchors embedded by Granite). Anchors are never ignored; ICS is defined by anchor–centroid consistency when anchors are present.

**Location:**  
- Lexical: `lexical_run/recp_lexical_MAY_ctxon.json`, `recp_lexical_FEB_ctxon.json`, …  
- Semantic: `semantic_run/recp_semantic_MAY_ctxon.json`, `recp_semantic_FEB_ctxon.json`, …

---

## 3. CAIF metrics (summary)

CAIF evaluates **Feb coords** in the **MAY baseline basin** (identity centroid + covariance, τ_α from α-quantile).

- **Lexical:** Basin from MAY lexical ctxon coords; Feb stream → mean/max Mahalanobis, zone counts (A/B/C), TDR. τ_α ≈ 1.49.
- **Semantic:** Basin from MAY semantic ctxon coords; Feb stream → τ_α ≈ 1.40 (after re-run with tailed inputs); all Feb points Zone A; mean r ≈ 0.26.

**Location:**  
- `caif_lexical/caif_metrics.json`, `caif_zones.csv`  
- `caif_semantic/caif_metrics.json`, `caif_zones.csv`

---

## 4. Supplement (reproducibility)

- **Key:** Single `secure_key.bin` in this folder; all RECP steps used this key and `secure_log/`.
- **Inputs:** Visualizer LOCKED — `RUN_MAY/CLEAN_MAY_*`, `RUN_FEBRUARY/CLEAN_FEBRUARY_*` (unchanged).
- **Scripts:** `run_step1_lexical_evidence.ps1` (passes `--anchors` + `--anchor-embeddings` for every RECP call so anchors_count and ICS_anchor_centroid are correct), `run_step1.3_semantic_evidence.ps1`, `run_step2_caif_evidence.ps1`.
- **CAIF:** CaifBatch with `--baseline` MAY ctxon coords, stream = Feb ctxon coords; α = 0.95, λ = 1e-6.
- **Semantic:** Re-run with tailed inputs (run_semantic_rerun_proper.ps1, last 2500 chars per line) so MAY embeddings are distinct; then CAIF semantic is valid (τ_α ≈ 1.40, Feb all Zone A).

---

**End of report.**
