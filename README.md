# 🛠️ Bearing Vibration Anomaly Detection (NASA IMS Dataset)

This project uses **unsupervised learning** to detect anomalies in industrial vibration data using:

- **Isolation Forest (Statistical Method)**
- **LSTM Autoencoder (Deep Learning Method)**

Both methods are applied to the [NASA IMS Bearing Dataset (Kaggle)](https://www.kaggle.com/datasets/vinayak123tyagi/bearing-dataset).



---

## 📁 1. Dataset Summary
- Each file contains **1 second** of vibration data.
- **8 sensor channels**, each with **20,480 samples**.
- Filenames encode timestamps:  
  `YYYY.MM.DD.HH.MM.SS`

---

## 🧹 2. Data Preprocessing

### ✔ Mean Absolute Value Extraction
Each file is compressed into 8 features by computing the **mean absolute value (MAV)** per sensor.

### ✔ Missing Value Handling
Performed using:
- `interpolate(method="time")`
- Backward fill (`bfill`)
- Forward fill (`ffill`)

### ✔ Outlier Cleaning (Z-score + Winsorization)
- Outliers detected using `|z| > 4`
- Winsorized using 0.1% and 99.9% percentiles
- Interpolated to maintain continuity
- Produces `Sensor_1_clean`

---

## 📊 3. Exploratory Visualization

### ✔ Sensor Trend Plot
Shows raw signal + rolling mean to highlight vibration drift.

### ✔ Correlation Heatmap
Displays relationships among all 8 sensors.

---

## 🧾 4. Multi-Sensor Feature Engineering
For all 8 sensors, rolling features are extracted:

- RMS  
- Rolling Standard Deviation  
- Rolling Kurtosis  

Features are standardized using `StandardScaler`.

---

## 🔧 5. Isolation Forest (Approach 1)

### ✔ Hyperparameter Tuning
Grid search over:
- `n_estimators`: 200, 300, 400  
- `contamination`: 0.01, 0.02, 0.05  

Best model chosen by **highest anomaly-score variance**.

### ✔ Anomaly Detection
- Labels: `1 = normal`, `-1 = anomaly`
- Scores and labels added back to timeline  
- Anomalies visualized with **red markers**

---

## 🤖 6. LSTM Autoencoder (Approach 2)

### ✔ Sequence Preparation
- Sensor_1_clean converted into sequences of 30 timesteps  
- Input shape: `(samples, 30, 1)`

### ✔ Model Architecture
- Encoder LSTM (64 units)  
- RepeatVector  
- Decoder LSTM  
- TimeDistributed output layer  

### ✔ Training
- 15 epochs  
- Batch size 32  
- EarlyStopping used for stability

### ✔ Evaluation
- Reconstruction error (MSE) computed  
- Threshold = mean + 3 × std  
- Anomalies plotted on timeline

---

## 🧠 7. Unsupervised Model Evaluation
Both models are compared visually:

- **Isolation Forest (orange)** → detects abrupt spikes  
- **LSTM Autoencoder (red)** → detects gradual pattern drifts  
- Overlapping anomalies indicate high-confidence events

This qualitative approach is used because the dataset has **no labeled anomalies**.

---

## 📦 8. Technologies Used
- Python  
- Pandas / NumPy  
- SciPy  
- Scikit-learn  
- TensorFlow / Keras  
- Matplotlib / Seaborn  

---

## ✅ 9. Conclusion
This project demonstrates a complete **unsupervised anomaly detection pipeline** for machine vibration data.  
Isolation Forest captures short-term outliers, while the LSTM Autoencoder captures long-term temporal deviations.  
Together, they provide a robust approach for real-world predictive maintenance.

Name: Mohamed Rafik A

Mail Id: mohameedrafik.a@gmail.com
