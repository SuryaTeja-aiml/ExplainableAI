marks: 30, 1st q = 5+5, 2nd q = 3+3+4, 3rd q = 5+5  
### 1
A retail company has developed a complex AI model (black-box) to predict the monthly sales (in units) for its top-selling product based on various marketing factors such as online advertisements, promotions, and customer engagement.

To make the model explainable, the data science team has created a simplified surrogate model that mimics the behavior of the black-box model for interpretability.

The following are the predicted sales from both models for four recent months:

| Month | Black-box Model Predictions | Surrogate Model Predictions |
|---:|---:|---:|
| 1 | 50 | 52 |
| 2 | 60 | 63 |
| 3 | 55 | 54 |
| 4 | 65 | 66 |

(a) Calculate the Root Mean Square Error (RMSE) between the black-box and surrogate model predictions.

(b) Based on the RMSE value, comment on the fidelity of the surrogate model.

---

### 2
A marketing analyst at a company wants to evaluate the performance of a **linear regression model** that predicts monthly product sales (in thousands of units) based on the amount spent on online advertising.

For a recent quarter, the actual and predicted sales values are given below:

| Month | Actual Sales (y) | Predicted Sales (ŷ) |
|---:|---:|---:|
| 1 | 20 | 22 |
| 2 | 25 | 24 |
| 3 | 30 | 29 |

(a) Calculate the Coefficient of Determination (R² value) for the given data.

(b) Based on the R² value, interpret how well the model fits the data.

---

### 3
A data scientist is analyzing customer spending amounts (in thousands of rupees) from a sample of four customers:

| Customer ID | Spending Amount |
|---:|---:|
| 1 | 12 |
| 2 | 18 |
| 3 | 24 |
| 4 | 30 |

(a) Add a random perturbation noise of +0.3 to each spending value and show one possible result.

(b) Apply a structured perturbation by replacing the third customer’s spending value with the mean of all four original values.

(c) Using the average prediction values from the PDP (Partial Dependence Plot) calculation given below, draw a PDP showing the relationship between BP (x-axis) and Average Prediction (ŷ) (y-axis).

| BP | Average Prediction (ŷ) |
|---:|---:|
| -0.05 | 102.0 |
| 0.00  | 105.3 |
| 0.05  | 107.8 |

(d) Find the output of the Sigmoid activation function for the input I = -4.

---

### 4
The marketing team of a company wants to predictionally model product sales (y) based on the number of online ads posted (x).

The dataset is as follows:

| Number of Online Ads (x) | Product Sales (y) |
|---:|---:|
| 2 | 12 |
| 4 | 20 |
| 3 | 16 |

Calculate the slope (β₁) and intercept (β₀) for the linear regression line.

---

### 5
A bank is developing two AI models to predict whether a customer will repay or default on a loan:
- **Model A:** Uses a deep neural network, which provides highly accurate predictions but does not reveal how the decision is made.
- **Model B:** Uses a decision tree, where each rule and decision path can be clearly understood by the bank’s officers.

Based on the above scenario, differentiate between Black-Box and White-Box models in terms of their definition, characteristics, and example algorithms.

| Aspect | Black-Box Model | White-Box Model |
|---|---|---|
| Definition |  |  |
| Characteristics |  |  |
| Example algorithms |  |  |
