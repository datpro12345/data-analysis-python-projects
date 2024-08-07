# Predict Future Sales competition in Kaggle


## Background and motivation

This project idea comes from one of the competitions in Kaggle, which is the world's largest community of data scientists and machine learners. In this project, we will work with a challenging time-series dataset consisting of daily sales data, kindly provided by one of the largest Russian software firms - [1C Company](https://1c.ru).

We implemented some time series techniques we have learned in class (such as ARIMA) and some more advanced algorithms (such as LSTM) on this dataset. We will discuss some specific models that might be used in below model consideration. The goal is to predict total sales for every product and store in the next month.

## Data description

We are provided with daily historical sales data. The task is to forecast the total amount of products sold in very for the test set. Note that this dataset is a real-world dataset. It may have some missing or unreasonable values but we think dealing with dirty data and creating a robust model is also part of the fun in this project.

The data overview is shown in Table 1.

|         | Train              | Test         |
|---------|--------------------|--------------|
| **Data**| Item x shop x day  | Item x shop  |
| **Period** | 34 months          | 1 month      |
| **Aggregation** | daily             | monthly      |

*Table 1. Data overview*

File description (from Kaggle): the website [Predict Future Sales Data](https://www.kaggle.com/c/competitive-data-science-predict-future-sales/data) provides several csv files for different data.

- sales_train.csv - the training set. Daily historical data from January 2013 to October 2015.
- test.csv - the test set. You need to forecast the sales for these shops and products for November 2015.
- items.csv - supplemental information about the items/products.
- item_categories.csv - supplemental information about the items categories.
- shops.csv - supplemental information about the shops.

Data fields (from Kaggle):

- shop_id - unique identifier of a shop
- item_id - unique identifier of a product
- item_category_id - unique identifier of item category
- item_cnt_day - number of products sold.
- item_price - current price of an item
- date - date in format dd/mm/yyyy
- date_block_num - a consecutive month number, used for convenience. January 2013 is 0, February 2013 is 1,..., October 2015 is 33)
- item_name - name of item
- shop_name - name of shop
- item_category_name - name of item category

This dataset is permitted to be used for any purpose, including commercial use.

## CRISP-DM Framework Plan

### 1. Business Understanding

**Objective**:
- Predict total sales for every store and product in the next month to optimize inventory management and strategic planning.

**Requirements**:
- Understand the business context and goals.
- Define the key metrics for success (e.g., RMSE for prediction accuracy).

**Tasks**:
- Conduct meetings with stakeholders to gather detailed business requirements.
- Define the scope of the project, including any constraints and assumptions.
- Identify key business metrics and performance indicators.

### 2. Data Understanding

**Objective**:
- Gather and explore the data to understand its structure, quality, and potential insights.

**Requirements**:
- Access to historical sales data and related metadata (e.g., item prices, shop details).
- Tools for data exploration and visualization (e.g., Python, Jupyter notebooks).

**Tasks**:
- **Data Collection**:
    - Collect datasets from Kaggle and other provided sources.
    - Translate non-English labels to English if necessary.
- **Initial Data Exploration**:
    - Summarize data using descriptive statistics (mean, median, mode, variance).
    - Visualize data distributions using histograms and density plots.
    - Identify missing values, outliers, and data quality issues.
- **Exploratory Data Analysis (EDA)**:
    - Visualize trends, seasonality, and patterns in sales data.
    - Plot sales over time, broken down by store and product.
    - Identify correlations between different variables (e.g., item price and sales).

### 3. Data Preparation

**Objective**:
- Clean and transform the data to prepare it for modeling.

**Requirements**:
- Tools for data manipulation and cleaning (e.g., Pandas in Python).
- Detailed understanding of data cleaning techniques.

**Tasks**:
- **Data Cleaning**:
    - Handle missing values by imputation or removal.
    - Address outliers using appropriate methods (e.g., capping or removal).
- **Data Transformation**:
    - Normalize or standardize numerical features if necessary.
    - Encode categorical variables using techniques like one-hot encoding.
- **Feature Engineering**:
    - Create new features such as moving averages, lagged features, and rolling statistics.
    - Aggregate daily sales data to monthly sales to leverage CLT.
    - Generate additional features like average monthly sales, sales per city, and sales per product category.
- **Data Merging**:
    - Merge datasets (e.g., sales data with item and shop metadata).
    - Ensure consistency in the merged dataset.

### 4. Modeling

**Objective**:
- Select and apply appropriate modeling techniques and calibrate model parameters to optimal values.

**Requirements**:
- Tools for model development and evaluation (e.g., Scikit-learn, XGBoost, LightGBM).
- Understanding of various modeling techniques and their assumptions.

**Tasks**:
- **Model Selection**:
    - Choose a variety of models to test, including traditional models (e.g., ARIMA, ETS) and modern machine learning models (e.g., XGBoost, LightGBM).
- **Model Training**:
    - Split the data into training and validation sets.
    - Train each model using the training set.
    - Perform hyperparameter tuning using techniques like grid search or random search.
- **Model Evaluation**:
    - Evaluate models using RMSE and other metrics like MAE and MAPE.
    - Conduct residual analysis to check for normality and homoscedasticity.
    - Compare model performance using statistical tests to determine if differences are significant.

### 5. Evaluation

**Objective**:
- Assess the performance of the model(s) to ensure they meet business objectives and are reliable.

**Requirements**:
- Tools for model evaluation and statistical analysis.
- Criteria for model success (e.g., RMSE threshold).

**Tasks**:
- **Model Validation**:
    - Validate model performance on the validation set.
    - Perform cross-validation to ensure robustness.
- **Statistical Testing**:
    - Use hypothesis testing to compare models and ensure improvements are statistically significant.
- **Error Analysis**:
    - Analyze errors and residuals to identify patterns and potential improvements.
    - Document any limitations or assumptions made during modeling.

### 6. Deployment

**Objective**:
- Deploy the final model into the production environment where it can be used for decision-making.

**Requirements**:
- Infrastructure for deploying and monitoring models (e.g., cloud services, API development).
- Documentation of the deployment process.

**Tasks**:
- **Deployment Planning**:
    - Develop a deployment strategy, including data pipelines and real-time prediction capabilities.
    - Create an API for model predictions if necessary.
- **Monitoring and Maintenance**:
    - Set up monitoring to track model performance over time.
    - Implement alerting for performance degradation.
    - Plan for regular model retraining and updates.
- **Documentation**:
    - Document the entire process, from data preparation to model deployment.
    - Provide user guides and technical documentation for stakeholders.

## Conclusion and Future Research

While the model's performance is robust, future research can explore incorporating additional external factors such as promotions, holidays, and economic indicators to further enhance the predictive accuracy. Additionally, advanced techniques like LSTM and Transformer models for time-series forecasting could be investigated.


