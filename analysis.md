---
layout: default
---
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

_Note_: I wrote these notes with inspiration from "Elementary Classical Analysis" by Marsden as well as several Lab lectures and classroom lectures at UPenn. 

**Table of Contents:**

[Ch. 5 : Uniform Convergence](#chapter-5-uniform-convergence)



## Chapter 5 Uniform Convergence 
Outline: 

* intro 
* Pointwise and Uniform convergence
* Weistrass M Test
* Integration and Differentiation of Series
* The Elementary Functions
* The Space of Continuous Functions
* The Arzela-Ascoli Theorem
* The Contraction Mapping Principle and Its Applications
* The Stone-Weistrass Theorem
* The Dirichlet and Abel Tests
* Power Series and Cesaro and Abel Summability
* Examples and Exercises (end of chapter). 

* **intro**: 
    -  some functions are defined using infinite sequences or infinite series. We need specific tests to study the uniform convergence of such functions. Some helpful tests are : Weistrass M Test for series and the Cauchy criterion, everything else is more specialized. 
    -  for uniform convergence we deal with the vector space of continuous functions.
        + here the "vectors" or "points" are cts functions. 
        + here the convergence of a sequence \\( == \\) uniform convergence of these cts functions. 
        + This space is _complete_ (why?) because Cauchy sequences converge within it. 
        + Thus space has the _Arzela-Ascoli_ theorem applied in it, which talks about compactness of some subsets. 
        + The _Stone Weistrass Theorem_ is also useful here, it allows you to approximate continuous functoins by series. 
        + The contraction mapping principle leads the way to applications to integration and differentiation. 

* **Pointwise and Uniform Convergence:**
    - pointwise is the most natural way to think about convergence. 
        + (why?) because we only ask for each point \\(x\\) in the domain the sequence \\(f\_{k}(x)\\) converges. 
    - **pointwise convergence** (def) : 
        + \\(N\\) is a metric space. A is a set. \\(f\_{k} : A \mapsto N\\) for \\(k = 1,2,3.....\\)
        + then the sequence of functions \\(f\_{k}\\) is said to converge pointwise/ converge simply to a function \\(f : A \mapsto N\\) if...
            * for each \\(x \in A\\) 