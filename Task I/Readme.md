# Linear Regression House Price Predictor

This project builds and evaluates a Linear Regression model for predicting California house prices. It follows a basic machine learning workflow: data loading, EDA, preprocessing, train/test split, model training, evaluation, visualization, and reporting.

## Files

- `task1_ml_linear_regression.ipynb` - Main notebook template with the full workflow.
- `Task1_ML_Linear_Regression_results.ipynb` - Executed notebook with results and outputs.
- `Task1_ML_Linear_Regression_Report.pdf` - Short 3-page project report.
- `dataset/housing.csv` - California Housing CSV dataset.

## Dataset

The project uses the California Housing dataset. In the executed notebook, the dataset was uploaded as `housing.csv`.

After preprocessing:

- Rows: 20,640
- Columns: 13
- Target: `MedHouseVal`
- Train rows: 16,512
- Test rows: 4,128

## Model

The model used is `LinearRegression` from scikit-learn.

Features include:

- Location features such as longitude and latitude
- Housing age
- Population
- Median income
- Engineered average room, bedroom, and occupancy features
- Encoded ocean proximity categories

## Results

| Metric | Value | Meaning |
|---|---:|---|
| MAE | 0.538797 | About $53,880 average absolute error |
| RMSE | 0.812622 | About $81,262 error with larger errors penalized |
| R2 Score | 0.496070 | About 49.6% test-set variance explained |

## How to Run

1. Open `task1_ml_linear_regression.ipynb` in Google Colab or Jupyter Notebook.
2. Run the cells from top to bottom.
3. Upload `dataset/housing.csv` when the notebook asks for a CSV file.
4. Review the EDA charts, model metrics, prediction plots, and saved model output.
5. Run the final report cell if a PDF report needs to be regenerated.

## Conclusion

Linear Regression gave a simple and interpretable baseline for house price prediction. Median income and location-based features were important predictors. The model explains about half of the variation in the test data, so future improvement could come from stronger feature engineering, cross-validation, Ridge/Lasso Regression, Random Forest, or Gradient Boosting models.
