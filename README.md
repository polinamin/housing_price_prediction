# Project 2 - Ames Housing Data and Kaggle Challenge

**Primary Learning Objectives:**

1. The main objective of this analysis is to create a regression model based on the Ames Housing Dataset. This model will predict the price of a house at sale. The Ames Housing Dataset is an exceptionally detailed and robust dataset with over 70 columns of different features relating to houses.

2. The analysis was conducted to help Realtor Aggregator Sites (such as Redfin and Zillow) gain more insight into the Consumer thought process via their UI, and provide additional guidance for new features that could be helpful for driving more satisfaction and, ideally, more home-buying across users.


## Set-up
- I took an iterative approach to the problem and started with the simplest model; building complexity, iterating, and tweaking as I went.
- Every model is built to stand more-or-less independently, so some engineering, transformation and cleaning will be repeated across models.
-- While this is not optimal, it helps to maintain model independence and continue running each model concurrently without interdependence. Nevertheless, it does leave room for manual error and inconsistency across like variables.


## Models and Outcomes

| | **Model** | **Summary** | **R^2** | **RMSE** |
| --- | --- | --- | --- | --- |
| 1 | Simple Linear Regression | No transformations/feature engineering. Variables with multicollinearity were not included. Variables include: Overall Quality, Total Basement SF, Gr Living Area, 1st Flr SF, Garage Cars | Train: 0.78; Test: 0.82 | 33980 |
| 2 | Linear Regression | Feature engineered and scaled features. Variables include: Total sqft, Overall Condition, Overall Quality, Interaction Condition and Quality, Zone (Dummy), Neighborhood (Dummy) | Train: 0.81; Test: 0.85  | 31248 |
| 3 | Same as Model 2, but Lasso Regularization | --- | Train: 0.81; Test: 0.85 | 31043 |
| 4 | Linear Regression | Feature engineered and scaled features. Variables include: Total sqft, Overall Condition, Overall Quality, Interaction Condition and Quality, Bathrooms, Bedrooms, Month sold, Neighborhood (Dummy) | Train: 0.79; Test: 0.80 | 34671 |
| 5 | Linear Regression | Feature engineering and scaled features. Variables include: Total sqft, Lot Area, Overall Condition, Overall Quality, Interaction Condition and Quality, Bathrooms, Bedrooms, Neighborhood (Dummy), Garage Capacity, House Style (Dummy) | Train: 0.81; Test: 0.80 | 35175 |
| 6 | Lasso Regression | Feature engineering and scaled features. Variables include: Overall Condition (log), Overall Quality, Interaction Condition and Quality, Bathrooms, Bedrooms, Total sqft House (log), Total sqft Lot Area (log) | Train: 0.77; Test: 0.80 | 34435 |
| 7 | Linear Regression | Feature engineering and scaled features. Variables include: Overall Condition, Overall Quality, Interaction Condition and Quality, Bathrooms, Bedrooms, Total sqft Lot Area (log), Price per Sqft (per neighborhood) | Train: 0.82; Test: 0.84 | 30908 | 
| 8 | Lasso Regression | Feature engineering and scaled features. Variables include: Total sqft House (feature engineering), Overall Condition, Overall Quality, Interaction of Condition/Quality, Bathrooms, Bedrooms, Total sqft Lot Area (log), Price per Sqft (per neighborhood)otal sqft Lot Area (log), Price per Sqft (per neighborhood), Zone, Building Type | Train: 0.82; Test: 0.84 | 30800 | 
| 9 | Lasso Regression | Feature engineering and scaled features. Variables include: Neighborhood (dummy), Total sqft Lot Afea (log), Total sqft House (log), Bedrooms, Bathrooms, House Type (dummy), Bldg Type (dummy), Cost/Sqft (per neighborhood), Garage Capacity, Overall Quality | Train: 0.84; Test: 0.83 | 31773| 


- [Model 1]("./code/Model 1.ipynb")
- [Model 2 and 3]("./code/Model 2 and 3.ipynbModel 2 and 3.ipynb")
- [Model 4]("./code/Model 4.ipynb")
- [Model 5]("./code/Model 5.ipynb")
- [Model 6]("./code/Model 6.ipynb")
- [Model 7]("./code/Model 7.ipynb")
- [Model 8]("./code/Model 8.ipynb")
- [Model 9]("./code/Model 9.ipynb")


### Summary 

This analysis intentionally focused on a select set of features, to explore how they interact with and impact Sale Price of homes. The models are all closely related, and work through various iterations of variables and feature engineering, transformation, and regression methodologies.

While none of the models did particularly well on the Kaggle Challenge, the purpose of this analysis was more to understand specific feature behavior and not to minimize RMSE overall. With this in mind, models 3 and 9 provide the most interesting findings.

**Model 3:**
- There is a significant difference between the train and test outcomes; indicating that the model is underfitting.
- Additionally, the model requires more optimization, in order to automate the reconciliation of datasets across all the encoded cateogrical fields included as explanatory variables.

**Model 9:** 
- This model had more features than Model 3, and eliminates some features that were constant across the other models (namely: Overall Condition and Interaction between Condition/Quality.)
- This feature set most closely resembles the features that consumers filter through when looking at houses via Realtor aggregator sites. My intention is to provide insights to Realtor Aggregator sites around how to optimize the consumer experience and improve their takeaways and further utilization of their sites.