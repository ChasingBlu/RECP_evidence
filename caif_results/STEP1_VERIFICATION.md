# Step 1 Verification Report — 20260227_EVIDENCE_FINAL (Lexical)

**Date:** 2026-02-27  
**Run:** Full Lexical (MAY + FEB ctxon/ctxoff, anchors, coords, RECP). SecureLogger-locked; single key in evidence folder.

## Status: PASS

### Inputs (unchanged)
- **LockRoot:** `CAIROS_visualizer\QuantumSimulationEngine\data\LOCKED_TRACK_A_B_Final_20260217`
- **RUN_MAY:** `CLEAN_MAY_ctxon_turns.txt`, `CLEAN_MAY_ctxoff_turns.txt`, `CLEAN_MAY_anchors.txt`
- **RUN_FEBRUARY:** `CLEAN_FEBRUARY_ctxon_turns.txt`, `CLEAN_FEBRUARY_ctxoff_turns.txt`, `CLEAN_FEBRUARY_anchors.txt`

### Outputs (all under `20260227_EVIDENCE_FINAL`)
| Artifact | Location |
|----------|----------|
| Key | `secure_key.bin` |
| Secure log | `secure_log\` (logger_state.json, RED_WAX.*, entry files) |
| Embeddings | `lexical_run\MAY_CTXON_EMBEDDINGS.jsonl`, `MAY_CTXOFF_EMBEDDINGS.jsonl`, `FEB_CTXON_EMBEDDINGS.jsonl`, `FEB_CTXOFF_EMBEDDINGS.jsonl`, `may_anchors_lexical.jsonl`, `feb_anchors_lexical.jsonl`, `ANCHORS_EMBEDDINGS.jsonl` |
| RECP | `lexical_run\recp_lexical_MAY_ctxon.json`, `recp_lexical_MAY_ctxoff.json`, `recp_lexical_FEB_ctxon.json`, `recp_lexical_FEB_ctxoff.json` |
| Coords | `lexical_run\coords_3d\` (may_ctxon_coords_3d.csv, feb_ctxon_coords_3d.csv, anchors_ctxon_coords_3d.csv, etc.) |

### Notes
- RECP FEB ctxoff failed in-script once (SecureLogger rename permission); retried in a fresh process and succeeded. All four RECP JSONs present.
- No REPA shortcuts; same key used for all RECP steps.

**Next:** Step 1.3 — Full Semantic run (same key, same evidence folder).
