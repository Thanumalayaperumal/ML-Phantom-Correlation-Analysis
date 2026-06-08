# Machine Learning-Based Identification of Phantom Correlations

## Overview

This project investigates a fundamental challenge in machine learning and data-driven materials science: **phantom correlations** (also known as spurious or proxy correlations).

A phantom feature may appear highly predictive of a target variable based on correlation metrics and model performance, despite having no direct causal relationship with the target. Such features can mislead data-driven discovery and result in models that fail to generalize beyond the training data.

This project develops a synthetic dataset with hidden material families and demonstrates how conventional feature ranking methods can incorrectly identify a proxy variable as an important descriptor.

---

## Problem Statement

Machine learning models often rely on statistical relationships to identify important features. However, a feature may appear important simply because it is correlated with a true causal driver.

This project addresses the following question:

> How can we distinguish a genuinely causal feature from a phantom feature that only appears important due to hidden correlations?

---

## Dataset Description

A synthetic dataset containing **260 samples** was generated and divided into two hidden material families:

- Family A (130 samples)
- Family B (130 samples)

### Features

| Feature | Role |
|----------|----------|
| true_driver | Actual causal variable |
| shadow_feature | Phantom proxy feature |
| weak_feature | Weak but genuine contributor |
| noise1 | Random noise |
| noise2 | Random noise |
| target | Response variable |

The target property is generated using:

target = 2.3 × sin(true_driver / 2) + 0.55 × weak_feature + noise

Importantly, **shadow_feature does not appear in the target equation** and therefore has no direct causal influence.

---

## Methodology

The project is divided into two major phases.

### Phase 1: Global (Naive) Analysis

Features are evaluated without considering hidden family structure.

Techniques used:

- Scatter Plot Analysis
- Pearson Correlation Analysis
- Single-Feature Linear Regression
- R² Ranking

Result:

Both `true_driver` and `shadow_feature` appear highly predictive, creating the illusion that the phantom feature is important.

---

### Phase 2: Regime-Aware Analysis

Hidden family information is introduced to test feature robustness.

Techniques used:

- Family-wise Correlation Analysis
- Family-wise R² Evaluation
- Cross-Family Generalization Testing
- Residual Structure Analysis
- Stability Assessment Across Regimes

Result:

The predictive power of `shadow_feature` collapses when evaluated across families, while `true_driver` remains consistently predictive.

---

## Controlled Intervention Testing

To distinguish correlation from causation, intervention experiments were performed.

### Intervention 1

Vary `true_driver` while keeping all other variables fixed.

Observation:

- Target changes systematically.
- Causal relationship confirmed.

### Intervention 2

Vary `shadow_feature` while keeping `true_driver` fixed.

Observation:

- Target remains unchanged.
- No causal relationship exists.

This confirms that `shadow_feature` is a phantom descriptor.

---

## Machine Learning Models Used

### Linear Regression

Used for:

- Single-feature R² analysis
- Baseline comparison

### Polynomial Regression

Used to capture nonlinear relationships between:

- true_driver
- target

### Random Forest Regression

Used for:

- Nonlinear modeling
- Feature importance analysis
- Robust predictive comparison

---

## Feature Importance Analysis

The following diagnostic techniques were applied:

- Correlation Analysis
- R² Ranking
- Cross-Family Validation
- Residual Analysis
- Conditional Importance Testing
- Permutation Importance

These analyses consistently identified:

✅ true_driver as the genuine causal feature

❌ shadow_feature as a phantom proxy

---

## Key Findings

- High correlation does not imply causation.
- Phantom features can appear highly predictive.
- Hidden regimes can create misleading feature importance.
- Cross-family generalization is an effective diagnostic tool.
- Intervention testing provides strong evidence for causal relevance.
- Feature importance should be evaluated using robustness, not only predictive performance.

---

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Scikit-Learn
- Jupyter Notebook

---

## Repository Structure

```text
ML-Phantom-Correlation-Analysis/
│
├── notebooks/
│   └── phantom_correlation_detection.ipynb
│
├── report/
│   └── Machine_Learning_Based_Identification_of_Phantom_Correlations.pdf
│
├── images/
│
├── README.md
│
└── requirements.txt
```

---

## Results

The study demonstrates that a feature can achieve high predictive performance while lacking any direct causal influence on the target variable.

Through regime-aware analysis, intervention testing, and permutation importance evaluation, the project successfully distinguishes true physical drivers from phantom proxies.

---

## Author

**Thanumalayaperumal T**

M.Tech Integrated Computational Engineering

Indian Institute of Technology Madras

---

## License

This project is intended for academic and educational purposes.
