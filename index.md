# Project Proposal: Predicting Emotional Regulation Success from EEG Using Contrastive Learning

## Motivation
Rather than just classifying emotional states (happy, sad, aroused, etc.), this project aims to predict an individual's ability to regulate their emotions based on their neurophysiological signatures during stimuli.

## Dataset: DEAP
- **Name:** DEAP (Database for Emotion Analysis using Physiological Signals)
- **Description:** EEG and peripheral physiological signals from 32 participants watching emotional videos.
- **Features:** 32-channel EEG, self-reports, 40 video trials per subject.

## Objective
Use contrastive learning to learn EEG representations that distinguish between successful and unsuccessful emotional regulation.

## Methodology

### 1. Preprocessing
- Band-pass filtering (1–50 Hz)
- Epoch extraction and artifact removal (eye movements, etc)
- Baseline normalization

### 2. Contrastive Learning Framework
- SimCLR or EEG-specific architecture (e.g., EEGNet + projection head)
- Positive pairs: same trial, different segments or augmentations
- Negative pairs: trials from different emotional states

### 3. Classifier
- Train a downstream MLP or SVM on the learned representations to classify regulation success (high vs. low arousal/valence)

## 4. Evaluation
- Metrics: Accuracy, F1, ROC-AUC
- Cross-subject generalization

## 5. Challenges
- EEG noise and variability
- Label ambiguity or subjectiveness in self-reported ratings
- Limited sample size

## 6. Timeline
| Week | Task |
|------|------|
| 1-2  | Dataset review, preprocessing setup, implement learning model, feature extraction and classifier | 
|  3   | Evaluation and presentation |

---

## Author
- Xiaoan Wang

