# Project 3

## Executive Summary
In recent times, COVID-19 have led to an increase in alcoholism and smoking in communities. More people are staying home and we are facing a mental health crisis amongst the vulnerable. There is a clear need to find innovative methods to provide help to these people in their platform more than ever, given that quite a sizable number are unable to physically come down for rehabilitation due to COVID-19 restrictions. Our solution aims to create a model to predict if the post sent in by patient to the rehab center's frontend is for smoking or alcoholism, allowing us to better classify patient's problems and provide the appropriate treatment to them more efficiently and quickly, in the comfort of their own homes. We have gathered subreddit posts of both smoking and alcoholic anonymous and applied Natural Language Processing to our data, before training our Supervised Machine Learning Model with the data we gathered. This allowed us to sort our post with a degree of accuracy of 95% for our test data with our Multinomial Naive Bayes Model.


## Context
We are a group of consultants who are hired to present our data models to a panel of directors in rehabilitation centers for smokers and alcoholics.


## Problem Statement
The recent COVID-19 situation have restricted the rehabilitation of several people with smoking or alcohol issues. This has led to a rise in alcoholism and smoking in communities. Directors of these rehabilitation centers are looking for more innovative ways to better engage the community about alcoholism and smoking. 

One way of engaging patients is to engage them online. Several of them have turned to subreddits to post about their problems and concerns. We can leverage on this to provide further appropriate treatment to their posts.

Our director has requested us to create an algorithm that can more efficiently process requests from patients who will be using their online platform for rehabilitation. This algorithm will be used in their online frontend to more quickly classify patients with alcoholism or smoking problems, thus minimising resource and time wastage, allowing help to be rendered more efficiently. 


## Goal of this Data Analysis
Our goal in this data analysis is to be able to classify our patient's posts into smoking or alcoholic issues. This problem is a classification problem, and requires supervised machine learning. We will be using the Naive Bayers and KNN Classification models in our data analysis.

It is important to note that our problem here is a classification problem and thus regression models will not be appropriate here. Supervised learning will be used in this data analysis and we have opted to use Naive Bayes and KNN models.


## Baseline Model
Currently, directors can only gage if the posts are smoking or alcoholics by pulling a set of data from the subreddits, looking at the majority of the data pulled, before deciding if the data is for smoking or alcoholics. Should any future data be sent to them, they have no means of recognising the data by machine learning, if the data belongs to alcoholics or smoking.


## Success Evaluation
Our evaluation metrics for the success of our model will be with our model prediction score, in particular the prediction accuracy score of both our train and test data (Which is split into a ratio of 80-20 from our data) in comparison to our baseline model score.  


---
# Data Scraping
PushShift API was used to retrieve 2000 subreddit posts. As PushShift API has a 100 post restriction per request, a loop was used to repeatedly retrieve data from the subreddits. We retrieved 2000 posts from each subreddits, totalling 4000 total data.


# Data Cleaning 
Upon retrieval of our data, there are several columns that are unnecessary. We are only interested in the text data, which are the selftext and title column. This is done by simply splicing the data from our dataframe into a separate dataframe and saving it to our clean data.

Also note that we removed as many special characters that we could from our data as well. Tagging of each subreddits was also done to establish our prediction variable.


## Data Dictionary:
|Feature|Type|Description|
|---|---|---|
|**index**|*integer*|Index of post|
|**selftext**|*string*|Main text of the subreddit posts|
|**title**|*string*|Title of subreddit posts|

---
# EDA
We have performed 3 different types of Count Vectorizer for our EDA process, namely (1,1) Count Vectorization, (2,2) N-gram Vectorization and TF-IDF Vectorization. We started by cleaning out text by removing punctuations, before removing stopwords. Subsequently, we lemmatized the words, before count vectorization was applied.

Note that we have decided to use lemmatization instead of stemming mainly because stemming typically result in words that are in weird formats. Also we have access to hardware to process our data, which is also another consideration for our project.

Additional stopwords were discovered when we performed our initial count vectorizing and were removed as much as possible.

