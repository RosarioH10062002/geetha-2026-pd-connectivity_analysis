# Supplementary Material:

**a.** Preprocessing
Functional and anatomical data were preprocessed using a modular preprocessing pipeline including realignment with correction of susceptibility distortion interactions, slice timing correction, outlier detection, direct coregistration to structural, direct segmentation and MNI-space normalization, and smoothing. Functional data were realigned using SPM realign & unwarp procedure, where all scans were coregistered to a reference image (first scan of the first session) using a least squares approach and a 6 parameter (rigid body) transformation and resampled using b-spline interpolation to correct for motion and magnetic susceptibility interactions. Temporal misalignment between different slices of the functional data (acquired in interleaved Siemens order) was corrected following SPM slice-timing correction (STC) procedure, using Sinc temporal interpolation to resample each slice BOLD timeseries to a common mid-acquisition time. Potential outlier scans were identified using Artifact detection tools (ART) as acquisitions with framewise displacement above 0.9 mm or global BOLD signal changes above 5 standard deviations, and a reference BOLD image was computed for each subject by averaging all scans excluding outliers. Functional and anatomical data were coregistered using SPM intermodality coregistration procedure with a normalized mutual information objective function. Functional and anatomical data were normalized into standard MNI space, segmented into grey matter, white matter, and cerebrospinal fluid (CSF) tissue classes, and resampled to 2 mm isotropic voxels following a direct normalization procedure using SPM unified segmentation and normalization algorithm with the default IXI-549 tissue probability map template [@ashburner_fast_2007, @ashburner_unified_2005]. Lastly, functional data were smoothed using spatial convolution with a Gaussian kernel of 8 mm full width half maximum (FWHM).

**b.** Denoising
In addition, functional data were denoised using a confound regression pipeline incorporating established nuisance regressors. This included the removal of potential confounding effects derived from white matter (5 regressors), CSF (5 regressors), motion parameters and their first-order derivatives (12 regressors), outlier scans (<16 regressors), session effects and their first-order derivatives (2 regressors), and linear trends (2 regressors) within each functional run, followed by bandpass frequency filtering of the BOLD timeseries between 0.01 Hz and 0.08 Hz. Component-based noise correction (CompCor) regressors were estimated within each subject’s eroded white matter and CSF masks by extracting the mean signal and the largest principal components orthogonal to the mean signal, motion parameters, and outlier scans. Based on the number of nuisance regressors included, the effective temporal degrees of freedom of the denoised BOLD signal ranged from 69.3 to 74.9 (mean 74.3) across subjects.

**c.** Seed-Based Connectivity Analysis
Seed-based connectivity maps (SBC) were estimated characterizing the spatial pattern of functional connectivity with a seed area. Seed regions included 15 High-Performance Computing Independent Component Analysis (HPC-ICA) network ROIs. Functional connectivity strength was represented by Fisher-transformed bivariate correlation coefficients from a weighted general linear model (weighted-GLM), estimated separately for each seed area and target voxel, modeling the association between their BOLD signal timeseries. In order to compensate for possible transient magnetization effects at the beginning of each run, individual scans were weighted by a step function convolved with an SPM canonical hemodynamic response function and rectified. Group-level analyses were performed using a General Linear Model (GLM). For each individual voxel a separate GLM was estimated, with first-level connectivity measures at this voxel as dependent variables (one independent sample per subject and one measurement per task or experimental condition, if applicable), and groups or other subject-level identifiers as independent variables. Voxel-level hypotheses were evaluated using multivariate parametric statistics with random-effects across subjects and sample covariance estimation across multiple measurements. Inferences were performed at the level of individual clusters (groups of contiguous voxels). Cluster-level inferences were based on parametric statistics from Gaussian Random Field theory. Results were thresholded using a combination of a cluster-forming p < 0.001 voxel-level threshold, and a familywise corrected p-FDR < 0.05 cluster-size threshold.

**d.** Harmonization
Harmonization was applied to reduce scanner-related variability in this multicenter dataset, ensuring that observed differences reflect biological rather than acquisition-related effects. In this study, harmonization was performed using the ComBat method, which corrects for systematic site-related differences in feature distributions while preserving biological variability (Orlhac et al., 2022). ComBat models the observed signal as a combination of biological effects and additive and multiplicative scanner effects:
Equation (1):
$$
y_{ij} = \alpha + \gamma_i + \delta_i \varepsilon_{ij}
$$
where $y_{ij}$ denotes the feature value for subject $j$ at site $i$, $\alpha$ is the global mean, $\gamma_i$ and $\delta_i$ represent additive and multiplicative site effects, and $\varepsilon_{ij}$ is the residual error. Using a Bayesian framework, these site effects are estimated and removed to obtain harmonized values:

Equation (2):
$$
y_{ij}^{\text{ComBat}} = \frac{y_{ij} - \hat{\alpha} - \hat{\gamma}_i}{\hat{\delta}_i} + \hat{\alpha}
$$
where $\hat{\alpha}$, $\hat{\gamma}_i$, and $\hat{\delta}_i$ are the estimated parameters. Harmonization was applied to the extracted features (e.g., connectivity measures), and the resulting data were used for subsequent statistical analyses. Implementation was performed using the NeuroHarmonize Python toolbox [@pomponio_rpomponioneuroharmonize_2026].

