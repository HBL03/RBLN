---
title: "Future Directions"
weight: 1
---

## 향후 실험 계획 :contentReference[oaicite:6]{index=6}

1. **컴파일 실패 모델 분석**
   - 사용자 정의 C++ 연산, 비표준 Layer 탐지  
   - 컴파일 실패 원인별 대응 로직 구축

2. **성능 개선 실험**
   - Quantization, Pruning, Distillation 기반 효율화  
   - Mixed Precision 적용 시 정확도 변화 추적

3. **KV 캐시 효율 연구**
   - 메모리 블록 재할당 및 캐시 파편화 처리  
   - PagedAttention 개선 및 실시간 캐시 재사용 전략

4. **멀티디바이스 비교 확대**
   - ATOM 외 L4, L40S, A4000~A6000 포함  
   - Vision-Language 및 Diffusion 모델 추가 테스트
