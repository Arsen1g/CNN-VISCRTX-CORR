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
- **Layer-wise representations of ResNet-50**

The goal is to quantify **hierarchical alignment** between DNN representations and brain activity.

---

## Data

- **BOLD5000 fMRI dataset**: preprocessed ROI-level RDMs per subject  
- **ResNet-50**: precomputed RDMs for each convolutional block/layer  
- **Images**: 2985 images shared across subjects and model for alignment  
- **ROIs**: 10 cortical regions, including EarlyVisual, LOC, OPA, PPA, RSC  

**Note**: The repository does **not** include raw MRI or image data due to size and licensing restrictions. Scripts expect data paths for `.h5` files.

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

<p align="center">
  <img src="Joint%20Heatmap%20(3%20subjects).png" width="250"/>
  <img src="ScatterPlot%20Subset%20ROI.png" width="250"/>
  <img src="3D%20RSA%20SURFACE.png" width="250"/>
</p>


```python
aligned_rdms_data = rdms_data.subset_pattern('image', common_patterns)
aligned_rdms_model = rdms_model.subset_pattern('image', common_patterns)
