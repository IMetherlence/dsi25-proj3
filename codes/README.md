# Project 3

## Context
We are a group of consultants who are hired to present our data models to a panel of directors in rehabilitation centers for smokers and alcoholics.

## Problem Statement
The recent COVID-19 situation have resulted in several people with smoking or alcohol issues not being able to access rehabilitation services readily. This has led to a rise in alcoholism and smoking. The directors of these rehabilitation centers are looking for ways to better treat these patients and are of the opinion that engaging patients online is a field that should be explored. One way to engage the patients is in their subreddits, as this will make the treatment more personalised for the patients.

Our director has requested us to create an algorithm that can more efficiently process requests from patients who will be using their online platform for rehabilitation. Thus, our algorithm will used to sort patient's comments and posts into the necessary rehabilitation categories.

## Goal of this Data Analysis
Our goal in this data analysis is to be able to classify our patient's posts into smoking or alcoholic issues. This problem is a classification problem, and requires supervised machine learning. We will be using the Naive Bayers and KNN Classification models in our data analysis.

It is important to note that this project is a classification problem. Thus, Supervised learning based on our classification models will be used to model our data.

## Executive Summary


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

# EDA

We have performed 3 different types of Count Vectorizer for our EDA process, namely (1,1) Count Vectorization, (2,2) N-gram Vectorization and TF-IDF Vectorization.

We have gathered the top 20 words in both single words and 2 word phrases that are used for both smokers and alcoholics. We also have managed to find several useful words that will aid in our classification problem.

We also gained insights to how people with alcoholism or smoking problems think. We found that most of them know about their problems, and that they are usually trying to seek help.

# Modelling
