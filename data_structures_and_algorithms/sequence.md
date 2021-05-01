# Sequence data structures and algorithms <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Rotation (cyclic shift)](#rotation-cyclic-shift)
	- [Three reverses rotation algorithm](#three-reverses-rotation-algorithm)
	- [Gries–Mills algorithm](#griesmills-algorithm)
	- [Dolphin (juggling) algoirithm](#dolphin-juggling-algoirithm)
- [Circular buffer](#circular-buffer)
- [Longest increasing subsequence](#longest-increasing-subsequence)
- [Maximum subsequence](#maximum-subsequence)
	- [Kadane’s algorithm](#kadanes-algorithm)
- [Majority element](#majority-element)
	- [Boyer–Moore majority vote algorithm](#boyermoore-majority-vote-algorithm)
- [Sqrt decomposition](#sqrt-decomposition)

---

## Rotation (cyclic shift)

> A `K`-rotation (or a `K`-cyclic shift) of a sequence <code>{a<sub>0</sub>a<sub>2</sub>...a<sub>N-1</sub>}</code> is a sequence <code>{a<sub>P(1)</sub>a<sub>P(2)</sub>...a<sub>P(N-1)</sub>}</code>, where the index permutation is `P(i) = (i + K) % N`. Any non-zero rotation has no trivial cycles. The number of (non-trivial) cycles is `gcd(K, N)`.

:link:

- [*Benchmarking block-swapping algorithms* – Dr. Dobb’s Journal](http://www.drdobbs.com/parallel/benchmarking-block-swapping-algorithms/232900395)

:book:

- Sec. 11.3: *Rotation* – A.A.Stepanov, D.E.Rose. [*From mathematics to generic programming*](http://www.fm2gp.com/) (2014)
- Sec. 10.4: *Rotate algorithms* – A.A.Stepanov, P.McJones. [*Elements of programming*](http://elementsofprogramming.com/) (2009)
- Sec. 2.3: *The power of primitives* – J.Bentley. *Programming pearls* (1999)

:page_facing_up:

- C.A.Furia. *Rotation of sequences: Algorithms and proofs*. Preprint (2014).\
[Full text](https://arxiv.org/abs/1406.5453)
- D.Gries, H.Mills. *Swapping sections*. Technical report 81-452, Department of computer science, Cornell University, 1981.\
[Full text](https://hdl.handle.net/1813/6292)

### Three reverses rotation algorithm

> Gist of the algorithm: reverse the subsequences <code>{a<sub>0</sub>...a<sub>K-1</sub>}</code> and <code>{a<sub>K</sub>...a<sub>N-1</sub>}</code>, then reverse the whole sequence <code>{a<sub>K-1</sub>...a<sub>0</sub>a<sub>N-1</sub>...a<sub>K</sub>}</code>. The total number of swaps is <code>&lfloor;N/2&rfloor; + &lfloor;K/2&rfloor; + &lfloor;(N-K)/2&rfloor; &sim; N</code>. With 3 assignments per swap, the total number of assignments is <code>&sim; 3N</code>. This algorithm is typically used to implement `std::rotate` for bidirectional iterators.

### Gries–Mills algorithm

> Gist of the algorithm: if `K = N - K`, swap the subsequences <code>{a<sub>0</sub>...a<sub>K-1</sub>}</code> and <code>{a<sub>K</sub>...a<sub>N-1</sub>}</code>; if `K < N - K`, swap the subsequences <code>{a<sub>0</sub>...a<sub>K-1</sub>}</code> and <code>{a<sub>K</sub>...a<sub>2K-1</sub>}</code>, then proceed recursively for the suffix subsequence <code>{a<sub>0</sub>...a<sub>K-1</sub>a<sub>2K</sub>...a<sub>N-1</sub>}</code> with `K' = K`; if `K > N - K`, swap the subsequences <code>{a<sub>0</sub>...a<sub>N-K-1</sub>}</code> and <code>{a<sub>k</sub>...a<sub>N-1</sub>}</code>, then proceed recursively for the suffix subsequence <code>{a<sub>N-K</sub>...a<sub>K-1</sub>a<sub>0</sub>...a<sub>N-K-1</sub>}</code> with `K' = 2K - N`. The section sizes `(K, N - K)` form the same sequence as that obtained if the subtraction-based Euclidean algorithm is employed to calculate `gcd(K, N)`. The total number of swaps is `N - gcd(K, N)`. With 3 assignments per swap, the total number of assignments is `3[N - gcd(K, N)]`. The Gries–Mills algorithm can be implemented such that it only requires to move one step forward, so this algorithm is typically used to implement `std::rotate` for forward and random access iterators.

### Dolphin (juggling) algoirithm

> Gist of the algorithm: compute the number of cycles, `Nc = gcd(K, N - K)`; for each cycle <code>{a<sub>Ci(0)</sub>a<sub>Ci(1)</sub>a<sub>Ci(2)</sub>...}</code> with `Ci(j) = (i + jK) % N, i = 0, ..., Nc - 1`, make a cyclic shift of all the elements by one position to obtain <code>{a<sub>Ci(1)</sub>a<sub>Ci(2)</sub>...a<sub>Ci(0)</sub>}</code>. The total number of assignments is `N + gcd(K, N)`. However, this algorithm is not cache-friendly and can have poor performance in practice, although it makes much fewer (~2-3 times) memory accesses. This algorithm is sometimes used to implement `std::rotate` for random access iterators.

:page_facing_up:

- W.Fletcher, R.Silver. *Algorithm 284: Interchange of two blocks of data* – [Communications of the ACM **9**, 326](https://dx.doi.org/10.1145/355592.365609) (1966)

---

## Circular buffer

> A circular buffer (cyclic buffer, ring buffer) is a data structure that uses a single, fixed-size buffer as if it were connected end-to-end. When the buffer is filled, new data is written starting at the beginning of the buffer and overwriting the old.

:link:

- [*Circular buffer*](https://en.wikipedia.org/wiki/Circular_buffer) – Wikipedia
- B.Stout. [*“Olympic” filtering for noisy data](https://github.com/eugnsp/CUJ/blob/master/13.03/stout/stout.md) – C/C++ Users Journal **13** (1995)

:anchor:

- [*Boost.Circular Buffer: The circular buffer library*](https://www.boost.org/doc/libs/release/libs/circular_buffer/)

---

## Longest increasing subsequence

> Problem: find the longest monotonically increasing subsequence (not necessarily contiguous) within a given sequence. The dynamic programming solution (without additional tricks) has running time <code>O(N<sup>2</sup>)</code>, and is not the most efficient one. The problem can be solved in `O(N log N)` time using an algorithm based on binary search. This algorithm is output-sensitive: if the size of the output, the length `K` of a subsequence, is taken into account, it requires `O(N log K)` time. Any comparison-based algorithm requires at least <code>N log<sub>2</sub> N - N log<sub>2</sub> log<sub>2</sub> N + O(N)</code> comparisons in the worst case.

:link:

- [*Longest increasing subsequence*](https://en.wikipedia.org/wiki/Longest_increasing_subsequence) – Wikipedia
- [*Longest increasing subsequence*](https://cp-algorithms.com/sequences/longest_increasing_subsequence.html) – CP-Algorithms

:movie_camera:

- [*Dynamic programming*](https://www.youtube.com/watch?v=1ivFSH0ijOM&t=2570) – MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

:book:

- Sec. 8.3: *Longest increasing sequence* – S.S.Skiena. [*The algorithm design manual*](http://www.algorist.com/) (2008)
- Sec. 3.5.2 *Classical examples* – S.Halim, F.Halim. [*Competitive programming*](https://cpbook.net/) (2013)
- Sec. 6.5.2: *Finding the k<sup>th</sup> smallest element*, Sec. 6.11.1: *Longest increasing subsequence* – U.Manber. *Introduction to algorithms: A creative approach* (1989)

:page_facing_up:

- M.L.Fredman. [*On computing the length of longest increasing subsequences*](https://core.ac.uk/download/pdf/82290717.pdf) – [Discrete Mathematics **11**, 29](https://dx.doi.org/10.1016/0012-365X(75)90103-X) (1975)

<!--### Counting the number of longest increasing subsequences-->

---

## Maximum subsequence

> Problem: find a contiguous subsequence with the largest sum within a given one-dimensional sequence.

:book:

- Col. 8: *Searching* – J.Bentley. [*Algorithm design techniques*](https://www.oreilly.com/library/view/programming-pearls-second/9780134498058/) (1999)

:page_facing_up:

- J.Bentley. [*Programming pearls: Algorithm design techniques*](http://akira.ruc.dk/~keld/teaching/algoritmedesign_f03/Artikler/05/Bentley84.pdf) – [Communications of the ACM *27*, 865](https://dx.doi.org/10.1145/358234.381162) (1984)

### Kadane’s algorithm

:page_facing_up:

- D.Gries. [*A note on a standard strategy for developing loop invariants and loops*](https://core.ac.uk/download/pdf/82596333.pdf) – [Science of computer programming *2*, 207](https://dx.doi.org/10.1016/0167-6423(83)90015-1) (1982)

---

## Majority element

### Boyer–Moore majority vote algorithm

:link:

- [*Boyer–Moore majority vote algorithm*](https://en.wikipedia.org/wiki/Boyer%E2%80%93Moore_majority_vote_algorithm) – Wikipedia

---

## Sqrt decomposition

:link:

- [*Sqrt decomposition*](https://cp-algorithms.com/data_structures/sqrt_decomposition.html) – CP-Algorithms
- S.Kopeliovich. [*Sqrt decomposition*](http://acm.math.spbu.ru/~sk1/mm/lections/mipt2016-sqrt/mipt-2016-burunduk1-sqrt.en.pdf) – MIPT (2016)
