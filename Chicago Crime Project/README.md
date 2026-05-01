# 🕵️ Chicago Crimes Analysis & Prediction
### A CO³ Labs Study | Christian Olivares-Rodriguez

---

## 📌 Overview
This project analyzes the Chicago Crimes dataset (2001–Present) to uncover patterns 
in criminal activity and build a deep learning model to predict arrest likelihood.

The project is split into two phases:

1. **Phase 1 — Exploratory Analysis:** Trends in crime across time, location, type, 
   and arrest rates using interactive visualizations.
2. **Phase 2 — Arrest Prediction:** A PyTorch neural network trained on 192,082 
   records to predict whether an arrest will be made given crime type, location, 
   time of day, and other contextual features.

---

## 📊 Dataset
Chicago Crimes dataset containing reported incidents from 2001 to present.

| Feature | Description |
|---------|-------------|
| Date, Year | Temporal features |
| Latitude, Longitude, District, Community Area | Spatial features |
| Primary Type, FBI Code, IUCR | Crime category identifiers |
| Arrest, Domestic | Classification targets |

*Source: [Chicago Data Portal](https://data.cityofchicago.org/d/ijzp-q8t2)*

---

## 🧠 Phase 2 — PyTorch Model Results

| Metric | No Arrest | Arrest |
|--------|-----------|--------|
| Precision | 0.87 | 0.78 |
| Recall | 0.94 | 0.59 |
| F1-Score | 0.91 | 0.67 |

**Overall Accuracy: 86%** on 38,417 held-out test records.

### Model Architecture
- 4-layer fully connected neural network (128 → 64 → 32 → 1)
- Batch normalization and dropout (0.3) for regularization
- WeightedRandomSampler to handle 75/25 class imbalance
- Optimizer: Adam (lr=0.001) | Loss: BCE | Epochs: 20 | Batch size: 512

---

## 🛠️ Tech Stack
| Tool | Purpose |
|------|---------|
| Python | Core language |
| Pandas | Data cleaning and manipulation |
| PyTorch | Neural network training |
| Scikit-Learn | Train/test split, scaling, evaluation metrics |
| Plotly | Interactive maps and visualizations |
| Matplotlib / Seaborn | Charts and confusion matrix |

---

## 📁 How to Run
1. Download the dataset from the [Chicago Data Portal](https://data.cityofchicago.org/d/ijzp-q8t2)
2. Place the CSV in your project directory
3. Open `Chicago_Crimes_Project.ipynb` and run cells top to bottom
4. Phase 1 runs on the full dataset; Phase 2 builds and trains the PyTorch model
