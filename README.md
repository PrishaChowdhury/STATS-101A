# Housing Price Prediction Model  
## STATS-101A
Introduction to Data Analysis and Regression
# Housing Price Prediction Using Multiple Linear Regression

Statistical modeling project predicting residential sale prices using advanced regression techniques and rigorous model validation.

## 📊 Project Overview

Built a multiple linear regression model to predict house prices across 7,000 properties, achieving significant accuracy improvements through systematic feature engineering, statistical transformations, and model selection techniques.

**Key Achievement:** Improved model R² from 0.432 to 0.641 (48% improvement) through Box-Cox transformations and forward stepwise selection.

## 🎯 Objectives

1. Develop interpretable regression model for housing price prediction
2. Apply statistical transformations to meet model assumptions
3. Address multicollinearity through systematic variable selection
4. Validate model performance through diagnostic testing

## 📈 Results Summary

| Metric | Initial Model | Final Model | Improvement |
|--------|--------------|-------------|-------------|
| **R²** | 0.432 | 0.641 | +48% |
| **Model Validity** | Violated assumptions | Met assumptions | ✓ |
| **Predictors** | 14 variables | 13 variables | Simplified |
| **VIF Issues** | Multiple | Reduced | Improved |

## 🔬 Methodology

### 1. Feature Engineering
- Created `Qual_x_Area` interaction term (OverallQual × GrLivArea)
- Engineered `Amenities` composite variable from 4 binary indicators:
  - Garage presence
  - Central AC/heating
  - Basement
  - Fireplace

### 2. Data Transformation (Box-Cox Method)
Applied log transformations to address:
- **Response variable:** SalePrice (right-skewed distribution)
- **Predictors:** LotArea, X1stFlrSF (non-linear relationships)

**Impact:**
- Improved normality of residuals
- Addressed heteroscedasticity
- Enhanced linearity of relationships

### 3. Variable Selection
**Method:** Forward stepwise selection based on Akaike Information Criterion (AIC)

**Process:**
1. Started with intercept-only model
2. Added predictors sequentially by AIC improvement
3. Compared with backward selection and all-subsets (results identical)

**Final Predictors (13 variables):**
- Quality metrics: OverallQual, OverallCond
- Size variables: log(LotArea), GrLivArea, log(X1stFlrSF), X2ndFlrSF
- Time factors: YearBuilt, YearRemodAdd
- Features: Amenities, BedroomAbvGr, FullBath, HalfBath
- Interaction: Qual_x_Area

### 4. Multicollinearity Assessment
**Tool:** Variance Inflation Factor (VIF) analysis

**Results:**
- Some VIF values remained >5 (expected for interaction terms)
- Slight improvement after variable selection
- Acceptable given model interpretability and performance

### 5. Model Validation
**Diagnostic Tests:**
- ✅ Residuals vs Fitted: Random scatter (linearity confirmed)
- ✅ Normal Q-Q Plot: Residuals approximately normal
- ✅ Scale-Location: Constant variance achieved
- ✅ Residuals vs Leverage: No highly influential outliers

## 📁 Project Structure

```
housing-price-prediction/
├── stats101a_project.Rmd          # Main analysis notebook
├── final_report.pdf               # Complete project report
├── data/
│   ├── train.csv                  # Training dataset (7,000 obs)
│   └── test.csv                   # Test dataset (3,000 obs)
├── plots/
│   ├── diagnostic_plots.png       # Model diagnostics
│   ├── scatterplot_matrix.png    # Variable relationships
│   └── transformation_plots.png   # Before/after transformations
└── README.md
```

## 🛠️ Technologies & Methods

**Programming:** R  
**Packages:** ggplot2, dplyr, MASS (Box-Cox)  
**Statistical Methods:**
- Multiple Linear Regression
- Box-Cox Transformation
- Forward Stepwise Selection (AIC)
- Variance Inflation Factor (VIF) Analysis
- Diagnostic Testing (Residual Analysis)

## 📊 Key Visualizations

### 1. Diagnostic Plots Comparison

**Before Transformation:**
- Heteroscedasticity evident (funnel pattern)
- Non-normal residuals (Q-Q plot deviation)
- Non-constant variance

