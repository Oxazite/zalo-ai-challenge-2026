# Zalo AI Challenge 2026 — Systems & Architecture Showcase

An architectural overview of competitive solutions engineered for **Zalo AI Challenge 2026**, covering **Track 2 (DataMate)** and **Track 1 (LifeMate)** under strict offline execution, compute-bounded, and latency-constrained conditions.

---

## 1. Track 2: DataMate — High-Throughput Data Reasoning Engine

### Problem Overview
Translating complex Vietnamese multi-turn business queries into relational SQL execution plans across relational schemas (order histories, mechanic commissions, hierarchical categories, product pipes).

### Core Engineering Highlights
- **5.8s Standalone Offline Inference Engine:** Designed a high-throughput runtime with zero external API dependencies, pre-materialized binary state caches, and vectorized relational lookups.
- **Relational Domain Logic:** Comprehensive coverage of domain constraints across 14+ distinct schema structures (e.g., dev_001 through dev_014), handling dynamic commission calculations, null handling, and aggregation splits.
- **Penalized Accuracy Optimization:** Implemented a calibrated confidence threshold system that strategically abstains on ambiguous inputs to safeguard against negative penalty margins and prevent public-to-private leaderboard shakeups.

```
[ Natural Language Query ]
            │
            ▼
[ Rule-Based & Semantic Parser ] ──▶ [ Entity & Category Normalizer ]
            │
            ▼
[ Pre-computed Schema Cache ] ────▶ [ Vectorized Execution Plan ]
            │
            ▼
[ Confidence Calibrator ] ────────▶ [ Verified Final Answer / Abstain ]
```

---

## 2. Track 1: LifeMate — Quantized Conversational Speech Agent

### Problem Overview
Accurate, low-latency Vietnamese Automated Speech Recognition (ASR) and dialogue state tracking for conversational smart assistant environments.

### Core Engineering Highlights
- **Quantized PhoWhisper Inference (CTranslate2):** Converted fine-tuned transformer speech models into INT8 CTranslate2 compute graphs, cutting peak VRAM by >50% while accelerating inference throughput by ~3.5x over standard FP16 PyTorch runtimes.
- **Acoustic Preprocessing Pipeline:** Audio waveform conditioning, adaptive speech activity detection (VAD), dynamic range compression, and high-frequency noise suppression.
- **Deterministic Post-Processing:** Regex-based numeric, currency, and entity re-formatting tailored to colloquial Vietnamese voice commands.

---

## Technical Stack

- **Speech & NLP:** PhoWhisper, CTranslate2, Hugging Face Transformers, Tokenizers
- **Data Engineering:** Python 3.10+, Pandas, NumPy, SQLite3
- **Containerization & Deployment:** Standalone Docker images, zero-network runtime isolation

---

## Disclaimer & Confidentiality

*In compliance with Zalo AI Challenge competition rules and intellectual property safeguards, private datasets, proprietary fine-tuned weights, and active submission scripts are maintained in a private development environment. This repository serves as an architectural documentation and technical summary.*
