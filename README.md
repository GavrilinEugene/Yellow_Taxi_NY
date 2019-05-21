This project represents the prediction model for Time series (rides per region) for NY yellow taxi.

Project page: https://www.coursera.org/learn/data-analysis-project
Project competition page: https://inclass.kaggle.com/c/yellowtaxi/ 
The raw data for testing models might be downloaded here: http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml

## The models that were introduced:
* Base SARIMAX model for single region 
* SARIMAX model for clusters that describe all regions:

![alt text](http://savepic.ru/14657957.png)

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

Q_{june} = \frac1{R* 715 * 6} \sum\limits_{r=1}^{R}  \sum_{T=2016.05.31\,23:00}^{2016.06.30\,17:00}  \sum_{i=1}^6 \left| \hat{y}_{T|T+i}^r - y_{T+i}^r \right|.

## Visualization
The heatmap of NY taxi rides

![alt text](http://savepic.ru/14518043.png)

![alt text](http://savepic.ru/14520088.png)

Prediction example:

![alt text](http://savepic.ru/14670244.png)
