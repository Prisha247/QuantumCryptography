---
Title: "Math Behind RSA"
description: "the math behind the rsa algorithm, and why factoring can break it"
image: 'images/rsa.png'
---

{{< subheadings >}}
  {{< subheader >}}
  ### Math Behind The RSA Algorithm

  RSA involves a public key and private key. The public key can be known to everyone- it is used to encrypt messages. Messages encrypted using the public key can only be decrypted with the private key. The keys for the RSA algorithm are generated the following way:

  here will be an example of the algorithm in use, possibly with an animation, to make it easier for the viewer to understand. *ADD AN EXAMPLE*
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
