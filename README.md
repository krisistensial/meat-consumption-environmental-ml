# Modeling the Impact of Meat Consumption on Environmental Sustainability Using Machine Learning

## Overview
This academic project aims to analyze and predict the environmental impact of meat consumption across multiple countries using machine learning. By combining global food balance sheets, agricultural production statistics, and greenhouse gas emissions with socio-economic indicators, we model the total GHG emissions from livestock (kg CO2eq per capita) and apply Explainable AI (SHAP) to isolate critical ecological drivers.

## Dataset
Our panel data covers **148 countries** over the years **2010–2022** and integrates multiple authoritative global sources:
*   **FAOSTAT**: Emissions from Livestock (CH4, N2O), Food Balances (meat supply/capita for Beef, Pork, Poultry, and Sheep), and Crops & Livestock Production.
*   **World Bank**: GDP per capita (constant USD), population demographics, urbanization rate, and agricultural land coverage.

## Methodology
1.  **Data Harmonization**: Standardized temporal and regional country names across heterogeneous sheets; handled skewness through Logarithmic Transformations (log(x+1)) on highly skewed predictors (GDP, Population, Production).
2.  **Feature Engineering**: Consolidated CH4 and N2O emissions into Carbon Dioxide Equivalents (CO2eq) using global warming potentials (GWP100: CH4 = 28, N2O = 265).
3.  **Missing Value Imputation**: Addressed spatial data holes using grouped median country-wise aggregations and Forward/Backward chronological fills for macro-structural World Bank metrics.
4.  **Modeling Approaches**: Compared classic linear models (Linear Regression, Ridge, Lasso) with non-linear tree ensembles (Random Forest, Gradient Boosting Regressors) optimized via 5-Fold Cross-Validation Grid Search.
5.  **Explainable AI**: Conducted global and local feature attribution using **SHAP (SHapley Additive exPlanations)** to interpret non-linear contributions.

## Results
*   **Best Model**: **Gradient Boosting Regressor** emerged as the superior model.
    *   **R² Score**: **0.9765** (explaining ~97.7% of the total variance in environmental emissions).
    *   **Mean Absolute Error (MAE)**: **95.36 kg CO2eq/capita** (~12.1% relative error compared to global mean).
*   **Key Insights (SHAP)**:
    *   `log_produksi_total_t` (Overall Livestock Production) and `kons_sheep` (Mutton & Goat Meat consumption) are identified as the most impactful drivers of emissions.
    *   Increasing ruminant meat intake (`kons_beef` and `kons_sheep`) scales up emissions quadratically, whereas poultry consumption (`kons_poultry`) shows a relatively flat environmental footprint.

## Tech Stack
*   **Languages**: Python
*   **Libraries**: Pandas, NumPy, Scikit-Learn, Matplotlib, Seaborn, SHAP, SciPy
*   **Deployment/Environment**: Google Colab / Jupyter Notebooks
