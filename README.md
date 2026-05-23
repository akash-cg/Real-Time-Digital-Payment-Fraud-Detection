# Real-Time-Digital-Payment-Fraud-Detection
This repository contains an end-to-end Machine Learning pipeline designed for real-time digital payment fraud detection. Built with Python, this project addresses the heavy class imbalance typical in fraud detection and utilizes custom feature engineering to assess transaction risk.

## Repository Structure

```text
Real-Time-Digital-Payment-Fraud-Detection/
│
├── dataset/
│   └── Time_fraud_detection.csv
│
├── results/
│   ├── confusion_matrix_logistic.png
│   ├── confusion_matrix_random_forest.png
│   ├── roc_curve.png
│   └── feature_importance.png
│
├── fraud_detection.ipynb
└── README.md

## Architecture & Workflow
1. **Data Ingestion:** Processes transactional records including timestamps, amounts, and categorical metadata.
2. **Feature Engineering:** Synthesizes multiple risk vectors into actionable features:
   - High Transaction Amount Flag: Transactions above the 95th percentile of transaction amount were flagged as high-value transactions
   - Night Transaction Flag: Transactions occurring between 10 PM and 5 AM were flagged as night transactions
   - Location Mismatch / Foreign IP Flag: Transactions were flagged as location-risk cases if they involved foreign transactions or high-risk countries
   - Unusual Transaction Frequency: Transactions from users with unusually high recent transaction counts were flagged based on the 95th percentile threshold 
   - **Composite Risk Score**: A custom risk score was created using weighted fraud-risk indicators such as high transaction amount, night transaction activity, location risk, unusual transaction frequency, and previous fraud count
3. **Data Preprocessing:** Standard scaling and stratified splitting to maintain the integrity of minority class representation.
4. **Modeling:** Implements baseline (Logistic Regression) and ensemble (Random Forest) models with balanced class weighting.
5. **Evaluation:** Since fraud detection is an imbalanced classification problem, accuracy alone is not sufficient. The models were evaluated using:
   - Precision
   - Recall
   - F1-score
   - ROC-AUC
   - Confusion Matrix
   Prioritizes Recall and ROC-AUC to minimize false negatives (undetected fraud).

## Tech Stack
* **Language:** Python
* **Libraries:** Pandas, NumPy, Scikit-Learn, Matplotlib, Seaborn
* **Environment:** VS Code

## Installation
1. Clone this repository.
2. Ensure you have the required libraries installed: `pip install pandas numpy scikit-learn matplotlib seaborn`
3. Place `Time_fraud_detection.csv` in the root directory.
4. Run the pipeline:
```bash
   python fraud_detection.py