**e.** Graph Theory
The resulting ROI-to-ROI connectivity matrices which were harmonized were used as input. The diagonal elements of these matrices were set to zero and, although using absolute edge weights, undirected, weighted graphs were constructed using absolute edge weights which provide a measure of the magnitude of functional coupling, regardless of the correlation direction. This is important, since all of the graph metrics used in this study assume a network is weighted non-negatively.

Graph-theoretical analysis was conducted using BCTpy-0.6.1 Roan LaPlante, n.d. Graphs were proportionally thresholded across densities from 0.10 to 0.30 in steps of 0.05, and area under the curve values were computed across thresholds using trapezoidal integration. The metrics listed in the main methods were selected to characterize overall connectivity, integration, segregation, centrality, cross-network participation, and within-network integration.

Global metrics included weighted strength, clustering coefficient, global efficiency, and betweenness centrality. Local metrics included nodal strength, nodal clustering coefficient, nodal betweenness centrality, participation coefficient, and within-module strength z-score. The participation coefficient measured the level of cross-network integration, while the z-score of the within-module strength measured the strength of connection between each ROI found within its assigned module when compared to other ROIs in that module. For module-based metrics, module labels were predefined according to the CONN atlas assignments: DMN, salience network, and frontoparietal network.

Global weighted strength was calculated as:
Equation (3):
$$
S^w = \frac{1}{N} \sum_{i=1}^{N} \sum_{j=1}^{N} w_{ij}
$$
where $S^w$ denotes global weighted strength, $w_{ij}$ is the edge weight between nodes $i$ and $j$, and $N$ is the total number of nodes.

Weighted clustering coefficient was calculated as:
Equation (4):
$$
C^w = \frac{1}{N} \sum_{i=1}^{N} \frac{1}{k_i (k_i - 1)} \sum_{j,h} (w_{ij} w_{ih} w_{jh})^{1/3}
$$
where $C^w$ is the global clustering coefficient and $k_i$ is the degree of node $i$.

Global efficiency was calculated as:
Equation (5):
$$
E_{glob} = \frac{1}{N(N - 1)} \sum_{i \neq j} \frac{1}{d_{ij}}
$$
where $E_{glob}$ represents global efficiency and $d_{ij}$ is the shortest path length between nodes $i$ and $j$.

Global betweenness centrality was calculated as the average nodal betweenness centrality:
Equation (6):
$$
BC = \frac{1}{N} \sum_{i=1}^{N} \sum_{s \neq i \neq t} \frac{\sigma_{st}(i)}{\sigma_{st}}
$$
where $\sigma_{st}$ is the number of shortest paths between nodes $s$ and $t$, and $\sigma_{st}(i)$ is the number of those paths passing through node $i$.
The same thresholding and AUC procedure was used for local graph metrics. 

Nodal strength was calculated as:
Equation (7):
$$
s_i^w = \sum_{j=1}^{N} w_{ij}
$$
where $s_i^w$ is the weighted strength of node $i$.

Nodal clustering coefficient was calculated as:
Equation (8):
$$
C_i^w = \frac{1}{k_i (k_i - 1)} \sum_{j,h} (w_{ij} w_{ih} w_{jh})^{1/3}
$$
where $C_i^w$ is the clustering coefficient of node $i$.

Nodal betweenness centrality was calculated as:
Equation (9):
$$
BC_i = \sum_{s \ne i \ne t} \frac{\sigma_{st}(i)}{\sigma_{st}}
$$
where $BC_i$ is the betweenness centrality of node $i$.

Participation coefficient was calculated to characterize cross-network integration:
Equation (10):
$$
P_i = 1 - \sum_{m=1}^{M} \left( \frac{s_{i,m}^w}{s_i^w} \right)^2
$$
where $P_i$ is the participation coefficient of node $i$, $s_{i,m}^w$ is the strength of connections from node $i$ to module $m$, $s_i^w$ is the total nodal strength, and $M$ is the number of predefined modules. Modules corresponded to the DMN, salience network, and frontoparietal network.

Within-module strength z-score was calculated to characterize within-network integration:
Equation (11):
$$
z_i = \frac{s_{i,m_i}^w - \mu_{m_i}}{\sigma_{m_i}}
$$
where $z_i$ is the within-module strength z-score of node $i$, $s_{i,m_i}^w$ is the within-module strength of node $i$ within its assigned module $m_i$, and $\mu_{m_i}$ and $\sigma_{m_i}$ are the mean and standard deviation of within-module strengths within module $m_i$.

This set of metrics was selected to characterize complementary aspects of brain network organization, including overall connectivity, integration, segregation, centrality, cross-network participation, and within-network integration. Pairwise group comparisons were performed using two-sided Mann–Whitney U tests. Benjamini–Hochberg FDR correction was applied across metrics within each pairwise comparison.
