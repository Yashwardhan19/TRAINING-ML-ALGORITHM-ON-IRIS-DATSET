#  Iris Species Classification

ML project — classifying Iris flowers into 3 species using machine learning.

---

##  Dataset

- **Source:** Iris Dataset (`Iris.csv`)
- **Samples:** 150 (50 per class)
- **Features:** 4
  - SepalLengthCm
  - SepalWidthCm
  - PetalLengthCm
  - PetalWidthCm
- **Target:** Species (Iris-setosa, Iris-versicolor, Iris-virginica)

---

##  Project Flow

```
Data Loading → EDA → Preprocessing → Model Training → Cross Validation → Best Model → Evaluation
```

---

##  Exploratory Data Analysis (EDA)

- Pie chart — class distribution (balanced dataset, 33% each)
- Histograms — feature distributions per species
- Scatter plot — Petal Length vs Petal Width
- Box plots — feature comparison per species
- Pair plot — all features vs all features
- Correlation heatmap — feature relationships

---

##  Preprocessing

- Dropped `Id` column
- Checked null values — none found
- Stratified Train/Test Split: **80% train / 20% test** (`random_state=42`)
- Applied `StandardScaler` for KNN and SVM via **Pipeline** (prevents data leakage)

---

##  Models Trained

| Model | CV Accuracy | Std |
|---|---|---|
| Decision Tree | 94.17% | ±2.04% |
| Random Forest | 95.00% | ±1.67% |
| Logistic Regression | **96.67%** | **±1.67%** ✅ |
| KNN | 96.67% | ±3.12% |
| SVM | 96.67% | ±3.12% |

> Cross Validation: 5-Fold CV on training data only

---

##  Best Model — Logistic Regression

Chosen because:
- Highest CV accuracy (96.67%)
- Lowest standard deviation (±1.67%) — most consistent model
- Simpler model preferred when accuracy is equal

---

##  Final Evaluation on Test Data

```
                    precision  recall  f1-score  support

       Iris-setosa       1.00    1.00      1.00       10
   Iris-versicolor       1.00    0.90      0.95       10
    Iris-virginica       0.91    1.00      0.95       10

          accuracy                         0.97       30
```

**Test Accuracy: 97%** — only 1 misclassification out of 30 samples.

---

##  Confusion Matrix

```
              Predicted
              Set  Ver  Vir
Actual Setosa  10    0    0   ✅
    Versicolor   0    9    1   ❌ (1 misclassified as Virginica)
     Virginica   0    0   10   ✅
```

> Versicolor and Virginica are naturally similar species — 1 mistake is expected.

---

##  Feature Importance (Random Forest)

| Feature | Importance |
|---|---|
| PetalLengthCm | 0.46 ⭐ Most Important |
| PetalWidthCm | 0.42 |
| SepalLengthCm | 0.11 |
| SepalWidthCm | 0.02 |

> Petal features are far more useful than Sepal features for classification.

---

##  Libraries Used

- `pandas` — data loading and manipulation
- `matplotlib` & `seaborn` — visualization
- `scikit-learn` — model training, evaluation, cross validation, pipeline

---

##  Files

```
├── training.ipynb       # Main notebook
├── Iris.csv             # Dataset
├── Plots                # EDA Plots
└── README.md            # This file
```

---

## 🚀 How to Run

```bash
pip install pandas matplotlib seaborn scikit-learn
jupyter notebook training.ipynb
```

---
 Iris Classification | scikit-learn*