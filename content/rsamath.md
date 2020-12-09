---
Title: "Math Behind RSA"
description: "the math behind the rsa algorithm, and why factoring can break it"
image: 'images/rsa.png'
---

{{< subheadings >}}
  {{< subheader >}}
  ### Math Behind The RSA Algorithm

  RSA involves a public key and private key. The public key can be known to everyone- it is used to encrypt messages. Messages encrypted using the public key can only be decrypted with the private key. The keys for the RSA algorithm are generated the following way:

Pick two prime numbers $p$ and $q$ and take their product ($N$). The numbers $p$ and $q$ are not released to the public.

<!-- Assign $p$ here: <input type="text" name=n value="" id="rsa-p"><br />
Assign $q$ here: <input type="text" name=n value="" id="rsa-p"><br />
 -->

<!-- <input type="number" name="q" id="rssafrga-p" value="2" placeholder="p" /> -->
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
</form>
<div id="error" color="red"></div>

Here, $p$ is <span class="p">$2$</span> and $q$ is <span class="q">$7$</span>, thus their product ($N$) is <span class="n">$14$</span>. 
$N$ becomes the modulus in the encryption and decryption key, thus $N$ is released to the public.
Next, find $\phi(N)$  (see Totient Theorem) which is (p-1) \cdot (q-1) = (1) \cdot (6) = 6.
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

Assign value to text received. Let D equal 4.

411(mod14) = 4194304(mod14) = 2(mod14) 

2 is the decryption. 2 is equal to B.

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

    // update p
    var list = document.getElementsByClassName("p");
    for (var i = 0; i < list.length; i++) {
        updateEl(list[i], "$" + p + "$");
    }

    // update q
    var list2 = document.getElementsByClassName("q");
    for (var i = 0; i < list2.length; i++) {
        updateEl(list2[i], "$" + q + "$");
    }

    // update n
    n = p * q;
    var list = document.getElementsByClassName("n");
    for (var i = 0; i < list.length; i++) {
        updateEl(list[i], "$" + n + "$");
    }
  }


  function updateEl(el, expr) {
    el.innerHTML = expr;
    MathJax.Hub.Queue(["Typeset",MathJax.Hub,el]);
  }

  validateP() && validateQ() && refreshAll();
</script>