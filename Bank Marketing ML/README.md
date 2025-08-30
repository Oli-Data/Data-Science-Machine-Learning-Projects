# 🏦 Portuguese Bank Marketing – Machine Learning Project

This project analyzes the **Portuguese Bank Marketing dataset** to predict whether a client will subscribe to a term deposit.  
It applies different machine learning models, evaluates their performance, and identifies key features that influence client decisions.  

---

## 📊 Dataset
- **Source:** UCI Machine Learning Repository – [Bank Marketing Dataset](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing)  
- **Shape:** 41,188 records × 20 features  
- **Target Variable (`y`):** Whether the client subscribed to a term deposit (`yes` or `no`)  
- **Features include:**  
  - Client demographics (age, job, marital status, education)  
  - Contact information (communication type, campaign contact history)  
  - Socioeconomic attributes (employment variation rate, consumer price index, etc.)  

---

## 🚀 Project Workflow
1. **Data Preprocessing**
   - Cleaning and encoding categorical variables  
   - Handling class imbalance  
   - Normalization/standardization of numerical features  
2. **Model Training**
   - Logistic Regression  
   - Random Forest Classifier  
   - K-Nearest Neighbors (KNN)  
   - Artificial Neural Network (ANN)  
3. **Model Evaluation**
   - Accuracy  
   - Precision  
   - Recall  
   - F1-score  

---

## 📈 Results & Findings
- **Logistic Regression** performed well as a baseline model.  
- **Random Forest** provided strong overall performance with balanced precision and recall.  
- **KNN** struggled due to dataset size and dimensionality, making it less effective.  
- **ANN** achieved the **highest accuracy and recall**, outperforming 3 of the 4 traditional models.  
- In some cases, **Random Forest slightly outperformed ANN** depending on the performance metric.  
- Confusion matrices and performance breakdowns were visualized to support model evaluation.  

---

## ⚙️ Technologies Used
- **Python 3.x**  
- Jupyter Notebook / Google Colab  
- pandas, NumPy (data handling)  
- scikit-learn (ML models & evaluation)  
- TensorFlow / Keras (ANN)  
- matplotlib, seaborn (visualization)  

---

## 📌 Files
- `Portuguese Bank Marketing.ipynb` → main analysis & ML workflow  
- `bank-additional-full.csv` → dataset  

---

## 🔮 Next Steps
- Perform hyperparameter tuning for Random Forest and ANN  
- Explore feature selection to reduce dimensionality  
- Apply cross-validation for more robust evaluation  
- Extend analysis to compare model interpretability (feature importance vs ANN weights)  
