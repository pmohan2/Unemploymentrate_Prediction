### EAS 503 - Programming and Database Fundamentals for Data Science
### Prediction of State-wise Unemployment Rate in US
## Introduction
*The U.S Department of Labor, specifically the Bureau of Labor Statistics (BLS), began collecting employment information via monthly household surveys. Other data series are available back to 1912. The unemployment rate has varied from as low as 1% during World War I to as high as 25% during the Great Depression (in most countries it started in 1929 and lasted until 1941. It was the longest, deepest, and most widespread depression of the 20th century). More recently, it reached peaks of 10.8% in November 1982 and 10.0% in October 2009. Unemployment tends to rise during recessions and fall during expansions. From 1948 to 2015, unemployment averaged about 5.8%. The United States has experienced 11 recessions since the end of the postwar period in 1948.*

*The U.S. Bureau of Labor Statistics has defined the basic employment concepts as follows:*
- People with jobs are employed.
- People who are jobless, looking for jobs, and available for work are unemployed.
- People who are neither employed nor unemployed are not in the labor force.
*Predicting unemployment rates will be helpful for the state level planning of job market.*

*Note: This analysis and prediction is based on the assumption that the COVID-19 has not occurred and the trend continues.*


---

## Sources
[Demographic Characteristics](https://data.census.gov/cedsci/table?d=ACS%205-Year%20Estimates%20Data%20Profiles&table=DP05&tid=ACSDP5Y2015.DP05)
- Demographic data refer to the Decennial Census and other surveys of individuals
and households administered by the Census Bureau.
- Includes Sex and Age, Race, Hispanic Origin, Housing Units, etc.

[Economic Characteristics](https://data.census.gov/cedsci/table?d=ACS%205-Year%20Estimates%20Data%20Profiles&table=DP03&tid=ACSDP5Y2015.DP03)
- Economic data or economic statistics are data (quantitative measures) describing an
actual economy, past or present.
- Includes Income, Employment, Occupation, Commuting to Work, etc.

[Social Characteristics](https://data.census.gov/cedsci/table?d=ACS%205-Year%20Estimates%20Data%20Profiles&table=DP02&tid=ACSDP5Y2015.DP02)
- Social, cultural, religious and other characteristics of a person or group of people which contribute to the specification of the population to which they belong. For example, first language spoken, indigenous status, religious affiliation, sex.
- Includes Education, Marital Status, Relationships, Grandparents, etc.

[Unemployment Rate](http://www.dlt.ri.gov/lmi/laus/us/annavg.htm)
- Includes year wise Unemployment Rate Data.
---

## Database Creation
- Raw data has been extracted for each aspect (Social, Economic, Demographic,
Unemployment Rate) from year 2010 to 2018.
- Created a Database with 36 tables for the respective raw data.
- Populated each table with the values from the raw data.
- Performed ‘UNION ALL’ operation in combining the year-wise data of each aspects
with the help of Common Table Expression (CTE).
- Performed ‘INNER JOIN’ operation in merging the data of each aspect with the help
of Common Table Expression (CTE).
- Finally queried the merged data from the Database for Feature Engineering,
Exploratory Data Analysis (EDA), and Model Fitting.


## Packages used for EDA
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from ipywidgets.embed import embed_minimal_html
```
- *Note:The following packages need to be installed:* 
- *pip install seaborn*
- *pip install ipywidgets.embed*

### Data Visualization:
*Exploratory Data Analysis is a process of conducting initial investigations on data set to identify patterns, anomalies, to test hypothesis and to check assumptions with the help of summary statistics and graphical representations. Before removing the outliers from the dataset the distribution of predictors are highly skewed which is evident from the below scatter matrix plot. After removing outliers, the distribution of parameters turns out to be normalized. Making the predictor more normalized gives us the better model.*
*The insights that can be derived from the Scatter Matrix Plot are:*
- *Most of the trips recorded had the passenger count to be in two’s and three’s, this shows that most of the passengers who opted for the yellow taxi tends to travel in two’s and three’s the most.*
- *Most number of trips recorded had passengers travelling less than 30 miles, which makes sense as yellow taxis are commonly used for short trips within NYC.*
- *Similarly average trip duration lies within fifty minutes.*

#### Scatter Matrix Plot (Raw Data):

![Image of Plot](Images/scatter1.png)

#### Scatter Matrix Plot (Final Data):

![Image of Plot](Images/scatter2.png)

#### Monthly Fluctuation of Demand:

*The line graph shows the monthly fluctuation of demands for the top 5 locations (location with most number of rides in the year 2019) and can be inferred that the demand for yellow taxi was at the peak during the month of March at Madison square. Minimum demand was observed during the month of January and December. This might be due to the impact of winter vacation. Also, the similar downward trend was observed during the summer vacation.*

![Image of Plot](Images/Top5.jpeg)

#### Heat Map (Weekly vs Hourly):

*The following Heat Map compares weekly vs hourly taxi demand and it is evident that the demand was maximum during weekdays. Also, it can be inferred that demand was at its peak from evening to late in night. It is understood that people prefer to take yellow taxi during night time rather than the public transport.*

![Image of Plot](Images/Heatmap.jpeg)

#### Temperature vs Demand:

*From the Temperature vs Demand plot we can see that there is an increase in trend for demand of taxis when the temperature is very low as well as the temperature is very high. This might be because people may decide their mode of transportation depending upon the atmospheric condition.*

![Image of Plot](Images/TempvsDemand.jpeg)

### Model Results:

![Image of Plot](Images/Results.png)

### Conclusion and Remarks:
- *This project focuses upon studying the behaviour of people who utilize yellow taxi in NYC and predict the demand by considering various factor like atmospheric conditions, etc.* 
- *There were a total of 255 different pickup and drop-off location zones in NYC. Due to computational limitations, we have decided to predict the demand for the top 20 zones were most number of trips were recorded.*
- *For these 20 zones, exploratory data analysis was conducted. From the EDA we have identified unique patterns and anomalies in taxi demand with respect to people’s behaviour and atmospheric conditions.*
- *Informed decision were made in choosing, tuning, training and testing the models and the results were interpreted based upon the best model. The model with best accuracy seems to be the Extreme Gradient Boosting (XG Boost).*
- *The XGB Model states that the factors Temperature, Wind Speed, Hour, Day and Pickup Location are the most significant factors in predicting the demand. Therefore, it is critical for taxi companies to consider these factors in allocating cabs for various locations in NYC.*
---
