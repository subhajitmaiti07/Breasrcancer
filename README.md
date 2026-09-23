# Breast Cancer Exploratory Data Analysis (EDA)

**Author:** Subhajit Maiti  
**Project:** Exploratory Data Analysis on the Breast Cancer Wisconsin (Diagnostic) Dataset  
**Programme:** IBM SkillsBuild Internship — Data Science & AI

---

## Project Description

This project performs a comprehensive **Exploratory Data Analysis (EDA)** on the [Breast Cancer Wisconsin (Diagnostic) dataset](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data). The dataset contains real-valued features computed from digitised images of fine needle aspirates (FNA) of breast masses, describing characteristics of the cell nuclei present in the images.

The objective is to:
- Understand the structure and quality of the dataset.
- Identify statistical patterns that distinguish **Malignant (M)** from **Benign (B)** tumours.
- Discover the most predictive features using correlation analysis, Random Forest feature importances, and PCA.
- Produce publication-quality visualisations that communicate key insights.

---

## Dataset

| Property | Value |
|----------|-------|
| **Source** | UCI Machine Learning Repository |
| **Kaggle link** | https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data |
| **Samples** | 569 (212 Malignant, 357 Benign) |
| **Features** | 30 numerical + id + diagnosis (target) |
| **Missing values** | None (after dropping artefact column) |
| **Duplicate rows** | None |

The 30 numerical features describe 10 properties of each cell nucleus (radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, fractal dimension), each measured as its **mean**, **standard error (SE)**, and **worst (maximum)** value.

---

## Technologies Used

| Library | Version (minimum) | Purpose |
|---------|-------------------|---------|
| Python | 3.8+ | Primary language |
| Jupyter Notebook | 6.4+ | Interactive development |
| pandas | 1.3+ | Data loading, cleaning, analysis |
| numpy | 1.21+ | Numerical operations |
| matplotlib | 3.4+ | Custom visualisations |
| seaborn | 0.11+ | Statistical visualisations |
| scikit-learn | 0.24+ | Random Forest + PCA |

---

## Project Structure

```
.
├── SubhajitMaiti_BreastCancerEDA.ipynb   ← Main Jupyter Notebook (complete EDA)
├── SubhajitMaiti_ProjectReport.docx      ← Full project documentation (Word)
├── requirements.txt                       ← Python dependencies
├── README.md                              ← This file
├── data.csv                               ← Raw dataset
├── data_cleaned.csv                       ← Cleaned dataset (output)
├── plot_01_diagnosis_distribution.png     ← Class balance visualisation
├── plot_02_tumor_size.png                 ← Tumour size histograms
├── plot_03_tumor_shape.png                ← Tumour shape violin plots
├── plot_04_correlation.png                ← Correlation heatmap + top-10 features
├── plot_05_feature_importance.png         ← Random Forest feature importances
├── plot_06_pca.png                        ← PCA scree plot + 2D projection
└── plot_07_malignancy_patterns.png        ← Radar chart + box plots
```

---

## Setup & Run Instructions

### 1. Clone / Download the project

Download all files into a local directory (or clone the repository if hosted on Git).

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv
# Windows
venv\Scripts\activate
# macOS / Linux
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Then open **`SubhajitMaiti_BreastCancerEDA.ipynb`** in the browser.

### 5. Run all cells

Use **Kernel → Restart & Run All** to execute the entire notebook from scratch. All output plots will be regenerated and saved as PNG files in the same directory.

> **Note:** `data.csv` must be present in the same directory as the notebook. The cleaned dataset `data_cleaned.csv` is generated automatically by the notebook.

---

## EDA Sections at a Glance

| Section | What it covers |
|---------|---------------|
| 1. Load Data | Read CSV, inspect shape and head |
| 2. Basic Info & Data Types | dtypes, column info |
| 3. Drop Unnamed Columns | Remove all-NaN artefact column |
| 4. Missing Value Analysis | Count, percentage, imputation strategy |
| 5. Duplicate Row Analysis | Detect and remove duplicate records |
| 6. Column-level Inspection | Unique value counts, categorical value distributions |
| 7. Descriptive Statistics | Mean, std, min/max, quartiles for all features |
| 8. Outlier Detection (IQR) | Identify outlier-prone features with boxplots |
| 9. Data Type Corrections | Encode diagnosis, cast id to string |
| 10. Final Dataset Summary | Cleaned dataset shape + head |
| EDA Vis 1 | Diagnosis distribution (pie, bar, stacked bar) |
| EDA Vis 2 | Tumour size characteristics (histograms by class) |
| EDA Vis 3 | Tumour shape irregularity (violin plots) |
| EDA Vis 4 | Correlation analysis (heatmap + top-10 bar chart) |
| EDA Vis 5 | Feature importance (Random Forest — 300 trees) |
| EDA Vis 6 | PCA (scree plot + 2D projection) |
| EDA Vis 7 | Malignancy patterns (radar chart + box plots) |

---

## Key Findings

1. **Size is the strongest discriminator** — `radius_worst`, `perimeter_worst`, and `area_worst` are the top predictors of malignancy.
2. **Shape irregularity is highly informative** — `concave points_worst` and `compactness_worst` strongly correlate with the malignant class.
3. **High multicollinearity** among size features (radius ≈ perimeter ≈ area); tree-based methods handle this naturally.
4. **Near-linear separability** in PCA space — PC1 + PC2 explain 63.2% of variance with clear class separation.
5. **Mild class imbalance** (62.7% Benign, 37.3% Malignant) — use AUC-ROC and F1-score, not just accuracy, for model evaluation.
6. **Data is clean** — zero missing values and zero duplicates after column cleanup.

---

## License

Dataset: [CC0 Public Domain](https://creativecommons.org/publicdomain/zero/1.0/) via UCI / Kaggle.  
Code: MIT License.
