# fill-probability-model

> **All data is synthetic or public. No employer or client data is used.** Training data is generated synthetically (reusing the `order-lifecycle-analyzer` event generator) or drawn from public datasets, and the source is documented in `data/README` when added.

Spans Penn Engineering courses **C6–C8**: Statistics Essentials, Machine Learning Essentials, and Deep Learning Essentials.

## Problem

**Binary classification: will an order fill within *N* seconds of being placed?**

This is the kind of question that gets answered with gut feel on a product team. The goal here is to answer it with a model, evaluate it honestly, and then decide whether the more complex model was worth it.

## Approach

The work is deliberately staged so each step has a baseline to beat:

1. **Baseline** — majority class and a one-feature rule (e.g. order size vs. median). Establishes the floor.
2. **Feature engineering** — order size, price distance from mid, venue, time-of-day, recent fill rate for the same instrument, and so on. Documented with the reasoning for each feature.
3. **Logistic regression** — the interpretable model. Coefficients are inspected, not just scored.
4. **Small neural net** — a compact MLP. Same features, same split, same metrics.

Throughout:

- A proper **train / validation / test split** (time-ordered, no leakage from the future).
- Metrics beyond accuracy: precision/recall, ROC-AUC, and PR-AUC on an imbalanced target.
- A **calibration check** (reliability diagram + Brier score), because a fill *probability* is only useful if 70% actually means 70%.

## The deliverable that matters

A written argument, in `notebooks/` and summarised below, answering: **did the deep model earn its complexity over logistic regression?** Judged on held-out performance, calibration, interpretability, and cost to maintain. A "no" is an acceptable answer if the evidence says so.

## Layout

```
fill-probability-model/
├── src/              data prep, features, models, evaluation
├── notebooks/        exploration and the final write-up
├── data/             git-ignored; see data/README for how to regenerate
├── tests/            pytest suite for feature and evaluation code
└── requirements.txt
```

## Running

```bash
pip install -r requirements.txt
pytest
jupyter lab notebooks/
```

## Results

_To be filled in: metrics table (baseline / logistic / MLP), reliability diagram, and the verdict._
