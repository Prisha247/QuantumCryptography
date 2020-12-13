---
  title: "Discrete Math meets Cryptography"
  content: "A Study into RSA and its Breakability"
---

{{< subheadings >}}
  {{< subheader >}}

### Math Behind The RSA Algorithm

RSA (Rivest, Shamir, and Adleman) Algorithm is a method of cryptography used to secure communication.
RSA involves a public key and private key. The public key can be known to everyone- it is used to encrypt messages. Messages encrypted using the public key can only be decrypted with the private key. The keys for the RSA algorithm are generated the following way:

Pick two prime numbers $p$ and $q$ and take their product ($N$). The numbers $p$ and $q$ are not released to the public.

Next, find $\phi(N)$  (see Totient Theorem) which is $(p-1) (q-1) = $<span class="p-1">$1$</span>$ \cdot $<span class="q-1">$6$</span>$ = $<span class="totient">$6$</span>.
Choose encryption number $e$ such that $1 < e < \phi(N)$ AND $e$ is a [coprime](https://en.wikipedia.org/wiki/Coprime_integers) of $N$  (<span class="n">$14$</span>) and $\phi(N)$ $($<span class="totient">$6$</span>$)$
Choose decryption number $(d)$ such that $de\ (\bmod N) = 1$
The decryption key is $(d, N)$

Encryption Key: (5,14)

<form action="#">
  <div class="row gtr-uniform">
    <div class="col-6 col-12-xsmall">
      Enter $p$
      <input type="text" name="Enter p" onchange="refreshAll()" id="rsa-p" value="2" placeholder="Enter p" />
    </div>
    <div class="col-6 col-12-xsmall">
      Enter $q$
      <input type="text" name="Enter q" onchange="refreshAll()" id="rsa-q" value="7" placeholder="Enter q" />
    </div>
  </div>
  <div class="row gtr-uniform">
    <div class="col-12 col-12-xsmall">
      Enter Encryption Text
      <input type="text" name="Enter Encrpytion Text" onchange="refreshText()" id="enc-text" value="B" placeholder="Encrpytion Text" />
    </div>
  </div>
</form>
<div id="error" color="red"></div>

Here, $p$ is <span class="p">$2$</span> and $q$ is <span class="q">$7$</span>, thus their product ($N$) is <span class="n">$14$</span>.
<span class="n">$14$</span> becomes the modulus in the encryption and decryption key, thus <span class="n">$14$</span> is released to the public.

Assign value to text. Let B equal to 2.

25(mod14) = 32(mod14) = 4(mod14)

4 is the encryption. Let 4 equal D.

Decryption: (11,14)

Text received: D

Assign value to text received. Let D equal 4.

411(mod14) = 4194304(mod14) = 2(mod14)

2 is the decryption. 2 is equal to B.

  {{< /subheader >}}
  {{< subheader >}}
  ### How Can Factoring Break the Algorithm?

  The security of cryptography relies on certain "hard" problems. These problems are calculations that are simple to do with the right cryptographic key, but extremely difficult to do without it. A "hard" problem should take the best computers available billions of years to solve; an "easy" problem is one that can be solved very quickly.

  Trapdoor functions are based on multiplication - which is easy to perform in one direction but next to impossible in the other
      E.g. it is relatively easy to know that 263 * 373 = 98,099. However, given 98,099, it is extremely difficult to figure out what two prime numbers were multiplied to produce that number. As the prime numbers get larger, it becomes even more difficult to factor.

  RSA is currently an example of a “hard” problem, because it relies on integer factorization. A user starts with a message and performs arithmetic on it that involves multiplication by a very large number (hundreds of digits long). The only way to decode the message is to find the prime factors of the resulting product. The security of RSA encryption rests on the fact that there’s no fast way to identify the prime factors of very large numbers. If you’re not the intended recipient of a message — and if you therefore lack the right key to decode it — you could search for a thousand years with the best computers and still not find the right prime factors.


  {{< /subheader >}}
  {{< subheader >}}
  ### Future Steps
 The future of RSA is dependent on how efficiently one can factor to determine the prime numbers p and q explained above. Today's computers (classical computers) are not efficient enough to break the RSA algorithm in a timely manner. This is where quantum computing comes into play. Quantum computers have significantly greater speed than classical computers posing a danger to RSA and all data encrypted using RSA. Click on the Quantum Computing page to learn more!
  {{< /subheader >}}
{{< /subheadings >}}

<script type="text/javascript">
  pEl = document.getElementById("rsa-p");
  qEl = document.getElementById("rsa-q");
  p = 2;
  q = 7;

  function prime(n) {   
    // almost copied from https://www.geeksforgeeks.org/check-a-number-is-prime-or-not-using-javascript/         
    var i, flag = true;

    // Getting the value form text
    // field using DOM
    n = parseInt(n) || 0;
    if(n === 0) {
      return false;
    }
    for(i = 2; i <= n - 1; i++)
        if (n % i == 0) {
            flag = false;
            break;
        }

        // Check and display alert message
    if (flag == true)
        return true; // prime
    else
        return false; // not prime
  }
  function gcd(x, y) {
    if(x === 0 || y === 0) {
      return 0;
    }
    if(x === y) {
      return x;
    }
    if(x >= y) {
      return gcd(x-y, y);
    }
    return gcd(x, y-x);
  }
  function coprime(x, y) {
    return gcd(x, y) === 1;
  }

  // function updatePQ(el) {
  //   // if(el.)
  // }
  // for loop copied from https://stackoverflow.com/questions/22754315/for-loop-for-htmlcollection-elements


  function refreshAll() {
    if(validateP() && validateQ()) {
      document.getElementById("error").innerHTML = "";
      updatePQ()
    } else {
      errorEl = document.getElementById("error");
      errorEl.innerHTML = "Error: Ensure that $p$ and $q$ are prime numbers less than 1000 <br /><br />";
      MathJax.Hub.Queue(["Typeset",MathJax.Hub,errorEl]);

      updatePQ();
    }
  }
  function validateP() {
    testP = pEl.value;
    if(testP > 1 && testP < 1000 && prime(testP)) {
      p = testP;
      return true;
    } else {
      return false;
    }
  }

  function validateQ() {
    testQ = qEl.value;
    if(testQ > 1 && testQ < 1000 && prime(testQ)) {
      q = testQ;
      return true;
    } else {
      return false;
    }
  }

  function updatePQ() {

    // update p and q
    updateClass("p", p);
    updateClass("q", q);

    // update p and q
    updateClass("p-1", p-1);
    updateClass("q-1", q-1);

    // update n
    n = p * q;
    updateClass("n", n);

    // update totient
    totient = (p-1)*(q-1);
    updateClass("totient", totient);

    // update d https://stackoverflow.com/questions/23279208/calculate-d-from-n-e-p-q-in-rsa#23281286
  }

  function updateClass(className, expr, options) {
    var list = document.getElementsByClassName(className);
    for (var i = 0; i < list.length; i++) {
        updateEl(list[i], (options || "$") + expr + (options || "$"));
    }
  }

  function updateEl(el, expr) {
    el.innerHTML = expr;
    MathJax.Hub.Queue(["Typeset",MathJax.Hub,el]);
  }

  function refreshText() {
    return true;
  }

  pEl.value = 2;
  qEl.value = 7;
  validateP() && validateQ() && refreshAll();
</script>
