# PlantVillage DT-DKD Ablation Log

All runs use MobileNetV2 student and ResNet-18 teacher. Evaluation metric is **best validation top-1 accuracy** over all epochs. The DKD fixed-tau baseline (B4) achieves **99.87%** for reference.

---

## Summary Table

| Version | Epochs | IMG | Batch | LR (student) | α / β | τ range | LR_τ | H | GRL Schedule | Best Val Top-1 | Best Epoch |
|---------|--------|-----|-------|-------------|-------|---------|------|---|--------------|----------------|------------|
| **v1** | 125 | 64 | 64 | 0.05 | 1.0 / 8.0 | [2.0, 10.0] | 1e-3 | 64 | Cosine (no warmup offset) | 99.54% | 115 |
| **v2** | 60 | 64 | 64 | 0.05 | 1.0 / 8.0 | [2.0, 10.0] | 1e-3 | 64 | Cosine (10-epoch warmup offset) | 99.34% | 53 |
| **v3** | 60 | 64 | 64 | 0.05 | **2.0 / 12.0** | [2.0, 10.0] | 1e-3 | 64 | Cosine (10-epoch warmup offset) | 98.97% | 38 |
| **v4** | 60 | 64 | 64 | 0.05 | **0.5 / 10.0** | [2.0, 10.0] | 1e-3 | 64 | Cosine (10-epoch warmup offset) | 99.21% | 52 |
| **v5** | 60 | 64 | 64 | **0.075** | 0.5 / 10.0 | [2.0, **12.0**] | 1e-3 | 64 | Cosine (10-epoch warmup offset) | 99.34% | 58 |
| **v6** | 60 | 64 | 64 | 0.075 | 0.5 / 10.0 | [2.0, 10.0] | **1e-4** | 64 | Cosine (10-epoch warmup offset) | 99.50% | 54 |
| **v7** | 60 | 64 | 64 | 0.075 | 0.5 / 10.0 | [2.0, **10.0**] | **1e-3** | 64 | Cosine (no warmup offset) | 94.14% | 58 |
| **v8** | 60 | 64 | 64 | 0.075 | **0.1 / 2.0** | [2.0, **6.7**] | 1e-4 | 64 | Cosine (no warmup offset) | 99.39% | 49 |
| **v9** | 60 | 64 | 64 | 0.075 | 0.1 / 2.0 | [2.0, **5.0**] | 1e-4 | 64 | **Mirror-cosine** (reverses after ep 30) | 99.30% | 59 |
| **v9b** | 60 | 64 | 64 | 0.075 | 0.1 / 2.0 | [2.0, 5.0] | 1e-4 | **16** | Mirror-cosine (drops to 0 after ep 40) | 99.43% | 57 |
| **v10** | 60 | **128** | **48** | **0.05** | **0.5 / 2.0** | [2.0, **7.0**] | 1e-4 | 16 | Mirror-cosine (drops to 0 after ep 40) + **mixed precision** | 99.82% | 53 |
| **v11** | 60 | 128 | **56** | 0.05 | 0.5 / 2.0 | [2.0, 7.0] | 1e-4 | 16 | **Full cosine** (no drop) + mixed precision | 99.89% | 48 |
| **v12** | 60 | 128 | 56 | 0.05 | 0.5 / 2.0 | [2.0, 7.0] | 1e-4 | 16 | Full cosine + mixed precision; | **99.91%** | 59 |

---
