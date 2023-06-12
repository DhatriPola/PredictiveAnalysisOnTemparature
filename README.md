# PredictiveAnalysisOnTempareture

INTRODUCTION:
In the recent decades, abnormal weather such as heavy snow, heavy rain and drought has been occurring more frequently in all parts of the world resulting in human injury and death, property damage, and health and environmental issues. As the temperature is quite unstable at present, it is causing global warming. As a result, temperature prediction and forecasting are important fields of research because of their applications in real-world events such as agricultural weather forecasting, airport environment forecasting, tourism, and so on. But due to the chaotic structure of the atmosphere, temperature prediction and forecasting studies are extremely difficult. This project aims at predicting Bangalore's temperature by taking into account significant parameters such as humidity, wind speed, dew point, and pressure.


PROBLEM STATEMENT:
The primary objective of this project is to forecast the temperature of Bangalore city using Univariate and Multivariate Time Series. The secondary objective is to check the impact of Humidity, Wind Speed, Dew Point and Pressure on Temperature.


RELATED WORKS:
Inyoung Park and team [1] used a vast amount of model training data to construct a temperature prediction model based on Deep Learning. The long short-term memory (LSTM) neural network, which is a recurrent neural network that is ideal for time-series data modeling, was used to refine and restore missing data. The performance of this LSTM based model which predicted the temperature by three time steps was measured by its root-mean-squared error (RMSE) and compared to the RMSEs of a Feedforward Deep Neural Network. A further model was extended to predict 7 and 14 day future temperatures, and its performance was measured by its root-mean-squared error (RMSE).

Zhang Kaicheng and his colleagues looked at two different approaches to lightweight thermal predictors. They used feature selection algorithms to improve the performance of previous designed machine learning methods. Later, developed methods based on neural networks and linear regression, and performed various prediction models with higher prediction accuracy, and the generated optimization methods reduced average prediction errors. Models that used Neural Networks and Lasso Linear Regression produced average prediction errors. They proposed prediction models on a two-node system configuration to help identify the optimal task placement and these models achieved great success rates with better thermal response [2].


LIMITATIONS OF EXISTING WORKS:
One of the limitations in existing works was collecting weather data that had many data points missing. Thus, the collected data are apt to be incomplete with random or extended gaps. The used time series model had a low accuracy rate which showed huge deviations from the existing values.

ADVANTAGES OF PROPOSED SOLUTION:
The proposed solution will forecast the temperature of Bangalore city for every month for 2 years. Along with the prediction, the solution will also find the influence of Humidity, Wind Speed, Dew Point and Pressure in the increase or decrease of Temperature of the city.

DATA DESCRIPTION:
The monthly temperature data for Bangalore was collected from the Weather Underground Website which consisted of 6 variables namely Time, Temperature (° F), Dew Point (° F), Humidity (%), Wind Speed (mph) and Pressure (Hg). The data was gathered during a nine-year period  from January 2012 to April 2022. The website reported maximum, minimum and average values for these variables from which the  average values were considered for this project [3].

METHODOLOGY:
This project focuses on Univariate and Multivariate Time Series Forecast of Temperature for the next 2 years by considering the existing and present values. 

1.Univariate Time Series Analysis:
A Univariate Analysis of the Temperature variable was performed, and the same was forecasted for the next two years. To check the Trend and Seasonality of the data, it was decomposed into different patterns. The modeling procedure is as follows:

1.1.Stationarity test: Time Series models rely on the assumption that data is stationary and this can be tested by the Augmented Dickey-Fuller (ADF) test. 
The Hypothesis for this test can be considered as: 
Null Hypothesis, H0: Data is not stationary and 
Alternative Hypothesis, H1: Data is stationary. 
The decision about the hypothesis can be made by p-value. The test confirmed that data is not stationary and differencing has to be performed on the data to make it stationary.  

1.2.Modeling:
ARIMA (AutoRegressive Integrated Moving Average) model is a non-stationary model used to predict the future values and is an extension of ARMA (Autoregressive Moving Average model) stationary model.  The Autoregressive Integrated Moving Average Model is a type of Regression Analysis that measures the strength of one dependent variable in relation to the change in other variables. The model's purpose is to forecast future securities or financial market movements by studying the discrepancies between the serial data rather than actual values.

1.3.Selection of best model
The AIC value obtained for the model was 425.612 which is far less than the value obtained by other models. Once the best model was found, it was fitted using the SARIMAX() function and was tested on the test data which contained the previous 3 years temperature values. The same model was used to forecast the temperature for the next 2 years. 

2.Multivariate Time Series Analysis
Vector Auto Regressive (VAR) Multivariate Model was used in forecasting the future temperature values. The system of equations for a VAR model with two time series variables Y1 and Y2 is as follows.
                   
Before building a model for a Multivariate Time Series data, we should select the features which are significant to the model. This can be tested by the following tests:

