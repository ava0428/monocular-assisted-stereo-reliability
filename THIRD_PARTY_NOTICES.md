# License scope and third-party notices

Copyright (c) 2026 Zhenqi Wei and Jinsong Hu for their original contributions.

| Material in this release | Applicable license |
| --- | --- |
| Original project source code, including the authors' analysis scripts and model-head implementations | MIT; full text in `LICENSE` |
| Authors' original result tables, analysis outputs and shareable learned risk-head checkpoints | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); full text in `LICENSE-CC-BY-4.0.txt` |
| Identified Depth Anything V2 preprocessing source portion | Apache-2.0; full text in `LICENSE-Apache-2.0.txt` |
| Six Booster-derived CAL operand files listed below | The underlying material retains [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/); it is excluded from the general MIT and CC BY 4.0 grants |

These scopes apply inside the ZIP archives as well as to loose files. An archive is a container and is not assigned a single license that overrides its contents. The authors' grants cover only rights they hold; the specific third-party terms below remain applicable. For attribution to original project materials, credit **Zhenqi Wei and Jinsong Hu**, identify the material and release used, link the applicable license, and indicate your modifications. Use the repository/release URL from which you obtained the files as the source link.

## Depth Anything V2 source portion

In `CVIU_Public_Code.zip`, `generation_sources/src/adapters/depth_anything.py` adapts the preprocessing sequence from the official [Depth Anything V2 `depth_anything_v2/dpt.py`](https://github.com/DepthAnything/Depth-Anything-V2/blob/main/depth_anything_v2/dpt.py), under [Apache-2.0](https://github.com/DepthAnything/Depth-Anything-V2/blob/main/LICENSE). The project changes include the adapter interface, source/checkpoint hash verification and RGB-input handling. The released adapter carries a corresponding change notice. The original upstream license text is included in `LICENSE-Apache-2.0.txt`; no upstream NOTICE file was found in the retained source tree. This notice does not replace any upstream source-file copyright notice.

The experiment uses Depth Anything V2 **Small (`vits`)**, whose [official README](https://github.com/DepthAnything/Depth-Anything-V2#license) specifies Apache-2.0. The Base, Large and Giant model terms differ. The vendor source tree and pretrained backbone checkpoint are external dependencies and are not included here.

## Booster-derived CAL operands

The following exact members of `CVIU_Analysis_Calibration_Public.zip` contain Booster-derived samples:

- `analysis_round5/cal_operands/r1_20260910.npz`
- `analysis_round5/cal_operands/r1_20260911.npz`
- `analysis_round5/cal_operands/r1_20260912.npz`
- `analysis_round5/cal_operands/r2_gate_20260910.npz`
- `analysis_round5/cal_operands/r2_gate_20260911.npz`
- `analysis_round5/cal_operands/r2_gate_20260912.npz`

Source: **Booster Dataset** (2022), **Pierluigi Zama Ramirez, Fabio Tosi, Matteo Poggi, Samuele Salti, Stefano Mattoccia and Luigi Di Stefano**, University of Bologna. DOI: [10.6092/unibo/amsacta/6876](https://doi.org/10.6092/unibo/amsacta/6876). The [official repository record](https://amsacta.unibo.it/id/eprint/6876/) licenses its labeled data and README under [Creative Commons Attribution-NonCommercial 4.0 International](https://creativecommons.org/licenses/by-nc/4.0/); see the [full legal code](https://creativecommons.org/licenses/by-nc/4.0/legalcode.en).

Changes: selected the declared 19 CAL scene-directory groups and sampled 8,192 pixels per group; computed disparity-error and uncalibrated model-radius values; stored `error`, `h0` and `scene` arrays for each declared scorer/run. Each file contains 155,648 samples. These are sampled derivative operands, not the complete dataset or native GT images. The underlying licensed material may be shared and adapted for noncommercial purposes under CC BY-NC 4.0, with attribution and indication of changes. No endorsement by the dataset authors is implied; their material is supplied without warranties under that license. Do not remove the source attribution or impose restrictions inconsistent with the source license.

Raw Booster image/GT archives and RGB/ROI display assets are excluded from this release. Authors' aggregate statistics are separately identified as results; this notice does not assert exclusive rights over facts or relabel the underlying dataset.

## Learned risk-head checkpoints and SceneFlow training provenance

`CVIU_Checkpoints_Risk_Scorers.zip` contains 18 source-selected project risk-head checkpoints; `CVIU_Checkpoints_RelDirect.zip` contains three source-selected Rel-Direct checkpoints. The authors license their rights in these shareable heads under **CC BY 4.0**. The checkpoint catalogs, selected steps and hashes identify the files. These archives do not contain RAFT-Stereo or Depth Anything V2 backbone checkpoints.

The heads were trained/selected using the recorded SceneFlow source protocol. [SceneFlow's official dataset terms](https://lmb.informatik.uni-freiburg.de/resources/datasets/SceneFlowDatasets.en.html) specify research-only dataset use and prohibit commercial dataset use; they do not expressly address redistribution or licensing of trained weights. This is training provenance, not an added noncommercial restriction on the authors' CC BY 4.0 grant, and this release does not assert clearance of every possible third-party right for commercial deployment. Cite the training dataset: N. Mayer, E. Ilg, P. Häusser, P. Fischer, D. Cremers, A. Dosovitskiy and T. Brox, *A Large Dataset to Train Convolutional Networks for Disparity, Optical Flow, and Scene Flow Estimation*, CVPR 2016.

## External backbone dependencies

- **RAFT-Stereo**: [official source](https://github.com/princeton-vl/RAFT-Stereo), [MIT license](https://github.com/princeton-vl/RAFT-Stereo/blob/main/LICENSE), copyright (c) 2021 Princeton Vision & Learning Lab. The project adapter loads the separately obtained vendor source and checkpoint. Retained SceneFlow checkpoint identity: `raftstereo-sceneflow.pth`, SHA-256 `ba75bdcb379b4c3942d1e714565d0e66e6b2450a3da8129f54073302d67e0a6d`.
- **Depth Anything V2-Small**: [official source and model instructions](https://github.com/DepthAnything/Depth-Anything-V2), Apache-2.0 as specified above. Retained checkpoint identity: `depth_anything_v2_vits.pth`, SHA-256 `715fade13be8f229f8a70cc02066f656f2423a59effd0579197bbf57860e1378`.

Obtain external packages, dataset files and backbone weights from their respective providers and retain their terms. The licenses for this project's materials do not replace those providers' licenses.

## DDCV / Un-ViTAStereo reference

The project comparator records the rule and warp/quantile conventions inspected at Un-ViTAStereo commit `ddf2f57f5ec518a0a167c5da3fc5dfab90211dac`. Reference: [official `loss_fuction.py` at that commit](https://github.com/CwLiuzzZ/Un-ViTAStereo/blob/ddf2f57f5ec518a0a167c5da3fc5dfab90211dac/toolkit/function/depth_function/loss_fuction.py), SHA-256 `bdc5470913400fddb59d26b6c5104dfe573352ea24a39af019941745d2861117`.

The copied upstream inspection file is excluded because a license covering it was not found. The public materials retain the project's comparator implementation and provenance description. This does not grant a license to the upstream implementation or claim reproduction of its complete network.
