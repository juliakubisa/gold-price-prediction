# GOLD PRICE PREDICTION
:blue_book: This project was a part of my thesis bachelor thesis: *What moves the gold price? An analysis of gold market and short-term forecasting.*

:orange_book: This project is an attempt to expand the previous studies by analyzing and forecasting the gold price based on the most recent data. An ARIMA model was applied due to its wide application in econometrics and good fit for various time series types, including financial data. The main goal was to correctly estimate values in the 3 months period. 

### DATASET 
The dataset was obtained from World Gold Council and it consists of 390 monthly observations between January 1990 and June 2022. Basic cleaning was not needed becuase there weren't any missing or seemingly incorrent values. The dataset was split into two parts: 
- in-sample (Jannary 1990 - March 2022) used for building the model
- out-of-sample (April - June 2022) used for testing the accuracy of the estimated observations  

### ANALYZING THE DATA 
The time series wasn't adjusted seasonally. There were two steps in the initial identification of the data: 
- visualizing gold prices in the given date range using matplotlib 
- printing basic statistics such as mean, median and standard deviation

Performing both of these tasks gave an overview on the data. Mean gold price for 32 year period was 822,82 dollars while the difference between min and max value amounted to 1710,10 dollars. It can be also assumed that the time series is non-stationary: values of observation are oscilliating around an increasing trend. 

### DIAGNOSTIC TESTS   
##### DF and ADF tests  
Dickey-Fuller test was performed to test the stationarity of the time series. Test statistic was higher than critical values - there weren't sufficient evidence to reject the null hypothesis (non-stationarity). Breusch-Godfrey test was used to check the autocorelaction of residuals: p-value < 0,05 therefore ADF (Augmented-Dickey-Fuller) applied to the model.
Breusch-Godfrey test showed that for one augmentation the problem of autocorellation was eliminated. The time series was then differenced and thus H0 was rejected and stationary was obtained.

##### KPSS test 
KPSS testi an alternative test to check the stationarity of data. For the differnced data, test statistic showed less than critical values for each significance level. The time series is stationary. 

##### ACF and PACF 
ACF and PACF plots were applied to figure out the order or AR and MA, and check if stationary data is not a white noise. Only for the lag=0, for both ACF and PACF, there is a significant line, which allows to assume that p = 1 and q = 1. 

### FORECAST 
Forecast was conducted manually and afterwards the results were double checked by auto ARIMA function. First, p and q was identified based on ACF and PACF graphs. The highest considered ARIMA model was ARIMA(1, 1, 1). Different variants were then tested based on AIC i BIC criteria. The best fitted model turned out to be ARIMA (0, 1, 1)

### TRACKING ERRORS 
Ex-post tracking errror values were calculated to check the similarity of estimated and real values. The values showed, that the estimated model is well fitted. MAPE (the mean error in percents) wsa equal to  4,76% while the difference between mean prices was 87,3 dollars. 

### CONCLUSION AND REMARKS 
Prognosing financial data isn't a trivial task, becuase of the rapidly changing global market situation. However, some models can quite accurately estimate the values of chosen time series, for example gold prices. 
The result of this project is satisfactionary, as tracking errors showed there isn't much differnce between the real and estimated data. Moreover, multiple Python libraries have definitely helped to carry out the research (as compared to R, where some tests have to be performed manually). 
