---
title: "Mechanisms of Action (MoA) Prediction"
excerpt: "Predict MoA from data of gene and cell vitality, build multi-label classifier"
header:
  teaser: /assets/images/pill.jpg
 
tags: 
  - Kaggle
  - tensorflow
  - ML Pipeline
  - Deep neuron network
---

- [Data Description](https://www.kaggle.com/c/lish-moa)

- [Notebook link](https://www.kaggle.com/scleeza/cv6-tfa-labeling)


## Quick View
__Goal__: 
 
 - Predict MoA (only 0 and 1) from data of gene and cell vitality, build multiple binary classifier

__Metrics__: 
 - Minimum Log loss

__Procedure__:
   - MoA tag are extremely imbalanced, average 89 positive tags in each column from 21K entries, so a special kfold function has beed used
   ```python
from iterstrat.ml_stratifiers import MultilabelStratifiedKFold
   ```
    
   - Label Smoothing has been conducted to help improve accuracy in this multiple output case [A great explanation here](https://www.pyimagesearch.com/2019/12/30/label-smoothing-with-keras-tensorflow-and-deep-learning/)
    
   - Use Pipeline function to automatically finished column transform
       - Numerical data
         - Quantile transform
         - PCA
       - Categorical
         - One-hot-labeling  
         
   - Build DNN model with 3 NN layer with appropriate regulation.    
   - Use __keras.tuner__ to do hyper parameters tuning and code is in [Notebook](https://github.com/scleeza/ML-Projects/blob/main/MoA/hyperparam.ipynb)

## Links 
[Github](https://github.com/scleeza/ML-Projects/tree/main/MoA)