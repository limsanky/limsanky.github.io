---
layout: page
title: DBMSolver
description: A Training-free Diffusion Bridge Sampler for High-Quality Image-to-Image Translation.
img: assets/img/publication_preview/teaser-nodpm4.jpg
importance: 1
category: Generative AI
---

**Status:** Accepted to CVPR 2026 Main Track.

*Note: Camera-ready submitted. Full paper and code repository will be made public upon the lifting of the conference embargo.*

### Project Overview
Diffusion-based image-to-image (I2I) translation excels in high-fidelity generation but suffers from slow sampling in state-of-the-art Diffusion Bridge Models (DBMs), often requiring dozens of function evaluations (NFEs). To solve this, we introduced DBMSolver, a training-free sampler that exploits the semi-linear structure of DBM's underlying SDE and ODE via exponential integrators.

### Key Innovations & Performance
* **Unprecedented Efficiency:** Our 1st- and 2nd-order solutions reduce Network Function Evaluations (NFEs) by up to **5x**.
* **Quality Boost:** Achieved a **53% drop in FID** on the DIODE dataset at 20 NFEs compared to the 2nd-order baseline.
* **Versatility:** Successfully tested on inpainting, stylization, and semantics-to-image tasks across resolutions up to 256x256. 
* **New SOTA:** Establishes a new state-of-the-art efficiency-quality tradeoff, enabling true real-world applicability for diffusion bridge models.

### Visual Results

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/teaser-nodpm4.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Figure 1: Visual comparison of DBMSolver generating high-fidelity I2I translations with significantly fewer NFEs.
</div>