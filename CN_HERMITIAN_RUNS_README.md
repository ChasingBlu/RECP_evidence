# CN Hermitian Conservation Runs — 2026-02-22

This folder contains real-time Crank–Nicolson (CN) conservation audits using a **Hermitian** Hamiltonian with a fixed potential grid (`identity_potential_grid_*.npy`).

## Solver upgrades (2026-02-22)
- MKL PARDISO deterministic defaults: `MKL_INTERFACE_LAYER=LP64`, `MKL_THREADING_LAYER=SEQUENTIAL`
- Boundary decoupling (Dirichlet): interior rows do **not** couple to boundary neighbors; boundary values forced to 0.
- P/Invoke pinned buffers for potential + ψ (deterministic marshalling).
- Optional `cn_refactor_each_step` toggle (re-factorize A each step).

## Threshold policy (triad‑scaled)
Energy drift tolerance scales with steps:

```
energy_drift_tol_abs = max(1e-8, steps * 1e-10)
energy_drift_tol_rel = 1e-10
```

## Runs
- `cn_hermitian_100steps/`
  - 100‑step audit, unitarity + energy + hermiticity pass.
- `cn_hermitian_300steps_refactor_visuals/`
  - 300‑step audit, `cn_refactor_each_step=true`, frames saved.
  - Energy drift max_abs ≈ 1.53e‑8 (passes under triad‑scaled tolerance).
- `cn_hermitian_300steps_may_frames_20260222/`
  - 300‑step audit (May coords), `cn_refactor_each_step=true`, **300 frames + plots** saved.
  - Residual diagnostics enabled (`cn_residual.csv` + summaries in `cn_audit_report.json`).

Each run folder contains:
- `cn_audit.csv`, `cn_audit_report.json`
- `cn_residual.csv` (when enabled)
- `energy.csv`, `norm_audit.csv`, `cn_invariance.csv`
- `run_manifest.json`, `run_settings_snapshot.json`, `manifest.sha256`
- `frames/` and `plots/` where enabled


​‌​​​​‌‌​‌​​​​‌​​‌​‌‌​‌​​‌​‌​‌‌‌​​​​​​​​​​​​​​​​​​​​​​​​​​‌‌‌​‌‌​‌​‌‌‌‌​​‌‌​​​​‌​​​‌‌​​‌‌‌‌‌​‌‌​​‌​​​​‌‌​‌​​​​‌​​‌​​‌‌​​​‌​​​​​‌​‌​​​​‌​​​‌​‌‌​‌​​‌‌​​​‌​​‌​‌‌‌​​​‌‌​​​​​​‌​‌‌​‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌‌​​‌​​‌‌​​‌‌​​‌‌​‌​​​​‌‌​‌​‌​​‌‌​​‌​​​‌​‌‌​‌​‌​‌​​‌‌​‌​‌​​​​​‌​​​‌​‌​‌​​​​‌‌​​‌​‌‌​‌​​‌‌​‌‌‌​​‌‌​​‌‌​‌‌​​​‌​​​‌‌‌​​‌​​‌‌​​‌‌​‌‌​​‌‌​​​‌‌‌​​​​​‌‌​​‌‌​‌‌​​‌​‌​‌‌​​​‌​​​‌‌​‌‌​​​‌‌​‌​​​​‌‌​​​​​​‌‌​‌‌‌​‌‌​​​‌‌​‌‌​​​‌​​​‌​‌‌​‌​‌‌​​​​‌​‌‌​​‌​​​​‌‌​‌​‌​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌​‌​​‌‌‌​​‌​​‌‌​‌‌​​​‌‌​​​​​‌‌​​​‌​​​‌‌‌​​‌​‌‌​​​​‌​​‌‌​​‌​​​‌‌​​‌‌​​‌‌​​‌‌​​‌‌​‌‌‌