# Smart Integration of Industry 4.0 Technologies

### Streamlit Dashboard
🔗 https://smart-industry-4-0.streamlit.app/

---

## Overview

This project presents a diagnostic analytics system designed for machine health monitoring, production performance evaluation, quality diagnostics, and 6G network reliability assessment within smart manufacturing environments. The system combines data validation, exploratory data analysis, manufacturing KPI engineering, correlation diagnostics, and a Random Forest classifier to analyze machine performance and classify operational efficiency across a 50-machine industrial fleet.

The project was developed as an end-to-end Business Intelligence and Machine Learning solution focused on Industrial IoT analytics, 6G-enabled network diagnostics, and AI-powered manufacturing decision support.

---

## Project Structure

- `app.py` — Streamlit application entry point for dashboard and prediction interface.
- `Executive Summary.docx` — Executive summary report for stakeholders.
- `Manufacturing_Cleaned_Dataset.csv` — Cleaned dataset used for model training and analysis.
- `manufacturing_random_forest_model.pkl` — Serialized Random Forest model for inference.
- `requirements.txt` — Python dependencies required to run the project.
- `Ishaanindustry4.0.ipynb` — Exploratory analysis notebook with visualizations and modeling steps.
- `Ishaanindustry4.0.csv` — Original manufacturing dataset used for data preparation.

---

## Objectives

- Analyze machine-level operational performance using business intelligence analytics
- Evaluate sensor, production, quality, and network telemetry across a 50-machine fleet
- Identify high-efficiency and low-efficiency machine operating patterns
- Analyze operational KPI structures and predictive maintenance risk
- Quantify the correlation structure among manufacturing variables and assess multicollinearity risk
- Predict machine operational efficiency using machine learning models
- Build an AI-driven manufacturing intelligence framework
- Develop an interactive Streamlit dashboard for visualization and live prediction

---

## Dataset Information

A smart manufacturing telemetry dataset containing operational records across many machines was used to capture:

- Machine sensor behaviour (temperature, vibration, power consumption)
- 6G network performance (latency, packet loss)
- Production throughput patterns
- Quality-control defect and error behaviour
- Predictive maintenance risk scoring
- Efficiency distribution across operating conditions
- Operation-mode dependent behaviour (Active / Idle / Maintenance)
- Three-month longitudinal telemetry dynamics

The dataset includes operational and sensor information from a simulated industrial environment spanning:

- Active Production Operation
- Idle Operation
- Scheduled Maintenance

The project focuses on understanding how sensor conditions, network reliability, production throughput, and quality outcomes jointly influence machine efficiency and operational sustainability.

---

## Technologies Used

### Programming Language

- Python

### Libraries & Frameworks

- Pandas
- NumPy
- Scikit-learn
- Plotly
- Streamlit
- Joblib

---

## Exploratory Data Analysis (EDA)

The project includes detailed EDA involving:

- Sensor distribution analysis
- Efficiency status distribution analysis
- Operation-mode distribution analysis
- Machine-level sensor comparison
- Production speed and consistency analysis
- Defect rate and error rate analysis
- Network latency and packet-loss analysis
- Correlation heatmaps
- Outlier detection via IQR
- Machine-level performance distribution analysis

---

## Feature Engineering

Several engineered KPIs were created, including:

- MachineHealthIndex
- DefectDensityScore
- ErrorFrequencyIndex
- AverageNetworkLatency
- AveragePacketLoss

These engineered indicators improved machine profiling and supported executive-level reporting.

---

## Correlation & Multicollinearity Diagnostics

### Method Used

- Pearson Correlation Analysis
- Correlation Heatmaps
- Interactive Pair Plots

### Evaluation Findings

- Nearly all manufacturing variable pairs exhibit near-zero linear correlation (|r| < 0.02)
- The only moderate relationship observed is between Day and Month (r = −0.37), a calendar artifact rather than an operational relationship
- No multicollinearity risk was identified prior to modeling

### Key Implication

The near-total linear independence among sensor, production, quality, and network variables indicates that machine efficiency cannot be reliably inferred from any single telemetry channel, reinforcing the need for multivariate, model-based classification.

---

## Machine Learning Model Evaluated

| Model | Accuracy (Test Set) | 5-Fold CV Accuracy |
|---|---|---|
| Random Forest | 99.995% (19,999 / 20,000) | 99.991% ± 0.004% |

