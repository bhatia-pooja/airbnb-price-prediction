# Results Directory

This folder contains the outputs, findings, and key deliverables from the Airbnb price prediction analysis.

## Contents Overview

### Model Performance Summary

The analysis systematically compared eight different modeling approaches:

| Model | Adjusted R² | RMSE | AIC | Key Characteristics |
|-------|-------------|------|-----|-------------------|
| Linear Regression (CV) | **39.84%** | **67.16** | N/A | **Selected model** - Best generalization |
| Forward Selection | 39.84% | 67.16 | 5989.34 | Stepwise variable selection |
| Manual Selection | 39.75% | 67.14 | 5995.94 | Iterative p-value removal |
| Backward Selection | 39.79% | 67.38 | 5991.73 | Stepwise elimination |
| Exhaustive Search | 38.85% | 67.36 | 5994.10 | All combinations tested |
| Full Model | 38.95% | N/A | N/A | All variables included |
| Significant Variables | 37.56% | N/A | N/A | p < 0.05 only |
| K-Nearest Neighbors | N/A | 73.09 | N/A | k = 23 optimal |

## Key Research Findings

### Primary Predictors of Airbnb Price

1. **amenities_count**: +$2.14 per additional amenity
2. **accommodates**: Guest capacity drives premium pricing
3. **bedrooms**: Number of bedrooms significant predictor
4. **bathrooms**: Bathroom count impacts pricing
5. **property_type**: Houses > Condos > Apartments > B&Bs
6. **room_type**: Entire homes command premium over private/shared rooms
7. **host_since**: Experienced hosts can charge more
8. **maximum_nights**: Stay duration policies affect pricing
9. **extra_people**: Additional guest fees negatively impact base price
10. **cancellation_policy**: Strict policies reduce pricing power

### Statistical Model Performance

**Final Model Specifications:**
- **Model Type**: Linear Regression with 10-fold Cross-Validation
- **Variables**: 13 predictors selected through forward selection
- **Adjusted R²**: 39.84% (explains ~40% of price variation)
- **RMSE**: $67.16 average prediction error
- **F-statistic**: 28.15 (p < 2.2e-16) - highly significant
- **Residual Standard Error**: $64.99

### Model Diagnostics

**Assumption Validation:**
- **Linearity**: Confirmed through residual plots
- **Homoscedasticity**: Random scatter in residuals vs fitted
- **Normality**: Q-Q plots show reasonable normal distribution
- **Independence**: Cross-validation supports generalizability

**Outlier Analysis:**
- Some extreme high-price properties identified
- IQR method effectively handled bedroom outliers
- Model robust to remaining outliers

## Business Intelligence Summary

### Strategic Recommendations

**For Hosts:**
1. **Amenity Investment**: Highest ROI predictor - $2.14 return per amenity
2. **Capacity Optimization**: Maximize guest accommodation within space constraints
3. **Property Positioning**: Market houses/condos as premium offerings
4. **Policy Flexibility**: Consider moderate vs strict cancellation policies
5. **Experience Marketing**: Leverage host tenure as value proposition

**For Platform (Airbnb):**
1. **Dynamic Pricing**: Integrate model predictors into pricing algorithms
2. **Host Education**: Provide ROI calculations for property improvements
3. **Market Segmentation**: Different strategies for property types
4. **Quality Metrics**: Emphasize amenities in listing optimization

### Market Insights

**Price Drivers Ranked by Impact:**
1. Amenities count (strongest predictor)
2. Property size (accommodates, bedrooms, bathrooms)
3. Property type classification
4. Room type (entire vs shared)
5. Host experience level
6. Policy flexibility

**Property Type Analysis:**
- **Houses**: Command highest premiums
- **Condominiums**: Strong performance in urban markets
- **Apartments**: Moderate pricing tier
- **Bed & Breakfasts**: Typically lower price points

## Methodology Validation

### Model Selection Justification

**Why Linear Regression with CV Won:**
- Highest adjusted R² among interpretable models
- Robust cross-validation performance
- Clear coefficient interpretation for business use
- Met all statistical assumptions
- Optimal bias-variance tradeoff

**Alternative Model Assessment:**
- **KNN**: Higher RMSE, less interpretable
- **Full Model**: Overfitting risk, unnecessary complexity
- **Exhaustive Search**: Fewer variables, lower R²
- **Stepwise Methods**: Similar performance, less robust validation

### Data Quality Assessment

**Dataset Characteristics:**
- **Original Size**: Unknown (missing data present)
- **Final Dataset**: 886 observations
- **Completeness**: 100% after listwise deletion
- **Representativeness**: Captures diverse property types and price ranges
- **Quality Controls**: Negative prices removed, outlier treatment applied

## Technical Implementation Notes

### Cross-Validation Framework
- **Method**: 10-fold cross-validation
- **Purpose**: Prevent overfitting, ensure generalizability
- **Result**: Consistent performance across folds
- **Validation**: RMSE stable across validation sets

### Variable Selection Process
1. **Forward Selection**: Systematic addition of predictors
2. **AIC Optimization**: Balance fit quality and complexity
3. **Statistical Significance**: p-value thresholds maintained
4. **Business Relevance**: Economically interpretable coefficients

## Limitations and Considerations

### Model Limitations
- **Temporal Factors**: No seasonal or time-based pricing captured
- **Geographic Granularity**: Location effects not fully modeled
- **External Factors**: Market conditions, events not included
- **Non-linear Relationships**: Linear model may miss complex interactions

### Data Constraints
- **Sample Size**: 886 observations after cleaning
- **Missing Data**: Listwise deletion may introduce bias
- **Feature Limitations**: Some potentially relevant variables unavailable

## Future Research Directions

### Model Enhancements
1. **Ensemble Methods**: Combine multiple algorithms
2. **Time Series Analysis**: Seasonal pricing patterns
3. **Geographic Modeling**: Location clustering and spatial analysis
4. **Feature Engineering**: Interaction terms and polynomial features

### Business Applications
1. **Real-time Pricing**: Dynamic price optimization
2. **Revenue Management**: Demand-based pricing strategies
3. **Market Analysis**: Competitive positioning insights
4. **Investment Guidance**: Property acquisition recommendations

---

*This analysis demonstrates systematic application of statistical methods to business problems, providing both technical rigor and actionable insights for stakeholders.*
