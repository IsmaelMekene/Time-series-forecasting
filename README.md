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

  <p align="center">
  <img src="https://github.com/IsmaelMekene/Metaheuristics--Stochastic-Optimization/blob/main/images/visuatraintest.png"/>
  <figcaption>Figure 1: Electricity Consumption (kW per hour)</figcaption>
  </p>


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
  
 
  It is clearly seen on Figure 2 that both models are not appropriate.
   
  - **Seasonal pattern** 
  
  We will now focus the forecasts over the seasonal patterns and linear trends.
  
  - [ ] **Additive seasonal Holt-Winters**: paramaters (seasonal='additive', h=900)
  - [ ] **Multiplicative seasonal Holt-Winters**: paramaters (seasonal='multiplicative', h=900)
  - [ ] **Damped additive seasonal Holt-Winters**: paramaters (seasonal='additive', h=900, damped=TRUE)
  - [ ] **Damped multiplicative seasonal Holt-Winters**: paramaters (seasonal='multiplicative', h=900, damped=TRUE)
  
  _see_ [code](https://github.com/IsmaelMekene/Time-series-forecasting/blob/main/model/TimesSeries.ipynb)
  
  
  After setting the parameters, we can observe the plot on Figure 3.
    
  <p align="center">
  <img src="https://github.com/IsmaelMekene/Metaheuristics--Stochastic-Optimization/blob/main/images/seasonalandlinear.png"/>
  <figcaption> Figure 3: Additive seasonal vs Multiplicative seasonal vs Damped additive vs Damped multiplicative</figcaption>
  </p>
    
  The models on Figure 3 are still not suitable.
  We can try to stabilize the variance by Box-Cox transformation in the previous Additive HW models.
  - [ ] **Additive seasonal Holt-Winters**: paramaters (seasonal='additive', h=900, lambda = 'auto')
  - [ ] **Damped additive seasonal Holt-Winters**: paramaters (seasonal='additive', h=900, damped=TRUE, lambda = 'auto')
  
  _see_ [code](https://github.com/IsmaelMekene/Time-series-forecasting/blob/main/model/TimesSeries.ipynb)
  
  After setting the parameters, we can observe the plot on Figure 4.
  
  <p align="center">
  <img src="https://github.com/IsmaelMekene/Metaheuristics--Stochastic-Optimization/blob/main/images/boxcox.png"/>
  <figcaption> Figure 4: Stqbilization in Additive HW models</figcaption>
  </p>
 
  As we can see a small omprovement on the previous results, it is preferable to compute the root mean square error (RMSE) of each model to have a better view.
  - [x] RMSE in Simple Exponentional Smoothing: 60.76483
  - [x] RMSE in Non-seasonam Holt-Winters: 64.57402
  - [x] RMSE in Additive seasonal Holt-Winters: 73.46383
  - [x] RMSE in Multiplicative seasonal Holt-Winters: 73.40462
  - [x] RMSE in Damped additive seasonal Holt-Winters: 60.91925
  - [x] RMSE in Damped multiplicative seasonal Holt-Winters: 60.48178
  - [x] RMSE in Additive seasonal Holt-Winters Stabilised: 70.18168
  - [x] RMSE in Damped additive seasonal Holt-Winters Stabilised: 60.84705
  
  _see_ [code](https://github.com/IsmaelMekene/Time-series-forecasting/blob/main/model/TimesSeries.ipynb)
  
  **RECAP**:
  The model with the lowest error so far is Damped multiplicative Holt-Winters, however; this is not because it is the best model (See that the prediction pattern is not correlate with pattern of test set).     
This low error is just because our calculation base on mean different and Damped multiplicative Holt-Winters gives us the linear model that situates around the middle of the graph.    
We should also consider that all alpha, beta, gamma and phi parameters used above are automatically chosen just to screen and see the pattern of each forecasting model.    
Therefore, if we really want to compare between each model, the parameters should be fixed.    
(For example, if you want to compare the effect of damped version to multiplicative Holt-Winters model, you should fix alpha, beta and gamma for both model (the only difference will be with or without phi parameter))    
But we will not consider them now since clearly we cannot use any exponential smoothing for our forecast.


### 2. Forecast using outdoor temperature

