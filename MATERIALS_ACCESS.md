# Material access and archive correspondence

Prepared on 2026-10-24 for `ava0428/monocular-assisted-stereo-reliability`. This document describes local prepared contents and execution scope; it does not record an independently verified upload, journal submission or external download test.

## Public versus journal payloads

| Public file | Counterpart in the local journal-material delivery | Relationship |
|---|---|---|
| `CVIU_S1_Original_Evaluation.zip` | `data/CVIU_S1_Original_Evaluation.zip` | Exact original archive bytes |
| `CVIU_S2_Evaluation_States.csv` | `data/CVIU_S2_Evaluation_States.csv` | Exact original CSV bytes |
| `CVIU_S3_Implementation_Records_Public.zip` | `data/CVIU_S3_Implementation_Records.zip` | Public derivative: one copied upstream DDCV file excluded; verifier reports that exclusion; notices added |
| `CVIU_S4_Additional_Evaluation.zip` | `data/CVIU_S4_Additional_Evaluation.zip` | Exact original archive bytes |
| `CVIU_Analysis_Execution_Consistency.zip` | `analyses/CVIU_Analysis_Execution_Consistency.zip` | Exact original archive bytes |
| `CVIU_Analysis_Calibration_Public.zip` | `analyses/CVIU_Analysis_Calibration.zip` | Public derivative: public-release/license notices added; all six sampled operands and research records unchanged |
| `CVIU_Checkpoints_Risk_Scorers.zip` | `checkpoints/CVIU_Checkpoints_Risk_Scorers.zip` | Exact original archive bytes |
| `CVIU_Checkpoints_RelDirect.zip` | `checkpoints/CVIU_Checkpoints_RelDirect.zip` | Exact original archive bytes |
| `CVIU_Public_Code.zip` | Current editable-source tree | Curated derivative, not the journal's full `CVIU_Editable_Source.zip` |

The six unchanged payloads retain their historical hashes. Modified public containers have their own hashes in `PUBLIC_FILE_INDEX.csv`. Historical archives remain preserved locally; source-identification records are not rewritten to conceal public exclusions. Old pre-release statements about pending sharing/license decisions inside preserved README files are superseded by this release's root scope and licensing documents.

S3's public verifier checks every retained source hash and separately reports the exact omitted upstream inspection file. Read its `PUBLIC_RELEASE_README.md` and `DDCV_UPSTREAM_SOURCE.md`. The file's historical SHA and fixed upstream commit remain available; no license to redistribute that upstream file is implied.

## Checkpoints and normalization

- The 18-checkpoint archive covers `r1`, `r2_concat`, `r2_dis`, `r2_gate`, `n_random` and `n_shuffle`, each for three fixed runs. Its manifest maps family, display run, original seed, selected step, member path, size and SHA-256.
- Rel-Direct is separately supplied as `grel_direct`, three checkpoints selected at steps 8000, 2000 and 8000. Its original catalog and post-hoc provenance qualification remain intact. Legacy serialization/import dependencies are not removed by packaging.
- The checkpoint files are original source-selected envelopes, not all bare model state dictionaries; Rel-Direct also retains training-state metadata. None contains a RAFT-Stereo or DAV2 backbone checkpoint. Member identity checks did not construct or run models.
- Model/feature sources and `normalization_sceneflow_train.json` are retained in S3, S4's execution snapshots and the curated code bundle. Use the configuration belonging to the intended execution; do not mix original fits and additional-execution scores.

## Official assets and generation path

1. **Booster:** obtain the labeled official data from [the University of Bologna record](https://amsacta.unibo.it/id/eprint/6876/), DOI [10.6092/unibo/amsacta/6876](https://doi.org/10.6092/unibo/amsacta/6876). Use the recorded TRAIN/balanced camera00/02 members in S3's `split_frames.csv`, `split_scenes.csv` and `split_contract.json`: 19 CAL directory groups / 120 frames and 19 EVAL groups / 108 frames. Preserve their exact frame identities and geometry rather than selecting a new cohort.
2. **Frozen predictors:** obtain [RAFT-Stereo](https://github.com/princeton-vl/RAFT-Stereo) and [Depth Anything V2-Small](https://github.com/DepthAnything/Depth-Anything-V2) separately under their terms. The retained `raftstereo-sceneflow.pth` SHA-256 is `ba75bdcb379b4c3942d1e714565d0e66e6b2450a3da8129f54073302d67e0a6d`; `depth_anything_v2_vits.pth` is `715fade13be8f229f8a70cc02066f656f2423a59effd0579197bbf57860e1378`. Preserve the recorded preprocessing, disparity units, padding and inference settings in `generation_sources/` and S3/S4 configs.
3. **Input packing:** the documented adapter outputs are scoring-grid stereo disparity and mono-relative-depth arrays. The reconstructed `reproduce.py prepare-inputs` entry packs existing predictions and hash-matched official RGB into a new directory; it performs neither backbone inference nor GT sampling. Its prior one-frame check is a limited historical validation, not a new all-frame or clean-host execution.
4. **CAL/EVAL:** recorded `analysis_round2` entries describe score recovery, CAL fitting, native evaluation and saved-result reduction. They require full native GT, camera geometry, compatible source imports and prediction caches. Historical builder scripts can use fixed project paths and overwrite outputs; inspect them and work in a separate reconstruction workspace.

The lightweight release omits raw RGB/GT, large native arrays, full prediction caches, third-party model trees and image-based display inputs. Six sampled CAL operand files are supplied only in `CVIU_Analysis_Calibration_Public.zip`, with their exact Booster attribution and CC BY-NC scope. They do not replace full native GT.

## Figure regeneration

The public code bundle includes numeric inputs and scripts for current contrasts, coverage curves, the synthetic/empirical offset explanation and scene contrasts. With NumPy and Matplotlib, `analysis_revision/build_core_figures.py`, `analysis_round8/plot_mechanism.py` and `analysis_round8/plot_scenes.py` redraw from saved records without new model, CAL or bootstrap execution. Their output directory is `manuscript/figures/`; the full manuscript is not included.

Image-based overview/frame-panel scripts are retained for inspection, but their Booster RGB/ROI/display NPZs and final embedded-image SVG/PDF exports are excluded from this code/results release. This repository therefore does not claim to regenerate the final author-edited Figure 1 or the image-based Figure 6 from the public ZIP alone. The local journal source package retains those editable assets.
