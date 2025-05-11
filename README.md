# Predicting Emotional Regulation from EEG Using Contrastive Learning

## Overview

This project aims to go beyond traditional emotion classification by predicting an individual's **ability to regulate emotions** from EEG signals during emotional stimulation. Using the DEAP open dataset, we apply cutting-edge contrastive learning techniques to model latent emotion regulation capacity from brain signals.

![EEG Emotion](./29d5c9e9-550e-4d32-84bd-f6b833e0f690.png)

---

## 💡 Project Motivation

While many studies focus on classifying emotional states (e.g., happy, sad, aroused), this project seeks to infer **how well a person regulates those emotions**, which has significant implications for affective computing, mental health research, and personalized neurofeedback systems.

### Key Innovations:
- Focus on **emotion regulation**, not just emotion detection.
- Leverage **contrastive learning**, a modern unsupervised deep learning approach for EEG.
- Integrate cognitive neuroscience concepts into machine learning pipelines.

---

## 🧠 Dataset: DEAP

We use the [DEAP dataset](https://www.eecs.qmul.ac.uk/mmv/datasets/deap/), a multimodal dataset for emotion analysis using physiological signals:

- **Subjects**: 32 participants
- **Stimuli**: 40 one-minute emotionally evocative music videos
- **Modalities**: EEG (32 channels), GSR, EMG, ECG, respiration, temperature, face video
- **Labels**: Self-reported valence, arousal, dominance, liking (1–9 scale)

**EEG Details:**
- 32 electrodes (10–20 system), sampled at 512 Hz (downsampled to 128 Hz)
- Preprocessed: bandpass filtered (4–45 Hz), ICA cleaned, re-referenced

---

## 🧪 Assumptions for Labeling Regulation

We hypothesize emotion regulation based on patterns in self-report and EEG:

- **Low arousal with high valence** after high-arousal stimuli may indicate downregulation.
- **Discrepancy between EEG activation and subjective ratings** could reflect cognitive modulation.
- **Temporal differences** (early vs. late EEG in the clip) may show regulation over time.

---

## 📉 Scope & Constraints

To ensure feasibility within BrainHack:

1. Use **5 subjects** with highest data quality
2. Analyze **10 video clips per subject** (with strongest affective signal)
3. Focus on **one emotion dimension** (valence or arousal)

This proof-of-concept lays groundwork for larger studies, even if generalizability is limited.

---

## 🔁 Methodology Pipeline

### 1. **EEG Preprocessing**
- Filtering, artifact removal (ICA), normalization
- Time-locked segmentation (2–5 sec windows)
- Feature extraction (Power Spectral Density)
- Data augmentation for contrastive training

### 2. **Contrastive Learning**
- Framework: SimCLR (or similar)
- Backbone: Shallow CNN or MLP
- Loss: NT-Xent (contrastive loss)

### 3. **Classifier / Prediction**
- Use learned embeddings to train:
  - **MLP classifier**
  - **Logistic / Linear regression (baseline)**
  - **SVM**

### 4. **Emotion Regulation Score**
- Based on self-report + EEG mismatch / time dynamics
- Binary or continuous target depending on assumption

---

## 📊 Evaluation Metrics

- **F1 Score**
- **Accuracy**
- **ROC-AUC**
- Embedding visualization (e.g., t-SNE/UMAP)

---

## 🔬 Relevant Works

- *Self-supervised Group Meiosis Contrastive Learning for EEG-Based Emotion Recognition* (2022) — GCNs + contrastive learning
- *PhysioSync* (2025) — Cross-modal & temporal contrastive learning

---

## 🔗 Resources

- 📁 [DEAP Dataset](https://www.eecs.qmul.ac.uk/mmv/datasets/deap/)
- 🧠 [SimCLR paper](https://arxiv.org/abs/2002.05709)
- 📘 GCN & EEG survey: [Link TBD]

---

## 🛠️ Future Work

- Incorporate peripheral modalities (GSR, EMG) into contrastive framework
- Expand to all 32 subjects and full stimulus set
- Test on other datasets (e.g., SEED, MAHNOB-HCI)

---

