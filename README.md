# Data_Science_Final_Project

## Introduction

The objective of this project is to use Jupyter and its imports to analyze Uber Data. I wanted to know when the best time to take an uber would be, that being the time with the lowest amount of rides. I quickly realized that a lot of people take ubers and the amount of data that would be in a avaliable for a given year across the USA would be too much for my small computer to handle. So I bagan searching Kaggle.

On Kaggle I was able to find a "small" data set from 2014 in NY. INSERT LINK. I will use this to answer a my questions:

When is the most travled time during the day?
Week?
When is the least travled time during the day?
Week?

## Selection of Data
What is the source of the dataset?

The source of the dataset comes from [here](https://www.kaggle.com/datasets/fivethirtyeight/uber-pickups-in-new-york-city), a post from kaggle that does have more months included but I chose to focus of the July 2014 data.

Characteristics of data?

The model processing and training are conducted using a Jupyter Notebook and is available [here](https://github.com/memoatwit/dsexample/blob/master/Insurance%20-%20Model%20Training%20Notebook.ipynb).

The table consitst of 796121 rows and 8 columns.
The objective is find the best time and day to take an uber.
The column names are Date/Time,	Lat, Lon,	Base. Date/Time being the date and time, Lat being the latitude, Lon being the longitude, Base the The TLC base company code affiliated with the Uber pickup.

Any munging, imputation, or feature engineering?
For my question I did not need Lat and Lon so I decided to drop those columns. Shown here:

IMAGE

To make the date and time more readable I converting them from a str value to a datetime value and then to data/time more usable I split them into their own respective columns. Those columns being timeOfDay, dayOfWeek, and date. Before making them all their own columns I floored the times to the 15 minute mark to make the data easier to analyze in a graph.

## Methods

Tools:
- NumPy, Pandas, matplotlib.pyplot, and seaborn
- Juypter for coding 

These tools were used to graph and to anaylze the data.

## Results
My results are shown below in the following graphs:

![data screenshot](./Image#1.jpeg)
(The first graph is in bar plot and the second is in line plot)

In this graph we are shown the amount of rides over the course of the month. The interesting thing about this is the trend that repeats itself every seven days. This being the weekly cycle. This doesnt really answer our question and seems to be too inconclusive and too inconsitant to definetly say what day we should travel on. So lets go another step and look into the average rides per week in  the month of July.

INSERT IMAGE

Our second graph here shows the average amount of rides taken per each day of the week. This allows us to narrow down the day upon which the least amount of rides occur. That day being Monday. Now we know which day to travel but now we want to figure out which time of the day would be the best to travel at. Not only for monday but for all the days as well.

INSERT IMAGE

The image of above shows a heatmap of the average amount of rides at specific times during each day of the week. This allows us to pinpoint the busiest days and times during the week. This time being around 5:30 pm - 6:15 pm. The day and time being the least busy is from 12 am - 3 am on the days Monday-Thursday. 

INSERT IMAGE

The last images what the heatmap showed but in a line plot for easier repersentation.

ANSWER:
When is the most travled time during the day?
- 5:30-6:15 pm
When is the most travled time during the week?
- Tuesday
When is the least travled time during the day?
- 12:00 - 3:00 am
When is the least travled time during the week?
- Monday

## Discussion
Experimenting with various feature engineering techniques and regression algorithms, I found that linear regression with one-hot encoding provided one of the highest accuracies despite its simpler nature. Across all these trials, my training accuracy was around 75% to 77%. Thus, I decided the deploy the pipelined linear regression model. The data was split 80/20 for testing and has a test accuracy of 73%. 

I looked at some kaggle notebooks studying this problem and found this to be an acceptable level of success for this dataset. I am interested in analyzing the training data further to understand why a higher accuracy can't be easily achieved, especially with non-linear kernels. 

One unexpected challenge was the free storage capacity offered by Heroku. I experimented with various versions of the libraries listed in `requirements.txt` to achieve a reasonable memory footprint. While I couldn't include the latest pycaret library due to its size, the current setup does include TensorFlow 2.3.1 (even though not utilized by this sample project) to illustrate how much can be done in Heroku's free tier: 
```
Warning: Your slug size (326 MB) exceeds our soft limit (300 MB) which may affect boot time.
```

## Summary
This sample project deploys a supervised regression model to predict insurance costs based on 6 features. After experimenting with various feature engineering techniques, the deployed model's testing accuracy hovers around 73%. 

The web app is designed using Streamlit, and can do online and batch processing, and is deployed using Heroku and Streamlit. The Heroku app is live at https://ds-example.herokuapp.com/.

Streamlit is starting to offer free hosting as well. The same repo is also deployed at [![Open in Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/memoatwit/dsexample/app.py)  
More info about st hosting is [here](https://docs.streamlit.io/en/stable/deploy_streamlit_app.html).


## References
[1] [GitHub Integration (Heroku GitHub Deploys)](https://devcenter.heroku.com/articles/github-integration)

[2] [Streamlit](https://www.streamlit.io/)

[3] [The pycaret post](https://towardsdatascience.com/build-and-deploy-machine-learning-web-app-using-pycaret-and-streamlit-28883a569104)

[4] [Insurance dataset: git](https://github.com/stedy/Machine-Learning-with-R-datasets)

[5] [Insurance dataset: kaggle](https://www.kaggle.com/mirichoi0218/insurance)
