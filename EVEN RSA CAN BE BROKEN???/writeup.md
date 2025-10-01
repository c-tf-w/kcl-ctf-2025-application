EVEN RSA CAN BE BROKEN???
===

**Author**: Michael Crotty
**Tags**: `Easy` `Cryptography` `picoCTF 2025` `browser_webshell_solvable`

---

### Solve Attempt

Hints:

- How much do we trust randomness?
- Notice anything interesting about N?
- Try comparing N across multiple requests
  
I netcat the server 12 times to get some `N`, `e`, and ciphertext. All instances of `N` are even, so maybe `p_1 == p_2 == ... == p_12 == 2`?

---
(The next day...)

~~I self-identify as bad at maths. Why am I doing crypto challenge? Actually why am I even in STEM?~~ the brain worms are coming out

I was reading [b6a newsletter 3](https://b6a.black/files/2025-09-12-b6a-newsletter-vol3/b6a-newsletter-vol3.pdf), on page 12 the article is about writing nvim plugin to automatically solve simple RSA challenge ("most ctf targeting people who 'have arms and legs' have a lot of easy crypto challenges, such as: [given `p`, `q`, `e`, `ct`, find plaintext]"). I'm not sure if I understand the code (I'm also reading off wikipedia that I barely understand), but might as well give it a try.

If I assume `p = 2`, then `q = N / 2`. Then we have `d = inverse(e, (p-1)*(q-1))`.

Then `pow(ciphertext, d, N)` should give us cleartext, and `long_to_bytes(pow(ciphertext, d, N)).decode('utf-8')` should (hopefully) give us the flag.

I went back and checked, and the source seems to ask for a 1024-bit key and `get_primes(k//2)` presumably (is supposed to) give you two 512-bit primes. The `N` are ~513 bits long, so probably `p = 2`.

#### Flag:

picoCTF{tw0_1$_pr!m37dbe6984}
