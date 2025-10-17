---
title: "Transformer Bottleneck Analysis"
weight: 1
---

## I/O 병목 문제
Transformer의 주요 병목은 **메모리 대역폭 제한**으로 인한 I/O 병목입니다.  
어텐션 계산 중 생성되는 거대한 행렬 \( S = QK^T \)는 GPU SRAM에 적재 불가해 HBM에 저장 후 재전송되어 **연산 병목**이 발생합니다 :contentReference[oaicite:3]{index=3}.

## KV 캐시 단편화
- KV 캐시는 재사용을 통해 속도를 향상시키지만,  
  입력 길이의 다양성으로 인해 **메모리 조각화(fragmentation)** 문제가 발생합니다.  
- 실제 메모리가 남아있음에도 **새 요청을 수용하지 못하는** 비효율 발생.
