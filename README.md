# Predict the minimum support price


Problem statement
-----------------

**Note**: This is a time-series-based problem.

A commodity is a basic good used in commerce. It is interchangeable with other similar goods. Examples of commodities include grains, gold, meat, oil, and natural gas.

For investors, commodities are an important way to diversify their portfolios beyond traditional securities. However, commodity prices are volatile as are commodity exchanges which are also dynamic. For many financial institutions, worldwide commodity trading has become an important means of making a profit.

One of the main reasons for the price changes in commodities is the inflation rate. The inflation rate is affected by the price of production costs that mainly depend on the final price of the goods and services in a market. Therefore, price changes of the most important commodities in the world's commodity exchange markets influence the price of local producers or imported production.

**Task**

You are given datasets that are related to each other.

Your task is to use these datasets to predict the MSP (minimum support price) of various commodities mentioned across some months in a year that are provided in the test data.

Data description
----------------
|Dataset name|Description|No. of rows|No. of columns|
|----|---|---|---|
|commodityID_and_details.csv|Contains various commodities that are sold in the market with their respective identification numbers|142|2|
|wpi_and_inflation.csv|Contains information about wholesale price index and the inflation of various commodities|13728|4|
|train.csv|Contains important features such as cost of production, policy changes, climatic factors (masked), etc. that influence the MSP value|7000|11|
|test.csv|Contains two features, Month-year and commodity_name|69|2|
|sample_submission.csv|Contains a sample format of your submission file|69|3|

The datasets contain the following columns:

**commodityID\_and\_details.csv**

|Column name|Description|
|--- |--- |
|CommodityID|Represents a unique identification number of a commodity|
|Commodity_name|Represents the name of a commodity|

**wpi\_and\_inflation.csv**

|Column name|Description|
|--- |--- |
|CommodityID|Represents a unique identification number of a commodity|
|Month-year|Represents a month of the year Format: YYYY/MM/DD|
|Wholesale Price Index|Represents the WPI value of a commodity|
|Inflation (CPI) %|Represents the inflation value of a commodity|

**Note**

*   Due to policy changes, some months of a year can have more than one inflation value. You can take the average of the inflations for modeling. 
*   This dataset must be used for both _**test.csv**_ and **_train.csv_**.

**train.csv** 

|Column name|Description|
|--- |--- |
|Month-year|Represents the month of a year Format: YYYY/MM/DD|
|CommodityID|Represents a unique identification number of a commodity|
|Production weight (in million tonnes)|Represents the production weight of a commodity (in tonnes)|
|Labour_availability|Represents the following types of availability of labor in the market: <br/> <ol><li> Abundant </li><li> Low </li><li> Moderate</li></ol>|
|Govt_policy_change|Represents whether there is any change in government policies with respect to a commodity <br/> Here, there are two values: <ol> <li>Yes: Represents that there is a policy change</li><li> No: Represents that there is no policy change</li></ol>|
|Demand|Represents the level of demand of a commodity <br/> Here, there are five levels: <br/><ul> <li> High: Represents a high demand for a specific period of time</li> <li>Low: Represents a low demand for a specific period of time </li> <li>Long-run: Represents a demand that is expected to not fall for a long period of time</li> <li>Short-run: Represents a demand that is expected to fall after a short period of time </li><li> Very-low: Represents almost no significant demand of a commodity</li></ul>|
|Cost of production|Represents the cost of production of a commodity (in INR)|
|Climatic factor 1 (masked)|Represents a climatic factor that can affect a commodity’s production, demand, or cost|
|Climatic factor 2 (masked)|Represents a climatic factor that can affect a commodity’s production, demand, or cost|
|Maximum price per kg|Represents the ceiling price set by the government with respect to a commodity (in INR)|
|Minimum support price (in Rs/Quintal) (target)|Represents the minimum support price or floor price of a commodity|


**test.csv**

|Column name|Description|
|--- |--- |
|Month-year|Represents the month of a year|
|Commodity_name|Represents the name of a commodity|


**Note**: In test data, you are required to predict the target value for a _Month-year_ of a specific commodity only. 

Evaluation metric
-----------------

    100*max(0, 1-metrics.mean_squared_log_error(actual, predicted))
