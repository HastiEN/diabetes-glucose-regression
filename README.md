# Diabetes Glucose Regression Using Machine Learning Regressors

**Machine Learning - First Mini Project**

## Abstract

This project compares multiple regression models for predicting blood glucose
level using the Pima Indians Diabetes dataset. The workflow includes exploratory
data analysis, missing-value handling, KNN imputation, outlier treatment,
train/test splitting, regression model training, evaluation with MSE and R2,
and feature-importance analysis.

## Objective

The objective is to predict a continuous medical value, `Glucose`, from other
medical measurements. Although the original dataset includes a binary diabetes
classification label named `Outcome`, this project removes that label and
treats the task as a regression problem.

## Dataset

The dataset contains 768 samples and 9 original columns:

- Pregnancies
- Glucose
- BloodPressure
- SkinThickness
- Insulin
- BMI
- DiabetesPedigreeFunction
- Age
- Outcome

The target variable for this project is `Glucose`.

## Data Cleaning and Preprocessing

Some columns contain zero values that are not medically meaningful. For this
reason, zero values in `BloodPressure`, `BMI`, `Glucose`, `Insulin`, and
`SkinThickness` are treated as missing values.

The preprocessing workflow includes:

1. Drop the `Outcome` column.
2. Replace invalid zero values with `NaN`.
3. Scale the data with `StandardScaler`.
4. Apply `KNNImputer` with five neighbors.
5. Convert the imputed values back to the original scale.
6. Detect outliers with the IQR rule.
7. Re-impute outlier positions with KNN.

## Modeling

The following regression models are compared:

- Linear Regression
- Ridge Regression
- Lasso Regression
- Polynomial Regression with degree 2
- KNN Regression
- Support Vector Regression with RBF kernel
- Decision Tree Regression
- Random Forest Regression
- Bayesian Ridge Regression

Each model is evaluated on the test set using:

- Mean Squared Error (MSE)
- R2 score

## Final Recorded Results

| Model | MSE | R2 |
|---|---:|---:|
| Linear Regression | 551.3952 | 0.4521 |
| Ridge Regression | 551.4030 | 0.4521 |
| Lasso Regression | 551.6126 | 0.4518 |
| Polynomial Regression | 537.3451 | 0.4660 |
| KNN Regression | **516.3685** | **0.4869** |
| SVR | 535.1923 | 0.4682 |
| Decision Tree Regression | 532.4813 | 0.4709 |
| Random Forest Regression | 556.1475 | 0.4473 |
| Bayesian Ridge Regression | 547.9070 | 0.4555 |

## Conclusion

The best recorded model was KNN Regression, which achieved the lowest MSE and
highest R2 score. Decision Tree Regression and SVR also performed competitively.

The linear models produced similar results, suggesting that part of the
relationship between the predictors and glucose level is approximately linear,
but nonlinear models can capture additional structure.

The overall R2 values are moderate, which means glucose prediction remains
challenging using only the available features. Future work may include
hyperparameter tuning, cross-validation, additional feature engineering, and
more careful comparison of imputation strategies.
