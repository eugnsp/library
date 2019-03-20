# Sorting

## Table of contents

* [Comparison sorting](#comparison-sorting)
	* [Insertion sort](#insertion-sort)
	* [Selection sort](#selection-sort)
	* [Heap sort](#heap-sort)
	* [Merge sort](#merge-sort)
		* [Inversions counting](#inversions-counting)
* [Order statistics](#order-statistics)

---

## Comparison sorting

> In comparison sorting one may compare two element (checking whether <code>a<sub>i</sub></code> < <code>a<sub>j</sub></code>). Other operations on element (e.g., using them as indices) are not allowed.

:memo: **Notes**

* For practical applications one should always consider constant factors hidden in the big-`O` notation. Typically, <code>O(n<sup>2</sup>)</code> algorithms (e.g., insertion sort) are faster than `O(n log n)` ones (e.g., quick sort) for small inputs. For example, `std::sort` implementation in `stdlibc++` resorts to the insertion sort if the input size doesn't exceed `16` elements, and Microsoft's implementation uses the value `32`.

:page_facing_up: **Papers**

* J.L.Bentley, M.D.McIlroy. *Engineering a sort function*. Software: Practice and experience **23**, [1249](https://dx.doi.org/10.1002/spe.4380231105) (1993).\
[Full text](https://cs.fit.edu/~pkc/classes/writing/samples/bentley93engineering.pdf)

:dizzy: **Visualizations**

* [Comparison sorting algorithms visualization](https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html)

### Insertion sort

> At each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted list, and inserts it there. It repeats until no input elements remain.

:memo: **Notes**

* Insertion sort is commonly used to sort a small number of elements. It is employed in many `std::sort` implementations as a final step of recursion when a sub-range is small enough.

:book: **Books**

* Ch. 9: *Medians and order statistics* &ndash; T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009.\
[Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
* Ch. 8: *Elementary sorting methods* &ndash; R.Sedgewick. *Algorithms*. Addison-Wesley, 1983.

### Selection sort

:memo: **Notes**

* Selection sort makes only `O(n)` writes in the average and the worst cases, and is useful when writes are significantly more expensive than reads, e.g. when elements have small keys and very large associated data or when elements are stored in flash memory.

:link: **Webpages**

* [Selection sort &ndash; Wikipedia](https://en.wikipedia.org/wiki/Selection_sort)

:book: **Books**

* R.Sedgewick. *Algorithms*. Addison-Wesley, 1983 &ndash; Ch. 8: *Elementary sorting methods*.

### Heap sort

:wrench: **Applications**

* Implementation of `std::partial_sort` that rearranges a given range such that `k` smallest elements become the first `k` elements of the range, in sorted order.

## Order statistics

> The `k`<sup>th</sup> order statistic of an array is its `k`<sup>th</sup> smallest element.

:memo: **Notes**

* Any comparison-based algorithm of finding the smallest element in an array of size `n` requires at least `n - 1` comparisons in the worst case.
* Any comparison-based algorithm of finding both the smallest and the largest elements in an array of size `n` requires at least `⌈3n / 2⌉ - 1` comparisons in the worst case.
* Any comparison-based algorithm of finding both the smallest and the second smallest element in an array of size `n` requires at least <code>N + &lceil;log<sub>2</sub> N&rceil; - 2</code> comparisons in the worst case.

:link: **Webpages**

* [Selection and order statistics &ndash; ICS 161: Design and analysis of algorithms (1996)](https://www.ics.uci.edu/~eppstein/161/960125.html)
* [Sample proofs involving selection problems &ndash; COMP 363: Design and analysis of computer algorithms (2003)](http://cs.slu.edu/~goldwasser/class/loyola/comp363/2003_Spring/handouts/selectionproofs.pdf)
* [Lower bounds and optimality &ndash; COMP 2011/2711: Data organisation (2006)](https://www.cse.unsw.edu.au/~cs2011/lect/2711_Adversary.pdf)

:movie_camera: **Videos**

* *Order statistics, median* &ndash; MIT OCW 6.046J/18.410J: Introduction to algorithms (2005).\
[Watch at YouTube](https://www.youtube.com/watch?v=mR_RUjsJnV8) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-introduction-to-algorithms-sma-5503-fall-2005/)
* Lectures 6-10: *Finding the smallest and second smallest elements* &ndash; Alexander Stepanov: Efficient programming with components (2013).\
[Watch at YouTube](https://www.youtube.com/watch?v=lWSYE-hRw0s&list=PLHxtyCq_WDLXryyw91lahwdtpZsmo4BGD) (subsequent lectures are in the playlist)

:book: **Books**

* Ch. 9: *Medians and order statistics* &ndash; T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009.\
[Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
* Sec. 6.5.2: *Finding the k<sup>th</sup> smallest element*, Sec. 6.11.2: *Finding the two largest elements in a set* &ndash; U.Manber. *Introduction to algorithms: A creative approach*. Addison-Wesley, 1989.
* Sec. 3.6: *Order statistics*, Sec. 3.7: *Expected time for order statistics* &ndash; A.V.Aho, J.E.Hopcroft, J.D.Ullman. *The design and analysis of computer algorithms*. Addison-Wesley, 1974.

:page_facing_up: **Papers**

* S.S.Kislitsyn. *On the selection of the k<sup>th</sup> element of an ordered set by pairwise comparison*. Sibirsky matematichesky zhurnal **5**, 557 (1964).\
[Full text (russian)](https://gdz.sub.uni-goettingen.de/id/PPN394039319_0005?tify={%22pages%22:[559]})

### Merge sort

:wrench: **Applications**

* Sorting linked lists.
* External sorting of data that doesn't fit into memory.

:link: **Webpages**

* [Merge sort &ndash; Wikipedia](https://en.wikipedia.org/wiki/Merge_sort)

#### Inversions counting

> Problem: count the number of inversions in a permutation <code>P = (a<sub>1</sub>, ..., a<sub>n</sub>)</code>, i.e. the number of pairs <code>(a<sub>i</sub></code>, <code>a<sub>j</sub>)</code> with `i < j` and <code>a<sub>i</sub> &gt; a<sub>j</sub></code>.

:memo: **Notes**

* The minimum number of adjacent swaps required to sort a permutation `P` (i.e. convert it into the identity one) is equal to the number of inversions in `P`.

:link: **Webpages**

* [Counting inversions in a permutation &ndash; CS 122: Algorithm design and analysis (2010)](https://en.wikipedia.org/wiki/Merge_sort)

:movie_camera: **Videos**

* *Counting the number of inversions in a permutation* &ndash; CS 122: Algorithm design and analysis (2010).\
[Watch at YouTube](https://www.youtube.com/watch?v=Vj5IOD7A6f8) |
[Course website](http://web.cs.ucdavis.edu/~gusfield/cs122f10/)

:book: **Books**

* Sec. 5.3.: *Counting inversions* &ndash; J.Kleinberg, E.Tardos. *Algorithm design*. Pearson, 2005.\
[Book website](https://www.pearson.com/us/higher-education/program/Kleinberg-Algorithm-Design/PGM319216.html)

<!--* The minimum number of adjacent swaps required to sort a permutation `P` (i.e. convert into the identity one) is equal to the number of inversions in `P`. The minimum number of swaps, not necessarily adjacent, is equal to the size of `P` minus the number of cycles in `P`.-->
