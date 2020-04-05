---
layout: default
---
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

### Lectures 9-11   

\\( x \\)

**Composition of Linear Maps**   

- Recall that if X,Y,Z are all sets, and \\( f: X \mapsto Y \\) and \\( g: Y \mapsto Z \\) _if we have a mapping f from X to Y and a mapping g from Y to Z_
- we can form a composite map:
    + \\( g \circ f : X \mapsto Z\\) that is defined by \\( g \circ f = g(f(x)) \\) for all \\( x \in X\\)
- we already used  







### Lectures 12-13

**Traces**  
* It is useful to have numerical invariants measuring the complexity of linear maps  
* we already have some discrete (= integer invariants)  
    * for every linear map \\( T: V \mapsto W \\)  
    * we have two integers cpaturing information about T (transformation)  
        * **nullity of T:** = dim Kernel(T) = dim Nullspace(T) = dim of the solution set to \\(Ax=0\\)  
            + **Nullspace (T)**: set of all n-dimensional column vectors such that \\(Ax=0\\), the solution set of the homog linear system.  
                * **_Theorem_**: The nullspace N(A) is a subspace of the vector space \\(\mathbb{R^{n}}\\)  
                * proof: WTS: N(A) is nonempty, closed under addition, closed under scalar multiplication:  
                * S1: the trivial solution is always in N(A)- so it's nonempty. \\(\vec{x}=\vec{0}\\)  
                * S2: WTS: \\( x,y \in N(A) => x+y \in N(A)\\)  
                    * Well, \\( Ax = 0, Ay = 0, A(x+y) = A(x) + A(y) = 0 + 0 = 0 \\)  
                * S3: \\(c \in \mathbb{R}, x \in N(A) => cx \in N(A)\\)  
                    * Well, \\(A(cx)=c*A(x) = c * 0 = 0\\)
                * QED  
        + **rank of T**: dim image(T) = ...QUESTION: any other defs?   

