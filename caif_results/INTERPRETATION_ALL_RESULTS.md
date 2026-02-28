# Interpretation of All Results — 20260227_EVIDENCE_FINAL

**Purpose:** Plain-language interpretation of RECP and CAIF metrics for publication. Baseline = MAY; comparison = February (8 months later). Two axioms: Lexical (word2vec), Semantic (Granite).

---

## 1. What each metric means (short)

| Metric | Meaning |
|--------|--------|
| **ICS** | Identity Consistency Score (0–1). Higher = turn embeddings more consistent with each other / with anchor centroid. |
| **ECR** | Entropy / consistency residual. Often negative; magnitude reflects deviation from ideal. |
| **LDI** | Latent divergence index. Lower = less drift between turns. |
| **TCDM** | Turn-to-turn or trajectory divergence. Lower = more stable trajectory. |
| **RDS** | Residual divergence score. Lower = tighter identity. |
| **τ_α** | Basin boundary (Mahalanobis radius). Points with r ≤ τ_α are “in basin”; r > τ_α = outside (Zone C). |
| **Zone A/B/C** | A = core (r ≤ 0.7·τ_α), B = penumbra, C = exterior. More A = stronger identity retention. |
| **Mean r** | Mean Mahalanobis distance of Feb points to MAY centroid. Lower = Feb closer to MAY identity. |
| **TDR** | Tangential / radial drift ratio. Higher = more motion along the basin than outward; lower = more radial (toward exit). |

---

## 2. Lexical axiom

### RECP
- **MAY ctxon:** ICS = **0.9994** → very high pairwise consistency; LDI and TCDM small (0.0006, 0.042).
- **FEB ctxon:** ICS = **0.9972** → still very high, small drop vs MAY; LDI 0.0028, TCDM 0.0064.

**Interpretation:** Lexical identity is strong at both timepoints. The small MAY→Feb drop in ICS and slight rise in LDI are consistent with mild drift over 8 months, but identity remains well above threshold.

### CAIF (Feb evaluated in MAY basin)
- **τ_α ≈ 1.49** (basin from MAY lexical coords).
- **Feb:** 1 point in Zone A (core), 2 in Zone B (penumbra), **1 in Zone C** (exterior).
- **Mean r = 2.39**, max r = 5.81; **mean TDR = 1.18**.

**Interpretation:** One February point falls outside the MAY lexical basin (Zone C); the others stay in core or penumbra. Mean Mahalanobis > τ_α indicates that on average Feb is farther from the MAY centroid than the basin boundary. TDR > 1 suggests drift is partly tangential (moving around the basin) rather than purely radial (exiting). Overall: **lexical identity is largely preserved, with one clear excursion and moderate average distance from baseline.**

---

## 3. Semantic axiom

### RECP
- **MAY ctxon:** ICS = **0.76**, LDI = 0.24, TCDM = 0.27 (13 anchors).
- **FEB ctxon:** ICS = **0.79**, LDI = 0.21, TCDM = 0.016 (13 anchors).

**Interpretation:** Semantic consistency is lower than lexical (ICS ~0.76–0.79 vs ~0.997). That is expected: semantic embeddings are more sensitive to content and context. February actually shows a **slight increase** in ICS and a **large drop** in TCDM (0.27 → 0.016), suggesting the Feb trajectory is more stable in the semantic space than MAY in this run.

### CAIF (Feb evaluated in MAY basin, after tailed-input re-run)
- **τ_α ≈ 1.40** (basin from MAY semantic coords).
- **Feb:** **All 4 points in Zone A** (core).
- **Mean r = 0.26**, max r = 0.47; **mean TDR = 5.14**.

**Interpretation:** All February points lie well inside the MAY semantic basin (mean r ≪ τ_α). High TDR (5.14) means drift is mostly tangential (along the basin) rather than radial. **Semantic identity, relative to the MAY baseline, is strongly retained at February; no points exit the basin.**

---

## 4. RECP vs CAIF — combined reading

| Aspect | Lexical | Semantic |
|--------|---------|----------|
| **RECP (ICS)** | Very high at both MAY and Feb; small drop at Feb. | Moderate at both; slight rise at Feb. |
| **CAIF (Feb in MAY basin)** | One point in Zone C; mean r > τ_α. | All points in Zone A; mean r ≪ τ_α. |
| **Story** | Strong pairwise consistency (RECP), but one Feb point clearly outside the MAY lexical basin (CAIF). | Lower pairwise consistency (RECP), but Feb points all sit deep inside the MAY semantic basin (CAIF). |

**Why the difference?**  
- **Lexical** (word form / surface): RECP says “turns still look very similar”; CAIF says “one Feb turn has moved outside the MAY identity region in the reduced space.” So RECP and CAIF can diverge when one or a few turns shift in the projection even if overall similarity stays high.  
- **Semantic** (meaning): RECP says “similarity is moderate”; CAIF says “Feb’s semantic positions are all close to the MAY centroid.” So the MAY semantic basin is large enough (or Feb is close enough) that every Feb point remains in core.

**Takeaway for the paper:**  
- **Lexical:** Strong consistency (RECP) with one clear basin exit (CAIF) — good for showing that CAIF can flag an excursion even when ICS remains high.  
- **Semantic:** Moderate consistency (RECP) with full retention inside the basin (CAIF) — good for showing that semantic identity, once defined by MAY, is preserved at Feb in the geometry sense.

---

## 5. Summary table (interpretation-ready)

| Axiom   | RECP MAY | RECP Feb | CAIF Feb (in MAY basin) | One-line interpretation |
|---------|----------|----------|--------------------------|-------------------------|
| Lexical | ICS 0.999 | ICS 0.997 | 1×A, 2×B, **1×C**; mean r 2.39 | Very high consistency; one Feb point outside MAY lexical basin. |
| Semantic| ICS 0.76  | ICS 0.79  | **4×A**, 0×B, 0×C; mean r 0.26 | Moderate consistency; all Feb points inside MAY semantic core. |

---

**End of interpretation.**
