This project represents the prediction model for Time series (rides per region) for NY yellow taxi.

Project page: https://www.coursera.org/learn/data-analysis-project

Project competition page: https://inclass.kaggle.com/c/yellowtaxi/ 

The raw data for testing models might be downloaded here: http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml

## The models that were introduced:
* Base SARIMAX model for single region 
* SARIMAX model for clusters that describe all regions:

![alt text](https://github.com/GavrilinEugene/Yellow_Taxi_NY/blob/master/images/model_prediction.png)

On the pic some regions from one cluster are shown
* XGBoost with lags, weekly seasonality as features(no SARIMAX time series)

* Tuning XGBoost, adding weather info

## Brief description:
* The data is filtered by removing all non-significant rides: zero-time rides, non-passenger rides, etc.;
* Than the data is grouped in the tables by calculation statistics: rides from the regions with time-stamp 1 hour;

region|1|2|...|2499|2500
------|-|-|---|----|----
1 may 2016, 0 hour|0|1|...|0|2 
1 may 2016, 1 hour|5|0|...|34|0 
1 may 2016, 2 hour|0|49|...|0|8 


* By choosing the threshold in average 5 rides from the region, the table is reduced: providing the set of **2500** regions, only **102** of them are significant.
* Building simple model on weekly seasonality features: sin and cos
* Arima params optimisation: building ACF, PACF, choosing p,q,P,Q,d,D.
* Optimal model (AIC)
* Repeating maram optimisation for region-clustering



## Metrics

![equation](https://latex.codecogs.com/gif.latex?Q_%7Bjune%7D%20%3D%20%5Cfrac1%7BR*%20715%20*%206%7D%20%5Csum%5Climits_%7Br%3D1%7D%5E%7BR%7D%20%5Csum_%7BT%3D2016.05.31%5C%2C23%3A00%7D%5E%7B2016.06.30%5C%2C17%3A00%7D%20%5Csum_%7Bi%3D1%7D%5E6%20%5Cleft%7C%20%5Chat%7By%7D_%7BT%7CT&plus;i%7D%5Er%20-%20y_%7BT&plus;i%7D%5Er%20%5Cright%7C.)

## Visualization
The heatmap of NY taxi rides

![alt text](https://github.com/GavrilinEugene/Yellow_Taxi_NY/blob/master/images/heatmap.png)


Prediction example:

![alt text](https://github.com/GavrilinEugene/Yellow_Taxi_NY/blob/master/images/predictions_example.png)

![alt text](https://github.com/GavrilinEugene/Yellow_Taxi_NY/blob/master/images/prediction_error.png)
