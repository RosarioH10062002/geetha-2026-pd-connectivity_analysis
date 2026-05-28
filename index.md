# Characterization of large-scale brain connectivity patterns associated with depression in Parkinson’s disease

Abstract:
Depression is a prevalent and disabling non-motor symptom of Parkinson’s disease (PD), substantially contributing to cognitive decline and reduced quality of life. Resting-state functional MRI (rs-fMRI) provides a non-invasive approach to investigate large-scale network alterations associated with psychiatric manifestations in PD. In this study, we investigated whether resting-state connectivity patterns could serve as candidate markers of depression in PD using data from 90 participants from the Parkinson’s Progression Markers Initiative (PPMI). Connectivity was assessed using complementary seed-based connectivity (SBC), ROI-to-ROI functional connectivity, and graph-theoretical analyses across 15 regions spanning the default mode (DMN), salience (SN), and frontoparietal (FPN) networks. SBC analysis revealed significant connectivity differences between PD patients with depression (PDD) and without depression (PDND), identifying alterations involving the medial prefrontal cortex (mPFC), dorsal anterior cingulate cortex (dACC), superior parietal lobule (SPL), and supramarginal gyrus (SMG). ROI-based functional connectivity further identified convergent alterations within mPFC-centered DMN connectivity, showing negative associations between depressive symptom severity and functional connectivity measures. Based on these convergent findings, a composite DMN connectivity score was constructed, revealing a progressive decrease in connectivity across groups and significant differences between PDD and controls. Collectively, these findings highlight mPFC-centered DMN connectivity as a potential marker associated with depression in Parkinson’s disease.

Keywords: PPMI, seed-based connectivity, graph theory, functional connectivity, geriatric depression scale, resting-state fMRI

---

# Introduction
Depression is a prevalent and disabling non-motor symptom of Parkinson’s disease (PD), affecting up to 50\% of patients and exacerbating motor and cognitive decline. Its multifactorial etiology involves demographic, clinical, and neurocognitive factors [@cong_prevalence_2022]; however, the underlying neural mechanisms remain poorly understood. While motor network dysfunction in PD has been extensively characterized, depression-related connectivity alterations, particularly within the default mode and limbic networks [@morgan_altered_2018], [@xu_altered_2022], remain heterogeneous. Given this heterogeneity, we focused on large-scale resting-state networks most consistently implicated in depression, particularly the default mode network (DMN), because the DMN supports self-referential and affective processing and contains hubs, notably the medial prefrontal cortex (mPFC), that show reproducible connectivity alterations in major depression [@zheng_beyond_2026], @zhang_dysfunction_2024, @sheline_default_2009].

This study investigates resting-state connectivity as a potential marker of depression in PD using Parkinson’s Progression Markers Initiative (PPMI) data. We analyzed rs-fMRI, T1-weighted imaging, and Geriatric Depression Scale (GDS) scores from 90 participants. Functional connectivity was evaluated through seed-based and ROI-to-ROI approaches focusing on 15 regions spanning the default mode (DMN), salience (SN), and frontoparietal (FPN) networks, given their reported involvement in depression and PD. In addition, graph-theoretical analysis was employed to characterize alterations in large-scale network organization, including global integration and local segregation. 

We hypothesized that depression in PD would be associated with altered large-scale network organization, particularly within the DMN, and that medial prefrontal cortex (mPFC)-centered connectivity alterations would emerge as a potential marker associated with depressive symptom severity. 

