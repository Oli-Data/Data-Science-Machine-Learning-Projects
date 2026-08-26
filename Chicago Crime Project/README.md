
Chicago readme · MD
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
> **Note:** Both phases below were run against a random 2.5% sample of the full 
> dataset (192,082 of ~8M+ total records), not the complete historical archive. 
> See "How to Run" for how to switch to the full dataset.
 
---
 
## 📊 Dataset
 
Chicago Crimes dataset containing reported incidents from 2001 to present.
 
| Feature | Description |
|---------|-------------|
| Date, Year | Temporal features |
| Latitude, Longitude, District, Beat, Community Area | Spatial features |
| Primary Type, FBI Code, IUCR | Crime category identifiers |
| Domestic | Contextual binary feature (used as a model input, not a prediction target) |
| Arrest | Classification target |
 
*Source: [Chicago Data Portal](https://data.cityofchicago.org/d/ijzp-q8t2)*
 
---
 
## 🧠 Phase 2 — PyTorch Model Results
 
| Metric | No Arrest | Arrest |
|--------|-----------|--------|
| Precision | 0.87 | 0.78 |
| Recall | 0.94 | 0.59 |
| F1-Score | 0.91 | 0.67 |
 
**Overall Accuracy: 86%** on 38,417 held-out test records.
 
Worth noting: the dataset is 75% "no arrest" to begin with, so a model that always 
guessed "no arrest" would already score 75% accuracy. The more meaningful numbers 
are the 0.59 arrest recall and 0.78 arrest precision, which show the model is 
picking up real signal on the minority class rather than just riding the imbalance.
 
### Model Architecture
- Input: 60-feature matrix (one-hot encoded crime type + district, plus Beat, 
  Community Area, Hour, and Domestic)
- 4-layer fully connected neural network (60 → 128 → 64 → 32 → 1)
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
| Plotly | Interactive scatter map and crime-type filtering |
| Folium | Interactive geographic heatmaps (static and time-animated) |
| Matplotlib / Seaborn | Charts and confusion matrix |
 
---
 
## 📁 How to Run
 
1. Download the dataset from the [Chicago Data Portal](https://data.cityofchicago.org/d/ijzp-q8t2) 
   — either the full historical export, or use the notebook's own small-sample 
   generator (see the "(Optional) How the smaller CSV was created" cell) to build 
   a lighter 2.5% random sample for faster prototyping.
2. Update the `data_path` in the data-loading cell to point at wherever you saved 
   the CSV — it's currently hardcoded to the author's local folder structure 
   (`~/Data Sci/Projects/Python/Chicago Crimes/CSV/`) and will need to match your 
   own machine before it runs.
3. Open `Chicago_Crimes_Project.ipynb` and run cells top to bottom. The data-loading 
   cell will prompt you in the terminal/output area to type **`small`** or **`large`** 
   — small loads the 2.5% sample (~210K rows, faster, used to produce the results 
   and charts documented in this README); large loads the full 8M+ row dataset.
4. Both Phase 1 (exploratory charts and maps) and Phase 2 (the PyTorch model) run 
   on whichever dataset size you chose in step 3.
