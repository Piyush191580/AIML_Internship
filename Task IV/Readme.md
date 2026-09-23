# AI/ML Task 4: Classification Models, Evaluation Metrics & Handling Imbalanced Data

This task moves from regression to classification. The goal was to build a binary classifier for customer churn prediction and evaluate it properly using metrics beyond accuracy, since the dataset turned out to be imbalanced.

## Files

- `Task4_Classification_Churn.ipynb` - Executed notebook with full results and outputs.
- `Task4_Report.pdf` - 2-page report covering metric selection, imbalance handling, and final model decision.
- `WA_Fn-UseC_-Telco-Customer-Churn.csv` - Telco Customer Churn dataset.

## Dataset

Telco Customer Churn dataset.

- Rows: 7,043
- Columns: 21 (customerID dropped before training)
- Target: `Churn` (Yes/No)
- Train rows: 5,634
- Test rows: 1,409

Class distribution:

- No Churn: 5,174 (73.5%)
- Churn: 1,869 (26.5%)

The dataset is imbalanced, which is the main reason this task focuses on metrics other than accuracy.

## What Was Done

- Cleaned the dataset (dropped customerID, fixed TotalCharges blanks)
- One-hot encoded categorical columns
- Checked class balance before training anything
- Trained a baseline Logistic Regression model
- Built a confusion matrix and classification report
- Plotted the ROC curve and calculated AUC
- Handled class imbalance using `class_weight="balanced"`
- Compared Logistic Regression against a Decision Tree Classifier

## Confusion Matrix (Baseline Logistic Regression)

|  | Predicted No Churn | Predicted Churn |
|---|---:|---:|
| Actual No Churn | 925 | 110 |
| Actual Churn | 162 | 212 |

Out of 374 customers who actually churned, the baseline model caught 212 and missed 162.

## Why Accuracy Alone Was Not Enough

With 73.5% of customers not churning, a model could score around 73% accuracy by just predicting "No Churn" every time. The baseline model got 80.7% accuracy, which looks fine on the surface, but its recall on the churn class was only 0.57, meaning it missed almost half of the actual churners.

## Imbalance Handling Results

| Model | Precision (Churn) | Recall (Churn) | F1 (Churn) | Accuracy |
|---|---:|---:|---:|---:|
| Logistic Regression (baseline) | 0.66 | 0.57 | 0.61 | 0.807 |
| Logistic Regression (balanced) | 0.51 | 0.79 | 0.62 | 0.740 |

Using `class_weight="balanced"` pushed recall up from 0.57 to 0.79, meaning the model catches far more at-risk customers. Precision dropped as a tradeoff, and overall accuracy went down too, but for churn prediction, recall on the churn class matters more than raw accuracy.

## Model Comparison Table

| Model | Accuracy | Precision | Recall | F1-Score | AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression (baseline) | 0.807 | 0.66 | 0.57 | 0.61 | 0.8418 |
| Logistic Regression (balanced) | 0.740 | 0.51 | 0.79 | 0.62 | 0.8414 |
| Decision Tree (default) | 0.726 | 0.48 | 0.48 | 0.48 | 0.6465 |

The Decision Tree hit 99.8% accuracy on training data but only 72.6% on test data, a clear overfitting case. Its AUC of 0.6465 was also much lower than either Logistic Regression version.

## Best Model

**Logistic Regression with `class_weight="balanced"`**

Selected because:

- Catches 79% of actual churners vs 57% for the baseline
- AUC stayed almost the same (0.8414 vs 0.8418), so overall ranking ability did not get worse
- No overfitting, unlike the Decision Tree
- Missing a churner is more costly to the business than a false alarm, so recall was prioritized

## How to Run

1. Open `Task4_Classification_Churn.ipynb` in Google Colab or Jupyter.
2. Run all cells top to bottom.
3. Upload `WA_Fn-UseC_-Telco-Customer-Churn.csv` when prompted.
4. Check the confusion matrix and classification report after Step 9.
5. Check the ROC curve and AUC in Step 10, and the imbalance comparison in Step 11.

## Conclusion

Task 4 showed that the model with the highest accuracy is not always the most useful one. The Decision Tree had high training accuracy but failed badly on test data, and the baseline Logistic Regression had decent accuracy but missed a lot of actual churners. Using `class_weight="balanced"` made the model better suited for the real goal of catching at-risk customers, even though its accuracy number was lower. Choosing the right metric for the problem turned out to be just as important as choosing the right model.
