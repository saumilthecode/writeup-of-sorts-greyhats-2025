# firstly, i invite you to look at this picture

![](https://raw.githubusercontent.com/saumilthecode/writeup-of-sorts-greyhats-2025/refs/heads/main/Idk/cat.webp)

thanks i found the image hella funny and wanted someone else to look at it

So "IDK" chal is 
> I've been really into zero knowledge proofs lately! I wrote a simple program that can prove that I'm the only person who knows how to decrypt this message, and because I'm so confident, I'll even give you some dumps of my proofs!

and a attached .zip that extracts to 3 .txt's and 2.py's

how to solve?


---

**1. Parse `message.txt`**

* Extract the 617-digit modulus `N`, exponent `e=65537`, and ciphertext `c`.

**2. Load both proof dumps (`dump1.txt` and `dump2.txt`)**

* Each dump has the format:

  1. Line 1: `F_hex` (the prover’s plaintext commitment, here “746869735f69735f615f736563726574” → `this_is_a_secret`)
  2. Lines 2–9: eight σ‐values (commitments)
  3. Lines 10–2849: µ‐values (each of the 2 840 responses)
  4. Line 2850: “OK”

**3. Factor `N` via differing square‐roots**

* Whenever θⱼ is a quadratic residue, the prover picks a random sign for
  µⱼ = ± √θⱼ mod N.
  Running the protocol twice on the same θⱼ yields two distinct nonzero µ₁ⱼ ≠ µ₂ⱼ such that
  µ₁ⱼ² ≡ θⱼ  (mod N) and µ₂ⱼ² ≡ θⱼ (mod N).
* Take any index j where µ₁ⱼ ≠ 0, µ₂ⱼ ≠ 0, and µ₁ⱼ ≠ µ₂ⱼ, then

```
g = gcd( µ₁ⱼ − µ₂ⱼ, N )
```

yields a nontrivial factor of N. In this challenge, one of the earliest nonzero µ-pairs already factors N into

```
p = 142260237691… (309 digits)  
q = 107261859432… (309 digits)
```

**4. Compute the private exponent and decrypt**

```python
phi = (p−1)*(q−1)
d   = inverse(e, phi)
m   = pow(c, d, N)
plaintext = m.to_bytes((m.bit_length()+7)//8, "big")
```

Evaluating this returns the ASCII string:

```
grey{how_i_swear_you_shouldve_had_0_knowledge}
```

---

**Flag:**

```
grey{how_i_swear_you_shouldve_had_0_knowledge}
```


and the obligatory 