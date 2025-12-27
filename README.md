# Backdoors on Tabular Data in Federated Learning

This repository contains code, experiments, and documentation for the master's thesis "Backdoors on Tabular Data in Federated Learning" by Mario A. Pereira.

## Overview

Federated Learning (FL) allows multiple clients to collaboratively train machine learning models without sharing raw data. This work studies backdoor attacks and defenses specifically for tabular data in FL settings. The repository includes implementations of attack methods, defense strategies, experimental pipelines, and supporting analysis for the thesis.

## Thesis goals

- Analyze how backdoor attacks affect tabular data models in federated learning.
- Implement and evaluate representative backdoor attack methods on tabular datasets.
- Study the effectiveness of existing defenses and propose improvements or best practices.
- Provide reproducible experiments and evaluation scripts.

## Repository structure

- data/                - scripts & instructions for preparing datasets (not included due to privacy/legal constraints)
- src/                 - implementation of models, attacks, defenses, and training pipelines
- experiments/         - experiment configurations and runner scripts
- notebooks/           - analysis and visualization notebooks
- results/             - experiment outputs, logs, and trained models
- docs/                - additional documentation, diagrams, and thesis excerpts
- requirements.txt     - Python dependencies
- README.md            - this file

(Adjust folder names if your repository uses a different structure.)

## Datasets used in the thesis

The experiments in this repository focus on tabular datasets. Datasets used (or referenced) in the thesis include examples and domain-specific datasets. Update this list to reflect the exact datasets you used in your experiments:

- UCI Adult (Income) — common tabular benchmark for classification and fairness-related experiments.
- Kaggle Credit Card Fraud Detection — used for imbalanced classification and attack robustness testing.
- UCI Credit Approval / German Credit — used for credit-risk-like scenarios and tabular modeling.
- Any domain-specific datasets you collected or had access to (obey licensing and privacy constraints).

If you used other datasets (e.g., proprietary or hospital/financial data), list them in `data/README.md` and provide instructions for obtaining/preprocessing.

## Models and federated setups

The thesis experiments compare several model families commonly used on tabular data. Update the list below to reflect the exact models implemented in `src/`:

- Logistic Regression (sklearn) — baseline linear model
- Random Forest / Gradient Boosted Trees (sklearn / XGBoost / LightGBM) — strong tabular baselines
- Simple fully-connected neural networks (PyTorch / TensorFlow) — used for investigating learned feature backdoors in neural models
- (Optional) TabNet or other specialized tabular architectures — include if used

Federated learning setup and flavors evaluated:

- Simulated cross-silo or cross-device FL using FedAvg (centralized server aggregation)
- Experiments with different numbers of clients, data heterogeneity levels (IID vs non-IID), and malicious client fractions
- Attack scenarios: targeted backdoor triggers, label-flipping, and data-poisoning approaches adapted to tabular features
- Defenses evaluated: robust aggregation (median, trimmed mean), anomaly detection on updates, differential privacy, and client-level validation

## Notebooks

The `notebooks/` directory contains interactive analyses used during the thesis. Typical notebooks include:

- 00_data_exploration.ipynb — dataset summaries, missing values, feature distributions, and exploratory visualizations
- 01_preprocessing.ipynb — feature engineering steps, encoders, scaling, train/val/test splits, and scripts used to create the `data/` artifacts
- 02_baseline_training.ipynb — standalone training (non-federated) of baseline models and metric computations
- 03_federated_simulation.ipynb — example federated training loop (FedAvg), client selection, and aggregation behavior visualization
- 04_attack_experiments.ipynb — code and analysis for injecting backdoors into client updates or datasets and measuring attack success rate
- 05_defense_evaluation.ipynb — evaluation of defenses, robustness metrics, and trade-offs (utility vs security)
- 06_results_plots.ipynb — generation of the figures and tables used in the thesis write-up

Each notebook is organized to be runnable end-to-end (where possible). Notebooks include configuration cells at the top that point to `experiments/configs/*.yaml` where reproducible runs are defined.

## How to run the notebooks

1. Create and activate a virtual environment and install requirements:

```bash
python -m venv .venv
source .venv/bin/activate  # macOS / Linux
pip install -r requirements.txt
