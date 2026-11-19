# Depression Brain Connectivity Analysis

A reproducible MRI analysis project investigating structural brain characteristics and resting-state functional connectivity in depression.

The project aims to build a practical neuroimaging workflow covering MRI data organization, quality control, preprocessing, functional connectivity estimation, and exploratory group-level analysis. It is also designed as a hands-on learning project to develop practical experience with MRI data and connectomics.

> **Project status:** In development. Analyses, results, and methodological decisions will be documented as the project progresses.

## Research question

How do structural brain measures and resting-state functional connectivity differ between participants with depression and healthy controls?

A secondary methodological question is how preprocessing and denoising choices influence estimated functional connectivity.

## Dataset

The primary dataset is planned to be:

- **Dataset:** [OpenNeuro ds002748](https://openneuro.org/datasets/ds002748)
- **Data type:** Structural MRI (T1-weighted) and resting-state fMRI
- **Study population:** Participants with depression and healthy controls
- **Format:** BIDS-organized neuroimaging data

Dataset characteristics, participant counts, acquisition parameters, diagnostic labels, and missing data will be verified during the initial data audit before analysis.

The project will follow the dataset's access conditions and data-use requirements. Raw imaging data and participant-level sensitive information will not be committed to this repository.

## Planned workflow

1. **Data reconnaissance and BIDS validation**
   - Inspect the dataset structure and metadata.
   - Review participant information and imaging acquisition parameters.
   - Validate the BIDS organization.

2. **MRI quality control**
   - Run MRIQC where computational resources permit.
   - Review image quality reports and relevant acquisition metrics.
   - Identify missing data, potential artifacts, and exclusion criteria.

3. **MRI preprocessing**
   - Use fMRIPrep for resting-state fMRI preprocessing.
   - Inspect preprocessing outputs and confound regressors.
   - Explore structural MRI outputs where feasible.

4. **Functional connectivity**
   - Extract regional time series using a predefined brain parcellation.
   - Estimate Pearson correlation-based functional connectivity matrices.
   - Apply Fisher z-transformation where appropriate.

5. **Denoising sensitivity analysis**
   - Compare selected nuisance-regression strategies.
   - Examine the influence of motion and other confounds on connectivity estimates.
   - Evaluate quality-control measures such as framewise displacement and QC-FC relationships.

6. **Exploratory group analysis**
   - Compare connectivity patterns between depression and control groups.
   - Account for relevant confounders where justified.
   - Report effect sizes, uncertainty, and multiple-comparison correction where appropriate.

7. **Reproducibility and reporting**
   - Document software versions, configuration choices, and analysis decisions.
   - Maintain scripts and analysis notes.
   - Produce figures and a concise research report.

## Tools and technologies

| Area | Planned tools |
|---|---|
| Neuroimaging data organization | BIDS, NIfTI |
| Quality control | MRIQC |
| fMRI preprocessing | fMRIPrep |
| Functional connectivity | Nilearn |
| Statistical analysis | Python, SciPy, statsmodels |
| Machine learning, if feasible | scikit-learn |
| Version control | Git, GitHub |
| Reproducibility | Docker or Apptainer |

## Repository structure

```text
depression-brain-connectivity-analysis/
│
├── README.md
├── .gitignore
├── environment.yml
│
├── configs/
│   └── analysis_config.yaml
│
├── notebooks/
│   ├── 01_dataset_exploration.ipynb
│   ├── 02_quality_control.ipynb
│   └── 03_functional_connectivity.ipynb
│
├── scripts/
│   ├── validate_bids.py
│   ├── run_mriqc.sh
│   ├── run_fmriprep.sh
│   └── extract_connectivity.py
│
├── src/
│   └── connectivity_analysis/
│
├── reports/
│   └── figures/
│
└── docs/
    └── analysis_notes.md
```

This is the intended structure and may change as the workflow develops.

## Current priorities

- [ ] Inspect the dataset and verify participant information.
- [ ] Validate the BIDS structure.
- [ ] Review representative T1-weighted and resting-state fMRI images.
- [ ] Run a small MRIQC pilot.
- [ ] Run an fMRIPrep pilot on a small number of participants.
- [ ] Extract regional resting-state time series.
- [ ] Generate and inspect functional connectivity matrices.
- [ ] Compare denoising strategies.
- [ ] Perform exploratory group-level analysis.
- [ ] Document the complete workflow and findings.

## Important methodological considerations

- Functional connectivity represents statistical relationships between regional BOLD time series. It should not be interpreted as direct evidence of anatomical connections or causal communication.
- Head motion and physiological noise can substantially affect resting-state connectivity estimates.
- Diagnostic group comparisons must account for relevant confounders and multiple testing.
- Given the expected modest sample size, any predictive modelling will be exploratory and interpreted cautiously.
- Clinical scores that define or closely characterize diagnostic groups will not be used as independent predictors of those same group labels.

## References and resources

- [OpenNeuro dataset ds002748](https://openneuro.org/datasets/ds002748)
- [Bezmaternykh et al. (2021), Brain Networks Connectivity in Mild to Moderate Depression](https://doi.org/10.1155/2021/8846097)
- [fMRIPrep documentation](https://fmriprep.org/en/stable/)
- [MRIQC documentation](https://mriqc.readthedocs.io/en/stable/)
- [Nilearn documentation](https://nilearn.github.io/stable/)
- [BIDS tutorials](https://bids-website.readthedocs.io/en/latest/getting_started/tutorials/)

## Disclaimer

This repository is an independent research and learning project. It is not a clinical diagnostic tool, and its exploratory findings should not be interpreted as clinical evidence.