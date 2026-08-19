# Laptop Price Prediction

## Overview
This project is an end-to-end machine learning application that predicts the price of laptops based on their hardware specifications and features. The goal is to help consumers estimate fair market values and assist businesses with pricing strategies. The final model is deployed as an interactive web application using Streamlit.

**Live Demo:** [https://laptop-price-prediction-sandymoirangthem.streamlit.app](https://laptop-price-prediction-sandymoirangthem.streamlit.app)

## Dataset & Feature Engineering
The model is trained on a comprehensive dataset of 1,303 laptop configurations. To improve predictive accuracy, several feature engineering steps were applied:
* **Screen Properties:** Extracted physical resolution (X and Y) to calculate Pixels Per Inch (PPI) and created flags for IPS panels and Touchscreen capabilities.
* **Hardware Categorization:** Processors were grouped into tiers (Intel Core i3, i5, i7, Other Intel, and AMD), and storage was split into explicit HDD and SSD capacities (dropping outdated hybrid/flash storage).
* **Normalization:** Converted raw RAM and Weight text data into purely numeric formats.
* **Target Variable:** Applied a log transformation (`np.log`) to the laptop prices to handle skewed data distribution.

## Model Performance
Multiple algorithms were evaluated to find the best fit for capturing the complex, non-linear relationships between hardware specs and price. 

| Model | Mean Absolute Error (MAE) | R-squared |
| :--- | :--- | :--- |
| Linear Regression | 0.2101 | 0.8073 |
| Decision Tree | 0.1819 | 0.8401 |
| Support Vector Regressor | 0.2023 | 0.8083 |
| Random Forest Regressor | 0.1586 | 0.8873 |
| Gradient Boost Regressor | 0.1598 | 0.8806 |
| **Voting Regressor** | **0.1582** | **0.8898** |

**Conclusion:** The **Voting Regressor**, an ensemble method combining the predictions of Random Forest and Gradient Boosting, achieved the highest accuracy and lowest error rate. This model was selected for the final web deployment.

## How to Run Locally
To download the code and run the Streamlit app on your own machine, run these commands in your terminal:

```bash
git clone [https://github.com/sandymoirangthem/laptop-price-prediction.git](https://github.com/sandymoirangthem/laptop-price-prediction.git)
cd laptop-price-prediction
pip install -r requirements.txt
streamlit run app.py
