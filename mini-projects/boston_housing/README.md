# Predicting Real Estate Prices in Boston - A Linear Regression-Based Analysis

## Summary

In this project, we focus on predicting the median value of owner-occupied homes (`MEDV`) in the Boston metropolitan area. The goal is to provide insight into the real estate market in Boston, using a linear regression-based. As it turns out none of those models will meet the assumptions of linear regression.

---

## Project Overview

### 1. **Understanding the Dataset Variables**

The dataset is based on the Boston Standard Metropolitan Statistical Area (SMSA) from 1970, with each record corresponding to a town or suburb in the Boston area. The dataset contains the following attributes:

* **CRIM**: Per capita crime rate by town
* **ZN**: Proportion of residential land zoned for lots over 25,000 sq. ft.
* **INDUS**: Proportion of non-retail business acres per town
* **CHAS**: Charles River dummy variable (= 1 if tract bounds river, 0 otherwise)
* **NOX**: Nitric oxides concentration (parts per 10 million)
* **RM**: Average number of rooms per dwelling
* **AGE**: Proportion of owner-occupied units built prior to 1940
* **DIS**: Weighted distances to five Boston employment centers
* **RAD**: Index of accessibility to radial highways
* **TAX**: Full-value property tax rate per \$10,000
* **PTRATIO**: Pupil-teacher ratio by town
* **B**: \$1000(Bk - 0.63)^2\$, where \$Bk\$ is the proportion of African American residents by town
* **LSTAT**: Percentage of lower status population

**Target Variable**:

* **MEDV**: Median value of owner-occupied homes in \$1000s

---

### 2. **Exploratory Data Analysis (EDA)**

EDA was performed to understand the distribution and relationships between variables. Key findings include:

* **Skewness**: Several features exhibit skewness, which was addressed by applying transformations to the positively and negatively skewed variables.
* **Correlation**: The highest correlations with the target variable `MEDV` were found with `RM` (average number of rooms per dwelling) and `LSTAT` (percentage of lower status population).
* **Outliers**: Outliers were detected using the IQR method, and certain columns were winsorized to mitigate their impact.

---

### 3. **Data Cleaning**

* Missing values and duplicates were checked, but none were found in the dataset.
* Categorical variables (e.g., `CHAS`) were one-hot encoded.
* Skewed data was log-transformed to bring distributions closer to normal.
* Outliers in specific columns (such as `CRIM`, `RM`, `DIS`, `LSTAT`, and `MEDV`) were identified and winsorized.

---

### 4. **Model Building**

We experimented with multiple regression models to predict housing prices:

#### a) **Linear Regression**

* A simple linear regression model was built using the features most correlated with `MEDV` (`RM`, `ZN`, `LSTAT`, `PTRATIO`, `CHAS_1`).
* Performance metrics such as Mean Absolute Error (MAE), Mean Squared Error (MSE), Root Mean Squared Error (RMSE), and R-squared (R²) were calculated for both the training and test datasets.

#### b) **Assumption Checks**

* **Normality** of residuals was checked using the Shapiro-Wilk test.
* **Homoscedasticity** was tested using the Breusch-Pagan test.
* **Autocorrelation** of residuals was evaluated using the Durbin-Watson statistic.
* Plots were generated to assess residuals, actual vs predicted values, and more.

#### c) **Additional Models**

* Decision Tree Regressor
* Random Forest Regressor
* Support Vector Machine (SVM) Regressor

Each model was evaluated based on performance metrics, and assumptions were checked.

---

### 5. **Hyperparameter Tuning**

Several models were fine-tuned using GridSearchCV for hyperparameter optimization. Models tuned include:

* **Lasso**: Regularized linear model.
* **Ridge**: Linear regression with L2 regularization.
* **ElasticNet**: Combines Lasso and Ridge regularization.
* **SVR**: Support Vector Machine regression.
* **Random Forest Regressor**: An ensemble learning method using decision trees.

The best hyperparameters were identified for each model, and the final predictions were evaluated on the test set.

---

### 6. **Summary of Results**

Despite several models being tested, including linear regression, decision trees, random forests, and SVM, the results showed that real-world data, such as the Boston housing data, often violate key assumptions required by linear regression models, such as normality and homoscedasticity of residuals. These violations make it challenging to interpret the results without caution. Nevertheless, it’s important to be aware of these limitations when building predictive models, as decisions made based on these models may carry risks if assumptions aren’t met.

By tuning and using different models, including regularized linear models and ensemble methods, the project demonstrated how advanced regression techniques can improve predictive performance, offering more reliable predictions of house prices.


