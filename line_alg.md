---
layout: default
---
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

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
    - (a): dim Ker(T), dim Im(T) = dim V
* _proof_: for part (a), note that \\(Ker(T) \subset V\\) is a subspace of V and by the monotonicity of dimension of spaces we get that 
    - \\( dim(Ker(T) \leq dim(V) \leq \infty)\\) (both finite, dim ker is less)
* Also if \\( \\{ e\_{1},...,e\_{n} \\} \\) is a basis of V
    - then V = span\\(\\{e\_{i}\\}\\) 
* so then the image of T, which is all of T applied to every vector in V, is the span of T applied to every basis vector, by linearity of T:
    - \\(Im(T) = T(V) = span(T(e\_{1}),...,T(e\_{n})) \\) 
* from this fact it follows that \\(im(T)\\) is spanned by finitely many vectors, and so the dim \\(im(T) \leq \infty\\). 
* For part (b) : 
    - choose a basis of the Ker(T), \\(\\{ e\_{1},...,e\_{k} \\}\\)
 
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
- if dim(V) < \\(\infty\\) => \\(V\\) and \\(V^{v}\\) are isomorphic
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
