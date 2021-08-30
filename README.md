# Web-Scrapping, Reddit, NLP, and Classification

**Executive Summary**
Web scapping is an integral process that helps in quick and effective extraction of news data from the different sources.
Reddit is a social news platform that allow users to discuss and vote on content that other users have submitted.
**NLP** or natural language processing is important because it helps resolve ambiguity in language and adds useful numeric structure to the data for many downstream applications, such as speech recognition or text analytics.
In this project, all three important tools are used to collect data, clean data, and modelling them by using Random Forest and Linear Regression models.
It will help users to idndetify which model is accurate based on test scores and train scores.

**Problem Statement**
We have got the data from Reddit. According to the objective or problem statement, here we are goign to identify which vehicle (Cars or motorcycles) is the best for earning money using different dataset.  
We have to create a random forest model and logistic regression model that will help us to get the best train and test scores.
In this part, the Reddit challenge offers two datasets called **cars_posts.csv** and **motorcycles_posts.csv** to train the model. It is also given a test dataset called **test.csv** to test our model as unseen data.
We have to clean the dataset and fit the model into it to make our predictions. A sample prediction is already uploaded to the Reddit challenge for getting the score.
Based on models and the predictions, we have to find what are some key predictors that can use in predicting prices.

How it was carried out
**Data Cleaning and EDA**
- Both datasets are huge. First, we have to understand what is needed and what is not.
-I started by generating a list of percentages of null values in each feature after the initial import into the dataframe.
-It helps me to understand the data and gives a broad overview of which features have so many missing values. I have considered such features which have 90% null values were discarded.
-After that, I used a describe command on the data set, along with the .isnull() to give a rough sense of the distribution for each non-numeric feature.
-It helps me to understand if the data is nominal or ordinal.
-Then I moved towards correlation and several visualizations of the data to check the outliers and maximum missing values. All actions are given below
-Replacing the missing values in poolQC, Miscfeature, Alley Fence  FireplaceQu so replacing with None
-Filling missing values with none values, Area of each street is connected so replacing the missing value with median, replacing with most frequent value in the column which is None,
-Replacing missing with 0, Missing value in these features means no basement (replace with 0), NaN means in these columns is no basement,
-NA means no masonry veneer for houses. (Fill zero for the area and None for type), NA means no masonry veneer for houses. (Fill zero for the area and None for type),
-Filling MSZoning with most common value 'RL', For Utilities, most of the records are 'AllPub'. It won't help in prediction, data description says- Assume typical(Typ) unless deductions are warranted, replacing with most repeated "SBrkr" value, set "TA" most frequent in place of missing value, replacing with most common value, replacing with most common value again, MSSubClass-type of dwelling, NA means no building class. (fill with None)
-Based on that I have dropped several columns that are not at all important such as Id, etc. I have dropped that from both the train and test data.

**Preprocessing and Modeling**
After handling all missing values, I have moved towards model preprocessing. I have divided the target and actual data from the actual training data.
I have processed columns and removed rows to eliminate duplicacy. I used final_df.isnull().sum() to check if there are any rows with null values.
Then we have checked what we need to check in a classification problem. Then we finally move towards the train and test split.
Dropped all the null variables from the training data splits. Then we move towards the modeliing.

**Evaluation and Conceptual Understanding**
In case of Random Forest model -
It focused on best params(bootstrap': True, 'criterion': 'entropy', 'max_depth': None, 'max_features': 0.1, 'min_samples_split': 5, 'n_estimators': 30, 'random_state': 42, 'warm_start': True)
For the training dataset, I have used Random Forest. The values are given below
I got the model Train score = 0.8260810443296165
and Test score = 0.7687601957585645
In case of logistic regression model -
It focuses on Best params = {'C': 2, 'class_weight': 'balanced', 'penalty': 'l2', 'random_state': 42, 'solver': 'lbfgs', 'warm_start': True}
The values are given below
I got model Train score = 0.7827032907261354
and Test score = 0.7728384991843393
Compare these two models, The most Accurate model is Random Forest Model.

**Prediction the test set**
Due to the Random Forest Model is the best one, we have tested test data on that model. Based on that we have predicted the values of salesprice on that test data and exported
the data in CSV format as the instruction given.

**Features to consider**
bootstrap, criterion, max_depth, max_features, min_samples_split, n_estimators, random_state, warm_start.

**Conclusion and Recommendations**
Random Forest Model gave slightly better accuracy with the training data.
The accuracy classification is fine but not that good.
The main reason is similarity of subreddits.
Many characteristics of cars and motorcycles are same that makes similarity inn subreddits.
This code is used to classify any two subreddits by changing the names while retrieving data.
To get a better result, min_df should be ignored.
The performance of models can change depending on selection of subreddits, number of posts, and way of processing the data.
