# Step 2 Verification Report — 20260227_EVIDENCE_FINAL (CAIF)

**Date:** 2026-02-27  
**Run:** CAIF per axiom (Lexical, Semantic). Basin from MAY baseline; Feb = stream (8 months later). CaifBatch with --baseline.

## Status: PASS (with note)

### Configuration
- **Baseline:** MAY ctxon coords (identity centroid + covariance from MAY).
- **Stream:** Feb ctxon coords (evaluated in MAY basin).
- **Alpha:** 0.95 | **Lambda:** 1e-6 | **core_ratio:** 0.7.

### Outputs (under 20260227_EVIDENCE_FINAL)
- **Lexical:** caif_lexical — caif_metrics.json, caif_zones.csv
- **Semantic:** caif_semantic — caif_metrics.json, caif_zones.csv

### Lexical CAIF (MAY basin to Feb stream)
- tau_alpha: 1.489 | Centroid (x,y): (0.610, 0.296)
- Feb in basin: Zone A: 1, B: 2, C: 1 | Mean r: 2.39 | Max r: 5.81
- TDR: mean 1.18, max 3.19

### Semantic CAIF (MAY basin to Feb stream) — after proper re-run
- tau_alpha: 1.40 | Centroid (x,y): (0.55, 0.54)
- Feb in basin: Zone A: 4, B: 0, C: 0 | Mean r: 0.26 | Max r: 0.47
- TDR: mean 5.14, max 14.22

**Re-run note:** Semantic pipeline was re-run with tailed inputs (last 2500 chars per line) so Granite receives distinct text per turn; MAY coords then had non-zero variance. Script: run_semantic_rerun_proper.ps1. CAIF semantic was recomputed after the re-run.

**Next:** Step 2.4 — RECP vs CAIF comparison table and supplement (see REPORT_2.4_RECP_vs_CAIF.md).
