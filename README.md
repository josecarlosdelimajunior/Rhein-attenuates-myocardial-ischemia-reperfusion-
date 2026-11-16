Rhein attenuates myocardial ischemia–reperfusion injury by suppressing NF-κB–driven inflammatory priming
![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24234374.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
Analysis notebooks for the Research Letter of the same name (J Am Heart Assoc, submitted).
Every panel of Figure 1 comes from one of the notebooks below, computed from the raw values in the Zenodo record. Nothing reported in the Letter is a number typed in by hand — run the notebook and you get it back, statistics included.
Notebooks
Notebook	Panel	Reads
`Panel1A_v3_rt_pcr_diacerein_analysis.ipynb`	1A	`rt_pcr.xlsx`
`Panel1B_WB_foldchange_figure.ipynb`	1B	`WB_Fig1DE_analysis.xlsx`
`Panel1C_D_v15_RNAseq_CtrlVsDiacerein_v15.ipynb`	1C, 1D	`counts.txt`, `tpm.txt`
`Panels1E-F_Infarct_size_figures.ipynb`	1E, 1F	`Infarct_size_analysis.xlsx`
`NFkB_p65_analysis.ipynb`	text result	NF-κB p65 ELISA workbook
<details>
<summary><b>What each notebook computes</b></summary>
<br>
Panel 1A — RT-qPCR. Ct values to fold change against Gapdh, iterative Grubbs outlier screening on log2 fold change, Welch tests with Benjamini–Hochberg correction across the eight transcripts, and a two-way repeated-measures ANOVA (treatment × myocardial area) as a supporting analysis. Writes the panel, the statistics table and the legend text.
Panel 1B — Western blot. Densitometry normalised to the same-lane loading control on the same membrane, activation ratios formed within a membrane, Welch tests on log2 fold change.
Panels 1C–D — RNA sequencing. QC and PCA, DESeq2 differential expression from the RSEM count matrix, GO over-representation via g:Profiler, KEGG GSEA by permutation. Both the primary and the full-cohort analyses run on every execution.
Panels 1E–F — Infarct size. Per-slice planimetry summed per heart to an area-weighted infarct ratio, slice-level QC, Welch tests and one-way ANOVA. Reads either the cleaned workbook or the original.
NF-κB p65. Background correction against the non-specific-binding well, Welch test, Cohen's d.
</details>
Each notebook is self-contained — it reads its own workbook, applies its own filtering, and writes its figure, statistics table and a written report. They do not depend on each other and run in any order.
Running them
Open any notebook in Colab by prefixing its URL:
```
https://colab.research.google.com/github/josecarlosdelimajunior/Rhein-attenuates-myocardial-ischemia-reperfusion-/blob/main/<notebook>
```
The first cell offers a file picker for the input workbook. To run locally, put the workbook beside the notebook and run all cells.
Dependencies are `numpy`, `pandas`, `scipy`, `matplotlib` and `openpyxl` — all preinstalled in Colab — plus `pydeseq2` and `gprofiler-official` for the transcriptomics notebook, which installs them itself.
Figures for submission are drawn at their physical print size with 8 pt type, so they drop into the assembled figure without rescaling.
Data availability
Raw data, source data, and detailed methods for all experiments are publicly available on Zenodo (doi:10.5281/zenodo.24234374). Data from bulk RNA sequencing of rat heart are available from Gene Expression Omnibus (GEO) under accession GSE354658.
The Zenodo record holds the input workbooks, the figure files, and the Supplementary Methods document the Letter cites. A copy of these notebooks is archived there too, so the analysis stays citable and version-fixed even as this repository changes.
Reading the output
> [!NOTE]
> **Error bars differ by panel**, and each legend says which. Infarct-size panels show mean ± SD. RT-qPCR and western blot panels show the back-transformed geometric mean with SEM computed on the log2 scale, because ratio data are log-normal and a mean of raw fold changes is biased upward.
Ratio data are analysed on the log2 scale. Fold changes, RQ values and densitometry ratios are log2-transformed before any test.
Exclusions are variables, not deletions. Every animal, heart or slice left out is named in the Supplementary Methods with its reason, and each notebook keeps the exclusion in a set you can empty to recover the fuller analysis — `PRIMARY_DROP` in the RNA-seq notebook, `EXCLUDE` in the infarct-size notebook.
Where a correction is applied, the corrected value is what's reported. Figure 1A reports Benjamini–Hochberg-corrected p values across the eight transcripts, on which no transcript differs significantly; uncorrected values are printed alongside in the notebook's report.
Citing
> de Lima-Junior JC, Carmo HRP, et al. Rhein attenuates myocardial ischemia–reperfusion injury by suppressing NF-κB–driven inflammatory priming. *J Am Heart Assoc.* (submitted)
If you use the data or the analysis itself, please also cite the archived record:
> de Lima-Junior JC, Carmo HRP, et al. Source data, analysis notebooks and supplementary methods for: Rhein attenuates myocardial ischemia–reperfusion injury by suppressing NF-κB–driven inflammatory priming. Zenodo; 2026. doi:10.5281/zenodo.24234374
Code here is released under the MIT License (see `LICENSE`). The deposited data and methods carry CC BY 4.0.
Corresponding author — Andrei C. Sposito, MD, PhD · sposito@unicamp.br
