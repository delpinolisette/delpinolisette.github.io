---
layout: default
---
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

Below are some rough notes on mathematical cryptography - these are always in progress.

# Key Issues 

Factoring numbers intro prime factors is *hard*. The fastest known algorithms are exponential in the number of bits of the number. 

Primality testing is easy. 

This contrast allows secure encryption to exist. 

### Preliminaries:
#### **Ring of Integers Mod m**
*  :=   $$\mathbb{Z}/m\mathbb{Z}$$={$$0,1,2,......,m-1$$}
    * Notice $$\mathbb{Z}/m\mathbb{Z}$$ is the quotient ring of $$\mathbb{Z}$$ by the _principal ideal_ $$/m\mathbb{Z}$$
    * then $$0,1,2,......,m-1$$ are _coset representatives_ for the congruence classes that make up the elements of $$\mathbb{Z}/m\mathbb{Z}$$

#### **Set of all units**
* numbers that have inverses modulo m ($$a$$ has inverse mod $$m$$ iff gcd(a,m)=1) are units. 
    * EXERCISE: Prove that the inverse of a mod m exists iff gcd(a,m) = 1
    * (a colloquial way to think about $$\mathbb{Z}/m\mathbb{Z}^{*}$$ is the set of integers mod m without 0- since it can only include units)

#### **Primitive Root Theorem**
* Let p be prime. 
* Then there is an element $$g \in \mathbb{F}_{p}^{*}$$ - multiplicative group
...(to be continued)

---

### Public Key Cryptosystems:

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

---
#### **The Discrete Logarithm Problem:**
* first construction is based on the DLP (Discrete Logarithm Problem) in $$\mathbb{F}_{p}$$ 
    * (the finite field with p elements, where p is prime!)
* recall that the elements of \\(\mathbb{F}\_{p}^{*}\\) = \\(\\{ 1,g,g^{2},...,g^{p-2} \\}\\)
  - because by FLT \\(g^{p-1} = 1\\)
  - \\(g\\) is primitive root (g is a primitive root mod n if it is a generator for the same multiplicative group). 
* **Discrete Logarithm Problem** (def): 
  * g is a primitive root for \\(\mathbb{F}\_{p}\\), 
  * \\(h\\) is nonzero element of \\(\mathbb{F}\\)
  * DLP says find an \\(x\\) s.t. \\(g^{x} \equiv h (mod p)\\)
  * \\(x\\) = "the discrete log of h to the base g" = \\(log\_{g}h\\)   

---
### Quantifying the "Hardness" of Discrete Logarithm Problem 

* $$Log_{a}b = x$$ <=> $$a^{x}=b$$

* What is D.L.P?
  - Given a group $$G$$ and elements $$g,h \in G$$,
  - find an exponent $$x$$ such that 
  -   $$g^{x}=h$$ , or ($$log_{g}h=x$$)

* A way to 'measure hardness': how many operations do we need to solve this with the fastes method known?? Different methods:
  - Trial and error : $$g^{x}=h$$, try x = 1, 2, 3,.... until we get $$h$$
    + def: **order of group**
      * smallest possible element n such that $$g^{n}=e$$, where e is the identity element in the group. 
      * [more info on order](https://en.wikipedia.org/wiki/Order_(group_theory))
      
  - if $$g$$ has order $$n$$ (so we multiply $$g$$ by itself $$n$$ times to get $$e$$)
  - then we are guaranteed using trial and error to find the solution in at most $$n$$ steps/operations 
    + if n is very large (ex: $$n \geq 2^{80}$$) - unfeasible


  - Fast exponentiation method: [method](https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/fast-modular-exponentiation)
  - 

---
### The Chinese Remainder Theorem: 
* C.R.T describes solutions to system of linear congruences. 
* ex: \\(x \equiv a\\)(mod m) and \\(x \equiv b\\)(mod n) with \\(gcd(m,n) = 1\\), in this case the solution is unique and mod mn, (why)?
* ex: solve for integer x. 
  + \\(x \equiv 1\\)(mod 5) and \\(x \equiv 9\\)(mod 11)
    - S1: substitute one congrunce into the other: 
      * since \\(x \equiv 1\\) (mod 5), then
      * (to be continued) [checkitout](https://brilliant.org/wiki/chinese-remainder-theorem/)


---
### 2.9 The Pohlig-Hellman Algorithm: 
* recall that though the Chinese Remainder Theorem...
  - if \\(m = m\_{1} \cdot m\_{2} \cdot ...m\_{t}\\) is the product of _pairwise relatively prime_ integers (ex: 7*6 is relatively prime, their only common divisor is 1). 
    + then solving an equation (mod m) 









 