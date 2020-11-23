# Title: Detecting anomalies in business process event logs using statistical leverage
## Detecting anomalies in business process event logs using statistical leverages, Jonghyeon Ko and Marco Comuzzi, Information Sciences, Accepted for publication (Nov 2020)

This repository shows developed algorithm of adjucted leverage score and anomaly detection for event log, and a folder "BINET_tnolle" is refered from "https://github.com/tnolle/binet" to show baseline models including Sampling, Naive, OC-SVM, DAE, BINET refered from [2].
The algorithm of adjected leverage is coded using statistical package R as seen in folder "Leverage_Ko" and it calculates anomaly score for each case in trace level. 
The total result of performance was recorded in "table.csv" file.

## Prepared Data1 - 70 artifical logs
We used 7 types of process models including large_log, small_log refered from [1], small, medium, large, huge, wide refered from [1] to generate artificial logs. With 10 times of repetition, there are 10 artifical_logs for each model.  

In process models of large_log and small_log, we injected "replace" anomaly pattern used in [1]. In otherwise, in process models of small, medium, large, huge, and wide, we injected 5 types of anomaly patterns including "insert", "skip", "early", "late", and "rework" used in [2]

## Prepared Data2 - 6 real-life logs
For real-life logs, we used BPI challenge 2012, 2013, 2017 data sets. For each log in BPIC13, BPIC17, there are 3, 2 subsets of logs. 

About anomaly patterns, we injected all 6 types of anomaly patterns including "replace", "insert", "skip", "early", "late", and "rework" on real-life logs.

The statistics of datasets are summarised in Table 1 in our paper.

## R-files
- Preprocessing.R : Apply one hot encoding and zero-padding and save
- adjusted_leverage.R : The code includes all 5 types of thresholds applied on basic leverage and weighted leverage.

&#x1F53A; Changes from original code in BINet
- We don't use generator to add artificial attributes because of our purpose of trace-level approach.
- In real-life logs, we deleted all the other attributes without 'caseid', 'activity', 'timestamp' since we focus on trace-level anomaly detection. In cases of some baseline methods designed in BINet folder like SVM, we found that the methods use the additional attributes for classfication problem but it should be deleted for fair comparison in our research.
- Since we found an error in a function that automatically recognizes key atrributes on BPIC 2015 dataset, we adjusted the activity name to be 'activityNameEN' from 'action_code'. (Official data repository "https://data.4tu.nl/repository/uuid:31a308ef-c844-48da-948c-305d167a0ec1" introduces activity name as 'activityNameEn' or 'activityNameNL'.   
- The functions of each anomaly pattern are partially revised according our paper's definition.
- There are a few small changes in preprocessing parts of code for a need that some code should be adjusted from the above changes.


## References
[1] Nguyen, H. T. C., Lee, S., Kim, J., Ko, J., & Comuzzi, M. (2019). Autoencoders for improving quality of process event logs. Expert Systems with Applications, 131, 132-147.

[2] Nolle, T., Luettgen, S., Seeliger, A., & Mühlhäuser, M. (2019). Binet: Multi-perspective business process anomaly classification. Information Systems, 101458.









