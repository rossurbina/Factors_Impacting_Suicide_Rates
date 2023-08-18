# Factors_Impacting_Suicide_Rates
Correlation and Regression Analysis on Factors that Impact Suicide Rates

## Purpose
Suicides are a very complex and serious topic, and I wanted to examine which factors impact suicide rates. By understanding who is more likely to commit suicide through data based on factors, it can hopefully help to reduce the number of suicides. This analysis will look at the variation in social, economic, and political factors of each country in the United Nations to identify patterns that may explain variation in suicide rates around the world.

## Data Tools Used
I used Python in Jupyter Notebook to clean, transform, and analyze the data. Here is the link to the [Jupyter notebook file](https://github.com/rossurbina/Factors_Impacting_Suicide_Rates/blob/main/Factors_Impacting_Suicide_Rates.ipynb)

# Insights & Observations

## Correlation Analysis

Based on correlation analysis of various factors in our database compared to the suicide rate, I found the most and least correlated items to the suicide rate, shown below. 

![alt text](https://github.com/rossurbina/Factors_Impacting_Suicide_Rates/blob/main/Correlation_chart.png)

**Sex:** Sex has the highest correlation with suicide rates at 43%; men are much more likely to commit suicide than women. Note that the chart shows -43% because it’s looking at values of 1 for women and 0 for men.

**Age:** Age rank has the second highest correlation with suicide rates, meaning that older groups are more likely to commit suicide. Note that there are 6 age groups in the database, ranging from 5-14 years for the first group and 75+ for the last group. 

Those two factors are the only ones that have strong correlation with suicide rates, since all the other factors are less than 15% positively or negatively correlated. However, these are the factors that are slightly correlated with suicide rates, in the range of 10-15% correlation. Note that these correlations are likely too small to draw any conclusions off of:

• Urban population having access to drinking water (positive 14%)

• The percentage of females in the labor force within the person’s country (positive 12%)

• Percentage of Individuals using the Internet within the person’s country (negative 12%)

• Unemployment rate (negative 10%)

Further analysis is done into Age and Gender below since they are very highly correlated with suicide rates. 

![alt text](https://github.com/rossurbina/Factors_Impacting_Suicide_Rates/blob/main/Age_chart.png)

As the age value increases, the number of suicides also increases. We can take this to mean a country with an aging population is more likely to see higher levels of suicide. The first group (5-14) have hardly any suicides. The middle 4 age groups have steady growth from each category, then there is a large increase to the 75+ bar. Therefore, age is highly correlated with suicide rate, with wide variations between the youngest and oldest group. 

![alt text](https://github.com/rossurbina/Factors_Impacting_Suicide_Rates/blob/main/Sex_chart.png)

Shown above, men are almost 4 times more likely to commit suicide than women. Note that this is general data that will be different per country. 

## Regression Analysis

When the final dataset was cleaned, I split the cleaned data into training and testing data with 70% and 30% of the data, respectively, then fit the data into a Lasso linear model. This model generated a mean absolute error value of 7.66 and a mean absolute deviation score of 145.28.

After that, my goal was to calculate the lowest Mean Absolute Deviation (MAD) score possible, which measures the differences between the observed values and the predicted values (so a lower score is better).

The first step was to import multiple regression libraries, such as Linear Regression, Decision Tree Regressor, etc. then run each one of those models to see which ones performed the best. Each time I ran the code, the score varied because the training and test data was chosen at random. However, the first regression analysis on average produced a result of about -10.5.

I wanted to improve the score, so I did the following steps to improve the results: 

1. Created a for loop that drops one of the attributes, then re-run each of the regression models. If the model performs better without that attribute, then I removed that attribute from the list of attributes for the next regression analysis
2. Added the attribute that had the most positive influence on the score twice so it would affect the analysis more

This new model gave an average score about -13, which is better than the initial -10.5. The results varied depending on which data was randomly selected for test vs. train data, but the enhanced model performed better about 90% of the time. 


# Steps to Data Analytics Process

## Explore & Gather Data
I used 3 different databases for this analysis. Below are the links to each data source: 
• [WHO Suicides Rates](https://www.kaggle.com/datasets/szamil/who-suicide-statistics)

• [UNData Country Statistics](https://www.kaggle.com/datasets/sudalairajkumar/undata-country-profiles)

• [World Happiness Scores](https://www.kaggle.com/datasets/unsdsn/world-happiness)

## Cleaning & Transforming the Data with Python

• Merged the files together to run correlation & regression analysis on data

• Selected which columns we wanted to focus on for the analysis

• Created dummy columns for categorical data (sex and age), which was required for correlation and regression analysis

• The UN profile data used placeholder values of -99.0, '-99', '...', '.../...' to represent unavailable data, so I replaced those with NAN values for removal after merging

• Some columns had two attributes within 1 column, such as “45.1/27.0”, so split those into separate columns

• Basic data cleaning (dropped Null or 0 values, removed extra spaces, etc.)

## Data Visualization (Python matplotlib)

• Used Seaborn to generate various charts to help with correlation analysis (in Jupyter notebook file)

