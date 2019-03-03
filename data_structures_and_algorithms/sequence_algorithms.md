# Sequence algorithms

## Table of contents

* [Longest increasing subsequence](#longest-increasing-subsequence)
* [Sorting](#sorting)
	* [Comparison sorting](#comparison-sorting)
	* [Order statistics](#order-statistics)
		* [Second smallest element](#second-smallest-element)
* [String searching](#string-searching)
	* [Knuth&ndash;Morris&ndash;Pratt algorithm](#knuthmorrispratt-algorithm)

---

## Longest increasing subsequence

> Problem: find the longest monotonically increasing subsequence (not necessarily contiguous) within a given sequence.

:memo: **Notes**

* The dynamic programming solution (without additional tricks) has running time <code>O(N<sup>2</sup>)</code>, and is not the most efficient one. The problem can be solved in `O(N log N)` time using an algorithm based on binary search. This algorithm is output-sensitive: if the size of the output, the length `K` of a subsequence, is taken into account, it requires `O(N log K)` time.
* Any comparison-based algorithm requires at least <code>N log<sub>2</sub> N - N log<sub>2</sub> log<sub>2</sub> N + O(N)</code> comparisons in the worst case.

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
* U.Manber. *Introduction to algorithms: A creative approach*. Addison-Wesley, 1989 &ndash; Sec. 6.5.2: *Finding the k<sup>th</sup> smallest element*, Sec. 6.11.1: *Longest increasing subsequence*

:page_facing_up: **Papers**

* M.L.Fredman. *On computing the length of longest increasing subsequences*. Discrete Mathematics **11**, [29](https://dx.doi.org/10.1016/0012-365X(75)90103-X) (1975)\
[Full text](https://dx.doi.org/10.1016/0012-365X(75)90103-X),
[Full text (alternative source)](https://core.ac.uk/download/pdf/82290717.pdf)

<!--### Counting the number of longest increasing subsequences-->

## Sorting

### Comparison sorting

> In comparison sorting one may compare two element (checking whether <code>a<sub>i</sub></code> < <code>a<sub>j</sub></code>). Other operations on element (e.g., using them as indices) are not allowed.

:page_facing_up: **Papers**

* J.L.Bentley, M.D.McIlroy. *Engineering a sort function*. Software: Practice and experience **23**, [1249](https://dx.doi.org/10.1002/spe.4380231105) (1993)\
[Full text](https://cs.fit.edu/~pkc/classes/writing/samples/bentley93engineering.pdf)

### Order statistics

> The k<sup>th</sup> order statistic of an array is its k<sup>th</sup> smallest element.

:memo: **Notes**

* Any comparison-based algorithm of finding the smallest element in an array of size `N` requires at least `N - 1` comparisons in the worst case.
* Any comparison-based algorithm of finding both the smallest and the largest elements in an array of size `N` requires at least `⌈3N / 2⌉ - 1` comparisons in the worst case.
* Any comparison-based algorithm of finding both the smallest and the second smallest element in an array of size `N` requires at least <code>N + &lceil;log<sub>2</sub> N&rceil; - 2</code> comparisons in the worst case.

:link: **Webpages**

* [Selection and order statistics &ndash; ICS 161: Design and analysis of algorithms (1996)](https://www.ics.uci.edu/~eppstein/161/960125.html)
* [Sample proofs involving selection problems &ndash; COMP 363: Design and analysis of computer algorithms (2003)](http://cs.slu.edu/~goldwasser/class/loyola/comp363/2003_Spring/handouts/selectionproofs.pdf)
* [Lower bounds and optimality &ndash; COMP 2011/2711: Data organisation (2006)](https://www.cse.unsw.edu.au/~cs2011/lect/2711_Adversary.pdf)

:movie_camera: **Videos**

* MIT OCW 6.046J/18.410J: Introduction to algorithms (2005) &ndash; *Order statistics, median*\
[Watch at YouTube](https://www.youtube.com/watch?v=mR_RUjsJnV8) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-introduction-to-algorithms-sma-5503-fall-2005/)
* Alexander Stepanov: Efficient programming with components (2013) &ndash; Lectures 6-10: *Finding the smallest and second smallest elements*\
[Watch at YouTube](https://www.youtube.com/watch?v=lWSYE-hRw0s&list=PLHxtyCq_WDLXryyw91lahwdtpZsmo4BGD) (subsequent lectures are in the playlist)

:book: **Books**

* T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009 &ndash; Ch. 9: *Medians and order statistics*\
[Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
* U.Manber. *Introduction to algorithms: A creative approach*. Addison-Wesley, 1989 &ndash; Sec. 6.5.2: *Finding the k<sup>th</sup> smallest element*, Sec. 6.11.2: *Finding the two largest elements in a set*
* A.V.Aho, J.E.Hopcroft, J.D.Ullman. *The design and analysis of computer algorithms*. Addison-Wesley, 1974 &ndash; Sec. 3.6: *Order statistics*, Sec. 3.7: *Expected time for order statistics*

:page_facing_up: **Papers**

* S.S.Kislitsyn. *On the selection of the `k`<sup>th</sup> element of an ordered set by pairwise comparison*. Sibirsky matematichesky zhurnal **5**, 557 (1964)\
[Full text (russian)](https://gdz.sub.uni-goettingen.de/id/PPN394039319_0005?tify={%22pages%22:[559]})

## String searching

### Knuth&ndash;Morris&ndash;Pratt algorithm

:link: **Webpages**

* [Knuth&ndash;Morris&ndash;Pratt algorithm &ndash; Wikipedia](https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm)
