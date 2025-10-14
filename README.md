# Signature-Anomaly Intrusion Detection

A Bimodal Framework of Calibrated and Explainable Machine Learning for Hybrid Signature-Anomaly Intrusion Detection
## What is IDS?
A security tool that monitors a network or system for malicious activity or policy violations and alerts administrators to potential threats. 
This project implements a hybrid intrusion detection system using the CIC-IDS2017 dataset that leverages:
•	Signature Detection: Multi-class classification for known attack types
•	Anomaly Detection: Binary classification to identify unknown threats
•	Model Calibration: Probability calibration for reliable confidence scores
•	Explainable AI: SHAP-based feature importance analysis
•	Open-Set Validation: Detection of previously unseen attack families


# Installation 
 ### Core data science libraries
pandas>=1.5.0
numpy>=1.21.0
scikit-learn>=1.0.0
matplotlib>=3.5.0
seaborn>=0.11.0

### Specialized libraries
imbalanced-learn>=0.9.0
shap>=0.41.0
Optional for advanced features
google-colab  # if running in Colab environment
### Quick Setup
pip install pandas numpy scikit-learn matplotlib seaborn imbalanced-learn shap

## Experimental steps 

Comprehensive step-by-step instructions are provided below for easy implementation.

### Dataset Preparation
  ## Dataset Preparation

- Monday-WorkingHours.pcap_ISCX.csv
- Tuesday-WorkingHours.pcap_ISCX.csv  
- Wednesday-WorkingHours.pcap_ISCX.csv
- Thursday-WorkingHours.pcap_ISCX.csv
- Friday-WorkingHours.pcap_ISCX.csv
- combined_dataset.csv (generated after processing)

This dual approach ensures robust evaluation:

- **Combined dataset** for comprehensive model training
- **Day-wise files** for realistic open-set validation and attack family isolation

The core pipeline can be run in the following sequence:
The core pipeline can be run in the following sequence:
1.	Open preprocessing_pipeline.py 
2.	The default settings are for processing the CIC-IDS2017 dataset. Users can change the input file path and output results path at:
                                   file_path = "/content/drive/My Drive/combined_dataset.csv"
  	                                Modify the path if your dataset is stored elsewhere
4.	If the user wants to process a different dataset format, modify the data loading and cleaning functions in the rigorous_clean() function starting at line 45.
5.	When running the preprocessing pipeline, the following outputs can be found in the terminal:
  o	Dataset shape and column information
  o	Data quality checks (missing values)
  o	Label distribution before and after processing
  o	Feature engineering summary
  o	Final dataset dimensions
6.	The preprocessing pipeline generates:
  o	X_train_processed.csv: Cleaned training features
  o	X_test_processed.csv: Cleaned test features
  o	y_train.csv: Training labels
  o	y_test.csv: Test labels
7.	For advanced feature engineering, run feature_engineering.py which creates security-focused features including:
  o	Flow duration conversions
  o	Packet rate calculations
  o	Protocol abnormality scores
  o	DDoS detection features
  o	TCP flag analysis

### Model Training
1.	Open model_training.py
2.	Choose mode:
  o	Anomaly Detection (Binary: BENIGN vs Attack)
  o	Signature Detection (Multi-class: Specific attack types)
3.	Models automatically save performance metrics and visualizations
# License

# Citation

Cite: 

