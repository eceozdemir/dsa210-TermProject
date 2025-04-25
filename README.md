# dsa210-TermProject


Project Overview


In this project, I will analyze the relationship between the daily energy (kWh) charged to my Tesla vehicle and the weather conditions on that day. The goal is to explore whether certain weather parameters (e.g., temperature, humidity, wind speed) influence the amount of energy I charge into my car. Understanding this relationship could help identify patterns in energy consumption behavior depending on environmental factors.


Hypothesis 

Null Hypothesis (H₀): There is no significant relationship between daily weather conditions and the amount of energy (kWh) charged to the Tesla.

Alternative Hypothesis (H₁): There is a significant relationship between daily weather conditions and the amount of energy (kWh) charged to the Tesla.

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

Weather information will be obtained from Open-Meteo. Since the API does not directly provide daily average values, hourly data for parameters such as temperature, humidity, and wind speed will be collected for each day and averaged by dividing the sum by 24 to obtain a representative daily value.

-Energy Data:

Daily energy consumption data (in kWh) will be obtained from Tesla. The raw dataset provided by Tesla includes additional variables such as charging start and end times, duration, location, and charger type. These irrelevant fields will be filtered out to retain only the total energy charged per day.

-Data Cleaning:

Unnecessary columns will be removed, missing values will be handled appropriately, and the data will be aligned by date to ensure both weather and energy data correspond to the same day.

-Exploratory Data Analysis (EDA):

Initial analysis will focus on identifying patterns and trends in daily energy consumption and how they vary with temperature, humidity, and other weather conditions. This will involve statistical summaries and visualizations.

-Regression Analysis:

Statistical modeling techniques such as linear regression will be used to examine the relationship between weather variables (independent variables) and the amount of energy charged daily (dependent variable). The aim is to determine if specific weather conditions are associated with increased or decreased charging behavior.



