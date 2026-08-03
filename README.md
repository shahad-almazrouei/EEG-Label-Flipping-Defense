# Agent-Based Defense Against Label-Flipping Poisoning Attacks in EEG Emotion Classification

An AI security project that investigates the impact of label-flipping data poisoning attacks on EEG emotion classification and proposes a multi-agent defense framework to improve model robustness against adversarial training-time attacks.

---

## Project Overview

Machine learning models are vulnerable to data poisoning attacks, where maliciously modified training data degrades model performance. This project investigates the effects of label-flipping poisoning attacks on EEG-based emotion classification and develops an agent-based defense framework to detect, correct, and mitigate poisoned training samples before model retraining.

The proposed defense pipeline combines multiple autonomous agents that collaboratively improve dataset quality and restore classification performance after a poisoning attack.

---

## Dataset

The project uses a preprocessed EEG emotion classification dataset containing numerical features extracted from five EEG electrode locations.

The dataset was provided as part of the **COSC 435** course at **Khalifa University** and is **not included in this repository**.

The original dataset consists of EEG frequency-band features representing four emotion classes and was supplied as separate training and testing datasets.

---

## Objectives

- Develop baseline EEG emotion classification models.
- Simulate a label-flipping data poisoning attack.
- Measure the impact of poisoning on model performance.
- Design a multi-agent defense framework against poisoned training data.
- Compare baseline, poisoned, and defended models using multiple evaluation metrics.

---

## Project Workflow

The project consists of three stages:

### Model I – Baseline Classification

Three supervised machine learning models were trained on the clean EEG dataset:

- Random Forest
- Support Vector Machine (SVM)
- Multi-Layer Perceptron (MLP)

The baseline models establish the reference performance before introducing adversarial attacks.

---

### Model II – Label-Flipping Poisoning Attack

A label-flipping attack was implemented by randomly changing the labels of 15% of the training samples while leaving the feature vectors unchanged.

The objective was to evaluate how corrupted training labels affect model performance and robustness.

---

### Model III – Agent-Based Defense

A multi-agent defense pipeline was developed to mitigate the poisoning attack before retraining the classifier.

The pipeline consists of three autonomous agents:

### Label Curator Agent

- Detects suspicious labels using a trusted baseline Random Forest model.
- Identifies inconsistencies between predicted and assigned labels.
- Corrects mislabeled samples before further processing.

### Centroid-based Curator Agent

- Computes feature-space centroids for each emotion class.
- Detects structural anomalies based on centroid distance.
- Removes suspicious feature-space outliers.

### Validator Agent

- Trains lightweight Logistic Regression models on candidate cleaned datasets.
- Compares validation performance.
- Selects the dataset that provides better generalization for final model training.

---

## Experimental Results

The project compares three scenarios:

- **Model I:** Baseline model trained on clean data.
- **Model II:** Model trained on poisoned data after a 15% label-flipping attack.
- **Model III:** Defended model trained using the proposed multi-agent defense pipeline.

The experimental results demonstrate that:

- Label-flipping attacks significantly reduce classification performance.
- The proposed defense pipeline successfully improves model robustness after poisoning.
- Combining label correction, feature-space cleaning, and validation provides better resilience than relying on a single defense mechanism.

---

## Academic Project

This project was developed as part of the **COSC 435** course at **Khalifa University**.
