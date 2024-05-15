# NYC-Green-Taxi-Trip-Analysis

## Project Overview
This project delves into the NYC Green Taxi Trip Data spanning from January 2022 to January 2023. Green Taxis, which are authorized to pick up passengers from the street outside Manhattan's central business district and airports, were introduced to enhance taxi services in typically underserved areas. They now share operational territories with Yellow Taxis, which were once confined to Manhattan and airports, thus broadening their operational scope. The project focuses on employing regression and classification machine learning techniques to accomplish two primary objectives:

1. **Fare Amount Prediction:**
   By using data points such as pickup and drop-off locations, trip distances, and timestamps along with other relevant attributes, the aim is to build a regression model that predicts the fare for individual taxi trips, thereby improving fare estimation accuracy.

2. **Profitable Pickup Location Identification:**
   By analyzing data on pickup locations, trip distances, and fare amounts, this project aims to create a clustering model designed to pinpoint profitable pickup spots for Green Taxis, helping drivers optimize their routes for better earnings.

## Dataset Characteristics

- **Trip Record Data:** Sourced from the New York City Taxi and Limousine Commission (TLC), this dataset comprises 908,613 recorded trips.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/b843569b-4894-4f1c-8dbf-3d2ff51bb344)

- **Taxi Zone Map Dataset:** Contains 265 records used to correlate location IDs in the main dataset with corresponding NYC boroughs, zones, and service areas.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/afeba543-d5ef-4a71-ad13-3a29f2e3177e)

- **Holiday Dataset:** A custom dataset created to differentiate trips on holidays, regular weekdays, and weekends, comprising 23 recorded holidays.

## Initial Data Distribution Analysis

1. **Trip Distance:** The data shows an average trip distance of 78.72 miles, ranging from 0 to 360,068.14 miles, with most trips covering between 1.15 and 3.73 miles.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/0be2cde1-8eef-4f80-8a15-09ea3059e893)

2. **Fare Amount:** Trips average a fare of $15.39, with fares ranging from -$350.08 to $2020.20 and most falling between $7.90 and $18.20.
  ![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/b45cd2ba-db49-4f41-a4e4-aa8480a8f012)

3. **Payment Mode:** The majority of transactions (64%) are made with credit cards, followed by cash (36%), with less than 1% involving disputes or no charge.
   ![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/a9bef1f3-a491-4358-a1d4-822f496b7645)


## Feature Engineering

- **Taxi Zone Integration:** Enhances dataset with additional information about pickup and drop-off boroughs and zones.

- **Column Management:** Ineffective columns are removed, and relevant columns are renamed to standardize data formats.

- **Trip Filtering and Cleaning:** Trips are filtered to exclude those with irregular fares or distances, and those missing essential data are removed.

- **DateTime Feature Extraction:** New features like 'dayofweek' and 'pickuphour' are created to enhance analysis capabilities, including identifying peak hours and holiday trips.

- **Congestion Surcharge Identification:** Adds a flag to denote trips including a congestion surcharge.

## Exploratory Data Analysis Highlights

- **Vendor Analysis:** Shows disparity between two vendors with one overwhelmingly dominating the market share.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/75af4145-9b62-4362-b1b6-9b0389ec7c3f)

- **Rate Code Usage:** Identifies frequency of different rate codes, highlighting standard and negotiated rates as the most common.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/4afd2833-de76-4bf8-bba6-4a0c849da3f8)

- **Hourly Trip Distribution:** Maps out the demand cycle across a day, showing peak periods during typical rush hours.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/5818652d-371c-4a6c-adf6-a283b5a8235d)

-- **Trip Distance**
After cleaning the data by removing trips with negative or overly long distances (over 100 miles), the dataset was reduced to 740,737 entries. The average distance of a trip significantly dropped to 2.99 miles. Trip distances now vary from a minimum of 0.01 miles to a maximum of 95.50 miles, with most trips falling between 1.28 and 3.60 miles. The median distance for these trips is 2.03 miles.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/afff2e91-621a-496a-9ade-30344a9f52dc)

-- **Fare Amount**
After excluding trips with fares below the minimum of $3, the average cost of a trip fell to $13.82, and the standard deviation narrowed to $11.31. Fare amounts now range from $3.50 to $499.00, with most trips costing between $7.50 and $16.00. The median fare, post-cleanup, is $10.50.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/d5d350e6-e188-4097-85c7-0d15ec5f6ac2)

-- **Trip Time**
By removing trips with either negative durations or those exceeding 180 minutes, the dataset was refined to 740,737 entries. This cleaning led to a reduction in the average trip duration to about 14.95 minutes, with a smaller standard deviation of 11.87 minutes. Durations now span from as short as 1.02 minutes to as long as 178.55 minutes. The bulk of the trips last between 7.75 and 18.32 minutes, with the median trip time now at 11.97 minutes. This adjustment allows for a more precise analysis of trip durations within practical limits.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/121c2d66-4ed5-4ac7-a4cf-0879fd41832a)

