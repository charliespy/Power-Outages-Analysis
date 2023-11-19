# Blackout Blueprint: Unraveling the Mysteries behind Major Power Outages in the US
**Authors:** Charlie Sun, Aaron Feng

## Project Overview
TODO: bullshit about 3-4 sentences. Abstract sort of thing. 

## Investigating Topic and Introduction
TODO: bullshit about background Analysis

### Introduction of the Dataset
TODO: bullshit about columns analysis


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

<p style="text-align:center"><iframe src="assets/outage_duration.html" width=800 height=600 frameBorder=0></iframe></p>


<p style="text-align:center"><iframe src="assets/anomaly_level.html" width=800 height=600 frameBorder=0></iframe></p>

<p style="text-align:center"><iframe src="assets/heatmap.html" width=800 height=600 frameBorder=0></iframe></p>


### Bivariate Analysis

<p style="text-align:center"><iframe src="assets/biv_1.html" width=800 height=600 frameBorder=0></iframe></p>

<p style="text-align:center"><iframe src="assets/biv_2.html" width=800 height=600 frameBorder=0></iframe></p>


### Interesting Aggregates 

We created a pivot table: 

|   equipment failure |   fuel supply emergency |   intentional attack |   islanding |   public appeal |   severe weather |   system operability disruption |
|--------------------:|------------------------:|---------------------:|------------:|----------------:|-----------------:|--------------------------------:|
|             308.235 |                17433    |              497.282 |     259.267 |        2125.91  |          3279.95 |                         601.861 |
|            3201.43  |                 7658.82 |              426.818 |     142.176 |        1376.53  |          4059.33 |                         941.018 |
|             505     |                22799.7  |              312.557 |     209.833 |         596.231 |          4416.69 |                         478.2   |


<p style="text-align:center"><iframe src="assets/aggregates.html" width=800 height=600 frameBorder=0></iframe></p>





## Assessment of Missingness

### NMAR Analysis
We think that the dataset is NMAR. In the analysis of the dataset derived from 'A Multi-Hazard Approach to Assess Severe Weather-Induced Major Power Outage Risks in the U.S.' (Mukherjee et al., 2018), a significant pattern of missingness is observed in the `OUTAGE.RESTORATION` column. This dataset exclusively encompasses major outages, defined per the Department of Energy's criteria as incidents impacting at least 50,000 customers or causing an unplanned firm load loss of at least 300 MW. Given the considerable scale and impact of these events, it is implausible that the lack of restoration data is due to inadvertent omission or data collection negligence. Rather, it is posited that the missingness in restoration times is predominantly attributable to the intrinsic uncertainties and complexities inherent in the restoration process of such large-scale outages. These complexities might include multifaceted technical challenges, logistical constraints, and varying restoration protocols, which collectively contribute to an ambiguity in precisely determining the restoration moment. Consequently, this pattern of missing data is best characterized as NMAR, where the absence of information is inherently linked to the nature and context of the data itself, rather than random or systemic data collection errors.


### Missingness Dependency





## Hypothesis Testing 

Null Hypothesis (H0): The cumulative distribution functions (CDFs) of 'ANOMALY.LEVEL' for the 'severe weather' and 'equipment failure' cause categories are identical.

Alternative Hypothesis (H1): The cumulative distribution functions (CDFs) of 'ANOMALY.LEVEL' for the 'severe weather' and 'equipment failure' cause categories are not identical.

We would select only the useful column, including 'ANOMALY.LEVEL' and 'CAUSE.CATEGORY'. Recognizing the abundance of difference values in 'CAUSE.CATEGORY', we decide to only perform text on 'severe weather' and 'equipment failure'.

Since anomaly level is numerical data, and there exits outier in anomaly level for severe weather and equiment failure, we choose to use  Kolmogorov-Smirnov (KS) statistic as our test statistics, considering its advantage on sensitivity to difference and robustness on ouliers.

We ran permutation for 10000 times and the graph shows the distribution of permuation test result. The red line marks the observed value.

```python
P-value: 0.6543
Observed KS Statistic: 0.08171442127738092
```

<p style="text-align:center"><iframe src="assets/p_val.html" width=800 height=600 frameBorder=0></iframe></p>

The P-value for the testing is roughly 0.65, which means that at significant level of 0.05, we fail to reject the null hypothesis. 

In real-life terms, this result suggests that the reason for the outage ('severe weather' or 'equipment failure') may not be a strong predictor of the severity of the outage. Other factors or a combination of factors might contribute to the observed severity levels.

The comparable damage levels caused by 'equipment failure' and 'severe weather' may be due to resilient infrastructure, proactive maintenance, and swift response protocols in the power system. Investments in technology, regional climate considerations, and adherence to regulatory standards further contribute to minimizing outage severity. Data aggregation into broad categories may conceal nuanced variations, emphasizing the importance of a detailed analysis for a comprehensive understanding of the observed similarities.







