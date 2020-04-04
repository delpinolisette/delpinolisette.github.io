---
layout: default
---
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

### Lectures 12-13

**Traces**
* It is useful to have numerical invariants measuring the complexity of linear maps 
* we already have some discrete (= integer invariants) 
    - for every linear map $$T: V \mapsto W$$
    - we have two integers cpaturing information about T (transformation)
        + **nullity of T:** = dim Kernel(T) = dim Nullspace(T) = dim of the solution set to $$Ax=0$$
            + Nullspace (T): set of all n-dimensional column vectors such that $$Ax=0$$, the solution set of the homogenous linear system. 
                * _Theorem_: The nullspace N(A) is a subspace of the vector space $$\mathbb{R^{n}}$$
                * proof: WTS N(A) is nonempty, closed under addition, closed under scalar multiplication:
                * S1: the trivial solution is always in N(A)- so it's nonempty
        + ****

### Lecture 14: Row Reduction

Outline
1. Simplifying Linear Systems
2. Row Reduction and Echelon Forms
3. Solving Systems with Row Reduction
4. Corollaries

** Solving a Linear System **
*  using row and column operations we can convert every linear system into a system in which all variables separate
    -  _row operation_: 
    -  _column operation_:
