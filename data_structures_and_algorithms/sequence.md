# Sequence algorithms

## Table of contents

* [Rotation (cyclic shift)](#rotation-cyclic-shift)
	* [Three reverses rotation algorithm](#three-reverses-rotation-algorithm)
	* [Gries&ndash;Mills algorithm](#gries-mills-algorithm)
	* [Dolphin algoirithm](#dolphin-algoirithm)
	* [Lexicographically minimal rotation](#lexicographically-minimal-string-rotation)
		* [Duval's based algorithm](#duvals-based-algorithm)
* [Longest increasing subsequence](#longest-increasing-subsequence)
* [Lyndon factorization](#lyndon-factorization)
	* [Duval's algorithm](#duvals-algorithm)
* [Maximum subsequence](#maximum-subsequence)
	* [Kadane's algorithm](#kadanes-algorithm)
* [Majority element](#majority-element)
	* [Boyer&ndash;Moore majority vote algorithm](#boyer-moore-majority-vote-algorithm)
* [Permutations](#permutations)
	* [Random permutations](#random-permutations)
		* [Fisher&ndash;Yates AKA Knuth shuffle algoritm](#fisheryates-aka-knuth-shuffle-algoritm)
* [String searching](#string-searching)
	* [Knuth&ndash;Morris&ndash;Pratt algorithm](#knuthmorrispratt-algorithm)
* [Sqrt decomposition]
---

## Rotation (cyclic shift)

> A `k`-rotation (or a `k`-cyclic shift) of a sequence <code>(a<sub>0</sub>a<sub>2</sub>...a<sub>n-1</sub>)</code> is a sequence <code>(a<sub>P(1)</sub>a<sub>P(2)</sub>...a<sub>P(n-1)</sub>)</code>, where the index permutation is `P(i) = (i + k) % n`.

:memo:

* Any non-zero rotation has no trivial cycles. The number of (non-trivial) cycles is `gcd(k, n)`.

:link:

* [Benchmarking block-swapping algorithms &ndash; Dr. Dobb's Journal](http://www.drdobbs.com/parallel/benchmarking-block-swapping-algorithms/232900395)

:book:

* Sec. 11.3: *Rotation* &ndash; A.A.Stepanov, D.E.Rose. *From mathematics to generic programming*. Addison-Wesley, 2014.\
[Book website](http://www.fm2gp.com/)
* Sec. 10.4: *Rotate algorithms* &ndash; A.A.Stepanov, P.McJones. *Elements of programming*. Addison-Wesley, 2009.\
[Book website](http://elementsofprogramming.com/)
* Sec. 2.3: *The power of primitives* &ndash; J.Bentley. *Programming pearls*. Addison-Wesley, 2<sup>nd</sup> ed., 1999.

:page_facing_up:

* C.A.Furia. *Rotation of sequences: Algorithms and proofs*. Preprint (2014).\
[Full text](https://arxiv.org/abs/1406.5453)
* D.Gries, H.Mills. *Swapping sections*. Technical report 81-452, Department of computer science, Cornell University, 1981.\
[Full text](https://hdl.handle.net/1813/6292)

### Three reverses rotation algorithm

> Gist of the algorithm: reverse the subsequences <code>(a<sub>0</sub>...a<sub>k-1</sub>)</code> and <code>(a<sub>k</sub>...a<sub>n-1</sub>)</code>, then reverse the whole sequence <code>(a<sub>k-1</sub>...a<sub>0</sub>a<sub>n-1</sub>...a<sub>k</sub>)</code>.

:memo:

* The total number of swaps is <code>&lfloor;n/2&rfloor; + &lfloor;k/2&rfloor; + &lfloor;(n-k)/2&rfloor; &sim; n</code>. With 3 assignments per swap, the total number of assignments is <code>&sim; 3n</code>.
* This algorithm is typically used to implement `std::rotate` for bidirectional iterators.

### Gries&ndash;Mills algorithm

> Gist of the algorithm: if `k = n - k`, swap the subsequences <code>(a<sub>0</sub>...a<sub>k-1</sub>)</code> and <code>(a<sub>k</sub>...a<sub>n-1</sub>)</code>; if `k < n - k`, swap the subsequences <code>(a<sub>0</sub>...a<sub>k-1</sub>)</code> and <code>(a<sub>k</sub>...a<sub>2k-1</sub>)</code>, then proceed recursively for the suffix subsequence <code>(a<sub>0</sub>...a<sub>k-1</sub>a<sub>2k</sub>...a<sub>n-1</sub>)</code> with `k' = k`; if `k > n - k`, swap the subsequences <code>(a<sub>0</sub>...a<sub>n-k-1</sub>)</code> and <code>(a<sub>k</sub>...a<sub>n-1</sub>)</code>, then proceed recursively for the suffix subsequence <code>(a<sub>n-k</sub>...a<sub>k-1</sub>a<sub>0</sub>...a<sub>n-k-1</sub>)</code> with `k' = 2k - n`.

:memo:

* The section sizes `(k, n - k)` form the same sequence as that obtained if the subtraction-based Euclidean algorithm is employed to calculate `gcd(k, n)`.
* The total number of swaps is `n - gcd(k, n)`. With 3 assignments per swap, the total number of assignments is `3[n - gcd(k, n)]`.
* The Gries&ndash;Mills algorithm can be implemented such that it only requires to move one step forward, so this algorithm is typically used to implement `std::rotate` for forward and random access iterators.

### Dolphin algoirithm

> Gist of the algorithm: compute the number of cycles, `nc = gcd(k, n - k)`; for each cycle <code>(a<sub>Ci(0)</sub>a<sub>Ci(1)</sub>a<sub>Ci(2)</sub>...)</code> with `Ci(j) = (i + jk) % n, i = 0, ..., nc - 1`, make a cyclic shift of all the elements by one position to obtain <code>(a<sub>Ci(1)</sub>a<sub>Ci(2)</sub>...a<sub>Ci(0)</sub>)</code>.

:memo:

* This algorithm is also known as the juggling algorithm.
* The total number of assignments is `n + gcd(k, n)`. However, this algorithm is not cache-friendly and can have poor performance in practice, although it makes much fewer (~2-3 times) memory accesses.
* This algorithm is sometimes used to implement `std::rotate` for random access iterators.

:page_facing_up:

W.Fletcher, R.Silver. *Algorithm 284: Interchange of two blocks of data*. Communications of the ACM **9**, [326](https://dx.doi.org/10.1145/355592.365609) (1966).

### Lexicographically minimal string rotation

> Lexicographically minimal rotation if the rotation of a string possessing the lowest lexicographical order of all its rotations.

:link:

* [Lexicographically minimal string rotation &ndash; Wikipedia](https://en.wikipedia.org/wiki/Lexicographically_minimal_string_rotation)

#### Duval's based algorithm

:memo:

* This algorithm is also known as the Zhou Yuan's minimal expression algorithm.

:link:

* [Lyndon factorization &ndash; CP-Algorithms](https://cp-algorithms.com/string/lyndon_factorization.html)
* [How does the minimum expression algorithm by Zhou Yuan work? &ndash; Quora](https://www.quora.com/How-does-the-minimum-expression-algorithm-by-Zhou-Yuan-work)

---

## Longest increasing subsequence

> Problem: find the longest monotonically increasing subsequence (not necessarily contiguous) within a given sequence.

:memo:

* The dynamic programming solution (without additional tricks) has running time <code>O(n<sup>2</sup>)</code>, and is not the most efficient one. The problem can be solved in `O(n log n)` time using an algorithm based on binary search. This algorithm is output-sensitive: if the size of the output, the length `k` of a subsequence, is taken into account, it requires `O(n log k)` time.
* Any comparison-based algorithm requires at least <code>n log<sub>2</sub> n - n log<sub>2</sub> log<sub>2</sub> n + O(n)</code> comparisons in the worst case.

:link:

* [Longest increasing subsequence &ndash; Wikipedia](https://en.wikipedia.org/wiki/Longest_increasing_subsequence)
* [Longest increasing subsequence &ndash; CP-Algorithms](https://cp-algorithms.com/sequences/longest_increasing_subsequence.html)

:movie_camera:

* *Dynamic programming* &ndash; MIT OCW 6.006: Introduction to algorithms (2011).\
[Watch at YouTube](https://www.youtube.com/watch?v=1ivFSH0ijOM&t=2570) (from 42:50) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:book:

* Sec. 8.3: *Longest increasing sequence* &ndash; S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008.\
[Book website](http://www.algorist.com/)
* Sec. 3.5.2 *Classical examples* &ndash; S.Halim, F.Halim. *Competitive Programming*. 3<sup>rd</sup> ed., 2013.\
[Book website](https://cpbook.net/)
* Sec. 6.5.2: *Finding the k<sup>th</sup> smallest element*, Sec. 6.11.1: *Longest increasing subsequence* &ndash; U.Manber. *Introduction to algorithms: A creative approach*. Addison-Wesley, 1989.

:page_facing_up:

* M.L.Fredman. *On computing the length of longest increasing subsequences*. Discrete Mathematics **11**, [29](https://dx.doi.org/10.1016/0012-365X(75)90103-X) (1975).\
[Full text](https://dx.doi.org/10.1016/0012-365X(75)90103-X) |
[Full text (alternative source)](https://core.ac.uk/download/pdf/82290717.pdf)

<!--### Counting the number of longest increasing subsequences-->

---

## Lyndon factorization

> Lyndon word is a (non-empty) string that is strictly smaller in lexicographic order than all of its rotations. Lyndon factorization is a decomposition of a string `s` into Lyndon words, <code>s = w<sub>1</sub>w<sub>2</sub>...w<sub>n</sub></code>, such that <code>w<sub>1</sub> &ge; w<sub>i</sub> &ge; ... &ge; w<sub>n</sub></code>.

:memo:

* An algorithm for Lyndon factorization can be used to find the lexicographically minimal string rotation. See [Lexicographically minimal string rotation](#lexicographically-minimal-string-rotation).

:link:

* [Lyndon word &ndash; Wikipedia](https://en.wikipedia.org/wiki/Lyndon_word)

### Duval's algorithm

:link:

* [Lyndon factorization &ndash; CP-Algorithms](https://cp-algorithms.com/string/lyndon_factorization.html)

:page_facing_up:

* J.P.Duval. *Factorizing words over an ordered alphabet*. Journal of algorithms **8**, [363](https://dx.doi.org/10.1016/0196-6774(83)90017-2) (1983).
* S.S.Ghuman, E.Giaquinta, J.Tarhio. *Alternative algorithms for Lyndon factorization*. Preprint (2014).\
[Full text](https://arxiv.org/abs/1405.4892)

---

## Maximum subsequence

> Problem: find a contiguous subsequence with the largest sum within a given one-dimensional sequence.

:page_facing_up:

* J.Bentley. *Programming pearls: Algorithm design techniques*. Communications of the ACM *27*, [865](https://dx.doi.org/10.1145/358234.381162) (1984).\
[Full text](http://akira.ruc.dk/~keld/teaching/algoritmedesign_f03/Artikler/05/Bentley84.pdf)

### Kadane's algorithm

* D.Gries. *A note on a standard strategy for developing loop invariants and loops*. Science of computer programming *2*, [207](https://dx.doi.org/10.1016/0167-6423(83)90015-1) (1982).\
[Full text](https://core.ac.uk/download/pdf/82596333.pdf)

---

## Majority element

### Boyer&ndash;Moore majority vote algorithm

:link:

* [Boyer&ndash;Moore majority vote algorithm &ndash; Wikipedia](https://en.wikipedia.org/wiki/Boyer%E2%80%93Moore_majority_vote_algorithm)

---

## Permutations

### Random permutations

#### Fisher&ndash;Yates AKA Knuth shuffle algoritm

:link:

* [*Fisher&ndash;Yates shuffle* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle)
* [*Knuth shuffle* &ndash; Rosetta Code](https://www.rosettacode.org/wiki/Knuth_shuffle)

---

## String searching

### Knuth&ndash;Morris&ndash;Pratt algorithm

:link:

* [Knuth&ndash;Morris&ndash;Pratt algorithm &ndash; Wikipedia](https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm)

:movie_camera:

* *KMP searching algorithm* &ndash; William Brinkman (2017).\
[Watch at YouTube](https://www.youtube.com/watch?v=y2b94AxPlF8)

---

## Sqrt decomposition

:link:

* [Sqrt decomposition [CP-Algorithms]](https://cp-algorithms.com/data_structures/sqrt_decomposition.html)
* [Sqrt decomposition [S.Kopeliovich, MIPT] (2016)](http://acm.math.spbu.ru/~sk1/mm/lections/mipt2016-sqrt/mipt-2016-burunduk1-sqrt.en.pdf)
