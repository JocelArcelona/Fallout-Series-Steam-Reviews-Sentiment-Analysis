# Fallout-Series-Steam-Reviews-Sentiment-Analysis
![8d22f283b530203b355e0b9800a4cd09](https://user-images.githubusercontent.com/108106393/218854660-307ddfeb-4a22-4342-b336-a92f02a75e61.png)

# Business Problem 
Bethesda Game Studios just got bought by Microsoft and currently has an influx of budget to produce their next Fallout title. However, they lack the understanding of what factors are driving players to recommend or not recommend the game.  

# Objectives
Here are the objectives of this project: 
1. This project aims to understand the overall player sentiment towards the Fallout Series using Natural Language Processing 
2. To identify the most common themes and topics that emerge from player reviews using Gensim's Topic Modeling 
3. To provide insights and recommendations to Bethesda Game Studios on how to improve user experience based on player reviews
4. To create a sentiment analysis model that can accurately predict a players sentiment towards the Fallout Series

# Data
The data used in this project was scraped from the STEAM app. It contained 320,000 reviews consisting of 22 features. I concatenated 6 different datasets from 6 different fallout titles. At the end of data cleaning, I ended up using 192,000 of these reviews after dropping non-english reviews and reviews that consisted of NANs. On my NLTK predictive model I had 192,000 data points with around 530 features and on my GENSIM predictive model, I had 192,000 reviews with 330 features. 

# Methods 

Data Collection: I had to manually web scrape reviews from all the 6 different Fallout Titles from the STEAM app (Fallout 3, Fallout 3 Game of The Year Edition, Fallout 4, Fallout 76, Fallout New Vegas, Fallout Shelter). I originally scraped 320,000 datapoints after combining all reviews
Data Pre-processing for NLTK (Unigrams): For my NLTK preprocessing, I used a function that lowercases textual data, removes all the stop words, removes all non-english patterns, tokenizes then lemmatizes the data before vectorization. Once the data has been cleaned, I vectorized it to prepare it for predictive modeling along with all my other numerical features. 
Data Pre-processing for Gensim (Bigrams): For my Gensim preprocessing, I did the same data cleaning on my reviews and once the data is cleaned, I plugged it to Gensim's Phrases object to generate Bigrams. I vectorized these Bigrams, converted it to an array and added it to my numerical features for predictive modeling. 
Data Visualization and EDA: I wanted to see which words under the positive and negative reviews will show up the most so I used Gensim's Topic Modeling to generate topics and create a visualization of the words that occur the most in those topics. 
Modeling: I used accuracy as my metric for my prediction modeling. After cleaning the textual data, vectorizing it and concatenating it with the numerical features in the original dataframe, I created pipelines for each model I used. I used 4 different machine learning models namely: Multinomial Naive Bayes, Decision Trees, Random Forest and XGBoost. And due to memory allocation error, I had to reduce my feature space of 50,000 down to 530 features for the NLTK Unigrams and 29,000 features down to 330 features for the Gensim Bigrams for modeling. I addressed the data imbalance with Synthetic Minority Over Sampling Technique and after running my predictions, I visualized the ratio of my false negatives to my false positives using the ROC-AUC curve. I also used an ensemble method and stacked Multionomial Naive Bayes and XGBoost together, this classifier yielded an accuracy of 93% which is the same as the the accuracy of the XGBoost model by itself but the stacked classifier provided a better balance between the recall and the precision so I picked this as my best model. 

# Visualizations 
This graph shows the huge class imbalance in my dataset 
![classimb](https://user-images.githubusercontent.com/108106393/219446078-8bf86f86-12cf-4688-a22c-9c7a927282b5.png)

These are the models I have used for my predictive modeling: 
![Screenshot (9)](https://user-images.githubusercontent.com/108106393/219449980-95f9491f-cb2b-4006-9345-c8e9866c0791.png)

This is the result of my best model, Stacked Classifier using Multinomial Naive Bayes and XGBoost: 
![Screenshot (10)](https://user-images.githubusercontent.com/108106393/219450109-50f49c8f-d0fa-403b-823c-024c864ff6d3.png)

These graphs shows which features are the most important derived from my stacked classifier:

Numerical Features:
![numfeatures](https://user-images.githubusercontent.com/108106393/219450496-f0f82684-0b95-47ac-a7cf-6c3ebb79efc4.png)

Word Features:
![wordfeat](https://user-images.githubusercontent.com/108106393/219450639-a947252d-38b4-4ac0-a865-8ed7df2e2efb.png)

# Recommendations
1. 

