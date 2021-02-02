---
title: "Covid-19 Case Prediction"
excerpt: "Train models to predict cases trend in next 30 days"
header:
  teaser: /assets/images/corona.jpg
gallery:
  - url: assets/images/prediction.png
    image_path: assets/images/prediction.png
    alt: "Trend"
  - url: assets/images/models_comparsion.png
    image_path: assets/images/models_comparsion.png
    alt: "Comparsion"
tags: 
  - Time Series Anlysis
  - ARIMA
  - Deep Learning
  - CNN
  - RNN
  - LSTM
---
### Overview

Trained models to predict covid-19 case trend using traditional ARIMA model and deep learning models including DNN, CNN, RNN, LSTM, cross-validate performance and showcase on web app built by streamlit.

### Dash Board

Limited to given storage amount of github (25Mb), only ARIMA and LSTM models are embedded into [Streamlit Dash Board](https://share.streamlit.io/scleeza/covid19visualization/app.py)

### Build ARIMA models

- Used differentiate method to get stationary data (Generally there are 3 ways to do,Moving average, differentiate, and exponential weighted)

- Passed Stationary test through Augmented Dickey-Muller statistics (p<0.05) .

- Chose hyperparameter (p,d,q) through Auto Correlation Function and Partial Correlation Function.
    
- Fine-tuned best ARIMA hyperparameters setting by **Grid Search**

### Build Neuron Network models

- Generated time series tensor data, basically I use past 30 days data to predict cases in next 30 days.

- A train-in-once model, which generate all countries' next 30 days prediction by setting output layer neurons to country amount

- Built connecting layer to deal with time series data when using DNN and CNN model.

- Hyperparameter tuning.

- Compared MSE of each models including ARIMA (fine-tuned)

### Link

[Github](https://github.com/scleeza/COVID19Visualization/)

{% include gallery caption=" Trend chart and models performance" %}