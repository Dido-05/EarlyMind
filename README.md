# EarlyMind

**Staging Alzheimer's disease from structural brain MRI**

EarlyMind classifies brain MRI scans into three stages: **cognitively normal (CN)**, **mild cognitive impairment (MCI)** and **Alzheimer's disease (AD)**. It is built as a fair benchmark: classical and deep models are compared on the same leakage-free data and tested on patients from a separate study.

> Senior Project · Faculty of Technology & Information, New Giza University
> Team: Mamdouh Mohsen · Amin El Kady
> Supervisor: Dr. Ayman Mahmoud Khalifa

---

## Why this project

Many published models report near-perfect results, but often because of data leakage, missing baselines or no testing on new patients. The early stage, MCI, is the hardest to detect and the one that matters most. EarlyMind measures what MRI-based staging really achieves when evaluated honestly.

## Approach

| Step | What happens |
|---|---|
| 1. Data | ADNI T1-weighted MRI scans and diagnosis tables |
| 2. Labels | CN / MCI / AD from clinical diagnosis at each scan's visit |
| 3. Preprocessing | Clinica: bias correction, registration to a standard template, quality control |
| 4. Split | By person (not by scan) into train / validation / test |
| 5. Models | Linear SVM on gray-matter maps · regional-feature classifier · 3D CNN |
| 6. Evaluation | Balanced accuracy, macro-F1, per-class AUC, confusion matrix, confidence intervals |
| 7. External test | Trained on ADNI, tested once on OASIS-3 |

**Planned ablations:** hippocampus-only 3D CNN; hybrid of CNN and regional features.
**Later phase:** confirm labels with amyloid PET (amyloid is never a model input).

## Datasets

- **ADNI** (training): access approved October 2026
- **OASIS-3** (external test)

**No imaging or clinical data is stored in this repository.** ADNI and OASIS-3 data are used under their data use agreements, which do not allow redistribution. To reproduce this work, request access directly from each dataset provider.

## Tech stack

Python · PyTorch · Clinica (SPM12) · FreeSurfer · scikit-learn · Google Cloud

## Status

**Milestone I:** literature review complete (21 sources), datasets selected, ADNI access granted, initial data exploration done. Preprocessing and baseline models are next.

## Repository structure (planned)

    EarlyMind/
    ├── data/            # scripts only, no data files
    ├── preprocessing/   # Clinica pipelines and quality control
    ├── models/          # SVM, regional classifier, 3D CNN
    ├── evaluation/      # metrics and external testing
    └── notebooks/       # data exploration
