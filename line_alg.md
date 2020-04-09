---
layout: default
---
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

#### Table of Contents:
* [Lectures 9-11](#lectures-9-11)
* [Lectures 12-13](#lectures-12-13)
* [Lecture 14](#lecture-14)

### Lectures 9-11   

**Composition of Linear Maps**   

- Recall that if X,Y,Z are all sets, and \\( f: X \mapsto Y \\) and \\( g: Y \mapsto Z \\) _if we have a mapping f from X to Y and a mapping g from Y to Z_
- we can form a composite map:
    + \\( g \circ f : X \mapsto Z\\) that is defined by \\( g \circ f = g(f(x)) \\) for all \\( x \in X \\)
- we already used the notion of composition to define invertible/bijective maps of sets. 
- composition also preserves the property of maps being linear!! _verycool_ we state it formally and prove it:
- **_Claim_**: The composition of two linear maps is also linear. Let U, V, W be \\( \mathbb{F} \\) vector spaces. 
    + Let these be linear maps:
    + \\( T: U \mapsto V \\) and \\( S: V \mapsto W \\)
    + the compositon of these is also linear:
    + \\( S \circ T : U \mapsto W \\)
- _proof_: Let \\( x,y \in V \\), \\( c \in K \\). Then:
    + \\( S \circ T(x+y) = S(T(x+y)) = S(T(x) + T(y)) = S(T(y)) + S(T(y)) = S \circ T(x) + S \circ T(y) \\)
    + also, \\( S \circ T(cx) = S(T(cx)) = S(cT(x)) = cS(T(x)) = cS \circ T(x) \\)
    + QED
- Thus the operation of compositions gives yet another way of constructing new linear maps out of known ones.   
- Under our dictionary that uses bases to convert linear maps to matrices and matrices back to linear maps (QUESTION: lets see an example)
    + => the natural operations on linear maps that produce new linear maps just become the natural operations of matrices (that produce new matrices?)
    + **_Theorem_**: Let U, V, W, be \\( \mathbb{F} \\) -vector spaces with bases:
        * \\( \mathbb{E} = \{ e_{1},.......,e_{n} \} \subset U \\)
        * \\( \mathbb{F} = \{ f_{1},.......,f_{n} \} \subset V \\)
        * \\( \mathbb{G} = \{ g_{1},.......,g_{n} \} \subset W \\)
    * (1) : If \\( T_{1}: U \mapsto V, T_{2}: U \mapsto V  \\) are linear mappings, \\( c \in \mathbb{F} \\)
        - and \\( A_{1}, A_{2} \in Mat_{mxn}\mathbb{F}\\) are matrices of \\( T\_{1}, T_{2} \\) in the bases \\( \mathbb{E}, \mathbb{F} \\)
        - then matrices of :
            + \\( T_{1} + T_{2}: U \mapsto V \\) == \\( A_{1} + A_{2} \\)
            + \\( cT_{1}: U \mapsto V \\) == \\( cA_{1} \\)
        - in our bases \\( \mathbb{E} \\) and \\( \mathbb{F} \\)  
    * (2) :  (Linear mapping composition corresponds to matrix multiplcation): if \\( T: U \mapsto V \\) and \\( S: V \mapsto W \\) are linear mappings and 
        - T has an (m x n) matrix A with bases E (from U) and F (from V) [bases from domain and codomain]
        - S has a (k x m) matrix B with bases F (from V) and G (from W) [bases from domain and codomain]
    * Then \\( S \circ T \\) has an (k x n) matrix B*A in the bases E (from domain U) and G (from codomain W)
    * _proof_: 
        * (1) follows from the definition of the matrix of a linear map
        * (2) Consider the linear map \\( f:= S \circ T: U \mapsto W \\) and let C be the matrix of of that operator \\( S \circ T \\) in the bases E (from domain U) and G (from codomain W)
            - every entry of C \\( c_{pq} \\) is given by:
            - \\( c_{qp} = \\) the q-th coordinate of the vector \\( f\_{e_{p}} \\) in the basis \\( \mathbb{G} = (g\_{1}...g\_{n}) \\)
            - we can actually compute each entry \\( c_{qp} = f\_{e\_{p}} \\) directly: 
            -  \\( f\_{e\_{p}} = S \circ T(e\_{p})  \\)
            -  = \\( S(T(e\_{p})) \\)
            -   = \\( S(A\_{1p}f\_{1} +...+ A\_{mp}f\_{m}) \\) QUESTION: where does m come from?
            -  = \\( \sum_{r=1}^{m} A\_{rp} (S\_{f\_{r}}) \\)
            -  = \\( \sum_{r=1}^{m} A\_{rp} (\sum\_{q=1}^{k} B\_{qr} g\_{q})\\)
            -  = \\( \sum \_{1}^{m} (\sum\_{1}^{m} B\_{qr}A\_{rp}) g\_q{} \\)
            -  so we have \\( c\_{qp} = \sum\_{1}^{m} B\_{qr}A\_{rp} \\)
            -   = (row q of B)(column p of A) = \\( (BA)\_{qp} \\)   
    * Example 1 : (General Reflections)
        - Let \\( L \in \mathbb(R)^{2}\\) be any line through the origin and let the transformaition \\(s\_{L} : R^{2} \mapsto R^{2}\\) be the reflection across L
        - so \\(s\_{L}\\) send a point in R^{2} to its mirrror image, where them mirror is L
        - **_Claim_** : \\(s\_{L}\\) is a linear map. 
        - _proof_: you can prove this directly using difficult geometric constructions, or you can use the fact that compositions of linear maps are linear:
        - S1: show that the reflection across the x-axis is linear:
            + \\(s = s\_{x-axis} : \mathbb{R^{2} \mapsto \mathbb{R^{2}}}\\)
            + \\s(x, y)^{t} = (x -y)^{t}\\) for all vectors x,y
            + ![reflection over x axis](delpinolisette.github.io/img/reflectx.png)
            + reflection over x axis matrix == 
            + A = \\(
                        \begin{bmatrix}
                        1 & 0  \\\
                        0 & -1  \\\
                        \end{bmatrix}  
                        \\)
        - S2: notice that reflection across L can be viewed as a composition of three linear maps:
            + 1. rotate the plane so that L becomes the x-axis
            + 2. reflect the plane across the x axis 
            + 3. rotate the plane so that x-axis becomes L
        - each of these is linear, so \\(s\_{L}\\) is linear.
        - S3: in concrete terms, \\(\theta : \\) measured in radians, counter closckwise direction, Then, 
            + \\(s\_{L} = rot\_{\theta} \circ s \circ rot\_{-\theta}\\)
            + use the previous theorem, and we can get matrices for these transformations:
            + \\(A\_{rot\_{\theta}}\\) = \\(
                        \begin{bmatrix}
                        cos(\theta) & -sin(\theta)  \\\
                        sin(\theta) & cos(\theta)  \\\
                        \end{bmatrix}  
                        \\)
            + \\(A\_{rot\_{\theta}}\\) = \\(
                        \begin{bmatrix}
                        cos(\theta) & sin(\theta)  \\\
                        -sin(\theta) & cos(\theta)  \\\
                        \end{bmatrix}  
                        \\)
            + \\(A\_{s}\\) = reflection over x axis matrix 
            + EXERCISE: derive these matrices 
            + and so \\(A\_{s\_{L}}\\) = multiplication/composition of the three: = \\(
                        \begin{bmatrix}
                        cos(2\theta) & sin(2\theta)  \\\
                        sin(2\theta) & -cos(2\theta)  \\\
                        \end{bmatrix}  
                        \\)
    * EXERCISE: Compute the matrix of the reflection over the line L with respect to the line L: y =7x in the standard basis of \\(R^{2}\\)

**Properties of the Composition of Linear Maps:**   

* (1): if 
    - \\( T \in L(V,W)\\)
    - \\( S \in L(U,V)\\)
    - then \\(T \circ S \in L(U,W)\\)
* (2) Composition is a linear map in each argument. if
    - \\( S \in L(U,V) \\) 
    - then the map \\( S \circ (-): L(V,W) \mapsto L(U,W) \\) (no entiendo? QUESTION) is a linear map between the two vector spaces L(V,W), L(U,V)
    - _example_: if \\(a, b \in \mathbb{F}\\), \\(T\_{1}, T\_{2} \in L(V,W)\\)
    - then \\(S \circ (aT\_{a} + b\_{T\_{2}})\\)
    - = \\( aS \circ T\_{1} + bS \circ T\_{2} \\). 
    - _check_: we can check this directly! just check both sides are equal to the same thing when evaluated on any vect \\(u \in U\\) (because U is domain of S? That's where we start)
    - from the definition of addition and scaling in the vector space of linear maps, [here it is!](https://math.stackexchange.com/questions/2381942/the-set-of-all-linear-maps-tv-w-is-a-vector-space/2381955)
    - = \\(S \circ (aT\_{1}+bT\_{2})(u)\\)
    - = \\(S \circ ((aT\_{1}+bT\_{2})(u))\\)
    - = \\(S \circ (aT\_{1}(u) + bT\_{2}(u))\\)
    - = \\( aS(T\_{1}(u)) + bS(T\_{2}(u))) \\)
    -  = \\( a S \circ T\_{1}(u) + b S \circ T\_{2}(u)\\)
    -  QED
    -  QUESTION:  CHECK WHETHER LINEAR MAPS IN QUESTION ARE CORRECT: THEY MIGHT BE FLIPPED IN THE NOTES! for this next one too
    -  similarly: \\(T \in L(V,W)\\), check directly that \\((-) \circ T : L(U,V) \mapsto L(U,W)\\) is linear 
        +  because \\((aS\_{1} + bS\_{2}) \circ T = aS\_{1} \circ T + b S\_{2} \circ T\\) for all a,b scalars and \\(S\_{1}, S\_{2} \in L(U,V)\\)
* (3): Inverse maps of linear maps are linear. 
    - Suppose \\(T: V \mapsto W\\) is al inear map which is bijective (is invertible as a map of sets + is injective and surjective + is one to one and onto)
    - consider the inverse map \\(T\_{-1}: W \mapsto V\\), 
    - then \\(T\_{-1}\\) is also linear. 
    - _proof_: let \\(y\_{1}, y\_{2} \in W\\) - the domain of inverse map, let \\(a\_{1}, a\_{2} be two scalars in \mathbb{F}\\)
        + WTS: \\( T\_{-1}(a\_{1}y\_{1} + a\_{2}y\_{2}) = a\_{1}T^{-1}(y\_{1}) + a\_{2}T^{-1}(y\_{2}) \\)
        + assign some names: \\( x\_{1} = T^{-1}(y\_{1}) \in V \\) and \\(x\_{2} = T^{-1}(y\_{2}) \in V \\) - V =codomain of \\(T^{-1}\\)  
        + then the RHS \\( a\_{1}T^{-1}(y\_{1}) + a\_{2}T^{-1}(y\_{2}) \\) is equal to \\(a\_{1}x\_{1} + a\_{2}x\_{2} \in V\\)
        + Let's evaluate the original map T on this vector. Remember T is linear and we get:
        + \\( T(a\_{1}x\_{1} + a\_{2}x\_{2}) = a\_{1}T(x\_{1}) + a\_{2}T(x\_{2}) \\)
        + = \\( a\_{1}T \circ T^{-1}(y\_{1}) + a\_{2}T \circ T^{-1}(y\_{2})\\)
        + = \\( a\_{1}y\_{1} + a\_{2}y\_{2} \\)
        + Thus, \\(T(a\_{1}x\_{1} + a\_{2}x\_{2}) = a\_{1}y\_{1} + a\_{2}y\_{2}\\)
        + Now let's evaluate \\(T^{-1}\\) on both sides of this identity. Literally just: 
        + \\(T^{-1} \circ T(a\_{1}x\_{1} + a\_{2}x\_{2})\\) = \\( T^{-1} (a\_{1}y\_{1} + a\_{2}y\_{2})\\)
        + => \\( a\_{1}x\_{1} + a\_{2}x\_{2}\\) = \\( T^{-1} (a\_{1}y\_{1} + a\_{2}y\_{2})\\)
        + \\( a\_{1}T^{-1}(y\_{1}) + a\_{2}T^{-1}(y\_{2})\\) = \\( T^{-1} (a\_{1}y\_{1} + a\_{2}y\_{2})\\)
        + we have shown the linearity of the inverse map \\(T^{-1}\\)
* **isomorphism** (def): the linear map \\(T : V \mapsto W\\) is an _isomorphism_ if there exists a linear map \\(S: W \mapsto V\\) s.t \\(S \circ T = id\_{v}\\) and \\(T \circ S = id\_{v}\\) (also think about corresponding definition in terms of matrices)[more info](https://math.stackexchange.com/questions/441758/what-does-isomorphic-mean-in-linear-algebra)
    - note: we checked above that a linear map is an isomorphism iff it is a bijection 
    - note: we also checked that the inverse linear map is simply the inverse set theoretic map.
* **isomorphism** (def): two vector spaces V,W over \\(\mathbb{F}\\) are isomorphic if there exists a linear map \\(T: V \mapsto W\\) which is an isomorphism (so if it is bijective). 
    - isomorphic means "has same shape". useful for turning undamiliar algebraic objects into familiar ones, making them easier to work with. 
    - note: as with sets we will not distinguish isomorphic (vector) spaces. 
        + the rational is tht using the isomorphism and its inverse we can transport any property of V to W and back again
        + these preperties and feauees that only involce teh addition and scaling of vectors are matched in V and W via the isomorphism and its inverse. 
* **Examples of Isomorphisms and Isomorphic Spaces**:
* [more examples](https://en.wikibooks.org/wiki/Linear_Algebra/Definition_and_Examples_of_Isomorphisms)
* Example (1): (iso that sends linear combination vector to its coordinates and back)If V is a finite dimensional vector space over \\(\mathbb{F}\\) 
    * then every choice of a basis \\(\mathbb{B} = \\{ b\_{1},..,b\_{n} \\}\\) gives you an isomorphism, namely: \\( [-]\_{\mathbb{B}} : V \mapsto \mathbb{F} ^{n}\\) between V and coordinate n space
    * so what does this map do?
    * \\([-]\_{\mathbb{B}}\\) assigns to each \\( v \in V\\) _the column vector of its coordinates_ in the basis \\(\mathbb{B}\\)
    * what this means is that each \\( v \in V\\) has a unique representation as \\(v = \sum\_{i=1}^{n} x\_{i}b\_{i}\\) with \\( (x\_{1},..,x\_{n}) \in V, b\_{1}...b\_{n} \in \mathbb{B} \\) (in the vector space V!!)
    * this vector gets sent to a column vector of the coordinates from the field. \\( [v]\_{B} := (x\_{1}...x\_{n})^{T} \\)
    * conversely, the inverse map \\([-]^{-1} : \mathbb{F} ^{n} \mapsto V\\) is also easy to write explicitly. Sends a column vector of coordinates from the scalar field to the linear combination representation of the vector v. 
* _Notation:_ we can write and see the linear combination \\(\sum\_{i}^{n} x\_{i}b\_{i}\\) as a formal matrix product \\(\mathbb{B} \cdot x\\) where
    - \\(\mathbb{B} = (b\_{1},...,b\_{n})\\) == the row vector of vectors (in the basis)
    - \\(x = (x\_{1},...,x\_{n})^{t}\\) is the column vector of coordinates in \\(\mathbb{F} ^{n}\\)
    - with this new notation, new view, we can look at the inverse map of \\([-]\_{B}: V \mapsto F^{n}\\) as the "matrix multiplication by B map": \\(B \cdot (-) : \mathbb{F} ^{n} \mapsto V\\)
* _further notes on example 1_: note that the isomorphism [-] depends on your choice of a basis. 
    - different bases will give rise to different isomophism. 
    - another way to descrube \\([-]\_{\mathbb{B}} : V \mapsto \mathbb{F} ^{n}\\) is to say that it is the unique linear map that sends the basis B of V to the standard basis \\(E = \\{e\_{1},...,e\_{n}\\} \\) of \\(\mathbb{F} ^{n}\\). 
        + so the mapping \\([-]\_{\mathbb{B}}\\) is the unique linear map for which \\( [b\_{i}]\_{\mathbb{B}} = e\_{i}\\) for i = 1,...,n
        + in vector notation : \\( [\mathbb{B}]\_{\mathbb{B}} = E \\)
* (2): Let V,W be vector spaces over \\(\mathbb{F}\\) with bases 
    - \\(E = \\{ e\_{1},...,e\_{n} \\} \subset V\\)
    - \\(F = \\{ f\_{1},...,f\_{n} \\} \subset W\\)
    - now given a linear map \\(T: V \mapsto W\\) let \\(A\_{T} \in Mat(mxn)(\mathbb{F})\\) be its matrix (T's matrix) in the bases E and F. 
    - Then the assignment \\(A\_{(-)}: L(V,W) \mapsto  Mat(mxn)(\mathbb{F}) :: T \mapsto A\_{T}\\) is a linear map. 
        + this follows from part (1) of the first theorem above. 
    - And \\(A\_{(-)}\\) is also an isomorphism. (it's bijective)
        * _check_: 
            * first, by definition, \\( A\_{T} \\) is the unique matrix such that \\( T(E) = T(e\_{1} + .. + T(e\_{n})) = F \cdot A\_{T} \\) 
                * QUESTION: why is this true? are \\(T(e\_{1}, ...)\\) are column vectors?
            * This fact guides us on how to compute values of T in terms of \\(A\_{T}\\): (Here's how):
                - if \\(v \in V\\) and we have \\(x \in F^{n}\\) := vector of coordinates of v in the basis E, 
                - then \\(v = Ex\\)
                - by linearity of T we have: 
                - \\( T(v) = T(Ex) = T(E) \cdot x = F \cot A\_{T}x\\)
                - recalling that \\(x = [v]\_{E} \in F^{n}\\) is the vector of the cordinates of v in the basis E, we now have a formula for T in terms of A\_{T}, its matrix:
                    + \\(T(v) = F A\_{T}[v]\_{E}\\)
                - this derivation also gives us the inverse of the map \\(A\_{(-)} : T \mapsto A\_{T}\\),
                    + \\(A\_{(-)} ^{-1} : Mat(mxn)(\mathbb{F}) \mapsto L(V,W) :: A \mapsto FA[-]\_{\mathbb{E}}\\) 
                    + QUESTION: so what does this actually look like? need examples
* Example (3): variant of example 1 (T that sends bases to bases is an iso)
* Let V,W be vector spaces over \\(\mathbb{F}\\) with the bases:
    + \\(E = \\{ e\_{1},...,e\_{n} \\} \subset V \\) 
    + \\(F = \\{ f\_{1},...,f\_{n} \\} \subset W \\)
* Then the unique linear map \\(T: V \mapsto W\\) which sends the basis E to the basis F is an isomorphism!
* _Proof_: Let T be as defined above with bases E and F, for which \\(T(E) = F\\)
* and let \\(S: W \mapsto V\\) be another such that \\(S(F) = E\\)
* both T and S exist and are unique thanks to the theorem we proved above and lectures 7,8. 
* Then \\(S \circ T : V \mapsto V\\) is a linear map such that 
    - \\(S \circ T(E) = S(T(E)) = S(F) = E\\)
* But we already have such a map that maps from V to V and sends E to E. It's the identity map! \\(id\_{v}\\)
* by the uniqueness part of the above theorem and the last lecture, we get that this \\(S \circ T = id\_{v}\\), they are one and the same. 
* the same argument applies to \\(T \circ S\\) on F, it equals \\(id\_{w}\\) 
* **Corollary**: Let V,W be finite dimensional vector spaces over F. Then 
    - (V and W are isomorphic) iff (dim V = dim W) _nice_
    - _proof_: => follows from isomorphism. look: 
        + If \\(T: V \mapsto W\\) is an isomorphism then for any basis B of V the vectors \\(T(B) \subset W\\) form the basis of W (important point!)
        + We can check this directly: 
            * if \\(w \in W\\) then we can consider \\(v = T^{-1}(w) \in V\\)
            * by definition, \\(T(v) = T(T^{-1})(w) = w\\). 
            * but, \\(v \in (V = span(B))\\) 
            * So by the linearity of T we have
                - \\(w = (T(v) \in span(T(B)))\\) QUESTION: is spanT(B) = W? oh wait thats the conclusion we are trying to reach. 
            * This shows that T(B) is a generating set of W
            * But if \\(B = \\{ b\_{1}...b\_{n} \\} \\) and \\( \\{c\_{1},..,c\_{n}\\} \\) are scalars in the field such that the linear combination of these with the bases vectors is in W and equals 0, or \\( c\_{1}T(b\_{1})+...+c\_{n}T(b\_{n}) = \vec{0} \in W\\)
            * then we can apply \\(T^{-1}\\) to both sides and get: 
            * \\( T^{-1}(\vec{0}) = T^{-1}(\sum\_{i=1}^{n} c\_{i}T(b\_{i})) \\)
            * = \\( \sum\_{i=1}^{n} c\_{i}T^{-1}T(b\_{i}) \\) (linearity of T)
            * = \\( \sum\_{i=1}^{n}c\_{i}b\_{i} \\) 
            * since B is a basis, this implies that \\(c\_{1}=...=c\_{n} = 0\\) and hence that T(B) is a linearly independent set of W
            * Since it is both spanning and linearly in dependent, 
            * T(B) is a basis of W and thus...
            * dim V = number of vectors in B = number of vectors in T(B) = dim W
        - (<=): WTS: dim V = dim W => V and W and isomorphic 
            + supposed dim V = dim W = n (so there's n vectors in the basis)
            + and let 
                - \\( E = {\\ e\_{1},..,e\_{n} }\\ \subset V\\)
                - \\( F = {\\ f\_{1},..,f\_{n} }\\ \subset W\\) be bases
            + Then by the previous claim(what is it!) the unique linear map \\(T: V ]mapsto W\\) such that T(E) = F (sends one basis to another) is an isomorphism. nice. 
* _notation_: two isomorphic spaces over the same field:= \\(V \simeq W\\)
* _caution_: the previous claim just says if dim V = dim W there exists an isomorphism between them. It is not the case that any linear map between the two spaces is an isomorphism. 
    - ex: \\(0 : v \mapsto W\\) is a linear map between the two that is not an isomorphism. Not bijective when dim V is greater than 0. 
    - the size of the Kernel helps tell if a mapping is an iso. 
*  **Kernel** (definition) : the subspace of the domain of a linear mapping \\(T : v \mapsto W\\) between two vector spaces
    -  ker(T) = \\( \\{ v \in V s.t. T(v) = 0 \\} \\)
* **Theorem** ( equal dimensions and kernel has zero vector implies iso ):
    - given a linear map T between V and W, F vector spaces, that have the same finite dimension, 
    - T is an iso iff <=> Ker(T) = {\\( \vec{0} \\)}
    - _proof_: 
        + S1: ( => ) T is an isomorphism / bijective, so from the "onto" criteria we have 
            * there exists (for sure) a vector v in V that maps to 0 in W. This is because W needs to have the 0 vector to be a vector space. 
            * there exists \\(v \in V\\) s.t. \\(T(v) = \vec{0} \in W\\)
        + S2: But T is linear, so \\(T(0) = T(0v) = 0 T(v) = 0\\)
        + S3: This shows that \\(\vec{0} \in V\\) is the uniqe vector in V that is mapped to 0 in W by T. 
            * This proves that \\(Ker(T) = 0\\) 
            * -(QUESTION: does this mean that the solution set has only the trivial solutin in an isomorphism?) - the id matrix is an iso, and when set = 0 its only solution is 0, think about this, so it seems to be the case, at least for the id matrix
        + S1: (<=) "kernel only contains 0 implies T is an iso" (harder!)
            * suppose \\(Ker(T) = \\{\vec{0}\\}\\)
            * Let \\(\\{ e\_{1},...,e\_{n} \\}\\) be a basis of V
            * S2: so the vectors \\(\\{ f\_{1} = T(e\_{1} ... f\_{n} = T(e\_{n})) \\} \in W\\) are linearly independent. (how do we know this?)
                - well, if we have scalars \\(a\_{n} \in \mathbb{F}\\) s.t. \\(a\_{1}f\_{1},...,a\_{n}f\_{n} = \vec{0} \in W\\) then we get
                - \\(\vec{0} = \sum\_{i=1}^{n}a\_{i}f\_{i}\\)
                - \\(= \sum\_{i=1}^{n}a\_{i}T(e\_{i}) \\)
                - = \\( \sum\_{i=1}^{n}T(a\_{i}e\_{i})\\) (linearity of T)
                - = \\( T(\sum\_{a=1}^{n}a\_{i}e\_{i}) \\) = \\(\vec{0}\\), (linearity of T)
            * S3: but since we have that \\(Ker(T) = \\{\vec{0}\\}\\), 
                - \\(Ker(T) = \\{ \sum\_{a=1}^{n}a\_{i}e\_{i} = \vec{0}\\}\\), and kernel is a subspace of the domain T, V, so \\(\sum\_{a=1}^{n}a\_{i}e\_{i} \in V \\)
            * S4: since {e}'s were a basis of V, we have \\(a\_{2} = ...= a\_{n} = 0\\) 
            * S5: we have now shows that S2 is true. 
                - This face, that the {f} are linearly independent + dim V = dim W = n (bases of V and W have the same number of vectors) shows that \\(f\_{1},...,f\_{n}\\) is a basis of W. 
            * S6: Since T sends the basis of V to the basis of W, it is an isomorphism. 
            * QED
* **Image of T**(definition): For a linear mapping \\(T: V \mapsto W\\),
    - im(T) = \\( \\{w \in W : \exists v \in V s.t. T(v) = w\\} \\)
    - EXERCISE: check that im(T) is always a subspace of W.   
* **Theorem**: V,W, F-vector spaces with equal finite dimension. dim V = dim W < \\(\infty\\). Then a linear map \\(T: V \mapsto W\\) is an iso <=> (iff) im(T) = W 
* QUESTION: is this any different than the def of iso? being onto => range(T) = W? oh i see this only works for the first direction. 
    * _proof_ : ( => )If T is an isomorphism, then 
        + T is bijective (in particular onto/surjective:). Thus image(T) = W.
    + (<=) "if im(T) = W then T is an isomorphism."
    + Suppose image(T) = W, 
    + let \\(\\{ f\_{1},...,f\_{n}\\}\\) is a basis of W. 
    + since im(T) = W we can find vectors \\(e\_{1},..,e\_{n} \in V\\) such that \\(T(e\_{i}= f\_{i})\\) , \\(i = 1,...,n\\)
    + Then the vectors \\(\\{e\_{1},...,e\_{n}\\}\\) are linerly independent in V. how so? well :
        - suppose we have scalars \\(a_{1},...,a_{n} \in K\\) 
        - so that \\( a_{1}e_{1} + .. + a_{n}e_{n} = \vec{0} \\)
        - then, \\( T(\sum_{i=1}^{n} a_{i}e_{i}) = T(\vec{0})\\)
        - \\( \sum_{i=1}^{n} a_{i}T(e_{i}) = T(\vec{0})\\) 
        - \\( \sum_{i=1}^{n} a_{i}f_{i} = T(\vec{0})\\)
        - since \\( \\{ f_{1},...,f_{n} \\} \\) is a basis in V, then we can conclude that the scalars \\( a_{1}=...=a_{n} = 0\\)
        - thus, \\( \\{e_{1},...,e_{n}\\} \\) is linearly independent. 
    + Since we have dim V = dim W = n, this implies that \\( \\{ e_{1},...,e_{n} \\} \\) is a basis of V
    + and because we have a linear mapping T that sends a basis to another it is an isomorphism. 
    + QED
* The argument we used to prove the previous two theorems can be refined to show that Ker(T) and im(T) always have complementary dimensions.    

* **Theorem**: (Rank-Nullity?) Let V,W be F-vector spaces. \\( T:V \mapsto W\\) is a linear map. Dimension V < infinity (it's finite). _note that this only talks about the dimentison of the domain_ Then:
    - (a): dim Ker(T), dim Im(T) finite. 
    - (b): dim Ker(T), dim Im(T) = dim V
* _proof_: for part (a), note that \\(Ker(T) \subset V\\) is a subspace of V and by the monotonicity of dimension of spaces we get that 
    - \\( dim(Ker(T) \leq dim(V) \leq \infty)\\) (both finite, dim ker is less)
* Also if \\( \\{ e\_{1},...,e\_{n} \\} \\) is a basis of V
    - then V = span\\(\\{e\_{i}\\}\\) 
* so then the image of T, which is all of T applied to every vector in V, is the span of T applied to every basis vector, by linearity of T:
    - \\(Im(T) = T(V) = span(T(e\_{1}),...,T(e\_{n})) \\) 
* from this fact it follows that \\(im(T)\\) is spanned by finitely many vectors, and so the dim \\(im(T) \leq \infty\\)
* For part (b) : 
    - choose a basis of the Ker(T), \\(\\{ e\_{1},...,e\_{k} \\}\\).  
    - now choose a completion to a basis of V to a basis of V : \\( \\{ e\_{1},...,e\_{k},e\_{k+1},...,e\_{n} \\} \\)
    - QUESTION: get an explicit example of doing this!
    - Then we get that \\(T(e\_{1}),...,T(e\_{n})\\) span im(T)! QUESTION: why? from part a!
    - But \\(T(e\_{1}) = ...= T(e\_{k}) = 0\\), from the basis of Ker(T)
    - so we get that really, \\(T(e\_{k+1}), ..., T(e\_{n})\\) will span im(T)
    - but the vectors \\(T(e\_{k+1}), ... , T(e\_{n})\\) will be linearly independent in \\(im(T) \subset W\\) (_how so_)? :
        + well, if we have \\(a\_{k+1},...,a\_{n} \in \mathbb{F}\\) s.t. 
        + \\(\sum\_{i=k+1}^{n} a\_{i}T(e\_{i}) = \vec{0}\\) 
        + then \\( T(\sum\_{i = k+1}^{n}a\_{i}e\_{i}) = \vec{0}\\) (by linearity of T)
        + and so \\( \sum\_{i = k+1}^{n}a\_{i}e\_{i} \in Ker(T) \\)
            * because its the argument in T(0) = 0, do you see it?
        + so \\(\sum\_{i = k+1}^{n}a\_{i}e\_{i} = \sum \_{j=1}^{k}b\_{j}e\_{j}\\)
        + since\\(\\{e\_{1},...,e\_{n}\\}\\) is a basis of V it follows that 
            * all coefficients must be equal to zero, \\(a\_{k+1},...,a\_{n} = 0\\), (which implies linear independence?)
        + Thus \\(T(e\_{k+1}),...,T(e\_{n})\\) is a basis of im(T). 
        + This shows that dim im(T) = \\(n-k\\) = dim V - dim ker(T). 
        + QED

**Dual Spaces and isomorphisms:**   

* We can use the criteria for isomorphic spaces to uncover more truths about the relationship between \\(V \\) and \\(V^{v}\\)  
* **Claim**: if V is a finite dimensional vector space over F, 
    - then (=>) \\(dimV^{v} = dim V\\)
* _proof_: Let \\(E = \\{e\_{1},...,e\_{n}\\} \\) be a basis of V. 
* Then for all \\(i\\) consider this unique linear operator / function:
    - \\({e\_{i}}^{v}: V \mapsto \mathbb{F}\\) (from the vector space to the field) s.t.
    - \\({e\_{i}}^{v}{e\_{j}}\\) = 
    $$ \begin{cases} 
    0 & j \neq 1 \\\
    1 & j = i 
    \end{cases} $$
* we claim that the functions: \\(e\_{1}^{v},...,e\_{n}^{v} \in V^{v}\\) form a basis of the dual space \\(V^{v}\\) of \\(V\\) _how so you ask!_
* well, let \\(f \in V^{v}\\) be any element in the dual space, so it is a linear functional that sends vectors in v to the field. 
* the function \\(f: V \mapsto \mathbb{F}\\) is unqiely determined by its values on the spanning set E of V. 
    - QUESTION: so the lemma works for spanning sets, not just bases?????
* these values are: \\( f(e\_{1}),...,f(e\_{n}) \in \mathbb{F} \\). (recall they send vectors in v, in this case e, to a scalar in the field)
* consider the linear function: 
    - g = \\( f(e\_{1})e\_{1}^{v},...,f(e\_{n})e\_{n}^{v}\\) 
    - \\(g(e\_{j}) = f(e\_{1})e\_{1}^{v}(e\_{j}) + ... + f(e\_{n})e\_{n}^{v}(e\_{j})\\) = \\(f(e\_{j})\\), because it becomes \\( f(1*e\_{j})\\) for all j. 
    - Thus, \\(f : V \mapsto F\\) and \\(g : V \mapsto F\\), take the same values on the basis \\(e\_{1},...,e\_{n}\\)
    - since linear transformations are characterized by what they do to a generating set, then \\(f = g\\) (remeber E is a spanning set of V)
* This shows that \\(V^{v} =\\) span\\( (e\_{1}^{v}, ..., e\_{n}^{v}) \\)
* Next, let scalars \\(c\_{1},...,c\_{n}\\) are such that \\(c\_{1}e\_{1}^{v},...,c\_{n}e\_{n}^{v} = 0 \in V^{v}\\)
* so this \\(c\_{1}e\_{1}^{v},...,c\_{n}e\_{n}^{v} : V \mapsto F\\) is the zero function. 
* Evaluate the function on \\( (e\_{j})\\), gives \\( c\_{1}e\_{1}^{v}(e\_{j}),...,c\_{n}e\_{n}^{v}(e\_{j}) \\)
* but value of zero mapping on any vector just gives you zero back, so 
    - \\( c\_{1} = ... = c\_{n} =0\\)
* Hence, \\( \\{ e\_{1}^{v},...,e\_{n}^{v} \\}\\) is linearly independent, thus they form a basis, since they are also spanning, of the dual space. 
* Hence, \\(dim V^{v} = n = dim V\\)  
* **dual basis** (def) : \\(E^{v}= e\_{1}^{v},...,e\_{n}^{v} \\), as defined above, is the dual bases of E (of V)
* _note_: dual spaces allow us (only when V is finite dimensional!) to define an isomorphism \\(T: V \mapsto V^{v}\\). 
    - T is defined as the unique linear map sending the basis E of V to the dual basis \\(E^{v} of V^{v}\\).
* also works in opposite direction ... 
* **Claim**: V is a finite dim vector space over F, let
    - \\( F = \\{ f\_{1},...,f\_{n} \\} \\) be a basis of \\(V^{v}\\)
    - Then there exists a unique basis \\(E = \\{ e\_{1},...,e\_{n} \\}\\) of V s.t.\\(E^{v} = F\\) 
    - (a basis for the dual space can always constructed from a basis for the space, so we can find the "origin" basis for any basis in \\(V^{v}\\))
    - _proof_: 
        + note that each vector \\( x \in V \\) defines a linear function 
            * \\(ev\_{x}: V^{v} \mapsto \mathbb{F}\\) alt: \\(f \mapsto f(x)\\) (the evaluation map! kirillov was talking about this!)
        + This gives a map: 
            * \\(ev : V \mapsto V^{vv}\\) alt: \\( x \mapsto ev\_{x} \\)
        * this map is linear:
            - if \\(x\_{1},x\_{2} \in V\\), \\(a\_{1}, a\_{2} \in F\\)
            - then for every \\( f \in V^{v}\\) we have: 
            - \\(ev\_{a\_{1}x\_{1} + a\_{2}x\_{2}}(f) =V s\mapsto F f(a\_{1}x\_{1}+a\_{2}x\_{2}) = a\_{1}f(x\_{1}) + a\_{2}f(x\_{2}) = a\_{1}ev\_{x1}(f) + a\_{2}ev\_{x2}(f)\\)
        * By the previous claim on \\(dim V^{vv} = dim V^{v} = n\\),
        * so \\(ev: V \mapsto V^{vv}\\) is a linear map between vector spaces of the same dimension. 
        * _now a brief interruption for a lemma we need to prove to finish proving this claim_:
    * **Lemma:** (the evaluation map is an isomorphism)
        + For a finite dimensional vector space V over F the map \\( ev: V \mapsto V^{vv} \\) is an isomorphism. (a natural one!)
        + _proof_: Let \\(\\{ b\_{1},..,b\_{n} \\}\\) be a basis of \\(V\\). 
            * let \\(\\{b\_{1}^{v},...,b\_{n}^{v}\\}\\) be a basis \\(V^{v}\\). 
            * let \\( \\{ b\_{1}^{vv},...,b\_{n}^{vv} \\} \subset V^{vv}\\) be a basis dual to the dual basis. 
            * Compute \\(ev\_{b\_{i}}(b\_{j}^{v})\\). 
            * By definition, we have 
            * \\( ev\_{b\_{i}}(b\_{j}^{v}) = b\_{j}^{v}(b\_{i}) =  \\)
            $$ \begin{cases} 
            0 & j \neq 1 \\\
            1 & j = i 
            \end{cases} $$
            * Thus, we can see that \\( ev\_{bi} \\) and \\( b^{vv} \\) take on the same values on the dual basis \\( \\{ b\_{1}^{v},...,b\_{n}^{v} \\} \\) 
            * since every linear map,function is uniquely detemined by its values on a spanning set, it follows that:
                - \\( ev\_{bi} = b\_{i}^{vv}\\) for i =1,..,n
            * Conclusion: \\(ev\\) sends a basis of V toa basis of \\(V^{vv}\\) and so it is an isomorphism. 
    * back to the proof.... 
    * Now let us start wuth the basis
        - \\( F = \\{ f\_{1},...,f\_{n}\\} \\) of \\(V^{v}\\)
    * Let \\(F^{v} = \\{ f\_{1}^{v},...,f\_{n}^{v} \\}\\) be the dual basis of \\(v^{vv}\\)
    * Since we have \\(ev: V \mapsto V^{vv}\\) is an isomorphism (proved above)
    * for each \\(i = 1,...,n\\) we have a unique vector \\(e\_{i} \in V\\) s.t.
        - \\(ev\_{e\_{i}} = f\_{i}^{v}\\) (because an iso sends a basis to a basis?)
    * But then, \\(f\_{i}(e\_{j}) = ev\_{ej}(f\_{i}) = f\_{j}^{v}(f\_{i}) = \begin{cases} 
            0 & j \neq 1 \\\
            1 & j = i 
            \end{cases} \\)
    * Now consider the collection of vectors \\( \\{ e\_{1},...,e\_{n} \\} \subset V\\)
        - It is a basis of V since it is the image of the basis of the double dual: \\(\\{ f\_{1}^{v},..,f\_{n}^{v} \\}\\) of \\(V^{vv}\\) under the isomorphism: \\(ev^{-1}: V^{vv} \mapsto V\\)
    * The formula \\( f\_{i}(e\_{j}) = \begin{cases} 
            0 & j \neq 1 \\\
            1 & j = i 
            \end{cases} \\) implies that ..
    * \\(f\_{1},..,f\_{n}\\) is the dual basis of \\( e\_{1},...,e\_{n} \\) and this proves our claim. 
    * QED   

* _Remark_: If \\(V\\) is an n-dimensional space over F, we now know that 
    - \\(V \simeq V^{v}\\) 
    - \\(V \simeq V^{vv}\\)
* However, the first one is a isomorphism that depends on the choice of the basis, the second is a _canonical_ isomorphism.
* To construct the first, we need to find a basis of V. 
* To construct the second, there is a canonical isomorphism \\(ev: V \mapsto V^{vv}\\) which is deinfed only in terms of V and doesn't depend on a basis. 
**Exercises:**
* (Duality for Linear Maps): Let U, V, W be vector spaces over F
    - (1) Show that if \\(T: V \mapsto W\\) is a linear map, then the map \\(T^{v}: W^{v} \mapsto V^{v}\\) defined by \\(T^{v}(f) = f \circ T\\), for any linear function \\(f: W \mapsto F\\) is also linear. 
    - (2) Show that if \\(S: U \mapsto V\\), \\(T: V \mapsto W\\) are linear maps, then \\( (T \circ S)^{v}: S^{v} \circ T^{v}\\)
    - (3) Suppose that V,W are finite dimensional and let 
        + \\( E = \\{ e\_{1},...,e\_{n} \\} \subset V \\)
        + \\( F = \\{ f\_{1},...,f\_{n} \\} \subset W \\) 
    - be bases of V and W. 
    - Let \\(S \in Mat(mxn)(F)\\) be the matrix of T in the bases \\(E \subset V\\) and \\( F \subset W \\). 
    - Show that the matrix of \\(T^{v}: W^{v} \mapsto V^{v}\\) in the dual bases \\( F^{v} \subset W^{v} \\) and \\( E^{v} \subset V^{v} \\) is the matrix \\( A^{T} \in Mat(nxm)(F) \\)
    - (4) Prove that if \\(A \in Mat(nxm)(F)\\) and \\(B \in Mat(mxk)(F)\\)
        + then \\((AB)^{T} = B^{T}A^{T}\\). 




### Lectures 12-13

**Traces**  
- It is useful to have numerical invariants measuring the complexity of linear maps  
- we already have some discrete (= integer invariants)  
    + for every linear map \\( T: V \mapsto W \\)  
    + we have two integers cpaturing information about T (transformation)  
        + **nullity of T:** = dim Kernel(T) = dim Nullspace(T) = dim of the solution set to \\(Ax=0\\)  
            + **Nullspace (T)**: set of all n-dimensional column vectors such that \\(Ax=0\\), the solution set of the homog linear system.  
                * **_Theorem_**: The nullspace N(A) is a subspace of the vector space \\(\mathbb{R^{n}}\\)  
                * proof: WTS: N(A) is nonempty, closed under addition, closed under scalar multiplication:  
                * S1: the trivial solution is always in N(A)- so it's nonempty. \\(\vec{x}=\vec{0}\\)  
                * S2: WTS: \\( x,y \in N(A) => x+y \in N(A)\\)  
                    * Well, \\( Ax = 0, Ay = 0, A(x+y) = A(x) + A(y) = 0 + 0 = 0 \\)  
                * S3: \\(c \in \mathbb{R}, x \in N(A) => cx \in N(A)\\)  
                    * Well, \\(A(cx)=c*A(x) = c * 0 = 0\\)
                * QED  
        + **rank of T**: dim image(T) = ...QUESTION: any other defs? yes, see lec 14 for longer discussion 

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
                        * S2: Then \\( T =  \sum_{i,j=1}^{n} a_{ij} * s_({{b_{ji}}^{v}, b_{i}}) \\) 
                            * for every \\( k = 1,....,n \\), we have
                            * \\( T(b_{k}) =  \sum_{i=1}^{n} a_{ik} * b_{i} \\)
                            * and we also have:
                            * \\( (\sum_{ij} a_{ij}*s_{{b_{ji}}^{v}b_{i}} )(b_{k}) \\) 
                            * \\( =  {\sum_{ij}} a_{ij}*s_{{b_{ji}}^{v}b_{i}}  (b_{k}) \\)
                            * \\( =  \sum_{ij} a_{ij} {b_{j}}^{v}(b_{k})b_{i} \\)
                            * \\( = \sum_{i=1}^{n} a_{ik} * b_{i} \\)
                        * S3: Thus, \\( T = \sum_{ij}a_{ij}s_{{b_{j}}^{v}, b_{i}} \\)
                        * This representation is unique since the matrix of T in the basis \\( \mathbb{B} \\) is uniquely determined by T and \\( \mathbb{B} \\) 
                            *("linear extension theorem" - a linear transformation is uniqely determined by what it does to a basis.) ?
                        * by the characterization of linear maps (the one descirbed above?) we then have a unique linear function, trace:
                            - \\( tr: L(V,V) \mapsto \mathbb{F} \\)
                            - ENDED PG 7 REVISIT AFTER LEC 9-11

### Lecture 14

**Row Reduction:**

* Simplifying Linear Systems
* Row Reduction and Echelon Forms
* Solving Systems with Row Reduction
* Corollaries
* **Solving a Linear System**  
* using row and column operations we can convert every linear system into a system in which all variables separate
    -  _row operation_: 
    -  _column operation_:
* \\(Ax=b\\) where 
    - \\(A \in Math(mxn)(F)\\) is a given coefficient matrix. 
    - \\(b \in F^{m}\\) is a given vector of right hand sides. 
    - \\(x \in F^{n}\\) is an unknown vector. 
* we proved (QUESTION: where b?) that we can find invertible matrices
    - \\( R \in Mat(mxm)(F) \\)  - number of eqs
    - \\( C \in Mat(nxn)(F) \\) - number of unkowns
    - such that after performing on A the row operation corresponding to R, and then the column operation corresponding to C we get the simplest possible matrix:
    - \\( \tilde{A} =  RAC =\\) ![block matrix](delpinolisette.github.io/img/blockmat1.png)
        + where r = rank of matrix (see discussion on rank below!!)
    - Using R and C we can simplify the system Ax=b. 
    - Left multiplying (Ax=b) by R gives an equivalient system 
        + \\(RAx = Rb <=> RACC^{-1}=Rb\\)
            * so the id matrix is written in the form \\(CC^{-1}\\) which doesnt change anything, but we have our simple matrix RAC to work with. 
        + given the notation: 
            * \\(\tilde{A} = RAC \in Mat(mxn)F\\)
            * \\(\tilde{b} = Rb \in (F^{m})\\)
            * \\(\tilde{x} = C^{-1}x \in F^{n} \\) = column vector with n entries. 
        + write system as \\(\tilde{A}\tilde{x}=\tilde{b}\\), but since we used only invertible operations to get this new system, we can answer quesetions about the old system with this one. 
        + in terms of the new variables \\(\tilde{x} = (\tilde{x}\_{1},...,\tilde{x}\_{n})^{T}\\) = \\(C^{-1}x\\)
        + so it becomes : 
        \\[ \tilde{x}\_{1} = \tilde{b}\_{1} \\\
        ... \\\
        \tilde{x}\_{r} = \tilde{b}\_{r} \\\
        0 = \tilde{b}\_{r+1}\\\
        ...\\\
        0 = \tilde{b}\_{m}
        \\]
        + note that it is m equations. we got this very simple system we alluded to using the block matrix previously. 
        + So we conclude that we can get the solutions of Ax=b through \\(\tilde{A}\tilde{x}=\tilde{b}\\)
            - _proof_: 
            - S1: The tilde system and Ax = b are both consistent iff \\(\tilde{b}\_{r+1}= ... = \tilde{b}\_{m}=0\\)
            - S2: If \\( \tilde{b}\_{r+1}=...=\tilde{b}\_{m}=0\\) then the solutions of \\( \tilde{A}\tilde{x}=\tilde{b} \\) are vectors of the form: \\[ \tilde{b}\_{1} \\\
             ... \\\
            \tilde{b}\_{r} \\\
            \tilde{x}\_{r+1} \\\
            ... \\\
            \tilde{x}\_{n}  \\]
            - with \\( \tilde{x}\_{r+1},...,\tilde{x}\_{n} \in \mathbb{F} \\) being free variables
            - S3: If \\(\tilde{b}\_{r+1}= ... =\tilde{b}\_{m}=0\\) then the solutions of \\(Ax=b\\) are of the form: x = 
            \\[ \tilde{b}\_{1} \\\
             ... \\\
            \tilde{b}\_{r} \\\
            \tilde{x}\_{r+1} \\\
            ... \\\
            \tilde{x}\_{n}  \\]
            - with \\( \tilde{x}\_{r+1},...,\tilde{x}\_{n} \in \mathbb{F} \\) being free variables.\, and the whole column vector of solutions is multiplied by \\(C\\). (why? because solutions \\(\tilde{x} were our solutions x multiplied by C^{-1}\\) !)
        + but this method is not constructive, we had to pick bases in \\(F^{n}, F^{m}\\) to fit with A. We had actually construct R and C by choosing these bases, adopted to map T, or matrix of map A. Row reduction algorithm solves the issue. 
            + the algo simplifies the system systematically, uses only row ops, done in simple steps, and allows us to get close enough to solve the system.  
            + also they solve the systm in _finitely_ many steps!
* **Elementary Row Operations**:  
    * note that Ax=b is the matrix equation for our equation \\(F(v) = b\\), once we choose a basis in the vector space V. 
    * If A is (mxn), the augmented matrix is (m x n+1). 
    * Elemtary Row Operations are just left multiplication by a specific elementary matrix. We called it R above. 
        - they just replace rows in the matrix with linear combinations of rows, in an invertible way (you can always work backwards).
        - The important question is - why is it that these row operatiors don't change the solution set?? Because they are all invertible, reversible. 
        - the inverses of ERO's are just ERO's of the same type. 
        - ![ERO's and inverses:](delpinolisette.github.io/img/ERO.png)
        - What are these special elementary matrices? Well, they are just obtained by doing the corresponding row operation to the identity matrix. 
            + Row operation 1: switch two rows: ![type 1](delpinolisette.github.io/img/type1.png)
            + Row operation 2: multiply a row by a scalar multiple: ![type 2](delpinolisette.github.io/img/type2.png)
            + Row operation 2: add a scalar multiple of a row to another row: ![type 3](delpinolisette.github.io/img/type3.png)
        - another way of showing that a row operation does not change the solution set of a system, matrix equation style :) E is the elementary matrix representating a row operation.
            + \\(Ax=b\\)
            + \\(EAx = Eb\\) (implies any solution of this equation is a solution of the previous, because we multiplied them all by the same matrix)
            + \\(E^{-1}EAx = E^{-1}Eb\\)
            + \\(Ax = b\\), QED. 
        - **claim**: the composition of row operations is also a row operation! 
            + _proof_: if \\(p\_{1},...,p\_{s}: \mathbb{F}^{n} \mapsto \mathbb{F}^{n}\\) 
* **Rank of a Matrix** : 
    + recall that left multiplication by an mxn matrix \\(A\\) defines a linear map: 
        - \\(T : \mathbb{F}^{n} \mapsto \mathbb{F}^{m}\\) :: \\(v \mapsto Av\\)
    + the rank of the matrix A is then the rank of T. 
        - rank(T) = dimension of the subspace \\( im(T) \subset \mathbb{F}^{m}\\) of the codomain. 
    * **rank (A)** (def): rank (A) = rank(T) = dim im(T) = dim (column space of A) = maximal number of linearly independent vectors in col space A = max number of linearly independent columns of A. 
    * **im(T)** (def): im(T) = \\(y \in F^{m} : y = T(v) = Av\\) for some \\(v \in F^{n}\\) = span(columns of A) 
        -   (we show the last part now), that im(T) = span of columns of A.
        - now note that: 
        - \\(F^{n}\\), the domain of the linear map, which is a coordinate n space, is spanned by the vectors of the cardinal basis \\(e\_{1},...,e\_{n}\\) and therefore \\(im(T)\\) is spanned by the vectors \\(Ae\_{1},...,Ae\_{n} \in F^{m}\\), which as we now discuss are just the columns of A
            - we know that image of a linear map is gneerated by the image of the generators of the source space (QUESTION: - when did we discuss this?)
            - recall that each \\(e\_{i}\\) has a 1 in the ith spot, 0 everywhere else, so by definition of matrix multiplication (row by column), 
                + \\(Ae\_{i}\\) = i-th column of A. 
        - Thus, im(T) = span(columns of A)
    * 





### Extra notes/defs to categorize later   
**Dual Spaces and Dual Basis**  
* The dual space of V is the set of all linear functionals from V to \\(\mathbb{F}\\( , so : \\(V^{v} = T: V \mapsto \mathbb{F} \\( 
    - all such elements of dual space are linear functionals
- if dim(V) < \\( \infty\\) => \\( V \\) and \\( V^{v} \\) are isomorphic
    + to show this is true, show that they have the same dimension
    + another way to show the isomorphism is to use the dual basis
        * linear extension theorem: says if you know what T does on basis vectos, you know what T does on every vector:
            * Let \\(\mathbb{B} = \{ v_{1}....v_{n} \}\\(
            * enough to know what \\(f(v_{1}),.....,f(v_{n})\\( is 
            * usually hard to graphically represent linear transformations, but since the codoamin of all such linear functions are scalars, \\(f: V \mapsto \mathbb{F}\\(, you can draw a graph of your linear functionals (where your inputs end up.)
            


**Isomorphism**
* mapppings that are injective and surjective (1:1 and onto) 
* [watch this](https://www.youtube.com/watch?time_continue=6&v=-Iww3p1-_bA&feature=emb_logo)
* **How to check if a mapping is an isomorphism between two vector spaces:** 
    - a linear transformation \\(T: V \mapsto W\\) is one-to-one if:
        + \\(T\\) maps distinct vectors in V to distinct vectors in W
        + check if two distinct vectors in the domain give you two different vectors in the codomain when you apply the linear transformation to it.
    - it is onto if:
        * range(T) = W
        * so take any vector in W and you can find some vector in V that maps to it
