# Signal Peptide Prediction using Machine Learning

## Overview

This project focuses on the classification of amino acid sequences into signal peptide (SP) and non-signal peptide (Non-SP) categories using various machine learning models.

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
  ProtBERT transformer + two sequential dense layers (256 neurons each)  
  _Performance:_ Poor to moderate

- **v2:**  
  ProtBERT transformer + two CNN layers (1024 neurons each)  
  _Performance:_ Experimental only

- **v3:**  
  ProtBERT transformer + one CNN layer (1024 neurons) + bidirectional LSTM (1024 neurons) + dense layer (2×512 neurons) + CRF  
  _Performance:_ Moderate to good performance

- **v4:**  
  ProtBERT transformer + two CNN layers (1024 neurons each) + bidirectional LSTM (1024 neurons) + dense layer (2×512 neurons) + CRF  
  _Performance:_ Training interruptions, poor

- **v5 / v5_2:**  
  ProtBERT transformer + CNN layer (1024 neurons) + normalization + bidirectional LSTM (1024 neurons) + dense layer (2×512 neurons) + CRF  
  _Performance:_ Best

---

### 2-State Binary Classifiers

- **v1:**  
  Logistic regression on one-hot encoded amino acid sequences  
  _Performance:_ Very good


