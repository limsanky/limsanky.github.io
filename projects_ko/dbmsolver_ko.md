---
layout: page
title: DBMSolver
description: 고품질 이미지 변환을 위한 디퓨전 브릿지 샘플러 (Training-free Diffusion Bridge Sampler).
img: assets/img/publication_preview/teaser-nodpm4.jpg
importance: 1
category: Generative AI
permalink: /projects/dbmsolver/ko/
---

*🌐 [🇬🇧 Read in English](../)*

---

**상태 (Status):** CVPR 2026 Main Track 채택.

*참고: Camera-ready 제출 완료. 전체 논문 및 코드 저장소는 학회 엠바고 해제 후 공개될 예정입니다.*

### 프로젝트 개요 (Project Overview)
디퓨전 기반 이미지 대 이미지(I2I) 변환은 고품질 생성에 탁월하지만, 최신 디퓨전 브릿지 모델(DBM)에서는 샘플링 속도가 느려 수십 번의 네트워크 함수 평가(NFE)가 필요하다는 단점이 있습니다. 이를 해결하기 위해, 당사는 지수 적분기(exponential integrators)를 통해 DBM의 기반이 되는 SDE 및 ODE의 반선형(semi-linear) 구조를 활용하는 학습이 필요 없는(training-free) 샘플러인 DBMSolver를 도입했습니다.

### 주요 혁신 및 성능 (Key Innovations & Performance)
* **전례 없는 효율성:** 제안된 1차 및 2차 솔루션은 네트워크 함수 평가(NFE)를 최대 **5배** 감소시킵니다.
* **품질 향상:** 20 NFE 조건에서 2차 베이스라인과 비교하여 DIODE 데이터셋에서 **FID를 53% 감소**시켰습니다.
* **범용성:** 최대 256x256 해상도에서 인페인팅(inpainting), 스타일 변환(stylization), 의미론적 이미지 변환(semantics-to-image) 작업에 성공적으로 테스트 되었습니다.
* **새로운 SOTA 달성:** 디퓨전 브릿지 모델의 실제 적용을 가능하게 하는 효율성과 품질 간의 새로운 SOTA (State-of-the-Art) 트레이드오프를 확립했습니다.

### 시각적 결과 (Visual Results)

<div style="width: 80%; margin: 0 auto;">
    <div class="row mt-3">
        <div class="col-sm mt-3 mt-md-0">
            {% include figure.liquid loading="eager" path="assets/img/publication_preview/teaser-nodpm4.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
        </div>
    </div>
</div>

> **Figure 1:** 훨씬 적은 NFE로 고품질 I2I 변환을 생성하는 DBMSolver의 시각적 비교.

---

<div style="width: 80%; margin: 0 auto;">
    <div class="row mt-3">
        <div class="col-sm mt-3 mt-md-0">
            {% include figure.liquid loading="eager" path="assets/img/publication_preview/combined_diode_e2h-cam_ready_1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
        </div>
    </div>
</div>

> **Figure 2:** DIODE 256x256 및 Edges2Handbags 64x64 데이터셋에서의 DBMSolver 시각적 비교.

---

<div style="width: 80%; margin: 0 auto;">
    <div class="row mt-3">
        <div class="col-sm mt-3 mt-md-0">
            {% include figure.liquid loading="eager" path="assets/img/publication_preview/CelebA-6-30-Large_half_2.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
        </div>
    </div>
</div>

> **Figure 3:** CelebAMask-HQ 256x256 데이터셋에서의 DBMSolver 시각적 비교.

---

<div style="width: 80%; margin: 0 auto;">
    <div class="row mt-3">
        <div class="col-sm mt-3 mt-md-0">
            {% include figure.liquid loading="eager" path="assets/img/publication_preview/teaser-1x6.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
        </div>
    </div>
</div>

> **Figure 4:** DBMSolver를 사용한 CelebAMask-HQ 256x256에서의 6 NFE 결과.