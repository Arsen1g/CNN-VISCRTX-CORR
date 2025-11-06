# RSA Analysis: ResNet-50 vs BOLD5000

This repository contains code and analysis comparing **ResNet-50 model RDMs** with **human fMRI responses** from the **BOLD5000 dataset** using **Representational Similarity Analysis (RSA)**. The study investigates the hierarchical alignment between deep neural network layers and visual cortical regions across multiple subjects.

---
![Python](https://img.shields.io/badge/Python-3.10-blue)
![License](https://img.shields.io/github/license/Arsen1g/CNN-VISCRTX-CORR)
![RSA Toolbox](https://img.shields.io/badge/rsatoolbox-v0.1.5-green)

## Table of Contents

- [Motivation](#motivation)  
- [Data](#data)  
- [Methods](#methods)  
  - [Pattern Alignment](#pattern-alignment)  
  - [ROI Selection](#roi-selection)  
  - [Model Preparation](#model-preparation)  
  - [RSA Analysis](#rsa-analysis)  
- [Visualizations](#visualizations)  
  - [Heatmaps](#heatmaps)  
  - [Grouped Bar Plots](#grouped-bar-plots)  
  - [Scatter Plots](#scatter-plots)  
  - [Radar Charts](#radar-charts)  
  - [3D RSA Surface](#3d-rsa-surface)  
- [Results Summary](#results-summary)  
- [Reproducibility](#reproducibility)  
- [Requirements](#requirements)  
- [References](#references)  

---

## Motivation

Understanding how **deep neural networks (DNNs)** mirror human visual processing is a key question in **computational neuroscience** and **NeuroAI**.  

This analysis examines:

- **Early visual areas (V1/V2)**
- **Mid-level visual areas (LOC, OPA)**
- **High-level scene/object areas (PPA, RSC)**
- **Layer-wise representations of ResNet-50 (5-Layers)**

The goal is to quantify **hierarchical alignment** between DNN representations and brain activity.

### Visual System Hierarchical Latencies

This table summarizes approximate onset latencies for key visual cortical areas in humans after seeing a stimulus. Latencies are based on EEG, MEG, and iEEG studies.

| Area | Approximate Onset / Selectivity Latency | Notes & References |
|------|-----------------------------------------|------------------|
| **V1** | ~30–60 ms | Earliest cortical activation in humans measured with MEG/VEF; reflects feedforward processing of low-level visual features (Foxe & Simpson, 2002; Di Russo et al., 2002). |
| **V2** | ~40–70 ms | Latencies very close to V1; macaque studies show similar onset timing between V1 and V2 neurons (Schmolesky et al., 1998; Nowak et al., 1995). Human direct V2 latency data are less precise. |
| **LOC (Lateral Occipital Complex)** | ~160–300 ms | ERP and iEEG studies show object shape selectivity emerging ~230 ms; TMS studies demonstrate causal involvement ~160–200 ms (Kourtzi & Kanwisher, 2000; Carlson et al., 2013). |
| **PPA (Parahippocampal Place Area)** | ~80–170 ms | Intracranial recordings show early scene/place discrimination (~80–170 ms) depending on stimulus type and PPA sub-region (Rajimehr et al., 2011; Golarai et al., 2010). |
| **OPA (Occipital Place Area)** | ~240–300 ms | iEEG and MEG studies indicate scene layout discrimination in OPA emerges ~242–300 ms (Kamps et al., 2016; Baldassano et al., 2016). |
| **RSC (Retrosplenial Complex)** | Poorly characterized; likely >400 ms | RSC participates in memory/navigation and allocentric coding; human onset latencies for visual stimuli are sparse (Epstein, 2008; Vann et al., 2009). |

---

## Data

This project uses data derived from the BOLD5000 Additional ROIs and RDMs for Neural Network Research dataset
(Pickard et al., 2023), a derivative of BOLD5000 Release 2.0 (Chang et al., 2021). The dataset extends the original BOLD5000 study by providing new region-of-interest (ROI) definitions, beta activation vectors, and representational dissimilarity matrices (RDMs).

- **BOLD5000 fMRI dataset**: preprocessed ROI-level RDMs per subject
- **ResNet-50**: precomputed RDMs for each convolutional block/layer 
- **Images**: 2985 images shared across subjects and model for alignment  
- **ROIs**: 10 cortical regions, including EarlyVisual, LOC, OPA, PPA, RSC categorised by hemisphere lateralisation (L/R) 

**Note**: The repository does **not** include raw MRI or image data due to size and licensing restrictions. Scripts expect data paths for `.h5` files.

Full dataset available on Dryad: [https://doi.org/10.5061/dryad.wpzgmsbtr](https://doi.org/10.5061/dryad.wpzgmsbtr)

### Datasets used for this study
- ResNet50_CORR_RDMs.h5 
- CSI1_BOLD5000_CORR_RDMs.h5 (*subject 1*)
- CSI2_BOLD5000_CORR_RDMs.h5 (*subject 2*)
- CSI3_BOLD5000_CORR_RDMs.h5 (*subject 3*)

---

## Methods

### Pattern Alignment
- Extracted common images across all subjects and model: 2985 patterns  
- Subsetted all RDMs to shared image patterns using **rsatoolbox**:

---


## Visualizations

### Heatmaps & Bar Plots Side by Side

<table>
<tr>
  <td><img src="subject1%20Heatmap.png" alt="Subject 1 Heatmap" width="300"/></td>
  <td><img src="Subject1%20BarPlot.png" alt="Subject 1 Bar Plot" width="300"/></td>
</tr>
<tr>
  <td>Subject 1 Heatmap</td>
  <td>Subject 1 Bar Plot</td>
</tr>

<tr>
  <td><img src="subject2%20Heatmap.png" alt="Subject 2 Heatmap" width="300"/></td>
  <td><img src="Subject2%20Barplot.png" alt="Subject 2 Bar Plot" width="300"/></td>
</tr>
<tr>
  <td>Subject 2 Heatmap</td>
  <td>Subject 2 Bar Plot</td>
</tr>

<tr>
  <td><img src="subject3%20Heatmap.png" alt="Subject 3 Heatmap" width="300"/></td>
  <td><img src="Subject3%20Barplot.png" alt="Subject 3 Bar Plot" width="300"/></td>
</tr>
<tr>
  <td>Subject 3 Heatmap</td>
  <td>Subject 3 Bar Plot</td>
</tr>
</table>

### Scatter Plots

<img src="ScatterPlot%20Subset%20ROI.png" alt="Scatter Plot" width="500"/>

### 3D RSA Surface

<img src="3D%20RSA%20SURFACE.png" alt="3D RSA Surface" width="500"/>

## References
## References

- Baldassano, C., Esteva, A., Fei-Fei, L., & Beck, D. (2016). Two distinct scene-processing networks in human cortex. *Journal of Neuroscience, 36*(3), 1150–1164.  
- Carlson, T. A., Tovar, D. A., Alink, A., & Kriegeskorte, N. (2013). Representational dynamics of object vision: The first 1000 ms. *Journal of Vision, 13*(10), 1–19.  
- Di Russo, F., Martínez, A., Sereno, M. I., Pitzalis, S., & Hillyard, S. A. (2002). Cortical sources of the early components of the visual evoked potential. *Human Brain Mapping, 15*(2), 95–111.  
- Epstein, R. (2008). Parahippocampal and retrosplenial contributions to human spatial navigation. *Trends in Cognitive Sciences, 12*(10), 388–396.  
- Foxe, J. J., & Simpson, G. V. (2002). Flow of activation from V1 to frontal cortex in humans: A framework for visual cognition. *Experimental Brain Research, 142*, 139–150.  
- Golarai, G., Liberman, A., Yoon, J., & Grill-Spector, K. (2010). Differential development of high-level visual cortex: A comparison of face, place, and object areas. *Cerebral Cortex, 20*(5), 1277–1292.  
- Kamps, F. S., Hendrix, C. L., Brennan, P. A., & Dilks, D. D. (2016). Occipital place area represents the local elements of scenes. *NeuroImage, 142*, 137–149.  
- Kourtzi, Z., & Kanwisher, N. (2000). Activation in human lateral occipital complex relates to object perception, not object motion. *Nature Neuroscience, 3*, 52–58.  
- Nowak, L. G., Sanchez-Vives, M. V., & McCormick, D. A. (1995). Mechanisms of bursting in cortical layer 5 neurons in vivo. *Journal of Neurophysiology, 74*(4), 1753–1769.  
- Rajimehr, R., Devaney, K. J., Bilenko, N. Y., Young, J. C., & Tootell, R. B. (2011). The “parahippocampal place area” responds preferentially to high spatial frequencies. *Neuron, 71*(1), 102–112.  
- Schmolesky, M. T., Wang, Y., Hanes, D. P., Thompson, K. G., Leutgeb, S., Schall, J. D., & Leventhal, A. G. (1998). Signal timing across the macaque visual system. *Journal of Neurophysiology, 79*(6), 3272–3278.  
- Vann, S. D., Aggleton, J. P., & Maguire, E. A. (2009). What does the retrosplenial cortex do? *Nature Reviews Neuroscience, 10*, 792–802.

```python
aligned_rdms_data = rdms_data.subset_pattern('image', common_patterns)
aligned_rdms_model = rdms_model.subset_pattern('image', common_patterns)

'''

