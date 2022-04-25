# DATA 606 Capstone Project Report

## Effectiveness of the COVID-19 policy responses using Machine Learning

by Hugues Nelson Iradukunda

### Introduction

This research investigates the influence that governmental policy responses have had on the COVID-19 pandemic around the world.

Since March 2020, Coronavirus disease (COVID-19) was declared as a global pandemic.
As of today, the COVID-19 infections are over a half billion cases and the death toll is about 6 millions worldwide.
Several restrictions and policies were imposed by countries to minimize the infections and deaths.

Being able to understand drivers and predict Coronavirus disease confirmed cases can be used in policy and decisions making regarding the restrictions or lockdown measures. In addition, citizens can understand how governments are working in terms of fighting against COVID-19 in a consistent way. 
Form the government perspective, being able to predict COVID confirmed cases could be used to measures what policy responses are effective.

The goal of this study is to use machine learning model with a focus to understand effectiveness of the governmental policy responses to COVID-19 worldwide with latest information.

### Hypothesis/ Research Question(s)

This study will focus on answering the following questions:

1. Have policy responses contributed in preventing COVID-19 over the past 2 years?
2. Are the collected COVID-19 policy responses statistically significant in predicting the infections?
3. What are COVID-19 policy responses drivers in predicting the confirmed cases?


### Unit of Analysis

Overall, we have 186 countries worldwide in this dataset. Each country is represented in the data by its name.


### Dataset Description

- The timeserie data being explored comes from [COVID-19 GOVERNMENT RESPONSE TRACKER]
(https://github.com/OxCGRT/covid-policy-tracker) presented by the Oxford Covid-19 Government Response Tracker (OxCGRT). 

The OxCGRT systematically collects information on several different common policy responses governments have taken, records these policies on a scale to reflect the extent of government action, and aggregates these scores into a suite of policy indices.
The different COVID-19 policy responses are coded into 21 indicators, such as public places closures, travel restrictions, testing and vaccinations.
Those COVID-19 policy responses are into grouped five categories:
C: containment and closure policies,
E: economic policies,
H: health system policies,
V: vaccination policies,
M: miscellaneous indicator.

There is a strigency index where a higher score indicates a stricter government response (i.e. 100 = strictest response) based on policy indices. 
However, the stringency index cannot say whether a government's policy has been implemented effectively.

- This data also include the number of reported Covid-19 confirmed cases and deaths in each country. 
These are collected by the [Center for Systems Science and Engineering (CSSE) at Johns Hopkins University](https://github.com/CSSEGISandData/COVID-19) data repository for all countries and the US States.
</p>

### Exploratory Data Analysis (EDA)

#### Data correlation 
![Heatmap](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/Heatmap.png?raw=true)

#### Trends of top 10 countries by confirmed cases
![Trends1](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/Top10ConfirmedCases.png?raw=true)

#### Trends of top 10 countries with high confirmed cases and their given stringency index
![Trends2](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/Top10StringencyIndex.png?raw=true)

#### Table of Top 10 countries by COVID-19 Cases and their highest Stringency Index so far
![Table](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/Top10ConfirmedCasesandStringencyIndex.png?raw=true)
- A higher position in stringency index does not necessarily mean that a country's response is better in fighting with COVID than others lower on the stringency index. It is an indication of how strict a country is in terms of policy response.

- Some of policy responses contributed in minimizing the number of coronavirus disease infection rates, especially in the early phase of the pandemic.

### Machine Learning Model

The target variable is ConfirmedCases. And other remaining attributes are considered as inputs variables for our machine learning regression models.

#### Ordinary Least-Squares (OLS) regression model
![OLS](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/OLS.png?raw=true)

<p>
According to the OLS Model results:

- Overall, OLS Model  𝑅-ssquared  is 0.843, so our model is capturing 84% of the variance in ConfirmedCases.
- The attributes used in this dataset are statistically significant except H1_Flag, H7_Flag, V1_Vaccine Prioritisation (summary), V2G_Frontline workers  (healthcare), V2B_Vaccine age eligibility/availability age floor (general population summary)_55-59 yrs, V2B_Vaccine age eligibility/availability age floor (general population summary)_80+ yrs, V2C_Vaccine age eligibility/availability age floor (at risk summary)_16-19 yrs, V2C_Vaccine age eligibility/availability age floor (at risk summary)_55-59 yrs, and V2C_Vaccine age eligibility/availability age floor (at risk summary)_75-79 yrs since they have a greater than the usual significance level 0.05.
- ConfirmedDeaths, H2_Testing policy, V4_Mandatory Vaccination (summary), H8_Protection of elderly people are the main strongest drivers of ConfirmedCases predictions because of their high t-statistics.
</p>

#### Residuals
![Residuals1](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/EvaluateResiduals.png?raw=true)
<br>
![Residuals1](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/ResidualDistribution.png?raw=true)
<br>
The residuals has a near-normal distribution. Therefore, there is no concerns with the residuals.

#### Linear Regression Model
- With sklearn libaries, I performed training and testing sets split of 80/20. 
- Data preprocessing includes standardization of numerical values, transformation categorical variables into dummy variables. 
- The pipeline involves the linear regression model.
- The R-squared for both training and testing sets are about 84%. 
- No identication of model overfitting.

#### Ridge Regression for model regularization
![Ridge](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/RidgeRegression.png?raw=true)

- Using the ridge regression model, the  𝑅-squared  is still around 84% for both training and testing data sets. Therefore, Ridge regression does not seem to change the model for the better fitting. In conclusion, OLS model was also good by itself.

### Interpretations and Conclusions
Based on the findings of this study, we can return to the hypothesis questions:
<p>
1. Have policy responses contributed in preventing COVID-19 over the past 2 years?
<br>
  Some of the policy responses contributed in minimizing the number of coronavirus disease infection rates, especially in the early phase of the pandemic. The stringency index was higher when the countries started imposing the lockdown measures after seeing the rise in infections and daily deaths during the pandemic.
</p>
<p>
2. Are the collected COVID-19 policy responses statistically significant in predicting the infections?
<br>
Ordinary Least-Squares (OLS) regression model used for this project show that most the attributes or columns from this dataset are statistically significant, except  
H1_Flag, H7_Flag, V1_Vaccine Prioritisation (summary), V2G_Frontline workers  (healthcare), V2B_Vaccine age eligibility/availability age floor (general population summary)_55-59 yrs, V2B_Vaccine age eligibility/availability age floor (general population summary)_80+ yrs, V2C_Vaccine age eligibility/availability age floor (at risk summary)_16-19 yrs, V2C_Vaccine age eligibility/availability age floor (at risk summary)_55-59 yrs, and V2C_Vaccine age eligibility/availability age floor (at risk summary)_75-79 yrs.
</p>
<p>
3. What are COVID-19 policy responses drivers in predicting the confirmed cases?
<br>
The COVID-19 policy responses drivers in predicting the confirmed cases are: ConfirmedDeaths, H2_Testing policy, V4_Mandatory Vaccination (summary), H8_Protection of elderly people.
</p>

### References
1. https://github.com/OxCGRT/covid-policy-tracker
2. https://github.com/CSSEGISandData/COVID-19
3. https://www.bsg.ox.ac.uk/research/research-projects/covid-19-government-response-tracker
4. [Python Machine Learning, 3rd Edition, Raschka and Mirjalili](https://www.packtpub.com/product/python-machine-learning-third-edition/9781789955750).
