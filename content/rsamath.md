---
  title: "Discrete Math meets Cryptography"
  content: "A Study into RSA and its Breakability"
---


### Math Behind The RSA Algorithm

RSA (Rivest, Shamir, and Adleman) Algorithm is a method of cryptography used to secure communication.
RSA involves a public key and private key. The public key can be known to everyone- it is used to encrypt messages. Messages encrypted using the public key can only be decrypted with the private key. The keys for the RSA algorithm are generated the following way:

Pick two prime numbers $p$ and $q$ and take their product ($N$). The numbers $p$ and $q$ are not released to the public.

Next, find $\phi(N)$  (see Totient Theorem) which is $(p-1) (q-1)$.
Choose encryption number $e$ such that $1 < e < \phi (N)$ AND $e$ is a [coprime](https://en.wikipedia.org/wiki/Coprime_integers) of $N$ and $\phi(N)$.
Choose decryption number $(d)$ such that $de\ (\bmod N) = 1$
The encrpytion key is $(e, N)$ and the decryption key is $(d, N)$.

<form action="#">
  <div class="row gtr-uniform">
    <div class="col-6 col-12-xsmall">
      Enter $p$
      <input type="text" name="Enter p" onchange="refreshAll()" id="rsa-p" value="1103" placeholder="Enter p" />
    </div>
    <div class="col-6 col-12-xsmall">
      Enter $q$
      <input type="text" name="Enter q" onchange="refreshAll()" id="rsa-q" value="3301" placeholder="Enter q" />
    </div>
  </div>
  <br />
  <div class="row gtr-uniform">
    <div class="col-12 col-12-xsmall">
      Enter Encryption Letter
      <input type="text" name="Enter Encryption Letter" onchange="refreshAll()" id="rsa-t" value="A" placeholder="Encryption Letter" />
    </div>
  </div>
</form>
<div id="error" style="color:red;"></div>

Here, $p$ is <span class="p">\_\_</span> and $q$ is <span class="q">\_\_</span>.
Additionally, the encryption text is "<span class="tStr">\_\_</span>".

The product ($N$) is $pq$, or <span class="n">\_\_</span>.

<span class="n">\_\_</span> becomes the modulus in the encryption and decryption key, thus <span class="n">\_\_</span> is released to the public.

Assign value to text. Let that value be <span class="t">\_\_</span>.

Now $e$ equals <span class="e">\_\_</span>.

Now solve to get the encrypted text:
<span class="emod"></span>
<br>
Here's the value for $d$:
<span class="d"></span>

Decryption: <span class="priv-key">\_\_</span>

Encryption received: <span class="enc">\_\_</span>
<br>

Solve to decrypt the text using $d$: <span class="dmod">\_\_</span>

<span class="dec">\_\_</span> is the decryption, which can be converted into <span class="decStr">\_\_</span>.

Note that if the encrypted and decrypted text aren't the same, it's likely that $p$ and $q$ are too small to encode the information you've sent. There are only $N$ possible values of anything $\\bmod N$, so if the encoded message (as a number) is larger than $N$, it can't be accurately encrypted.

### How Can Factoring Break the Algorithm?

The security of cryptography relies on certain "hard" problems. These problems are calculations that are simple to do with the right cryptographic key, but extremely difficult to do without it. A "hard" problem should take the best computers available billions of years to solve; an "easy" problem is one that can be solved very quickly.

RSA is currently an example of a “hard” problem, because it relies on integer factorization. A user starts with a message and performs arithmetic on it that involves multiplication by a very large number (hundreds of digits long). The only way to decode the message is to find the prime factors of the resulting product. The security of RSA encryption rests on the fact that there’s no fast way to identify the prime factors of very large numbers. If you’re not the intended recipient of a message — and if you therefore lack the right key to decode it — you could search for a thousand years with the best computers and still not find the right prime factors.


### Future Steps

The future of RSA is dependent on how efficiently one can factor to determine the prime numbers p and q explained above. Today's computers (classical computers) are not efficient enough to break the RSA algorithm in a timely manner. This is where quantum computing comes into play. Quantum computers have significantly greater speed than classical computers posing a danger to RSA and all data encrypted using RSA. Click on the Quantum Computing page to learn more!


<script type="text/javascript"
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
<script type="text/javascript">
  pEl = document.getElementById("rsa-p");
  qEl = document.getElementById("rsa-q");
  tEl = document.getElementById("rsa-t");
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
  // function gcd(x, y) {
  //   if(x === 0 || y === 0) {
  //     return 0;
  //   }
  //   if(x === y) {
  //     return x;
  //   }
  //   if(x >= y) {
  //     return gcd(x-y, y);
  //   }
  //   return gcd(x, y-x);
  // }
  // https://www.w3resource.com/javascript-exercises/javascript-math-exercise-8.php
  function gcd(x, y) {
    if ((typeof x !== 'number') || (typeof y !== 'number')) 
      return false;
    x = Math.abs(x);
    y = Math.abs(y);
    while(y) {
      var t = y;
      y = x % y;
      x = t;
    }
    return x;
  }
  function coprime(x, y) {
    return gcd(x, y) === 1;
  }
  function getE(N, totient) {
    i = 3;
    while (i < totient) {
      if (coprime(i, N) && coprime(i, totient)) {
        return i;
      }
      i += 2;
    }
    return 0;
  }
  // http://umaranis.com/2018/07/12/calculate-modular-exponentiation-powermod-in-javascript-ap-n/
  // calculates   base^exponent % modulus
  function powerMod(base, exponent, modulus) {
      if (modulus === 1) return 0;
      var result = 1;
      base = base % modulus;
      while (exponent > 0) {
          if (exponent % 2 === 1)  //odd number
              result = (result * base) % modulus;
          exponent = exponent >> 1; //divide by 2
          base = (base * base) % modulus;
      }
      return result;
  }

  function str2int(stringInput) {
    let output = "";
    for (var i = 0; i < stringInput.length; i++) {
        output += stringInput[i].charCodeAt(0).toString(2);
    }
    return parseInt(output, '2');
  }
  function int2str(intInput) {
    let output = "";
    while (intInput > 0) {
      output = String.fromCharCode(intInput % 128) + output;
      intInput = Math.floor(intInput/128);
    }
    return output;
  }

  // https://stackoverflow.com/questions/23279208/calculate-d-from-n-e-p-q-in-rsa#23281286
  function getD(a, m) {
    // validate inputs
    [a, m] = [Number(a), Number(m)]
    if (Number.isNaN(a) || Number.isNaN(m)) {
      return NaN // invalid input
    }
    a = (a % m + m) % m
    if (!a || m < 2) {
      return NaN // invalid input
    }
    // find the gcd
    const s = []
    let b = m
    while(b) {
      [a, b] = [b, a % b]
      s.push({a, b})
    }
    if (a !== 1) {
      return NaN // inverse does not exists
    }
    // find the inverse
    let x = 1
    let y = 0
    for(let i = s.length - 2; i >= 0; --i) {
      [x, y] = [y,  x - y * Math.floor(s[i].a / s[i].b)]
    }
    return (y % m + m) % m
  }

  // for loop copied from https://stackoverflow.com/questions/22754315/for-loop-for-htmlcollection-elements

  function refreshAll() {
    if(validateP() && validateQ()) {
      document.getElementById("error").innerHTML = "";
      updatePQ();
    } else {
      errorEl = document.getElementById("error");
      errorEl.innerHTML = "Error: Ensure that $p$ and $q$ are prime numbers less than 100000 <br /><br />";
      MathJax.Hub.Queue(["Typeset",MathJax.Hub,errorEl]);

      // updatePQ();
    }
  }
  function validateP() {
    testP = pEl.value;
    if(testP > 1 && testP < 100000 && prime(testP)) {
      p = testP;
      return true;
    } else {
      return false;
    }
  }

  function validateQ() {
    testQ = qEl.value;
    if(testQ > 1 && testQ < 100000 && prime(testQ)) {
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

    // update e
    e = getE(n, totient);
    updateClass("e", e);
    // update d https://stackoverflow.com/questions/23279208/calculate-d-from-n-e-p-q-in-rsa#23281286

    tStr = tEl.value;
    t = str2int(tStr);

    updateClass("tStr", tStr, "");
    updateClass("t", t);

    enc = powerMod(t, e, n);
    console.log("" + t + "^" + e + "\\ (\\bmod " + totient + ") = " + enc);
    updateClass("emod",
      "" + t + "^{" + e + "}\\ (\\bmod " + n + ") = " + enc
    );
    updateClass("enc", enc);

    d = getD(e, totient);
    updateClass("d", d);

    updateClass("priv-key", "(" + d + "," + n + ")");
    dec = powerMod(enc, d, n);
    updateClass("dmod", 
      "" + enc + "^{" + d + "}\\ (\\bmod " + n + ") = " + dec
    );
    updateClass("dec", dec)

    decStr = int2str(dec);
    updateClass("decStr", decStr, "");
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

  refreshAll();
</script>
