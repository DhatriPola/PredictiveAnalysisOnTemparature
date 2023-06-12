# PredictiveAnalysisOnTemparature

Prediction of Temperature for European Union Countries

Introduction
In the last several decades, abnormal weather, such as cold weather, heavy snow, heavy rain, and drought, has been occurring more and more frequently in all parts of the world, causing human injury and death, property damage, and health and environmental problems. Temperature measures the degree of hotness or coldness, indicating the direction in which heat energy flows. There are three temperature scales used at present namely, degree Celsius, degree Fahrenheit and degree Kelvin. At present the temperature is very uncertain which is leading to global warming. Hence temperature prediction and forecasting are important fields of research due to its applications in real-world events like agricultural weather prediction, airport environment prediction, tourism, etc.. and its effectiveness in human life, to know what happens for unpredictable situations and events. Temperature prediction and forecasting research are very challenging due to the chaotic nature of the atmosphere. This project aims to predict the temperature of European Union countries by considering radiation as an important factor.


Problem Statement
The main objective of the project is to forecast the temperature of European Union countries. The secondary objective is to check the impact of radiation on temperature. Multivariate Time Series models are used to forecast the temperature.


Related works
Inyoung Park and team created a temperature prediction model based on deep learning and a large amount of model training data was used. The model was used to refine missing data and restore missed data, for the long short-term memory (LSTM) neural network was used which is recurrent neural network and is suitable for time-series data modeling. After the missing data is refined, the LSTM-based model was retrained by refined data. This LSTM-based model predicted the temperature by three time steps and a further model was extended to predict 7 and 14 day future temperatures and its performance was measured by its root-mean-squared error (RMSE) and compared with the RMSEs of a feedforward deep neural network [1]. Zhang Kaicheng and team took two avenues and explored lightweight thermal predictors.  They used feature selection algorithms to improve the performance of previous designed ML methods. Later, developed methods using neural networks and linear regression-based methods and perform some prediction models which have better prediction accuracy and the obtained optimization methods reduce the average prediction errors. And newly developed models using neural networks and Lasso linear regression had average prediction errors. They proposed prediction models on a two-node system configuration to help identify the optimal task placement and  those models achieved good percent success rates with better thermal response [2].


Limitations of existing works
One of the limitations in existing works was collecting weather data had many data values missing. Thus, the collected data are apt to be incomplete, with random or extended gaps. The used time series model had a low accuracy rate which showed huge deviations from the existing values.


Advantages of proposed solution
The proposed solution will forecast the temperature of European Union countries for every hour which will be predicted for 2 years. Along with the prediction, the solution will also find the influence of radiation in the increase or decrease of temperature of these countries. 


References
[1] Inyoung Park, Hyun Soo Kim ,Jiwon Lee ,Joon Ha Kim, Chul Han Song, Hong Kook Kim, "Temperature Prediction Using the Missing Data Refinement Model Based on a Long Short-Term Memory Neural Network".
[2] Kaicheng Zhang, Akhil Guilani, Gokhan Memik, "Machine Learning-Based Temperature Prediction for Runtime Thermal Management Across System Components," IEEE.


