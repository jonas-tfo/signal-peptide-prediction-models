# Signal Peptide Prediction using Machine Learning

## Overview

This project focuses on the classification of amino acid sequences and/or the contained individual amino acids into various different categories related to signal peptide types and residue locations using various machine learning models.

---

## Classification Tasks

- **2-state:**  
  - `0`: Non signal peptide  
  - `1`: Signal peptide

- **4-state:**  
  - Non signal peptide  
  - `S`: Sec/SPI  
  - `L`: Sec/SPII  
  - `T`: Tat/SPI and Tat/SPII

- **6-state:**  
  - `I`: Intracellular  
  - `M`: Membrane  
  - `O`: Extracellular  
  - `S`: Sec/SPI  
  - `L`: Sec/SPII  
  - `T`: Tat/SPI and Tat/SPII

---

## Model Versions

### 6-State Classifiers

- **v1:**  
  _Architecture:_ ProtBERT transformer + two sequential dense layers (256 neurons each)  
  _Description:_ Simple deep learning baseline using transformer embeddings and dense layers.  
  _Performance:_ Poor to moderate

- **v2:**  
  _Architecture:_ ProtBERT transformer + two CNN layers (1024 neurons each)  
  _Description:_ Adds convolutional layers to capture local sequence patterns.  
  _Performance:_ Experimental only

- **v3:**  
  _Architecture:_ ProtBERT transformer + one CNN layer (1024 neurons) + bidirectional LSTM (1024 neurons) + dense layer (2×512 neurons) + CRF  
  _Description:_ Combines CNN, LSTM, and CRF for sequence labeling.  
  _Performance:_ Moderate to good

- **v4:**  
  _Architecture:_ ProtBERT transformer + two CNN layers (1024 neurons each) + bidirectional LSTM (1024 neurons) + dense layer (2×512 neurons) + CRF  
  _Description:_ Deeper CNN-LSTM-CRF model, but unstable during training.  
  _Performance:_ Training interruptions, poor

- **v5 / v5_2:**  
  _Architecture:_ ProtBERT transformer + CNN layer (1024 neurons) + normalization + bidirectional LSTM (1024 neurons) + dense layer (2×512 neurons) + CRF  
  _Description:_ Best-performing deep model with normalization and CRF.  
  _Performance:_ Best

---

### 4-State Classifiers

- **v1:**  
  _Architecture:_ XGBoost (Gradient Boost) on ProtBERT transformer embeddings.  
  _Description:_ Uses transformer-based sequence embeddings as features for XGBoost.  
  _Performance:_ Very good, Accuracy: 98%

---

### 2-State Binary Classifiers

- **v1 (Logistic Regression):**  
  _Architecture:_ Logistic regression on one-hot encoded amino acid sequences.  
  _Description:_ Simple baseline for binary SP/Non-SP classification.  
  _Performance:_ Moderate, Accuracy: 96.8%

- **v2 (SVM)**
  _Architecture:_ SVM using one-hot encoded amino acid sequences  
  _Description:_ Support Vector Machine for binary SP/Non-SP classification.  
  _Performance:_ Moderate, Accuracy: 95.3%

- **v3 (Gradient Boosting):**  
  _Architecture:_ GradientBoostingClassifier on one-hot encoded amino acid sequences.  
  _Description:_ Basic gradient boosting for binary SP/Non-SP classification.  
  _Performance:_ Good, Accuracy: 97.7% 

- **v4 (XGBoost):**  
  _Architecture:_ XGBoost on one-hot encoded amino acid sequences.  
  _Description:_ XGBoost model for binary SP/Non-SP classification.  
  _Performance:_ Good, Accuracy: 97.7%

- **v5 (XGBoost/LightGBM):**  
  _Architecture:_ XGBoost and LightGBM with hyperparameter search on one-hot encoded sequences.  
  _Description:_ Uses random search for hyperparameter tuning on XGBoost model.  
  _Performance:_ Good, Accuracy: 97.4%

- **v6 (Transformer Embedding + XGBoost):**  
  _Architecture:_ XGBoost on ProtBERT transformer embeddings.  
  _Description:_ Uses transformer-based sequence embeddings as features for XGBoost.  
  _Performance:_ Very good, Accuracy: 99.4%
