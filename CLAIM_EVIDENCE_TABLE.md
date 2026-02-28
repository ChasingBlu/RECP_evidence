CB03420260228
# Claims ↔ Evidence Table (Final Locked Package)
# Source: evidence/ — 20260220_Final_Evidence_Locked (RECP_Publication_Package_20260220)
# Lock date: 2026-02-20

| Claim ID | Claim | Evidence Files | Status | Notes |
|----------|-------|----------------|--------|-------|
| C1 | May ctx-on mean distance = **0.3763** | identity_baseline/may_ctxon_summary.json | Supported | Mean distance reported. |
| C2 | Feb ctx-on mean distance = **0.1188** | identity_baseline/feb_ctxon_summary.json | Supported | Mean distance reported. |
| C3 | Reduction May→Feb (distance) = **~68.4%** | may_ctxon_summary.json, feb_ctxon_summary.json | Supported | Computed from means. |
| C4 | 95% CI non-overlap (May ctx-on vs Feb ctx-on) | identity_baseline/bootstrap_ci_95.json | Supported | CIs do not overlap. |
| C5 | Bootstrap resamples = **10,000** (seed 42) | identity_baseline/bootstrap_ci_95.json | Supported | Explicit in file. |
| C6 | Feb ctx-off mean distance = **0.3064** | identity_baseline/feb_ctxoff_summary.json | Supported | Mean distance reported. |
| C7 | Random Gaussian baseline mean = **1.126** | identity_baseline/random_gaussian_summary.json | Supported | Mean distance reported. |
| C8 | Centroid computed from May ctx-on coords | identity_baseline/identity_centroid.json, may_ctxon_distances.csv | Supported | Method + centroid stored. |
| C9 | PCA basis fixed on May; min-max scaling uses May | baseline_manifest.json, LOCK_MANIFEST.txt | Supported | Explicit in manifest. |
| C10 | Distances + distributions | identity_baseline/*_distances.csv | Supported | Per-turn distances. |
| C11 | Quantum/Schrödinger isomorphism | — | Not supported | No empirical evidence in package. |
| C12 | Conservation error < 1e-6 | conservation/conservation_report.json, norm_audit.csv | Supported | norm_error_max/mean in report. |
| C13 | Cross-architecture replication | — | Not supported | No standardized replication artifacts. |
| C14 | Centroid-referenced energy U reduction (CAIROS_Seshat) | centroid_energy_runs_20260221/centroid_comparison_summary.csv, feb_vs_may_centroid/, IDENTITY_CENTROID_COMPARISON.md | Supported | may_ctxon 31.2%, feb_ctxon 38.7%, feb_ctxoff 63.0% (u_centroid t=0→t=99). |
| C15 | CN Hermitian energy conservation (real‑time, Hermitian H) | cn_hermitian_runs_20260222/cn_hermitian_300steps_may_frames_20260222/cn_audit_report.json, cn_audit.csv, cn_residual.csv; cn_hermitian_runs_20260223/cn_hermitian_50steps_unreal_may_20260223_155750/cn_audit_report.json, cn_audit.csv, cn_invariance.csv | Supported | Triad‑scaled tolerance; unitarity + hermiticity pass; energy drift within scaled threshold. 2026‑02‑23 run verifies same conservation under Unreal‑operational conditions (local transport only). |
| C16 | CN Hermitian C1/C2 delta (May vs Feb coords) | cn_hermitian_runs_20260222/cn_c1_c2_delta.json, cn_c1_c2_delta.csv | Supported | Δ(C2−C1): centroid distance, norm deviation, energy drift. |

All paths relative to evidence package.


​‌​​​​‌‌​‌​​​​‌​​‌​‌‌​‌​​‌​‌​‌‌‌​​​​​​​​​​​​​​​​​​​​​​​​​​‌‌‌​‌‌‌​‌​‌​‌​‌​‌‌‌‌‌​​‌‌​​​‌​‌‌​‌​​‌‌​‌​​​​‌‌​‌​​​​‌​​‌​​‌‌​​​‌​​​​​‌​‌​​​​‌​​​‌​‌‌​‌​​‌‌​​​‌​​‌​‌‌‌​​​‌‌​​​​​​‌​‌‌​‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌‌​​‌​​‌‌​​‌‌​​‌‌​‌​​​​‌‌​‌​‌​​‌‌​​‌​​​‌​‌‌​‌​‌​‌​​‌‌​‌​‌​​​​​‌​​​‌​‌​‌​​​​‌‌​​‌​‌‌​‌​​‌‌​​​‌​‌‌​​‌​‌​​‌‌​​‌​​‌‌​​‌​​​​‌‌​​‌​​‌‌​​​​‌​​‌‌​‌​​​‌‌​​‌​​​​‌‌​​‌‌​​‌‌‌​​‌​‌‌​​​‌‌​‌‌​​‌​‌​​‌‌‌​​​​​‌‌​‌​​​‌‌​​‌​​​‌‌​​​‌‌​​‌​‌‌​‌​‌‌​​​​‌​​‌‌​‌​‌​‌‌​​​‌‌​‌‌​​​‌‌​‌‌​​‌​‌​‌‌​​‌​​​​‌‌‌​​‌​​‌‌​​​​​‌‌​​​​‌​‌‌​​​​‌​​‌‌​‌​​​‌‌​​​‌‌​​‌‌​‌​​​​‌‌​‌‌‌​​‌‌​​​​​‌‌​​​‌‌


​‌​​​​‌‌​‌​​​​‌​​‌​‌‌​‌​​‌​‌​‌‌‌​​​​​​​​​​​​​​​​​​​​​​​​​​‌‌‌​‌‌‌​‌‌​‌‌‌​​​‌​​‌​‌‌‌‌​​‌​‌‌‌‌‌​​‌​‌​​​​‌‌​‌​​​​‌​​‌​​‌‌​​​‌​​​​​‌​‌​​​​‌​​​‌​‌‌​‌​​‌‌​​​‌​​‌​‌‌‌​​​‌‌​​​​​​‌​‌‌​‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌​‌‌‌​​‌‌​​‌​​​‌‌​​‌​​​‌‌​‌‌‌​​‌‌​‌‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌‌​​​​​‌​‌‌​‌​‌​‌​​‌‌​‌​‌​​​​​‌​​​‌​‌​‌​​​​‌‌​​‌​‌‌​‌​‌‌​​​‌‌​‌‌​​‌​​​​‌‌​​​​​​‌‌‌​​‌​‌‌​​‌​​​​‌‌​‌​​​‌‌​​​​‌​​‌‌‌​​​​​‌‌‌​​‌​​‌‌‌​​​​‌‌​​‌​‌​​‌‌​​​‌​​‌‌​​​‌​​‌‌​​‌​​‌‌​​‌​​​​‌‌‌​​​​​‌​‌‌​‌​​‌‌‌​​‌​‌‌​​‌​​​​‌‌​‌​​​‌‌​​‌​​​​‌‌‌​​‌​​‌‌​‌​‌​​‌‌​‌​‌​‌‌​​‌​‌​‌‌​​‌​‌​​‌‌​​​‌​​‌‌‌​​​​​‌‌​​​‌​​‌‌​‌‌​​‌‌​​​​‌​​‌‌​​​‌​​‌‌​‌‌‌