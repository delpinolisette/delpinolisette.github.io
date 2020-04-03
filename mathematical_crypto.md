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
  * consists of 
  * a private key $$k_{priv}$$
  * a public key $$k_{pub}$$
   * often created by applying a key creation algorithm to $$k_{priv}$$ 
   *  
 
 