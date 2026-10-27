# Diabetes Linear Regression

This project is a **simple educational regression example** designed to practice the basic workflow of Machine Learning using the Diabetes dataset from `scikit-learn`.

The main goal is not to build a highly accurate predictive model, but to understand how a regression model is trained, how predictions are generated, and how different regression metrics should be interpreted.

## Dataset

The project uses the built-in **Diabetes dataset** from `scikit-learn`.

The dataset contains:

- **442 samples**
- **10 numerical features**
- A continuous target representing a quantitative measure of diabetes disease progression one year after baseline

The available features are:

`age`, `sex`, `bmi`, `bp`, `s1`, `s2`, `s3`, `s4`, `s5`, and `s6`.

## Feature Analysis

The correlation of each feature with the target was examined before building the model.

Among the available features, the strongest correlations with the target were:

- `bmi` ≈ **0.586**
- `s5` ≈ **0.566**
- `bp` ≈ **0.441**
- `s4` ≈ **0.430**

For this simple educational regression experiment, only **BMI** was selected as the predictor.

Therefore, the model is intentionally a **single-feature Linear Regression model**.

## Model

The model used in this project is:

```python
LinearRegression()
```

The relationship can be represented approximately as:

```text
Disease Progression ≈ 998.6 × BMI + 152.0
```

The dataset was divided into training and testing sets using an 80/20 split:

```python
train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

This produced **89 test samples**.

## Evaluation Metrics

Three common regression metrics were evaluated:

| Metric | Result |
|---|---:|
| Mean Squared Error (MSE) | **4061.83** |
| Mean Absolute Error (MAE) | **52.26** |
| R² Score | **0.233** |

### Mean Squared Error — MSE

```text
MSE = 4061.83
```

MSE measures the average squared difference between the actual and predicted values.

Because the errors are squared, large prediction errors are penalized more heavily.

In this experiment, the relatively large MSE indicates that the model still makes substantial prediction errors.

### Mean Absolute Error — MAE

```text
MAE = 52.26
```

MAE is easier to interpret because it represents the average absolute distance between predictions and actual values.

An MAE of approximately **52** means that, on average, the model predictions differ from the actual disease-progression values by about 52 units.

This is relatively large for this dataset.

### R² Score

```text
R² = 0.233
```

R² measures how much of the variability in the target can be explained by the model.

An R² of approximately **0.23** means that this simple regression model explains only about **23% of the variation** in disease progression.

Approximately 77% of the variability remains unexplained by this one-feature linear model.

## Why Are the Metrics Not Very Good?

The weak performance is understandable because the model uses only **one feature: BMI**.

Although BMI has the strongest individual correlation with the target in this dataset, diabetes progression is influenced by several variables.

The original dataset contains additional information such as:

- blood pressure
- age
- blood serum measurements
- BMI
- other physiological variables

Using BMI alone means that the model ignores much of this information.

Another reason is that the relationship between BMI and disease progression is not perfectly linear. Patients with similar BMI values may still have very different disease-progression outcomes.

For example, in the test data, one actual value was:

```text
Actual: 68
Predicted: 147.96
```

This large difference illustrates why both MSE and MAE remain relatively high.

## Visualization

The project also plots the actual test observations together with the fitted regression line.

The scatter plot shows that the real observations are widely distributed around the regression line, confirming that BMI alone is not sufficient to accurately predict disease progression.

## Key Learning Point

This is intentionally a **simple educational Machine Learning regression project**.

Its purpose is to demonstrate:

- loading a built-in dataset
- exploring feature correlation
- selecting a feature
- splitting data into training and testing sets
- training a Linear Regression model
- generating predictions
- visualizing the regression line
- evaluating the model using **MSE, MAE, and R²**

The results also demonstrate an important Machine Learning lesson:

> A feature can have a relatively strong correlation with the target and still be insufficient on its own for accurate prediction.

A future version of the project could use multiple features and compare whether the additional information improves MSE, MAE, and R².
