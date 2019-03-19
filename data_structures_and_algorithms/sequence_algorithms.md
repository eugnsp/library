# Sequence algorithms

## Table of contents

* [Rotation (cyclic shift)](#rotation-cyclic-shift)
	* [Three reverses rotation](#three-reverses-rotation)
	* [Lexicographically minimal rotation](#lexicographically-minimal-string-rotation)
		* [Duval's based algorithm](#duvals-based-algorithm)
* [Longest increasing subsequence](#longest-increasing-subsequence)
* [Lyndon factorization](#lyndon-factorization)
	* [Duval's algorithm](#duvals-algorithm)
* [String searching](#string-searching)
	* [Knuth&ndash;Morris&ndash;Pratt algorithm](#knuthmorrispratt-algorithm)

---

## Rotation (cyclic shift)

> A `k`-rotation (or a `k`-cyclic shift) of a sequence <code>(a<sub>0</sub>, a<sub>2</sub>, ... a<sub>n-1</sub>)</code> is a sequence <code>(a<sub>P(1)</sub>, a<sub>P(2)</sub>, ..., a<sub>P(n-1)</sub>)</code>, where the index permutation is `P(i) = (i - k) % n`.

:book: **Books**

* Sec. 10.4: *Rotate algorithms* &ndash; A.A.Stepanov, P.McJones. *Elements of programming*. Addison-Wesley, 2009.\
[Book website](http://elementsofprogramming.com/)

### Three reverses rotation

> Gist of the algorithm: to rotate a sequence <code>(a<sub>0</sub>, ..., a<sub>k</sub>, ... a<sub>n-1</sub>)</code> into <code>(a<sub>k</sub>, ..., a<sub>n-1</sub>, a<sub>0</sub>, ..., a<sub>k-1</sub>)</code>, first reverse the subsequences <code>(a<sub>0</sub>, ..., a<sub>k-1</sub>)</code> and <code>(a<sub>k</sub>, ... a<sub>n-1</sub>)</code>, then reverse the whole sequence <code>(a<sub>k-1</sub>, ..., a<sub>0</sub>, a<sub>n-1</sub>, ..., a<sub>k</sub>)</code>.

:memo: **Notes**

* This algorithm is typically used to implement `std::rotate` for bidirectional iterators.

### Lexicographically minimal string rotation

> Problem: find the rotation of a string possessing the lowest lexicographical order of all such rotations.

:link: **Webpages**

[Lexicographically minimal string rotation &ndash; Wikipedia](https://en.wikipedia.org/wiki/Lexicographically_minimal_string_rotation)

#### Duval's based algorithm

:memo: **Notes**

* This algorithm is also known as the Zhou Yuan's minimal expression algorithm.

:link: **Webpages**

* [Lyndon factorization &ndash; CP-Algorithms](https://cp-algorithms.com/string/lyndon_factorization.html)
* [How does the minimum expression algorithm by Zhou Yuan work? &ndash; Quora](https://www.quora.com/How-does-the-minimum-expression-algorithm-by-Zhou-Yuan-work)

## Longest increasing subsequence

> Problem: find the longest monotonically increasing subsequence (not necessarily contiguous) within a given sequence.

:memo: **Notes**

* The dynamic programming solution (without additional tricks) has running time <code>O(n<sup>2</sup>)</code>, and is not the most efficient one. The problem can be solved in `O(n log n)` time using an algorithm based on binary search. This algorithm is output-sensitive: if the size of the output, the length `k` of a subsequence, is taken into account, it requires `O(n log k)` time.
* Any comparison-based algorithm requires at least <code>n log<sub>2</sub> n - n log<sub>2</sub> log<sub>2</sub> n + O(n)</code> comparisons in the worst case.

:link: **Webpages**

* [Longest increasing subsequence &ndash; Wikipedia](https://en.wikipedia.org/wiki/Longest_increasing_subsequence)
* [Longest increasing subsequence &ndash; CP-Algorithms](https://cp-algorithms.com/sequences/longest_increasing_subsequence.html)

:movie_camera: **Videos**

* *Dynamic programming* &ndash; MIT OCW 6.006 Introduction to algorithms (2011).\
[Watch at YouTube](https://www.youtube.com/watch?v=1ivFSH0ijOM&t=2570) (from 42:50) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:book: **Books**

* Sec. 8.3: *Longest increasing sequence* &ndash; S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008.\
[Book website](http://www.algorist.com/)
* Sec. 3.5.2 *Classical examples* &ndash; S.Halim, F.Halim. *Competitive Programming*. 3<sup>rd</sup> ed., 2013.\
[Book website](https://cpbook.net/)
* Sec. 6.5.2: *Finding the k<sup>th</sup> smallest element*, Sec. 6.11.1: *Longest increasing subsequence* &ndash; U.Manber. *Introduction to algorithms: A creative approach*. Addison-Wesley, 1989.

:page_facing_up: **Papers**

* M.L.Fredman. *On computing the length of longest increasing subsequences*. Discrete Mathematics **11**, [29](https://dx.doi.org/10.1016/0012-365X(75)90103-X) (1975).\
[Full text](https://dx.doi.org/10.1016/0012-365X(75)90103-X),
[Full text (alternative source)](https://core.ac.uk/download/pdf/82290717.pdf)

<!--### Counting the number of longest increasing subsequences-->

## Lyndon factorization

> Lyndon word is a (non-empty) string that is strictly smaller in lexicographic order than all of its rotations. Lyndon factorization is a decomposition of a string `s` into Lyndon words, <code>s = w<sub>1</sub>w<sub>2</sub>...w<sub>n</sub></code>, such that <code>w<sub>1</sub> &ge; w<sub>i</sub> &ge; ... &ge; w<sub>n</sub></code>.

:memo: **Notes**

* An algorithm for Lyndon factorization can be used to find the lexicographically minimal string rotation. See [Lexicographically minimal string rotation](#lexicographically-minimal-string-rotation).

:link: **Webpages**

* [Lyndon word &ndash; Wikipedia](https://en.wikipedia.org/wiki/Lyndon_word)

### Duval's algorithm

:link: **Webpages**

* [Lyndon factorization &ndash; CP-Algorithms](https://cp-algorithms.com/string/lyndon_factorization.html)

:page_facing_up: **Papers**

* J.P.Duval. *Factorizing words over an ordered alphabet*. Journal of algorithms **8**, [363](https://dx.doi.org/10.1016/0196-6774(83)90017-2) (1983).
* S.S.Ghuman, E.Giaquinta, J.Tarhio. *Alternative algorithms for Lyndon factorization*. Preprint (2014).\
[arXiv preprint](https://arxiv.org/abs/1405.4892)

## String searching

### Knuth&ndash;Morris&ndash;Pratt algorithm

:link: **Webpages**

* [Knuth&ndash;Morris&ndash;Pratt algorithm &ndash; Wikipedia](https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm)

:movie_camera: **Videos**

* *KMP searching algorithm* &ndash; William Brinkman (2017).\
[Watch at YouTube](https://www.youtube.com/watch?v=y2b94AxPlF8)
