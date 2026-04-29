# DSA-210-Project


# Motivation
In recent years I have been interested in Formula 1 and have become a big fan of sport. To win the races, teams need to analyze and adapt to changing conditions like weather, durations of pit stops and tracks. The aim of this project is to understand the effects of these parameters on winning races in Formula 1.

# Datasets Used

Kaggle F1 Set (Link: https://www.kaggle.com/datasets/jtrotman/formula-1-race-data) \
This dataset contains number of .csv files but main ones used in this project are the following: \
races: Gives information of every race between 1950 - 2026 (1171 Rows) \
pit_stop: Gives information about every pitstop of each racer in each race between 1950 - 2026 (22194 row) \
results: Gives information about the ranking of each driver in each race between 1950 - 2026 (27305 row) 

-----------------------------------------------------------------------------------------

Meteostat - (Link: https://dev.meteostat.net/) \
This is an API with python libary that can be used for getting historic weather data for specific places. This is used for getting the weather information of each race track during the times of racing. 

-----------------------------------------------------------------------------------------

Kaggle F1 Track characteristics (Link: https://www.kaggle.com/datasets/kishan305/formula-1-circuits-1950-present) \
It contains every race track used in the history of F1 and gives detailed information about them such as number of turns, length etc. 



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



