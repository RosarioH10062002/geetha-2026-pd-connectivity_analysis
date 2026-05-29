# Graph-Theoretical Analysis of Resting-State Functional Connectivity in Parkinson’s Disease Depression

This repository contains a graph theory based analytical pipeline applied to the resting-state fMRI region-of-interest connectivity data of patients suffering from Parkinson’s disease with or without depressive disorder. This analytical pipeline involves the use of 15 literature-based regions of interest covering Default Mode Network (DMN), Salience Network (SN), and Frontoparietal Network (FPN). The networks were chosen based on their relevance to emotional processing, cognitive control, and connectivity alterations related to depression in Parkinson’s disease patients.


---

## Overview

The notebook performs the graph theoretical analysis of the ROIs' time-series obtained from the CONN-processed resting-state fMRI data. Functional connectivity matrices are generated for every individual, normalized based on the differences between scanner manufacturers through ComBat correction, and represented as undirected and weighted graphs. Afterwards, both global and nodal metrics are derived at various proportional density levels.

The purpose of this study is to establish whether there exists an association between depression and changes in the network organization within certain brain regions.

---

## Groups

The analysis includes three participant groups:

| Group | Description |
|---|---|
| CTRL | Healthy controls |
| PDND | Parkinson’s disease without depression |
| PDD | Parkinson’s disease with depression |

The final analysis used all available participants from the preprocessed folders:

| Group | N |
|---|---:|
| CTRL | 32 |
| PDND | 32 |
| PDD | 26 |

---

## Pipeline

The notebook performs the following steps:

1. Load ROI time series from CONN-preprocessed data.
2. Compute ROI-to-ROI Pearson correlation matrices.
3. Apply Fisher-Z transformation.
4. Harmonize connectivity features using ComBat.
5. Reconstruct harmonized connectivity matrices.
6. Convert matrices into undirected weighted graphs using absolute edge weights.
7. Apply proportional thresholding across densities from 0.10 to 0.30.
8. Compute global and nodal graph metrics at each density.
9. Calculate area under the curve across densities for each metric.
10. Perform pairwise group comparisons using Mann–Whitney U tests.
11. Apply Benjamini–Hochberg (BH) FDR correction.
12. Save result tables and generate summary plots.

---

## Graph Metrics

### Global metrics

| Metric | Meaning |
|---|---|
| Weighted strength | Overall network connectivity |
| Global efficiency | Global integration |
| Clustering coefficient | Network segregation / local specialization |
| Betweenness centrality | Global centrality / shortest-path mediation |

### Nodal metrics

| Metric | Meaning |
|---|---|
| Nodal strength | Regional connectivity |
| Nodal clustering coefficient | Regional local segregation |
| Nodal betweenness centrality | Regional shortest-path centrality |
| Participation coefficient | Cross-network participation |
| Within-module strength z-score | Within-network integration |

---

## Statistical Analysis

The main pairwise comparisons (*using two-sided Mann–Whitney U tests*) are:

- CTRL vs PDD
- PDND vs PDD

FDR correction is applied across metrics within each comparison using the BH technique.

---

## Main Findings

No global graph metric survived FDR correction.

Exploratory uncorrected nodal findings were observed for the CTRL vs PDD comparison:

| Metric | ROI | Direction in PDD |
|---|---|---|
| Nodal participation | DMN lateral parietal cortex, right | Lower |
| Nodal clustering | FPN posterior parietal cortex, left | Higher |
| Within-module strength z-score | DMN medial prefrontal cortex | Lower |

These results were not significant after correction for multiple comparisons and hence should be treated as exploratory. Nevertheless, the spatial pattern of these effects is in line with the existing literature suggesting involvement of the mPFC-based DMN and fronto-parietal network in PD depression.

---

## Requirements

The notebook requires the Python packages below to run:

```text
numpy
pandas
matplotlib
seaborn
scipy
statsmodels
nilearn
bctpy
neuroHarmonize
neuroCombat