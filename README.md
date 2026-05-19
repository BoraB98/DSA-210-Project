# DSA-210-Project


# Motivation
In recent years I have been interested in Formula 1 and have become a big fan of sport. During the races there are numerous changing conditions, such as track characteristics, weather and pit stop durations, that may affect the strategies followed by the teams. Therefore, the aim of this project is to understand different strategies followed by the teams and understand the effects of these conditions.


# Hypothesis Tests 

* **Hypothesis Test 1**

  * *Null Hypothesis*: The first pit stop laps are not correlated with the finish position

  * *Alternative Hypothesis*: The first pit stop laps are correlated with the finish position.

  * *Method*: Spearman Correlation can be used since both data are in terms of lap which is a rank. 

  * *Results*: 

    * *P Value*:  7.911089255470108e-25 
    * *Correlation*:  -0.12801623375708424

  * *Analysis*: From these results it can be seen that p value is significantly lower than 0.05 therefore null hypothesis is rejected. However, there is not a strong correlation between the first pit stop laps and finish position.

* **Hypothesis Test 2**

  * *Null Hypothesis*: The track temprature is not correlated with the number of pitstops.

  * *Alternative Hypothesis*: The track temprature is correlated with the number of pitstops.

  * *Method*: Convert track temperatures and number of pitstops to rank because Spearman allows non-linear relationship.

  * *Result*:

    * *P Value*:  0.4264388306436038 
    * *Correlation*:  -0.046084672464115836

  * *Analysis*: Since the p-value is high and the correlation does not exist, the null hypothesis can't be rejected. 

* **Hypothesis Test 3**

  * *Null Hypothesis:* Fastest Laps are independent of winning races.

  * *Alternative Hypothesis*: Drivers setting the fastest lap have better chance of winning the races.

  * *Method*: To check this hypothesis Chi-Square distribution will be used where the counts of 4 different cases will be calculated:

    1.   Winning the race and having the fastest lap.
    2.   Winning the race but not having the fastest lap.
    3.   Not winning the race but having the fastest lap.
    4.   Not winning the race and not having the fastest lap.

  * *Results*:

    * *P Value*:  1.9549296903538364e-98

  * *Analysis*: From these results it can be seen that p value is significantly lower than 0.05 therefore null hypothesis is rejected.

* **Hypothesis Test 4**

  * *Null Hypothesis*: The mean number of pitstops is equal for all types of tracks.

  * *Alternative Hypothesis*: At least one track type has different mean number of pitstops.

  * *Method*: To check this hypothesis test ANOVA can be applied since there are three types of tracks.

  * *Results*:

    * *P Value*:  0.019112248978174238
 
 * *Analysis*: From these results it can be seen that p value is significantly lower than 0.05 therefore null hypothesis is rejected.


# Machine Learning

The machine learning phase of this project consists of supervised learning and unsupervised learning sections. In the unsupervised learning section, the goal was to understand different pit stop strategies drivers/teams executed. In the supervised learning section, the goal was to train a regression model to predict the number of pitstops a driver should do in a race.

## Supervised Learning

At first linear models like Linear Regression, Lasso, Ridge and Polynomial regression with Lasso is trained. However, all of these models created very poor results with almost all of them having negative 𝑅^2 values. The best result obtained was Polynomial regression with three degrees and it had -0.00 𝑅^2 value.

Since all of the linear models performed very poorly, it was inferred that the model did not have a linear relationship therefore non-linear models were tested next. As a non-linear model XGBoost was implemented. In XGBoost depths ranging from 4 – 10 were tested and the best results were obtained when it was 7 which had 0.42 as its 𝑅^2 value. After depth 7 the model started to produce similar results with higher training time.

<img width="815" height="700" alt="image" src="https://github.com/user-attachments/assets/8cffa898-c50c-4c02-85ec-e16f3377ef77" />

From the graph it can be seen that the maximum number of laps in a grand prix is the most important feature. Then Circuit Type and Number of Turns are second and third most important features. On the other hand, the previous driver performance did not have a major contribution to the feature importance. From these results it can be inferred that number of pitstops is heavily related to track characteristics rather than driver performances. 

## Unsupervised Learning

Three models were trained to understand the strategies followed by the drivers:

 * K-Means
 * DBSCAN
 * Gaussian Mixture Model

### K-Means

Cluster | Pit Stop Lap Median  | First Pit Stop Lap | Last Pit Stop Lap | Temperature | # of Stops | Track Length | # of Turns | Direction | Circuit Type |
--------| -------------------- | ------------------ | ----------------- |------------ |----------- |------------- |----------- |-----------|------------- |
0       | 27.78                | 19.5               | 35.6              | 17.5        | 1.89       | 4.27         | 15.45      | Clockwise | Street       | 
1       | 24.46                | 16.95              | 33.38             | 20.7        | 1.95       | 5.08         | 16.85      | Anti-Clockwise | Race    | 
2       | 26.85                | 20.73              | 34.14             | 19.44       | 2.11       | 5.27         | 15.12      | Clockwise | Race         |
3       | 26.85                | 20.73              | 32.8              | 18.32       | 1.54       | 5.84         | 18         | Clockwise | Road         | 
4       | 22.21                | 16.62              | 27.83             | 25.1        | 1.8        | 5.53         | 20.172     | Anti-Clockwise | Street  | 


