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
  <u>Figure 1: Electricity Consumption (kW per hour)</u>
  </figure>


### 1. Forecast without outdoor temperature
 
It is not always an easy task to find the most appropriate model for a given dataset. However, we will stick on a searching methodology that has proven to be effective.

Starting with the Exponential Smoothing models, we will observe those not using seasonal patterns and then move to the ones that use them.

- **Exponential Smoothing**
  
  - **Non-seasonal pattern**
  
  In this section, we have focused on models that do not use seasonal pattern. A comparasion has been done in between the Simple Exponentional Smoothing and the Non-seasonam Holt-Winters. After setting the parameters, alpha in SES to NULL and (alpha, beta) to (NULL, NULL) we can observe it on Figure 2.
  
  <p align="center">
  <img src="https://github.com/IsmaelMekene/Metaheuristics--Stochastic-Optimization/blob/main/images/nonseasonal.png"/>
  <figcaption> Figure 2: Simple Exponential Smoothing vs Non-seasonal Holt-Winters </figcaption>
  </p>
  
  <p align="center">
  <img src="https://www.analyticsindiamag.com/wp-content/uploads/2018/12/timser.gif"/>
  </p>
  
  It is clearly seen on Figure 2 that both models are not appropriate.
   
  - **Seasonal pattern** 
  
  We will now focus the forecasts over the seasonal patterns and linear trends.
  
  - [ ] **Additive seasonal Holt-Winters**: paramaters (seasonal='additive', h=900)
  - [ ] **Multiplicative seasonal Holt-Winters**: paramaters (seasonal='multiplicative', h=900)
  - [ ] **Damped additive seasonal Holt-Winters**: paramaters (seasonal='additive', h=900, damped=TRUE)
  - [ ] **Damped multiplicative seasonal Holt-Winters**: paramaters (seasonal='multiplicative', h=900, damped=TRUE)
  
  After setting the parameters, we can observe the plot on Figure 3.
    
  <p align="center">
  <img src="https://github.com/IsmaelMekene/Metaheuristics--Stochastic-Optimization/blob/main/images/seasonalandlinear.png"/>
  <figcaption> Figure 3: Additive seasonal vs Multiplicative seasonal vs Damped additive vs Damped multiplicative</figcaption>
  </p>
    
  The models on Figure 3 are still not suitable.

 
 
### 2. Forecast using outdoor temperature

