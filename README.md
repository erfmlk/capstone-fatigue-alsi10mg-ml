# Fatigue Life Prediction of LPBF AlSi10Mg Using Machine Learning  
# capstone-fatigue-alsi10mg-ml

**Final Capstone Project (Module 24.1)**  

Course: **Professional Certificate in Machine Learning and Artificial Intelligence by Berkeley**  
**By: Erfan Maleki**


---

## Overview (Nontechnical)

Fatigue failure is one of the primary limitations preventing wider adoption of **additively manufactured (3D-printed) metal components** in safety-critical applications such as aerospace and automotive systems.  
While surface post-processing techniques can significantly improve fatigue performance, selecting the most effective treatment remains challenging and costly.

This capstone applies **machine learning techniques** to a real experimental dataset to **quantify how surface post-processing treatments influence fatigue life** of laser powder bed fused (LPBF) **AlSi10Mg** and to identify the **most important features governing fatigue performance**.

The goal is to move beyond trial-and-error testing toward **data-driven decision making**.

---

## Research Question

How do surface-induced variations in microstructural, surface texture/topography, and mechanical properties—resulting from different post-processing treatments—influence the fatigue life of LPBF AlSi10Mg components, and which features are most predictive of fatigue performance across varying stress regimes?

---

## Dataset and Data Source

This project uses a **comprehensive experimental dataset** derived from the following peer-reviewed study:

**Maleki, E., & Shamsaei, N. (2024).**  
*A comprehensive study on the effects of surface post-processing on fatigue performance of additively manufactured AlSi10Mg.*  
**Additive Manufacturing**, 86, 104179.

### Dataset Characteristics
- **88 fatigue test conditions**
- **21 surface post-processing treatments**, including:
  - Mechanical (SB, CSP, SSP, UNSM)
  - Chemical (CP, ECP)
  - Laser-based (LP, LSP)
  - Hybrid treatments (e.g., LSP+UNSM, GSSP+ECP)
- **Four stress amplitudes**
- All experiments conducted under controlled LPBF and post-processing conditions

### Feature Groups
- **Mechanical properties:** Yield strength, ultimate tensile strength, elongation
- **Surface characteristics:** Hardness, hardness depth, roughness (Ra, Rv)
- **Residual stress:** Surface CRS, maximum CRS, CRS depth
- **Defects:** Porosity, depth of pore closure
- **Microstructure:** Grain size, mean grain area
- **Loading condition:** Stress amplitude

### Target Variable
- **Fatigue life (cycles to failure)**

---

## Analytical Approach

The capstone follows a complete, end-to-end machine learning workflow:

1. **Data Preparation**
   - Column standardization and cleaning  
   - Median imputation for missing numeric values  
   - Train/test splitting for reproducibility  

2. **Exploratory Data Analysis (EDA)**
   - Descriptive statistics
   - Visualization of fatigue life versus stress amplitude, surface roughness, and treatment condition
   - Correlation analysis to identify key relationships

3. **Dimensionality Reduction**
   - Principal Component Analysis (PCA) to identify dominant sources of variance

4. **Unsupervised Learning**
   - K-Means clustering to group treatments by fatigue performance
   - DBSCAN to identify exceptional or outlier behavior

5. **Predictive Modeling**
   - Regression models:
     - Linear Regression
     - Ridge and Lasso Regression
     - Polynomial Regression
     - Random Forest Regression
   - Classification models:
     - K-Nearest Neighbors (KNN)
     - Support Vector Machine (SVM)
     - Random Forest Classifier

6. **Model Evaluation**
   - Cross-validation
   - Grid-search hyperparameter tuning
   - RMSE, R², and classification accuracy metrics

---

## Evaluation Metrics

- **RMSE (Root Mean Squared Error):** Measures typical prediction error in fatigue life
- **R² Score:** Indicates how much variability in fatigue life is explained by the model
- **Accuracy / Precision / Recall:** Used for fatigue-performance tier classification
- **Cross-Validation:** Ensures model generalization beyond a single train/test split

These metrics were selected for their interpretability and relevance to engineering decision-making.

---

## Key Findings (Plain Language)

- **Stress amplitude** is the strongest driver of fatigue life.
- **Surface roughness (Ra, Rv)** strongly influences crack initiation.
- **Residual compressive stress magnitude and depth** significantly delay crack growth.
- **Surface hardness gradients** contribute to improved fatigue resistance.
- Bulk mechanical properties alone are insufficient predictors without surface information.
- Hybrid surface treatments consistently outperform single-step post-processing methods.

---

## Practical Impact

This project demonstrates how machine learning can:
- Reduce reliance on costly trial-and-error fatigue testing
- Support data-driven selection of surface post-processing methods
- Improve confidence in fatigue-critical component design
- Provide a transferable workflow applicable to other alloys and AM processes

---

## Next Steps and Recommendations

- Expand the dataset to include additional alloys and build orientations
- Incorporate in-situ monitoring data as predictive features
- Deploy the final model as a decision-support tool
- Extend the framework toward qualification and certification workflows

---

## Repository Structure

| Path / File | Description |
|------------|------------|
| `notebooks/01_data_preparation.ipynb` | Data cleaning and preprocessing |
| `notebooks/02_exploratory_analysis.ipynb` | EDA and visualization |
| `notebooks/03_pca_clustering.ipynb` | PCA and unsupervised learning |
| `notebooks/04_regression_models.ipynb` | Regression models with CV and GridSearch |
| `notebooks/05_classification_models.ipynb` | Fatigue-tier classification |
| `notebooks/06_final_model_interpretation.ipynb` | Feature importance and conclusions |
| `data/raw/` | Original experimental dataset |
| `data/processed/` | Cleaned dataset |
| `requirements.txt` | Python dependencies |
| `README.md` | Project summary and instructions |

---

## How to Run

1. Clone the repository:
```bash
git clone https://github.com/erfmlk/capstone-fatigue-alsi10mg-ml.git
cd capstone-fatigue-alsi10mg-ml
