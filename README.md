# US-Home-Price-Estimator

## Introduction
The United States real estate market is a dynamic and multifaceted landscape, shaped by economic conditions, demographic trends, interest rates, and regional variations. Over the years, the affordability of housing has become a significant challenge for many individuals and families, as property prices continue to rise. This project aims to address this issue by developing a predictive model that leverages historical data and location demographics to provide accurate estimates of house prices across the U.S.

The objective is to analyze key factors influencing real estate values, such as location, property size, and amenities, to better understand the determinants of housing affordability. By doing so, the project seeks to provide stakeholders with data-driven insights into property valuation, enabling more informed decision-making for buyers, sellers, investors, and policymakers. The choice of this topic stems from its widespread relevance and practical implications in today’s housing market. Rising housing costs have made homeownership increasingly unattainable for many, prompting the need for tools and analyses that can shed light on market trends and property valuations. A predictive model can serve multiple purposes: helping buyers assess the fairness of asking prices and make better purchasing decisions, offering sellers insights into the value of their property and optimal pricing strategies, identifying opportunities for investors based on undervalued or overvalued properties, and informing policy makers on housing policies and affordability programs by understanding key drivers of price increases.

This project seeks to answer several questions: 

1. What are the most significant factors influencing house prices in the U.S.? 

2. How accurately can a predictive model estimate house prices based on property characteristics and location demographics? 

3. How can predictive modeling help address housing affordability and market accessibility for different stakeholders? 

By addressing these questions, the project hopes to illuminate the nuances of the U.S. housing market and contribute to a deeper understanding of the challenges and opportunities within it.

## Source of Data
### Data Summary
In this project, we have used three different datasets in order to optimize our model performance. There is a combination of various data types in the initial dataset, highlighting some initial obstacles that our group must overcome in the cleaning process. The objective is to build a predictive model to determine the house price in the U.S. market.

### Description
Below is a detailed description of each of the features in our datasets:
1. “realtor-data.csv” (12 columns with 2,226,382 entries)

| Attribute        | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| `brokered_by`    | Categorically encoded agency/broker                                         |
| `status`         | Housing status – either (a) ready for sale or (b) ready to build            |
| `price`          | Housing price: either current listing price or recently sold price          |
| `bed`            | Number of bedrooms                                                          |
| `bath`           | Number of bathrooms                                                         |
| `acre_lot`       | Property / land size in acres                                               |
| `street`         | Categorically encoded street address                                        |
| `prev_sold_date` | Previously sold date                                                        |
| `city`           | City name                                                                   |
| `state`          | State name                                                                  |
| `zip_code`       | Postal code of the area                                                     |
| `house_size`     | House area/size/living space in square feet                                 |



2. `uszips.csv` (18 columns, 33,784 entries)

For this dataset, we specifically chose the following attributes that we are interested in and merged with our previous dataset:

| Attribute   | Description                                                   |
|-------------|---------------------------------------------------------------|
| `zip`       | The 5-digit zip code assigned by the U.S. Postal Service.     |
| `lat`       | The latitude of the zip code.                                 |
| `lng`       | The longitude of the zip code.                                |
| `population`| An estimate of the zip code's population.                     |
| `density`   | The estimated population per square kilometer.                |



3. “us_income_zipcode.csv” (111 columns with 33,774 entries)

• For this dataset, we specifically chose only the “Households Median Income” column and merged with our previous dataset for further analysis.

| Attribute   | Description                                                   |
|-------------|---------------------------------------------------------------|
| `Households Median Income (Dollars)`       | Income in U.S. dollars per household     |

## Models Explored
1. Linear Regression
2. Random Forest Regressor

With the ultimate goal of optimizing the predicting model, we split our process for linear regression into 6 stages:
Stage 1 - Run model with Kaggle dataset
Stage 2 - Zip Code demographics / location coordinates explored
Stage 3 - Zip code level median income explored
Stage 4 - Considered city-level data (Ex: Orlando)
Stage 5 - Re-considered the national-level data and explored state indicators
Stage 6 - Stage 4 Orlando model fit with the data standardised

## Conclusion
Predicting house prices by fitting a regression model to the data is quite an engaging task for a data scientist. However, delving into the data reveals the complexity and challenges involved in the process. Often the data at hand is not as clean as expected nor the relationships are obvious between dependent and independent variables. In the beginning phases of our project, we observed many outliers that heavily affected the model outcome. We spent significant time processing the data by fixing the outliers and imputing the missing values.

Then, upon plotting bivariate scatter plots and fitting preliminary models, we realized that there are nuances in the data that are not easy to capture with a simple linear fit. As we dealt with US-wide real estate data, we have come to a sort of understanding that - for example - a smaller house in New York would cost more than a bigger house in Dallas, which breaks the linearity between house size vs price. Therefore, to better tackle the issue, we have come up with two solutions: a linear regression model on city-level data, and a random forest regression on US-wide data with as many as 50 indicator variables, one for each state. This latter one is considered a non-parametric model that doesn't make many strict assumptions about the data. In our data exploration, some of the most important factors for house price were house size, number of beds, number of baths, location, and income for the area. In future explorations, it would be ideal to continue to find attributes that influence house price. 

In the real world, the choice of model depends heavily on the specific business context. For regional-level house price movements, where simplicity and explainability are paramount, linear regression is often a suitable choice. Its straightforward nature facilitates communication and stakeholder understanding. However, if the goal is to build an automated system for real-time price estimates across the entire country with minimal user input, a more complex model like Random Forest Regression might be preferred. While less intuitive, these models can achieve high predictive accuracy and effectively handle a variety of factors.
