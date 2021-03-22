---
layout: default
title: Maximum Likelihood Estimate
---
<script type="text/javascript"
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.3/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

## What is the Goal of Maximum Likelihood Estimate?

- The goal of ML (max likelihood) is to find the optimal way to fit a **distribution to your data**. 
- MLE is the answer to the question "what does my underlying model look like?"
- when we estimate values we think in terms of maximum likelihood estimates for parameters that we care about, such as the mean $$\mu$$, or the maximum likelihood estimation for the standard deviation $$\sqrt{\sigma}$$


- A useful example, for me at least is the role MLE in **Logistic Regression** (makes the most visual sense). 

Note from 03-22-2021...

A longer writeup is coming up soon, but in the case where you only have to classes in your classification (ex. hotdog or not a hotdog (haha....)) the MLE simplifies to a different, simpler sum. And by simpler I mean a sum that doesn't cause numerical underflow in Python by avoiding the case of `log(0) = -inf`. 

