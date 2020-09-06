# Covid_Tweets_Impact

This project uses the Coronavirus (COVID-19) Tweets dataset from Kaggle, which includes all Tweets globally using hashtags associated with Coronavirus in March and April 2020. The goal of this project is to gain a better understanding of the characteristics and patterns of these Tweets as well as to build and optimize a machine learning model that predicts the influence, i.e. the number of retweets, of Tweets.

**Dataset Preparation.ipynb cleans and prepares the three datasets for analysis**

**Project Notebook.ipynb covers exploratory analysis and machine learning model**

There are three main parts for this project. First, Part 1 - exploratory analysis will study the distributions and patterns of Tweets, including time analysis, textual analysis, and popularity analysis. Second, Part 2 - time series & country analysis will study the relationship between Tweets, number of confirmed Coronavirus cases, as well as its trend across time series and differences among countries. Third, Part 3 - Modeling will build and optimize linear regression model as well as random forest regression model in spark to predict the number of retweets of Tweets. Finally, this project will discuss the main challenges encountered during the analysis and the next steps.
  
This project is meaningful because the monitor and understanding of public sentiment is important for crisis management. To prevent massive panicking and public opinion crisis, governments need to observe public reaction, find out the trends of heated discussions, and address the most pressing concerns. A model that successfully predicts the influential tweets will enable governments to react quickly to the ferment of public sentiment and evolving concerns, which also helps prevent public relations crisis.

There were mainly three challenges in this project.

First, it was more difficult to read and process big data. The original datasets for Tweets in March and April had more than 23 million data entries in total and it was impossible to read them into colab without running out of RAM, so I had to do some basically cleaning for each dataset before I read them and concat them. After reading all the data, the data processing and cleaning process also took relatively longer time and a lot of RAM. To make it more efficient, I seperated the original data into three different datasets for different parts of analysis.

Second, it was challenging to handle the large amount of training data (around 3 million) for machine learning. I used Spark instead of sklearn because sklearn couldn't process that amount of training data. I also increased Spark memory space by resetting spark executor memory and spark driver memory. However, I still encountered an error of computation space when I adjusted the parameters of random forest regression (maxDepth and numTrees) to a higher number as well as when I fit and transformed pca on the training data.

Last but not least, there were some challenges when preparing the training data for modeling. The distribution of the training data was very wide and extremely uneven. While the number of retweets ranged from 0 to 60,000, more than 95% of the Tweets had retweet counts of 0 or 1. This made it very difficult to resample the dataset to achieve a balanced distribution. Furthermore, certain data points in the training data present inconsistent values. For example, a Tweet can have 25237 favorites with only 1 retweet and 300 followers, or thousands of retweets with no favorites. I think the reason might be that the bots on Twitter make it possible for users to manipulate their amount of favorites, retweets, or followers. These types of inconsistent data points may interfere with the modeling and decrease model performance.
