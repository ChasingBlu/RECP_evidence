# Step 1.3 Verification Report — 20260227_EVIDENCE_FINAL (Semantic)

**Date:** 2026-02-27  
**Run:** Full Semantic (MAY + FEB ctxon/ctxoff, anchors, coords, RECP). Same key as Step 1; Granite-278M.

## Status: PASS

### Inputs (unchanged)
- Same as Step 1: visualizer LOCKED RUN_MAY / RUN_FEBRUARY CLEAN_* paths.
- **ModelDir:** `CAIROS_Daemon_Mirror\models\granite-embedding-278m-multilingual`

### Outputs (all under `20260227_EVIDENCE_FINAL`)
| Artifact | Location |
|----------|----------|
| Embeddings | `semantic_run\MAY_CTXON_EMBEDDINGS.jsonl`, MAY_CTXOFF, FEB_CTXON, FEB_CTXOFF, may_anchors_semantic.jsonl, feb_anchors_semantic.jsonl, ANCHORS_EMBEDDINGS.jsonl |
| RECP | `semantic_run\recp_semantic_MAY_ctxon.json`, recp_semantic_MAY_ctxoff.json, recp_semantic_FEB_ctxon.json, recp_semantic_FEB_ctxoff.json |
| Coords | `semantic_run\coords_3d\` |
| Secure log | Same `secure_log\` as Step 1 (continuation). |

### Notes
- RECP FEB ctxoff failed in-script once (SecureLogger rename); retried in fresh process and succeeded.
- No port step needed; all outputs written directly under evidence folder.

**Next:** Step 2 — CAIF (basin from MAY baseline; Lexical + Semantic; deltas vs Feb).
