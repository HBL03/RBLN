---
title: "Static vs Dynamic Graph Compilation"
weight: 3
---

## 그래프 구조 비교 :contentReference[oaicite:5]{index=5}

| 구분 | 정적 그래프 | 동적 그래프 |
|------|--------------|--------------|
| 생성 시점 | 컴파일 시점 | 런타임 시점 |
| 입력 형태 | 고정 크기 | 가변 입력 지원 |
| 예시 | NPU | PyTorch (Define-by-Run) |

- **NPU는 정적 그래프 기반**으로 사전 최적화 효율이 높습니다.  
- **PyTorch는 동적 그래프 기반**으로 유연하지만 런타임 오버헤드가 존재합니다.  
- FCN(Fully Convolutional Network)을 활용하면 가변 입력도 지원 가능.
