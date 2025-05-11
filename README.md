
# Predicting Emotional Regulation from EEG Using Contrastive Learning

## Overview
This project aims to go beyond traditional emotion classification by predicting an individual's **ability to regulate emotions** from EEG signals during emotional stimulation. Using the DEAP open dataset, we apply cutting-edge contrastive learning techniques to model latent emotion regulation capacity from brain signals.

---

## Project Motivation
Rather than just classifying emotional states (happy, sad, aroused, etc.), this project aims to predict an individual's ability to regulate their emotions based on their neurophysiological measures during emotional stimuli.
![Emotion Regulation](https://behavioranalystresourcecenter.com/wp-content/uploads/Screenshot-2023-03-06-at-10.53.36-PM.png)

### Key Innovations:
- Explore **emotion regulation**, not just emotion detection.
- Try **contrastive learning**, a modern unsupervised deep learning approach for EEG.
- Study cognitive neuroscience concepts using machine learning technique.

Contrastive learning has recently shown strong performance in EEG-based emotion recognition. It functions by teaching models to distinguish between positive pairs (same label or segment) and negative pairs (different labels) of data. Recent studies demonstrate that integrating Graph Convolutional Networks (GCNs) into contrastive learning significantly enhances performance by encoding spatial dependencies between electrodes. For example, a 2022 paper titled "Self-supervised Group Meiosis Contrastive Learning for EEG-Based Emotion Recognition" achieved over 95% accuracy on the DEAP dataset using GCNs and contrastive learning jointly.

Another innovation is PhysioSync, which applies temporal and cross-modal contrastive learning to synchronize EEG with physiological signals like GSR or EMG, furthure improving emotional representation learning across time and modality in a 2025 study titled "PhysioSync: Temporal and Cross-Modal Contrastive Learning Inspired by Physiological Synchronization for EEG-Based Emotion Recognition".

---

## Dataset: DEAP
We use the [DEAP dataset](https://www.eecs.qmul.ac.uk/mmv/datasets/deap/):
The DEAP dataset (Dataset for Emotion Analysis using Physiological Signals) is a widely used open dataset for study of affective states. Collected by Koelstra et al. (2012), the dataset provides a comprehensive framework for analyzing emotional responses to audiovisual stimuli and has become a benchmark for emotion recognition experiments.

DEAP recorded 32 participants who each watched 40 one-minute music video clips selected to trigger a range of emotional reactions. During each trial, subjects’ EEG and several peripheral physiological measures (including electrooculogram, electromyogram, galvanic skin response, blood volume pulse, respiration, and temperature) were recorded. Additionally, frontal face videos of the participants were captured.

After each video, subjects rated their emotional experience on four self-assessment scales, each ranging from 1 to 9: valence (pleasantness), arousal (intensity of emotion), dominance (feeling of control), liking (subjective preference for the video).

**EEG Data Structure:**
- 32 electrodes (10–20 system), sampled at 512 Hz (downsampled to 128 Hz)
- Preprocessed: bandpass filtered (4–45 Hz), ICA cleaned, re-referenced

---

## Assumptions for Labeling
We hypothesize emotion regulation based on patterns in self-report and EEG:

-	Low arousal with high valence after a high-arousal stimulus → possible regulation
-	Use self-report 'liking' or 'familiarity' to infer engagement/regulation potential
-	Compare early vs. late EEG segments to infer downregulation over time


---

## Scope & Constraints
To ensure feasibility within BrainHack timeframe:

1. Use **5 subjects** with highest data quality
2. Analyze **10 video clips per subject** (with strongest affective signal)
3. Focus on **one emotion dimension** (valence or arousal)

This proof-of-concept project lays groundwork for larger scale studies.

---

## Methodology
### 1. **EEG Preprocessing**
- Filtering, artifact removal (ICA), normalization
- Time-locked segmentation (2–5 sec windows)
- Feature extraction (Power Spectral Density)
- Data augmentation for contrastive training

### 2. **Contrastive Learning**
- Framework: SimCLR (or similar)
- Loss: NT-Xent (contrastive loss)
Apply contrastive learning (SimCLR) to learn emotionally discriminative EEG features. Learn embeddings via contrastive loss; predict with simple classifier. The contrastive model uses a small neural network backbone (i.e a few convolutional or dense layers) trained with NT-Xent loss. After pretraining, the learned embeddings are fed into a simple MLP classifier that predicts the participant's emotional regulation.

### 3. **Classifier / Prediction**
- Use learned embeddings to train:
  - **MLP classifier**
  - **Logistic / Linear regression (baseline)**
  - **SVM**

**Emotion Regulation Score**
- Based on self-report + EEG mismatch / time dynamics
- Binary or continuous target depending on assumption

---

## 4. **Evaluation Metrics**
Evaluation of the models include using F1 score, accuracy, ROC-AUC. Will also conduct visualizations such as t-SNE/UMAP.

---

## Relevant Works
- *X. Shen, X. Liu, X. Hu, D. Zhang and S. Song, "Contrastive Learning of Subject-Invariant EEG Representations for Cross-Subject Emotion Recognition," in IEEE Transactions on Affective Computing, vol. 14, no. 3, pp. 2496-2511, 1 July-Sept. 2023, doi: 10.1109/TAFFC.2022.3164516.
- *Zhang, Hong, et al. "PhysioSync: Temporal and Cross-Modal Contrastive Learning Inspired by Physiological Synchronization for EEG-Based Emotion Recognition." 2025. arXiv:2504.17163.

---

## Resources
- [DEAP Dataset](https://www.eecs.qmul.ac.uk/mmv/datasets/deap/)
- [SimCLR paper](https://arxiv.org/abs/2002.05709)

---

## Future Work
- Incorporate peripheral modalities (GSR, EMG) into contrastive framework
- Expand to all 32 subjects and full stimulus set
- Include GCNs and PhsioSync (cross-modal & temporal contrastive learning) in the model training
![Emotion Regulation](https://bewelltherapygroup.org/wp-content/uploads/2024/03/Untitled-design-67.png)

---

