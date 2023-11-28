# ITM_Business-Analytics
Selecting the optimal location and route for air-taxi in SEOUL

# ITM_Business-Analytics-Project-Report-Team4 🖐
This is a team project that Selecting the optimal location and route for air-taxi in SEOUL



## 1. Topic description

![image](https://user-images.githubusercontent.com/66208800/201391151-8a332d2c-d1a0-49b2-ada5-8036e4907bbd.png)
+ The first goal of this project is to recommend ideal locations for air taxi stations upon the introduction of such a service, aiming to identify the most optimal stops.
   
+ Then, the second goal is to devise an efficient routing plan between these chosen locations, providing paths that minimize travel distance for passengers. 

## 2. Problem definition
+ As urban populations soar and the demand for efficient transportation intensifies, the current infrastructure struggles to keep pace, leading to exacerbated traffic congestion. The challenge is to innovate beyond the saturated capacity of roads and traditional public transit systems. Air taxis emerge as a prospective solution to these problems, offering an alternative mode of transportation that utilizes the underused airspace above cities.

The primary problem is the identification of strategic locations for air taxi stations that harmonize with urban layouts, optimize accessibility, and ensure maximum coverage with minimal disruption to existing cityscapes and regulations. The secondary problem is the development of an effective routing network that connects these stations, facilitating direct and efficient travel routes for passengers while minimizing the environmental impact and operational costs.
## 여기서부터 수정해야함.
## 3. Purpose of the analysis

### 1) Why Spain? 
+ In Spain, the funding system for renewable energies is quite effective. The share of renewables in total power plant capacity was 44 % on 31 December 2013. The share of renewables in total power demand has increased from less than 7 % in 2000 to more than 25 % in 2013. Moreover, Spain has a variety of possible renewable energy production such as wind and solar energy thanks to its topography and weather. Therefore, we selected Spain, which uses more than 40% of renewable energy, as a target and conducted an analysis.

### 2) Our Purpose
+ Our purpose is not only to analyze the relationship between weather and renewable energy production, but also to **find the optimal real-time electricity pricing models based on weather-related energy generation and consumption data**. Currently in Spain, only power transmission is under state control (REE, a state-owned enterprise), and power generation and distribution are operated by private companies.
We will use datasets for the energy, the weather, and the current Spanish TSO price (like SMP in Korea).
 
### 3) Our Constraints
+ Thus, our constraints are as follow:
  + 1) Our energy distribution policy considers only electric power transmissions from REE national power plants to substations of each company. 
  + 2) Loss of power due to distance is not considered.

### 4) Our Hypothesis
+ The price we predict could greatly enhance the profit of the entire region, rather than the price of electric energy under the TSO's current system.

### 5) Our Goal
+ By comparing the price predicted by the amount of fossil energy generation and the price predicted by the amount of renewable energy generation,we can determine how much renewable energy affects the price.  Using this, it is possible to predict prices using only renewable energy in the future even if the production of fossil energy is reduced, thereby encouraging the production of renewable energy at the national level.

## 4. Dataset
![image](https://user-images.githubusercontent.com/66208800/201389294-62d6d354-0a2f-4778-b956-7f6c11b88815.png)
+ *energy_dataset*

![image](https://user-images.githubusercontent.com/66208800/201389344-81317727-21da-42d1-b9c8-14b9d3cfca39.png)
+ *weather_features_dataset*

+ As for the datasets that will be used for this project, we found two main datasets on Kaggle uploaded by Nicholas Jhana that were last updated in 2019. In the former one, we have features about the energy consumption and production in Spain by the hour as well as the overall price of the energy. In the latter one, we have information about the weather in 5 cities in Spain such as Barcelona and Valencia and their respective temperature, rain, etc.

## 5. Preprocessing

### Feature extraction
  + Season contains spring, summer, autumn and winter and they need to be split to improve performance.
  + Energy generation is influenced by different season, so it is helpful to increase model performance.

## 6. Our models

### 1) Linear, Ridge and Lasso Regression
  + Linear regression is a linear model which represents the relationship between a scalar response and independent variables.
  + Ridge regression is used when the independent variables are highly correlated and lasso regression is used to improve the prediction accuracy.
  + The models are used to show performance improvement after feature extraction 'season' and to predict price using renewable and fossil energy dataset.
  
### 2) XGBoost Regression
  + XGBoost regression is the implementation of gradient boosting for regression predictive modeling and has very good prediction.
  + The model is used to predict price using renewable and fossil energy dataset.
  
### 3) Random Forest Regression
  + Random Forest regression is an ensemble technique performing both regression and classification with the use of multiple decision trees.
  + The model is used to predict price using renewable and fossil energy dataset.
  
### 4) ARIMA model
  + ARIMA model is forecasting a time series which can be made to be “stationary”.
  + The model is used to predict actual price by using datetime (Feature: price day ahead).


## 7. Evaluation

#### Season feature
 + Compare whether the season feature is used or not
 + Output is actual price and training models are Linear, Ridge and Lasso regression
 + When 'season' feature is used, the performance is improved

#### Fossil energy & Renewable energy
 + The correlation of attributes related to fossil energy was high
 + Split fossil energy dataset & renewable energy dataset
 + Use Linear, Ridge, Lasso, XGBoost and Random Forest model
 + XGBoost and Random Forest model: To compare accuracy, hyperparameter tuning and no hyperparameter tuning are used
 + In hyperparameter tuning, random search is used instead of grid search for speed and ordinal encoder is better than one hot encoder due to performance
 
 #### Evaluation results
  + We used **r2_score**, **mse**, and **mae** for evaluation metrics.
  + When comparing r2_score, renewable energy is generally larger than fossil energy
  + In renewable energy dataset, wind_speed, pressure and generation solar are important features
  + In fossil energy dataset, weather data and generation of energy data have a significant impact on predicting actual price
  + We need to consider the other model(ARIMA), because the previous models have rather low accuracy

## 8. Alternative(ARIMA)
  + Determining whether the time series is stationary or not with the Augmented Dickey-Fuller test.
  + Make the time series stationary and find the ARIMA parameter d
  + Do the ACF and PACF plot and find the parameters p and q
  + ACF plot is sinuosidal so we can use the ARIMA(p,d,0) model
  + Build the model and predict a forecast
  + Do it over different timespan: the ARIMA model is good for 1 and a half week
  + We need to update it regularly !

## 9. Conclusion
 + By considering R2 score, MSE and MAE, To best predict energy prices, we need to use a XGBoost MODEL in renewable energy dataset.
 + The model predicted prices better when considering renewables energy production data such as solar energy and biomass
 + The added feature 'season' impact positvely the price predictions
 + The R2 score is as low as 0.55 which means Spain does not produce enough renewable energy
 + The price decreases the more renewable energy is used
 + Additional datasets with features such as stock prices should be used in future work
