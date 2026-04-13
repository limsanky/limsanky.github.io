---
layout: page
title: FALCON
description: 깊이 추정을 위한 빠르고 적응적인 강도 및 이벤트 연산 프레임워크.
img: assets/img/publication_preview/Fig_pipeline1.jpg
importance: 2
category: Event-Based Vision
permalink: /projects/falcon/ko/
---

*🌐 [🇬🇧 Read in English](../)*

---

**상태 (Status):** CVPR 2026 Findings Track 채택.

*참고: 전체 소스 코드 및 논문은 학회 엠바고 해제 후 공개될 예정입니다.*

### 프로젝트 개요 (Project Overview)
이벤트 기반 스테레오 깊이 추정(Event-based stereo depth estimation)은 까다로운 조건에서도 고속의 강력한 인식을 약속합니다. 하지만 이벤트 데이터를 강도 프레임(intensity frames)과 병합하는 과정은 막대한 연산 비용을 초래하여 실시간 배포를 방해합니다. FALCON은 스파이킹 뉴런 역학(spiking neuron dynamics)을 간소화된 스테레오 백본과 공동 설계(co-designing)하여 이 문제를 해결합니다.

### 주요 혁신 및 아키텍처 (Key Innovations & Architecture)
* **스파이킹 뉴런 역학:** LIF(Leaky Integrate-and-Fire) 뉴런을 1x1 합성곱 이벤트 표현(convolutional event representations)과 통합했습니다.
* **연산량 대폭 감소:** 픽셀 단위의 스파이킹 인코더는 기존 모듈보다 **1000배 이상 적은 FLOPs**를 사용하여 시간적 동적 특성(temporal dynamics)을 캡처합니다.
* **최적화된 그룹화:** 이벤트 그룹화를 최적화하고 블러 현상을 최소화하기 위해 $\sigma$-매칭 휴리스틱을 구현했습니다.

### 정량적 벤치마크 (Quantitative Benchmarks)
FALCON은 놀라울 정도로 높은 프레임 속도에서 SOTA 정확도를 달성하여 뉴로모픽 비전 애플리케이션을 위한 새로운 실시간 벤치마크를 확립했습니다:
* **DSEC 데이터셋:** MAE 0.356, **32.2 FPS**로 구동.
* **MVSEC 데이터셋:** MDE 11.7 cm, **72.8 FPS**로 구동.

### 파이프라인 아키텍처 (Pipeline Architecture)

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/publication_preview/Fig_pipeline1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

> **Figure 1:** 빠른 깊이 추정을 위한 LIF 뉴런의 통합을 강조하는 FALCON 프레임워크.

---

<div align="center">
  <img src="/assets/img/publication_preview/FigTeaser_wide1.jpg" alt="FALCON Teaser Figure" width="80%">
</div>

> **Figure 2:**<br>
> **상단: 이벤트 표현 시각화.** 짧은 간격으로 이벤트를 단순 누적하는 방식("Short Stack," 왼쪽)은 장면의 구조를 포착하지 못합니다. 긴 간격으로 누적하는 방식("Long Stack," 가운데)은 심각한 모션 블러를 유발합니다. 당사의 스파이킹 표현 네트워크의 학습된 출력인 "RepNet Stack" (오른쪽)은 이벤트를 동적으로 집계하여 선명한 구조적 디테일을 보존합니다.<br><br>
> **하단: 런타임 vs. 오차.** DSEC 데이터셋의 MAE(Mean Absolute Error) 및 MVSEC 데이터셋의 MDE(Mean Depth Error) 대비 런타임(FPS) 비교. FALCON은 런타임에서 다른 모델들을 크게 압도하면서도 동등하거나 향상된 정확도를 달성합니다. 메트릭은 각각의 원본 논문에서 발췌되었습니다.

---

### 정성적 비교 (Qualitative Comparison)

<div style="display: flex; justify-content: space-between; align-items: center; width: 80%; margin: 0 auto;">
  <img src="/assets/img/publication_preview/sidebyside/main_rgb.jpg" alt="RGB Image" style="width: 19%;">
  <img src="/assets/img/publication_preview/sidebyside/rose.jpg" alt="RepNet Stack" style="width: 19%;">
  <img src="/assets/img/publication_preview/sidebyside/main_eis.jpg" alt="EI-Stereo" style="width: 19%;">
  <img src="/assets/img/publication_preview/sidebyside/main_secff.jpg" alt="SE-CFF" style="width: 19%;">
  <img src="/assets/img/publication_preview/sidebyside/ours.jpg" alt="FALCON (Ours)" style="width: 19%;">
</div>

> **Figure 3:**<br>
> **DSEC 데이터셋에서의 정성적 비교.** 정성적 결과를 시각화합니다: 3가지 다른 장면에 대한 (A) RGB 이미지, (B) RepNet Stacks, 그리고 (C) EI-Stereo, (D) SE-CFF, (E) FALCON (Ours)의 디스패리티(Disparity) 예측. 제안하는 모델의 예측은 더 많은 디테일과 선명한 객체 형태를 포함하는 반면, SE-CFF 및 EI-Stereo의 예측은 디테일이 부족하고 흐릿한 아티팩트(hazy artifacts)가 발생합니다.