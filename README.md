# Feature-Space and Label-Flip Poisoning Attacks on Adversarial Training Defenses

[![DOI](https://img.shields.io/badge/preprint-arXiv%3Axxxx.xxxxx-blue.svg)](https://arxiv.org/abs/xxxx.xxxxx) 
<!-- Uncomment if your paper is on arXiv --><!-- Remove if not relevant -->

## Overview

This repository contains the code and experimental results for our paper:

**"Feature-Space and Label-Flip Poisoning Attacks on Adversarial Training Defenses"**

Our work explores the vulnerability of online/streaming classifiers—especially tree-based models and ensembles—to two types of poisoning attacks (label flip and feature-space noise) and evaluates how adversarial training and drift detection interact as defenses. We combine an AutoML pipeline with a broad experimental framework for reproducibility and comparative benchmarking.

## Main Contributions

- **AutoML pipeline** for feature engineering, imputation, normalization, and feature selection.
- **Label-flip (dirty-label) poisoning**: randomly flips sample labels to simulate adversarial contamination.
- **Feature-space (clean-label) poisoning**: applies uniform noise injection to every feature, attacking the data distribution.
- **Adversarial Training (AT) defense**: model retraining using adversarially-perturbed samples at every batch.
- **Online concept drift detection** via EDDM, DDM, and ADWIN.
- **Evaluation on IoT and CIC datasets** using a variety of River-stream classifiers: HoeffdingTree, HoeffdingAdaptiveTree, AdaptiveRandomForest, LeveragingBagging, SRPClassifier, MondrianTree.
- **Comprehensive analysis of drift/poison overlap and AT-vs-naive robustness.**

## File Structure

- `experiments/main.py` ... Main script for running experiments (see below)
- `online_automl/poisoning.py`, `train.py`, `preprocessing.py`, `drift.py` ... Modular utility code
- `data/IoT_2020_b_0.01.csv`, `data/cic_0.01km.csv` ... Datasets (not included due to size, download as needed)

## Usage

### 1. Clone the Repo

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