We have gathered the top 20 words in both single words and 2 word phrases that are used for both smokers and alcoholics. We also have managed to find several useful words that will aid in our classification problem.

We also gained insights to how people with alcoholism or smoking problems think. We found that most of them know about their problems, and that they are usually trying to seek help.

---
# Modelling
We have decided to use Naive Bayes models (Bernoulli, Multinomial and Gaussian) and KNN model for our problem.


## Analysis of Model Metrics

From looking at our train and test data score, it appears that Multinomial Naive Bayes model scored the highest for both scores amongst all the other models we tested. A high score indicates that the model is more accurate in predicting whether our post belongs to alcoholic or smoking subreddits. 

From our confusion matrices, it appears that both our Gaussian Model and optimised Bernoulli falls short of expected results, with optimised Bernoulli unable to reach above a 0.9 F1 score. This leaves our Bernoulli, KNN and Multinomial models. However, Multinomial Naive Bayes scored consistently higher in all metrics amongst these model. This indicates that the error percentage of Multinomial Naive Bayes is lesser compared to the other models.

For our AUC metrics, It is clear that only KNN and Multinomial Naive Bayes scored a 0.99, with the rest falling short. This indicate to us that KNN and Multinomial models are possible models we can use to predict our posts.

Also note that amongst the 3 Naive Bayers models, Multinomial is likely the most suitable because Bernoulli's model is more suitable for binary data, whereas Gaussian model is more suitable for data that falls into a normal distribution Multinomial algorithm on the other hand is more suitable for textual data.

From these metrics, we can therefore shortlist either KNN modelling or Multinomial Naive Bayes model.

We have decided that Multinomial Naive Bayer's model is the most suitable model for our predictive model. Multinomial Naive Bayers model scored consistently higher in both test and training prediction score compared to our KNN model. Also, we note that Multinomial Naive Bayers also scored generally well for all different count vectorization methods that we employed.

## Comparison of our Selected Model to Baseline Model

It is clear that our model outperforms our baseline model's R2 score of 95% against 55% on our test data. This thus addresses our problem of not having a proper algorithm to classify incoming posts from patients based on the worded text. Our model has a higher level of accuracy in classifying incoming patient's posts with our machine learning model.

## Future Improvements
---
As we can see from our earlier data, we have attempted to remove stopwords from our data. It is highly likely that our data may not necessarily be the cleanest data due to the presence of special characters or unknown formatting. We can potentially look to remove these special characters as a future optimisation of our model.

Also, we can apply much larger N-Gram Vectorization to our data to see if it yields usable data. Consideration is given however, to the processing power of the system we have and is thus determined that we will explore with (2,2) N-gram as it is computionally less expensive than any higher numbers. With the use of cloud services such as AWS, Colab or Azure we may be able to perform these higher N-Gram Vectorizations for more insights and results.

Additionally, some future posts sent by patients may potentially contain issues for both smoking and alcoholics, it may be useful to be able to classify these post into both categories as well.

Some posts may not contain related issues to our model but may be other issues, say psychological distress or depression. It may be useful to expand the scope of our algorithm by adding more subreddits for our model to learn and predict on. This will allow our model to be more comprehensive with it's approach to classifying posts.


## Future Steps
---
We can implement our algorithm into the rehabilitation center's online portal. This will ensure that patients who send posts through the portal are able to receive proper treatment psychologically and physically, and reduce wastage of resources. This also falls in line with the COVID-19 situation where many patients may potentially be unable to reach rehab centers due to regional epidermic restrictions.

---
# Conclusion and Recommendations
---

From the insights that we garnered, it appears that most people with smoking and alcoholic issues are aware of their problems and are seeking help. Increasing engagement with them through additional methods, such as with social media platforms and subreddits, are very helpful to help treat those afflicted with smoking or alcoholism since these are platforms where patients are likely to be more personable.

With the advent of COVID-19, it is more difficult for patients to get the appropriate treatment they need. With our machine learning model, we are able to successfully classify patient's post into their respective categories and allow appropriate resources and help to be directed their way.
