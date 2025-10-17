---
title: "Device Specification Comparison"
weight: 1
---

## Overview

Rebellions **ATOM NPU**의 연산 성능과 메모리 대역폭을 NVIDIA GPU 라인업과 비교하였다.

| Device | FP32 TFLOPS | INT8 TOPS | Memory | Bandwidth | Power |
|---------|--------------|------------|----------|-------------|--------|
| ATOM | 32 | 128 | 16GB GDDR6 | 256 GB/s | Efficient |
| L4 | – | 485 | 24GB GDDR6 | 300 GB/s | – |
| A4000 Ada | – | 427.6 (est.) | 16GB GDDR6 | 448 GB/s | – |
| A5000 | 27.8 | – | 24GB GDDR6 | 768 GB/s | – |
| A6000 | 38.7 | – | 48GB GDDR6 | 768 GB/s | – |

### Observations
- **부동소수점 연산** 성능은 A5000과 A6000의 **중간 수준**  
- **정수 연산** 성능은 GPU 대비 낮지만, **전력 효율이 우수**
- **메모리 대역폭**은 GPU가 크게 우세

> 요약: ATOM은 “저전력 고효율형”으로, 대형 연산 대비 단일 추론에 적합.
