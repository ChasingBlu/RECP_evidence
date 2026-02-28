CB03720260228
# Error Report: Contextual Embedding Doc vs Publication & Baseline

**Date:** 2026-02  
**Scope:** Compare authoritative doc `contextual_embedding..md` (daemon_cairos) with SDD/R-RECP, RECP paper, and `identity_baseline` evidence. Identify conflation and errors.

**Authority (contextual embedding):**  
`E:\workstations (Scaffold and Storage)\ws01\Quantum_ON HOLD (INDEF_\CAIROS\cairos_02\daemon_cairos\doc\contextual_embedding..md`

**Baseline / publication evidence:**  
`D:\ChasingBlu_RND\Lab\Active\CAIROS_visualizer\RECP_Publication_Package_20260220\evidence\identity_baseline`

---

## 1. RECP vs Basins (Critical)

**User correction:** RECP has nothing to do with basins. Basins are CAIF (Mahalanobis distances, basins, chaos math).

**Error in paper:**  
`RECP_Paper_Complete_Memorial_20260225.md` §4.1 Node 01:

> **Node 01 (Closed-Loop Identity Baseline):** Measures **basin formation under RECP conditioning** vs. baseline (context-off) and random Gaussian controls. Outputs: distance distributions, confidence intervals, CAIF membership metrics.

**Problem:** Node 01 outputs (distance distributions, centroid-referenced distances, confidence intervals) are **identity-baseline / CAIF-style** metrics (distances to a baseline centroid, cohort displacement). They are **not** RECP metrics. RECP = ICS, API, ECR, LDI, SRV, TCDM (weighted anchor centroid, pairwise similarity, etc.). Conflating “basin formation” with “RECP conditioning” incorrectly ties basin/CAIF math to RECP.

**Correction:** Describe Node 01 as measuring **identity baseline / basin-relevant geometry** (distance to May ctx-on centroid, CAIF membership), and state that the **conditioning** (May–February interaction) is RECP-style; the **measurement** here is not RECP but CAIF/identity-baseline. Do not say “basin formation under RECP” as if basins were an RECP output.

---

## 2. Contextual Embedding: Two Different “On/Off” Concepts

**Doc (contextual_embedding..md):**  
- **Contextual embedding (Option 1):** Run **anchor** words through the LLM **in a prompt context** (e.g. “This is about Blu, a mirror…”), then mean-pool hidden states at anchor positions → identity vector e_id.  
- **Static:** Average of **anchor** word embeddings **in isolation**.

So in the doc, “contextual” vs “static” refers to **how anchors are embedded** to form e_id (in-context vs isolated).

**Paper / SDD:**  
- **Context-on (CTX-ON):** “Embeddings extracted from **full conversational context** using mean-pooling over anchor token positions **within dialogue**.”  
- **Context-off (CTX-OFF):** “Embeddings extracted from **isolated anchor phrases** without conversational history.”

So in the paper, context-on/off refers to **what is embedded**: full turn/dialogue vs isolated phrase (turn-level input).

**Conflation / risk:**  
- **Doc:** “Contextual embedding” = anchor-in-context vs anchor-in-isolation (identity vector construction).  
- **Paper/SDD:** “Context-on/off” = turn with full context vs turn stripped (input to embedder).

Same words (“context on/off”, “contextual”) are used for (1) **anchor** embedding strategy and (2) **turn** content. The publication does not cite the doc or distinguish these. Readers may assume “context-on” in the paper means the doc’s “contextual embedding” (anchors in context), but in the paper it means “turn with full conversational context.”

**Recommendation:**  
- In the paper (or a supplement), add a short note: “Context-on/off here refers to **turn content** (full dialogue vs stripped/isolated), not to the anchor-embedding strategy (contextual vs static) in [contextual_embedding doc].”  
- Optionally cite the doc and define: (a) **Turn-level** ctxon/ctxoff = what we embed; (b) **Anchor-level** contextual vs static = how e_id could be formed (per doc).

---

## 3. identity_baseline Evidence: Correct Scope, Wrong Framing in Paper

**What identity_baseline contains:**  
- `identity_centroid.json`: centroid = **mean of May ctx-on coords** (9 points), 2D.  
- `may_ctxon_distances.csv` / `feb_ctxon_distances.csv` / `feb_ctxoff_distances.csv`: **distances to that centroid** (and summaries).  
- `identity_potential_grid_*.meta.json`: potential formula V(x,y)=0.5*((x-cx)²+(y-cy)²) around that centroid.

