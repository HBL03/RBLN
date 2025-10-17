---
title: "LLM Benchmark Metrics"
weight: 2
---

## 주요 지표 정의 :contentReference[oaicite:2]{index=2}

| Metric | Description |
|--------|--------------|
| **E2E Latency** | 요청 수신 → 최종 토큰 출력까지의 전체 시간 |
| **TTFT (Time-To-First-Token)** | 첫 토큰 생성까지 걸린 시간 |
| **Per-token Latency** | 각 디코드 단계 평균 지연 |
| **Prefill Throughput** | 입력 토큰 처리 속도 (tokens/s) |
| **Decode Throughput** | 출력 토큰 생성 속도 (tokens/s) |
| **Request Throughput (RPS)** | 초당 완료 요청 수 |

## 보조 지표
- **Context Length 분포 (평균/P95/최대)**  
- **Scheduler Wait Time**  
- **Tokenizer Time**  
- **I/O Overhead (PCIe 전송 비용)**  
- **Memory Footprint (KV Cache 용량)**

## Cold vs Warm 구분
- **Model Load Time:** 첫 요청 전 weight 로드 및 캐시 빌드 시간  
- **KV Warm Ratio:** 동일 대화 재요청 시 TTFT 감소율

## 통계 분석
- 각 구간별 **P50, P90, P95, P99** 지연 분포 기록
