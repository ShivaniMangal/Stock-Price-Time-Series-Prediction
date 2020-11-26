# Google Stock Price Time Series Analysis and Prediction
(Undergraduate Academic Project Timeline : Nov 2018 - April 2019)

## Models trained in this repository:
### * ARIMA 
### * LSTM

## Results :
### PERFORMANCE ANALYSIS FOR GOOGLE STOCK PRICE DATASET
In this section, the error measures of ARIMA and LSTM are analyzed to evaluate performance for prediction of Google closing stock price.

## 6.2.1	STEPS TO IMPLETMENT ARIMA AND PERFORMANCE EVALUATION
•	The first step is to check if the data is stationary.  Data is said to be stationary if it’s mean, covariance and standard deviation is constant over a period of time. 

Figure 1 is a time series plot of all features in the stock price data. Skewed and uneven trends in the graph prove that this data is not stationary
 
Fig 6.8 Non-Stationary Google Stock Prices 

•	The next step is to make the data stationary by subtracting consecutive rows of data by a fixed time period order. Here, the period chosen was 1. As seen in Figure 6.9, the first row’s data becomes NaN when differencing of the order 1 is applied.

 
Fig 6.9 Differencing Google Stock Price Data by an order of 1 

After differencing, the stock price data is plotted again, to verify if stationary data has been obtained, as seen in Figure 6.10.
 
Fig 6.10 Stationary Google Stock Price Data  

•	Next step is to check for autocorrelation. Autocorrelation is a measure of similarity between observations as a function of the time lag between them. In other words, it is the correlation of a value with its immediate previous value. This can be found by plotting an ACF graph as shown in Figrure 6.11. The steep curve above the X axis indicates positive correlation. The lump below the X axis indicates negative correlation. An ideal ACF must have most of its values above the X axis. 

![Image] main/ReadMe_Results_Images/ACF.png 

Fig 6.11 Autocorrelation of Stationary Google ‘Close’ Stock Price Data

•	Before testing an ARIMA model for different p, d, q values, the frequency (Either daily, monthly, quarterly, yearly) must be set. Here, ARIMA was run for yearly interval
•	As seen in Figure 6.12, the lowest AIC of 135.418 was obtained for ARIMA(1, 1, 0)
 
Fig 6.12 ARIMA Training for Google ‘Close’ Stock Prices

•	Prediction for the test set of 50 values was implemented by fitting the obtained ARIMA model with a step size of 50. The array of predicted values generated is depicted in Fig 6.13.

 Fig 6.12 ARIMA Predicted Closing Prices

•	A graph with both test prices and predicted prices shown in Figure 6.13 showed that the ARIMA model did NOT perform very well. This could be due to gaps in time in the data. Properly structured data of continuous days or months is usually more suited for accurate ARIMA modelling. Hence, a shift was made to Deep Learning on the same data set.

 
Fig 6.12 Poorly Predicted Closing Prices by ARIMA


## 6.2.2	LSTM PERFORMANCE

The architecture of the RNN designed includes fours LSTM layers and one output layer. The following factors must be understood before proceeding to the results of the LSTM model.
### •	First, a Sequential model is initialized. Sequential() is a class in Kera library that allows one to create a deep learning model by adding successive layers through the ‘add()’ function.
### •	Four LSTM layers were added with 50 hidden units each. 
### •	Dropout Regularization is the method of ignoring and dropping random units during training. This is essential to prevent overfitting. Here, a dropout regularization of 20% was implemented for each layer.
### •	The output layer had one unit, the output unit, that is, the predicted ‘Close’ price of the Google Stock.
### •	Adam Optimizer is an extension of the tradition stochastic gradient descent which has proved too give more accurate results. Mean Squared Error was applied as the loss function.
### •	A batch size of 32 with 100 epochs was used for training. The 100th epoch returned a loss of 6.2778e-04
### •	The predicted closing prices in red versus test closing prices in blue are plotted in Figure 6.13

 
Fig 6.13 LSTM Predictions in Red plotted against Actual Test Closing Prices in Blue for June, July, August 2018

Hence LSTM performed extremely well for this dataset, predicting the right drops and rises in the closing Google stock prices.
