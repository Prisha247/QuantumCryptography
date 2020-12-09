---
Title: "Math Behind RSA"
description: "the math behind the rsa algorithm, and why factoring can break it"
image: 'images/rsa.png'
---

{{< subheadings >}}
  {{< subheader >}}
  ### Math Behind The RSA Algorithm

  RSA involves a public key and private key. The public key can be known to everyone- it is used to encrypt messages. Messages encrypted using the public key can only be decrypted with the private key. The keys for the RSA algorithm are generated the following way:

Pick two prime numbers p and q and take their product (N). P and q are not released to the public.
Here, p is 2 and q is 7, thus their product (N) is 14. 
N becomes the modulus in the encryption and decryption key, thus N is released to the public.
Next, find $φ(N)$  (see Totient Theorem) which is (p-1) \cdot (q-1) = (1) \cdot (6) = 6.
Choose encryption number (e) such that 1< e < $φ(N)$ AND e is a coprime of $N$ and $φ(N)$
Choose decryption number (d) such that $d*e(modN)$ = 1
The decryption key is $(d, N)$

Encryption Key: (5,14)
Text that needs to be encrypted: B
Assign value to text. Let B equal to 2.
25(mod14) = 32(mod14) = 4(mod14) 
4 is the encryption. Let 4 equal D.

Decryption: (11,14)
Text received: D
Assign value to text. D → 4
411(mod14) = 4194304(mod14) = 2(mod14) 
2 is the decryption. 2 is equal to B..

  {{< /subheader >}}
  {{< subheader >}}
  ### How Can Factoring Break the Algorithm?
  RSA’s public key consists of the modulus n (which we know is the product of two large primes) and the encryption exponent $e$. The private key is the decryption exponent d. Recall that e and d are inverses mod φ (n). Knowing φ (n) and n is equivalent to knowing the factors of n.

  One attack on RSA is to try to factor the modulus n. If we could factor n, we could calculate φ ( ) n and (by using the extended Euclidean algorithm) determine d.

  {{< /subheader >}}
  {{< subheader >}}
  ### Future Steps
  introduce quantum cryptography, and urge the audience to go to the next page, where we will talk about shor's algorithm.
  {{< /subheader >}}
{{< /subheadings >}}