So the folder is **correctly** “identity baseline” in the sense of **CAIF/basin-style** evidence: centroid from baseline cohort, distances to that centroid, centroid displacement. It does **not** contain RECP metrics (ICS, API, ECR, LDI, SRV, TCDM).

**Error:** The paper frames Node 01 as “basin formation under RECP conditioning” and uses this evidence. The **evidence** is appropriate for identity baseline / basin/CAIF; the **wording** should not imply that these distance/centroid outputs are RECP metrics or “RECP basin formation.”

---

## 4. Stray Duplicate File in identity_baseline

**File:** `feb_ctxoff_coords_2d copy.csv`  
**Issue:** Duplicate of `feb_ctxoff_coords_2d.csv` (same columns and values). Stray copy; should not be in publication evidence.

**Action:** Remove `feb_ctxoff_coords_2d copy.csv` from the evidence package or mark as non-artifact duplicate.

---

## 5. Summary Table

| # | Location | Error / issue | Severity |
|---|----------|----------------|----------|
| 1 | RECP paper §4.1 Node 01 | “Basin formation under RECP conditioning” conflates RECP with basin/CAIF. Basins = CAIF (Mahalanobis, chaos); RECP = six metrics (ICS, API, etc.). | **Critical** |
| 2 | Paper vs contextual_embedding doc | “Context-on/off” in paper = turn content; in doc “contextual” = anchor embedding strategy. Same terms, different definitions; no cross-reference. | **Medium** |
| 3 | identity_baseline framing | Evidence is correct for identity baseline/CAIF; paper should not describe it as RECP basin formation. | **Medium** |
| 4 | identity_baseline/ | Stray file `feb_ctxoff_coords_2d copy.csv`; duplicate of `feb_ctxoff_coords_2d.csv`. | **Low** |

---

## 6. Recommended Wording Change (Node 01)

**Current:**  
“Node 01 (Closed-Loop Identity Baseline): Measures basin formation under RECP conditioning vs. baseline (context-off) and random Gaussian controls. Outputs: distance distributions, confidence intervals, CAIF membership metrics.”

**Suggested:**  
“Node 01 (Closed-Loop Identity Baseline): Measures identity-baseline geometry (distances to May context-on centroid, centroid displacement) and CAIF-relevant membership, under RECP-style conditioning, vs. context-off and random Gaussian controls. Outputs: distance distributions, confidence intervals, CAIF membership metrics. (RECP metrics proper—ICS, API, ECR, LDI, SRV, TCDM—are computed separately by the daemon; basins and Mahalanobis distances are CAIF, not RECP.)”

This keeps the evidence and Node 01 outputs unchanged while separating RECP from basin/CAIF and aligning with the authoritative distinction.


​‌​​​​‌‌​‌​​​​‌​​‌​‌‌​‌​​‌​‌​‌‌‌​​​​​​​​​​​​​​​​​​​​​​​​​​‌‌‌​‌‌‌​‌​​​​‌​​​‌‌​‌‌​‌‌‌​​‌​​​​​​​​‌​‌​​​​‌‌​‌​​​​‌​​‌​​‌‌​​​‌​​​​​‌​‌​​​​‌​​​‌​‌‌​‌​​‌‌​​​‌​​‌​‌‌‌​​​‌‌​​​​​​‌​‌‌​‌​​‌‌​​​‌​​‌‌​‌‌‌​​‌‌​‌‌‌​​‌‌​​‌​​​‌‌​​‌​​​‌‌​‌‌‌​​‌‌​‌‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌‌​​‌​​‌​‌‌​‌​‌​‌​​‌‌​‌​‌​​​​​‌​​​‌​‌​‌​​​​‌‌​​‌​‌‌​‌​‌‌​​​‌​​​‌‌​​‌‌​‌‌​​​‌​​‌‌​​‌​​​​‌‌​‌​‌​‌‌​​‌‌​​​‌‌‌​​​​​‌‌​​​‌​‌‌​​‌​​​​‌‌​‌​‌​​‌‌​​‌​​​‌‌​‌‌‌​​‌‌​‌​​​‌‌​​​‌‌​‌‌​​​‌​​​‌‌​​‌​​​‌​‌‌​‌​‌‌​​​‌‌​‌‌​​​‌‌​‌‌​​‌​‌​​‌‌‌​​‌​​‌‌​‌‌‌​‌‌​​‌​​​​‌‌​‌‌‌​‌‌​​‌‌​​​‌‌​‌‌​​​‌‌​​‌​​​‌‌​‌‌‌​​‌‌​​‌‌​​‌‌​‌​‌​‌‌​​​​‌​‌‌​​​‌‌​​‌‌​‌​‌