The results show that direction of the track and the circuit types are different in all of the clusters which means that model used these features primally to cluster. This can be also supported by the values in other columns not having major differences in their values. Only cluster 4 has some value differences like having higher temperature and lower last pit stop laps. Therefore, from these results it can be inferred that K-Means clusters according to the strategy followed by the majority of the drivers follow in different types of tracks.


### DBSCAN

Cluster | Pit Stop Lap Median  | First Pit Stop Lap | Last Pit Stop Lap | Temperature | # of Stops | Track Length | # of Turns | Direction | Circuit Type |
--------| -------------------- | ------------------ | ----------------- |------------ |----------- |------------- |----------- |-----------|------------- |
0       | 24.81                | 15.75              | 34.1              | 19.44       | 2.1        | 5.27         | 15.12      | Clockwise | Race         | 
1       | 24.57                | 17.1               | 33.81             | 17.15       | 1.92       | 4.8          | 13.48      | Clockwise | Street         | 
2       | 29.37                | 23.52              | 35.42             | 18.36       | 1.57       | 3.33         | 19         | Clockwise | Street         |
3       | 24.52                | 17.04              | 33.48             | 20.86       | 1.94       | 5.1          | 16.85      | Anti-Clockwise | Race         | 
4       | 22.81                | 17.37              | 28.81             | 24.84       | 1.75       | 5.43         | 19.1       | Anti-Clockwise | Street  | 
5       | 24.09                | 21.61              | 26.58             | 19.61       | 1.25       | 5.84         | 18         | Clockwise | Road  | 
6       | 37.43                | 25.73              | 49.13             | 14.8        | 2          | 5.84         | 18         | Clockwise | Road  | 
7       | 16.19                | 15.08              | 17.49             | 26.87       | 1.37       | 6.17         | 27         | Anti-Clockwise | Street  | 
-1      | 38.82                | 13.96              | 47.51             | 18.53       | 3.86       | 5.11         | 16.79      | Inconclusive | Inconclusive  | 


From the graph it can be seen that again the direction and circuit types are mostly different in the clusters. In the clusters that have same direction and circuit type values, there are significant differences in other columns. For instance, in clusters 1 and 2 there are differences in the first pit stop laps and number of turns. Another example would be clusters 4 and 7 where number of turns and last pit stop laps are different. Therefore, from these results it can be inferred that DBSCAN created the majority strategy that the drivers follow in different types of tracks.

### Gaussian Mixture Model

Cluster | Pit Stop Lap Median  | First Pit Stop Lap | Last Pit Stop Lap | Temperature | # of Stops | Track Length | # of Turns | Direction | Circuit Type |
--------| -------------------- | ------------------ | ----------------- |------------ |----------- |------------- |----------- |-----------|------------- |
0       | 22.21                | 16.62              | 27.83             | 25.09       | 1.8        | 5.53         | 15.45      | Anti-Clockwise | Street  | 
1       | 25.47                | 16.15              | 34.96             | 19.9        | 2.12       | 5.12         | 16.85      | Clockwise | Race    | 
2       | 27.78                | 19.52              | 35.68             | 17.52       | 1.89       | 4.27         | 15.12      | Clockwise | Street         |
3       | 19.62                | 13.13              | 26.44             | 15.06       | 1.84       | 6.8          | 18         | Clockwise | 0.82 Race and 0.17 Road | 
4       | 24.46                | 16.95              | 33.38             | 20.74       | 1.95       | 5.08         | 20.172     | Anti-Clockwise | Race  | 

From these results it can be seen that the direction and circuit type were again the primary features for creating the clusters. However, one important distinction is that it categorized the road circuit and race circuits in the same category rather than creating separate clusters.

# Key Findings 

This project had two main findings:

 * The results of the hypothesis test 1, hypothesis test 4, three different clustering algorithms and feature importance graph of XGBoost show that track characteristics are the primary features to explain the pit stop strategies. Moreover, the feature importance graph can be used to infer that driver performance is not as effective as track characteristics to explain the pit stop strategies.

 * The results of hypothesis test 2, and three different clustering algorithms and feature importance graph of XGBoost show that temperature of the racetrack alone is not enough to explain the pit stop strategies.


# Limitations and Future Work
One of the crucial limitations of this project was not finding reliable information about the specifications of the cars used by the drivers like their weight or tire degradation. This information could be very valuable during the Machine Learning phase since these features could be correlated with the pit stop strategies of the drivers. Furthermore, there wasn’t further reliable information about the track characteristics like the length of the corners or the straights, which could be very useful since the ML models heavily depended on them.


In the future these models can be improved by creating ML models that calculate the tire degradation and use those predictions as features to improve the models designed in this project. Also, the hypothesis 3 showed that there could be a potential dependency between the fastest laps and finish positions which can be further investigated by creating ML models.


# Reproducibility

The project was conducted on Google Colab. Only meteostat module needs to be pip installed and that command is available on EDA notebook.  

