---
title: "Attention Optimization Techniques"
weight: 2
---

## Flash Attention
- 중간 행렬을 HBM에 쓰지 않고 **SRAM에서 계산**
- **Tiling:** Q, K, V를 작은 블록 단위로 분할  
- **Kernel Fusion:** 여러 연산 단계를 하나의 GPU 커널로 통합  
- **Recomputation:** 중간값 저장 대신 재계산으로 메모리 절약

## Paged Attention
- OS의 **페이징 메모리 기법**에서 착안  
- KV 캐시를 작은 블록 단위로 나누어 **불연속적 할당**  
- **Block Table**로 각 토큰의 KV 위치를 관리  
→ KV 캐시 단편화 문제 완화 :contentReference[oaicite:4]{index=4}.
