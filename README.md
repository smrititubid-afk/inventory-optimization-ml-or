# Uncertainty-Aware Predictive Inventory Optimization using Machine Learning and Conformal Prediction

An end-to-end Machine Learning and Operations Research framework for improving retail inventory decisions under demand uncertainty using the Walmart M5 Forecasting Dataset.

---

# Project Overview

Inventory management is one of the most critical functions in retail supply chains. Maintaining too much inventory increases holding costs, while insufficient inventory results in stockouts and poor customer service. Traditional inventory planning approaches often rely on deterministic demand forecasts and fixed safety stock policies, making them less effective when demand is highly uncertain.

This project develops an uncertainty-aware inventory optimization framework that combines Machine Learning forecasting, Conformal Prediction, inventory optimization, lead-time scenario analysis, and statistical validation into a unified decision-support pipeline.

The framework demonstrates how forecast uncertainty can be incorporated into inventory decisions, enabling more robust and interpretable inventory policies.

---

# Problem Statement

Most inventory planning systems suffer from several practical limitations:

* Depend only on point forecasts without considering prediction uncertainty.
* Assume normally distributed forecast errors.
* Apply fixed safety stock policies across products with different demand patterns.
* Ignore uncertainty in replenishment lead times.
* Provide limited support for business decision-making under uncertainty.

This project addresses these challenges by integrating uncertainty estimation directly into the inventory optimization process.

---

# Project Objectives

The project was designed to:

* Analyze historical retail demand patterns.
* Build an accurate demand forecasting model using Machine Learning.
* Estimate forecast uncertainty using Conformal Prediction.
* Compare multiple inventory planning strategies.
* Incorporate lead-time uncertainty into inventory decisions.
* Perform sensitivity, robustness, and statistical validation analyses.
* Generate interpretable business insights for inventory management.

---

# Dataset

**Source:** Walmart M5 Forecasting Dataset

The original Walmart M5 dataset contains demand information for more than **30,000 retail products** across multiple stores.

To enable efficient experimentation while preserving representative demand characteristics, a sample of **100 SKUs** was selected. The sampled dataset retains intermittent demand behaviour, demand variability, and zero-demand periods commonly observed in retail inventory systems.

---

# Project Workflow

```text
Demand Analysis
        ↓
Feature Engineering
        ↓
LightGBM Forecasting
        ↓
Forecast Diagnostics
        ↓
Conformal Prediction
        ↓
Inventory Optimization
        ↓
Lead-Time Scenario Analysis
        ↓
Inventory Policy Optimization
        ↓
Sensitivity & Robustness Analysis
        ↓
Statistical Validation
        ↓
Managerial Decision Support
```

---

# Repository Structure

```text
inventory-optimization-ml-or/

│
├── notebooks/
│   ├── 01_demand_analysis.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_baseline_modeling.ipynb
│   ├── 04_forecast_diagnostics.ipynb
│   ├── 05_conformal_prediction.ipynb
│   ├── 06_inventory_optimization.ipynb
│   ├── 07_lead_time_scenario_policy_engine.ipynb
│   ├── 08_inventory_policy_optimization_engine.ipynb
│   ├── 09_sensitivity_robustness_final_testing.ipynb
│   ├── 10_baseline_ablation_final_validation.ipynb
│   └── 11_research_validation_and_statistical_analysis.ipynb
│
├── assets/
├── reports/
├── requirements.txt
├── README.md
└── .gitignore
```

---

# Methodology

## 1. Demand Analysis

Performed exploratory data analysis to understand retail demand behaviour.

Tasks included:

* Demand distribution analysis
* Average demand calculation
* Demand variability assessment
* Coefficient of Variation (CV)
* Zero-demand ratio analysis
* Identification of intermittent demand patterns

---

## 2. Feature Engineering

Constructed forecasting features using historical demand information.

Features include:

* Lag features (1, 7 and 28 days)
* Rolling mean
* Rolling standard deviation
* Calendar features
* Weekend indicators
* Monthly and quarterly information

---

## 3. Machine Learning Forecasting

Demand forecasting was performed using a **LightGBM Regressor** trained on engineered time-series features.

Forecast performance was evaluated using:

* RMSE
* MAE
* Residual Analysis

---

## 4. Forecast Diagnostics

The forecasting model was further validated through:

* Residual histogram
* Residual boxplot
* Forecast error analysis
* Prediction error distribution

---

## 5. Conformal Prediction

Conformal Prediction was applied to estimate prediction intervals around each demand forecast without assuming normally distributed forecast errors.

Instead of relying only on point forecasts, inventory decisions were based on uncertainty-aware prediction intervals.

---

## 6. Inventory Optimization

Five inventory policies were implemented and compared.

* Point Forecast Policy
* Gaussian Safety Stock Policy
* Conformal Safety Stock Policy
* Newsvendor-Style Policy
* Lead-Time Scenario Optimized Policy

