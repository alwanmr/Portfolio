# Housing Value Prediction with Regularized Regression

**Project type:** Supervised Machine Learning — Regression  
**Tools:** Python, Pandas, Scikit-learn, Jupyter Notebook  
**Models:** Ridge Regression, LASSO Regression, Multiple Linear Regression

## Overview

This project explores how modeling decisions affect housing-value prediction. Using the Boston Housing dataset, the analysis compares regularized regression models, tests whether removing a highly correlated feature improves prediction, and investigates the effect of excluding target observations at an apparent upper boundary.

The project is presented as an analytical case study rather than a claim that the model is ready for real-world property valuation.

## Problem Statement

Can housing value be predicted from property and neighborhood characteristics, and how do feature selection, target treatment, and model choice affect predictive performance?

The target variable is `medv`, the median value of owner-occupied homes. The dataset contains 506 observations, 13 predictor variables, and one target variable.

## Approach

1. **Data understanding and EDA** — reviewed dataset structure, data quality, target distribution, and feature relationships.
2. **Baseline modeling** — standardized predictors and compared Ridge and LASSO using validation RMSE for model selection.
3. **Feature-selection experiment** — tested whether removing `rad`, which is strongly correlated with `tax` (approximately 0.91), improved validation performance.
4. **Target-treatment experiment** — assessed the effect of excluding observations with `medv >= 50`, motivated by dataset documentation describing an apparent upper-bound censoring issue.
5. **Model comparison** — compared Multiple Linear Regression, Ridge, and LASSO on the treated target range.

## Key Findings

- **Ridge and LASSO had nearly identical baseline performance.** On the original test set, Ridge achieved RMSE 4.3058 and LASSO achieved RMSE 4.3021.
- **Removing `rad` did not improve validation performance.** The best full-feature model had validation RMSE 4.6267, compared with 4.7006 after removing `rad`. The full feature set was retained.
- **Target treatment improved the reported metrics but narrowed target coverage.** Excluding observations with `medv >= 50` reduced the dataset from 506 to 490 observations. For the treated Ridge model, test RMSE was 4.0052, MAE was 3.0258, and MAPE was 15.8895%.
- **Regularization was not automatically superior.** In the treated-data comparison, LASSO and Multiple Linear Regression produced practically identical results. Ridge had higher RMSE but lower MAE and MAPE.

## Interpretation and Limitations

The target-treatment experiment is a sensitivity analysis, not proof that observations at the upper boundary are invalid outliers. Excluding these observations means the resulting model is not trained on that high-end target range, which limits how confidently it can be applied to high-value properties.

The Boston Housing dataset also has known contextual and historical limitations. Results from this dataset should not be treated as evidence of real-world market readiness. In a practical setting, model selection would require suitable contemporary data, validation against the intended population, and domain review.

## Conclusion

The most consequential lesson was not that one algorithm universally outperformed the others. Instead, the experiments showed the importance of validating assumptions, comparing approaches on held-out data, and interpreting performance metrics alongside target coverage.

The model should be viewed as an **initial analytical reference for exploring housing-value prediction**, not as a replacement for professional property valuation.

## Project Materials

- **Presentation:** To be added
- **Notebook:** To be added
- **Dataset:** Use an authorized source; dataset files are not included in this folder yet.
