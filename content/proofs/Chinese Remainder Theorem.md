+++
title = 'Chinese Remainder Theorem'
description = 'How does CRT help solve modular arithmetic problems?'
slug = 'post1'
image = 'images/pic03.jpg'
disableComments = true
+++

The G
Solve modular arithmetic systems of equations as if the equations were independent.
Condition: all divisors (e.g. m in $$x \equiv y\ (\bmod m)$$ ) must be relatively prime.

Consider the equation x≅2 (mod 3) and x≅1 (mod 4).

3 and 4 are relatively prime, so this equation can be solved using CRT.

To split this equation into multiple parts, consider a solution x to be in the form of x≅4a + 3b (mod c). The variable a is used to solve x≅2 (mod 3) and b is used to solve x≅1 (mod 4).

We multiply a by 4 so that changing the value of a only changes what x is congruent to mod 3. 

Essentially, by ensuring that 4a is divisible by 4, we know that no matter what integer is used as a, 4a is zero mod 4. If there were more terms, then instead of just multiplying by 4, we would multiply by all modulo numbers other than the first number. For example, if the equation were x≅2 (mod 3), x≅1 (mod 4), and x≅3 (mod 5), a would be multiplied by 4 and 5 so that it doesn’t change x mod 4 or 5, and just x mod 3.

Now, solve for a in the equation where 4a≅2 (mod 3). Actually finding the solution to this equation, a=2 (8≅2 (mod 3)), is quite trivial for small numbers, but it gets more complicated as the numbers for the modulo function increase. This is out of the scope of CRT, but important to note.

Similarly, solve the equation 3b≅1 (mod 4) to get b=3. Now, 4a+3b = 4*2 + 3*3 = 17 = x. The final answer is x≅17 (mod 12) or x≅5 (mod 12). The final answer is mod 12 because whenever 12 is added or subtracted from x, it has the same remainder when dividing by 3 or 4. In other words, 12 is the least common multiple of 3 and 4.


$$ 1 + 1 = 2 $$