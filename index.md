# Characterization of large-scale brain connectivity patterns associated with depression in Parkinson’s disease
Abstract: |
Depression is a prevalent and disabling non-motor symptom of Parkinson’s disease (PD), substantially contributing to cognitive decline and reduced quality of life. Resting-state functional MRI (rs-fMRI) provides a non-invasive approach to investigate large-scale network alterations associated with psychiatric manifestations in PD. In this study, we investigated whether resting-state connectivity patterns could serve as candidate markers of depression in PD using data from 90 participants from the Parkinson’s Progression Markers Initiative (PPMI). Connectivity was assessed using complementary seed-based connectivity (SBC), ROI-to-ROI functional connectivity, and graph-theoretical analyses across 15 regions spanning the default mode (DMN), salience (SN), and frontoparietal (FPN) networks. SBC analysis revealed significant connectivity differences between PD patients with depression (PDD) and without depression (PDND), identifying alterations involving the medial prefrontal cortex (mPFC), dorsal anterior cingulate cortex (dACC), superior parietal lobule (SPL), and supramarginal gyrus (SMG). ROI-based functional connectivity further identified convergent alterations within mPFC-centered DMN connectivity, showing negative associations between depressive symptom severity and functional connectivity measures. Based on these convergent findings, a composite DMN connectivity score was constructed, revealing a progressive decrease in connectivity across groups and significant differences between PDD and controls. Collectively, these findings highlight mPFC-centered DMN connectivity as a potential marker associated with depression in Parkinson’s disease. This work was supported by the Impact Scholars Program. We acknowledge the contributions of Michael J Fox Foundation [former team members, teaching assistants, or mentors whose involvement does not meet the criteria of any authorship role].
---

# Introduction
Depression is a prevalent and disabling non-motor symptom of Parkinson’s disease (PD), affecting up to 50\% of patients and exacerbating motor and cognitive decline ([@parkinsons_foundation_depression_2026], [@parkinsons_foundation_depression_2026-1]). Its multifactorial etiology involves demographic, clinical, and neurocognitive factors ([@cong_prevalence_2022]); however, the underlying neural mechanisms remain poorly understood. While motor network dysfunction in PD has been extensively characterized, depression-related connectivity alterations, particularly within the default mode and limbic networks ([@morgan_altered_2018], [@xu_altered_2022]), remain heterogeneous. Given this heterogeneity, we focused on large-scale resting-state networks most consistently implicated in depression, particularly the default mode network (DMN), because the DMN supports self-referential and affective processing and contains hubs, notably the medial prefrontal cortex (mPFC), that show reproducible connectivity alterations in major depression (\cite{zheng_beyond_2026, zhang_dysfunction_2024, sheline_default_2009}).

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





We then describe our results clearly, concisely, and in a logical order. We use a single high-resolution figure to support the findings and reference it in the text (@figure-main A).

```{figure} figure.png
:name: figure-main
:alt: Multi-panel figure supporting the main findings

\
**A.** Here we describe panel A.
\
**B.** Here we describe panel B.
\
**C.** Here we describe panel C.
```

Finally, we interpret our results, discussing their implications and relevance to the field. We provide a clear takeaway message for the reader that summarizes the contribution of this micropublication.

