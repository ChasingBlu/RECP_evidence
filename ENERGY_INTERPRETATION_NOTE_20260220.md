CB03620260228
# Evidence Interpretation Note — conservation/energy.csv

**Date:** 2026-02-20  
**REPA Amendment:** Append-only. This note clarifies interpretation; it does not modify locked artifacts.  
**Reference:** `INVESTIGATION_FINDINGS_20260220.md` (package root)

---

## Summary

The values in `conservation/energy.csv` (E_0≈17.65, E_f≈9.22, −47% reduction) are **simulation diagnostic energy**, not embedding-space energy and not identity-centroid-centered energy.

---

## What energy.csv represents

- **Source:** MetricsEngine (CPU) or GPU diagnostics. Hamiltonian expectation ⟨ψ|Ĥ|ψ⟩.
- **Potential in diagnostic:** V(x,y)=½(x²+y²) centered at **grid origin (0,0)**.
- **NOT:** V(e)=½‖e−c₀‖² (identity centroid c₀).
- **NOT:** The evolution potential (anchor + entropy).

---

## Correct interpretation

- **Supports:** Schrödinger-like evolution exhibits energy relaxation under a harmonic reference.
- **Does not support:** Identity-centroid energy minimization V(e)=½‖e−c₀‖² over embeddings.
- **Claim C12:** Conservation (norm_error < 10⁻⁶) — unchanged. Valid.

---

## Paper / manifest wording

If the paper or LOCK_MANIFEST cites "Energy May→Feb (embedding)" for 17.6→9.2, that wording is **incorrect**. The energy is simulation diagnostic Hamiltonian energy. Identity-based evidence for energy minimization would require a different computation (see INVESTIGATION_FINDINGS, Section 5).

---

*REPA: Accurate. Traceable to code inspection 2026-02-20.*


​‌​​​​‌‌​‌​​​​‌​​‌​‌‌​‌​​‌​‌​‌‌‌​​​​​​​​​​​​​​​​​​​​​​​​​​‌‌‌​‌‌​​​​‌​‌‌‌‌‌​‌​‌​​​​​​‌​​​‌​​‌‌​‌​‌​​​​‌‌​‌​​​​‌​​‌​​‌‌​​​‌​​​​​‌​‌​​​​‌​​​‌​‌‌​‌​​‌‌​​​‌​​‌​‌‌‌​​​‌‌​​​​​​‌​‌‌​‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌‌​​‌​​‌‌​​‌‌​​‌‌​‌​​​​‌‌​‌​‌​​‌‌​​‌​​​‌​‌‌​‌​‌​‌​​‌‌​‌​‌​​​​​‌​​​‌​‌​‌​​​​‌‌​​‌​‌‌​‌​​‌‌‌​​​​​‌‌​‌​‌​​‌‌‌​​‌​‌‌​​​‌‌​​‌‌‌​​‌​​‌‌​​​‌​​‌‌​‌​‌​​‌‌​​‌​​‌‌​​‌‌​​‌‌​​‌​‌​‌‌​​‌‌​​​‌‌​​​‌​​‌‌​‌‌‌​‌‌​​​‌​​‌‌​​‌‌​​​‌‌​‌​​​​‌​‌‌​‌​​‌‌​​​‌​‌‌​​‌‌​​​‌‌​‌​‌​‌‌​​​‌​​​‌‌​‌‌​​​‌‌​​​‌​​‌‌​‌‌‌​‌‌​​‌​​​​‌‌​​​​​‌‌​​‌​‌​​‌‌‌​​​​​‌‌​‌​‌​‌‌​​‌​‌​​‌‌​​‌​​‌‌​​‌‌​​​‌‌​‌​​

​‌​​​​‌‌​‌​​​​‌​​‌​‌‌​‌​​‌​‌​‌‌‌​​​​​​​​​​​​​​​​​​​​​​​​​​‌‌‌​‌‌​​‌​​‌​​​‌​​‌‌​​​‌‌‌​‌​‌‌​‌​​​‌​​‌​​​​‌‌​‌​​​​‌​​‌​​‌‌​​​‌​​​​​‌​‌​​​​‌​​​‌​‌‌​‌​​‌‌​​​‌​​‌​‌‌‌​​​‌‌​​​​​​‌​‌‌​‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌​‌‌‌​​‌‌​​‌​​​‌‌​​‌​​​‌‌​‌‌‌​​‌‌​‌‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌‌​​‌​​‌​‌‌​‌​‌​‌​​‌‌​‌​‌​​​​​‌​​​‌​‌​‌​​​​‌‌​​‌​‌‌​‌​​‌‌​​‌‌​‌‌​​​‌​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌​‌‌​​​‌‌​‌‌​​​‌‌​​​‌​​‌‌​‌​​​‌‌​​‌​​​‌‌​​​‌​​​‌‌​​​‌​​‌‌‌​​‌​‌‌​​​‌‌​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​​‌​‌​‌‌​​‌​‌​​‌‌​‌​‌​​‌‌​​‌‌​​‌‌​‌‌‌​​‌‌​​‌‌​‌‌​​​‌‌​‌‌​​​‌​​‌‌​​‌​‌​‌‌​​​‌​​​‌‌​​‌‌​​‌‌​​​​​‌‌​​‌‌​​​‌‌‌​​‌​‌‌​​‌‌​​‌‌​​​‌‌