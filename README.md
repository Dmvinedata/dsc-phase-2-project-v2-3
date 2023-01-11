# King County Home Value Predictions

![Presentation Link](https://github.com/Dmvinedata/dsc-phase-2-project-v2-3/blob/main/Phase2_Project_Presentation_DJackson.pdf) <br>

![Jupyter Notebook Link](https://github.com/Dmvinedata/dsc-phase-2-project-v2-3/blob/main/RE_Prediction_P2.ipynb) 

## Author: Deztany Jackson

# Overview

Real Estate agents in King County, Seattle are evaluating the neighborhoods to encourage current home owners of he benefits of improving and upgrading their property value. Housing data from King County was used to develop linear regressions models to support future price prediction.

--
# Business Understanding

The primary stakeholders are real estate agents because of their wide use cases, network, domain knowledge and their incentive for home owners to increase their property value.

This model is used as an intial model supporting course predictions. The main attributes used to support model prediciton are: Condition, Grade and Sqft Living. The main attributes used to support model creation are:

'bedrooms', 'bathrooms', 'sqft_living', 'sqft_lot', 'floors','waterfront', 'yr_built', 'zipcode', 'cond_num', 'grade_num' 

The model explains 67% of the variation. This means there are things that the model still doesn account for in making predictions.

 [Phase 1 Project Description](https://learning.flatironschool.com/courses/4964/pages/phase-2-project-description), 2022

---

# Data Understanding

This project uses the King County House Sales dataset (from GitHub project repo). This can be found in several locations: [Git Hub Data](https://github.com/learn-co-curriculum/dsc-phase-2-project-v2-3/tree/main/data) & [Kaggle](https://www.kaggle.com/datasets/harlfoxem/housesalesprediction). Several types of features were apart (categorical obectd, cardinal and nominal numbers)    
# Modeling

## Training and Testing  & Cross Validation Approach

Predicting new home prices comes after training and testing the model. The train/test split is used for intial model validation. Kfold cross validation will also be used for all.
## Baseline Model (1)

The initial linear regression model will be done with the highest correlated feature. This will be considered our
baseline model. The highest correlated feature was the **"sqft_living"**  with .7 correlation with the "price". 

## Second Model with Categories and Numerical Features (2)

We will improve the baseline model by adding more features training more features(numerical and categorical). Additional features should support an increase a R2 score because it will help describe the dataset more. More processing of the data will occur across the training and testing data to support an improved model.

## Feature Selection Modeling (3)

Certain features from the dataset will be transformed. Log transformations will be performed on the sqft features and the "price" to normalize their data, due to their skewness. Because we already transformed the "condition" and "grade" features to numbers, we will apply the One Hot Encoding transformation to the "Waterfront" categorical feature.

***
![Home Value Distribution](https://github.com/Dmvinedata/dsc-phase-2-project-v2-3/blob/main/images/Initial_DistPrices_1.png)
***

 The feature(s) that are above the needed p-value (.05) are: - **"wa_NO"** . This feature will be dropped for rejecting the Null Hypothesis of being significant.

Ref Statsmodel Interpretation[Tim McAleer, 2020](https://medium.com/swlh/interpreting-linear-regression-through-statsmodels-summary-4796d359035a)

## Best Feature Selection/Final model (4)

The best features were used for the final model. After modeling three iterations at similar score of ~.65 for the training and validation data, a final model will be fit and used for prediciton using the last dataset. 
# Regression Results
## Model Results
    
The final accuracy metrics are good enough to use the model for basic home value predictions.

**Coefficient Results:**<br>
Grade Feature: For every one-unit increase in the Grade, the home value increases by about 26%.
Condition Feature: For every one-unit increase in the Condition, the home value increases by about 3%.
Sqft_living Feature: For every 5% increase in the sqft, the home value by about 20 %.

**RMSE Score Results:**<br>

The refinement of our model decreased the train and test RMSE scores by over 260K to ~197K. 

**R2 Score Results:**<br>

The final model increased its R2 score by ~.15. The best base model score was .5 and the final test's model score ended with ~.66. This was due primarily to the use of multiple features and the filtering of insignificant ones.

**Linear Regression Model Assumptions:**

The final model passed the linearity, normalization and homoescedasticity assumptions and failed the multicollinearity assumption.
 
## Model RMSE and R2 Scores:

**Final Unlogged Train Mean Squared Error:** 206364.0 <br>
**Final Unlogged Test Mean Squared Error:**  196739.0 <br>

**Final Train Model Score:**  0.6438531698069864<br>
**Final Test Model Score:**  0.6565129767577557<br>

## Prediction Results

Using the the trained multi-linear regression model, home prices were able to be predicted for a subset of homes. Because this problem was to predict home values after improvements, homes were chosen that had a major space for improvement.

The intial dataset used was filtered by the top five zipcodes that have the most homes with a "**condition" of 3-Average or less & a "grade" of 6-Low Average or less**". 

The chosen homes were then modified to have a condition of **4-Good** and a grade of **8-Good** while all the other features stayed the same. 
## Home Improvement Prediction Results

Across the five chosen zipcodes, they all resulted in several hundred thousand dollar increase and minimum 100% increase in value.

***
![Average Zipcode Home Value Comparison ](https://github.com/Dmvinedata/dsc-phase-2-project-v2-3/blob/main/images/ZipcodeAvg_HomeValue.png)
***

Specific zipcode example (98188) had the highest amount of homes (106) that met our Condition and Grade criteria for needing improvement.<br>

***
![ Zipcode 98188 Home Value Comparison ](https://github.com/Dmvinedata/dsc-phase-2-project-v2-3/blob/main/images/Zipcode18_HomeValue.png)
***

# Conclusion
## Top Limitations

There were several major limitations. A lot of it stemmed from understanding the domain and making processing and analysis decisions from that knowledge.

- **Limited dataset:** <br>
- **Unknown realistic "Condition" and "Grade" values:**  <br>
- **Unknown affects on other variables:** <br>
- **Communal effects:** <br>  
 - **Dataset limitations:** <br>  
## Recommendations
- Low Hanging Fruit: Focus on major areas with high needs to bring up home values.
    - At a minimum promote increasing conditions (e.g. maintenence) in the homes.
        - For every one-unit increase in the Condition, the home value increases by about 3%
    - Promote bring homes up to code (this increases the grade, which impacts home values the most).
        - For every one-unit increase in the Grade, the home value increases by about 26%.
    - While improving the home recommend adding a room (e.g. bathroom, small bedroom).
        - For every 5% increase in the sqft, the home value by about 20 %.
        - For every 1% increase in the sqft, the home value by about 4 %. 