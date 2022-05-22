# DATA 606 Capstone Project Report

## Analysis of the COVID-19 policy responses using Machine Learning

by Hugues Nelson Iradukunda

### Introduction

This research investigates the influence that governmental policy responses have had on the COVID-19 pandemic around the world.

Since March 2020, Coronavirus disease (COVID-19) was declared as a global pandemic.
As of today, the COVID-19 infections are over a half billion cases and the death toll is about 6 millions worldwide.
Several restrictions and policies were imposed by countries to minimize the infections and deaths.

Being able to understand drivers that predict Coronavirus disease confirmed cases can be used in policy and decisions making regarding the restrictions or lockdown measures. In addition, citizens can understand how governments are working in terms of fighting against COVID-19 in a consistent way. 
Form the government perspective, being able to predict COVID confirmed cases could be used to assess what policy responses have been effective throughout the pandemic.

The goal of this study is to use machine learning model with a focus to understand effectiveness of the governmental policy responses to COVID-19 worldwide with latest data.

### Hypothesis/ Research Question(s)

This study will focus on answering the following questions:

1. Have restrictions contributed to minimizing COVID-19 daily infections over the past 2 years?
2. Are all the collected data regarding the policy responses statistically significant in predicting the confirmed cases?
3. What are the main policy responses drivers in predicting the confirmed cases?

### Dataset Description