---

## Best Performing Model

### Random Forest Classifier

- **Test Accuracy**: 99.995% (rounds to 100.00% at two decimal places)
- **5-Fold Cross-Validation Accuracy**: 99.991% ± 0.004%
- **Weighted F1 Score**: 0.99995
- **Macro F1 Score**: 0.99968
- **Decision Boundary Alignment**: The ground-truth operational efficiency categories in the manufacturing simulation follow axis-aligned threshold boundaries governed predominantly by `Production_Speed` and `Error_Rate` (>96% cumulative feature importance). Decision tree ensembles natively split along orthogonal axes, allowing Random Forest to resolve the operational regimes without linear boundary distortion.
- **Data Validation & Integrity**: Zero data leakage, zero duplicate records, and rigorous stratified train/test partitioning (80,000 train / 20,000 test).
- **High Reliability**: Outstanding precision, recall, and F1 across both dominant (`Low`) and minority (`High`, `Medium`) classes.

| Class | Precision | Recall | F1 | Support |
|---|---|---|---|---|
| High | 1.0000 | 0.9983 | 0.9992 | 597 |
| Medium | 0.9997 | 1.0000 | 0.9999 | 3,838 |
| Low | 1.0000 | 1.0000 | 1.0000 | 15,565 |
| **Weighted Avg** | **0.9999** | **0.9999** | **0.9999** | **20,000** |

---

## Efficiency Prediction System

The prediction framework uses:

- Random Forest Classifier
- Feature-engineered machine telemetry profiles
- Standardized sensor, production, quality, and network features
- Manufacturing KPI engine outputs
- Live, filter-aware model inference

The system predicts:

- Efficiency status category (High / Medium / Low)
- Class-probability distribution
- Machines approaching degraded operational thresholds
- Network and sensor-driven efficiency risk

---

## Streamlit Dashboard Features

The project includes an interactive Streamlit dashboard with:

- Executive Overview Dashboard
- Machine Health Monitoring
- Production Performance Analytics
- Quality Diagnostics
- 6G Network Performance Diagnostics
- Cross-Metric Correlation Analysis
- AI-Powered Efficiency Prediction Center
- Interactive KPI Dashboard
- Executive Business Intelligence Report
- Live Confusion Matrix on Filtered Data

---

## Key Performance Indicators (KPIs)

- Machine Health Index
- Average Production Speed
- Average Temperature
- Average Vibration
- Average Power Consumption
- Predictive Maintenance Score
- Defect Density Score
- Error Frequency Index
- Average Network Latency
- Average Packet Loss
- Factory-Wide Efficiency Mix

---

## Project Structure

```text
Smart-Integration-of-Industry-4.0-Technologies/
│
├── manufacturing_random_forest_model.pkl
├── app.py
├── Industry4.0.csv
├── Industry4.0.ipynb
├── Manufacturing_Cleaned_Dataset.csv
├── Executive_Summary.docx
├── README.md
└── requirements.txt
```

---

## Running the Project

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Run Streamlit Dashboard

```bash
streamlit run app.py
```

---

## Research & Academic Notes

- The dataset used in this project contains structured manufacturing sensor, production, quality, and network telemetry.
- Results were evaluated within the available operational and efficiency feature space.
- Correlation diagnostics confirm near-total feature independence, supporting the use of multivariate classification over univariate threshold alarms.
- Machine learning performance depends on class-imbalance-aware evaluation, given the 77.8% / 19.2% / 3.0% Low/Medium/High distribution.
- This work is intended as an educational, research-oriented, and industrial analytics implementation project.

---

## Future Improvements

- Comparative ensemble modeling (Random Forest, XGBoost, LightGBM)
- Class-imbalance mitigation (class-weighted loss, SMOTE, threshold calibration)
- Real plant-floor dataset validation
- SHAP-based explainability analysis
- Temporal / streaming analytics pipeline
- Live operational monitoring system
- Cloud-based deployment architecture
- Unsupervised anomaly-detection layer
- Predictive-maintenance-integrated alerting
- Edge AI integration

---

## Authors

- Ishaan Verma
- Kirti Yadav

---

## Acknowledgement

This project was developed as part of advanced Business Intelligence, Data Science, and Machine Learning research focused on 6G-enabled smart manufacturing analytics and operational efficiency classification.

---

## License

This project is released under MIT License.
