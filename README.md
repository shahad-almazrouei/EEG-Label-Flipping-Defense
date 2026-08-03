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

- **Model I:** Baseline EEG emotion classification using multiple machine learning classifiers.
- **Model II:** Label-flipping poisoning attack to evaluate model vulnerability.
- **Model III:** Agent-based defense framework to detect, repair, and validate poisoned data before retraining.

### Agent-Based Defense Pipeline


<img width="370" height="678" alt="image" src="https://github.com/user-attachments/assets/9ddaa925-d7f0-4894-8a7a-a684ec49972d" />


---

## Model I – Baseline Classification

Three supervised machine learning models were trained and evaluated on the clean EEG dataset:

- Random Forest
- Support Vector Machine (SVM)
- Multi-Layer Perceptron (MLP)

These models established the baseline performance before introducing adversarial attacks.

---

## Model II – Label-Flipping Poisoning Attack

A label-flipping attack was implemented by randomly modifying the labels of **15% of the training samples** while leaving the feature vectors unchanged.

This simulated a realistic training-time poisoning attack and demonstrated how corrupted labels can significantly degrade classification performance.

---

## Model III – Agent-Based Defense

To mitigate the poisoning attack, a sequential multi-agent defense framework was developed consisting of three specialized agents.

### Label Curator Agent

- Detects suspicious labels using a trusted Random Forest reference model.
- Corrects mislabeled samples with high-confidence predictions.

### Centroid-Based Curator Agent

- Computes class centroids within the feature space.
- Detects structural anomalies based on centroid distance.
- Removes suspicious feature-space outliers.

### Validator Agent

- Evaluates candidate cleaned datasets using Logistic Regression.
- Selects the dataset that provides the best validation performance before retraining the final classifier.

---

## Experimental Results

The project compares three scenarios:

- **Model I:** Baseline classifier trained on clean data.
- **Model II:** Classifier trained on poisoned data after a 15% label-flipping attack.
- **Model III:** Defended classifier trained using the proposed multi-agent defense pipeline.

The experimental evaluation demonstrated that:

- Label-flipping attacks reduced the reliability of the EEG emotion classifier.
- The proposed multi-agent defense improved model robustness by correcting mislabeled samples and removing anomalous data.
- Combining label correction, feature-space cleaning, and validation produced stronger results than applying a single defense strategy alone.

---

## Project Presentation

A summary of the project, methodology, defense pipeline, experimental evaluation, and results is available in:

- **Project_Presentation.pdf**
