This project represents the prediction model for Time series (rides per region) for NY yellow taxi.

## The models, that were introduced:
* Base SARIMAX model for single region 
* SARIMAX model for clusters that describe all regions
* to be continued

## Brief description:
* The data is filtered by removing all non-significant rides: zero-time rides, non-passenger rides, etc.;
* Than the data is grouped in the tables by calculation statistics: rides from the regions with time-stamp 1 hour;

region|1|2|...|2499|2500
------|-|-|---|----|----
1 may 2016, 0 hour|0|1|...|0|2 
1 may 2016, 1 hour|5|0|...|34|0 
1 may 2016, 2 hour|0|49|...|0|8 

Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
* By choosing the threshold in average 5 rides from the region, the table is reduced: providing the set of **2500** regions, only **102** of them are significant.

The raw data for testing models might be downloaded here: http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml


## Metrics
 todo

## Visualistion
The heatmap of NY taxi rides

![alt text](http://savepic.ru/14518043.png)

![alt text](http://savepic.ru/14520088.png)
