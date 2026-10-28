# AI Learning Route — Well Production ML (Repo #1)

Repo #1 of four in a 14-week, self-study **AI/ML Learning Route Map** (Oct 19, 2026 → Feb 5, 2027). It covers **production engineering in oil and gas**: forecasting well production with tabular ML, then adding uncertainty, foundation-model benchmarks and a deployable service.

**Goal:** show industry-grade ML rigor on real well data: leakage-free validation, interpretability, calibrated uncertainty and production deployment.

---

## Where this repo fits

| # | Repo | Focus | Route weeks |
|---|------|-------|-------------|
| **1** | **well-production-ml** (this repo) | **Tabular ML, uncertainty, deployment** | **1, 10, 11, 14** |
| 2 | petro-rag | RAG with citations, evals, multimodal retrieval | 7, 9, 11, 12 |
| 3 | well-tools-mcp | Agent tools, MCP server, Skills | 8, 11, 14 |
| 4 | subsurface-dl-lab | Clustering, CNN/GNN, generative & Bayesian methods, well world model | 2, 3, 4, 13 |

Each repo is built step by step during its route weeks. Every week ends with a push.

---

## Learning path in this repo

Each step builds on the model from the step before.

### 1. Build a rigorous baseline (Week 1 · Oct 19–23)
| Day | Topic | Output |
|-----|-------|--------|
| 1 | scikit-learn Pipelines and cross-validation | End-to-end pipeline notebook |
| 2 | XGBoost and data leakage | Two leakage traps in well data (gauge-derived features, random splits across time) |
| 3 | GroupKFold and TimeSeriesSplit | Unbiased training set expressed as GroupKFold by well |
| 4 | **Lab:** Volve daily production with LightGBM, well-held-out split | Per-well error table |
| 5 | SHAP (TreeSHAP) on the lab model | SHAP summary plot |

### 2. Add energy-AI methods and uncertainty (Week 10 · Jan 4–8)
| Day | Topic | Output |
|-----|-------|--------|
| 3 | **Lab:** Chronos-2 zero-shot forecast (with covariates) vs LSTM baseline | Foundation-model benchmark |
| 4 | **Lab:** MAPIE conformal prediction, 90% intervals | Coverage plot on held-out wells |

### 3. Ship it (Week 11 · Jan 11–15)
| Day | Topic | Output |
|-----|-------|--------|
| 1 | Production-readiness: tracking, testing, drift monitoring | Checklist for well models |
| 2 | **Lab:** serve the model with FastAPI + Docker; log runs in MLflow | Running container, documented endpoint |
| 4 | Capstone polish | Final README (problem → data → method → result → limits) |

### 4. Compare with a frontier model (Week 14 · Feb 1–5)
| Day | Topic | Output |
|-----|-------|--------|
| 3 | **Lab:** TabPFN vs LightGBM on the Week-1 task | Result and licence note |

---

## What this repo demonstrates

- **Validation rigor:** well-grouped and time-aware splits, explicit leakage checks
- **Interpretability:** SHAP feature attributions
- **Uncertainty:** conformal intervals with checked coverage
- **Benchmarking:** LightGBM vs Chronos-2, LSTM and TabPFN
- **Production ML:** FastAPI, Docker, MLflow, drift monitoring

**Target roles:** reservoir/production data scientist; ML engineer (energy).

---

## Data

[Equinor Volve dataset](https://www.equinor.com/energy/volve-data-sharing): daily well production from a Norwegian North Sea field.
Volve is released under Equinor's own licence. Check its terms before publishing derived data. This repo publishes code and results only.
TabPFN-2.5+ weights are non-commercial, so they are used here as a research benchmark only.

## Tools and resources

scikit-learn · LightGBM / XGBoost · SHAP · MAPIE · Chronos-2 · TabPFN · FastAPI · Docker · MLflow

All core resources are free: Kaggle Learn (Intermediate ML), scikit-learn docs, Molnar's *Interpretable ML* (SHAP chapter), Made With ML, plus *Designing Machine Learning Systems* ch. 8 through library access.

---

## Progress

- [ ] Week 1: Pipeline, leakage notes, GroupKFold baseline, per-well errors, SHAP
- [ ] Week 10: Chronos-2 benchmark, conformal intervals
- [ ] Week 11: FastAPI + Docker service, MLflow tracking, final README
- [ ] Week 14: TabPFN comparison

## License

[MIT](LICENSE)
