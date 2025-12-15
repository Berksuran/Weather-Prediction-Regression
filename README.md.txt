# 🌤️ World War II Weather Prediction Project

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange)
![Status](https://img.shields.io/badge/Status-Completed-green)

## 📖 Overview
This project aims to predict the **Maximum Daily Temperature (MaxTemp)** based on the **Minimum Daily Temperature (MinTemp)** and other weather features using various Regression models.

Using the **World War II Weather Dataset**, I conducted a comparative analysis between **Linear Regression** and Regularized Regression models (**RidgeCV, LassoCV, ElasticNetCV**) to find the best performing algorithm.

## 📊 Dataset
- **Source:** Kaggle - Weather Conditions in World War Two
- **Original Size:** ~119,000 Rows
- **Cleaned Size:** ~99,000 Rows
- **Target Variable:** `MaxTemp` (Celsius)
- **Main Features:** `MinTemp`, `Precip`, `Snowfall`

## 🛠️ Data Preprocessing & Cleaning
To ensure high-quality predictions, the following steps were taken:
1.  **Data Cleaning:** Handled "Trace" (T) values in precipitation columns by coercing them to NaN and removing inconsistencies.
2.  **Feature Selection:** Removed redundant features (e.g., Fahrenheit duplicates like `MAX`, `MIN`) to prevent **Multicollinearity**.
3.  **Leakage Prevention:** Removed `MeanTemp` to avoid data leakage, as it is directly derived from the target variable.
4.  **Scaling:** Applied `StandardScaler` to normalize the features for regularized models.

## ⚙️ Models Applied
I implemented and compared the following models:
1.  **Linear Regression:** The baseline model.
2.  **RidgeCV:** Linear regression with L2 regularization (Cross-Validated).
3.  **LassoCV:** Linear regression with L1 regularization (Cross-Validated).
4.  **ElasticNetCV:** A combination of L1 and L2 regularization.

## 📈 Results & Conclusion

| Model | R² Score | MAE (Mean Absolute Error) | MSE (Mean Squared Error) |
|-------|----------|---------------------------|--------------------------|
| **Linear Regression** | 0.744 | 3.07 | 15.55 |
| **RidgeCV** | 0.744 | 3.07 | 15.55 |
| **LassoCV** | 0.744 | 3.07 | 15.55 |
| **ElasticNetCV** | 0.744 | 3.07 | 15.55 |

**Key Finding:**
All models produced nearly identical results. This indicates that:
1.  The relationship between `MinTemp` and `MaxTemp` is **strongly linear**.
2.  The dataset is large enough (~99k samples) that the model does not suffer from overfitting, rendering the regularization penalties (L1/L2) unnecessary for this specific feature set.
3.  **Simple Linear Regression** is sufficient and the most efficient choice for this problem (Occam's Razor).

