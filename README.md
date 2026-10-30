<div align="center">
  <h1>📊 Awesome Provenance Graph Papers</h1>
  <p>
    <b>A curated collection of provenance graph & APT detection papers</b>
  </p>
  <p>
    <img src="https://img.shields.io/badge/papers-22-blue" alt="papers">
    <img src="https://img.shields.io/badge/last%20update-2026--10--30-green" alt="update">
    <img src="https://img.shields.io/github/stars/xythink/provenance-graph-papers?style=social" alt="stars">
  </p>
  <p>
    Only peer-reviewed work from top security/data-mining venues and the PRISM@NDSS workshop is listed.<br>
    PRs welcome · ⭐ Star to support
  </p>
</div>

---

## 📋 Table of Contents

- [📈 Research Trends](#-research-trends)
- [Surveys, Frameworks & Evaluation](#surveys-frameworks--evaluation)
- [Learning-based Detection](#learning-based-detection)
- [Rule-based Detection](#rule-based-detection)
- [LLM-based Methods](#llm-based-methods)
- [Tactic & Technique Recognition](#tactic--technique-recognition)
- [Privacy-Preserving Detection](#privacy-preserving-detection)
- [Provenance Systems & EDR Integration](#provenance-systems--edr-integration)
- [Datasets & Benchmarks](#datasets--benchmarks)
- [Open Source Code](#open-source-code)

---

## 📈 Research Trends

**Key observations:**
- 🏆 **Top-venue core:** KAIROS, FLASH, R-CAID (S&P'24), MAGIC (USENIX Sec'24), NODLINK (NDSS'24), CAPTAIN (NDSS'25), ORTHRUS and TAPAS (USENIX Sec'25), Slot and OCR-APT (CCS'25), PIDSMaker and APT-CGLP (KDD'26)
- 📊 **DARPA TC/E3 remains the main benchmark**, but the field is now questioning it. Bilot et al. (USENIX Sec'25) show a simple model matches complex PIDS on most DARPA datasets, and an NDSS'27 paper studies how benchmarks and evaluation protocols shape conclusions
- 🎯 **Attribution quality over raw detection scores:** ORTHRUS and the USENIX ;login: follow-up argue that alert granularity, not headline accuracy, decides practical usability
- 🧰 **Unified frameworks:** PIDSMaker (KDD'26) standardizes preprocessing, graph construction, and evaluation across PIDS
- 🏭 **Industrial turn:** PRISM@NDSS'26 adds EDR integration, provenance recovery from commercial EDR telemetry, and next-generation datasets
- 🔒 **Privacy and adaptivity:** MIRAGE (decentralized, privacy-preserving PIDS), CAPTAIN (gradient-adapted rules)
- 🤖 **LLMs enter the pipeline:** OCR-APT (CCS'25) is the strongest peer-reviewed LLM-for-PIDS work so far

---

## Surveys, Frameworks & Evaluation

| Paper | Venue | Links | Highlights |
|-------|-------|-------|------------|
| **How Benchmarks and Evaluation Protocols Shape Conclusions in Provenance-Based Intrusion Detection** | NDSS'27 | [news](https://dig.telecom-paris.fr/news/ndss.html) | Examines how datasets and evaluation protocols drive conclusions about PIDS |
| **PIDSMaker**: Building and Evaluating Provenance-based Intrusion Detection Systems | KDD'26 | [arxiv](https://arxiv.org/abs/2601.22983) · [code](https://github.com/ubc-provenance/PIDSMaker) | Unified framework for building and evaluating PIDS |
| **Sometimes Simpler is Better**: A Comprehensive Analysis of State-of-the-Art PIDS | USENIX Sec'25 | [paper](https://www.usenix.org/conference/usenixsecurity25/presentation/bilot) · [pdf](Bilot_SoK_2025.pdf) | Re-implements eight PIDS, identifies nine shortcomings, shows a simple model is competitive |

---

## Learning-based Detection

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **GNNFormer**: Capturing Local Interactions and Long-Term Global Dependencies for APT Detection in Provenance Graphs | Sci. China Inf. Sci.'26 | [doi](https://doi.org/10.1007/s11432-025-4776-x) | GNN + Transformer for local and global dependencies |
| 2 | **ProvFusion**: Beyond Nodes vs. Edges, A Multi-View Fusion Framework for Provenance-Based Intrusion Detection | S&P'26 (see note) | [arxiv](https://arxiv.org/abs/2604.14685) | Fuses attribute, structure, and causal views with voting |
| 3 | **APT-CGLP**: APT Hunting via Contrastive Graph-Language Pre-Training | KDD'26 | [arxiv](https://arxiv.org/abs/2511.20290) · [pdf](APT-CGLP_2025.pdf) | Contrastive graph-language pre-training |
| 4 | **Slot**: Provenance-Driven APT Detection through Graph Reinforcement Learning | CCS'25 | [arxiv](https://arxiv.org/abs/2410.17910) · [paper](https://dl.acm.org/doi/10.1145/3719027.3744788) · [pdf](Slot_2024.pdf) | Graph reinforcement learning for adaptive detection |
| 5 | **TAPAS**: An Efficient Online APT Detection with Task-guided Process Provenance Graph Segmentation and Analysis | USENIX Sec'25 | [paper](https://www.usenix.org/conference/usenixsecurity25/presentation/zhang-bo-tapas) | Task-guided segmentation, stacked LSTM-GRU, up to 1806x storage reduction |
| 6 | **ORTHRUS**: Achieving High Quality of Attribution in Provenance-based IDS | USENIX Sec'25 | [paper](https://www.usenix.org/conference/usenixsecurity25/presentation/jiang-baoxiang) · [pdf](ORTHRUS_2025.pdf) · [code](https://github.com/ubc-provenance/orthrus) | Node-level, high-quality attribution |
| 7 | **DistTempGraph**: Distributed Temporal Graph Learning with Provenance for APT Detection in Supply Chains | ICDCS'25 | [arxiv](https://arxiv.org/abs/2504.02313) · [pdf](DistTempGraph_2025.pdf) | Distributed temporal graph learning for supply chains |
| 8 | **KAIROS**: Practical Intrusion Detection and Investigation using Whole-system Provenance | S&P'24 | [arxiv](https://arxiv.org/abs/2308.05034) · [pdf](KAIROS_2024.pdf) | Temporal causal GNN encoder-decoder |
| 9 | **FLASH**: A Comprehensive Approach to Intrusion Detection via Provenance Graph Representation Learning | S&P'24 | [paper](https://ieeexplore.ieee.org/document/10646725/) · [pdf](FLASH_2024.pdf) | Semantic-aware graph representation learning |
| 10 | **R-CAID**: Embedding Root Cause Analysis within Provenance-based Intrusion Detection | S&P'24 | | Root cause analysis integrated into detection |
| 11 | **MAGIC**: Detecting APTs via Masked Graph Representation Learning | USENIX Sec'24 | [arxiv](https://arxiv.org/abs/2310.09831) · [pdf](MAGIC_2023.pdf) · [code](https://github.com/FDUDSDE/MAGIC) | Masked graph autoencoder, self-supervised |
| 12 | **NODLINK**: An Online System for Fine-Grained APT Attack Detection and Investigation | NDSS'24 | [arxiv](https://arxiv.org/abs/2311.02331) · [pdf](NODLINK_2023.pdf) | Online detection via Steiner tree formulation |

---

## Rule-based Detection

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **CAPTAIN**: Incorporating Gradients to Rules, Towards Lightweight, Adaptive Provenance-based Intrusion Detection | NDSS'25 | [paper](https://www.ndss-symposium.org/ndss-paper/incorporating-gradients-to-rules-towards-lightweight-adaptive-provenance-based-intrusion-detection/) · [code](https://github.com/LexusWang/CAPTAIN) | Differentiable tag propagation, gradient-tuned rule parameters |

---

## LLM-based Methods

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **OCR-APT**: Reconstructing APT Stories from Audit Logs using Subgraph Anomaly Detection and LLMs | CCS'25 | [arxiv](https://arxiv.org/abs/2510.15188) · [pdf](OCR-APT_2025.pdf) | Subgraph anomaly detection + LLM attack story reconstruction |

---

## Tactic & Technique Recognition

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **TREC**: APT Tactic/Technique Recognition via Few-Shot Provenance Subgraph Learning | CCS'24 | [arxiv](https://arxiv.org/abs/2402.15147) · [pdf](TREC_2024.pdf) | Few-shot tactic recognition |

---

## Privacy-Preserving Detection

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **MIRAGE**: Private Yet Accurate, A Decentralized Approach to System Intrusion Detection | PRISM@NDSS'26 | [program](https://www.ndss-symposium.org/ndss-program/prism-2026/) | First privacy-preserving PIDS, decentralized |

---

## Provenance Systems & EDR Integration

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **How to Effectively Trace Provenance on Windows Endpoint Detection & Response Telemetry** | PRISM@NDSS'26 | [pdf](https://www.ndss-symposium.org/wp-content/uploads/prism2026-12.pdf) | Recovers whole-system provenance from commercial EDR telemetry, with denoising heuristics |
| 2 | **SYSARMOR**: The Practice of Integrating Provenance Analysis into EDR Systems | PRISM@NDSS'26 | [pdf](SYSARMOR_PRISM2026.pdf) | Microservice EDR architecture, async NODLINK/KNOWHOW detection |

---

## Datasets & Benchmarks

| Dataset | Description | Source | Used by |
|---------|-------------|--------|---------|
| **DARPA TC** | Transparent Computing, the main APT detection benchmark (Trace/Theia/Cadets/FiveDirections) | [GitHub](https://github.com/darpa-i2o/Transparent-Computing) | Most papers above |
| **DARPA OpTC** | Operational-level Transparent Computing dataset | [GitHub](https://github.com/FiveDirections/OpTC-data) | Several |
| **StreamSpot** | Streaming heterogeneous information flow graphs | [paper](https://dl.acm.org/doi/10.1145/2939672.2939716) | Several |
| **Unicorn** | Enterprise-scale endpoint dataset | [paper](https://dl.acm.org/doi/10.1145/3319535.3363214) | Several |

**New:** [Building Next-Generation Datasets for Provenance-Based Intrusion Detection](https://www.ndss-symposium.org/wp-content/uploads/prism2026-21.pdf) (PRISM@NDSS'26) proposes design principles and a construction method for next-generation provenance datasets, including the PROVATTACK benchmark.

---

## Open Source Code

| Paper | Code | Stars |
|-------|------|-------|
| PIDSMaker | [ubc-provenance/PIDSMaker](https://github.com/ubc-provenance/PIDSMaker) | ![](https://img.shields.io/github/stars/ubc-provenance/PIDSMaker?style=social) |
| ORTHRUS | [ubc-provenance/orthrus](https://github.com/ubc-provenance/orthrus) | ![](https://img.shields.io/github/stars/ubc-provenance/orthrus?style=social) |
| MAGIC | [FDUDSDE/MAGIC](https://github.com/FDUDSDE/MAGIC) | ![](https://img.shields.io/github/stars/FDUDSDE/MAGIC?style=social) |
| CAPTAIN | [LexusWang/CAPTAIN](https://github.com/LexusWang/CAPTAIN) | ![](https://img.shields.io/github/stars/LexusWang/CAPTAIN?style=social) |
| DARPA TC | [darpa-i2o/Transparent-Computing](https://github.com/darpa-i2o/Transparent-Computing) | ![](https://img.shields.io/github/stars/darpa-i2o/Transparent-Computing?style=social) |

> 📢 If you know of open-source code for other papers, PRs are welcome.

---

## 🔧 Contributing

PRs adding new papers are welcome. Format:

```markdown
| # | **Paper Title**: Description | Venue | [arxiv](url) · [pdf](file.pdf) | Key technique |
```

**Guidelines:**
1. PDF file naming: `PaperName_Year.pdf`
2. Sort by year, newest first
3. List the publication venue. Preprint-only papers are not accepted until they are published at a top venue or workshop

---

## 📄 License

MIT

---

<p align="center">
  <b>If you find this repository useful, please consider giving it a ⭐</b>
</p>
