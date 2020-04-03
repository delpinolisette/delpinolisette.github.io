---
layout: default
---
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

Section 2.2
Diffie Hellman introduces public key cryptosystems and therefore:
* one-way function: 
    * an invertible function that is easy to compute but whose inverse is difficult to compute
    * meaning of "difficult to compute": if any algorithm tries to compute the inverse in a reasonable amount of time, it will fail - (the age of the universe is an example of an unreasonable time). 
 
* trapdoor information
    * a peice of trapdoor info is auxiliary info that lets you compute the inverse easily (Public key cryptsystems are built using one way functions that have a trapdoor) 

* Public key cryptosystem = asymmetric cryptosystem
    * consists of: 
    * a private key $$k_{priv}$$
        - sometimes called "trapdoor information", without it very hard to compute inverse to $$e_{k_{pub}}$$
    * a public key $$k_{pub}$$
        * often created by applying a key creation algorithm to $$k_{priv}$$ 
   *  for every pair ($$k_{priv}, k_{pub}$$) there exists a 
       -  $$e_{k_{pub}}$$: encryption algorithm
           +  is public knowledge and easy to compute
       -  $$d_{k_{priv}}$$: decryption algorithm
           +  easily computabe by someone who has private key $k_{priv}$
           +  very difficult to compute for someone who only knows public key (that's the point!)
* actually very hard to prove whether true one way functions exist - we rely on the assumption that these problems are difficult (see P vs. NP unsolved problem)

===============================================================================

## The Discrete Logarithm Problem:
* first construction is based on the DLP (Discrete Logarithm Problem) in $$\mathbb{F}_{p}$$ 
    * (the finite field with p elements, where p is prime!)

first some definitions and an important theorem:

###Ring of Integers Mod m
*  :=   $$\mathbb{Z}/m\mathbb{Z}$$={$$0,1,2,......,m-1$$}
    * Notice $$\mathbb{Z}/m\mathbb{Z}$$ is the quotient ring of $$\mathbb{Z}$$ by the _principal ideal_ $$/m\mathbb{Z}$$
    * then $$0,1,2,......,m-1$$ are _coset representatives_ for the congruence classes that make up the elements of $$\mathbb{Z}/m\mathbb{Z}$$

###Set of all units
* numbers that have inverses modulo m ($$a$$ has inverse mod $$m$$ iff gcd(a,m)=1) are units. 
    * EXERCISE: Prove that the inverse of a mod m exists iff gcd(a,m) = 1
    * 

###Primitive Root Theorem
* Let p be prime. 
* Then there is an element $$g \in \mathbb{F}_{p}^{*}$$
    - what is the difference between $$\mathbb{F}_{p}$$ and $$\mathbb{F}_{p}^{*}$$? 
        - 

 
 