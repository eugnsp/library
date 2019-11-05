# Dynamic programming <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [General information](#general-information)
- [Linear partition](#linear-partition)
- [Longest increasing subsequence](#longest-increasing-subsequence)

---

## General information

:movie_camera:

- *Dynamic programming.* [Part I](https://www.youtube.com/watch?v=OQ5jsbhAv_M), [Part II](https://www.youtube.com/watch?v=ENyox7kNKeY), [Part III](https://www.youtube.com/watch?v=ocZMDMZwhCY), [Part IV](https://www.youtube.com/watch?v=tp4_UXaVyx8) &ndash; MIT 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

:book:

- Ch. 8: *Dynamic programming* &ndash; S.S.Skiena. [*The algorithm design manual*](http://www.algorist.com/) (2008)

---

## Linear partition

> Problem: partition (without reordering) a set of non-negative integral numbers into `k` ranges such that the maximum sum over all the ranges is minimized.

:memo:

- This problem has another solution based on binary searching the answer in the space of possible answers that is obtained using a greedy approach.

:book:

- Sec. 8.5: *The partition problem* &ndash; S.S.Skiena. [*The algorithm design manual*](http://www.algorist.com/) (2008)
- Sec. 8.4.1: *Two components: Binary search the answer and other* &ndash; S.Halim, F.Halim. [*Competitive programming*](https://cpbook.net/) (2013)

---

## Longest increasing subsequence

See [Sequence algorithms &ndash; Longest increasing subsequence](sequence_algorithms.md#longest-increasing-subsequence).


<!--
Maximum square in bool matrix:

- D.Gries. *A note on a standard strategy for developing loop invariants and loops*. Science of computer programming *2*, [207](https://dx.doi.org/10.1016/0167-6423(83)90015-1) (1982).\
[Full text](https://core.ac.uk/download/pdf/82596333.pdf)

https://dl.acm.org/citation.cfm?id=800754
 -->
