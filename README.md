# Description
## EV_market_analysis:
This script assumes that you have a CSV file named ev_market_data.csv containing the relevant data for your analysis. One may need to adjust the column names and data types according to your actual dataset.
This script assumes the availability of certain columns in the dataset, such as city, annual_income, age, env_score, tech_score, commute_distance, has_home_charging, and vehicle_purpose.
### K-means clustering on selected features to group consumers into different segments was performed.
### Analyze the clusters by calculating the mean values of each feature for each cluster.
### Identify potential target segments based on the specified criteria (urban area, high income, young age, environmental consciousness, tech-savviness, daily commute, home charging, and non-commercial usage).

## EV_analysis:
1) The different dataset taken was loaded. Missing values in numeric columns are filled with the mean of each column. Missing values in non-numeric columns are filled with the string 'missing'. Categorical and numerical features are identified.
A preprocessing pipeline is set up: Categorical features are encoded using OneHotEncoder. Numerical features are passed through without transformation (passthrough).

2) A composite score called market_opportunity_score is calculated based on three weighted factors:
    '2022 - EV'
    'Proportion of Electric Vehicle'
    '2023 (Till 01-08-2023) - Total'
These numerical columns are normalized before calculating the composite score. The target variable (y) is set to market_opportunity_score. Only numerical columns are selected for the features (X).

3) SelectKBest with f_regression is used to select the top 10 features from X.
4) The data is split into training and testing sets using train_test_split. A LinearRegression model is trained on the training set. The model is evaluated on the test set using R-squared and Mean Squared Error (MSE). The R-squared and MSE values are printed.
5) Scatter plots of the target variable (market_opportunity_score) against individual features are created. A pairplot of the top features selected by SelectKBest is generated. A residual plot is created to visualize the residuals (differences between predicted and actual values) from the training set predictions.
