---
layout: default
title: On the Binomial Distribution
---
<script type="text/javascript"
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.3/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>


The Binomial Distribution, in simplest terms, describes the probabilities of getting $x$ successes in $n$ trials. 

For example, what is the probability of getting $$4$$ heads if i flip a _fair_ coin $$6$$ times? Also, what is the probability of getting $$4$$ heads if I flip an _unfair_ coin $$6$$ times? These questions can be answered with the Binomial Distribution!

Notice that the Binomial distribution is a **discrete** distribution. That means that for any expected values of the parent distribution, you should evaluate using sums, not integrals. 

The Binomial Distribution is also called a Bernoulli Distribution, since a single Bernoulli trial measures the probability of binary success in a single trial. 

In this post I show two ways that I implement the Binomial Distribution, even though in practice you should use the one that relies on `scipy`, especially in professional settings. 

Recall that the formula for the Binomial Distribution is ...

$$
P_x = {n \choose x} p^{x} (1-p)^{n-x}
$$

But since $$ {n \choose x} = \frac{n!}{x! (n-x)!} $$

We also have :
$$
P_x = {\frac{n!}{x! (n-x)!}} p^{x} (1-p)^{n-x}
$$


## Method 1 - Implement the formula from scratch 

`warning` : (requires lots of helper methods)

the pseudocode for an implementation like this is :


```python
# a recursive factorial defn. 
def factorial(x)
  if x > 1:
    return x*factorial(x-1)
  else:
    return 1

# returns n choose x
def choose(n,x):
  return factorial(n) / (factorial(x)*factorial(n-x))

# returns binomial PMF
def binomial_pdf(n,x,p):
  n_choose_x = choose(n,x)

  return n_choose_x * (p**x) * ((1-p)**(n-x))

```

## Method 2

This one is probably better form after you've tried implementing the binomial distribution from scratch. 

This is the method for a non-cumulative distribution, functions documented [here](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.binom.html):

```python
from scipy.stats import binom

def pb(x,n,p):
  return binom(n,p)

```
And this is the method for a cumulative binomial distribution :

```python
```