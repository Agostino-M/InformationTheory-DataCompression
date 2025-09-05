# InformationTheory-DataCompression

Project completed as part of the Information Theory and Data Compression course for the MSc in Computer Engineering at the University of Palermo, academic year 2023/24.

## Exercises Overview

### ES1 – Sardinas-Patterson Algorithm
Write a Python program that applies the Sardinas-Patterson algorithm and returns the type of code received as input, distinguishing the three different halt conditions.

- Apply the algorithm to test whether the code set `C = {012, 0123, 4, 310, 1024, 2402, 2401, 4013}` is uniquely decodable (UD).
- Apply the algorithm to verify which of the following codes are UD:
  - `C1 = {10, 010, 1, 1110}`
  - `C2 = {0, 001, 101, 11}`
  - `C3 = {0, 2, 03, 011, 104, 341, 11234}`
  - `C4 = {01, 10, 001, 100, 000, 111}`
- Modify your algorithm to output, when a code is not UD, a pair of distinct sequences of codewords that prove the code is not uniquely decodable (if such sequences exist). Apply this to the code set `{0, 01, 011, 0111}` and discuss the output.

*These exercises are part of the lab project for the final examination.*

---

### ES2 – Huffman Coding
1. Define a function that, given a text, creates the corresponding discrete source.
2. Add a `Huffman` method to the `Source` class that computes the Huffman encoding.
3. Write a program that, given an input text, computes its Huffman encoding and also includes a decoding procedure to recover the original message.

---

### ES3 – Burrows-Wheeler Transform (BWT)
Write a program to compute the Burrows-Wheeler Transform of a text `T` in two ways:
1. By sorting all cyclic rotations of `T`.
2. By appending `$` to `T` and using the SA-IS algorithm to sort the suffixes of `T$`.

The algorithm should also output the number of equal-letter runs `r` for `BWT(T)` and `r$` for `BWT(T$)`.

Test your program on:
- A random word.
- A Fibonacci word of a given order.
- All words of a given length, reporting the words with the maximal number of equal-letter runs.

Compare results when applied to Fibonacci words of even order with the last symbol removed.

> Fibonacci words are defined as:
> ```
> f0 = b, f1 = a, fi = fi-1 fi-2, i ≥ 2
> Example: f5 = abaa bab a, f6 = abaa bab a abaa b aa b
> ```

---

### ES4 – LZ77 and LZSS Encoding
Write a program that, given a text `T`, outputs both the LZ77 and LZSS encodings of the text. Include a parameter `W` for the length of the search buffer.

Compare the number of triplets `z` produced by LZ77(T)/LZSS(T) with the number of equal-letter runs `r` from BWT(T).

Experimentally verify whether:
- `r = O(z log2 n)`
- `z = O(r log n)`

where `n` is the length of the input text. Compute `z` and `r` for:
- The set, for a given $k > 0$, of words:

$$
T_k = \{ w_{i,k} = \prod_{j=1}^{i} (a b^{j^{k}}) \mid i \ge 1 \}
$$

- Fibonacci words of odd and even order.
- Given an integer $k > 5$, the set of the words $w_k$ defined as:
  
$$
w_k = \left( \prod_{i=2}^{k-1} (s_i \cdot e_i) \right) \cdot q_k
$$
  
  where:
  
  - $s_i = a b^i a a$
  - $e_i = a b^i a b a^{i-2}$
  - $q_k = a b^k a$

---

### ES5 – Universal Integer Codes
Write a program to compute all studied universal integer codes (encoding and decoding):
- Binary, gamma, delta, Fibonacci codes.
- Rice codes for `k = 5` and `k = 7`.

Perform experiments:
- Number of bits to encode 100 integers between 1 and 100,000.
- Number of bits to compress 100 random integers between 1 and 1000.
- Number of bits to encode 1000 integers with a predefined distribution.

---

### ES6 – RE-PAIR Grammar
Write a program that, given a string `T`, constructs the grammar produced by the RE-PAIR algorithm. Also implement grammar construction in **Chomsky Normal Form**.

Compute the size of the grammar in both cases.

---

### Sensitivity Analysis
- **Multiplicative sensitivity of measure r**
  A morphism generates repetitive strings: each letter of an alphabet is mapped to a word, closed under concatenation.
  Example (binary alphabet $\{a, b\}$):
  
$$
\mu(a) = aab, \quad \mu(b) = bb
$$
$$
\mu(aab) = \mu(a)\mu(a)\mu(b) = \text{aab aab bb}
$$

- Define a function computing the **BWT multiplicative sensitivity** of a morphism:
  
$$
\text{MS}_{\mu}(n) = \max { \frac{r(\mu(w))}{r(w)} \Big| w \in \Sigma^n }
$$

  where $r$ is the number of equal-letter runs from BWT, and $\Sigma^n$ is the set of all words of length $n$ over $\Sigma = \{a, b\}$.

- Graphically describe how $\text{MS}_{\mu}(n)$ varies for $n \geq 2$.
