# 🧠 Customer Churn Prediction — Hybrid Clustering + Classification

### 🎯 Objective
Build a **robust hybrid model** that segments customers by behavior using **K-Means clustering** and predicts churn using a **Gradient Boosting Classifier**.  
The goal is to identify and tag **At-Risk customers** based on churn probability and cluster-level behavior.

---

## 📊 Data Description
The dataset (`Final_Data.xlsx`) contains aggregated customer-level information such as:
- Total Transaction Amount  
- Total Transactions Count  
- Total Units Purchased  
- Average Days Between Purchases  
- Average Transaction Value  
- Tier Status & Trade Type

Each record represents a unique customer with transactional and behavioral details.

---

## ⚙️ Methodology

### Step 1️⃣ — Data Cleaning & Preprocessing
- Standardized column names, handled missing values.
- Encoded categorical variables using Label Encoding.
- Created a synthetic churn label where not explicitly available.

### Step 2️⃣ — Feature Engineering
- Derived behavioral indicators (recency, frequency, spend, purchase gaps).
- Scaled features using `StandardScaler`.

### Step 3️⃣ — Unsupervised Clustering
- Applied **K-Means** for segmentation.
- Used **Elbow** and **Silhouette** methods to determine the optimal cluster count.
- Visualized clusters using PCA for interpretability.

### Step 4️⃣ — Supervised Classification
- Trained **Gradient Boosting Classifier** to predict churn.
- Integrated cluster labels as an additional feature to enhance prediction accuracy.
- Evaluated model using:
  - Confusion Matrix (visual + text)
  - Classification Report
  - ROC-AUC Curve
  - Permutation Feature Importance

### Step 5️⃣ — Risk Tagging
- Computed churn probability for each customer.
- Combined model probabilities and cluster churn rates to create an `At_Risk` flag:
  - “Yes” → High churn probability or risky cluster.
  - “No” → Low probability or stable behavior.

---

## 📈 Results Summary

| Metric | Score |
|--------|-------|
| **Accuracy** | ~0.85–0.90 (realistic post-calibration) |
| **ROC-AUC** | ~0.87 |
| **Churn Distribution** | At_Risk: ~25–30% of total customers |

**Top Predictors:**
- Recency (Days Since Last Purchase)
- Average Days Between Purchases
- Total Transactions Count
- Average Transaction Value

**Key Clusters:**
- Cluster 0: High-value frequent buyers  
- Cluster 1: Inactive or dormant (high churn risk)  
- Cluster 2: Moderate spenders with steady frequency

---

## 📦 Output Files
- `Hybrid_Final_With_Risk.xlsx` → Includes:
  - `At_Risk` flag  
  - `Cluster_Label`  
  - `Churn_Probability`  
  - `Feature_Importance` & `Cluster_Churn_Rate` sheets  

---

## 🧩 Future Improvements
- Hyperparameter tuning (`GridSearchCV`)
- Calibrated probabilities (`CalibratedClassifierCV`)
- Time-based validation to simulate real churn prediction
- Integration with Power BI or Tableau for churn dashboards

---

## 🧑‍💻 Tech Stack
- **Python 3.10+**
- **Libraries:** pandas, numpy, scikit-learn, seaborn, matplotlib
- **Modeling:** K-Means, Gradient Boosting Classifier
- **Visualization:** Matplotlib, Seaborn

---

## 📚 How to Run
```bash
# Clone the repository
git clone https://github.com/<your-username>/Customer-Churn-Model.git
cd Customer-Churn-Model

# Install dependencies
pip install -r requirements.txt

# Open the notebook
jupyter notebook Customer_Churn_Model_Notebook.ipynb
