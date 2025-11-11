# 🚗 Kaggle Playground S5E10: Predicting Road Accident Risk

This repository contains my complete solution for the **Kaggle Playground Series - Season 5, Episode 10: Predicting Road Accident Risk**. The notebook `submission5.ipynb` details the entire pipeline, from data preprocessing and feature engineering to model tuning and ensembling.

**Competition Page:** [https://www.kaggle.com/competitions/playground-series-s5e10](https://www.kaggle.com/competitions/playground-series-s5e10)

## 🎯 Objective

The goal of this competition was to predict the `accident_risk`, a continuous value between 0.0 and 1.0, for various road segments based on a set of 12 features.

* **Evaluation Metric:** Submissions were evaluated using the **Root Mean Squared Error (RMSE)**.
* **Dataset:** The data was synthetically generated from a deep learning model trained on the *Simulated Roads Accident* dataset.

## 🛠️ Methodology & Approach

My approach focused on robust feature engineering, hyperparameter optimization, and model ensembling.

1.  **Feature Engineering:**
    * Created several interaction features between categorical variables (e.g., `weather_lighting`, `road_surface_weather`).
    * Generated polynomial and ratio features from numerical data (e.g., `speed_x_curvature`, `accidents_per_vehicle`, `log_traffic`).

2.  **Preprocessing:**
    * **Categorical Features:** Applied **One-Hot Encoding** to all `object` and `bool` type features.
    * **Scaling:** Used `StandardScaler` from scikit-learn to scale the entire feature set before training.

3.  **Model Training & Tuning:**
    * **Models:** Utilized an ensemble of two powerful gradient boosting models: **LightGBM (LGBM)** and **XGBoost (XGB)**.
    * **Hyperparameter Tuning:** Employed **Optuna** to perform Bayesian optimization, finding the best hyperparameters for both LGBM and XGB by minimizing the cross-validated RMSE.

4.  **Validation & Ensembling:**
    * A **5-fold StratifiedKFold** (using the target binned into 10 quantiles) was used to generate out-of-fold (OOF) predictions.
    * The final ensemble weights for LGBM and XGB were optimized by minimizing the RMSE score on these OOF predictions.
    * The final models were re-trained on the entire dataset using the optimized hyperparameters.

5.  **Submission:**
    * The final prediction is a weighted average of the tuned LGBM and XGB models.
    * All predictions were clipped to the `[0, 1]` range to match the target's constraints.

## 📊 Results

The local cross-validation performance of the models was:
* **LGBM OOF RMSE:** 0.056081
* **XGB OOF RMSE:** 0.056103
* **Optimized Ensemble OOF RMSE:** 0.056066

## 🚀 How to Run

1.  Clone this repository.
2.  Download the competition data (`train.csv`, `test.csv`, `sample_submission.csv`) from the [Kaggle competition page](https://www.kaggle.com/competitions/playground-series-s5e10/data) and place it in an `/input/` directory or update the `DATA_PATH` variable in the notebook.
3.  Install the required libraries (see below).
4.  Run the `submission5.ipynb` notebook. The final `submission.csv` file will be generated in the working directory.

## 📚 Libraries Used

* `pandas`
* `numpy`
* `scikit-learn` (for KFold, StandardScaler, metrics)
* `lightgbm`
* `xgboost`
* `optuna` (for hyperparameter tuning)
* `matplotlib` & `seaborn` (for visualization)
