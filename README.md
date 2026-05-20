# E-commerce Sales Analysis & Predictive Modeling
### DecodeLabs Data Science Internship - Capstone Project

## Project Overview
This project focuses on analyzing an e-commerce dataset containing 1,200 sales transactions. The goal is to clean the dataset, perform Exploratory Data Analysis (EDA) to unlock business insights, and build a predictive model to estimate total order prices.

## Key Technical Steps Included:
- **Task 1: Dataset Understanding:** Analyzed 14 features consisting of numerical and categorical variables to understand the data structure.
- **Task 2: Data Cleaning:** Handled missing values in coupon codes, checked for duplicates, and properly formatted date and financial columns (rounding TotalPrice to 2 decimal places).
- **Task 3 & 4: EDA & Visualization:** Discovered that **Chairs** are the top-selling product and **Instagram** is the highest revenue-generating marketing channel. Visualized trends using Heatmaps, Pie Charts, and Count Plots.
- **Task 5: Predictive Modeling:** Built a **Linear Regression** model using `scikit-learn` to predict `TotalPrice` based on quantity and unit price, achieving an impressive accuracy score of **89% ($R^2 = 0.89$)**.

## Business Insights & Recommendations
1. **Maximize Instagram Ads:** Double down on Instagram marketing campaigns since it delivers the highest sales revenue ($275K+).
2. **Address Order Cancellations:** Investigate logistics and shipping workflows, as cancelled and returned orders represent a significant portion of potential revenue.
3. **Bundle Offers:** Since customers have an average of 5-6 items in their carts but only purchase 3, introducing "Buy 3 Get 1 Free" bundles could significantly boost overall sales.

## Technologies Used
- **Language:** Python
- **Libraries:** Pandas, NumPy, Matplotlib, Seaborn, Scikit-Learn
