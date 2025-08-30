# 💧 County Water Withdrawals — Data Gathering, Transformation & Basic Models (HW1)

This project builds a **county-level dataset** for the contiguous United States and trains **baseline regression models** to predict **public + domestic self-supplied water withdrawals (2015)**.  
It covers **geospatial joins**, **multi-source data merging**, **feature engineering**, and **scikit-learn pipelines** with a **train/test split stratified by Census Division**.

---

## 📦 Project Contents
- `HW1.ipynb` — end-to-end notebook (data assembly, EDA, feature pipelines, models)
- (Data files provided alongside the assignment; see sources below)

---

## 🗺️ Data Sources (2015)
- **County geometries & FIPS** — contiguous US counties (GeoDataFrame used throughout)
- **Census Division codes** — used for **stratified** train/test split
- **NOAA Climate at a Glance** — county-level **average temperature** & **precipitation**
- **USGS Water Use** — `PS-Wtotl` (Public Supply total) + `DO-WFrTo` (Domestic, self-supplied from fresh surface/groundwater)  
  → summed into **`Water`**, with **`log_Water`** as the modeling target
- **BEA county demographics/income** — population and (per-capita) income features

> The notebook merges these into a single county-level dataframe keyed by **FIPS**.

---

## 🔁 Workflow
1. **Load & plot county shapefiles** → construct `gdf` (GeoDataFrame)  
2. **Merge Census Division codes**  
3. **Add NOAA climate features** (avg temp & precip; ensure consistent FIPS keys)  
4. **Merge USGS water withdrawals** → create `Water = PS-Wtotl + DO-WFrTo`; drop `Water <= 0`; add `log_Water`  
5. **Add BEA demographics/income** (population, income)  
6. **Explore distributions** (quick sanity checks/plots)  
7. **Train/test split** **stratified by Census Division**  
8. **Feature pipelines**  
   - Numeric: impute → scale  
   - Categorical (if present): impute → encode  
   - Combine with **`ColumnTransformer`**  
9. **Train candidate models** (baseline regressors)  
10. **Evaluate on test set** (e.g., **R²**) and visualize predictions

---

## 🧠 Target & Features
- **Target:** `log_Water` (natural log of county-level `Water`)  
- **Feature families:** climate (temp/precip), population, income, region/division, and other derived fields

---

## 🧪 Models
Baseline regressors trained via scikit-learn with the shared preprocessing pipeline:
- **Linear Regression**
- **Random Forest Regressor**
- (Optional extensions: Ridge/Lasso, KNN, Gradient Boosting)

> Performance is reported in the notebook (e.g., **R² on the held-out test set**), along with a prediction vs. truth plot.

---

## 🛠️ Tech Stack
- **Python 3.x**
- **pandas**, **NumPy**
- **GeoPandas**
- **scikit-learn** (pipelines, ColumnTransformer, models, metrics)
- **matplotlib** (visualization)

---

## ▶️ How to Run
1. Create/activate a virtual environment (optional but recommended)
2. Install dependencies:
   ```bash
   pip install pandas numpy geopandas scikit-learn matplotlib
