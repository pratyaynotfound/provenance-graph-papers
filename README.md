<div align="center">
  <h1>📊 Awesome Provenance Graph Papers</h1>
  <p>
    <b>A curated collection of provenance-based intrusion detection (PIDS) and APT investigation papers</b>
  </p>
  <p>
    <img src="https://img.shields.io/badge/papers-49-blue" alt="papers">
    <img src="https://img.shields.io/badge/last%20update-2026--10--30-green" alt="update">
    <img src="https://img.shields.io/github/stars/xythink/provenance-graph-papers?style=social" alt="stars">
  </p>
  <p>
    Scope: peer-reviewed work at top security, systems, and data-mining venues (S&P, USENIX Security, CCS, NDSS, KDD, FSE, ICDCS, TIFS, ACM CSUR) plus selected PRISM@NDSS and TaPP workshop papers.<br>
    PRs welcome · ⭐ Star to support
  </p>
</div>

---

## 📋 Table of Contents

- [📈 Research Trends](#-research-trends)
- [Surveys, SoKs & Evaluation](#surveys-soks--evaluation)
- [Detection: Rule & Heuristic-based](#detection-rule--heuristic-based)
- [Detection: Learning-based](#detection-learning-based)
- [Attack Investigation & Story Reconstruction](#attack-investigation--story-reconstruction)
- [Threat Hunting & Tactic Recognition](#threat-hunting--tactic-recognition)
- [Adversarial Robustness](#adversarial-robustness)
- [Privacy-Preserving Detection](#privacy-preserving-detection)
- [Provenance Capture, Storage & EDR Integration](#provenance-capture-storage--edr-integration)
- [Datasets & Benchmarks](#datasets--benchmarks)
- [Open Source Code](#open-source-code)

---

## 📈 Research Trends

```
2016-2020  Foundations: streaming graph anomaly detection (StreamSpot, UNICORN), tag propagation (SLEUTH, HOLMES), alert triage (NoDoze, RapSheet)
2021-2023  Deep learning arrives: SIGL, ShadeWatcher, ThreaTrace, ProGrapher; first evasion attacks on PIDS
2024       Top-venue peak: KAIROS, FLASH, R-CAID (S&P), MAGIC (USENIX Sec), NODLINK (NDSS)
2025       Reality check: Bilot et al. SoK, ORTHRUS attribution quality, TAPAS efficiency, Slot RL, OCR-APT LLM reconstruction
2026       Engineering and evaluation: PIDSMaker, APT-CGLP (KDD), ProvFusion (S&P), PRISM@NDSS workshop, NDSS'27 benchmark critique
```

**Key observations:**
- 🎯 **Attribution over headline accuracy.** ORTHRUS and the follow-up USENIX ;login: article argue coarse-grained alerts make most PIDS unusable regardless of reported detection rates.
- 📊 **Evaluation is under scrutiny.** Bilot et al. (USENIX Sec'25) show a simple model matches complex PIDS on five of seven DARPA datasets; an NDSS'27 paper studies how benchmarks and protocols drive conclusions.
- 🧰 **Shared infrastructure.** PIDSMaker (KDD'26) standardizes preprocessing, graph construction, and evaluation; AutoLabel (USENIX Sec'25) automates fine-grained attack labeling.
- 🏭 **Industrial turn.** PRISM@NDSS'26 covers EDR integration and provenance recovery from commercial EDR telemetry; Cerberus (FSE'26) targets deployed endpoint detection.
- ⚔️ **Robustness is unsolved.** Mimicry and adversarial-action attacks (2023) evade most learning-based PIDS.
- 🤖 **LLMs enter investigation, not detection.** OCR-APT (CCS'25) and APT-CGLP (KDD'26) use language models for story reconstruction and CTI alignment.
- 📦 **DARPA TC/E3 is still the default benchmark**, with OpTC and new purpose-built datasets emerging.

---

## Surveys, SoKs & Evaluation

| Paper | Venue | Links | Highlights |
|-------|-------|-------|------------|
| **How Benchmarks and Evaluation Protocols Shape Conclusions in Provenance-Based Intrusion Detection** | NDSS'27 | [news](https://dig.telecom-paris.fr/news/ndss.html) | How datasets and evaluation protocols shape PIDS conclusions |
| **PIDSMaker**: Building and Evaluating Provenance-based Intrusion Detection Systems | KDD'26 | [arxiv](https://arxiv.org/abs/2601.22983) · [code](https://github.com/ubc-provenance/PIDSMaker) | Unified framework for building and evaluating PIDS |
| **Sometimes Simpler is Better**: A Comprehensive Analysis of State-of-the-Art PIDS | USENIX Sec'25 | [paper](https://www.usenix.org/conference/usenixsecurity25/presentation/bilot) · [pdf](Bilot_SoK_2025.pdf) | Eight PIDS re-implemented, nine shortcomings, simple baseline is competitive |
| **AutoLabel**: Automated Fine-Grained Log Labeling for Cyber Attack Dataset Generation | USENIX Sec'25 | | Automated ground-truth labeling for attack datasets |
| **Provenance-based Intrusion Detection Systems: A Survey** (Zipperle et al.) | ACM CSUR | | Broad PIDS survey and taxonomy |
| **Provenance-based Intrusion Detection: Opportunities and Challenges** | TaPP'18 | [paper](https://www.usenix.org/conference/tapp2018/presentation/han) | Position paper framing PIDS as graph anomaly detection |

---

## Detection: Rule & Heuristic-based

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **CAPTAIN**: Incorporating Gradients to Rules, Towards Lightweight, Adaptive Provenance-based Intrusion Detection | NDSS'25 | [paper](https://www.ndss-symposium.org/ndss-paper/incorporating-gradients-to-rules-towards-lightweight-adaptive-provenance-based-intrusion-detection/) · [code](https://github.com/LexusWang/CAPTAIN) | Differentiable tag propagation, gradient-tuned rule parameters |
| 2 | **RapSheet**: Tactical Provenance Analysis for Endpoint Detection and Response Systems | S&P'20 | | ATT&CK-aware tactical provenance graphs over EDR alerts |
| 3 | **HOLMES**: Real-Time APT Detection through Correlation of Suspicious Information Flows | S&P'19 | | Maps information flows to APT kill-chain stages |
| 4 | **NoDoze**: Combatting Threat Alert Fatigue with Automated Provenance Triage | NDSS'19 | | Anomaly-scored dependency graphs for alert triage |
| 5 | **SLEUTH**: Real-time Attack Scenario Reconstruction from COTS Audit Data | USENIX Sec'17 | | Tag-based real-time attack reconstruction |

---

## Detection: Learning-based

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **ProvFusion**: Beyond Nodes vs. Edges, A Multi-View Fusion Framework for Provenance-Based Intrusion Detection | S&P'26 † | [arxiv](https://arxiv.org/abs/2604.14685) | Fuses attribute, structure, and causal views with voting |
| 2 | **APT-CGLP**: APT Hunting via Contrastive Graph-Language Pre-Training | KDD'26 | [arxiv](https://arxiv.org/abs/2511.20290) · [pdf](APT-CGLP_2025.pdf) | Contrastive graph-language pre-training against CTI |
| 3 | **GNNFormer**: Capturing Local Interactions and Long-Term Global Dependencies for APT Detection in Provenance Graphs | Sci. China Inf. Sci.'26 | [doi](https://doi.org/10.1007/s11432-025-4776-x) | GNN + Transformer hybrid |
| 4 | **Slot**: Provenance-Driven APT Detection through Graph Reinforcement Learning | CCS'25 | [arxiv](https://arxiv.org/abs/2410.17910) · [paper](https://dl.acm.org/doi/10.1145/3719027.3744788) · [pdf](Slot_2024.pdf) | Graph reinforcement learning |
| 5 | **TAPAS**: Efficient Online APT Detection with Task-guided Process Provenance Graph Segmentation and Analysis | USENIX Sec'25 | [paper](https://www.usenix.org/conference/usenixsecurity25/presentation/zhang-bo-tapas) | Task segmentation, stacked LSTM-GRU, up to 1806x storage reduction |
| 6 | **ORTHRUS**: Achieving High Quality of Attribution in Provenance-based IDS | USENIX Sec'25 | [paper](https://www.usenix.org/conference/usenixsecurity25/presentation/jiang-baoxiang) · [pdf](ORTHRUS_2025.pdf) · [code](https://github.com/ubc-provenance/orthrus) | Node-level detection with high-quality attribution |
| 7 | **DistTempGraph**: Distributed Temporal Graph Learning with Provenance for APT Detection in Supply Chains | ICDCS'25 | [arxiv](https://arxiv.org/abs/2504.02313) · [pdf](DistTempGraph_2025.pdf) | Distributed temporal graph learning |
| 8 | **KAIROS**: Practical Intrusion Detection and Investigation using Whole-system Provenance | S&P'24 | [arxiv](https://arxiv.org/abs/2308.05034) · [pdf](KAIROS_2024.pdf) | Temporal GNN encoder-decoder, anomalous time windows |
| 9 | **FLASH**: Intrusion Detection via Provenance Graph Representation Learning | S&P'24 | [paper](https://ieeexplore.ieee.org/document/10646725/) · [pdf](FLASH_2024.pdf) | Semantic embeddings + GNN, embedding database |
| 10 | **R-CAID**: Embedding Root Cause Analysis within Provenance-based Intrusion Detection | S&P'24 | | Root-cause-aware embeddings |
| 11 | **MAGIC**: Detecting APTs via Masked Graph Representation Learning | USENIX Sec'24 | [paper](https://www.usenix.org/conference/usenixsecurity24/presentation/jia-zian) · [pdf](MAGIC_2023.pdf) · [code](https://github.com/FDUDSDE/MAGIC) | Masked graph autoencoder, self-supervised |
| 12 | **NODLINK**: An Online System for Fine-Grained APT Attack Detection and Investigation | NDSS'24 | [arxiv](https://arxiv.org/abs/2311.02331) · [pdf](NODLINK_2023.pdf) | Online Steiner tree formulation |
| 13 | **ProGrapher**: An Anomaly Detection System based on Provenance Graph Embedding | USENIX Sec'23 | | Snapshot graph embedding + sequence prediction |
| 14 | **DistDet**: A Cost-Effective Distributed Cyber Threat Detection System | USENIX Sec'23 | | Distributed host/server detection split |
| 15 | **ShadeWatcher**: Recommendation-guided Cyber Threat Analysis using System Audit Records | S&P'22 | | Recommender-system view of entity interactions |
| 16 | **ThreaTrace**: Detecting and Tracing Host-based Threats in Node Level through Provenance Graph Learning | TIFS'22 | | Node-level GraphSAGE multi-model detection |
| 17 | **SIGL**: Securing Software Installations Through Deep Graph Learning | USENIX Sec'21 | [paper](https://www.usenix.org/conference/usenixsecurity21/presentation/han-xueyuan) | Graph LSTM autoencoder over installation graphs |
| 18 | **UNICORN**: Runtime Provenance-Based Detector for Advanced Persistent Threats | NDSS'20 | [paper](https://dev.ndss-symposium.org/ndss-paper/unicorn-runtime-provenance-based-detector-for-advanced-persistent-threats) | Graph sketching, evolving models |
| 19 | **ProvDetector**: You Are What You Do, Hunting Stealthy Malware via Data Provenance Analysis | NDSS'20 | | Rare path embedding for stealthy malware |
| 20 | **StreamSpot**: Fast Memory-efficient Anomaly Detection in Streaming Heterogeneous Graphs | KDD'16 | [paper](https://dl.acm.org/doi/10.1145/2939672.2939716) | Streaming graph sketch clustering |

† Venue inferred from an S&P'26 citation with a matching title; verify.

---

## Attack Investigation & Story Reconstruction

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **OCR-APT**: Reconstructing APT Stories from Audit Logs using Subgraph Anomaly Detection and LLMs | CCS'25 | [arxiv](https://arxiv.org/abs/2510.15188) · [pdf](OCR-APT_2025.pdf) | Subgraph anomaly detection + LLM reports |
| 2 | **DepComm**: Graph Summarization on System Audit Logs for Attack Investigation | S&P'22 | | Process-centric community summarization |
| 3 | **DepImpact**: Back-Propagating System Dependency Impact for Attack Investigation | USENIX Sec'22 | | Weighted backward/forward impact propagation |
| 4 | **ATLAS**: A Sequence-based Learning Approach for Attack Investigation | USENIX Sec'21 | | Sequence learning over causal graphs |
| 5 | **WATSON**: Abstracting Behaviors from Audit Logs via Aggregation of Contextual Semantics | NDSS'21 | | Behavior abstraction via semantic embeddings |

---

## Threat Hunting & Tactic Recognition

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **TREC**: APT Tactic/Technique Recognition via Few-Shot Provenance Subgraph Learning | CCS'24 | [arxiv](https://arxiv.org/abs/2402.15147) · [pdf](TREC_2024.pdf) | Few-shot tactic recognition |
| 2 | **ProvG-Searcher**: A Graph Representation Learning Approach for Efficient Provenance Graph Search | CCS'23 | | Learned subgraph matching for hunting queries |
| 3 | **POIROT**: Aligning Attack Behavior with Kernel Audit Records for Cyber Threat Hunting | CCS'19 | | CTI query graph alignment |

---

## Adversarial Robustness

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **Evading Provenance-Based ML Detectors with Adversarial System Actions** | USENIX Sec'23 | | Realistic adversarial system actions |
| 2 | **Sometimes, You Aren't What You Do**: Mimicry Attacks against Provenance Graph Host Intrusion Detection Systems | NDSS'23 | | Mimicry attacks evading graph-level PIDS |

---

## Privacy-Preserving Detection

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **MIRAGE**: Private Yet Accurate, A Decentralized Approach to System Intrusion Detection | PRISM@NDSS'26 | [program](https://www.ndss-symposium.org/ndss-program/prism-2026/) | First privacy-preserving, decentralized PIDS |

---

## Provenance Capture, Storage & EDR Integration

| # | Paper | Venue | Links | Key Technique |
|---|-------|-------|-------|---------------|
| 1 | **Cerberus**: Robust Endpoint Threat Detection in Practice | FSE'26 | | Deployed endpoint detection |
| 2 | **How to Effectively Trace Provenance on Windows Endpoint Detection & Response Telemetry** | PRISM@NDSS'26 | [pdf](https://www.ndss-symposium.org/wp-content/uploads/prism2026-12.pdf) | Whole-system provenance from commercial EDR telemetry + denoising |
| 3 | **SYSARMOR**: The Practice of Integrating Provenance Analysis into EDR Systems | PRISM@NDSS'26 | [pdf](SYSARMOR_PRISM2026.pdf) | Microservice EDR, async NODLINK/KNOWHOW detection |
| 4 | **Are We There Yet? An Industrial Viewpoint on Provenance-based Endpoint Detection and Response Tools** | CCS'23 | | Industry gaps for provenance EDR |
| 5 | **The Case for Learned Provenance Graph Storage Systems** | USENIX Sec'23 | | Learned compression for provenance storage |
| 6 | **CamFlow**: Practical Whole-System Provenance Capture | SoCC'17 | | LSM-based Linux provenance capture |

---

## Datasets & Benchmarks

| Dataset | Description | Source |
|---------|-------------|--------|
| **DARPA TC (E3/E5)** | Transparent Computing engagements (CADETS, THEIA, TRACE, ClearScope, FiveDirections); the default PIDS benchmark | [GitHub](https://github.com/darpa-i2o/Transparent-Computing) |
| **DARPA OpTC** | Operationally Transparent Cyber, enterprise-scale Windows telemetry | [GitHub](https://github.com/FiveDirections/OpTC-data) |
| **StreamSpot** | Streaming heterogeneous information flow graphs | [paper](https://dl.acm.org/doi/10.1145/2939672.2939716) |
| **Unicorn SC** | Supply-chain attack scenarios from CamFlow | [paper](https://dl.acm.org/doi/10.1145/3319535.3363214) |
| **PROVATTACK** | Next-generation multi-stage attack benchmark from [Building Next-Generation Datasets for Provenance-Based Intrusion Detection](https://www.ndss-symposium.org/wp-content/uploads/prism2026-21.pdf) (PRISM@NDSS'26) | [pdf](https://www.ndss-symposium.org/wp-content/uploads/prism2026-21.pdf) |

---

## Open Source Code

| Paper | Code | Stars |
|-------|------|-------|
| PIDSMaker | [ubc-provenance/PIDSMaker](https://github.com/ubc-provenance/PIDSMaker) | ![](https://img.shields.io/github/stars/ubc-provenance/PIDSMaker?style=social) |
| ORTHRUS | [ubc-provenance/orthrus](https://github.com/ubc-provenance/orthrus) | ![](https://img.shields.io/github/stars/ubc-provenance/orthrus?style=social) |
| MAGIC | [FDUDSDE/MAGIC](https://github.com/FDUDSDE/MAGIC) | ![](https://img.shields.io/github/stars/FDUDSDE/MAGIC?style=social) |
| CAPTAIN | [LexusWang/CAPTAIN](https://github.com/LexusWang/CAPTAIN) | ![](https://img.shields.io/github/stars/LexusWang/CAPTAIN?style=social) |
| DARPA TC | [darpa-i2o/Transparent-Computing](https://github.com/darpa-i2o/Transparent-Computing) | ![](https://img.shields.io/github/stars/darpa-i2o/Transparent-Computing?style=social) |

> 📢 Know of code for another listed paper? PRs welcome.

---

## 🔧 Contributing

Format:

```markdown
| # | **Paper Title**: Description | Venue | [arxiv](url) · [pdf](file.pdf) | Key technique |
```

**Guidelines:**
1. PDF naming: `PaperName_Year.pdf`
2. Newest first within each table
3. Peer-reviewed papers only. Preprints are added once accepted at a top venue or the PRISM/TaPP workshops

---

## 📄 License

MIT

---

<p align="center">
  <b>If you find this repository useful, please consider giving it a ⭐</b>
</p>
