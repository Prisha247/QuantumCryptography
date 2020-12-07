+++
title = 'Euler Totient Theorem'
slug = 'post2'
description = 'How does the Totient Theorem help create encryption keys?'
disableComments = true
+++
Euler’s Totient Function (mentioned as the phi function in the RSA Algorithm page) measures the "breakability of a number". The phi function serves to calculate the number of coprimes of the product of two prime numbers, and is therefore used in the RSA algorithm to generate encryption keys (e). The greater the phi number, the more possibilities of unique encryption keys. 

Suppose p and q are prime numbers. The phi function will provide the number of values which are prime relative to the product of p and q by taking the product of (p-1) and (q-1). 

Below is an example of the Totient Theorem in action.

We have two prime numbers p and q.
$$ p = 5 $$
$$ q = 7 $$

The product of these prime numbers is as follows.
$$ N = p \cdot q = 5 \cdot 7 = 35 $$

To calculate the number of coprimes of N, we use the phi function.
$$ phi function = (p-1)\cdot (q-1) = (4) \cdot (6) = 24 $$




