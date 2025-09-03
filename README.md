# Airbnb Price Prediction: Predictive Analytics Case Study

A comprehensive predictive modeling project analyzing Airbnb listing prices using multiple statistical and machine learning approaches in R.

## Project Overview

This project systematically evaluates eight different modeling approaches to predict Airbnb listing prices, from traditional statistical methods to machine learning algorithms. The analysis demonstrates a complete data science workflow including data preprocessing, exploratory analysis, feature engineering, model selection, and business interpretation.

## Business Context

Airbnb hosts need data-driven pricing strategies to maximize revenue while remaining competitive. This analysis identifies the key factors that drive pricing and provides quantifiable insights for hosts and the platform.

## Dataset

- **Source**: Airbnb listing data
- **Final Dataset**: 886 observations after cleaning
- **Variables**: 36 features after preprocessing (25 original + dummy variables)
- **Target Variable**: Price per night (USD)

## Methodology

### Data Preprocessing
- **Missing Data Handling**: Listwise deletion approach
- **Outlier Treatment**: IQR method applied to bedroom variable
- **Data Quality**: Removed negative price entries
- **Feature Engineering**: One-hot encoding for categorical variables
  - Property type (Apartment, House, Condominium, etc.)
  - Room type (Entire home, Private room, Shared room)
  - Cancellation policy (Flexible, Moderate, Strict)
  - Host verification status

### Exploratory Data Analysis
- Distribution analysis of numeric variables
- Correlation matrix examination
- Geographic price mapping
- Property characteristic analysis
- Room type and amenity impact assessment

### Model Development and Comparison

Implemented eight distinct modeling approaches:

1. **Full Model**: All 35 predictors without selection
2. **Significant Variables Only**: Variables with p < 0.05
3. **Manual Selection Model**: Iterative removal of high p-value predictors
4. **Forward Selection**: Stepwise forward variable selection
5. **Backward Selection**: Stepwise backward elimination
6. **Exhaustive Search**: All possible variable combinations
7. **Linear Regression with Cross-Validation**: 10-fold CV implementation
8. **K-Nearest Neighbors**: Non-parametric approach with k=23

## Results

### Model Performance Comparison

| Model Approach | Adjusted R² | RMSE | AIC | Variables |
|---------------|-------------|------|-----|-----------|
| **Linear Regression (CV)** | **39.84%** | **67.16** | N/A | 13 |
| Forward Selection | 39.84% | 67.16 | 5989.34 | 13 |
| Manual Selection | 39.75% | 67.14 | 5995.94 | 19 |
| Backward Selection | 39.79% | 67.38 | 5991.73 | 15 |
| Exhaustive Search | 38.85% | 67.36 | 5994.10 | 9 |
| Full Model | 38.95% | N/A | N/A | 35 |
| Significant Variables Only | 37.56% | N/A | N/A | 8 |
| K-Nearest Neighbors | N/A | 73.09 | N/A | All |

### Final Model Performance
- **Selected Model**: Linear Regression with 10-fold Cross-Validation
- **Adjusted R²**: 39.84% (explains ~40% of price variation)
- **RMSE**: $67.16 (average prediction error)
- **Residual Standard Error**: $64.99
- **F-statistic**: 28.15 (p < 2.2e-16, highly significant)

### Key Predictive Variables

The final model identified 13 significant predictors:

1. **amenities_count** (+$2.14 per additional amenity)
2. **accommodates** (guest capacity)
3. **bedrooms** (number of bedrooms)
4. **bathrooms** (number of bathrooms)
5. **property_typeBed_&_Breakfast** (negative coefficient - lower prices)
6. **room_typeEntire_home/apt** (premium for entire properties)
7. **property_typeHouse** (house premium)
8. **host_since** (host experience factor)
9. **property_typeCondominium** (condo premium)
10. **property_typeTownhouse** (townhouse premium)
11. **maximum_nights** (stay duration limits)
12. **extra_people** (additional guest fees - negative impact)
13. **cancellation_policystrict** (strict policy - negative impact)

## Business Insights

### For Airbnb Hosts:
- **Amenity Investment**: Each additional amenity increases price by $2.14
- **Capacity Optimization**: Larger accommodations command premium pricing
- **Property Type Strategy**: Houses and condominiums outperform bed & breakfasts
- **Policy Flexibility**: Strict cancellation policies may reduce pricing power
- **Experience Value**: Established hosts can command higher prices

### For Platform Strategy:
- **Pricing Algorithms**: Model can inform dynamic pricing recommendations
- **Host Education**: Clear ROI metrics for property improvements
- **Market Segmentation**: Different pricing strategies for property types

## Technical Implementation

### Tools and Libraries
- **R Version**: 4.0+
- **Core Packages**: tidyverse, caret, ggplot2
- **Statistical Analysis**: MASS, leaps, corrplot
- **Evaluation**: Metrics package for performance assessment

### Model Validation
- **Cross-Validation**: 10-fold CV for robust performance estimation
- **Residual Analysis**: Confirmed model assumptions
- **Diagnostic Plots**: Residuals vs fitted, Q-Q plots for normality

## File Structure

```
├── 01-data-cleaning-eda.Rmd            # Data preprocessing and exploratory analysis
├── 02-model-development.Rmd            # Comprehensive model comparison and selection  
├── 03-final-predictive-models.Rmd      # Final model implementation with cross-validation
├── airbnb1.csv                         # Dataset
├── final_presentation.pdf            # Project presentation
└── results/                            # Analysis outputs and findings
```

## Key Findings Summary

1. **Systematic Approach Works**: Forward selection and cross-validation provided optimal results
2. **Amenities Drive Value**: Strongest predictor with quantifiable ROI
3. **Property Type Matters**: Clear hierarchy in pricing potential
4. **Model Generalizability**: Cross-validation ensures robust predictions
5. **Business Actionability**: Findings translate directly to pricing strategies

## Methodology Strengths

- **Comprehensive Model Comparison**: Eight distinct approaches tested
- **Statistical Rigor**: Proper cross-validation and assumption checking
- **Business Context**: Analysis tied to actionable recommendations
- **Reproducible Workflow**: Complete documentation of process
- **Performance Transparency**: All models evaluated with consistent metrics

## Future Extensions

- Seasonal pricing analysis incorporating temporal patterns
- Geographic clustering for location-based pricing
- Sentiment analysis of reviews as predictive features
- Ensemble methods combining multiple approaches
- Real-time pricing optimization framework

## Academic Context

- **Course**: Business Analytics
- **Focus**: Predictive Modeling and Statistical Analysis
- **Methodology**: End-to-end data science project workflow
- **Skills Demonstrated**: R programming, statistical modeling, business analysis

This project demonstrates the application of rigorous analytical methods to real-world business problems, combining technical proficiency with strategic business thinking.
