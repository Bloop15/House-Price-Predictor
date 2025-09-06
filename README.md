# 🏡 Ames Housing Price Prediction

This project demonstrates a comprehensive machine learning workflow to accurately predict house prices using the **Ames Housing dataset**.  
The goal was to compare multiple regression models — from simple linear methods to advanced boosting techniques — and identify the best-performing model through a robust evaluation process.

---

## 📊 Data Preprocessing
The preprocessing pipeline prepared the raw dataset for modeling. Key steps included:

- **Handling Missing Values:**  
  - Dropped columns with a high percentage of missing values (e.g., *Alley, PoolQC*).  
  - Remaining missing values imputed with median (numerical) or mode/contextual values (categorical).  

- **Outlier Removal:**  
  - Outliers in features like *GrLivArea* and *TotalBsmtSF* were removed using scatter plots.  

- **Feature Engineering & Transformation:**  
  - Applied log-transformation to the target variable (*SalePrice*) and skewed numerical features.  
  - Encoded categorical features using **Ordinal Encoding** (ranked categories) and **One-Hot Encoding** (non-ranked categories).  

- **Scaling:**  
  - Standardized numerical features with **StandardScaler** to ensure consistent scale across models.  

---

## 🤖 Modeling Approach
A systematic workflow was followed to ensure robust evaluation:

1. **Baseline Models:**  
   - Trained multiple regression models: Linear Regression, Ridge, Lasso, ElasticNet, Decision Tree, Random Forest, XGBoost.  

2. **Cross-Validation:**  
   - Used **5-fold cross-validation** on the training set to estimate unbiased performance.  

3. **Hyperparameter Tuning:**  
   - Focused on top models (Ridge, Random Forest, XGBoost).  
   - Conducted **RandomizedSearchCV** (broad search) → **GridSearchCV** (fine-tuning).  

4. **Final Evaluation:**  
   - Evaluated the best-tuned models on a **hold-out test set** to measure true generalization performance.  

---

## 📈 Results (Quantitative)

### Final Test Set Performance

| Model          | RMSE   | R²     | MAE   |
|----------------|--------|--------|-------|
| **Ridge**      | 0.0902 | 0.9134 | 0.0681 |
| XGBoost        | 0.0987 | 0.8963 | 0.0716 |
| Random Forest  | 0.1198 | 0.8474 | 0.0890 |

---

## 🎨 Results (Qualitative / Visuals)

- **Residual Plots:**  
  Residuals for the Ridge model were randomly distributed around zero, showing that errors were not systematic.  

- **Feature Importance Plots:**  
  XGBoost and Random Forest highlighted *OverallQual, GrLivArea,* and *GarageCars* as the most influential predictors.  

- **Actual vs Predicted Plots:**  
  The Ridge model’s predictions aligned strongly with actual values, confirming its reliability.  

---

## ✅ Conclusion

- **Model Performance:**  
  Ridge Regression emerged as the top performer, achieving the **lowest RMSE (0.0902)** and the **highest R² (0.9134)** on the test set.  
  Its success is attributed to its ability to handle **multicollinearity and high dimensionality** through regularization, making it ideal for this dataset.  

- **Potential Improvements:**  
  Future work could explore **stacking/ensemble methods** or **polynomial feature engineering** to further boost performance.  
