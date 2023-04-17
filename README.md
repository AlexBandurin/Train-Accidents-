# Train Accident Analysis: Project Overview

In this analysis, I explore an accident dataset from the Federal Railroad Administration, which features data about accidents that happened in the US in the year 2022 (up until the end of November) as reported by railroad companies. 

[Data source](https://safetydata.fra.dot.gov/officeofsafety/publicsite/on_the_fly_download.aspx)

Python Version: 3.10.9 Packages: pandas, numpy, matplotlib, seaborn,folium, kmodes

## EDA

Used bar plots, pie charts, and folium maps to visualize the distributions and relationships between various variables. This dataset contained 114 features, so this was an extensive process. Below are some of the highlights.

<p align="center">
<img src="https://github.com/AlexBandurin/Train_Accidents/blob/master/Casualties_by_Company.jpeg"  width="60%" height="60%">

<img src="https://github.com/AlexBandurin/Train_Accidents/blob/master/Passenger_Trains.jpeg"  width="60%" height="60%">

<img src="https://github.com/AlexBandurin/Train_Accidents/blob/master/Accident_Causes.jpeg"  width="60%" height="60%">

<img src="https://github.com/AlexBandurin/Train_Accidents/blob/master/Accident_Causes_2.jpeg"  width="60%" height="60%">

<img src="https://github.com/AlexBandurin/Train_Accidents/blob/master/Casualties_by_code.jpeg"  width="110%" height="90%">  

<img src="https://github.com/AlexBandurin/Train_Accidents/blob/master/Accident_Map.jpeg"  width="60%" height="60%">
</p> 

## Clustering Analysis

I performed cluster analysis on this dataset using the **K-Prototypes** algorithm. To determine how many clusters I will to split my data into, a plot of "Cost" vs. "Number of Clusters" is created. The elbow method was used to determine the optimal number of clusters for best comprehension of the trends within the dataset.

<p align="center">
<img src="https://github.com/AlexBandurin/Train_Accidents/blob/master/Elbow_method.jpeg"  width="60%" height="60%">
</p> 

I picked out a few features for performing cluster analysis with. These include: 
- **RAILROAD**: the railroad company the accident is attributed to, 
- **TRNSPD**, the speed at which the train was going, 
- **PASSTRN**: whether the train was a passsenger train or a freight train 
- **CARS**: the number of train cars the train carried, and 
- **Cause**: The cause of the accident. This is one of the 5 categories: Here, H codes are human factors, T are "Track,Roadbed, and structure", E are mechanical and electrical failures, S is signal communication, and M are miscellaneous. Let's create a pie chart that captures the breakdown of accidents by their category.

I created a model with 2, 3, and 4 clusters. Out of these, I determined that the **3-cluster-model** was the most informative as I could see 3 distinct categories of trains. These are: 

- Trains with fewer cars, moving at low speeds, non-passenger
- Trains with many cars, moving at high speeds, non-passenger
- Trains with some slow, some fast cars, involving passenger and non-passenger trains

Going to 4 clusters, the last of those categories split up into 2 clusters without any additional insight.

# Conclusion:

From cluster analysis, I determined that:

- Freight trains carrying with few cars and going at low speeds happen due to human error. These must be locomotives being moved short distances at the the rail yard. The causes associated with these are primarily "shoving movement", which means that one train car collides with another, or "Switch improperly lined", meaning that the railroad switch, a mechanical installation for guiding trains from one track to another, has been improperly configured. 

- Accidents involving passenger trains happen due to miscellaneous reasons, and the most common one of these is the innatentiveness of car drivers on the highway, as was discovered during EDA.

It seems like injuries and deaths could be attributed primarily to the last cluster category, in which there are passenger (Amtrack) trains.
