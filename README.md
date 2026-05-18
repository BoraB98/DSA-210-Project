# DSA-210-Project


# Motivation
In recent years I have been interested in Formula 1 and have become a big fan of sport. During the races there are numerous changing conditions, such as track characteristics, weather and pit stop durations, that may affect the strategies followed by the teams. Therefore, the aim of this project is to understand different strategies followed by the teams and understand the effects of these conditions.


# Hypothesis Tests 

**Hypothesis Test 1**

*Null Hypothesis*: The first pit stop laps are not correlated with the finish position

*Alternative Hypothesis*: The first pit stop laps are correlated with the finish position.

To solve this problem Spearman correlation can be used since pit stop laps and finish positions are ranked structures.  

Results: 

P Value:  7.911089255470108e-25 \
Correlation:  -0.12801623375708424

From these results it can be seen that p value is significantly lower than 0.05 therefore we can safely reject the null hypothesis. However, there is not a strong correlation between the first pit stop laps and finish position.

**Hypothesis Test 2**

*Null Hypothesis*: The track temprature is not correlated with the number of pitstops.

*Alternative Hypothesis*: The track temprature is correlated with the number of pitstops.

To test this alternative hypothesis I converted track tempratures and number of pitstops to rank because Spearman allows non-linear relationship.

Result:

P Value:  0.4264388306436038 \
Correlation:  -0.046084672464115836

Since the p-value is high and the correlation does not exist, the null hypothesis can't be rejected. 

**Hypothesis Test 3**

*Null Hypothesis:* Fastest Laps are independent of winning races.

*Alternative Hypothesis*: Drivers setting the fastest lap have better chance of winning the races.

To check this hypothesis Chi-Square distribution will be used where the counts of 4 different cases will be calculated:


1.   Winning the race and having the fastest lap.
2.   Winning the race but not having the fastest lap.
3.   Not winning the race but having the fastest lap.
4.   Not winning the race and not having the fastest lap.

Results:

P Value:  1.9549296903538364e-98

Since this p-value is significantly lower than 0.05, we can safely reject the null hypothesis.

**Hypothesis Test 4**

*Null Hypothesis*: The mean number of pitstops is equal for all types of tracks.

*Alternative Hypothesis*: At least one track type has different mean number of pitstops.

To check this hypothesis test ANOVA can be applied since there are three types of tracks.

**Results**

P Value:  0.019112248978174238

Since the p-value is lower than 0.05, we can safely say that the null hypothesis is rejected.


# Machine Learning

The machine learning phase of this project consists of supervised learning and unsupervised learning sections. In the unsupervised learning section, the goal was to understand different pit stop strategies drivers/teams executed. In the supervised learning section, the goal was to train a regression model to predict the number of pitstops a driver should do in a race.

# Key Findings 

This project had two main findings:

•The results of the hypothesis test 1, hypothesis test 4, three different clustering algorithms and feature importance graph of XGBoost show that track characteristics are the primary features to explain the pit stop strategies. Moreover, the feature importance graph can be used to infer that driver performance is not as effective as track characteristics to explain the pit stop strategies.

•The results of hypothesis test 2, and three different clustering algorithms and feature importance graph of XGBoost show that temperature of the racetrack alone is not enough to explain the pit stop strategies.


# Limitations and Future Work
One of the crucial limitations of this project was not finding reliable information about the specifications of the cars used by the drivers like their weight or tire degradation. This information could be very valuable during the Machine Learning phase since these features could be correlated with the pit stop strategies of the drivers. Furthermore, there wasn’t further reliable information about the track characteristics like the length of the corners or the straights, which could be very useful since the ML models heavily depended on them.


In the future these models can be improved by creating ML models that calculate the tire degradation and use those predictions as features to improve the models designed in this project. Also, the hypothesis 3 showed that there could be a potential dependency between the fastest laps and finish positions which can be further investigated by creating ML models.


# Reproducibility

The project was conducted on Google Colab. Only meteostat module needs to be pip installed and that command is available on EDA notebook.  

