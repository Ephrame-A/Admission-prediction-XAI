# Graduate School Admission Prediction

This project explores the use of machine learning models to predict the chance of admission to a graduate school based on several key features. A central goal is to apply **Explainable AI (XAI)** concepts, specifically using the **SHAP (SHapley Additive exPlanations)** library, to not only build a predictive model but also to understand and interpret its decisions.

## 🚀 Project Overview

The core objective is to compare the performance of two popular regression models—a **Decision Tree** and an **XGBoost Regressor**—while simultaneously using SHAP to gain deep insights into what drives their predictions. This approach allows us to move beyond simple accuracy metrics and understand the "why" behind the model's output.

## 💾 Dataset

The dataset used in this project is the **Graduate Admission dataset**, containing 500 rows and 7 features. The features include:
- `GRE Score`
- `TOEFL Score`
- `University Rating`
- `SOP` (Statement of Purpose)
- `LOR` (Letter of Recommendation)
- `CGPA` (Cumulative Grade Point Average)
- `Research` (Binary: Yes/No)

The target variable is `Chance of Admit`, a value between 0 and 1.

## 🧠 Models and Methodology

I implemented two regression models for this task:

1.  **Decision Tree Regressor:** A simple, single tree-based model that makes predictions by learning a series of if-then-else rules. It is highly interpretable but prone to overfitting.
2.  **XGBoost Regressor:** An ensemble of many decision trees built sequentially. Each new tree corrects the errors of the previous ones, making it a very powerful and accurate model.

### Model Evaluation
Model performance was evaluated using the **Mean Squared Error (MSE)** metric, which measures the average squared difference between the actual and predicted values. A lower MSE indicates a more accurate model.

## ✅ Results and Interpretation

The following scores were achieved on the test data:

- **Decision Tree:**
    - **R² Score:** `0.68`
    - **MSE:** `0.0065`

- **XGBoost:**
    - **R² Score:** `0.746`
    - **MSE:** `0.0052`

*Analysis:**
The **XGBoost model performed better** than the Decision Tree, as evidenced by its higher R² score and lower MSE. The R² score of 0.746 indicates that the XGBoost model explains approximately 74.6% of the variance in the `Chance of Admit` variable.

### Model Interpretation with SHAP

To understand why the models make their predictions, we used **SHAP (SHapley Additive exPlanations)**. SHAP provides a way to assign each feature a contribution value for both global and local predictions.

* **Global Importance (Summary Plot):**
    The SHAP summary plots revealed that **CGPA** was the most influential feature for both models especially for decision tree, followed by `GRE Score` and `TOEFL Score`. This aligns with common sense, as these are strong indicators of academic performance.

* **Individual Predictions (Force & Waterfall Plots):**
    For a single student's prediction, the force and waterfall plots showed how each feature (e.g., a high CGPA, a strong LOR) pushed the predicted admission chance higher or lower from the average. For the decision tree, the CGPA has very big contribution. in contrast, in XGBoost the features have relatively uniform contribution.

## 📈 Conclusion

Both models demonstrated good performance, but XGBoost proved to be the more accurate choice. Using SHAP, we were able to move beyond just the prediction and gain critical insights into the features that drive the admission decision.
