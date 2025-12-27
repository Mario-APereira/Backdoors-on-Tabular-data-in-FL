# Backdoors on Tabular Data in Federated Learning

This repository contains code, experiments, and documentation for the master's thesis "Backdoor Attacks on Tabular Data in Federated Learning".

Federated Learning (FL) allows multiple clients to collaboratively train machine learning models without sharing raw data. This work studies backdoor attacks and defenses specifically for tabular data in FL settings.

## Internship goals

- Analyze how backdoor attacks affect tabular data models in horizontal federated learning (HFL) and Federated Transfer Learning (FTL).
- Implement and evaluate representative backdoor attack methods on tabular datasets.
- Study the effectiveness of existing defenses and propose improvements or best practices.
- Provide reproducible experiments and evaluation scripts.

## Datasets used in the thesis

The experiments in this repository focus on tabular datasets. Datasets used (or referenced) in the thesis include examples and domain-specific datasets. Update this list to reflect the exact datasets you used in your experiments:
Data used

- Forest Cover Type (CovType): http://archive.ics.uci.edu/ml/datasets/covertype
- Lending Club Loan (LOAN): https://www.kaggle.com/datasets/mariopereira8/loan-accepted-loans-dataset
- Higgs Boson (HIGGS): https://archive.ics.uci.edu/dataset/280/higgs. Also available on Kaggle: https://www.kaggle.com/datasets/erikbiswas/higgs-uci-dataset

## Models and federated setups

The thesis experiments compare several model families commonly used on tabular data. Update the list below to reflect the exact models implemented in `src/`:

- Logistic Regression (sklearn) — baseline linear model
- Random Forest / Gradient Boosted Trees (sklearn / XGBoost / LightGBM) — strong tabular baselines
- Simple fully-connected neural networks (PyTorch / TensorFlow) — used for investigating learned feature backdoors in neural models
- (Optional) TabNet or other specialized tabular architectures — include if used

Federated learning setup:

- Simulated cross-device FL using FedAvg (centralized server aggregation);
- Experiments with different numbers of clients, data heterogeneity levels (IID vs non-IID), and malicious client fractions;
- Attack scenarios: targeted backdoor triggers, label-flipping, and data-poisoning approaches adapted to tabular features;

## Files

- *.ipynb: notebooks used for each experiment;
- *.pth.zip: pretrained weights of our TabNet for each dataset;
- *.csv: dataset files (only for CovType, others are too big, require local download).


## How to run the notebooks

1. Create and activate a virtual environment and install requirements:

```bash
python -m venv .venv
source .venv/bin/activate  # macOS / Linux
pip install -r requirements.txt
