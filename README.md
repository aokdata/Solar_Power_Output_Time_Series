# U.S. Solar Power Output Time Series Analysis and Forecasting
Aidan O'Keefe

<img width="921" alt="Stock_Solar_Panels" src="https://user-images.githubusercontent.com/120589094/228377991-11ed5604-4bb3-4fc4-a275-21271304ed66.png">
*Image provided by Freepik*

# Overview
Univariate time series analysis and modeling project of solar power output in the United States.

# Business Overview
The North American Electric Reliability Corporation (NERC) regulates the electrical grid in the United States, Canada, and the northern part of Baja California, Mexico. They have asked us to try to forecast solar output in order to help them manage the US grid better.

# Data Overview
Data for this project was taken from the U.S. Energy Information Administration's Electricy Data Browser. The data has monthly frequency from Jan 2001 to Dec 2022 of solar output in thousand megawatthours. Each row is a location with power output grouped by individual state, region, and US Total.

Upon exploring the data, there is obvious seasonality with more solar power being produced in the summer months.
![US Monthly Solar Output by Year](https://user-images.githubusercontent.com/120589094/228961427-3023b549-5c64-4a1b-a24c-751a5b6382be.png)

# Methods Overview
To preprocess the data, I turned our raw csv into a datetime indexed dataframe of only Total US Solar Power Output. After trying to use rolling statistics, differencing and other transformations, I successfully stationarized the timeseries data using time series decomposition and confirmed stationarity using the Augmented Dickey-Fuller Test. I implemented a Naive model, a variety of SARIMAX/ARIMA models (including parameter search), and a Facebook Prophet model.

# Evaluation Overview
An ARIMA (4,0,1) model was chosen as the final model based on it's AIC and RMSE. On test data, the final model had a RMSE of 0.033 thousand megawatthours and a MAPE of 2.32%. We then forecasted US Solar output 12 months out using our final ARIMA(4,0,1) model (as well as the FB Prophet model for comparison).

## Test- ARIMA(4,0,1)
![ARIMA401_Test](https://user-images.githubusercontent.com/120589094/228961206-6b0d5a76-f8ac-4b17-a872-e1ddfe378fe1.png)

## Forecast- ARIMA(4,0,1)
![ARIMA401_Solar_Predictions](https://user-images.githubusercontent.com/120589094/228961073-a4288d5b-e99b-43f6-ad79-480df491f146.png)


# Reccommendations
I would recommend that NERC create a forecast to predict supply and avoid blackouts/grid failure caused by overproduction. The NERC can then prepare plan to meet seasonal supply and demand in conjunction with traditional energy sources.

# Next Steps
I would testing this forecast in the next year and calculating errors to see if the model is accurate enough to be helpful moving forwad. I would also add in data on the number on power plants as well as environmental factors (weather, solar irradiation) so the model accounts for more external factors. In the future, I would look to repeat this time series modeling and forecasting at the regional and state level in order to provide more actionable data.







## Repository Structure
```
├── data
├── .gitignore
├── README.md 
├── Solar_Power_Output_Time_Series_Notebook.ipynb
└── presentation.pdf
```
