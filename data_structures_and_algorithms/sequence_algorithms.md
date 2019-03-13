# Sequence algorithms

## Table of contents

* [Longest increasing subsequence](#longest-increasing-subsequence)
* [String searching](#string-searching)
	* [Knuth&ndash;Morris&ndash;Pratt algorithm](#knuthmorrispratt-algorithm)

---

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

## String searching

### Knuth&ndash;Morris&ndash;Pratt algorithm

:link: **Webpages**

* [Knuth&ndash;Morris&ndash;Pratt algorithm &ndash; Wikipedia](https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm)
