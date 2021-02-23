---
title: "Predict Survival on the Titanic"
excerpt: "Training by all modern ML classifiers   "
header:
  teaser: /assets/images/titanic.jpg
gallery:
  - url: assets/images/xgboost.png
    image_path: assets/images/xgboost.png
    
 
tags: 
  - Kaggle
  - Sci-Kit Learn
  - ML Pipeline
  - XGBoost
---

## Quick view

__Goal__: it is trying to use passenger list (e.g. Name, Sex, Class, Age...etc) to classify one would servive or not.

__Metrics__: Accuracy 

__Results__:

- __Baseline:__ 
    * NaiveBayes (val_acc = 0.78)
    * Logistic (val_acc = 0.79)


- __Feature Engineering:__
    * Have age from continuous number into categorical bins
    * Clean text feature "Title"
    * Create new feature "family size" by sum up parents and childern
    * One-hot-label to categorical features, and Standarscaler() for numericals.
    
    
- __ML Models:__
    * Logistic regression (val_acc: 0.829)
    * KNN (val_acc: 0.829)
    * Decision Tree (val_acc: 0.836)
    * Random Forest (val_acc:0.831)
    * SVM (val_acc:0.829)
    * __XGBoost (Val_acc:0.841)__
    
    > All models has been fine-tuned by RandomSearchCV

{% include gallery caption="XGBoost training and validation plot " %}

## Links
[Github](https://github.com/scleeza/ML-Projects/tree/main/Titanic-ML-master)