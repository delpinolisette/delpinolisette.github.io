---
layout: default
title: On the Binomial Distribution
---
<script type="text/javascript"
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.3/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>


The Binomial Distribution, in simplest terms, describes the probabilities of getting $x$ successes in $n$ trials. 

For example, what is the probability of getting $$4$$ heads if i flip a _fair_ coin $6$ times? Also, what is the probability of getting $4$ heads if I flip an _unfair_ coin $6$ times? These questions can be answered with the Binomial Distribution!

Notice that the Binomial distribution is a **discrete** distribution. That means that for any expected values of the parent distribution, you should evaluate using sums, not integrals. 

The Binomial Distribution is also called a Bernoulli Distribution, since a single Bernoulli trial measures the probability of binary success in a single trial. 

In this post I show two ways that I implement the Binomial Distribution, even though in practice you should use the one that relies on `scipy`, especially in professional settings. 

Recall that the formula for the Binomial Distribution is ...

$$
P
$$

## Method 1 - Implement the formula from scratch 

`warning` : (requires lots of helper methods)

the pseudocode for an implementation like this is :

```

```