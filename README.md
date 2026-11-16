Rhein attenuates myocardial ischemia–reperfusion injury by suppressing NF-κB–driven inflammatory priming
Source data, analysis code and supplementary methods
This record holds the data behind every panel of the Research Letter, the notebooks that
produced them, and the full methods, which the Letter itself has no room to carry.
Letter: de Lima-Junior JC, Carmo HRP, et al. Rhein attenuates myocardial ischemia–reperfusion
injury by suppressing NF-κB–driven inflammatory priming.
Corresponding author: Andrei C. Sposito, MD, PhD — sposito@unicamp.br
License: CC BY 4.0
RNA sequencing is not in this record. Raw reads and processed tables are in NCBI GEO under
accession GSE354658.
Zenodo: DOI: 10.5281/zenodo.24234374.
---
Start here
`Supplementary\\\_Methods\\\_Rhein\\\_IR.docx` is the methods document the Letter cites. It describes the
animals, the Langendorff protocols, every assay, and the statistical treatment of each panel,
and it is the right place to look before interpreting any file below.
Each analysis is a self-contained Jupyter notebook that reads its own workbook and regenerates
the figure and the statistics from the raw values. Nothing reported in the Letter is a number
typed in by hand: run the notebook and you get it back. The notebooks were written for Google
Colab and need only `numpy`, `pandas`, `scipy`, `matplotlib`, `openpyxl` and, for the
transcriptomics, `pydeseq2` and `gprofiler-official`.
---
What is in the record
Methods
File	Contents
`Supplementary\\\_Methods\\\_Rhein\\\_IR.docx`	Full methods for the Research Letter: animals and ethics, ex vivo I/R protocols, assays, statistics, primer table, software versions
Figure 1A — RT-qPCR, inflammasome and pyroptosis panel
File	Contents
`rt\\\_pcr.xlsx`	Raw Ct values, risk and non-risk myocardium, control and diacerein
`rt\\\_pcr\\\_diacerein\\\_analysis.ipynb`	ΔCt → RQ → fold change, Grubbs outlier screening, two-way repeated-measures ANOVA, figure
`rtpcr\\\_stats\\\_report.txt`, `rtpcr\\\_stats\\\_table.csv`	Per-gene statistics as the notebook prints them
`rtpcr\\\_anova\\\_2way.csv`, `rtpcr\\\_anova\\\_posthoc.csv`	Two-way ANOVA effects and Šidák post hoc comparisons
Eight transcripts (Casp1, Casp3, Casp7, Gsdmd, Nlrp3, Pycard, Il1b, Il18),
normalised to Gapdh, in 15 vehicle and 15 diacerein animals (14 diacerein for Nlrp3 and
Il1b after Grubbs screening).
Figure 1A reports one comparison: diacerein versus vehicle in the ischemic area, by Welch's
unequal-variance t-test on log2 fold change with Benjamini–Hochberg correction across the eight
transcripts. No transcript reaches significance. The largest effect is a 0.70-fold reduction
of Il1b (uncorrected p = 0.116, corrected p = 0.310). Bars are drawn relative to the vehicle
control of the same area, so the reference line at 1 is the group being tested against.
Because each heart contributes both a risk and a non-risk sample, the notebook also fits a 2 × 2
split-plot model with treatment between animals and area within animal. That model gives Il1b a
treatment main effect of F(1,27) = 4.96, p = 0.034 uncorrected — but 0.276 after correction across
the eight transcripts, so it does not change the conclusion. Both analyses are in the notebook and
in the CSVs above; earlier drafts of this work quoted the uncorrected value, and the Letter now
reports the corrected within-area comparison.
Figure 1B — Western blotting
File	Contents
`WB\\\_Fig1DE\\\_analysis.xlsx`	Integrated densities from manual ImageJ quantification
`WB\\\_foldchange\\\_figure.ipynb`	Normalisation, Welch tests on log2 fold change, figure
`Unedited\\\_blot\\\_and\\\_gel\\\_images.pdf`	Uncropped blots and gels
Nine quantities are reported. Every target is divided by its same-lane loading control on the
same membrane, and the two activation ratios (caspase-1 p20 / pro-caspase-1, GSDMD-NT / GSDMD-FL)
are formed within a membrane.
Figures 1C and 1D — RNA sequencing
Reads and processed tables are in GEO, not here. This record holds the re-analysis:
File	Contents
`RNAseq\\\_CtrlVsDiacerein\\\_v15.ipynb`	Differential expression from the RSEM count matrix, QC and PCA, GO over-representation, KEGG GSEA, volcano and pathway figures
`rnaseq\\\_v12\\\_results.xlsx`	Differentially expressed genes, GO and pathway results
`volcano\\\_primary.pdf`, `GSEA\\\_KEGG\\\_DvsC.pdf`	Panels 1C and 1D
All six sequenced samples are deposited in GEO. One treated sample (D4) clustered with the
vehicle group on the principal component analysis and was treated as a non-responder and excluded
before differential expression, so the primary comparison is three vehicle versus two diacerein.
D4 is not a technical outlier — it has the largest library and the highest RIN of the six — and
the exclusion rests on a biological interpretation. The notebook computes both cohorts on every
run, and the methods document reports the sensitivity analysis in full. Anyone who prefers the
three-versus-three comparison can read it straight off the same notebook.
Figures 1E and 1F — infarct size
File	Contents
`Infarct\\\_size\\\_analysis.xlsx`	Per-slice planimetry in pixels, per-heart sums, group statistics. Live formulas throughout, with a README sheet
`Infarct\\\_size\\\_figures.ipynb`	Reads either this workbook or the original `Infarct\\\_Size.xlsx` and redraws both panels
`hearts\\\_corrected.csv`	The per-heart table the figures are drawn from
`infarct\\\_rhein.pdf`, `infarct\\\_diacerein.pdf`	Panels 1E and 1F
Infarct size is the area-weighted ratio: slice areas are summed per heart before the ratio is
taken, not averaged across slices. Area at risk as a percentage of left ventricular area is
reported alongside as a check that the risk zone was comparable between groups.
Three exclusions are recorded, all in the high-dose oral diacerein group and all applied before
analysis. One slice had unreadable areas (heart 1, slice 4). One block of five slices carried a
heart label duplicating an animal already in the dataset, held entirely different pixel data, and
could not be traced to an animal. One heart (heart 8) had only four usable slices and a slice
whose risk tracing covered the whole left ventricle, which is not physically possible. Both heart
exclusions agree with the TTC image archive, which holds seven high-dose hearts against eight
controls and six low-dose animals. The notebook's `EXCLUDE` set makes all of this reversible:
empty it and the earlier nine-heart analysis comes back.
Text results
File	Contents
`NFkB\\\_p65\\\_analysis.ipynb` + workbook	NF-κB p65 DNA-binding ELISA, rhein 60 µM vs vehicle in LPS-stimulated H9c2 cells
Caspase-1 activity files	Cell-free colorimetric assay, rhein 10–60 µM
---
Conventions used throughout
Error bars differ by panel, and the figure legend says which is which. The infarct-size panels
show mean ± SD. The RT-qPCR and western blot panels show the back-transformed geometric mean with
SEM computed on the log2 scale, because ratio data are log-normal and a mean of raw fold changes
is biased upward. Individual animals are plotted in every panel.
Ratio data are analyzed on the log2 scale. Fold changes, RQ values and densitometry ratios are
log2-transformed before any test.
Tests are two-sided, with Welch's unequal-variance t-test as the default two-group test.
Where a panel carries several tests, the correction applied — or the decision not to correct — is
stated per panel in the methods document rather than assumed.
Exclusions are recorded, never silent. Every animal, heart, slice or value left out is named
in the methods document with the reason, and the notebooks keep the exclusion as a variable you
can empty to recover the fuller analysis.
---
Citing this record
de Lima-Junior JC, Carmo HRP, et al. Supplementary Methods and source data for: Rhein attenuates
myocardial ischemia–reperfusion injury by suppressing NF-κB–driven inflammatory priming. Zenodo;
2026. DOI: 10.5281/zenodo.24234374.
