# Trajectory-Clustering

## Introduction:
The objective of this exercise is to develop an approach to find the clusters of similar trajectories and identify those trajectories which do not fit in any of these clusters and thus, can be classified as an outlier.
In this exercise you are provided with about 7079 trajectories of taxi trips which is extarcted from the sample of T-Drive Trajectory dataset.

## Dataset:
### Original T-Drive trajectory data sample.
This is a sample of T-Drive trajectory dataset that contains a one-week trajectories of 10,357 taxis. The total number of points in this dataset is about 15 million and the total distance of the trajectories reaches 9 million kilometers.

### Data Processing
1. The original dataset contains the continous log of positions for 10,357 taxis over a one-week period and do not have any feature/id to split the log into individual trip.
2. For each taxi, out of this one-week log positional coordinates for the 2-hour contionous window where they have maximum number of records is picked and marked as a trajectory. 
3. From this subset of data only those taxis are picked which have 20 to 60 records in this 2-hour window of maximum records.
4. Thus, our final dataset for this task contains 7079 trips and total 258273 positional records for them.
**Note: The script used to do this processing is present in this repository with name: .
## The Baseline Approach
In this baseline approach we extrapolate the trajectories of each trip and find their positional coordinate at 5 minutes interval within the given 2-hour window. We do this to have a uniform number of records(24: 120/5) for each trip. After obtaining


