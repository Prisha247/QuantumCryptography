+++
title = 'Fermat Little Theorem'
slug = 'fermat-little'
description = 'Donec eget ex magna. Interdum et malesuada fames ac ante ipsum primis in faucibus. Pellentesque venenatis dolor imperdiet dolor mattis sagittis magna etiam.'
disableComments = true
+++

## Description

Fermat's Little Theorem, also known as Euler's Little Theorem, is an equation that involves modular equations with exponentiation, similar to the exponentiation done in RSA. More specifically, the theorem is as follows:

$$a^p \equiv a\ (\bmod p)$$

More specifically, $a$ can be any integer, and $p$ can be any **prime number**.

### Corollary

Dividing both sides by $a$ produces this corollary. Both this form and the above form can come in handy when solving modular arithmetic equations.

$$a^{p-1} \equiv 1\ (\bmod p)$$

## Proof

This proof can be done many ways, but one of the simplest ones involves using the binomial theorem and induction, and can prove the above equation for all positive values $a \geq 0$.

### Base Case

Consider the case where $a = 0$. The theorem can be expressed as follows:

$$0^{p} \equiv 0\ (\bmod p)$$

We know that for all values of $p \neq 0$, $0^p = 0$. Therefore, for all prime numbers $p$, $0^p = 0 \equiv 0\ (\bmod p)$

### Induction

Given that $a$ works in this proof, we want to prove that the $a+1$ case works. The $a+1$ case can be represented as the expression below.

$$(a+1)^p \equiv a+1\ (\bmod p)$$

#### Binomial Expansion

Expanding the left side of the equation is key for solving this proof. By the binomial theorem, the left side can be expanded as follows:

$$(a+1)^p = \sum_{i=0}^p {p \choose i} a^i 1^{p-i}$$

This may look like nothing at first. However, there is something important to note: almost all of the terms in the summation are divisible by $p$. In the term ${p \choose i}$, $p$ is always in the numerator. Because $p$ is prime, the only way to "cancel out" this $p$ is to have $p$ in the denominator, which only happens when $i=0$ (${p \choose 0} = \frac{p!}{0!(p-0)!}$) and $i=p$ (${p \choose p} = \frac{p!}{p!(p-p)!}$). When a term is divisible by $p$, it is equivalent to $0 \bmod p$, and the term can be ignored. Removing all but the two terms from the summation $i=0$ and $i=p$ gives the following output:

$$(a+1)^p \equiv {p \choose 0} a^0 + {p \choose p} a^p\ (\bmod p)$$

Since ${p \choose 0} = {p \choose p} = 1$, the equation can be further simplified as following:

$$(a+1)^p \equiv 1 + a^p\ (\bmod p)$$

#### Inductive Step

Using induction, we can assume that $a^p \equiv a\ (\bmod p)$. Substituting this into the equation derived above reveals the following result:

$$(a+1)^p \equiv a + 1\ (\bmod p)$$

This is, in fact, the $a+1$ statement we wanted to prove given that $a$ is true. By induction, this means that all integers $a \geq 0$ work for this theorem, and $a^p \equiv a\ (\bmod p)$.