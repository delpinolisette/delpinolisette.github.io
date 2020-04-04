---
layout: default
---
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

Read:
- Sec 1.1
- Sec 1.2
- Sec 1.4
- Sec 8.1

1. Let V be the $$\mathbb{R}$$- vector space of real valued continuous functions on the interval [$$-1,1$$]. Which functionals are linear? Which are not and why? (Functionals just send a vector from the vector space to a value in the scalar field)
    - a. $$\int_{-1}^{1} f(x)dx$$
    - b. $$\int_{-1}^{1} f(x)^{2}dx$$
    - c. $$f \mapsto f(0)dx$$
    - d. $$\int_{-1}^{1} f(x)dx$$

    - solutions:
    - **linear transformation def:** $$T(ax+by) = aT(x) + bT(y)$$ for all $$x,y \in V$$ (vector space) and $$\forall a,b \in$$ scalar field
    - **affine def** f(x) = ax + b is _affine_ - not linear, it's a translation of something linear. 
    **1a**
    * S1: notice that this would be a linear functional because it sends a vector from the vector space ($$f \in $$) set of all continuous functions in [-1,1] to a _definite integral_ , which is a scalar value in $$\mathbb{R}$$
        - if it were not a definite integral we would run into problems. 
        - QUESTION: is an indef integral a linear functional?
    * S2: check additivity: f,g, in Vector space. what is f+g
        - $$f+g = \int_{-1}^{1} (f+g)(x)dx = \int_{-1}^{1} f(x) + g(x) dx$$
        - $$\int_{-1}^{1} f(x)dx + \int_{-1}^{1} g(x)dx $$
    * S3: check homogeneity: aT(v) = T(av)
        - $$a$$ is a scalar. $$f$$ is a vector in vector space. 
        - $$a * T(f)$$ = a \int_{-1}^{1} (f)(x)dx = \int_{-1}^{1} a(f)(x)dx $$