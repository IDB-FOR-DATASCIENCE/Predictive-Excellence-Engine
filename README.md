# Predictive-Excellence-Engine
In this notebook, we will create an AI and time serie driven forecasting engine based on a set of 5 AI models and 5 time series models and employ several algorithms to perform feature engennering and selection on a multivaraite time series dataset. We are trying to find the best drivers of the HK flat price using various macro economics data.The dataset we are using is the 'HK macroeconomics data' from Kaggle. It is a daily dataset starting from 2nd January 2003 and goes on till 26th November 2019. The target variable is 'Private Domestic (Price Index)' and there 12 features which can help us forecast HK flat price. The dataset can be found [here](https://www.kaggle.com/stanley11291985/hk-macroeconomics-data).

We will first do exploratory data analysis on the data and then move on to data cleaning where we do the following:
1. Check if any dates are missing and add the missing dates
2. Use linear interpolation to fill the nulls (we will also provide the code for forward and backward fill
3. Perform outlier detection
4. Perform outlier treatment
5. Check time series components, ACF and PACF plots of target variable

Once the data has been cleaned up, we will create the following additional features:
1. 3 lags for each feature
2. Daily change for each feature
3. A flag for holidays
4. Flag for S&P 500 index
5. Calculate First hand sales price and drop the sales amount variable

The next step is to perform featue selection using the following techniques:
1. Select the top n features based on feature importance from random forest
2. Select the top n features based on absolute correlation with target variable
3. Select the features identified by Lasso regression
4. Select features by recursively considering smaller and smaller sets of features
5. Select the top n features based on absolute value of beta coefficients of features

The final features are the ones selected in at least 3 out of 5 models.

After feature selection, we train a set of 10 models (and perform hyper parameter tuning wherever required):
1. SARIMA (Univariate Time Series)
2. Holt Winters (Univariate Time Series)
3. SARIMAX(Multi-variate Time Series)
4. VAR(Multi-variate Time Series)
5. VECM(Multi-variate Time Series)
6. LSTM (Univariate Time Series)
7. Random Forest (Multi-variate AI)
8. XGBoost (Multi-variate AI)
9. Linear Regression (Multi-variate AI)
10. SVR (Multi-variate AI)

We make predictions for the next year using all the models and then take their average as the final predictions.

