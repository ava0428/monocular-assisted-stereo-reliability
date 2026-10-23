# Monocular-assisted stereo reliability: research materials

Code, saved results and source-selected risk-scorer checkpoints for **Monocular-Assisted Reliability for Stereo Depth: The Role of Score Processing and Coverage**, by **Zhenqi Wei and Jinsong Hu**.

Prepared snapshot: **2026-10-24**. Intended repository: [ava0428/monocular-assisted-stereo-reliability](https://github.com/ava0428/monocular-assisted-stereo-reliability). The materials distinguish the **original evaluation** from the **additional re-evaluation**; their identities and saved results are not merged.

## Start with saved results

Download `CVIU_Public_Code.zip` and extract it into a new working directory. The ZIP has no enclosing directory, so do not extract multiple packages over each other. Install NumPy, then run from the extracted directory:

```sh
python -m pip install -r /path/to/requirements-summary.txt
python reproduce.py --help
python reproduce.py summary
```

`requirements-summary.txt` is supplied at the repository root. Alternatively, install NumPy in your chosen environment. Python 3 and NumPy are sufficient for this entry; this dependency file does not install the full model/evaluation environment.

**`summary` recomputes the paired scene-change statistics, including the fixed-seed 10,000-draw scene-group bootstrap reduction, from saved unrounded scene records.** It reads the saved CAL-refit results to render the CAL display table. It does not load models, refit CAL or rerun native-pixel rankings. Derived files are overwritten in the extraction, so retain the downloaded archive and work in a fresh copy.

## Nine material payloads

| File | Contents | Starting point after extraction |
|---|---|---|
| [CVIU_Public_Code.zip](CVIU_Public_Code.zip) | Curated current analysis/plotting code, implementation/configuration records and numeric inputs | `python reproduce.py summary` |
| [CVIU_S1_Original_Evaluation.zip](CVIU_S1_Original_Evaluation.zip) | Original scene/configuration results, saved intervals, segment sums and replay code | `python reproduce.py --out NEW_DIRECTORY --plots` |
| [CVIU_S2_Evaluation_States.csv](CVIU_S2_Evaluation_States.csv) | Original evaluation state records | CSV reader |
| [CVIU_S3_Implementation_Records_Public.zip](CVIU_S3_Implementation_Records_Public.zip) | Split manifests, normalization/configuration, implementation records and public-copy verifier | `python verify_review.py` |
| [CVIU_S4_Additional_Evaluation.zip](CVIU_S4_Additional_Evaluation.zip) | Saved additional-execution frame/scene results, fits and executed sources | `python summarize_regenerated.py`; `python write_validation_tables.py` |
| [CVIU_Analysis_Execution_Consistency.zip](CVIU_Analysis_Execution_Consistency.zip) | Original/additional execution comparison and its minimal numeric inputs | `python analysis_round3/compare_evaluations.py` |
| [CVIU_Analysis_Calibration_Public.zip](CVIU_Analysis_Calibration_Public.zip) | Direct paired-change results, six sampled CAL operand files and saved CAL-group refits | `python reproduce.py summary`; explicit `python reproduce.py cal-bootstrap` |
| [CVIU_Checkpoints_Risk_Scorers.zip](CVIU_Checkpoints_Risk_Scorers.zip) | 18 source-selected checkpoints: four central and two content-control families × three runs | `checkpoint_manifest.json` |
| [CVIU_Checkpoints_RelDirect.zip](CVIU_Checkpoints_RelDirect.zip) | Three source-selected Rel-Direct checkpoints, catalog and loader/model source copies | `checkpoint_manifest.json` |

[PUBLIC_FILE_INDEX.csv](PUBLIC_FILE_INDEX.csv) records payload sizes, hashes, historical counterparts and entry points. [SHA256SUMS.txt](SHA256SUMS.txt) covers the payloads and root documents. Extract each ZIP separately; an archive's original filenames and recorded paths retain their historical meaning.

## Execution levels

- **Saved-result reduction:** works from supplied scene/frame/segment records. Depending on the selected entry, it recomputes reductions or paired bootstrap intervals; it is not inference or raw-pixel evaluation.
- **Sampled CAL refits:** `cal-bootstrap` is an explicit diagnostic in the calibration package. It refits six scorer/run offsets on 2,000 shared CAL-group draws and computes omitted-group **radius coverage**. Those refits are not propagated through EVAL rankings or selective risks.
- **Complete raw pipeline:** requires the official dataset, exact geometry, external backbone source/weights, compatible imports and frozen prediction/input caches. The preserved sources document the earlier execution but do not establish a one-command clean-host reproduction from this lightweight release.

See [REPRODUCTION_LEVELS.md](REPRODUCTION_LEVELS.md) for commands and scope, and [MATERIALS_ACCESS.md](MATERIALS_ACCESS.md) for data-generation paths and archive correspondence.

## What was checked for this prepared snapshot

Packaging checks verified archive CRCs, payload SHA-256/size identities, all 21 checkpoint member identities, retained Python syntax, deliberate exclusions and entry-point help. Prior recorded analysis/replay checks remain identified as prior checks. **This packaging step did not rerun bootstrap, CAL refits, training, model inference or native-pixel evaluation.** An entry-point help check or successful extraction is not a full reproduction claim.

## Public scope and licenses

Original author code is provided under [MIT](LICENSE); the authors' original saved results and shareable head checkpoints under [CC BY 4.0](LICENSE-CC-BY-4.0.txt). Identified third-party portions retain their own terms: the DAV2 preprocessing portion is Apache-2.0, and the six Booster-derived CAL operand files retain CC BY-NC 4.0. Read [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for exact file scope, dataset attribution and SceneFlow training provenance.

The public release excludes full manuscript sources/PDFs, author submission drafts, private revision records, raw RGB/GT and image/ROI display assets. Figure scripts for image-based panels remain inspectable but require excluded inputs. Third-party backbone weights are not bundled. The copied upstream DDCV inspection file is omitted with a pinned source/hash notice; its project adapter and historical identity records remain supplied. Public derivative archives are named explicitly and do not masquerade as the unchanged journal archives.

For citation of these materials, use [CITATION.cff](CITATION.cff) and identify the repository commit or downloaded version. No publication DOI or acceptance status is claimed.