**After Transformation:**
- Random residual scatter
- Residuals follow normal distribution
- Constant variance achieved

### 2. Variable Relationships
- Scatterplot matrix revealing correlations
- Strong positive association between quality metrics and price
- Non-linear relationships addressed through transformations

## 🎓 Statistical Concepts Demonstrated

### Box-Cox Transformation
**Purpose:** Find optimal power transformation to normalize data and stabilize variance

**Formula:** y^(λ) where λ is estimated from data
- λ = 0 → log transformation
- λ = 1 → no transformation
- λ = 0.5 → square root transformation

**Application:** Suggested log transformations for SalePrice, LotArea, and X1stFlrSF

### Akaike Information Criterion (AIC)
**Purpose:** Balance model fit vs. complexity

**Formula:** AIC = -2log(L) + 2k
- L = likelihood
- k = number of parameters

**Lower AIC = Better model** (accounts for overfitting)

### Variance Inflation Factor (VIF)
**Purpose:** Detect multicollinearity among predictors

**Interpretation:**
- VIF < 5: Acceptable
- VIF 5-10: Moderate multicollinearity
- VIF > 10: Severe multicollinearity

**Action:** Remove or combine highly correlated predictors

## 💡 Real-World Applications

This model can inform:

1. **Real Estate Valuation**
   - Automated property appraisal
   - Fair market value estimation
   
2. **Investment Decisions**
   - Identifying undervalued properties
   - ROI prediction for renovations
   
3. **Urban Planning**
   - Understanding price drivers
   - Neighborhood development strategies

4. **Homebuyers**
   - Fair price assessment
   - Feature prioritization

## 🔍 Insights & Findings

### Positive Price Drivers
- Overall quality rating (strongest predictor)
- Living area (square footage)
- Lot size
- Recent construction/remodeling
- Additional amenities

### Notable Patterns
- Strong interaction effect between quality and area (Qual_x_Area)
- Log transformations revealed non-linear price relationships
- Amenities bundled impact exceeds individual feature effects

### Model Limitations
- OverallCond showed negative coefficient (likely multicollinearity)
- Some VIF values remained elevated for interaction terms
- Model explains 64% of variance (36% from unmeasured factors)

## 📚 Learning Outcomes

**Technical Skills:**
- Advanced regression modeling
- Statistical transformation techniques
- Model selection and validation
- Diagnostic interpretation

**Statistical Thinking:**
- Assumption checking and remediation
- Multicollinearity detection and handling
- Balancing model complexity vs. interpretability
- Translating statistical findings to practical insights

## 👥 Team

Faith Bettis, Nicolle Jacquelyn, Hurmoni Leah Vicencio, Darren Suwandi, **Prisha Chowdhury**

UCLA STATS 101A Final Project (Fall 2024)

## 📄 Full Report

[[Link to final_report.pdf](https://github.com/PrishaChowdhury/STATS-101A/edit/main/README.md#:~:text=Housing-,Prices_,-101A%20Project.pdf)
] - Complete methodology, results, and visualizations

## 🎯 Future Enhancements

**Potential Improvements:**
- Incorporate neighborhood categorical variables
- Engineer additional interaction terms
- Compare with regularization methods (Ridge, Lasso)
- Validate on completely held-out test set
- Explore non-linear models (GAMs, Random Forests) for comparison

## 📧 Contact

**Prisha Chowdhury**  
UCLA Data Theory Student  
Email: prisha4@ucla.edu  
LinkedIn: [linkedin.com/in/prisha-chowdhury](https://linkedin.com/in/prisha-chowdhury-b47b0128b)

---

## 🔑 Key Takeaways

✅ **Statistical rigor matters:** Validating assumptions isn't optional  
✅ **Transformations are powerful:** Simple log transforms improved R² by 48%  
✅ **Feature engineering adds value:** Interaction terms captured important relationships  
✅ **Model selection requires balance:** Parsimony vs. explanatory power  
✅ **Domain knowledge enhances modeling:** Understanding housing markets informed feature choices

---

*This project demonstrates the application of classical statistical methods to real-world prediction problems, emphasizing interpretability and statistical validity alongside predictive performance.*
