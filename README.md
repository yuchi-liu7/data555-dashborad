# data555-dashborad
# Measurement Error in Piecewise Linear Regression

## 📊 Project Overview

This interactive dashboard explores the impact of measurement error on piecewise linear regression models through simulation. The dashboard demonstrates how naive estimation methods can severely bias effect estimates, particularly in threshold-based exposure-outcome relationships.

## 🚀 Access the Dashboard

**Live Dashboard**: [https://rlpsd3-yuchi-liu.shinyapps.io/dashboard/](https://rlpsd3-yuchi-liu.shinyapps.io/dashboard/)

## 🎯 Key Features

### Interactive Visualizations

1. **Question 1: Bias Visualization**
   - Toggle between true data, observed data, maximum likelihood fit, and naive fit
   - Adjustable sample sizes (100, 250, 500) to explore consistency properties
   - Interactive tooltips showing exposure and outcome values with units
   - Visual identification of the threshold (knot) at 3.5 units

2. **Question 2: Performance Metrics Table**
   - Filterable table displaying bias, standard deviation, and coverage probability
   - Compare naive vs. maximum likelihood methods across different sample sizes
   - Sortable columns with top filters
   - Performance metrics for all three parameters (intercept and two slopes)

### Dashboard Sections

- **About the Data**: Comprehensive dataset description including source, sample size, collection method, study population, and time period
- **Question 1**: Visual demonstration of how measurement error biases slope estimates
- **Question 2**: Quantitative performance comparison showing ML recovery of unbiased estimates

## 🔬 Methodology

### Data Generation

The simulation uses the following parameters:
- **True exposure (X)**: Normal distribution with mean = 3, SD = 1
- **Measurement error (U)**: Normal distribution with mean = 0, SD = √0.5
- **Observed exposure (Z)**: Z = X + U
- **Knot location**: 3.5 units
- **True parameters**: β₀ = 0, β₁ = 1, β₂ = 2
- **Outcome model**: Y = β₀ + β₁·X₁ + β₂·X₂ + ε, where X₂ = max(X - 3.5, 0)

### Estimation Methods

1. **Naive Method**: Regresses outcome on observed (error-contaminated) exposure
2. **Maximum Likelihood Method**: Accounts for known measurement error variance to recover unbiased estimates

## 📈 Key Findings

- **Measurement error introduces systematic bias**: Naive estimates substantially underestimate slopes, especially after the threshold
- **Threshold effects are particularly vulnerable**: The change in slope at the knot is severely distorted when measurement error is ignored
- **Maximum likelihood correction works**: ML estimates approach true parameters with minimal bias
- **Coverage probability reveals method quality**: ML maintains ~95% coverage while naive method has poor coverage (as low as 0%)
- **Sample size matters**: ML estimates become more precise with larger samples while maintaining low bias

## 🌍 Importance and Real-World Impact

This dashboard addresses a critical methodological challenge in public health and environmental research: how measurement error distorts our understanding of threshold-based exposure-outcome relationships. When regulatory agencies set safety limits for pollutants, chemicals, or nutrients, ignoring measurement error can lead to systematically biased estimates of health risks beyond safety thresholds, potentially resulting in regulations that inadequately protect public health or impose unnecessarily restrictive policies.

## 🔧 How to Run Locally

1. **Clone or download this repository**

2. **Install required R packages**:
```r
install.packages(c("flexdashboard", "shiny", "tidyverse", "plotly", "DT", "htmltools"))
```

3. **Open the .Rmd file in RStudio and click "Run Document"**
