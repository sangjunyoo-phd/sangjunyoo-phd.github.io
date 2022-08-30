---
title: "Machine Learning & Data Science Projects"
layout: archive
permalink: /mlprojects/
---

**Work in progress**

List of Machine Learning projects: Summary only.
* Climbing Qualification prediction
* Image Quantizer: James Webb image
* S&P 500 index predictor with LSTM
* BCG Virtual program

# Image Quantizer: Personalized James Web Image
![image-right](../assets/images/K_Means_10clusters.png){: .align-right}{:style="border: 0px solid black; padding: 10px"}{:height="40%" width="40%"}
* James Web Telescope published new pictures. I want to have a personalized version of them.
* Used K-Means Clustering method to Quantize the image
* Initialize the number of cluster using an Elbow Method

# BCG Virtual Experience Program: Data Science and Advanced Analytics
* Participated in BCG's open access virtual experience program with Forage: Business-oriented application of ML algorithm
* A power company wanted to reduce the "Churning" clients by providing a 20% discount. My goal is to check if the discount strategy will be effective. If so, suggest what client this company should focus on.
* Made a Random Forest classification model that predicts the client's churning state based on historical price data.
* Find there is no significant correlation between churning state and price so 20% discount strategy is going to be ineffective.
* Instead, I found clients with high energy consumption are less likely to quit the service. Suggested to focus on providing promotion to new customers with high energy consumption.

# IFSC Climbing Worldcup Qualification Predictor
* Exploratory projects to be familiarized with classification problems including EDA, Feature Engineering, Modeling, and evaluation
* Make a model that predicts if a player will pass the qualification when his/her score is provided with a Machine Learning algorithm
* Logistic Regression, Support Vector classifier, and Random Forest model were deployed
* No significant differences were found between Logistic Regression and Support Vector Classifier models (accuracy: ~0.8). Random Forest yielded slightly worse performance (accuracy: ~0.7)