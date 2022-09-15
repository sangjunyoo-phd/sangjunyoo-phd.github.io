---
title: "Deep Learning"
layout: archive
permalink: /deeplearning/
toc: true
---

**Work in progress**

Post what I have studied

List:
* ANN and back propagation with example code (2 hidden layers with 2 nodes)
* RNN and explosion/vanishing
* LSTM (why RNN to LSTM)

# Predict the Open and Close prices of the S&P 500 Index with LSTM
I made an LSTM model that predicts the open and close price of the S&P 500 index based on historical data. The historical price data (past 5 years) is scraped from Google Finance. The open and close prices of the next date are predicted based on the past 30 days' data with 5 features: Open, Close, High, Low, and Volume. The first 80% was used as training data, the next 10% as test data, and the last 10% as evaluation data (back-testing). The model evaluation is processed as follows. The model trained with a training set is evaluated with test data to estimate the performance of the model with unseen data. The model has been trained again with the train+test dataset (first 80%+10% = 90%) and evaluated again with the evaluation set. If the model performs as predicted, the evaluation metric from the previous step and this step should be similar to each other.

## Why LSTM?
By the time I started this project, the only deep learning technique that I know was Artificial Neural Network (ANN). There are several shortcomings with ANN to make a prediction model with historic data (time-series or sequential data). The problem arises from:
* Increased feature dimension
* Train/Test split

### Why not ANN: Increased Feature Dimension
The ANN cannot tell the past/future data. It predicts the value from the same data entry (i.e. predict one value from other columns within the same row). Therefore, it is necessary to increase the feature dimension to contain the past data within a row. For example, the past data such as a mean of the past 3 days, 5days, ... should be added after the original features. To get an acceptable prediction power, I had to expand the feature dimension by 53, which is exactly the opposite of an ideal situation. Other than this, there are more serious problems left.

### Why not ANN: Test/Train Split
To avoid overfitting, it is necessary to test the trained model with "unseen" data. A random split of the data is a typical way to deal with this problem. Randomized splitting is necessary to avoid biased sampling. In this case, however, the random split cannot produce the "unseen" test data. Let's assume the mean of the past 3 days has been added as a feature. If the "random" split assigns 500th data to the test set and 501st to the training set, the model "sees" the information from the 500th entry (test) as a form of a mean of the past 3 days. Therefore, there is no truly unseen test data with the randomized split.

### Why not RNN
After doing some research I found that __Recurrent Neural Network (RNN)__ is capable of dealing with sequential data (or equivalently called as "time-series" data). However, RNN could not predict the S&P prices as well as I wished. The RNN algorithm can hardly deal with the old data becuase it uses fixed weight. <br/>
For example, I am dealing with sequential data that contains information from past 30 steps. It means the oldest data will be multiplied by weight 30 times: $aW^{30}$.



# Artificial Neural Network (ANN) and Backpropagation
Test
## a
a
## b
b
## c
c

# RNN
RNN and its limitation
