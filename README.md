# US Property Valuation
Using various models to predict fair property transaction prices. 

# Background
Real Estate Investment Trust (REIT) invests in properties and one of their core business is to predict the fair transaction price of a property. This particular REIT operates in the US market.

This REIT currently employs a third-party appraisal service to estimate the property price. However, in practice, the skill level of individual appraisers vary quite large. The REIT ran a trial run to compare the actual transaction prices with the estimates from the appraiser. It was found that the estimates given by inexperienced appraisers differs $70,000 on average.

# Data Science Driven Approach
The REIT has hired a data scientist to find a data-driven approach to value properties instead of relying on the personal expertise from the appraiser. 

A dataset of previous transaction prices and property specs in the market has provided.

The goal is to build a real-estate pricing model to predict transaction prices with Mean Absolute Error (MAE) under $70,000 so the client can replace inexperienced appraisers with the model.

# Machine Learning Techniques

- Exploratory Data Analysis
- Feature Engineering 
- Linear Regression
- Decision Tree
- Random Forest 
- XGBoost
- CatBoost
- LightGBM
- Pipeline
- K-Fold Cross Validation

# Dataset
Dimension of the dataset: 1883 rows, 26 columns

Observations/Rows Explanation:
 
The dataset has 1883 observations in the city where the REIT is located.
Each observation represent the transaction details of one property only. 
The transaction price for the observation range from $200K to $800K.

Features/Columns Explanation:
Target variable:
'tx_price' - Transaction price in USD

Property Public records:
'tx_year' - Year the transaction took place 
'property_tax' - Monthly property tax 
'insurance' - Cost of monthly home owner's insurance

Property characteristics: 
'beds' - Number of bedrooms 
'baths' - Number of bathrooms 
'sqft' - Total floor area in squared feet 
'lot_size' - Total outside area in squared feet
'year_built' - Year property was built 
'basement' - Does the property have a basement? 

Location convenience scores 
'restaurants' - Number of restaurants within 1 mile 
'groceries' - Number of grocery stores within 1 mile 
'nightlife' - Number of nightlife venues within 1 mile 
'cafes' - Number of cafes within 1 mile 
'shopping' - Number of stores within 1 mile 
'arts_entertainment' - Number of arts and entertainment venues within 1 mile 
'beauty_spas' - Number of beauty and spa locations within 1 mile 
'active_life' - Number of gyms, yoga studios, and sports venues within 1 mile 

Neighborhood demographics 
'median_age' - Median age of the neighborhood 
'married' - Percent of neighborhood who are married 
'college_grad' - Percent of neighborhood who graduated college 

Schools 
'num_schools' - Number of public schools within district 
'median_school' - Median score of the public schools within district, on the range 1 - 10

# Results
10-fold cross validation:

1. XGBoost pipeline: 46966.178 | Time taken: 0.862691
2. CatBoost pipeline: 49003.277 | Time taken: 66.164037
3. Random Forest pipeline: 52555.943 | Time taken: 0.796871
4. Decision Tree pipeline: 69224.808 | Time taken: 0.167551
5. Linear Regression pipeline: 92218.076 | Time taken: 0.020941

Without tuning, it seems like in terms of accuracy and efficiency. XGBoost is the best model to use for the property valuation with the lowest MAE for 10-fold cross validation (~47k). For the second best model CatBoost (MAE: ~49k), it requires much more time to perform a 10-fold cross validation (~77 folds of time for XGBoost). And of course, more tuning can be done to improve the predictability of the models.