---
# Methods 
## Data & Participants
A total of 90 participants from the [PPMI dataset](https://www.ppmi-info.org/access-data-specimens/download-data), supported by the Michael J. Fox Foundation for Parkinson’s Research [@marek_parkinson_2011], were categorized into Healthy Controls (CTRL), Parkinson’s Disease without Depression (PDND), and Parkinson’s Disease with Depression (PDD), using a Geriatric Depression Scale (GDS) threshold of $\geq 5$ for the PDD group.

Data included 3T rs-fMRI, T1-weighted images, demographics, and clinical metrics. To address scanner heterogeneity, we used a harmonization procedure (see Supplementary Material).

Acquisition parameters were consistent across sites (TR = 2.5 s, 240 volumes), with comprehensive characteristics detailed in Table 1 and Table 2.

## Table 1. Participant characteristics across groups

| Group | N | Age (mean ± SD) | Sex (M/F) | GDS (mean ± SD) |
|---|---|---|---|---|
| CTRL | 32 | 65.67 ± 12.37 | 18/14 | – |
| PDND | 32 | 64.06 ± 10.52 | 19/13 | 1.03 ± 1.31 |
| PDD | 26 | 62.91 ± 9.73 | 18/8 | 6.88 ± 2.29 |

## Table 2. Distribution of participants across MRI scanner manufacturers

| Group | Siemens | Philips | GE Medical |
|---|---|---|---|
| CTRL | 24 | 4 | 4 |
| PDND | 24 | 4 | 4 |
| PDD | 18 | 4 | 4 |

## Preprocessing & ROI Definition

Functional and anatomical MRI data were preprocessed using the default preprocessing pipeline implemented in the CONN toolbox (CONNv25.b; [@nieto-castanon_conn_2022]), which is widely used in functional connectivity studies. Detailed preprocessing steps are provided in the Supplementary Material.

Following preprocessing, 15 regions of interest (ROIs) spanning the Default Mode Network (DMN), Salience Network (SN), and Frontoparietal Network (FPN) were selected from the CONN network atlas (Table 3). These networks were chosen based on their reported involvement in cognitive and emotional processing and their relevance to non-motor symptoms in Parkinson’s disease [@menon_large-scale_2011; @liao_networks_2021].

## Table 3. CONN toolbox network region of interest (ROI) definitions

| Network | Seed | x | y | z |
|---|---|---|---|---|
| Salience network (SAL) | Mid-cingulate cortex | 0 | 22 | 35 |
| Salience network (SAL) | Anterior insula (L) | -44 | 13 | 1 |
| Salience network (SAL) | Anterior insula (R) | 47 | 14 | 0 |
| Salience network (SAL) | Rostral prefrontal cortex (L) | -35 | 45 | 27 |
| Salience network (SAL) | Rostral prefrontal cortex (R) | 32 | 46 | 27 |
| Salience network (SAL) | Supramarginal gyrus (L) | -60 | -39 | 31 |
| Salience network (SAL) | Supramarginal gyrus (R) | 62 | -35 | 32 |
| FrontoParietal network (FPN) | Lateral prefrontal cortex (L) | -43 | 33 | 28 |
| FrontoParietal network (FPN) | Posterior parietal cortex (L) | -46 | -58 | 49 |
| FrontoParietal network (FPN) | Lateral prefrontal cortex (R) | 41 | 38 | 30 |
| FrontoParietal network (FPN) | Posterior parietal cortex (R) | 52 | -52 | 45 |
| Default mode network (DMN) | Medial prefrontal cortex | 1 | 55 | -3 |
| Default mode network (DMN) | Lateral parietal cortex (L) | -39 | -77 | 33 |
| Default mode network (DMN) | Lateral parietal cortex (R) | 47 | -67 | 29 |
| Default mode network (DMN) | Posterior cingulate cortex | 1 | -61 | 38 |

*Note: Coordinates are reported in Montreal Neurological Institute (MNI) space. L = left hemisphere; R = right hemisphere.*

## Connectivity Analyses

Connectivity analyses were performed in two stages. An initial seed-based connectivity (SBC) analysis was conducted in a homogeneous subset of participants acquired using the same scanner manufacturer (16 PDD, 20 PDND) to identify connectivity differences across groups. Subsequently, the study was extended to a larger multicenter cohort (N = 90, Table 2) using ComBat harmonization (see Supplementary Material), where ROI-based functional connectivity and graph analyses were performed to evaluate whether connectivity alterations were associated with depressive symptom severity (GDS).

### Seed-Based Connectivity Analysis

First-level seed-based connectivity maps were generated from the 15 predefined network ROIs using bivariate correlations within the CONN toolbox (CONNv25.b [@nieto-castanon_conn_2022]), followed by Fisher-Z transformation. At the second level, group-level connectivity differences were evaluated using the model:

$$
SBC = \beta_1(Control) + \beta_2(PDND) + \beta_3(PDD) + \beta_4(Outliers) + \epsilon
$$

where *SBC* represents seed-based connectivity strength and *Control*, *PDND*, and *PDD* serve as indicator variables for each diagnostic category, while *Outliers* accounts for the quality assurance covariate of excluded subjects. Differences across seeds were assessed using a multivariate omnibus F-test. Statistical significance was defined at voxel-level $p < 0.001$ and cluster-level FDR correction ($p_{FDR} < 0.05$) based on Gaussian Random Field theory. Detailed preprocessing steps are provided in the Supplementary Material.

### Functional Connectivity Analysis

ROI-based functional connectivity matrices were estimated using Pearson correlations between the predefined network ROIs and Fisher-Z transformed prior to harmonization.

Associations between connectivity and depressive symptom severity were evaluated using generalized linear models implemented in Python ([Statsmodels](https://www.statsmodels.org/stable/api.html)):

$$
FC_{ROI} = \beta_0 + \beta_1(GDS) + \beta_2(Sex) + \beta_3(Age) + \epsilon
$$

where *FC$_{ROI}$* represents ROI-to-ROI functional connectivity values and *GDS* denotes depressive symptom severity.
Multiple comparisons were controlled using FDR correction ($p_{FDR} < 0.05$). Graph-theoretical measures were subsequently derived from the harmonized connectivity matrices.

### Graph-Theoretical Analysis

Subject-level weighted connectivity matrices served as inputs to construct undirected weighted graphs across the 15 ROIs. They were converted to absolute weighted matrices, and diagonal elements were set to zero. Following standard graph theory approaches [bullmore_complex_2009, @rubinov_complex_2010] and using BCTpy-0.6.1 (Brain Connectivity Toolbox), graphs were thresholded across densities from 0.10 to 0.30 in steps of 0.05, and area under the curve (AUC) values were computed across densities for all metrics. The analysis included global metrics, including weighted strength, clustering coefficient, global efficiency, and betweenness centrality, as well as local metrics, including nodal strength, clustering coefficient, betweenness centrality, participation coefficient, and within-module strength z-score to characterize regional connectivity patterns [@sporns_graph_2018]. Group comparisons were performed using Mann–Whitney U tests with FDR correction.

# Results and Discussion

(@figure-main) summarizes the main findings.

Seed-based connectivity analysis revealed significant group-level differences between PDD and PDND, identifying four clusters of altered connectivity involving the left superior parietal lobule (SPL), medial prefrontal cortex (mPFC)/dorsal anterior cingulate cortex (dACC), right middle temporal gyrus (MTG), and right supramarginal gyrus (SMG) (Figure 1; Table 4A). The primary cluster was located in the left intraparietal sulcus (IPS)/SPL (cluster size $k = 209$, $p_{FDR} = 0.001890$), while the remaining clusters involved mPFC/dACC ($k = 101$), MTG ($k = 97$), and SMG ($k = 96$; all $p_{FDR} = 0.028392$). These findings suggest altered large-scale connectivity involving the DMN, salience, and frontoparietal networks in PDD. Altered mPFC/dACC connectivity, regions implicated in self-referential and emotional processing [@levorsen_decomposing_2025; @yun_functional_2022], may reflect depression-related network alterations previously reported in Parkinsonian populations [@su_altered_2022; @liao_networks_2021]. Altered IPS and SMG connectivity may further indicate frontoparietal reorganization associated with disrupted basal ganglia-thalamocortical circuitry [@liu_resting-state_2022].

ROI-based functional connectivity analysis identified convergent alterations within key DMN connections, including mPFC–left LP, mPFC–right LP, and mPFC–PCC (Figure 1; Table 4B). All associations showed negative beta coefficients, indicating reduced DMN connectivity with increasing depressive symptom severity (GDS). Although these findings did not survive multiple comparison correction, they were further explored due to their consistency with previous studies reporting reduced DMN connectivity in major depressive disorder and recurrent depression [@tozzi_reduced_2021; @yan_reduced_2019; @yuan_functional_2011].

Graph-based analysis provided a complementary evaluation of network topology across DMN, SN, and FPN. None of the global metrics showed significance; however, exploratory nodal effects were observed in the left frontoparietal posterior parietal cortex, right DMN lateral parietal cortex, and DMN mPFC (Table 4C), indicating possible alterations in cross-network participation, local segregation, and within-module integration. Although these effects did not survive FDR correction, their regional distribution aligns with previous findings demonstrating a relationship between DMN and FPN alterations and depressive symptoms in PD, as well as altered FPN modular organization in depression [@lan_decreased_2022; @wei_aberrant_2017].

Based on the convergent SBC, ROI-based, and graph-theoretical findings centered on the mPFC, a composite DMN connectivity score was constructed to further explore DMN alterations associated with depressive symptoms. Significant group differences ($p < 0.05$) were observed between PDD and control subjects, showing a progressive decrease in DMN connectivity across groups (Figure 1; Table 4). These findings suggest that mPFC-centered DMN connectivity may represent a potential marker associated with depression in Parkinson’s disease, consistent with the established role of the mPFC in emotional processing and stress-related responses [@pizzagalli_prefrontal_2022; @bittar_functional_2021].

## Table 4A. Significant clusters from seed-based connectivity analysis

| Cluster (coord) | Size (k) | $p_{unc}$ | $p_{FDR}$ |
|---|---|---|---|
| −36 −66 +54 | 209 | 0.000040 | 0.001890 |
| −02 +26 +32 | 101 | 0.001964 | 0.028392 |
| +36 −60 +18 | 97 | 0.002317 | 0.028392 |
| +66 −32 +40 | 96 | 0.002416 | 0.028392 |

---

## Table 4B. Uncorrected mPFC-centered functional connectivity findings

| ROI (coord) | $\beta$ | $p_{unc}$ | $p_{FDR}$ |
|---|---|---|---|
| DMN.MPFC → DMN.LP (L) | -0.023332 | 0.011707 | 0.892914 |
| DMN.MPFC → DMN.LP (R) | -0.021428 | 0.033765 | 0.892914 |
| DMN.MPFC → DMN.PCC | -0.023941 | 0.036295 | 0.892914 |

---

## Table 4C. Uncorrected graph-theoretical findings

| Metric | ROI (coord) | Effect Size | $p_{unc}$ | $p_{FDR}$ |
|---|---|---|---|---|
| Nodal participation | DMN.LP (R) | -0.021308 | 0.032826 | 0.492393 |
| Nodal clustering | FPN.PPC (L) | 0.019115 | 0.040591 | 0.522919 |
| Within-module strength z-score | DMN.MPFC | -0.011111 | 0.048238 | 0.723570 |

---

## Table 4D. Group comparison of mPFC-centered DMN connectivity scores

| Comparison | Test | $p$ |
|---|---|---|
| Global | Kruskal–Wallis | 0.0108 |
| CTRL vs PDD | Post-hoc | 0.0043 |
| CTRL vs PDND | Post-hoc | 0.0897 |
| PDND vs PDD | Post-hoc | 0.1023 |


# Conclusion

Seed-based analysis revealed significant functional connectivity differences between PDD and PDND within DMN and frontoparietal regions in a homogeneous Siemens cohort. Extending this analysis to a larger multicenter cohort through harmonization revealed convergent trends in mPFC-centered DMN connectivity, demonstrating a negative association between depressive symptom severity (GDS) and connectivity measures. Graph-theoretical analysis supported this pattern at the regional level, showing exploratory nodal alterations in DMN and frontoparietal regions without corrected global topology differences. Furthermore, exploration using a composite DMN connectivity score demonstrated a progressive decrease in connectivity across groups, significantly differentiating PDD from control subjects.

Collectively, these findings reveal convergent evidence across seed-based, ROI-based, graph-theoretical, and composite connectivity analyses, highlighting mPFC-centered DMN alterations as a potential marker of depression in Parkinson’s disease. The progressive reduction of DMN connectivity across groups further supports the involvement of large-scale network dysfunction in depression-related processes in PD.

```{figure} figure.png Overview of mPFC-centered connectivity analyses. 
:name: figure-main
:alt: Multi-panel figure supporting the main findings

\
**A.** Seed-based connectivity results showing significant clusters associated with mPFC connectivity alterations. Labeled regions indicate significant clusters located in the Left Superior Parietal Lobule (SPL), dorsal Anterior Cingulate Cortex (dACC) / medial Prefrontal Cortex (mPFC), and Right Supramarginal Gyrus / Inferior Parietal Cortex. Spatial coordinates are reported in millimeters along the X, Y, and Z axes. The color bar represents F-values (F(14, 714)) ranging from 2.62 to 4.18.
\
**B.** ROI-to-ROI DMN connectivity patterns centered on the mPFC. Line colors represent GLM beta values, showing negative associations between functional connectivity and group progression. For visualization purposes, connection thickness was kept uniform across edges.
\
**C.** Distribution of DMN connectivity scores across CTRL, PD, and PDD groups. Red lines indicate
group means, highlighting a progressive decrease in mPFC-centered DMN connectivity across groups.
```

# Acknowledgement
We thank the Neuromatch Impact Scholar Programme, the Michael J. Fox Foundation, and the Parkinson’s Progression Markers Initiative (PPMI) for supporting this work and providing access to the dataset.

# Author Contributions
Geetha Iyer performed the seed-based connectivity analyses. Rosario Huaranca conducted the ROI-to-ROI connectivity analyses. Salma Elatries performed the graph-theoretical analyses. Abdul Rauf Anwar supervised the project. All authors contributed to interpretation, manuscript preparation, and final approval.

# Data Availability Statement
The data used in this study were obtained from the Parkinson’s Progression Markers Initiative (PPMI) database (available at https://www.ppmi-info.org/data). The datasets are publicly and freely available to qualified investigators upon completing an online application, signing the Data User Agreement, and complying with the study’s publication policies. Because the terms of the Data User Agreement strictly prohibit the unauthorized distribution of participant-level data, the authors cannot share the raw data files directly.
