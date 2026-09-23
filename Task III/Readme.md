
# AI/ML Task 3: Model Validation, Overfitting Control & Hyperparameter Tuning

This task builds on Task 2 by adding proper model validation, overfitting analysis, and hyperparameter tuning using GridSearchCV. The goal was to move from just picking the best model to actually understanding *why* it performs well and whether it will hold up on new data.

## Files

- `Task3_Model_Validation_Tuning.ipynb` - Executed notebook with full results and outputs.
- `Task3_Report.pdf` - 2-page report covering overfitting analysis, tuning approach, and final model justification.
- `task3_best_house_price_model.pkl` - Saved best model (Tuned Random Forest).
- `task3_scaler.pkl` - Saved StandardScaler used during preprocessing.

## Dataset

Same California Housing dataset from Tasks 1 and 2, used as-is for fair comparison.

- Rows: 20,640
- Features after engineering: 14 (same as Task 2, includes `RoomsPerPerson` and `BedroomRatio`)
- Target: `HousePrice` (median house value)
- Train rows: 16,512
- Test rows: 4,128

## What Was Done

- Detected overfitting by comparing train vs test RMSE for all models
- Applied 5-fold cross-validation for more reliable performance estimates
- Tuned hyperparameters for Decision Tree, Ridge, and Random Forest using GridSearchCV
- Compared tuned models against Task 2 baselines
- Selected and saved the best model with justification

## Overfitting Analysis

The default Decision Tree was the clearest example of overfitting in this experiment:

| Model | Train RMSE | Test RMSE | Gap |
|---|---:|---:|---:|
| Linear Regression | 66,959 | 67,385 | +426 |
| Ridge (alpha=1) | 66,959 | 67,385 | +426 |
| Decision Tree (default) | 0 | 72,949 | +72,949 |
| Random Forest (default) | 18,356 | 49,643 | +31,286 |

The Decision Tree memorised the training data completely (train RMSE = 0) but performed worse than Linear Regression on the test set, which is a textbook overfitting case.

## Cross-Validation Results (5-fold)

| Model | Mean CV RMSE | Std |
|---|---:|---:|
| Linear Regression | 67,557 | 3,014 |
| Ridge (alpha=1) | 67,556 | 3,012 |
| Decision Tree (default) | 70,028 | 1,670 |
| Random Forest (default) | 48,890 | 1,136 |

Random Forest had both the lowest mean CV RMSE and the lowest standard deviation, meaning it was the most consistent model across folds.

## Hyperparameter Tuning Results

**Decision Tree — GridSearchCV**
- Parameters searched: `max_depth`, `min_samples_split`, `min_samples_leaf`
- Best params: `max_depth=10`, `min_samples_leaf=5`, `min_samples_split=20`
- Best CV RMSE: 58,998

**Ridge Regression — GridSearchCV**
- Parameters searched: `alpha` in [0.01, 0.1, 1.0, 10.0, 50.0, 100.0, 500.0]
- Best params: `alpha=50.0`
- Best CV RMSE: 67,534

**Random Forest — GridSearchCV**
- Parameters searched: `n_estimators`, `max_depth`, `max_features`
- Best params: `n_estimators=200`, `max_depth=None`, `max_features=sqrt`
- Best CV RMSE: 49,288

## Model Comparison Table

| Model | MAE | RMSE | R² Score |
|---|---:|---:|---:|
| Random Forest (Task-3 tuned) | 32,901 | 49,302 | 0.8145 |
| Decision Tree (Task-3 tuned) | 40,721 | 61,265 | 0.7136 |
| Linear Regression (Task-3 baseline) | 48,243 | 67,385 | 0.6535 |
| Ridge Regression (Task-3 tuned) | 48,221 | 67,414 | 0.6532 |
| Random Forest (Task-2) | ~33,916 | ~51,562 | 0.7971 |

The tuned Random Forest improved the Task-2 R² from 0.797 to 0.814.

## Best Model

**Tuned Random Forest**

- MAE: 32,901 (~$32,900 average error)
- RMSE: 49,302 (~$49,300)
- R² Score: 0.8145

Selected because it had the lowest test RMSE, highest R², and the most stable CV scores across all folds. Overfitting was controlled through `max_features=sqrt` and using 200 estimators, and hyperparameters were selected based on cross-validated performance rather than training accuracy.

## How to Run

1. Open `Task3_Model_Validation_Tuning.ipynb` in Google Colab or Jupyter.
2. Run all cells top to bottom.
3. Upload `housing.csv` when prompted (or the notebook uses the scikit-learn built-in).
4. Check overfitting analysis in Step 5, CV results in Step 6, and tuning results in Steps 7–9.
5. The best model is saved automatically as `task3_best_house_price_model.pkl`.

## Conclusion

Task 3 showed that a good test score on one split doesn't mean much on its own. The Decision Tree scored 0 on training data and still lost to Linear Regression on the test set, which is a good reminder of why validation matters. Cross-validation and GridSearchCV together give a much more reliable picture of how a model will actually behave on unseen data. The tuned Random Forest ended up as the best model and a solid starting point for any further work.
