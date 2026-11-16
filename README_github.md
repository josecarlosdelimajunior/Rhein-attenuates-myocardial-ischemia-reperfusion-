# Rhein attenuates myocardial ischemia–reperfusion injury by suppressing NF-κB–driven inflammatory priming

Analysis notebooks for the Research Letter of the same name (J Am Heart Assoc, submitted).

Every panel of Figure 1 is produced by one of the notebooks below, from the raw values in the
Zenodo record. Nothing reported in the Letter is a number typed in by hand — run the notebook and
you get it back, including the statistics.

---

## Notebooks

| Notebook | Panel | Reads | Produces |
| --- | --- | --- | --- |
| [`Panel1A_v3_rt_pcr_diacerein_analysis.ipynb`](Panel1A_v3_rt_pcr_diacerein_analysis.ipynb) | 1A | `rt_pcr.xlsx` | Fold changes, Grubbs screening, two-way repeated-measures ANOVA, panel + legend text |
| [`Panel1B_WB_foldchange_figure.ipynb`](Panel1B_WB_foldchange_figure.ipynb) | 1B | `WB_Fig1DE_analysis.xlsx` | Densitometry normalisation, Welch tests on log2 fold change, panel |
| [`Panel1C_D_v15_RNAseq_CtrlVsDiacerein_v15.ipynb`](Panel1C_D_v15_RNAseq_CtrlVsDiacerein_v15.ipynb) | 1C, 1D | `counts.txt`, `tpm.txt` | QC and PCA, DESeq2 differential expression, GO over-representation, KEGG GSEA, volcano + pathway panels |
| [`Panels1E-F_Infarct_size_figures.ipynb`](Panels1E-F_Infarct_size_figures.ipynb) | 1E, 1F | `Infarct_size_analysis.xlsx` or the original `Infarct_Size.xlsx` | Per-heart infarct size, slice QC, Welch tests and one-way ANOVA, both panels |
| [`NFkB_p65_analysis.ipynb`](NFkB_p65_analysis.ipynb) | text result | NF-κB p65 ELISA workbook | Background correction, Welch test, effect size |

Each notebook is self-contained: it reads its own workbook, applies its own filtering, and writes
its figure, its statistics table and a written report. They do not depend on each other and can be
run in any order.

---

## Running them

These were written for Google Colab. Open any notebook there directly:

```
https://colab.research.google.com/github/josecarlosdelimajunior/Rhein-attenuates-myocardial-ischemia-reperfusion-/blob/main/<notebook>
```

The first cell offers a file picker for the input workbook. Locally, put the workbook beside the
notebook and run all cells.

Dependencies are `numpy`, `pandas`, `scipy`, `matplotlib` and `openpyxl`, all preinstalled in
Colab, plus `pydeseq2` and `gprofiler-official` for the transcriptomics notebook, which installs
them in its own first cell. Figures intended for submission are drawn at their physical print size
with 8 pt type, so they drop into the assembled figure without rescaling.

---

## Data availability

The notebooks are here; the data they read are not.

Raw data, source data, and detailed methods for all experiments are publicly available on Zenodo
(doi:[10.5281/zenodo.24234374](https://doi.org/10.5281/zenodo.24234374)). Data from bulk RNA
sequencing of rat heart are available from Gene Expression Omnibus (GEO) under accession
[GSE354658](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE354658).

The Zenodo record holds the input workbooks each notebook reads, the figure files, and the
Supplementary Methods document the Letter cites for everything it has no room to describe. A copy
of these notebooks is archived there too, so the analysis remains citable and fixed even as this
repository changes.

## Things to know before reading the output

**Error bars differ by panel**, and each legend says which it is. The infarct-size panels show
mean ± SD; the RT-qPCR and western blot panels show the back-transformed geometric mean with SEM
computed on the log2 scale, because ratio data are log-normal and a mean of raw fold changes is
biased upward.

**Ratio data are analysed on the log2 scale** throughout — fold changes, RQ values and densitometry
ratios are all log2-transformed before any test.

**Exclusions are variables, not deletions.** Every animal, heart or slice left out of an analysis
is named in the Supplementary Methods with the reason, and each notebook keeps the exclusion in a
set or list you can empty to recover the fuller analysis. Two examples: the RNA-seq notebook's
`PRIMARY_DROP` holds the one treated sample excluded as a non-responder, and computes both cohorts
on every run; the infarct-size notebook's `EXCLUDE` holds two high-dose hearts, one with a
duplicated label and one with an impossible tracing.

**Where a correction is applied, the corrected value is the one reported.** The Figure 1A panel
reports Benjamini–Hochberg-corrected p values across the eight transcripts, on which no transcript
differs significantly; the uncorrected values are printed alongside in the notebook's report.

---

## Citing

> de Lima-Junior JC, Carmo HRP, et al. Rhein attenuates myocardial ischemia–reperfusion injury by
> suppressing NF-κB–driven inflammatory priming. J Am Heart Assoc. (submitted)

If you use the data or the analysis itself, please also cite the archived record, which is the
citable and version-fixed form of everything here:

> de Lima-Junior JC, Carmo HRP, et al. Source data, analysis notebooks and supplementary methods
> for: Rhein attenuates myocardial ischemia–reperfusion injury by suppressing NF-κB–driven
> inflammatory priming. Zenodo; 2026. doi:10.5281/zenodo.24234374

Code in this repository is released under the MIT License (see [`LICENSE`](LICENSE)). The deposited
data and methods carry CC BY 4.0.

Corresponding author: Andrei C. Sposito — sposito@unicamp.br
