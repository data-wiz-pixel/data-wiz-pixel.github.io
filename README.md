# Insight Analyst
Top skills: Data Modelling, Data Visualisation, Analysis, Data Storytelling, Power Query, DAX

## Navigation
- [About Me](#about-me)
- [Projects](#projects)
- [Online Retail Inventory Forecasting](#online-retail-inventory-forecasting)
- [Data Preparation](#data-preparation)
- [Train/Test Split](#train-test-split)
- [Forecasting](#forecasting)
- [Project Outcome](#project-outcome)



## About me
I’m an Insight Analyst with a passion for turning complex data into clear, actionable insight that supports real-world decision-making. I specialise in Power BI, DAX, Data Stroytelling and data visualisation, and I take pride in building intuitive, accessible dashboards grounded in UX design that help stakeholders understand and act on data with confidence.

My work spans a wide range of public sector projects, including care home relocation analysis, workforce planning, telephony demand modelling, environmental reporting, and programme evaluation. I’ve developed end-to-end data solutions—from API integration and data transformation through to reporting and storytelling—with a strong focus on automation, efficiency, and usability.

Currently completing a Level 6 Data Scientist Apprenticeship, I’m expanding my skillset into Python, machine learning, and forecasting techniques, applying these methods to real operational challenges such as demand prediction and service optimisation.

I’m particularly interested in:

- Building data products that drive operational change
- Applying analytics and modelling to public services
- Improving processes through automation and smarter data pipelines
- Creating clean, accessible, and user-focused visualisations

Beyond technical delivery, I enjoy collaborating with colleagues, sharing knowledge, and supporting others—whether that’s through training sessions, mentoring, or simplifying complex concepts for non-technical audiences.

My goal is to continue developing as a well-rounded data professional, combining technical expertise, business understanding, and clear communication to deliver meaningful impact.

# Projects

## Online Retail Inventory Forecasting
This project explores how time series forecasting can be used to better understand online retail demand patterns and support smarter inventory planning, using a publicly available online retail dataset from [UC Irvine Machine Learning Repository](https://archive.ics.uci.edu/dataset/502/online+retail+ii)

### Data Preparation
To prepare it for analysis, the data was cleaned by removing cancelled orders, filtering out records with negative or zero quantities and prices, and converting key columns into the correct data types. This ensured that the analysis focused only on valid sales activity.

To create a meaningful forecasting dataset, I transformed the transactional data into a daily time series, calculating total sales value per day by multiplying quantity by price and then aggregating this over time. This allowed me to move from individual purchases to a clearer view of overall demand trends. I then visualised the data to understand how purchasing behaviour changed over time.

#### Demand Over Time
![Line Chart](/images/demand_over_time.png)

Plotting the series helped reveal fluctuations in sales volume, while seasonal decomposition (STL) was used to separate the data into its underlying components:

#### Seasonal Decomposition (STL)
![Line Chart](/images/observations.png)
- Trend – the long-term direction of sales
- Seasonality – repeating short-term patterns
- Residuals – random variation not explained by the trend or seasonality

This step was important because it showed whether the series contained regular patterns that could be modelled and forecasted.

## Train Test Split
To test the forecasting approach, the dataset was split into training and test sets, using earlier observations to train the model and the most recent 30 days to evaluate performance. I then applied an Exponential Smoothing (ETS) model with additive trend and seasonality, designed to capture recurring weekly demand patterns.

![Line Chart](/images/train_test.png)


## Forecasting
Once the model was fitted, forecasts were generated for the next 30 days and compared them against the actual observed demand. This made it possible to visually assess how closely the model followed real sales behaviour and whether it could provide a reliable basis for inventory planning.

![Line Chart](/images/forecast_atuals.png)

The Mean Absolute Error (MAE) was calculated to measure performance, which shows the average size of the forecasting errors in the same units as the data. 
MAE:12940.21

Next, this was converted into an error rate and estimated model accuracy relative to average daily demand. These metrics provided a practical way to interpret how useful the forecast would be in a real business setting.

- Average Daily Demand: 27,555.86
- Mean Absolute Error (MAE): 12,940.21 units
- Model Error Rate:46.96%
- Model Accuracy:53.04%

Finally, the residual errors were analysed by plotting their distribution. This helped assess whether the model errors were centred around zero and whether there were any obvious biases in the forecast. A good forecasting model should produce residuals that are relatively balanced and random, suggesting that the main demand patterns have been successfully captured.

![Line Chart](/images/forecast_residuals.png)

## Project Outcome
This project demonstrates how forecasting can turn historic retail transactions into forward-looking insight. By combining data cleaning, time series decomposition, forecasting, and model evaluation, through a workflow that could help a retailer anticipate demand more effectively and make better inventory decisions.
