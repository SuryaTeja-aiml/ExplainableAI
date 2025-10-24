# XAI Mid

---

## Problem 1 — Surrogate model fidelity (RMSE)

A retail company developed a black-box model to predict monthly sales (units) for a product. A simplified surrogate model was created to explain the black-box predictions. Predictions for four months:

| Month | Black-box Model Predictions (y) | Surrogate Model Predictions (ŷ) |
|-------|---------------------------------|----------------------------------|
| 1     | 50                              | 52                               |
| 2     | 60                              | 63                               |
| 3     | 55                              | 54                               |
| 4     | 65                              | 66                               |

(a) Calculate the Root Mean Square Error (RMSE) between the black-box and surrogate model predictions.

Solution:

RMSE formula:

RMSE = sqrt((1/n) * sum(y_i - ŷ_i)^2)

n = 4

Squared errors:
- Month 1: (50 − 52)² = 4
- Month 2: (60 − 63)² = 9
- Month 3: (55 − 54)² = 1
- Month 4: (65 − 66)² = 1

Sum of squared errors = 4 + 9 + 1 + 1 = 15

MSE = 15 / 4 = 3.75

RMSE = sqrt(3.75) ≈ 1.936491673

Answer: RMSE ≈ 1.94 units

(b) Comment on fidelity

Given predictions range from 50 to 65 units, an RMSE ≈ 1.94 is about 3–4% relative error. This indicates high fidelity: the surrogate closely mimics the black-box predictions and is suitable for interpretability tasks.

---

## Problem 2 (labelled 1.1 in original) — Linear regression R²

A linear regression model predicts monthly product sales (in thousands) from advertising spend. For a quarter:

| Month | Actual Sales (y) | Predicted Sales (ŷ) |
|-------|------------------:|--------------------:|
| 1     | 20               | 22                  |
| 2     | 25               | 24                  |
| 3     | 30               | 29                  |

(a) Calculate the Coefficient of Determination (R²).

Solution:

Mean of actuals:

ȳ = (20 + 25 + 30) / 3 = 25

SS_res (sum squared residuals):
- (20 − 22)² = 4
- (25 − 24)² = 1
- (30 − 29)² = 1
SS_res = 6

SS_tot (total sum of squares):
- (20 − 25)² = 25
- (25 − 25)² = 0
- (30 − 25)² = 25
SS_tot = 50

R² = 1 − SS_res / SS_tot = 1 − 6 / 50 = 0.88

Answer: R² = 0.88 (88%)

(b) Interpretation

An R² of 0.88 means the model explains 88% of the variance in sales — a strong fit. Only 12% of variance remains unexplained, so the model is useful for forecasting and decision-making.

---

## Problem 3 — Perturbations, PDP and Sigmoid

### (a) Random perturbation

Original customer spending values (in thousands of rupees):

| Customer ID | Spending |
|-------------|---------:|
| 1           | 12       |
| 2           | 18       |
| 3           | 24       |
| 4           | 30       |

Add a random perturbation of +0.3 to each spending value (one possible result):

| Customer ID | Original | Perturbed |
|-------------|---------:|----------:|
| 1           | 12       | 12.3      |
| 2           | 18       | 18.3      |
| 3           | 24       | 24.3      |
| 4           | 30       | 30.3      |

Result: 12.3, 18.3, 24.3, 30.3 (in thousands of rupees)

### (b) Structured perturbation (replace 3rd customer's value with mean)

Mean of original values:

Mean = (12 + 18 + 24 + 30) / 4 = 84 / 4 = 21

Replace customer 3's value (24) with 21:

| Customer ID | Original | Perturbed |
|-------------|---------:|----------:|
| 1           | 12       | 12        |
| 2           | 18       | 18        |
| 3           | 24       | 21        |
| 4           | 30       | 30        |

Result: 12, 18, 21, 30 (in thousands of rupees)

### (c) Partial Dependence Plot (PDP)

Given average prediction values:

| BP    | Average Prediction (ŷ) |
|-------:|-----------------------:|
| −0.05 | 102.0                 |
|  0.00 | 105.3                 |
|  0.05 | 107.8                 |

To draw a PDP (BP on x-axis, Average Prediction on y-axis), plot the three points and connect them to show the relationship:

- (-0.05, 102.0)
- (0.00, 105.3)
- (0.05, 107.8)

Interpretation: As BP increases from −0.05 to 0.05, the average prediction rises from 102.0 to 107.8, showing a positive relationship in this BP range.

<img width="590" height="390" alt="image" src="https://github.com/user-attachments/assets/a334a6a5-87f0-4ba9-9716-3722a1b57744" />

### (d) Sigmoid activation for I = −4

Sigmoid:

σ(I) = 1 / (1 + e^(-I))

For I = −4:

σ(-4) = 1 / (1 + e^4) ≈ 1 / (1 + 54.59815) ≈ 0.017986

Answer: σ(−4) ≈ 0.018 (≈ 1.8%)

---

## Problem 4 — Simple linear regression slope and intercept

Dataset (Number of online ads x, Product sales y):

| x | y  |
|--:|---:|
| 2 | 12 |
| 4 | 20 |
| 3 | 16 |

Find the line y = β₀ + β₁ x.

Compute sums (n = 3):
- Σx = 2 + 4 + 3 = 9
- Σy = 12 + 20 + 16 = 48
- Σxy = 2·12 + 4·20 + 3·16 = 24 + 80 + 48 = 152
- Σx² = 2² + 4² + 3² = 4 + 16 + 9 = 29
- x̄ = 9 / 3 = 3
- ȳ = 48 / 3 = 16

Slope:

β₁ = (n·Σxy - Σx·Σy) / (n·Σx² - (Σx)²)
   = (3·152 - 9·48) / (3·29 - 9²)
   = (456 - 432) / (87 - 81)
   = 24 / 6
   = 4

Intercept:

β₀ = ȳ - β₁·x̄ = 16 - 4·3 = 4

Answer: Regression line y = 4 + 4x (β₀ = 4, β₁ = 4)

Interpretation: Each additional online ad increases product sales by 4 units on average; baseline sales when x = 0 is 4 units.

---

## Problem 5 — Black-Box vs White-Box models (banking example)

Scenario:
- Model A: Deep neural network — highly accurate, not easily explainable.
- Model B: Decision tree — less complex, easily explainable.

Comparison:

| Aspect | Black-Box Model (Model A) | White-Box Model (Model B) |
|---|---|---|
| Definition | Model whose internal decision process is not easily interpretable by humans. | Model whose logic and decision rules are transparent and understandable. |
| Characteristics | High predictive performance, complex internals, low transparency, needs post-hoc explanation techniques (e.g., SHAP, LIME). | Transparent decision paths, inherently interpretable, easy to justify decisions to stakeholders/regulators. |
| Example algorithms | Deep Neural Networks, Random Forests, SVMs, Gradient Boosting Machines | Decision Trees, Linear Regression, Logistic Regression, Rule-based systems |
| Banking application | High accuracy loan repayment predictions but hard to explain why a customer was approved/denied. | Clear rules (e.g., "if income > X and score > Y then approve"), easy for officers and regulators to review and explain. |

Key takeaway: Black-box models often deliver better predictive accuracy, while white-box models provide the explainability and transparency required in regulated domains like banking. Choosing between them depends on the trade-off between interpretability and performance, and sometimes a hybrid approach (black-box with surrogate or post-hoc explanations) is used.
