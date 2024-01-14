---
layout: post 
title: Bases and Change of Bases
---

<!-- Post in progress...
Let's explore change of bases.  -->

The change of basis matrix comes into play when we wish to write vectors in terms of a new basis. 

Assume you some vector $v$ from a vector space which has a basis $B_1 = \{b_1, b_2, \dots, b_k\}$. 

So, you can write your vector $v$ as a linear combination of the basis with some scalars:

$v = \alpha_1b_1 + a_2b_2 + \dots + \alpha_kb_k$

Say you have another basis for the space, $B_2$. You can also write your vector in terms of the other basis, but you want a clear way to do this. Enter the change of basis matrix, which is **derived by looking at how we can rewrite elements of one basis as a linear combination of elements from the other basis**. 

The power of the matrix is that we can ignore the vector you wish to rewrite and instead derive a matrix that will work on vectors from your space. 

(To be continued)

## Definitions

### Orthonormal Basis:
The orthonormal basis definition :
it is a set of linearly independent vectors which span the space in question:
 $e_i \cdot e_i = 1$ and $e_i \cdot e_j$ = 0. 

thus, the standard basis in $\mathbb{R^3}$ is an orthonormal basis (0s everywhere except for a 1 in the ith coordinate place)

<!-- Question : WHY are there truly infinite bases for $\mathbb{R^3}$? -->