# **Project Title: Characterization of large-scale brain connectivity patterns associated with depression in Parkinson’s disease**

## **Pipeline Protocol: fMRI Preprocessing & Seed-Based Connectivity Analysis**

**Software Environment: MATLAB | CONN Toolbox (v25.b) | SPM25 (25.01.02)**

1. **SETUP**  
* ***Basic Information:***  
  * **Number of Subjects:** 60  
  * **Number of Sessions per Subject:** 1  
  * **Repetition Time (TR):** 2.5 seconds  
  * **Acquisition Type:** Continuous  
* ***Structural Data:*** T1-weighted anatomical images assigned to each subject  
* ***Functional Data:*** BOLD fMRI scans assigned to each subject  
* ***Regions of Interest (ROIs)***: A total of 15 regions were selected from the default CONN network atlas for analysis, spanning the Salience, FrontoParietal, and Default Mode networks. The specific regions include:  
  * **Default Mode Network (DMN):** Medial prefrontal cortex (mPFC), Lateral parietal cortex (L), Lateral parietal cortex (R), Posterior cingulate cortex (PCC)  
  * **Salience Network (SN)**: Mid-cingulate cortex, Anterior insula (L), Anterior insula (R), Rostral prefrontal cortex (L), Rostral prefrontal cortex (R), Supramarginal gyrus (L), Supramarginal gyrus (R)   
  * **FrontoParietal Network (FPN):** Lateral prefrontal cortex (L), Posterior parietal cortex (L), Lateral prefrontal cortex (R), Posterior parietal cortex (R)

2. **PREPROCESSING**  
* **Pipeline Selected:** Default preprocessing pipeline for volume-based analyses (direct normalization to MNI-space) executed sequentially through the following steps:  
  * Functional Label current functional files as "original functional data"  
  * Functional Center to (0,0,0) coordinates (translation) separately for each run/session  
  * Functional Realignment with correction of susceptibility distortion interactions (subject motion estimation and correction)  
  * Functional Label current functional files as "realigned functional data"  
  * Functional Slice-Timing Correction (STC; correction for inter-slice differences in acquisition time)  
  * Functional Outlier Detection (ART-based identification of outlier scans for scrubbing)  
  * Functional Direct Segmentation & MNI-space Normalization (Simultaneous Grey/White/CSF segmentation and MNI normalization)  
  * Functional Label current functional files as "mni-space functional data"  
  * Structural Label current structural files as "original structural images"  
  * Structural Center to (0,0,0) coordinates (translation)  
  * Structural Segmentation & Normalization (Simultaneous Grey/White/CSF segmentation and MNI normalization)  
  * Structural Label current structural files as "mni-space structural images"  
  * Functional Smoothing (Spatial convolution with Gaussian kernel)  
  * Functional Label current functional files as "smoothed functional data"

* **Select Slice Order:** Interleaved (Siemens)  
* **Functional Outlier Detection Settings:** Use intermediate settings (97th percentiles in normative sample)  
* **Segment/Normalize/Resample Settings:** Use default Tissue Probability Map (SPM/TPM)  
* **Enter Smoothing Kernel FWHM (in mm):** 8

3. **DENOISING**  
* **Band-pass filter (Hz):** \[0.01 0.08\]

4. **1ST-LEVEL ANALYSIS: CONNECTIVITY ANALYSES**  
* **Analysis Name:** SBC  
* **Analysis Type:**   
  * Functional connectivity (weighted GLM)  
  * Seed-to-Voxel analyses  
* **Analysis Option:**   
  * **Output Measures:** Bivariate correlation coefficients (bivariate functional connectivity)  
  * **Temporal Weights:** Hemodynamic response function (hrf)  
* **Seeds Selected:** A total of 15 network seeds were included (Default Mode, Salience, and FrontoParietal networks)  
* **Seed Components:** 1 component was extracted per seed region to characterize its representative timeseries  
* **Other Options:**  
  * No temporal expansion  
  * No frequency decomposition

5. **2ND-LEVEL ANALYSIS: GROUP ANALYSES**

The second-level group analysis was configured as a custom General Linear Model (GLM) to evaluate between-group differences in functional connectivity based on the parameters below

* **Subject Effects:**  
  * **Variables Included:** Control (Healthy Controls), PDND (Parkinson's Disease No Depression), PDD (Parkinson's Disease with Depression), and ExcludeOutlierSubjects (Quality Assurance covariate)  
* **Between-Subjects Contrast:**  
  * Contrast Vector: \[0, \-1, 1, 0\]  
  * Difference PDD \> PDND (Directly compares the PDD group against the PDND group while nulling the effects of the Control group and controlling for excluded outlier subjects)  
* **Conditions:** rest (Resting-state session)  
* **Seeds/Sources & Between-Sources Contrast:**   
  * **Sources:** All 15 default network seeds selected during the 1st-level analysis  
  * **Contrast Type:** Any differences (F-test)  
  * **Matrix Pattern:** An identity-like contrast matrix (e.g., \[-1 1 0 0...; 0 \-1 1 0...\]) applied across the sources to run an F-test evaluating any main differences across the connectivity networks.