-- **Trip Distribution by Day**
Taxi demand varies throughout the week, peaking on Wednesday with 117,543 trips, and remaining high on Tuesday and Thursday with 114,668 and 114,479 trips, respectively. Demand starts moderately on Monday with 103,797 trips and declines towards the weekend, dropping to 96,623 on Saturday and further to 82,432 on Sunday, illustrating a midweek high that diminishes as the weekend approaches.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/400fdf40-0eba-4503-a4e2-ddefefb573aa)

-- **Number of Trips by Pickup and Dropoff LocationID**
Pick-up: ![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/72e2e2b3-0fee-4524-9088-6f6ebfd99bda)
Drop-off: ![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/93d095f3-20e9-4d54-af80-b080f677db05)

The analysis shows distinctive cab demand patterns in various New York City neighborhoods. East Harlem North and South, along with Central Harlem and Morningside Heights, are key pickup areas due to their residential and cultural appeal, while the same neighborhoods plus Upper East Side North see high drop-off activity. The diversity in demand across these areas reflects their unique residential, cultural, and commercial makeup, particularly near landmarks like Central Park and university-centered Morningside Heights.

-- **Distance vs. Fare Amount**
Generally, fares increase with trip distance, but anomalies exist where fares are disproportionately high for short distances (around 5-6 miles) reaching up to $500. This suggests factors other than distance affect fare calculations, necessitating further analysis to understand these outliers.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/a17d548e-d753-4a25-9610-99b661cb225b)

-- **Distance vs. Pickup Hour**
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/c1cbd40d-ede8-4eee-9040-4ca8799c8dbc)

Data shows that trip distances typically range between 1.28 and 3.60 miles. Distances gradually increase from morning to evening, with a noticeable uptick during early and late night hours, indicating shifts in travel patterns or preferences that may involve longer trips at these times.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/d4763cc1-fd76-4f25-80f0-dccb70b1e9fc)

-- **Fare Amount vs. Weekday**
Fare amounts trend upwards throughout the week, peaking on Saturdays at an average of $14.20. This increase could be due to heightened demand, altered travel patterns, or a predominance of longer trips on weekends.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/b441d371-b1b5-48d5-b296-a6654a6f20b8)


-- **Tip Amount vs. Hours**
Tip amounts peak around the 5th hour of the day, dip, and then stabilize from around $1.50 to $2.00 until the 15th hour. A gradual increase follows, peaking again around the 20th hour, reflecting variable tipping behaviors depending on the time of day.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/d714055c-803c-4195-acc3-78c3b3db981a)


-- **Tip Amount vs. Weekday**
Tips gradually increase from Monday to Wednesday, fluctuate mid-week, and surge from Friday to Sunday, indicating a progression in tipping behavior as the week advances, with weekends seeing the highest tips.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/171deb5d-6c78-444c-87e4-123f2ed9fc00)


-- **Data Splitting & Dimension Reduction**
For regression analysis, 'fare_amount' is set as the target variable 'y', with other features encoded as 'X'. The dataset was split in a 60-40 ratio for training and testing, and dimensionality reduction was applied to capture significant variance within the first three components, optimizing the dataset for machine learning.
![image](https://github.com/NaithikShetty/NYC-Green-Taxi-Trip-Analysis/assets/66748504/60f37375-e718-4e9c-8525-0e3c5bb7606b)

## Modeling Summary for NYC Green Taxi Fare Prediction

Here's a breakdown of the regression models used to predict taxi fares:

-- **KNN Regression:** This model performed the best, achieving the lowest Mean Squared Error (9.91) and the highest R-squared (0.9233), which indicates excellent predictive accuracy. It also reported a relatively low Mean Absolute Error (1.24), underscoring its robust performance.

-- **Random Forest Regressor:** This model showed strong performance with a Mean Squared Error of 12.02 and a solid R-squared of 0.9069. Its Mean Absolute Error is close to that of the KNN Regression, making it an effective tool for fare prediction.

-- **Decision Tree:** With a Mean Squared Error of 11.24 and an R-squared of 0.9129, this model performs reliably. Its Mean Absolute Error is within an acceptable range, indicating precise fare predictions.

-- **Linear Regression:** This model displayed moderate performance with a Mean Squared Error of 14.07 and an R-squared of 0.8910. Its Mean Absolute Error, similar to the Decision Tree, suggests reasonable accuracy.

-- **Lasso Regression:** Similar in performance to the Linear Regression, this model also recorded a Mean Squared Error of 14.07 and an R-squared slightly lower at 0.8910. The consistency of its Mean Absolute Error with Linear Regression shows it provides acceptable predictions.

In summary, the KNN Regression model excels in predicting taxi fares, while the Linear and Lasso Regression models show lower accuracy in comparison to the other models. The selected performance metrics (Mean Squared Error, R-squared, Mean Absolute Error) effectively highlight the reliability and accuracy of each model in forecasting fare amounts.