- The timeseries data being explored comes from [COVID-19 GOVERNMENT RESPONSE TRACKER](https://github.com/OxCGRT/covid-policy-tracker) presented by the Oxford Covid-19 Government Response Tracker (OxCGRT). 
The OxCGRT systematically collects information on several different common policy responses governments have taken.
The OxCGRT records these policies on a scale to reflect the extent of government action, and aggregates these scores into a suite of policy indices all over 187 countries worldwide.
The different COVID-19 policy responses are coded into 21 indicators, such as public places closures, travel restrictions, testing and vaccinations.
Those COVID-19 policy responses are into grouped five categories:
C: containment and closure policies,
E: economic policies,
H: health system policies,
V: vaccination policies,
M: miscellaneous indicator.
There is a strigency index variable where a higher score indicates a stricter government response (i.e. 100 = strictest response) based on policy indices. 

- This data also include the number of reported Covid-19 confirmed cases and deaths in each country around the globe. 
These are collected by the [Center for Systems Science and Engineering (CSSE) at Johns Hopkins University](https://github.com/CSSEGISandData/COVID-19) data repository for all countries and the US States.
</p>

### Exploratory Data Analysis (EDA)

#### Data correlation 
![Heatmap](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/Heatmap.png?raw=true)
- Obviously, the stringency index is correlated with the government policy responses used in this dataset, such as public events cancelation, school closing, and other restriction measures.

#### Table of Top 10 countries by COVID-19 Cases and their highest Stringency Index so far
![Table](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/Top10ConfirmedCasesandStringencyIndex.png?raw=true)
- A higher position in stringency index does not necessarily mean that a country's response is better in fighting with COVID than others lower on the stringency index. It is an indication of how strict a country is in terms of policy response.

### Machine Learning Model
- Target: `ConfirmedCases`. 
- Predictors variables: all remaining attributes, except string objects type representing countries names and codes which are excluded from the set. 
`Date` is also dropped from our model training set.
`ConfirmedDeaths` is correlated to ConfirmedCases, so it is not necessary for our model since we are looking to study the COVID-19 policy responses.
![image](https://user-images.githubusercontent.com/59127471/169708412-a2aaab75-a508-406e-9aec-370b5c902ef8.png)


#### Ordinary Least-Squares (OLS) regression model
![OLS](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/OLS.png?raw=true)

<p>
According to the OLS Model results:

- Overall, OLS Model  𝑅-ssquared  is 0.136, so our model is capturing around 14% of the variance in `ConfirmedCases`.
- The attributes used in this dataset are statistically significant except `C6_Flag`, `E4_International support`, `H5_Investment in vaccines`, `M1_Wildcard`, `V2D_Medically/ clinically vulnerable (Non-elderly)`,`StringencyIndexForDisplay`,
`StringencyLegacyIndex`,
`V2B_Vaccine age eligibility/availability age floor (general population summary)_30-34 yrs`,
`V2B_Vaccine age eligibility/availability age floor (general population summary)_50-54 yrs`,
`V2B_Vaccine age eligibility/availability age floor (general population summary)_65-69 yrs`,
`V2B_Vaccine age eligibility/availability age floor (general population summary)_70-74 yrs`,
`V2C_Vaccine age eligibility/availability age floor (at risk summary)_30-34 yrs`,
`V2C_Vaccine age eligibility/availability age floor (at risk summary)_50-54 yrs`,
`V2C_Vaccine age eligibility/availability age floor (at risk summary)_60-64 yrs`,
`V2C_Vaccine age eligibility/availability age floor (at risk summary)_70-74 yrs`,
`V2C_Vaccine age eligibility/availability age floor (at risk summary)_75-79 yrs`,
`V2C_Vaccine age eligibility/availability age floor (at risk summary)_80+ yrs` since they have a greater than the usual significance level 0.05.
- `V4_Mandatory Vaccination (summary)`, `H2_Testing policy`, `H8_Protection of elderly people` are the main strongest drivers of ConfirmedCases predictions because of their high t-statistics.
</p>

#### Residuals
![Residuals1](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/ResidualDistribution.png?raw=true)
- The residuals has a near-normal distribution. Therefore, there is no concerns with the residuals.

#### Linear Regression Model
- The 80% of data is used for training and the rest 20% for testing.
- Data preprocessing: 
Standardization of numerical values,
Transformation of categorical variables into dummy variables.
![LinearRegression](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/LinearRegression.png?raw=true)
- The 𝑅² scores for both training and testing sets are near 14%.
No indication of model overfitting.


#### Ridge Regression for model regularization
![Ridge](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/RidgeRegression.png?raw=true)

- Using the ridge regression model, the  𝑅-squared  is still around 14% for both training and testing data sets. Therefore, Ridge regression does not seem to change the model for the better fitting. 

#### XGBoost for Regression Model
- XGBoost is a gradient boosting algorithm. It provides parallel boosting trees algorithm that can solve Machine Learning tasks. 
- This XGBRegressor model is using 100 boosting trees (n_estimators=100).
- Below is the top 20 features of importance according to XGBRregressor Model:
![XGBRegressor](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/XGBRegressor.png?raw=true)

### Interpretations and Conclusions
Based on the findings of this study, we can return to the hypothesis questions:
<p>
1. Have policy responses contributed in preventing COVID-19 over the past 2 years?
<br>
  Most of the policy responses contributed in minimizing the number of coronavirus disease infection rates, especially in the early phase of the pandemic. The stringency index was higher when the countries started imposing the lockdown measures after seeing the rise in infections and daily deaths during the pandemic.
</p>
<p>
2. Are the collected COVID-19 policy responses statistically significant in predicting the infections?
<br>
Ordinary Least-Squares (OLS) regression model used for this project show that not all the attributes or columns from this dataset were statistically significant. 
</p>
<p>
3. What are COVID-19 policy responses drivers in predicting the confirmed cases?
<br>
The COVID-19 policy responses drivers in predicting the confirmed cases are: `H2_Testing policy`, `V4_Mandatory Vaccination (summary)`, `H8_Protection of elderly people`.
The safety measures, such as mandatory vaccination, testing, and strengthening the immunization among the elders are critical to saving lives and recovering from COVID.
</p>

### References
1. https://github.com/OxCGRT/covid-policy-tracker
2. https://github.com/CSSEGISandData/COVID-19
3. https://www.bsg.ox.ac.uk/research/research-projects/covid-19-government-response-tracker
4. [Python Machine Learning, 3rd Edition, Raschka and Mirjalili](https://www.packtpub.com/product/python-machine-learning-third-edition/9781789955750).
