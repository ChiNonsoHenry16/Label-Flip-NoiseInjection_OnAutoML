# Online AutoML: Evaluating Poisoning Attacks on Adversarial Training Defense Strategy in IoT Networks

This repository contains the implementation, experimental results, and supplementary materials for the research paper:

> **Online AutoML: Evaluating Poisoning Attacks on Adversarial Training Defense Strategy in IoT Networks**

**Authors:**  
Chukwunonso Henry Nwokoye, Khalil El-Khatib, and Li Yang

**Affiliations:**  
Faculty of Business and Information Technology, Ontario Tech University, Oshawa, Ontario, Canada  
Department of Computer Science, Alex Ekwueme Federal University, Nigeria

---

## Abstract

Machine learning (ML)-powered poisoning attacks are adversarial techniques in which an attacker intentionally inserts, corrupts, or alters training data to distort the learning process. In streaming environments, these attacks present a significant threat because online models continuously update using incoming data.

This study evaluates the effectiveness of **adversarial training (AT)** against two poisoning attacks—**label flip** and **noise injection**—within an online AutoML pipeline for Internet of Things (IoT) networks.

Five streaming-capable classifiers are evaluated:

- Hoeffding Tree (HT)
- Leveraging Bagging (LB)
- Streaming Random Patches (SRP)
- Hoeffding Adaptive Tree (HAT)
- Adaptive Random Forest (ARF)

The experiments compare naive and adversarially trained models using accuracy, precision, recall, and F1-score. The study also evaluates the behavior of three concept-drift detectors:

- Early Drift Detection Method (EDDM)
- Drift Detection Method (DDM)
- Adaptive Windowing (ADWIN)

At the maximum poisoning rate of **1.0**, AT-SRP achieved the highest F1-score against label-flip poisoning (**0.904**), while AT-LB achieved the highest F1-score against noise-injection poisoning (**0.933**).

---

## Research Objectives

The study investigates:

1. The impact of poisoning attacks on online AutoML classifiers operating on IoT data streams.
2. The effectiveness of adversarial training as a defense against poisoning attacks.
3. The behavior of concept-drift detectors under poisoned streaming conditions.
4. The relationship between detected concept drift and poisoned samples.

---

# Main Contributions

- **AutoML pipeline** for feature engineering, imputation, normalization, and feature selection.
- **Label-flip (dirty-label) poisoning**: randomly flips sample labels to simulate adversarial contamination.
- **Noise injection (clean-label) poisoning**: applies uniform adversarial noise to every feature, attacking the data distribution.
- **Adversarial Training (AT) defense**: model retraining using adversarially-perturbed samples at every batch.
- **Online concept drift detection** via EDDM, DDM, and ADWIN.
- **Evaluation on IoT20 dataset** using a variety of River-stream classifiers: HoeffdingTree, HoeffdingAdaptiveTree, AdaptiveRandomForest, LeveragingBagging, SRPClassifier, MondrianTree.
- **Comprehensive analysis of drift/poison overlap and AT-vs-naive robustness.**

## Experimental Framework

The proposed experimental framework follows this workflow:

```text
IoTID20 Traffic
      │
      ▼
Streaming Samples
      │
      ▼
Online AutoML
      │
      ├── Auto-Encoding
      ├── Auto-Imputation
      ├── Auto-Normalization
      └── Auto-Feature Engineering
      │
      ▼
Streaming Classifiers
      │
      ├── Hoeffding Tree
      ├── Leveraging Bagging
      ├── SRPClassifier
      ├── Hoeffding Adaptive Tree
      └── Adaptive Random Forest
      │
      ├───────────────────────┐
      ▼                       ▼
Naive Models             AT Models
Clean Samples            Clean + Perturbed Samples
      │                       │
      └───────────┬───────────┘
                  ▼
          Poisoning Attacks
                  │
          ┌───────┴────────┐
          ▼                ▼
     Label Flip      Noise Injection
          │                │
          └───────┬────────┘
                  ▼
        Performance Evaluation
                  │
       ┌──────────┼──────────┐
       ▼          ▼          ▼
   Accuracy    Precision   Recall/F1
                  │
                  ▼
           Drift Detection
                  │
        ┌─────────┼─────────┐
        ▼         ▼         ▼
      EDDM       DDM      ADWIN
                  │
                  ▼
         Drift-Poison Overlap
                  │
                  ▼
          Robustness Analysis




