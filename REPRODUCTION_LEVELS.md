# Reproduction levels and commands

Prepared snapshot: 2026-10-24. Run each command from the root of its own fresh archive extraction. Keep downloaded archives immutable; several entries overwrite derived outputs inside the extraction. The original evaluation and additional re-evaluation remain separate sources.

| Level | Command / archive | Actual computation | Scope boundary |
|---|---|---|---|
| Current paired-change reduction | `python reproduce.py summary` in `CVIU_Public_Code.zip` or `CVIU_Analysis_Calibration_Public.zip` | Recomputes before/after contrasts and their fixed-seed 10,000-draw scene-group bootstrap from saved unrounded records; uses saved CAL diagnostic for table rendering | No new model scores, CAL fits or EVAL pixel ordering |
| Original saved-result replay | `python reproduce.py --out NEW_DIRECTORY --plots` in S1 | Recomputes original scene/configuration summaries, paired intervals, exact segment reductions and plots | Saved sufficient summaries, not raw pixel/model execution |
| Implementation/split verifier | `python verify_review.py` in S3_Public | Retained source hashes, exact split records, saved empirical 0.90 checks and a separately labeled synthetic arithmetic example | Public verifier reports one deliberate upstream-source exclusion; a synthetic check is not empirical validation |
| Additional saved-result reduction | `python summarize_regenerated.py` and `python write_validation_tables.py` in S4 | Reduces previously evaluated additional frame records and writes display tables | Does not repeat the prior score-generation/CAL/native-evaluation chain |
| Execution comparison | `python analysis_round3/compare_evaluations.py` in the execution-consistency archive | Matches saved original/additional identities and recomputes comparison summaries/intervals | These are two executions on the same cohort, not independent-cohort validation |
| Sampled CAL-group diagnostic | Explicit `python reproduce.py cal-bootstrap` in the calibration archive | Also recomputes paired changes, then refits six scorer/run offsets on 2,000 shared group-bootstrap draws; computes omitted-group sampled radius coverage | Does not propagate refits through EVAL rankings or selective risks; not a joint CAL+EVAL uncertainty interval |
| Input packaging | `python reproduce.py prepare-inputs --balanced-root PATH --prediction-root PATH --role EVAL --out NEW_DIRECTORY` in the code archive | Uses hash-matched official RGB and already available frozen predictions; writes scoring-grid input bundles | Reconstructed non-overwriting packer, not model inference or a historical execution receipt |
| Asset inventory | `python reproduce.py preflight-raw --project-root PATH` in the code archive | Reports presence of specified manifest/checkpoint paths | Presence does not prove bytes, runtime or successful evaluation |
| Full raw pipeline | Preserved `analysis_round2` and `generation_sources` entries, with external inputs | Model/head score generation, CAL fitting, native evaluation and summary in a separate reconstruction workspace | Requires raw data, geometry, backbone dependencies, weights and caches; not a demonstrated one-command clean-host workflow |

## Statistical objects

The paired-change comparison uses Base-Risk minus Stereo-Err before and after the recorded processing change. Three fixed runs are averaged within each scene-directory group; the 19 scene groups are paired resampling units. These risk-change intervals condition on saved CAL fits. They are not intervals for percentage ratios or differences between independently displayed interval endpoints.

The CAL diagnostic uses six supplied `error`/`h0`/`scene` operand files (Stereo-Err and Base-Risk × three runs). Each contains 19 groups × 8192 sampled pixels. Its output is offset sensitivity and sampled **radius coverage**, including omitted groups. Retained coverage for selective-risk evaluation is a different quantity. The files retain their individual Booster-derived licensing notice.

## Dependencies and validation identity

Python 3 and NumPy are sufficient for the current `summary` and `cal-bootstrap` entries; `requirements-summary.txt` provides the small NumPy dependency specification. Plotting additionally requires Matplotlib; input packing additionally requires OpenCV and Pillow. These are separate from the full recorded PyTorch/model environment. The dependency range is not a claim that every Python/NumPy combination has been tested.

Historical records document the earlier full additional re-evaluation, saved-result replay, complete CAL-group diagnostic checks and limited input-packing validation. Public packaging checks inspect archive integrity, exact identities, exclusions, Python syntax and entry help. **No bootstrap, CAL diagnostic, training, model forward or native evaluation was newly run during this release preparation.** Reusing a prior verification record is not reported as a fresh execution.

Use `MATERIALS_ACCESS.md` for filenames, source identities and generation requirements, and `THIRD_PARTY_NOTICES.md` for the separate code/results/weight/operand license scopes.
