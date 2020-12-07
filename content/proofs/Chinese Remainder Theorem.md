+++
title = 'Chinese Remainder Theorem'
description = 'How does CRT help solve modular arithmetic problems?'
slug = 'crt'
disableComments = true
+++

The Chinese Remainder Theorem (CRT) can help solve systems of equations for modular arithmetic equations. For example, we will use CRT to solve the below problem:

$$ x \equiv 2\ (\bmod 3)$$
$$ x \equiv 1\ (\bmod 4)$$
$$ x \equiv 3\ (\bmod 5)$$

With CRT, we can solve this system of equations as if they were three independent equations. Consider the solution for x to be in the following form:

$$ x \equiv 4 \cdot 5 \cdot a + 3 \cdot 5 \cdot b + 3 \cdot 4 \cdot c\ (\bmod d) $$

_Note: this theorem only works when all of the divisors (e.g. $m$ in $x \equiv y\ (\bmod m)$ ) are [relatively prime](https://www.mathsisfun.com/definitions/relatively-prime.html)._

What are we multiplying by, and why? Each number, $a$, $b$, and $c$, represent **independent solutions** to the first, second, and third equations, respectively. By multiplying the first number by $4$ and $5$, we're ensuring that the value of $a$ only affects $x \bmod 3$. For any integer $a$, the value $4 \cdot 5 \cdot a$ has the same remainder when divided by $4$ and $5$:

$$ 4 \cdot 5 \cdot a \equiv 0\ (\bmod 4)$$
$$ 4 \cdot 5 \cdot a \equiv 0\ (\bmod 5)$$

Similarly, $b$ and $c$ are multiplied by all divisors except $4$ and $5$, respectively, so that they independently only change the values of $x \bmod 4$ and $x \bmod 5$ respectively.

Now, solve for $a$ in the equation where $20a \equiv 2\ (\bmod 3)$. For small numbers, this is trivial: when $a=1$, $20 \equiv 2\ (\bmod 3)$. Solving these individual equations gets more complicated as the numbers in the modulo function increase. This is out of the scope of CRT, but important to note.

Similarly, solve the equation $15b \equiv 1\ (\bmod 4)$ to get $b=3$ and $12c \equiv 3\ (\bmod 5)$ to get $c=4$. Now knowing the values of $a$, $b$, and $c$, $x = 20a+15b+12c = 20 \cdot 1 + 15 \cdot 3 + 12 \cdot 4 = 113$.

However, we still haven't solved for a specific value of $d$. The final answer is x≅17 (mod 12) or x≅5 (mod 12). The final answer is mod 12 because whenever 12 is added or subtracted from x, it has the same remainder when dividing by 3 or 4. In other words, 12 is the least common multiple of 3 and 4.


$$ 1 + 1 = 2 $$