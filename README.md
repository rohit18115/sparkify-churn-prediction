# sparkify-churn-prediction
Sparkify(proxy for Spotify) music service customer churn prediction using spark. 
## Introduction

This project is about customer churn prediction for a psudo music streaming app called sparkify (proxy for spotify).
We are provided with a huge 12gb dataset with user logs in it and we need to predict which customer will churn or not.  
We have used pyspark to handle such a big data. Before going into other parts of the project lets take a brief overview 
of what is churn and why is so important to predict it.

Churn prediction means detecting which customers are likely to leave a service or to cancel a subscription to a service. It is a critical prediction for many businesses because acquiring new clients often costs more than retaining existing ones. Once you can identify those customers that are at risk of cancelling, you should know exactly what marketing action to take for each individual customer to maximise the chances that the customer will remain.

Different customers exhibit different behaviours and preferences, so they cancel their subscriptions for various reasons. It is critical, therefore, to proactively communicate with each of them in order to retain them in your customer list. You need to know which marketing action will be the most effective for each and every customer, and when it will be most effective.

### Why is it important?

Customer churn is a common problem across businesses in many sectors. If you want to grow as a company, you have to invest in acquiring new clients. Every time a client leaves, it represents a significant investment lost. Both time and effort need to be channelled into replacing them. Being able to predict when a client is likely to leave, and offer them incentives to stay, can offer huge savings to a business.

As a result, understanding what keeps customers engaged is extremely valuable knowledge, as it can help you to develop your retention strategies, and to roll out operational practices aimed at keeping customers from walking out the door.

Predicting churn is a fact of life for any subscription business, and even slight fluctuations in churn can have a significant impact on your bottom line. We need to know: “Is this customer going to leave us within X months?” Yes or No? It is a binary classification task.

## The project focuses on the following tasks:

- Load and Clean Dataset
  - Check nan values
  - Check null values
  - Check blank values in userID
  - decide what to do with the missing values

- Exploratory Data Analysis
  - churn variable should be the focus over here, so all the analysis in this section will be around the churn variable by varying other columns.
  - check frequency of events of active users vs churned users.
  - Check frequency of unique active users vs churned users.
  - check frequency of male and female active vs churned users.
  - check frequency of paid and free active bs churned users.
  - check frequency of active and churned users at different locations.
  - check frequency of page visits of active and churned users.
  - check hourly activity of active users vs churned users.
  - check day of the month activity of active vs churned users.
  - check monthly activity of active vs churned users.
  - check week of the day activity of active and churned users.
  - focus on the difference in activity of users before and after churning.

- Feature Engineering¶
  - There are two ways in which we can format the data for training.
    - First, do the usual and just convert categorical data to dummy variables and staradize other numerical features and just feed the whole data set into the machine learning model.
    - Second, instead of using all the rows, we can groupby using userId column and calculate clever features which would actually help the model make better decisions. Some of these features that can be calculated for each user are:
        - Song length per user per session
        - Number of ThumbsUp, ThumbsDown, InviteFriends, downgrades, songs per session, artists the user fans
        - Session's duration, count per user
        - The user's subscription age
        - Number of days as free/paid user

- Modeling
  - I will be using to two methods for training the model.
    - First, use all the log events of every user without much feature engineering.
    - Second, use the dataset that we prepared in the previous section, where we grouped the data according to the user and condensed the logs where we end up with one row for each userId.
  - Import the previously saved data.
  - Remove the spaces between columns for the next task.
  - The imported data had string values for every column so we have to convert string value to Integer and Float type.
  - Scale the data to bring the distribution of the data with mean = 0 and stdv = 1.
  - Split the data into train, validation and test set.
  - Train the model for both kinds of data mentioned above.
    - Use crossvalidator.
    - Time the training time of model for both the datasets.
    - Calculate the feature contribution/ importance for both the datasets.
    - report the accuracy, f1-score, precision, recall. 

# Repository Structure

- Sparkify.ipynb (The main file where all the exploring, cleaning, analyzing and modeling is done)
- user_dataset.csv (feature engineered dataset, reduced and condensed version of the full dataset)
- user_dataset_full.csv (full dataset)

# External links for further explaination:

- [Medium article for explaining the project](https://medium.com/@rohit18115/we-will-make-you-stick-customer-churn-prediction-with-pyspark-677fd17cf915)
