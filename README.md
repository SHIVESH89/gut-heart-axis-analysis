# 🫀🦠 AI for Gut & Heart: Unraveling the Gut-Heart Axis

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/Status-Complete%20Analysis-success.svg)]()
[![Data-Source](https://img.shields.io/badge/Dataset-American%20Gut%20Project-informational.svg)](https://github.com/biocore/American-Gut)

---

## 📌 Summary

The **Gut-Heart Axis** is one of the most critical frontiers in modern biomedical data science. Emerging medical research (*Nature Medicine, JACC*) demonstrates that gastrointestinal microbiome composition directly influences cardiovascular pathophysiology through metabolic pathways such as **Trimethylamine N-oxide (TMAO)**, systemic inflammation, and short-chain fatty acids (SCFAs).

This repository contains an end-to-end data science and statistical pipeline analyzing **676 human participants** from the **American Gut Project**. We perform rigorous **Exploratory Data Analysis (EDA)**, **Inferential Hypothesis Testing ($t$-tests, ANOVA, Tukey's HSD)**, and **Principal Component Analysis (PCA)** to uncover how dietary diversity, lifestyle factors, and metabolic traits intersect to drive cardiovascular and gut health outcomes.

---

## 🎯 The Need for the Dataset

### Why the American Gut Project?
* **Real-World Ecological Scale:** Most clinical microbiome trials are limited by small cohorts ($N < 50$) and strict, artificial laboratory conditions. The American Gut Project provides the world's largest crowdsourced citizen science cohort with diverse lifestyle and dietary patterns.
* **Granular Dietary & Phenotypic Resolution:** Diet is the **#1 modifiable risk factor** for both gut dysbiosis and cardiovascular disease (WHO). This dataset uniquely pairs stool sample metadata with granular dietary frequency metrics (plant counts, fiber intake, fermented foods, alcohol, etc.) and clinical outcomes.
* **Target Cohort Selection:** We extracted **676 stool-sample participants** with **48 curated clinical and lifestyle features**, ensuring direct biological relevance to intestinal and systemic cardiometabolic health.

---

## 🔬 What Has Been Done

### 1. Data Cleaning & Preprocessing Pipeline
* **Artifact Removal:** Replaced system string nulls (`no_data`, `not provided`, `unspecified`) with standard IEEE `NaN` representations.
* **Feature Curation:** Filtered irrelevant metadata to isolate 48 core variables spanning demographics, dietary diversity metrics, bowel habits, and cardiovascular indicators.
* **Quality Assurance:** Assessed missingness distributions and verified variable data types across continuous, ordinal, and nominal features.

### 2. Exploratory Data Analysis (EDA) & Visualizations (`01_EDA_Visualization.ipynb`)
* **Univariate Distributions:** Systematic profiling of demographic variables, BMI distributions, and plant consumption frequencies.
* **Bivariate Associations:** Investigated relationships between dietary patterns and health outcomes (e.g., high plant intake vs. gastrointestinal symptom frequency; BMI vs. dietary habits).
* **Correlation Heatmaps:** Quantified cross-feature correlations to identify co-varying dietary and clinical factors.

### 3. Inferential Hypothesis Testing (`02_Statistical_Analysis.ipynb`)
* **Descriptive Suite:** Comprehensive calculation of central tendencies, dispersion, skewness, kurtosis, and frequency cross-tabulations.
* **Two-Sample Independent $t$-Tests:** Evaluated physiological variations (e.g., BMI across biological sex) accompanied by effect size estimation (**Cohen's $d$**).
* **One-Way ANOVA & Effect Sizes:** Evaluated variance across multiple dietary categories against metabolic indicators, measuring explained variance via **Eta-squared ($\eta^2$)**.
* **Post-Hoc Pairwise Comparisons:** Applied **Tukey's Honestly Significant Difference (HSD)** test with family-wise error rate control to locate exact subgroup divergence.

### 4. Unsupervised Learning & Dimensionality Reduction (PCA)
* **Feature Standardization:** Standardized multi-scale continuous features using Z-score normalization.
* **Variance Decomposition & Scree Plot:** Mapped cumulative explained variance to determine optimal dimensionality retention.
* **2D & 3D Biplot Projections:** Visualized sample distributions alongside feature loading vectors to identify the principal drivers of variance across the cohort.
* **Loadings Matrix Heatmap:** Extracted mathematical weights for each feature across leading principal components.

---

## 📂 Repository Structure

```text
├── dataset/                         # Curated & cleaned American Gut Project data
│   └── american_gut_clean.csv
│
├── plots/                           # Generated EDA figures (15 high-res PNGs)
│   ├── 01_missing_values.png
│   ├── 02_age_sex_distribution.png
│   ├── 03_bmi_distribution.png
│   └── ...
│
├── visualizations/                  # High-resolution PNG figures (categorized by notebook)
│   ├── 01_EDA_Visualizations/       # 15 EDA Plots (Distributions, Heatmaps, Scatter, Pairplots)
│   └── 02_Statistical_Analysis/     # 12 Statistical & PCA Plots (t-tests, ANOVA, Scree, Biplots, 3D PCA)
│
├── 01_EDA_Visualization.ipynb       # Exploratory Data Analysis & visual discovery notebook
├── 02_Statistical_Analysis.ipynb    # Descriptive, inferential stats ($t$-test/ANOVA) & PCA notebook
├── README.md                        # Project documentation, insights & setup guide
└── requirements.txt                 # Python dependencies for reproduction
```

---

## 📊 Key Findings & Insights

1. **Dietary Plant Diversity as a Key Differentiator:** High plant-count consumers demonstrated healthier metabolic profiles and distinct clustering patterns in PCA projections.
2. **Statistically Significant Subgroup Variance:** ANOVA and post-hoc Tukey HSD tests confirmed significant differences in metabolic metrics (e.g., BMI) across distinct dietary cohorts ($p < 0.05$).
3. **Dimensionality Reduction:** The first few principal components capture the dominant axis of variance driven primarily by age, BMI, and dietary fiber/plant variety indices.

---

## 🚀 Getting Started

### Prerequisites
* Python 3.9+
* Jupyter Notebook / JupyterLab

### Installation

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/SHIVESH89/gut-heart-axis-analysis.git
   cd gut-heart-axis-analysis
   ```

2. **Create and Activate a Virtual Environment:**
   ```bash
   # Windows (PowerShell)
   python -m venv venv
   .\venv\Scripts\Activate.ps1

   # macOS / Linux
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Launch the Notebooks:**
   ```bash
   jupyter notebook
   ```
   * Open `01_EDA_Visualization.ipynb` to explore the data pipeline.
   * Open `02_Statistical_Analysis.ipynb` to view the hypothesis testing and PCA suite.



---

## 📚 References & Acknowledgments

* **American Gut Project:** McDonald et al., *"American Gut: an Open Platform for Citizen Science Microbiome Research"*, *mSystems* (2018). [biocore/American-Gut](https://github.com/biocore/American-Gut)
* **Gut-Heart Axis Literature:**
  * Tang, W. H. W., et al. *"Intestinal Microbial Metabolism of Phosphatidylcholine and Cardiovascular Risk."* *New England Journal of Medicine* (2013).
  * Witkowski, M., et al. *"Vascular Effects of the Gut Microbiome: TMAO and Beyond."* *Circulation Research* (2020).

---

## 👤 Author
**Shivesh** ([@SHIVESH89](https://github.com/SHIVESH89))  
*Developed as part of the AI for Gut and Heart Health research initiative.*
