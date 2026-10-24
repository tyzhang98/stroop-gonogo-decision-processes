# Stroop and Go/No-Go analysis code

This repository contains the analysis notebooks for a 106-participant study of Stroop and Go/No-Go performance and MRI. It contains code, not participant-level data or completed analysis outputs. The notebooks have been cleared of execution outputs before release.

## Contents

| Notebooks | Analysis stage |
| --- | --- |
| `01_*` | Behavioural scores and demographics |
| `02_01_*` to `02_03_*` | HDDM fitting, posterior diagnostics, and parameter recovery |
| `03_*` | Computational components and behavioural associations |
| `04_*` and `05_*` | Resting-state and task-fMRI associations with HDDM components |
| `06_*` | Independent ROI, connectivity, and sensitivity analyses |
| `07_00_*` to `07_03_*` | MRI preprocessing, GLM, shared activation, and figures |

The notebooks are numbered by analysis topic. MRI preprocessing in `07_00_*` must be completed before notebooks that consume its derivatives. HDDM fitting in `02_01_*` precedes its diagnostics and recovery analyses. Run each notebook from this repository directory, in a Python 3 Jupyter kernel, after its observed inputs and prerequisite outputs are available.

## Inputs and environment

Install the Python packages listed in `requirements.txt`. The notebooks explicitly require HDDM 1.0.1 and Nilearn 0.13.1. MRI preprocessing also invokes external command-line tools: fMRIPrep 24.1.1, tedana 26.0.3, and ANTs (`antsApplyTransforms`). These executables and their non-Python dependencies are not installed by `requirements.txt`.

Set `A8_DATA_DIR` to the directory containing the observed input tables and `A8_OUTPUT_DIR` to a writable results directory. If `A8_DATA_DIR` is unset, the notebooks look for their documented stage subdirectories beside the notebooks. Core input filenames include `Participants.csv`, `Behavior_data.csv`, `HDDM_data.csv`, `MRI_manifest.csv`, and `ROI_masks.csv`; some downstream analyses also need fitted `HDDM_parameters.csv` and `HDDM_posterior_draws.csv`. The notebooks validate required columns and fail when an observed input is missing. Raw BIDS images alone do not supply all of these tables or the preprocessing derivatives.

The posterior-diagnostics notebook requests explicit ROPE endpoints interactively. Record the bounds used when reproducing that analysis. Model fitting and 500-repeat parameter recovery are computationally intensive.

## Reproducibility and privacy

This repository does not include participant-level records, MRI images, fitted posterior samples, or result tables. Its publication is not evidence that the full pipeline has been rerun in a clean environment or that every manuscript result has been independently reproduced. Before linking a dataset to this code, verify that the dataset contains the required observed inputs and that sharing them is permitted.

The source code is released under the MIT License (see `LICENSE`). This licence applies to the code in this repository, not to separately hosted participant data or MRI images.
