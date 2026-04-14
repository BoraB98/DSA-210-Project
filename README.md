# DSA-210-Project


# Motivation
In recent years I have been interested in Formula 1 and have become a big fan of sport. To win the races, teams need to analyze and adapt to changing conditions like weather, durations of pit stops and tracks. The aim of this project is to understand the effects of these parameters on winning races in Formula 1.

# Datasets Used

Kaggle F1 Set (Link: https://www.kaggle.com/datasets/jtrotman/formula-1-race-data) \
This dataset contains number of .csv files but main ones used in this project are the following: \
races: Gives information of every race between 1950 - 2026 (1171 Rows) \
pit_stop: Gives information about every pitstop of each racer in each race between 1950 - 2026 (22194 row) \
results: Gives information about the ranking of each driver in each race between 1950 - 2026 (27305 row) \

-----------------------------------------------------------------------------------------

Meteostat - (Link: https://dev.meteostat.net/) \
This is an API with python libary that can be used for getting historic weather data for specific places. This is used for getting the weather information of each race track during the times of racing. \

-----------------------------------------------------------------------------------------

Kaggle F1 Track characteristics (Link: https://www.kaggle.com/datasets/kishan305/formula-1-circuits-1950-present) \
It contains every race track used in the history of F1 and gives detailed information about them such as number of turns, length etc. \



# Hypothesis Tests \

Hypothesis Test 1: \
H0: The first pit stop lap is not correlated with race result \
H1: The first pit stop lap is correlated with race result \

Test: Spearman Correlation \
Results: \

P Value:  2.3260527360253857e-24 \
Correlation:  -0.12616286088928053 \

There isn't a strong correlation however it is statistically significant. \


Hypothesis Test 2: \
H0: Track temperature is not correlated on the number of pitstops
H1: Track temperature is correlated on the number of pitstops

Test: Spearman Correlation
Results:

P Value:  0.2737587919020263
Correlation:  -0.07550601598748641

There isn't strong correlation and it is not statistically significant. 


