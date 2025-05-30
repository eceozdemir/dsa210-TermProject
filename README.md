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

Energy charged (kWh): Daily energy data will be obtained through the Tesla, showing how much electricity I charged into the car each day.The raw dataset included fields like start/end times, charger type, and location. These were filtered to retain only the total energy charged per day.


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

Mean: 10.44 kWh
Median: 0.00 kWh
Mode: 0.00 kWh

2. Bar Charts
![image](https://github.com/user-attachments/assets/5c5d89c5-f601-4735-93e5-1594ecdde77a)

Average Monthly Charging: Highlighted that some months had significantly higher average energy usage.
Weather Condition Frequency: Cloudy and Rainy days were the most common

3. Weather-wise Energy Charts

Created separate daily bar charts showing energy charged on each day, grouped by weather category (Cloudy, Rainy, Snowy, Windy, Sunny).
![image](https://github.com/user-attachments/assets/e66e404e-00ac-4942-90d1-48913a37eacb)
![image](https://github.com/user-attachments/assets/d7eb7ccb-6ea3-43d4-99dd-9374e4d14b59)
![image](https://github.com/user-attachments/assets/9c2990ba-0fb8-473d-af82-aeb07f58b73d)
![image](https://github.com/user-attachments/assets/70fc0343-3c11-45ac-94d3-1abe380ac024)




4. Boxplot
![image](https://github.com/user-attachments/assets/a58860b0-dc31-4c8a-8ac7-d66f49a3d8cb)

Illustrated the variation in energy charged across different weather conditions. Sunny days showed the highest median charging.

5. Line Plot
![image](https://github.com/user-attachments/assets/8db4d471-f184-4f7c-b342-8ef3ed44fbf8)


Visualized the time series trend of energy charged over the full dataset period.

6. Correlation Heatmap
![image](https://github.com/user-attachments/assets/a58d8084-5fa7-49ad-9533-d3beb66ad1b2)


Computed correlation matrix between weather variables and energy charged:

-Weak negative correlation with humidity.
-Slight positive correlation with windspeed and temperature.

7. Pairplot
![image](https://github.com/user-attachments/assets/5b4c1a3f-9d01-40e1-819f-277f733f1a09)

Provided a multi-variable visual analysis of relationships between energy charged and weather variables.


Hypothesis Testing
--
T-Test Results:

T-Statistic: -0.854

P-Value: 0.3940

Conclusion: P-value > 0.05, so we fail to reject the null hypothesis. 

Conclusion
--
This project aimed to explore whether environmental conditions affect my Tesla charging habits. Despite general expectations that cold or bad weather increases EV energy consumption, my personal data shows no statistically significant difference in charging behavior on rainy or snowy days. Additionally, predictive modeling using only weather variables produced low to moderate performance, supporting the idea that weather alone is not a strong predictor of energy charged. Nonetheless, this project provided valuable insights into my own data and highlighted the importance of using personalized datasets in data science projects for real-world understanding.

Machine Learning Techniques
--
Regression: Predicting Daily Energy Charged (kWh)
Objective:
The goal of this machine learning task was to predict the amount of energy (in kWh) charged into the Tesla vehicle using environmental weather variables. The motivation was to examine whether temperature, humidity, wind speed, and precipitation (rain/snow) can explain variations in charging behavior.

Results Overview:

Regression Model: Random Forest Regressor

Features Used:

-temperature_2m

-relative_humidity_2m

-windspeed_10m

-rain_binary

-snowfall_binary

-bad_weather (binary: rain or snow)

*Regression RMSE* (Root Mean Squared Error): 34.56
Indicates the average deviation of predicted values from actual energy charged.

*Regression MAE* (Mean Absolute Error): 16.32
Reflects the average absolute difference between predicted and actual values.

- Scatter Plot: Actual vs. Predicted Energy
  ![image](https://github.com/user-attachments/assets/eacf7eaf-79a3-458c-b00b-099e48af310b)

Most points cluster near the red diagonal line, indicating good prediction accuracy.
A few outliers exist, suggesting days with unusual charging behavior the model couldn't capture.

- Bar Chart: Average Actual and Predicted Energy by Weather Type
  ![image](https://github.com/user-attachments/assets/8079e2ed-2b5e-4b21-a6c1-deb7c5067296)

The model successfully distinguished between clear and bad weather days.
It predicted slightly higher than actual values for rain/snow days but followed the general trend.

- Confusion Matrix: Binned Energy Usage Categories
  ![image](https://github.com/user-attachments/assets/abd07b0c-6e54-431c-bb70-b453d1aa29b3)

Energy usage was grouped into bins (0–10, 10–20, etc.) to evaluate classification performance.
Most predictions lie along the diagonal, meaning the model correctly identified energy usage categories.
Some misclassifications were made especially at higher ranges, possibly due to data imbalance or behavioral variance.

Limitations and future work
1.time period is limited (only 1 year )
2.Driver habits, trip distance and car usage patterns are not included.


- AI tools were utilized to assist with improving clarity in written explanations, enhancing the structure of this README, correcting syntax errors, and debugging faulty code. However, the analytical work, modeling steps, and result interpretations were completed through personal effort.
