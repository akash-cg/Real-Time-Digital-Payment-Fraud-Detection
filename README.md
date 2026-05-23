# Real-Time-Digital-Payment-Fraud-Detection
This repository contains an end-to-end Machine Learning pipeline designed for real-time digital payment fraud detection. Built with Python, this project addresses the heavy class imbalance typical in fraud detection and utilizes custom feature engineering to assess transaction risk.

## Architecture & Workflow
1. **Data Ingestion:** Processes transactional records including timestamps, amounts, and categorical metadata.
2. **Feature Engineering:** Synthesizes multiple risk vectors into actionable features:
   - High Transaction Amount Flag
   - Night Transaction Flag
   - Location Mismatch / Foreign IP Flag
   - Unusual Transaction Frequency 
   - **Composite Risk Score**
3. **Data Preprocessing:** Standard scaling and stratified splitting to maintain the integrity of minority class representation.
4. **Modeling:** Implements baseline (Logistic Regression) and ensemble (Random Forest) models with balanced class weighting.
5. **Evaluation:** Prioritizes Recall and ROC-AUC to minimize false negatives (undetected fraud).

## Tech Stack
* **Language:** Python
* **Libraries:** Pandas, NumPy, Scikit-Learn, Matplotlib, Seaborn
* **Environment:** VS Code

## Quick Start
1. Clone this repository.
2. Ensure you have the required libraries installed: `pip install pandas numpy scikit-learn matplotlib seaborn`
3. Place `Time_fraud_detection.csv` in the root directory.
4. Run the pipeline:
```bash
   python fraud_detection.py
