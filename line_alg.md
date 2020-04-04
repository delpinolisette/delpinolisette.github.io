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
            + **Nullspace (T)**: set of all n-dimensional column vectors such that $$Ax=0$$, the solution set of the homogenous linear system. 
                * **_Theorem_**: The nullspace N(A) is a subspace of the vector space $$\mathbb{R^{n}}$$
                * proof: WTS: N(A) is nonempty, closed under addition, closed under scalar multiplication:
                * S1: the trivial solution is always in N(A)- so it's nonempty. $$\vec{x}=\vec{0}$$
                * S2: WTS: $$ x,y \in N(A) => x+y \in N(A)$$
                    * Well, $$ Ax = 0, Ay = 0, A(x+y) = A(x) + A(y) = 0 + 0 = 0 $$
                *S3: $$c \in \mathbb{R}, x \in N(A) => cx \in N(A)$$
                    * Well, $$A(cx)=c*A(x) = c * 0 = 0$$
                * QED
        + **rank of T**: dim image(T)
    - turns out that for linear operators $$T: V \mapsto V$$ we also have refined invariants which are scalars of the field $$\mathbb{F}$$ 
        + ex: **Trace**: $$tr: L(V,V) \mapsto \mathbb{F}$$
            * the sum of elements on the main diagonal of a square matrix A
            * the sum of its complex eigenvalues
            * invariant with respect to change of basis
            * trace with this def applies to linear operators in general
            * is a linear mapping: $$tr(T + S) = tr(T) + tr(S)$$ and $$ ts(cT)= c*tr(T) $$
            * notice inside L(V,V) (:= linear maps from V to V) we have a natural collection of linear operators, from each one we can get a scalar back. 
                * how can we get this scalar? 
                * given any pair (f,v) where 
                    * $$v \in V$$ is a vector 

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
