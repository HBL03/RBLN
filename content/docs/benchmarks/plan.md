---
title: "Benchmark Plan"
weight: 1
---

## 목적
Rebellions ATOM을 비롯한 NPU와 GPU를 대상으로 **추론 성능, 메모리 사용량, 양자화 효과**를 정량적으로 분석한다.

## 평가 항목
- 평균/중앙값 추론 시간 (ms)
- FPS
- 레이턴시 분포 (P50, P95, P99)
- 표준편차 및 변동계수
- 모델 로딩 및 Warm-up 시간

## 테스트 모델
- ✅ Image Classification Model  
- ✅ Large Language Model (LLM)  
- ⭕ Vision-Language Model *(optional)*  
- ⭕ Diffusion Model *(optional)*

> 결과 예시: [Benchmark Result Example](https://nas.viplab.inu.ac.kr/s/C5NpMrJJActdtWb)
