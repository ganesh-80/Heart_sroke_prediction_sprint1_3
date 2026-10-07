# 🧠 Stroke Prediction Analytics

A three-sprint data analytics project that cleans, explores, and statistically analyzes a healthcare dataset to identify patient characteristics and health factors associated with stroke.

> **Note:** All findings describe *observed associations in this dataset*. They are not medical diagnoses or proof of causation.

---

## 📌 Project Overview

| Item | Details |
|---|---|
| **Business problem** | Identify patient characteristics and health factors associated with stroke occurrence |
| **Target variable** | `stroke` (0 = No stroke, 1 = Stroke) |
| **Records** | 5,110 patients |
| **Features** | 12 columns (demographic, health, and lifestyle) |
| **Class balance** | 249 stroke cases (4.87%) vs 4,861 non-stroke (95.13%) — highly imbalanced |
| **Tools** | Python, Pandas, NumPy, Matplotlib, Seaborn, SciPy, Google Colab |

---

## 📂 Repository Structure

```
Heart_stroke_prediction_sprint1_3/
│
├── healthcare-dataset-stroke-data.csv                 # Raw dataset
├── cleaned healthcare_dataset                         # Cleaned dataset (Sprint 1 output)
│
├── Sprint (1).ipynb                                   # Sprint 1 – Data understanding & cleaning
├── Sprint_(2).ipynb                                   # Sprint 2 – EDA & visualization
├── Sprint_3_based_Ap.ipynb                            # Sprint 3 – Statistics & feature engineering
│
├── Stroke_Sprint_1_doc.docx                           # Sprint 1 documentation
├── Sprint_2_StrokePredection_doc.pdf                  # Sprint 2 documentation
└── Sprint_3_Documentation_Stroke_Analytics.pdf        # Sprint 3 documentation
```

---

## 📊 Dataset Description

| Column | Description |
|---|---|
| `id` | Unique patient identifier |
| `gender` | Male / Female / Other |
| `age` | Age of the patient |
| `hypertension` | 0 = No, 1 = Yes |
| `heart_disease` | 0 = No, 1 = Yes |
| `ever_married` | Yes / No |
| `work_type` | Private, Self-employed, Govt_job, children, Never_worked |
| `Residence_type` | Urban / Rural |
| `avg_glucose_level` | Average blood glucose level |
| `bmi` | Body Mass Index |
| `smoking_status` | formerly smoked, never smoked, smokes, Unknown |
| `stroke` | **Target** – 1 if the patient had a stroke, else 0 |

---

## 🚀 Sprint Breakdown

### Sprint 1 — Data Understanding & Cleaning
- Explored dataset shape, data types, and summary statistics
- Found **201 missing values in `bmi`** and imputed them using the mean
- Verified no duplicate records and no invalid binary values
- Checked categorical columns for inconsistencies
- Performed **outlier analysis** using the IQR method and box plots
- Retained outliers in glucose and BMI, as they may reflect genuine patient conditions
- Exported the cleaned dataset

### Sprint 2 — Exploratory Data Analysis & Visualization
- Descriptive statistics: central tendency, dispersion, skewness
- Univariate analysis: histograms, box plots, categorical frequencies, target distribution
- Bivariate analysis: correlations, scatter plots, group comparisons by stroke outcome
- Group analysis by age group, smoking status, hypertension, and heart disease
- Business storytelling around observed risk patterns

### Sprint 3 — Advanced Statistics & Feature Engineering
- **Statistical analysis:** mean, median, mode, variance, standard deviation, skewness, kurtosis, correlation, covariance
- **Hypothesis testing** (α = 0.05):
  - T-test: age vs stroke
  - Chi-square test: hypertension vs stroke
  - ANOVA: age across work types
- **95% confidence intervals** for age, glucose level, and BMI
- **Feature engineering** with justification and evaluation for each feature
- Final business recommendations

---

## 🔍 Key Findings

**Correlation with stroke**

| Variable | Correlation |
|---|---|
| Age | 0.245 |
| Heart disease | 0.135 |
| Avg. glucose level | 0.132 |
| Hypertension | 0.128 |
| BMI | 0.036 |

**Hypothesis tests**

| Test | Result | Decision |
|---|---|---|
| T-test (age vs stroke) | t = 29.69, p ≈ 2.1 × 10⁻⁹⁵ | Reject H₀ |
| Chi-square (hypertension vs stroke) | χ² = 81.61, p ≈ 1.7 × 10⁻¹⁹ | Reject H₀ |
| ANOVA (age vs work type) | F = 1110.09, p ≈ 0 | Reject H₀ |

**Observed stroke rate by group**

| Age Group | Stroke Rate |
|---|---|
| Young (<18) | 0.23% |
| Adult (18–39) | 0.46% |
| Middle Age (40–59) | 3.84% |
| Senior (60+) | 13.15% |

| Disease Status | Stroke Rate |
|---|---|
| No disease | 3.39% |
| One condition | 13.47% |
| Both conditions | 20.31% |

| Glucose Category | Stroke Rate |
|---|---|
| Low / Normal / High | ~3.6–3.7% |
| Very High | 10.19% |

**Takeaways**
- Age is the strongest numerical factor associated with stroke.
- Having hypertension and/or heart disease sharply increases the observed stroke rate.
- Very high glucose levels show a notably higher stroke rate.
- BMI has only a weak relationship with stroke in this dataset.

---

## 🛠️ Engineered Features

| Feature | Description |
|---|---|
| `age_group` | Young, Adult, Middle_Age, Senior |
| `bmi_category` | Underweight, Normal, Overweight, Obese |
| `glucose_category` | Low, Normal, High, Very_High |
| `combined_disease_indicator` | Sum of hypertension + heart disease |
| `disease_status` | No Disease / One Condition / Both Conditions |
| `health_score` | Simple count of hypertension and heart disease indicators (not a clinical score) |

---

## ▶️ How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/Heart_stroke_prediction_sprint1_3.git
   cd Heart_stroke_prediction_sprint1_3
   ```

2. **Install dependencies**
   ```bash
   pip install numpy pandas matplotlib seaborn scipy jupyter
   ```

3. **Launch Jupyter**
   ```bash
   jupyter notebook
   ```

4. **Run the notebooks in order:** Sprint 1 → Sprint 2 → Sprint 3

> ⚠️ The notebooks were written in **Google Colab** and read files from `/content/`. When running locally, update the file paths (e.g., `pd.read_csv("healthcare-dataset-stroke-data.csv")`) and remove the `google.colab` download cells.

---

## ⚠️ Limitations

- Severe class imbalance (~4.9% stroke cases)
- Findings show association, **not causation**
- BMI missing values were mean-imputed, which may reduce variance
- No predictive model has been built yet

## 🔮 Future Work

- Handle class imbalance (SMOTE, class weights)
- Build and evaluate classification models (Logistic Regression, Random Forest, XGBoost)
- Evaluate with precision, recall, F1-score, and ROC-AUC
- Build a simple risk-screening dashboard

---

## 👤 Author

**Kothapalli Ganesh**


---

## 📄 License

This project is for educational purposes.
