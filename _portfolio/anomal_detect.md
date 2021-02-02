---
title: "Anomaly Detection Algorithm"
excerpt: "Using Phase 1 analysis to detect outliers and build SPC chart"
header:
  teaser: /assets/images/outlier-th.jpg
gallery:
  - url: assets/images/pareto.png
    image_path: assets/images/pareto.png
    alt: "PCA"
  - url: assets/images/t_test.png
    image_path: assets/images/t_test.png
    alt: "Hotelling T applied"
tags: 
  - Statistical Process Control
  - PCA
  - Multivariate 
---

### Overview
_Using Phase 1 analysis to detect outliers and build SPC chart_, implemented algo.rithms by Numpy

   > _Phase 1 analysis means the process of applying SPC chart to a training data, however data has unknown population mean and variance._

### Procedure

-  Applied PCA, reduce dimension of the dataset, avoid curse of dimesionality.
-  Calculated Hotelling T2 test for phase 1 analysis, we use T2 statistics to represent  how data point is located in a multivariate normal distributon (like t-statistics did). 
-  Plot SPC so as to locate outliers (find UCL/LCL, under alpha = 0.05, basically lookup from dist table).
-  Multi-variate chart like CUSUM or EWMA are also implemented to do outlier detection in case that T2 missed some small shifts.

    >In a high dimension, the noise components can add up to a great magnitude, even if individual ones are relatively small. As a result, the aggregated noise effect can overwhelm the signal effects and makes it harder to reject the null hypothesis. This is known as "curse of dimensionality."
                                                                                                                  
{% include gallery caption=" PCA and applied with T2 statistics " %}    

### Link
[Github](https://github.com/scleeza/PCA-and-HotellingT)                                                                                                                 