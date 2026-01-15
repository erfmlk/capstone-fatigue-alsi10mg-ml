# Data-Driven Assessment of Surface Post-Processing Effects on Fatigue Life of LPBF AlSi10Mg
# capstone-fatigue-alsi10mg-ml

**Project for Capstone Assignment 24.1: Capstone Project: Final Report **  
  
Course: **Professional Certificate in Machine Learning and Artificial Intelligence by Berkeley**  
**By: Erfan Maleki**

---

## Overview

This repository contains the **final capstone project (Module 24.1)** for the UC Berkeley Professional Certificate in Machine Learning & Artificial Intelligence.

The project presents a **complete, end-to-end machine learning workflow** for analyzing and predicting the fatigue life of **Laser Powder Bed Fusion (LPBF) AlSi10Mg** components using experimental data related to stress amplitude, surface post-processing condition, residual stress state, and mechanical properties.

The goal is to transform experimentally measured fatigue data into **actionable, data-driven guidance** for engineers working on fatigue-critical additively manufactured components.

---

## 1. Business Understanding (Plain Language)

Metal additively manufactured (3D-printed) components often fail due to **fatigue**, meaning they crack and fracture under repeated loading.  
Although surface post-processing techniques can significantly improve fatigue life, selecting the most effective treatment is challenging, expensive, and traditionally based on trial-and-error testing.

**This project addresses the following practical question:**

> *Which surface post-processing treatments most effectively improve the fatigue life of LPBF AlSi10Mg, and which material and surface features drive this improvement?*

Machine learning is used to reduce reliance on costly experimental testing and provide **evidence-based decision support**.

---

## 2. Research Question

How do surface-induced variations in microstructural, surface texture, residual stress, and mechanical properties—resulting from different post-processing treatments—influence the fatigue life of LPBF AlSi10Mg components, and which features are most predictive of fatigue performance across varying stress regimes?

---

## 3. Data Source

This capstone uses a **real experimental dataset** derived from the peer-reviewed publication:

Maleki, E., & Shamsaei, N. (2024).  
*A comprehensive study on the effects of surface post-processing on fatigue performance of additively manufactured AlSi10Mg*.  
**Additive Manufacturing**, 86, 104179.

### Dataset Characteristics
- 88 fatigue test conditions  
- 21 surface post-processing methods, including:
  - Mechanical (SB, CSP, SSP, UNSM)
  - Chemical (CP, ECP)
  - Laser-based (LP, LSP)
  - Hybrid treatments (e.g., LSP + UNSM, GSSP + ECP)
- Four stress amplitudes  
- All experiments conducted under controlled LPBF and post-processing conditions  

### Input Features
- **Mechanical:** Yield strength, ultimate tensile strength, elongation  
- **Surface:** Hardness, hardness depth, roughness (Ra, Rv)  
- **Residual stress:** Surface CRS, maximum CRS, CRS depth  
- **Defects:** Porosity, depth of pore closure  
- **Microstructure:** Grain size, mean grain area  
- **Loading:** Stress amplitude  

### Target Variable
- **Fatigue life (cycles to failure)**

---

## 4. Analytical Approach

The project follows a structured data science workflow:

1. **Data Preparation**
   - Cleaning, column standardization, median imputation
   - Train/test splitting for reproducibility

2. **Exploratory Data Analysis (EDA)**
   - Distributions of fatigue life and stress amplitude
   - Relationships between surface condition and fatigue behavior
   - Figures 01–09

3. **Dimensionality Reduction**
   - Principal Component Analysis (PCA) to identify dominant fatigue drivers
   - Figures 10–11

4. **Unsupervised Learning**
   - K-Means and DBSCAN clustering in PCA space
   - Identification of treatment-performance groupings

5. **Predictive Modeling**
   - Linear Regression (baseline)
   - Ridge and Lasso Regression
   - Random Forest and Gradient Boosting Regression
   - Classification models for fatigue-life tier screening

6. **Model Evaluation**
   - Cross-validation
   - Grid-search hyperparameter optimization
   - RMSE, R², and classification metrics

---

## 5. Evaluation Metrics and Rationale

- **R² (Coefficient of Determination):** Quantifies the proportion of fatigue-life variance explained by the model  
- **RMSE:** Measures typical prediction error magnitude  
- **Accuracy / Precision / Recall:** Evaluate classification reliability  
- **Cross-Validation:** Ensures generalization beyond a single data split  

These metrics are standard, interpretable, and well-aligned with engineering decision-making.

---

## 6. Summary of Key Findings

- **Stress amplitude** is the strongest driver of fatigue life.
- **Surface roughness (Ra, Rv)** governs crack initiation behavior.
- **Compressive residual stress magnitude and depth** significantly delay crack growth.
- **Surface hardness gradients** contribute to improved fatigue resistance.
- Bulk mechanical properties alone are insufficient predictors without surface information.
- **Nonlinear machine learning models** significantly outperform linear baselines.
- Hybrid surface post-processing treatments consistently outperform single-step processes.

---

## 7. Practical Impact

This work provides:
- A **data-driven framework** for selecting surface post-processing treatments
- Reduced reliance on costly trial-and-error fatigue testing
- Improved confidence in fatigue-critical AM component design
- A transferable ML workflow applicable to other alloys and AM processes

---

## 8. Conclusions and Next Steps

This capstone demonstrates how machine learning can enhance fatigue-life prediction and materials decision-making in additive manufacturing.

Future work includes:
- Expanding the dataset to additional alloys and build orientations
- Integrating in-situ process monitoring data
- Deploying trained models as decision-support tools
- Extending the framework toward certification and qualification pipelines

---

## Jupyter Notebook

The complete technical analysis is contained in:

**`capstone_FULL_35_FIGURES_FINAL.ipynb`**

The notebook includes:
- Clearly structured markdown sections and headings
- One figure per code cell (grader-friendly)
- Full EDA (Figures 01–09)
- PCA and clustering (Figures 10–11, 28–30)
- Regression and nonlinear modeling (Figures 21–25)
- Cross-validation and model evaluation (Figure 33)
- Hyperparameter optimization (Figure 35)
- Interpretation and conclusions

---

## Repository Structure

| File                                           | Description                                                                       |
| ---------------------------------------------- | --------------------------------------------------------------------------------- |
| `capstone_FULL_35_FIGURES_FINAL.ipynb`         | Main Jupyter Notebook with complete ML workflow, EDA, modeling, and Figures 01–35 |
| `Capstone data- Fatigue of LPBF AlSi10Mg.xlsx` | Dataset used in the project                                                       |
| `Capstone_Assignment_24.1-Erfan_Maleki.docx`   | Final written capstone report with full discussion and figure references          |
| `figures/`                                     | Directory containing all generated figures (Figures 01–35)                        |
| `README.md`                                    | Project description, summary of findings, and instructions                        |
| `LICENSE`                                      | MIT License (optional)                                                            |

---


## How to Run

1. Clone the repository:
```bash
git clone https://github.com/erfmlk/capstone-fatigue-alsi10mg-ml.git
cd capstone-fatigue-alsi10mg-ml
