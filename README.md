# Blackout Blueprint: Unraveling the Mysteries behind Major Power Outages in the US
**Authors:** Charlie Sun, Aaron Feng

## Project Overview
TODO: bullshit about 3-4 sentences. Abstract sort of thing. 

## Investigating Topic and Introduction
TODO: Background Analysis

### Introduction of the Dataset
TODO: columns analysis


## Cleaning and EDA
### Data Cleaning
TODO: Explain how we cleaned and selected the columns in words

Here's the cleaned dataframe: 

| U.S. STATE   | OUTAGE. START       | OUTAGE. RESTORATION  |  OUTAGE. DURATION |  ANOMALY. LEVEL | CLIMATE. CATEGORY  | CAUSE. CATEGORY    |
|:-------------|:--------------------|:---------------------|------------------:|----------------:|:-------------------|:-------------------|
| Minnesota    | 2011-07-01 17:00:00 | 2011-07-03 20:00:00  |              3060 |            -0.3 | normal             | severe weather     |
| Minnesota    | 2014-05-11 18:38:00 | 2014-05-11 18:39:00  |                 1 |            -0.1 | normal             | intentional attack |
| Minnesota    | 2010-10-26 20:00:00 | 2010-10-28 22:00:00  |              3000 |            -1.5 | cold               | severe weather     |
| Minnesota    | 2012-06-19 04:30:00 | 2012-06-20 23:00:00  |              2550 |            -0.1 | normal             | severe weather     |
| Minnesota    | 2015-07-18 02:00:00 | 2015-07-19 07:00:00  |              1740 |             1.2 | warm               | severe weather     |



### Univariate Analysis

<p style="text-align:center"><iframe src="assets/outage_duration.html" width=600 height=480 frameBorder=0></iframe></p>


<p style="text-align:center"><iframe src="assets/anomaly_level.html" width=600 height=480 frameBorder=0></iframe></p>

<p style="text-align:center"><iframe src="assets/heatmap.html" width=600 height=480 frameBorder=0></iframe></p>


### Bivariate Analysis

<p style="text-align:center"><iframe src="assets/biv_1.html" width=600 height=480 frameBorder=0></iframe></p>

<p style="text-align:center"><iframe src="assets/biv_2.html" width=600 height=480 frameBorder=0></iframe></p>


### Interesting Aggregates 

We created a pivot table: 

|   equipment failure |   fuel supply emergency |   intentional attack |   islanding |   public appeal |   severe weather |   system operability disruption |
|--------------------:|------------------------:|---------------------:|------------:|----------------:|-----------------:|--------------------------------:|
|             308.235 |                17433    |              497.282 |     259.267 |        2125.91  |          3279.95 |                         601.861 |
|            3201.43  |                 7658.82 |              426.818 |     142.176 |        1376.53  |          4059.33 |                         941.018 |
|             505     |                22799.7  |              312.557 |     209.833 |         596.231 |          4416.69 |                         478.2   |


<p style="text-align:center"><iframe src="assets/aggregates.html" width=600 height=480 frameBorder=0></iframe></p>





## Assessment of Missingness





## Hypothesis Testing 

<img src="assets/p_val.png.png"
     alt="Permutation Test for KS Statistic"
     style="text-align:center" />