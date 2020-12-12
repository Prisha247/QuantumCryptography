---
Title: "Quantum Computing and the future of RSA"
---

### What is Quantum Computing?

“Quantum computing” is computation performed using a computing device based on the physical properties of matter at very small scale, also known as quantum mechanics

Classical computers, like the ones we use today, function based on transistors that encode data in binary digits, also known as bits, that can only be a “1” or a “0”. Quantum computers, however, use “qubits,” where a single qubit is able to encode many more than two states.

### What is Shor's Algorithm?

Shor’s Algorithm is a three-part answer to the problem of prime factorization for any integer, so it works no matter how large the integer involved. The first part is performed on a classical computer in polynomial time, but it is only the set-up for the second and most important part. The second part requires the use of specially constructed quantum circuits to perform the quantum computation needed to find the value you need for the third part, which allows you to find the prime factors of the integer on a classical computer.

The first part of the algorithm is transforming the problem of prime factorization into an equivalent problem that is solvable, namely, finding the period of a modular operation. If you can find the period of this function using as the integer you want to factor as a modulus, you can find the prime factors fairly quickly on a classical computer with some additional calculations.

The problem is that, like prime factorization, finding the period of this modular operation isn’t something a classical computer can do in polynomial time, but Shor showed in the second part of the algorithm that using a theoretical quantum computer your could calculate this period and, most importantly, he was able to prove mathematically that this part of the quantum algorithm ran in polynomial time. After finding the period, a classical computer could use it to find the prime factors of any integer.

### Why does Quantum Computing Pose a Threat to the RSA Algorithm?

Peter Shor showed that a theoretical quantum computer could solve an intractable mathematical problem in ways that a classical computer never could by side-stepping the need to calculate single values at a time. Quantum computers can perform operations on qubits in superposition and literally reduce the time complexity of a problem exponentially.

When Shor devised his algorithm, quantum computing didn’t exist in any meaningful way. The idea had been around for a while, but it was entirely theoretical, impractical to even attempt to build, and no one could see the utility in trying to build one since there was no example of anything a quantum computer could do that a classical computer could not.

By showing how a quantum computer could actually be useful in a way that classical computers couldn’t by solving a classically intractable problem in polynomial time, Peter Shor sparked the interests of researchers around the world who began their own research into quantum computing and now actual, working quantum computers are being built. It will be a decade at least before a quantum computer has enough qubits to break RSA encryption, but its end is certain and already cryptographers have opened up new avenues of research into Post-Quantum Cryptography to make sure that everything that needs to remain secure does.

After Peter Shor’s algorithm proved that hard problems for classical computers could be solved, others began looking at other hard problems that might also be solved by quantum computers, and for good reason; of the many problems that remain to be solved, the potential benefit to solving them is as enormous as the problems themselves.
