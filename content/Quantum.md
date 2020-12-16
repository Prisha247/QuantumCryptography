---
Title: "Quantum Computing and the Future of RSA"

---

### What is Quantum Computing?

“Quantum computing” is performed using a device based on the physical properties of matter at the atomic level, also known as quantum mechanics.

Classical computers, like the ones we use today, function based on transistors that encode data in binary digits, also known as bits, that can only be a “1” or a “0”. Quantum computers, however, use “qubits,” where a single qubit is able to encode many more than two states.

### What is Shor's Algorithm?

Shor’s Algorithm is a three-part answer to the problem of prime factoring any integer, so it works no matter how large the integer involved is. The first part is performed on a classical computer in polynomial time, but it is used only to set up for the second, and most important part of the equation. This second part requires the use of specially constructed quantum circuits to perform the quantum computation needed to find the value needed for the third part, which allows you to find the prime factors of the integer on a classical computer.

The first part of the algorithm is transforming the problem of prime factorization into an equivalent problem that is solvable, aka finding the period of a modular operation. If you can find the period of this function using as the integer you want to factor as a modulus, you can find the prime factors fairly quickly on a classical computer with some additional calculations.

The problem is that, like prime factorization, finding the period of this modular operation isn’t something a classical computer can do in polynomial time, but Shor showed in the second part of the algorithm that using a theoretical quantum computer, you could calculate this period. Most importantly, though, he was able to prove mathematically that this part of the quantum algorithm runs in polynomial time. After finding the period, a classical computer could use the values generated to find the prime factors of any integer.

### Why does Quantum Computing Pose a Threat to the RSA Algorithm?

Peter Shor showed that a theoretical quantum computer could solve an unsolvable mathematical problem in ways that a classical computer never could. By side-stepping the need to calculate single values at a time, quantum computers can perform operations on qubits in superposition and reduce the time complexity of a problem exponentially.

When Shor completed the design of his algorithm, quantum computing had no real purpose - it didn't exist. The concept had been around for a while, but it was fully theoretical, impractical to even attempt to build, and no one could see the point of trying to build one, since there was no example of anything a quantum computer could do that a classical computer couldn't.

By showing how a quantum computer could actually be useful, Peter Shor sparked the interests of researchers around the world, who then began their own research into quantum computing. As a result, we now have real life, working quantum computers being built. It will almost certainly be at least a decade before a quantum computer has even close to enough qubits to break RSA encryption, but its eventual end is certain, and cryptographers have already opened up new avenues of research into Post-Quantum Cryptography to make sure that everything that needs to remain secure, does.

After Shor’s algorithm proved that "hard" problems for classical computers could actually be solved, other researchers began looking at other "hard" problems that might also be solved by quantum computers. The general realization is this: of the infinite problems that still need to be solved, the potential benefit to solving even a few of them is just as enormous as the problems themselves.
