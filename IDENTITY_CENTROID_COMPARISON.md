CB03920260228
# Identity-Centroid Energy Comparison (2026-02-21)

**Reference:** Identity centroid c₀ from May ctxon baseline  
**c₀ = (0.660352, 0.445470)**

All runs use `task3_conservation.toml` with identity centroid loaded.  
`u_centroid` = free energy U relative to identity centroid (V(e) = ½‖e−c₀‖²).

---

## Summary Table

| Run | u_centroid t=0 | u_centroid t=99 | Δu_centroid | energy t=0 | energy t=99 | mean_x t=0 | mean_y t=0 | dist from c₀ t=0 |
|-----|----------------|-----------------|-------------|------------|-------------|------------|------------|------------------|
| may_ctxon | 0.1151 | 0.0792 | **−0.0359** | 15.19 | 8.35 | 0.774 | 0.437 | ~0.12 |
| feb_ctxon | 0.2028 | 0.1242 | **−0.0786** | 17.02 | 8.08 | 0.578 | 0.560 | ~0.09 |
| feb_ctxoff | 0.2165 | 0.0800 | **−0.1365** | 15.83 | 6.67 | 0.493 | 0.343 | ~0.22 |

---

## Interpretation

1. **may_ctxon** — Same coordinate set as the identity baseline. Starts closest to c₀. Smallest u_centroid at t=0 (0.115). Relaxes by Δu = −0.036.

2. **feb_ctxon** — Feb coordinates with context on. Initial mean (0.578, 0.560) is near c₀. u_centroid starts at 0.203, drops to 0.124. Δu = −0.079.

3. **feb_ctxoff** — Feb coordinates with context off. Initial mean (0.493, 0.343) is farthest from c₀. Highest u_centroid at t=0 (0.217). Largest relaxation: Δu = −0.137, ending at 0.080 (close to may_ctxon t=99).

All three runs show **u_centroid decreasing** over time → relaxation toward identity centroid c₀.  
The run that starts farthest from c₀ (feb_ctxoff) shows the largest drop in u_centroid.

---

## Identity Baseline Distances (from evidence/identity_baseline)

| Dataset | N turns | mean dist to identity |
|---------|---------|------------------------|
| may_ctxon | 9 | ~0.28 (from distances CSV) |
| feb_ctxon | 7 | ~0.12 |
| feb_ctxoff | 7 | ~0.31 |

These are raw distance-to-identity means from the coords; u_centroid is the expectation of ½‖e−c₀‖² under the evolved wavefunction.

---

## Run Configuration

- **Tool:** Simulation.Core.exe --dev-run
- **Config:** task3_conservation.toml
- **Identity centroid:** QuantumSimulationEngine/results/identity_baseline/identity_centroid.json
- **Headless:** true, backend direct3d12, gpu_compute false


​‌​​​​‌‌​‌​​​​‌​​‌​‌‌​‌​​‌​‌​‌‌‌​​​​​​​​​​​​​​​​​​​​​​​​​​‌‌‌​‌‌​​​​​​​‌‌​‌‌‌‌‌​​​​‌‌‌​‌​‌​‌‌​‌‌​‌​​​​‌‌​‌​​​​‌​​‌​​‌‌​​​‌​​​​​‌​‌​​​​‌​​​‌​‌‌​‌​​‌‌​​​‌​​‌​‌‌‌​​​‌‌​​​​​​‌​‌‌​‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌‌​​‌​​‌‌​​‌‌​​‌‌​‌​​​​‌‌​‌​‌​​‌‌​​‌​​​‌​‌‌​‌​‌​‌​​‌‌​‌​‌​​​​​‌​​​‌​‌​‌​​​​‌‌​​‌​‌‌​‌​​‌‌​​‌​​‌‌​​​‌‌​​‌‌​‌​​​‌‌​​‌​‌​​‌‌‌​​​​​‌‌​‌​​​​‌‌​​‌‌​‌‌​​‌​​​​‌‌​‌‌‌​​‌‌​‌‌‌​‌‌​​​‌‌​​‌‌​​‌‌​​‌‌​​‌​​‌‌​​‌‌​​​‌‌​​‌​​​‌‌​​‌​​​‌​‌‌​‌​‌‌​​‌​​​‌‌​​‌​‌​​‌‌​‌‌‌​​‌‌​‌‌‌​​‌‌​‌​‌​‌‌​​‌​‌​‌‌​​‌‌​​​‌‌​‌​‌​‌‌​​​​‌​​‌‌​‌‌​​‌‌​​​​‌​​‌‌​​‌‌​‌‌​​​‌‌​​‌‌​‌​​​​‌‌​​‌​​‌‌​​‌​​

​‌​​​​‌‌​‌​​​​‌​​‌​‌‌​‌​​‌​‌​‌‌‌​​​​​​​​​​​​​​​​​​​​​​​​​​‌‌‌​‌‌‌‌​‌​‌‌​‌​​‌‌‌‌‌​​‌​‌‌‌​‌‌​‌‌​​​​‌​​​​‌‌​‌​​​​‌​​‌​​‌‌​​​‌​​​​​‌​‌​​​​‌​​​‌​‌‌​‌​​‌‌​​​‌​​‌​‌‌‌​​​‌‌​​​​​​‌​‌‌​‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌​‌‌‌​​‌‌​​‌​​​‌‌​​‌​​​‌‌​‌‌‌​​‌‌​‌‌​​​‌‌​​​‌​​‌‌​​​‌​​‌‌​​​​​​‌​‌‌​‌​‌​‌​​‌‌​‌​‌​​​​​‌​​​‌​‌​‌​​​​‌‌​​‌​‌‌​‌​​‌‌​​‌‌​​‌‌​​​‌​​‌‌​‌‌‌​‌‌​​‌​‌​‌‌​​​‌​​​‌‌​‌‌​​​‌‌​​‌‌​​‌‌​‌​​​‌‌​​​​‌​​‌‌​‌‌​​‌‌​​‌‌​​​‌‌​​​‌​​‌‌​​​​​‌‌​​‌‌​​​‌‌‌​​​​​‌‌​‌‌​​​‌​‌‌​‌​‌‌​​​‌​​‌‌​​​‌​​‌‌​​‌‌​​​‌‌​​​‌​​‌‌​​‌​​​‌‌​‌‌‌​‌‌​​​‌​​‌‌​​​‌‌​‌‌​​‌​​​​‌‌‌​​‌​‌‌​​​​‌​‌‌​​‌​​​​‌‌‌​​‌​‌‌​​‌​​​​‌‌​‌‌​​​‌‌​​‌​