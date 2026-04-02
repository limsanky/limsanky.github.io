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
*(During the interview, use this diagram to walk the panel through your Spiking Neural Network framework).*

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Fig_pipeline1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Figure 1: The FALCON framework, highlighting the integration of LIF neurons for rapid depth estimation.
</div>