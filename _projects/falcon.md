---
layout: page
title: FALCON
description: Fast Adaptive Lightweight Computation of Intensities and Events for Depth Estimation.
img: assets/img/publication_preview/Fig_pipeline1.jpg
importance: 2
category: Event-Based Vision
---

**Status:** Accepted to CVPR 2026 Findings Track.

*Note: Full source code and manuscript will be made public upon the lifting of the conference embargo.*

### Project Overview
Event-based stereo depth estimation promises high-speed, robust perception under challenging conditions. However, fusing events with intensity frames incurs heavy computational costs, hindering real-time deployment. FALCON solves this by co-designing spiking neuron dynamics with a streamlined stereo backbone.

### Key Innovations & Architecture
* **Spiking Neuron Dynamics:** Integrated Leaky Integrate-and-Fire (LIF) neurons with 1x1 convolutional event representations.
* **Massive Compute Reduction:** Our per-pixel spiking encoders capture temporal dynamics using over **1000x fewer FLOPs** than prior modules.
* **Optimized Grouping:** Implemented a $\sigma$-matching heuristic to optimize event grouping and minimize blur.

### Quantitative Benchmarks
FALCON establishes a new real-time benchmark for neuromorphic vision applications by achieving SOTA accuracy at remarkably high framerates:
* **DSEC Dataset:** MAE of 0.356 running at **32.2 FPS**.
* **MVSEC Dataset:** MDE of 11.7 cm running at **72.8 FPS**.

### Pipeline Architecture

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Fig_pipeline1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

> **Figure 1:** The FALCON framework, highlighting the integration of LIF neurons for rapid depth estimation.

---

<div align="center">
  <img src="/assets/img/publication_preview/FigTeaser_wide1.jpg" alt="FALCON Teaser Figure" width="80%">
</div>

> **Figure 2:**
> **Top: Visualizing Event Representations.** Naive stacking of events over a short interval ("Short Stack," left) fails to capture scene structure. Stacking over a long interval ("Long Stack," middle) introduces severe motion blur. Our "RepNet Stack" (right), the learned output of our spiking representation network, dynamically aggregates events to preserve sharp structural details.
> 
> **Bottom: Runtime vs. Error.** Comparison of runtime (FPS) against Mean Absolute Error (MAE) on DSEC and Mean Depth Error (MDE) on MVSEC. FALCON achieves comparable or improved accuracy while significantly outperforming others in runtime. Metrics are excerpted from the respective original papers.

---

### Qualitative Comparison

<div style="display: flex; justify-content: space-between; align-items: center; width: 80%;">
  <img src="/assets/img/publication_preview/sidebyside/main_rgb.jpg" alt="RGB Image" style="width: 19%;">
  <img src="/assets/img/publication_preview/sidebyside/rose.jpg" alt="RepNet Stack" style="width: 19%;">
  <img src="/assets/img/publication_preview/sidebyside/main_eis.jpg" alt="EI-Stereo" style="width: 19%;">
  <img src="/assets/img/publication_preview/sidebyside/main_secff.jpg" alt="SE-CFF" style="width: 19%;">
  <img src="/assets/img/publication_preview/sidebyside/ours.jpg" alt="FALCON (Ours)" style="width: 19%;">
</div>

> **Figure 3:**
> **Qualitative Comparison on DSEC.** We illustrate the qualitative results: (A) RGB Images, (B) RepNet Stacks, and Disparity Predictions of (C) EI-Stereo, (D) SE-CFF, and (E) FALCON (Ours), for 3 different scenes are shown. Predictions of our model contain more detail and have sharper object shapes, while those of SE-CFF and EI-Stereo contain less detail and suffer from hazy artifacts.