Granger’s Causality Test
If the obtained p-value of the features using this test are less than 0.05 we can infer that they have a significant relation between them and the features with greater p-values are dropped.  As the test resulted in all the features having p-values which are less than 0.05 we can conclude that all the variables are significant and are related to each other. 

Cointegration test
Cointegration is used to determine the statistical relationship between two or more time series. The tests are designed to identify the degree of sensitivity between two variables to the same average price over a certain period of time. The test resulted in significance of the variables on the whole system.

As two tests resulted in all the features being significant, we can use the preprocessed data to fit the model. The modeling procedure is as follows.


Training and Test Data:
The whole data was divided into training and test data based on months. The training data contains the temperature values for every month ranging from January, 2012 to April, 2021. The data from May, 2021 to April, 2022 was taken for test data.

Checking for Stationarity:
The main assumption of the Time series is the stationarity of data and the ADF(Augmented Dickey Fuller) test was used to check this. The test resulted in data not being stationary for 1st order differencing but being stationary for 2nd order differencing.  

Selecting the order of (P) of VAR model:
The 2nd order differenced data was modeled with VAR function to determine the optimum p value for the model. The optimum value was chosen based on the AIC value and the models with least AIC value are considered. It was 9 in this case. 

Training the VAR model:
After fitting the model with the value p = 9 and using the model summary function, we can check patterns, equations and methods used for modeling. The model prints the coefficient, standard error, t-statistic, and probability value for all the variables from Lag 1 to 9 (as the p value is 9). It also gives the residual correlation.   

Checking for Serial Correlation of Residuals using Durbin Watson Statistic:
Serial Correlation of Residuals is used to check if there is any pattern left in the residuals which was not considered. This is one of the important parameters to be considered because if there is some pattern in the time series that is still left to be explained by the model then the results will be inappropriate. This can be overcome by either increasing the order of the model or inducing more predictors into the system or looking for a different algorithm to model the time series. The result showed that the value of the statistic is close to 2 which implies that there is no significant serial correlation and the model is the best fit of the data. 

Forecasting result for test data:
The model is a good fit for the training data and now this can be implemented on the test data to observe the patterns and compare it with the actual values. But the obtained results are in differentiated form and this has to be converted to original form for comparison and this is carried out in the next step.

Invert Transformation to get Actual Forecast:
Since the obtained forecasted values are in the 2nd order differenced form, a user defined function ‘invert_transformation()’ has been used which will convert back the differenced values to actual values. In order to display the variation between actual and forecasted values, the values were reverted to their original form and a plot was produced. 

Evaluation of the Forecasted Values:
The efficiency of models was measured by calculating the Mean error (ME), Mean Absolute error (MAE), Mean Percentage error (MPE), Mean Absolute percentage error (MAPE) and Root Mean Squared error (RMSE). As all the above parameters resulted in less values, the obtained model is accurate and best suited to the data.

Extending the model for complete data and predicting for next 2 years:
Now that the model is trained well and tested on the dataset, it can be implemented on the entire dataset and predict the unknown temperature values for future years. The above process is repeated on training data again but here the entire dataset is considered for training. The trained model was used to predict the future Temperature, Humidity, Dew Point, Wind Speed and Pressure values.

RESULTS
After a successful Univariate and Multivariate Modeling, the results are as follows.

Univariate modeling:
1.It is evident from the plot that temperature shows high correlation among the beginning lags, indicating the presence of autocorrelation. The autocorrelation decreases with increasing lags until it is negligible after the 80th lag.
2.The graph shows that the model is best fit for the data because the variations predicted from the model are approximately the same as the actual values.  Hence this model is used to predict the next 24 months temperature values and the plot for the same is plotted below.
3.The line graph with orange color indicates the forecasted values and the one in blue indicates the present values. It is evident from the graph that the forecasted values are following the same trend and seasonal behavior as the present values. According to the predicted values, the temperature would be high during the middle of the year after which it gradually decreases. At the end of the year, the temperature would be minimum.

Multivariate modeling:
1.The plots show the difference between the original values and forecasted values. But from the plot we can infer there exist huge deviations from the original values because the model was constructed on the differenced data.
2.The graph infers that the forecasted values would tend to follow the same stationarity behavior as the present values. According to the predicted values, the temperature would be high during the middle of the year after which it gradually decreases. At the end of the year, the temperature would attain a minimum value.


CONCLUSIONS:
Based on the results obtained from the research, it is obvious that the temperature will tend to follow the same pattern as now but with a more increased upward trend. The main reason for this would be because of the effect of greenhouse gases. An enormous amount of harmful gases present in the atmosphere are trapping the sun’s heat from leaking into the atmosphere thus resulting in global warming. A study conducted by a researcher [4] revealed that human activities are one of the main contributions to global warming. A survey concluded that 2011 - 2020 was the warmest decade ever recorded. Therefore, it is the responsibility of every person to minimize emissions of these harmful gases that result in global warming, thereby lowering the temperatures and deflecting direct UV (Ultra Violet) rays from the sun. 







