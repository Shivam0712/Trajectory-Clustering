# Trajectory-Clustering

## Introduction:
The objective of this exercise is to develop an approach to find the clusters of similar trajectories and identify those trajectories which do not fit in any of these clusters and thus, can be classified as an outlier.
In this exercise you are provided with 7079 trajectories of taxi trips which is extarcted from the sample of T-Drive Trajectory dataset.

## Dataset:
### Original T-Drive trajectory data sample.
This is a sample of T-Drive trajectory dataset that contains a one-week trajectories of 10,357 taxis. The total number of points in this dataset is about 15 million and the total distance of the trajectories reaches 9 million kilometers.

You can find the original dataset [here](https://drive.google.com/file/d/1pzaGZaboOdUxsw7l6hhJDdsH8ZqUeZXs/view?usp=sharing).

### Data Processing
1. The original dataset contains the continous log of positions for 10,357 taxis over a one-week period and do not have any feature/id to split the log into individual trips.
2. For each taxi, out of this one-week log of positional coordinates, for the 2-hour continous window where they have maximum number of records is picked and marked as a trajectory. 
3. From this subset of data only those taxis are picked which have 20 to 60 records in this 2-hour window of maximum records.
4. Thus, our final dataset for this task contains 7079 trips and total 258273 positional records for them.

**Note: The script used to do this processing is [Extract Trajectories.ipynb](https://github.com/Shivam0712/Trajectory-Clustering/blob/master/Extract%20Trajectories.ipynb).**

**The final processed data can be found [here](https://github.com/Shivam0712/Trajectory-Clustering/blob/master/20190425_trajectories.csv).**

## The Baseline Approach
In this baseline approach we extrapolate the trajectories of each trip and find their positional coordinate at 5 minutes interval within the given 2-hour time window. We do this to have a uniform number of records(24: 120/5) for each trip. After obtaining these 24 positional coordinates for each trip, we run k-means algorithm to find the clusters of similar trajectories.
This whole approach is conducted in following steps:

### 1. Noise filtering from the selected 7079 trips.
1. Those trips which had any positional coordinate far away from the main bunch of positional coordinates were removed.
2. Unique number of trips after this filtering: 4234; Total positional coordinates: 258273
3. Plot of all the trajectories:
![All Trajectories](https://github.com/Shivam0712/Trajectory-Clustering/blob/master/AllTrajectories.png)
4. Some sample trajectories:
![Sample Trajectories](https://github.com/Shivam0712/Trajectory-Clustering/blob/master/IndiviDualTrajectories.png)
  
**The processed data after this step can be found [here](https://github.com/Shivam0712/Trajectory-Clustering/blob/master/20190425_ProcessedTaxiTrajectories.csv)** 
  
### 2. Extrapolation of trajectories:
1. For each trip the, time of earliest record was picked and marked as first timestep.
2. In the 2-hour period starting with the time of this first timestep, 23 timesteps with 5 minute interval between each were created.
3. The positional coordinate for these 24 timesteps were extrapolated from the positions of the original records having time immediately before and after the time of the given time step.
4. Those trips which had any positional coordinate far away from the main bunch of positional coordinates were removed as noise.
5. Unique number of trips after extrapolation: 3612; Total positional coordinates: 86688
6. Plot of extrapolated Trajectories:
![Extrapolated Trajectories](https://github.com/Shivam0712/Trajectory-Clustering/blob/master/ExtrapolatedTrajectories.png)

**The processed data after this step can be found [here](https://github.com/Shivam0712/Trajectory-Clustering/blob/master/20190425_Extrapolate.csv)** 

### 3. Clustering the trajectories:
1. K-Mean Clustering is used to obtain the clusters of similar trajectories.
2. The silhouette curve is used to find the optimum  number of clusters.
![Silhouette Curve](https://github.com/Shivam0712/Trajectory-Clustering/blob/master/silhoutte.png)
3. The plot of final clusters and their centroids are:
![Trajectories Clusters](https://github.com/Shivam0712/Trajectory-Clustering/blob/master/FinalClusterCentroids.png)


### Questions:

Check the notebook: to learn about the implementation of the approach mentioned above and answer the following questions:

1. Anlayze the approach and comment on the limitations of the given approach.
2. Observe the plot with the final clusters and write down your observation about these clusters.
3. Propose a method to do this task better than the current approach and make a notebook with its implementation.


