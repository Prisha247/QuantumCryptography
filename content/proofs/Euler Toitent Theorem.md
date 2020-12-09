+++
title = 'Euler Totient Theorem'
slug = 'post2'
description = 'How does the Totient Theorem help create encryption keys?'
disableComments = true
+++
Euler’s Totient Function (mentioned as the $φ$ function in the RSA Algorithm page) measures the "breakability of a number" by calculating the number of coprimes of the product of two prime numbers, and is therefore used in the RSA algorithm to generate encryption keys (e). The greater the $φ$ number, the more possibilities of unique encryption keys. 

Suppose $p$ is a prime number. Let the $φ$ function will provide the number of values which are prime relative to the $p$. Since all numbers are prime to $p$ except for $p$,  $φ(p) = (p-1)$. 

(Note that this is actually the inclusion/exclusion principle in action)!

For example $φ(7) = (7-1) = 6$ 

The 6 coprimes are 1, 2, 3, 4, 5, 6. 7 is excluded because 7 is not prime relative to 7.

In the same manner, if $q$ is a prime number,  $φ(q) = (q-1)$. 

Now, in order to calculate the number of coprimes for the product of two prime numbers $p$ and $q$, we can multiply $φ(p)$ with $φ(q)$ to get $φ(p \cdot q)$!

Below is an example of the Totient Theorem in action.

We have two prime numbers $p$ and $q$.
$$ p = 5 $$
$$ q = 7 $$

The product of these prime numbers is as follows.
$$ N = p \cdot q = 5 \cdot 7 = 35 $$

To calculate the number of coprimes of $N$:
$$ φ (p \cdot q) = (p-1)\cdot (q-1) = (4) \cdot (6) = 24 $$




