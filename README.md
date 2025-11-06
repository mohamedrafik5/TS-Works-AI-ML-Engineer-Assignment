🧠 Time Series Anomaly Detection for IoT Sensors
📌 Overview

This project detects anomalies in IoT sensor data using the NASA Bearing Dataset
 — a well-known benchmark dataset for predictive maintenance and machine health monitoring.

Two complementary approaches are implemented:

🌲 Isolation Forest — a statistical unsupervised method for detecting point anomalies.

🤖 LSTM Autoencoder — a deep learning model that learns normal vibration sequences and flags abnormal reconstruction patterns.

Both methods help identify unusual vibration behavior that may indicate bearing wear, imbalance, or equipment failure.

⚙️ Requirements

Make sure you have the following libraries installed:

pip install numpy pandas matplotlib seaborn scikit-learn tensorflow

🚀 How to Run the Code

Download the Dataset

Download the NASA Bearing Dataset
.

Extract it and place all data files inside:

D:/ts work assignment/Dataset/


Open the Notebook

Open model.ipynb in Jupyter Notebook or VS Code.

Run All Cells Sequentially

Execute each cell in order (Shift + Enter).

The notebook will automatically:

Load and clean the NASA dataset

Handle missing values and outliers

Generate rolling statistical features

Train Isolation Forest and LSTM Autoencoder models

Visualize anomalies detected by both methods

View Results

Detected anomalies are shown as orange (Isolation Forest) and red (LSTM) points on the sensor signal timeline.

The final comparison plot shows how both methods detect different types of irregularities.

📊 Outputs

EDA plots showing trends and sensor correlations

Isolation Forest anomalies (orange points)

LSTM Autoencoder anomalies (red points)

Combined anomaly comparison plot

🧩 Notes

This is a fully unsupervised pipeline — no labeled anomalies are required.

Model validation is based on visual inspection and domain reasoning typical of industrial IoT systems.

The project demonstrates a complete predictive maintenance workflow using the NASA Bearing dataset.

Author: Mohamed Rafik A
Email: mohameedrafik.a@gmail.com

Role: AI/ML Engineer (Fresher)