- turns out that for linear operators \\(T: V \mapsto V\\) we also have defined invariants which are scalars of the field \\(\mathbb{F}\\)  
    + ex: **Trace**: \\(tr: L(V,V) \mapsto \mathbb{F}\\) is  
        * the sum of elements on the main diagonal of a square matrix A  
        * the sum of its complex eigenvalues  
        * invariant with respect to change of basis  
        * trace with this def applies to linear operators in general
        * is a linear mapping: \\( tr(T + S) = tr(T) + tr(S)\\) and \\( tr(cT)= c * tr(T) \\)
        - notice inside L(V,V) (linear maps from V to V) we have a natural collection of linear operators, from each one we can get a scalar back. 
            * how can we get this scalar? 
            * given any pair (f,v) where 
                * \\(v \in V\\) is a vector
                * \\(f \in V^{v}\\) is a linear functional in the dual space = the space of all linear functionals from V to the scalar field
            * we can construct a linear operator:
                - \\(s_{f,v}: V \mapsto V, x \mapsto f(x)v \\)
                    - QUESTION: doesnt this give me a vector back?
            * but given (f,v) we can also get a natural scalar: 
                - \\( f(v)\in \mathbb{F} \\)
            * with this in mind we can form and prove the existence statement:
            * **_Lemma_**: 
                * Suppose V is finite dim vector space over \\(\mathbb{F}\\)
                * Then there exists a unique linear function:
                    - \\(tr: L(V,V) \mapsto \mathbb{F}\\)
                    - such that for all \\(v \in V\\) and \\(f \in V^{v}\\)
                    - \\(tr(s_{f,v}) = f(v)\\)
            * proof of lemma: 
                - fundamental fact: every linear function (any linear transformation) is uniquely determined by what it does to a basis (by its values on a basis)
                - from this fact, it suffices to constrct a basis of all linear functions from V to V, \\(L(V,V)\\) that consists of operators of the form \\(s_{f,v}\\) for the chosen f's and v's
                    - [more here](https://math.stackexchange.com/questions/2619275/whats-a-basis-for-mathcal-lv-w) 
                - Let \\( \mathbb{B} = \{ b_{1}.......b_{n} \} \subset V \\) be any basis of V
                - Let \\( \mathbb{B}^{v} = \{b_{1}^{v}.......b_{n}^{v} \} \subset V \\) be its dual basis
                - Then we can say that the collection of operators 
                    - \\( \mathbb{S} = \{ s_{{b_{1}}^{v},b_{1}}.......s_{{b_{n}}^{v},b_{n}} \} \\) is a basis of \\(L(V,V)\\) the set of all linear functions from V to V
                        * basis = spanning + linearly independent. 
                        * here, each \\({b_{i}}^{v}\\) is a linear functional from the dual basis, and each \\(b_{i}\\) is a vector from the basis of V. Each gets plugged into the linear operator s and spits out a and spits out a \\( {b_{i}}^{v} * b_{i} \\), which is QUESTION: a vector in V?
                    - proof that \\( \mathbb{S} \\) is a basis for L(V,V): 
                        * S1: \\( T: V \mapsto V \\) is a linear map.  
                            - Let \\( A \in Mat_{nxn}\mathbb{F} \\) be the matrix of T in the basis \\( \mathbb{B} \\)
                                + note: we can always represent a linear transformation/mapping by a matrix in its
                        * S2: Then \\( T =  \sum_{i,j=1}^{n} a_{ij} * s_({ b_{{ji}^{v}}, b_{i}}) \\) 
                            * for every \\( k = 1,....,n \\), we have
                            * \\( T(b_{k}) =  \sum_{i=1}^{n} a_{ik} * b_{i} \\)
                            * and we also have:
                            * \\( (\sum_{ij} a_{ij}*s_{{b_{ji}}^{v}b_{i}} )(b_{k}) \\) 
                            * \\( =  \sum_{ij} a_{ij}*s_{{b_{ji}}^{v}b_{i}}  (b_{k}) \\)
                            * \\( =  \sum_{ij} a_{ij} {b_{j}}^{v}(b_{k})b_{i} \\)
                            * \\( = \sum_{i=1}^{n} a_{ik} * b_{i} \\)
                        * S3: Thus, \\( T = \sum_{ij}a_{ij}s_{{b_{j}}^{v}, b_{i}} \\)
                        * This representation is unique since the matrix of T in the basis \\( \mathbb{B} \\) is uniquely determined by T and \\( \mathbb{B} \\) 
                            *("linear extension theorem" - a linear transformation is uniqely determined by what it does to a basis.) ?
                        * by the characterization of linear maps (the one descirbed above?) we then have a unique linear function, trace:
                            - \\( tr: L(V,V) \mapsto \mathbb{F} \\)
                            - ENDED PG 7 REVISIT AFTER LEC 9-11

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





### Extra notes/defs to categorize later
**Dual Spaces and Dual Basis**
* The dual space of V is the set of all linear functionals from V to \\(\mathbb{F}\\( , so : \\(V^{v} = T: V \mapsto \mathbb{F} \\( 
    - all such elements of dual space are linear functionals
- if dim(V) < \\(\infty\\( => \\(V\\( and \\(V^{v}\\( are isomorphic
    + to show this is true, show that they have the same dimension
    + another way to show the isomorphism is to use the dual basis
        * linear extension theorem: says if you know what T does on basis vectos, you know what T does on every vector:
            * Let \\(\mathbb{B} = \{ v_{1}....v_{n} \}\\(
            * enough to know what \\(f(v_{1}),.....,f(v_{n})\\( is 
            * usually hard to graphically represent linear transformations, but since the codoamin of all such linear functions are scalars, \\(f: V \mapsto \mathbb{F}\\(, you can draw a graph of your linear functionals (where your inputs end up.)
            


**Isomorphism**
* mapppings that are injective and surjective (1:1 and onto) 
