# Sequence algorithms

## Table of contents

* [Longest increasing subsequence](#longest-increasing-subsequence)
* [Sorting](#sorting)
	* [Comparison sorting](#comparison-sorting)
* [String searching](#string-searching)

---

## Longest increasing subsequence

> Longest increasing subsequence problem is a task to find the longest monotonically increasing subsequence (not necessarily contiguous) within a given sequence.

:memo: **Notes**

* The dynamic programming solution (without additional tricks) has running time `O(N^2)`, and is not the most efficient one. The problem can be solved in `O(N log N)` time using an algorithm based on binary search. This algorithm is output-sensitive: if the size of the output, the length `K` of a subsequence, is taken into account, it requires `O(N log K)` time.
* Any comparison-based algorithm has worst-case running time `Ω(N log N)`.

:link: **Webpages**

* [Longest increasing subsequence &ndash; Wikipedia](https://en.wikipedia.org/wiki/Longest_increasing_subsequence)
* [Longest increasing subsequence &ndash; CP-Algorithms](https://cp-algorithms.com/sequences/longest_increasing_subsequence.html)

:movie_camera: **Videos**

* MIT OCW 6.006 Introduction to algorithms (2011) &ndash; *Dynamic programming*\
[Watch at YouTube](https://www.youtube.com/watch?v=1ivFSH0ijOM&t=2570) (from 42:50) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:book: **Books**

* S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008 &ndash; Sec. 8.3: *Longest increasing sequence*\
[Book website](http://www.algorist.com/)
* S.Halim, F.Halim. *Competitive Programming*. 3<sup>rd</sup> ed., 2013 &ndash; Sec. 3.5.2 *Classical examples*\
[Book website](https://cpbook.net/)

:page_facing_up: **Papers**

* M.L.Fredman. *On computing the length of longest increasing subsequences*. Discrete Mathematics **11**, [29](https://dx.doi.org/10.1016/0012-365X(75)90103-X) (1975)\
[Full text](https://dx.doi.org/10.1016/0012-365X(75)90103-X) |
[Full text (alternative source)](https://core.ac.uk/download/pdf/82290717.pdf)

<!--### Counting the number of longest increasing subsequences-->

## Sorting

### Comparison sorting

:page_facing_up: **Papers**

* J.L.Bentley, M.D.McIlroy. *Engineering a sort function.* Software: Practice and Experience **23**, [1249](https://dx.doi.org/10.1002/spe.4380231105) (1993)\
[Full text](https://cs.fit.edu/~pkc/classes/writing/samples/bentley93engineering.pdf)

## String searching

### Knuth&ndash;Morris&ndash;Pratt algorithm

:link: **Webpages**

* [Knuth–Morris–Pratt algorithm &ndash; Wikipedia](https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm)
