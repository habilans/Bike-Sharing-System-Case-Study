# Bike-Sharing-System-Case-Study
## Problem Statement
A bike-sharing system is a service in which bikes are made available for shared use to individuals on a short term basis for a price or free. Many bike share systems allow people to borrow a bike from a "dock" which is usually computer-controlled wherein the user enters the payment information, and the system unlocks it. This bike can then be returned to another dock belonging to the same system.

A US bike-sharing provider BoomBikes has recently suffered considerable dips in their revenues due to the ongoing Corona pandemic. The company is finding it very difficult to sustain in the current market scenario. So, it has decided to come up with a mindful business plan to be able to accelerate its revenue as soon as the ongoing lockdown comes to an end, and the economy restores to a healthy state. 

In such an attempt, BoomBikes aspires to understand the demand for shared bikes among the people after this ongoing quarantine situation ends across the nation due to Covid-19. They have planned this to prepare themselves to cater to the people's needs once the situation gets better all around and stand out from other service providers and make huge profits.
They have contracted a consulting company to understand the factors on which the demand for these shared bikes depends. Specifically, they want to understand the factors affecting the demand for these shared bikes in the American market. The company wants to know:

- Which variables are significant in predicting the demand for shared bikes.
- How well those variables describe the bike demands
Based on various meteorological surveys and people's styles, the service provider firm has gathered a large dataset on daily bike demands across the American market based on some factors.

## Steps involved to build a Linear Model 
1. Data Preparation
   - Import requried libraries like Pandas, Numpy, sklearn, statsmodels, seaborn, matplotlib etc.
   - Read the input CSV file
3. Data Quality Check
   - Checking for NULL values in the dataset
   - Checking for Duplicate values in the dataset
4. Dropping unwanted columns from the dataset.
5. Converting the datatype of  `season`, `weathersit`,`mnth`,`weekday` to Categorical Variable
6. Dummy variable creation
   - Categorical variables to dummy variables
   - use drop_first=True which will create only k-1 dummy variables.
7. Splitting the Dataset into Train set  and Test set
8. Perform Exploratory Data Analysis on Train set
   - Create a dataframe for numerical variables in the dataset and visualize them using Pairplot
   - Using boxplot and barplot, visualize the categorical variables using subplot
9. Rescaling the features
     - Use MinMaxScaler() from sklearn to transform the numerical variables in the train dataset between 0 and 1.
10. Prepartion before buiding a Model
     - Before training the model, we need to find if there is any multicollinearity between the target variable and other predictor variable. Find that using the heatmap
     - Dividing the train set into X and Y sets for model building
         - Take the target variable from train set and stored as y_train
         - Other independent variables from train set are stored as x_train
11. Building a Linear Model
    - We will be using the LinearRegression function from SciKit Learn for its compatibility with RFE
        -  Running RFE with the output number of the variable equal to 15
        -  select only the variables with the RFE support is True.
    - Build  model using statsmodel, for the detailed statistics
        - Build the model with RFE selected variables
        - Drop the feature that are least helpful in Prediction (High p-value)
        - Drop the feature that are redundant (High VIF)
        - Rebuild the model and repeat.
    - Repeat the above steps until there is no multicollinearity
12. Residual Analysis and Assumption validation
13. Making Prediction using the Final Model
14. Model Evaluation
15. Check r2_score for both Train set and Test set.

The equation of our best fitted line is: 

$cnt =0.083854+0.233690  \times (yr) +0.571918 \times (temp) - 0.147367 \times (windspeed) + 0.082444 \times (season_2) +0.125072 \times (season_4)-0.250231 \times (weathersit_3) + 0.086771 \times (mnth_9)$

## Final Result
**Train ${R}^2$:**  0.800

**Train Adjusted ${R}^2$:**  0.797

**Test ${R}^2$:**  0.767

**Test Adjusted ${R}^2$:**  0.764

This seems to be Good model which explains 80% of the variance in Training dataset and explains 76.7% of the variance in Test dataset
    
     
  


