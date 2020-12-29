# :chart_with_upwards_trend: Time-series-forecasting

 This repository is aiming to Time Series Forecast over a given dataset. The goal of the exercise is to find the most appropriate model and make some predictions.

*Forecast done in R*

<p align="center">
  <img src="https://www.analyticsindiamag.com/wp-content/uploads/2018/12/timser.gif"/>
</p>



## Subject

The file Elec-train.xlsx ([dataset](https://github.com/IsmaelMekene/Time-series-forecasting/blob/main/dataset/Elec-train.xlsx)) contains electricity consumption (kW) and outdoor air temperature for one building.

These quantities are measured every 15 minutes, from 1/1/2010 1:15 to 2/16/2010 23:45. In addition, outdoor
air temperature are available for 2/17/2010. The goal is to forecast electricity consumption (kW) for
2/17/2010.

Two forecasts should be returned, in csv files entitled prediction and prediction with temperature:

1. the first one without using outdoor temperature,
2. the second one using outdoor temperature.

Of course, the goal is to get the best possible forecasting. 




## Solution


### Visualization

R has a broad range of packages that make data visualization more exciting. We will focus on:
- [x] forecast
- [x] ggplot2

As used in the [code](https://github.com/IsmaelMekene/Time-series-forecasting/blob/main/model/TimesSeries.ipynb) and by using the 80:20 ration, the observation can easily be done.

<figure align="center">
    <img src="https://github.com/IsmaelMekene/Metaheuristics--Stochastic-Optimization/blob/main/images/visuatraintest.png"/>
    <figcaption>Electricity Consumption (kW per hour)</figcaption>
</figure>


### 1. Forecast without outdoor temperature
 
 
### 2. Forecast using outdoor temperature
