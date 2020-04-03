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
        - sometimes called "trapdoor information", without it very hard to compute inverse to $e_{k_{pub}}$
    * a public key $$k_{pub}$$
        * often created by applying a key creation algorithm to $$k_{priv}$$ 
   *  for every pair ($$k_{priv}, k_{pub}$$) there exists a 
       -  $$e_{k_{pub}}$$: encryption algorithm
           +  is public knowledge and easy to compute
       -  $$d_{k_{priv}}$$: decryption algorithm
           +  easily computabe by someone who has private key $k_{priv}$
           +  very difficult to compute for someone who only knows public key (that's the point!)
* actually very hard to prove whether true one way functions exist - we rely on the assumption that these problems are difficult (see P vs. NP unsolved problem)
    

## The Discrete Logarithm Problem:
* first construction is based on the DLP (Discrete Logarithm Problem) in $$\mathbb{F}_{p}$$ 
    * (the finite field with p elements, where p is prime!)
    
**Primitive Root Theorem**
    * Let p be prime. 
    * Then there is an element $$g /in /mathbb{F}_{p}^{*}$$

 
 