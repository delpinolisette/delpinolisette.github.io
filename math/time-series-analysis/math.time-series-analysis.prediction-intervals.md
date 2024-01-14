---
title: Prediction Intervals
layout: post 
---

<!-- 
https://joaquinamatrodrigo.github.io/skforecast/0.4.3/notebooks/prediction-intervals.html

boss shared this link so taking notes to work through it -->

Notes on Time Series Forecasting 

last updated: Dec 2023

# Prediction Intervals in Multi Step Forecasting Models 

## Point forecasting
- when trying to guess at future values, most forecasting models will try to guess the exact value, called a **point estimate**
  - this is "point forecasting" 
- this kind of prediction is useful, but lacks information about the confidence of the model regarding that estimate, or the prediction uncertainty/range. 

## Probabilistic Forecasting (Techniques)
In comes probabilistic forecasting. 
- in differentiation from point forecasting, these techniques provide the expected outcome of a single feature value. 
  - QX: feature or dependent? ans: dependent
- so, prediction intervals give you the interval in which the true value of the response is expected to be, within a given probablity. 
  - IX: this can be applied to QM models?

<!-- ## One step ahead vs. multistep ahead forecasts 

- [ ] TODO -->

### Interval Prediction for residuals following a normal distribution 
- if you assume that the residuals of the model follow a normal distribution, then there are several methods that will work for prediction intervals: https://otexts.com/fpp3/prediction-intervals.html

### Interval Prediction for residuals not following a normal distribution 
- two commonly used alternatives when your residuals do not follow a normal distribution are bootstrapping and quantile regression. 
- They have different strengths, and have tried both, but I prefer bootstrapping for smaller, volatile data sets. 

<!-- #### Example of getting prediction intervals for assumption of non-normally distributed residuals with boostrapped residuals and recursive multi step forecasting 

- we can define the error of a one-step ahead forecast as $e_t = y_t - $
- so, the error at time t is ... -->

<!-- 2023.11.04 2023-11-04 11:11 -->

It is also important to view the autocorrelation function plot (see ACF plots) as those will tell you the window you can use for prediction. 

<!-- how do you interpret these formally? -->

<!-- # different libraries for this 

- i tried prophet because people said it owuld be more accurate but not so for me so far 
- best is using ForecasterAutoreg -->
