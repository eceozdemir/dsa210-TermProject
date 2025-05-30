# dsa210-TermProject


Project Overview
--

As a general understanding, it is widely known that electric vehicles tend to consume more energy in cold weather due to the use of heating systems inside the car and reduced battery efficiency. However, I wanted to investigate whether this pattern is also reflected in my own driving and charging behavior. If I tend to charge more on cold or bad weather days—such as rainy or snowy days—this would not only confirm general knowledge but also help me plan future road trips more cautiously by anticipating higher energy needs. With this motivation, the main objective of this project is to analyze the relationship between the daily energy (kWh) charged to my Tesla vehicle and the weather conditions on that day, and explore whether specific weather parameters (e.g., snow, temperature, wind) influence the amount of energy I charge into my car.


Hypothesis 
--
To test whether weather conditions impact my charging behavior, I defined the following hypotheses:

Null Hypothesis (H₀):  There is no significant difference in energy charged to Tesla between rainy/snowy days and other days.

Alternative Hypothesis (H₁): Rainy or snowy days significantly affect the energy charged.

Description of Dataset

Energy charged (kWh): Daily energy data will be obtained through the Tesla, showing how much electricity I charged into the car each day.

Weather conditions: Daily weather data including temperature, humidity, precipitation, snowfall, and wind speed will be collected using the Open-Meteo API.

Date: Each record will be associated with the exact date, allowing day-level granularity and matching between both datasets.

PLAN
--
Data Preparation and Analysis
At the end of the data collection period:

The dataset will be reviewed for completeness, consistency, and correctness.

-Weather Data:
Hourly weather data was obtained from the Open-Meteo historical weather API. The data included parameters such as temperature at 2 meters, relative humidity, precipitation, rain, snowfall, and wind speed at 10 meters. The request was made for the coordinates of my location in Istanbul (latitude: 41.01933, longitude: 29.015692), covering the date range from 30.06.2024 to 21.05.2025. The data was retrieved using the following API endpoint:
[https://archive-api.open-meteo.com/v1/archive?latitude=41.01933&longitude=29.015692&start_date=2025-01-01&end_date=2025-04-23&hourly=temperature_2m,relative_humidity_2m,precipitation,rain,snowfall,windspeed_10m&timezone=Europe%2FIstanbul
](https://archive-api.open-meteo.com/v1/archive?latitude=41.01933&longitude=29.01569&start_date=2024-06-30&end_date=2025-05-21&hourly=temperature_2m,relative_humidity_2m,rain,snowfall,windspeed_10m&timezone=Europe%2FIstanbul)

Since Open-Meteo does not directly provide daily averages, I manually calculated the daily means by averaging the 24 hourly observations for each variable.
I am planning to use snow, rain and wind datas as only 0 or grater than 0 which will be easy to see the affect of the weather .

-Energy Data:

Daily energy consumption data (in kWh) will be obtained from Tesla. The raw dataset provided by Tesla includes additional variables such as charging start and end times, duration, location, and charger type. These irrelevant fields will be filtered out to retain only the total energy charged per day.

-Data Cleaning:

Unnecessary columns will be removed, missing values will be handled appropriately, and the data will be aligned by date to ensure both weather and energy data correspond to the same day.

Explonatory Data Analysis (EDA)
--
1. Univariate Analysis

Histogram: Displayed the distribution of daily energy charged, showing a right-skewed shape.

Summary Statistics:

Mean: 11.19 kWh
Median: 0.00 kWh
Mode: 0.00 kWh

2. Bar Charts

Average Monthly Charging: Highlighted that some months had significantly higher average energy usage.
Weather Condition Frequency: Cloudy and Rainy days were the most common

3. Weather-wise Energy Charts

Created separate daily bar charts showing energy charged on each day, grouped by weather category (Cloudy, Rainy, Snowy, Windy, Sunny).

4. Boxplot

Illustrated the variation in energy charged across different weather conditions. Sunny days showed the highest median charging.

5. Line Plot

Visualized the time series trend of energy charged over the full dataset period.

6. Correlation Heatmap

Computed correlation matrix between weather variables and energy charged:

-Weak negative correlation with humidity.(?
-Slight positive correlation with windspeed and temperature.

7. Pairplot

Provided a multi-variable visual analysis of relationships between energy charged and weather variables.


Hypothesis Testing
--
T-Test Results:

T-Statistic: -1.285

P-Value: 0.2024

Conclusion: P-value > 0.05, so we fail to reject the null hypothesis. Rain does not have a statistically significant impact on energy charging.

Conclusion
--
-Most Tesla charging days occur under cloudy or rainy conditions.
Weather conditions like rain or snow do not significantly affect daily energy charged based on statistical testing.
Energy usage is highly variable and weather features alone are not good predictors.

Limitations and future work
1.time period is limited (only 4 months )
2.Driver habits, trip distance and car usage patterns are not included.
