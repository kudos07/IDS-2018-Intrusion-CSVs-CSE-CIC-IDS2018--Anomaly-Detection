
# **README: Real-Time Anomaly Detection System (RADS)**

## **Project Overview**
The Real-Time Anomaly Detection System (RADS) is designed to enhance cloud data center security by detecting Distributed Denial of Service (DDoS) and cryptomining threats in real-time. It leverages machine learning models such as Isolation Forest and Autoencoders to identify anomalous patterns in resource usage and visualize them through an interactive dashboard.

---

## **Directory Structure**
```
/code_files/
  ├── file_1.py      # Script for data preprocessing and feature engineering.
  ├── file_2.py      # Script for model training and evaluation.
/data/
  ├── CICIDS2018.csv # Dataset used for anomaly detection (network intrusion data).
/outputfiles/
  ├── df_combined.csv  # Processed dataset after feature engineering.
  ├── metrics.json     # Performance metrics (Precision, Recall, F1-score).
  ├── model_artifacts/ # Saved models (Isolation Forest and Autoencoder).
/Tableau_Dashboard/
  ├── dashboard.twbx # Tableau file for interactive anomaly detection visualization.
```

---

## **Execution Steps**

### **Step 1: Prepare the Dataset**
1. Download `CICIDS2018.csv` and place it in the `/data/` directory.
2. Open `file_1.py` and run the following command:
   ```bash
   python file_1.py
   ```
   - **Functionality**:
     - Cleans the dataset (removes missing values).
     - Balances the dataset to address class imbalances using resampling.
     - Saves the processed dataset as `df_combined.csv` in the `/outputfiles/` directory.

### **Step 2: Run Model Training Script**
1. Open `file_2.py` and run:
   ```bash
   python file_2.py
   ```
   - **Functionality**:
     - Loads `df_combined.csv` and applies feature scaling using Z-score normalization.
     - Trains the Isolation Forest and Autoencoder models.
     - Saves performance metrics (Precision, Recall, F1-score) and model artifacts.

### **Step 3: Connect Tableau Dashboard**
1. Open `dashboard.twbx` in Tableau Desktop.
2. Connect it to the `outputfiles/` directory to load the latest model outputs.
3. **Visualizations**:
   - Anomaly trends over time.
   - Interactive confusion matrices and resource usage metrics.

---

## **Dependencies**
- Python 3.x
- Libraries:
  - `pandas`, `numpy`, `sklearn`, `matplotlib`
  - `tensorflow/keras` (for Autoencoder)
- Tableau Desktop (for visualization)

---

## **Methodology**

### **1. Data Preprocessing**
- **Normalization**: Z-score normalization.
- **Dimensionality Reduction**: PCA to retain informative components.
- **Handling Missing Values**: Removed missing entries due to minimal occurrence.

### **2. Model Selection**
- **Isolation Forest**: Tree-based anomaly detection that isolates anomalies based on statistical deviations.
  - Formula for anomaly score:
    \[
    s(x, n) = 2^{-\frac{h(x)}{c(n)}}
    \]
- **Autoencoder**: Neural network-based model that flags anomalies based on high reconstruction errors:
  \[
  \text{Error} = \|X - \hat{X}\|_2
  \]

### **3. Dashboard Development**
- **Features**:
  - Interactive anomaly visualization.
  - Real-time resource usage metrics (CPU, memory, network).
  - Configurable thresholds for anomaly detection.

---

## **Results**
- **Detection Accuracy**: 82% with reduced false positives.
- **Operational Efficiency**: Anomalies detected within seconds, meeting real-time requirements.
- **User Satisfaction**: Intuitive interface with real-time updates improved decision-making.

---

## **Challenges and Solutions**
- **Overfitting**: Mitigated using regularization (dropout, L2).
- **Scalability**: Optimized tree depth and learning rates for efficiency.
- **Data Imbalance**: Addressed through synthetic data augmentation and unsupervised learning.

---

## **Future Enhancements**
- **New Models**: Explore reinforcement learning and transformers for anomaly detection.
- **Explainability**: Incorporate Explainable AI (XAI) for improved transparency.
- **Integration**: Expand compatibility with major cloud platforms (AWS, GCP).

---

## **Work Distribution**
- **Saransh Surana**: Model development and hyperparameter tuning.
- **Vinay Ratnala**: Testing, evaluation, and documentation.
- **Y. Sri Datta**: Dashboard integration and scalability enhancements.

---

## **References**
1. "A Comprehensive Survey on Machine Learning for Networking" – IEEE Communications Surveys & Tutorials.
2. Tableau Dashboard Documentation – [Tableau Help](https://help.tableau.com/).
3. CICIDS2018 Dataset – [AWS Marketplace](https://aws.amazon.com/marketplace/).

---

This README file serves as a comprehensive guide to the RADS project, detailing its structure, methodology, and execution.
