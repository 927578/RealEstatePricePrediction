# 🏠 Real Estate Price Prediction using Subset Selection and Regularization

A course project from **STAT 326** focused on developing predictive models for housing prices using R. This project applies traditional subset selection, cross-validation, and shrinkage methods (Ridge & Lasso Regression) to determine the best regression model for log-transformed housing prices.

## 📁 Dataset

- **Source**: `RealEstate.csv`
- **Target Variable**: `price` (log-transformed to `logPrice`)
- **Features**: 
  - Numeric: `sqfeet`, `bath`, `cars`, `year`, `lot`
  - Categorical: `ac`, `pool`, `quality`, `highway` (converted to factors)
- **Preprocessing**:
  - Dropped uninformative fields (`id`, original `price`)
  - Applied `log()` transformation to price
  - Standardized and encoded categorical variables as factors

## 🔍 Model Selection Approaches

### 1. 📉 Subset Selection using AIC & BIC
- **AIC Optimal Model**: 9 predictors  
- **BIC Optimal Model**: 7 predictors  
- Plotted AIC/BIC vs. number of predictors using `ggplot2`

### 2. 📦 Cross-Validation for MSPE
- Used 20-fold CV with the `caret` package
- **Lowest MSPE model**: 9 predictors (consistent with AIC)

## 🧊 Shrinkage Methods

### 🧪 Models Compared:
- **OLS (Ordinary Least Squares)**
- **Ridge Regression** (`alpha=0`)
- **Lasso Regression** (`alpha=1`)
- Used `glmnet` with 10-fold CV to choose optimal `lambda`

### 🔧 Best Lambda Values:
- **Ridge**: `λ = 0.0356`
- **Lasso**: `λ = 0.00177`

### 🔍 Coefficient Comparison:
Extracted and visualized coefficient paths for all three models and added OLS reference lines.

## 📊 Model Evaluation (Test Set)

| Model  | MSPE       |
|--------|------------|
| OLS    | 0.3641     |
| Ridge  | 0.0324     |
| Lasso  | **0.0318** ✅ |

✅ **Conclusion**: Lasso Regression performed best, offering the lowest prediction error on the test set.

## 📦 R Packages Used

- `dplyr`, `ggplot2`, `leaps`, `caret`
- `glmnet` for Ridge & Lasso
- `Matrix`, `tidyr`, `tibble`, `lattice`

## 📌 Project Structure

