# Project 2019
This is the repository for submitting your final assignment.

## Name: 
Qiang Ha
## LSE ID:
201851260
## e-mail:
q.ha@lse.ac.uk
## Project title:
Analysis of Misinformation Diffusion on Twitter Network during the 2016 US Election with Google Cloud Storage and Pyspark
## Summary:
Misinformation has become more and more prevalent and pervasive in our lives and have a serious impact on real-world events. 
This project hopes to contribute to the ongoing research of fake news detection on social media. The aim of this project is to compare fake news and true news in Twitter on both tweet level (e.g time/location of tweets), user level (e.g. favourite count for user) and the linguistic level (topic modelling), and identify characteristics that distinguish fake news from true news.

## Dataset
I will use a dataset collected by Barbera (2018) from Oct 12nd to 01st Nov, 2016. The dataset contains tweets that mentioned Hillary Clinton and Donald Trump from 30 before the election day, Nov 8th, 2016 until 10 days before the election date. In total, there are about 60 million tweets--50 GB of json.gz files （800GB of json file after decompressing. The unzipped files are stored in google cloud storage, available upon request.

A tweet json object is formed of 5 parts: Tweet Object (tweet status), User Object (user info), Entities Object (raw tweet), Extended Entities Object (contains media info), Geo Object (contains geo location of the tweet). A sample tweet can be found at https://gist.github.com/pandafulmanda/4442be1d0208b3b087fe1f61b0a70e75. Tweet schema can be viewed at twitter_schema.ipynb in the main folder.

## Research Methodology

The project is divided into three parts

1. preprocessing and fact checking

Firstly, I preprocessed the tweet json obejcts to select tweet level, user_level information related columns that may be useful in distinguishing fake news and true news. Then I fact checked each tweet and created a new column to store the result. 
* Please see fact_checking.ipynb for implementation. *

2. Topic analysis

I used Latent Dirichlet Allocation models to model the topics in twitter. For the 20 day periods, I ran the model to extract the top features to compare topics of true news and fake news and analyse the differences of topics and top features for fake and true news.

* Please see topic_modelling.ipynb for implementation. *


3. Analysis of tweet and user level features

I extracted tweet and user level characteristics and checked if they can be used as features to distinguish true or fake news. I used logistic regression with lasso penalty to do feature selection.

* Please see user_tweet_level_features.ipynb for implementation. *


---
Files included in the repositories:

#### Main folder:
Main analysis files

Analysis of Misinformation Diffusion on Twitter Network during the 2016 US Election with Google Cloud Storage and Pyspark.ipynb -- main results and workflow of the analysis

domains.csv -- a list of credible news websites and fake news websites

distributed computing technology.ipynb -- information about distributed computing technology used in the project

fact_checking -- fact checking tweets (using domains.csv)

topic_modelling.ipynb -- topic modelling for fake and true news

twitter_schema.ipynb -- schema of tweet json object

user_tweet_level_features.ipynb -- Analysis of tweet and user level features

#### Helper folder
Helper files

cluster.md -- how to create a cluster on Google Cloud

my-actions.sh -- an intialisation script useful for topic modelling

preprocessing.md -- some terminal commands to do preprocessing


##  Misinformation Diffusion on Twitter Network during the 2016 US Election.ipynb in the main folder contains main part of the analysis