Each policy was evaluated using expected inventory cost, holding cost, stockout cost, fill rate and service level.

---

## 7. Lead-Time Scenario Analysis

Different replenishment lead-time scenarios were incorporated to evaluate their impact on inventory decisions.

This enabled comparison between fixed lead-time planning and uncertainty-aware lead-time planning.

---

## 8. Sensitivity and Robustness Analysis

Inventory policies were evaluated under different business assumptions by varying:

* Holding cost
* Stockout cost
* Target fill rate

The resulting changes in safety factors and inventory performance were analysed.

---

## 9. Statistical Validation

Additional statistical analyses were performed to validate forecasting performance.

These include:

* Residual Histogram
* Residual Boxplot
* Conformal Score Distribution
* Prediction Interval Width Distribution
* Actual vs Predicted Analysis
* Residual vs Prediction Analysis
* Q-Q Plot
* Correlation Heatmap

---

## 10. Managerial Decision Support

Business-oriented analyses were conducted to interpret model performance.

These include:

* Cost reduction analysis
* Stockout reduction analysis
* Cost-service trade-off
* Safety factor analysis
* Fill-rate comparison
* Inventory policy evaluation

---

# Results

## Forecasting Performance

| Metric             | Value      |
| ------------------ | ---------- |
| RMSE               | **1.7857** |
| MAE                | **0.8253** |
| Conformal Coverage | **89.08%** |

---

## Inventory Performance

| Metric                      | Value                                   |
| --------------------------- | --------------------------------------- |
| Baseline Expected Cost      | **67,587.62**                           |
| Final Expected Cost         | **35,474.69**                           |
| Expected Cost Reduction     | **47.51%**                              |
| Expected Stockout Reduction | **100%**                                |
| Best Inventory Policy       | **Lead-Time Scenario Optimized Policy** |

---
---

# Project Visualizations

The following figures summarize the key analyses performed during the project and illustrate the performance of the proposed inventory optimization framework.

---

## 1. Forecast Error & Uncertainty Analysis

This figure validates the forecasting model by analyzing residuals, conformal scores, and adaptive prediction interval widths. The results indicate low systematic prediction bias and demonstrate how conformal prediction captures uncertainty without assuming a specific error distribution.

<p align="center">
  <img src="assets/forecast_validation.png" width="900">
</p>

---

## 2. Inventory Policy Evaluation

Five inventory policies were evaluated using expected inventory cost, fill rate, holding cost, stockout cost, and sensitivity analysis. The proposed **Lead-Time Scenario Optimized Policy** achieved the best overall cost–service trade-off.

<p align="center">
  <img src="assets/inventory_policy_evaluation.png" width="900">
</p>

---

## 3. Statistical Validation

Additional statistical validation was performed using Actual vs Predicted analysis, residual diagnostics, Q-Q plots, and feature correlation analysis. These analyses support the reliability of the forecasting model and justify the use of conformal prediction.

<p align="center">
  <img src="assets/statistical_validation.png" width="900">
</p>

---

## 4. Managerial Decision Support

Business-oriented analyses highlight the practical impact of the proposed framework. The results demonstrate significant reductions in expected inventory cost and stockout units while improving overall service levels.

<p align="center">
  <img src="assets/managerial_decision_support.png" width="900">
</p>

---
# Key Contributions

* Developed an end-to-end Machine Learning and inventory optimization framework.
* Integrated Conformal Prediction for distribution-free uncertainty estimation.
* Compared multiple inventory planning policies under demand uncertainty.
* Incorporated lead-time scenario analysis into inventory planning.
* Performed sensitivity and robustness analyses under different business assumptions.
* Conducted statistical validation of forecasting performance.
* Generated interpretable managerial insights for inventory decision support.

---

# Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* LightGBM
* SciPy
* Matplotlib
* Seaborn
* Jupyter Notebook

---

# How to Run

Clone the repository.

```bash
git clone https://github.com/smrititubid-afk/inventory-optimization-ml-or.git
```

Install the required libraries.

```bash
pip install -r requirements.txt
```

Execute the notebooks sequentially from **01** to **11**.

---

# Future Scope

The current implementation successfully validates the proposed uncertainty-aware inventory optimization framework.

Potential research extensions include:

* Decision-Focused Learning
* Scenario-Based Stochastic Programming
* Joint Demand–Lead Time Optimization
* Multi-Echelon Inventory Systems
* Interactive Decision Support Dashboard

---

# Repository Status

**Status:** Initial research framework completed and validated.

The implemented pipeline covers demand analysis, forecasting, uncertainty estimation, inventory optimization, lead-time scenario analysis, sensitivity analysis, and statistical validation. The items listed under Future Scope represent potential research extensions rather than incomplete project components.
