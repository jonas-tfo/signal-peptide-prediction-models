# Signal Peptide Prediction using machine learning

### Task 
- 6-state prediction of amino acid labels, namely (I: intracellular, M: membrane, O: extracellular, S: Sec/SPI, L: Sec/SPII, T: Tat/SPI and Tat/SPII)
  
**v1**: prot_bert transformer + two sequential dense layers (256 neurons each) -> poor to moderate performance  
**v2**: prot_bert transformer + two CNN layers (1024 neurons each) -> only experimental  
**v3**: prot_bert transformer + one CNN layer (1024 neurons) + bidirectional LSTM (1024 neurons) + dense layer (512*2 neurons) + CRF -> good performance  
**v4**: prot_bert transformer + two CNN layers (1024 neurons each) + bidirectional LSTM (1024 neurons) + dense layer (512*2 neurons) + CRF -> training interruptions, poor performance  
**v5** + continuation: prot_bert transformer + CNN layer (1024 neurons) + Normalization + bidirectional LSTM (1024 neurons) + dense layer (512*2 neurons) + CRF -> best performance  
