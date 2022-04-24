# DATA 606 Capstone Project Report

## Effectiveness of the COVID-19 policy responses using Machine Learning

by Hugues Nelson Iradukunda

### Introduction

This research investigates the influence that governmental policy responses have had on the COVID-19 pandemic around the world.

Since March 2020, Coronavirus disease (COVID-19) was declared as a global pandemic.
As of today, the COVID-19 infections are over 500 millions cases and the death toll is about 6 millions worldwide.
Several restrictions and policies were imposed by countries to minimize the infections and deaths.

Being able to understand drivers and predict Coronavirus disease confirmed cases can be used in policy and decisions making regarding the restrictions or lockdown measures. 
In addition, citizens can understand how governments are working in terms of fighting against COVID-19 in a consistent way. 
Form the government perspective, being able to predict COVID confirmed cases could be used to measures what policy responses are effective.

The goal of this study is to use machine learning model with a focus to understand effectiveness of the governmental policy responses to COVID-19 worldwide with latest information.

### Hypothesis/ Research Question(s)

This study will focus on answering the following questions:

1. Have policy responses contributed in preventing COVID-19 over the past 2 years?
2. Are the collected COVID-19 policy responses statistically significant in predicting the infections?
3. What are COVID-19 policy responses drivers in predicting the confirmed cases?


### Unit of Analysis

Overall, we have 186 countries worldwide in this dataset.
The countries are represented in the data by their names.


### Dataset Description

The timeserie data being explored comes from [COVID-19 GOVERNMENT RESPONSE TRACKER]
(https://github.com/OxCGRT/covid-policy-tracker).
presented by the Oxford Covid-19 Government Response Tracker (OxCGRT). 
<br>
The OxCGRT systematically collects information on several different common policy responses governments have taken, records these policies on a scale to reflect the extent of government action, and aggregates these scores into a suite of policy indices.
The different COVID-19 policy responses are coded into 21 indicators, such as public places closures, travel restrictions, testing and vaccinations.
Those COVID-19 policy responses are into grouped five categories:
1. C - containment and closure policies
2. E - economic policies
3. H - health system policies
4. V - vaccination policies
5. M - miscellaneous indicator
<br>
There is a strigency index where a higher score indicates a stricter government response (i.e. 100 = strictest response) based on policy indices. 
However, the stringency index cannot say whether a government's policy has been implemented effectively.
<br>
This data also include the number of reported Covid-19 confirmed cases and deaths in each country. 
These are collected by the [Center for Systems Science and Engineering (CSSE) at Johns Hopkins University](https://github.com/CSSEGISandData/COVID-19) data repository for all countries and the US States.

### Exploratory Data Analysis (EDA)

#### Data correlation 
![Heatmap](https://github.com/IradukundaHN/Hugues_DATA606/blob/main/Images/Heatmap.png?raw=true)

#### Trends of top 10 countries by confirmed cases

#### Trends of top 10 countries with high confirmed cases and their given stringency index

#### Table of Top 10 countries by COVID-19 Cases and their highest Stringency Index so far


### Machine Learning Model

#### Preprocessing data methods

#### Ordinary Least-Squares (OLS) regression model

#### Residuals

#### Linear Regression Model Pipeline

#### Ridge Regression for model regularization



### Interpretations and Conclusions

1. Have policy responses contributed in preventing COVID-19 over the past 2 years?
2. Are the collected COVID-19 policy responses statistically significant in predicting the infections?
3. What are COVID-19 policy responses drivers in predicting the confirmed cases?

### References

1. https://github.com/OxCGRT/covid-policy-tracker
2. https://github.com/CSSEGISandData/COVID-19
3. https://www.bsg.ox.ac.uk/research/research-projects/covid-19-government-response-tracker
