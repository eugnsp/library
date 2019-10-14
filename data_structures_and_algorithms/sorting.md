# Sorting algorithms

## Table of contents

* [Comparison sorting](#comparison-sorting)
	* [Insertion sort](#insertion-sort)
	* [Selection sort](#selection-sort)
	* [Heap sort](#heap-sort)
	* [Merge sort](#merge-sort)
		* [Inversions counting](#inversions-counting)
	* [Order statistics](#order-statistics)
* [Linear-time sorting](#linear-time-sorting)
	* [Count sort](#count-sort)
	* [Radix sort](#radix-sort)
* [Other algorithms](#other-algorithms)
	* [Pancake sorting](#pancake-sorting)
	* [Spreadsort](#spreadsort)
---

:link:

* [*Sort* &ndash; Boost libraries](https://www.boost.org/doc/libs/release/libs/sort/)

---

## Comparison sorting

> In comparison sorting one may compare two element (checking whether <code>a<sub>i</sub> &lt; a<sub>j</sub></code>). Other operations on element (e.g., using them as indices) are not allowed.

:memo:

* Any comparison-based algorithm of sorting an array of size `n` requires <code>&Omega;(n log n)</code> comparisons in the worst case. Determining the exact number of comparisons is a computationally hard problem even for small `n`. No simple formula for the solution is known.
* For practical applications one should always consider constant factors hidden in the big-`O` notation. Typically, <code>O(n<sup>2</sup>)</code> algorithms (e.g., insertion sort) are faster than `O(n log n)` ones (e.g., quick sort) for small inputs. For example, `std::sort` implementation in `stdlibc++` resorts to the insertion sort if the input size doesn't exceed `16` elements, and Microsoft's implementation uses the value `32`.

:link:

* [*Comparison sort*](https://en.wikipedia.org/wiki/Comparison_sort) &ndash; Wikipedia
* [*Minimal number of comparisons needed to sort `n` elements*](https://oeis.org/A036604) &ndash; The OEIS

:movie_camera:

* [*Lower bounds for sorting*](https://www.youtube.com/watch?v=Nz1KZXbghj8) &ndash; MIT OCW 6.006: Introduction to algorithms (2011)

:page_facing_up:

* J.L.Bentley, M.D.McIlroy. [*Engineering a sort function*](https://cs.fit.edu/~pkc/classes/writing/samples/bentley93engineering.pdf) &ndash; [Software: Practice and experience **23**, 1249](https://doi.org/10.1002/spe.4380231105) (1993)

:dizzy: **Visualizations**

* [Comparison sorting algorithms visualization](https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html)

### Insertion sort

> At each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted list, and inserts it there. It repeats until no input elements remain.

:memo:

* Insertion sort is commonly used to sort a small number of elements. It is employed in many `std::sort` implementations as a final step of recursion when a sub-range is small enough.

:book:

* Ch. 9: *Medians and order statistics* &ndash; T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)
* Ch. 8: *Elementary sorting methods*, Sec.: *Insertion sort* &ndash; R.Sedgewick. *Algorithms* (1983)

### Selection sort

:memo:

* Selection sort makes only `O(n)` writes in the average and the worst cases, and is useful when writes are significantly more expensive than reads, e.g. when elements have small keys and very large associated data or when elements are stored in flash memory.

:link:

* [*Selection sort* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Selection_sort)

:book:

* Ch. 8: *Elementary sorting methods*, Sec: *Selection sort* &ndash; R.Sedgewick. *Algorithms* (1983)

### Heap sort

:wrench: **Applications**

* Implementation of `std::partial_sort` that rearranges a given range such that `k` smallest elements become the first `k` elements of the range, in sorted order.

### Merge sort

:memo:

* Merge sort is useful for sorting linked lists and for external sorting of data that doesn't fit into main memory.

:link:

* [Merge sort &ndash; Wikipedia](https://en.wikipedia.org/wiki/Merge_sort)

#### Inversions counting

> Problem: count the number of inversions in a permutation <code>P = (a<sub>1</sub>, ..., a<sub>n</sub>)</code>, i.e. the number of pairs <code>(a<sub>i</sub></code>, <code>a<sub>j</sub>)</code> with `i < j` and <code>a<sub>i</sub> &gt; a<sub>j</sub></code>.

:memo:

* The minimum number of adjacent swaps required to sort a permutation `P` (i.e. convert it into the identity one) is equal to the number of inversions in `P`.

:link:

* [*Counting inversions in a permutation*](https://web.cs.ucdavis.edu/~gusfield/cs122/inversioncount.pdf) &ndash; CS 122A: [Algorithm design and analysis](https://web.cs.ucdavis.edu/~gusfield/cs122f10/) (2010)

:movie_camera:

* [*Counting the number of inversions in a permutation*](https://www.youtube.com/watch?v=Vj5IOD7A6f8) &ndash; CS 122A: [Algorithm design and analysis](https://web.cs.ucdavis.edu/~gusfield/cs122f10/) (2010)

:book:

* Sec. 5.3.: *Counting inversions* &ndash; J.Kleinberg, E.Tardos. [*Algorithm design*](https://www.pearson.com/us/higher-education/program/Kleinberg-Algorithm-Design/PGM319216.html) (2005)

<!--* The minimum number of adjacent swaps required to sort a permutation `P` (i.e. convert into the identity one) is equal to the number of inversions in `P`. The minimum number of swaps, not necessarily adjacent, is equal to the size of `P` minus the number of cycles in `P`.-->

### Order statistics

> The `k`<sup>th</sup> order statistic of an array is its `k`<sup>th</sup> smallest element.

:memo:

* Any comparison-based algorithm of finding the smallest element in an array of size `n` requires at least `n - 1` comparisons in the worst case.
* Any comparison-based algorithm of finding both the smallest and the largest elements in an array of size `n` requires at least `⌈3n / 2⌉ - 1` comparisons in the worst case.
* Any comparison-based algorithm of finding both the smallest and the second smallest element in an array of size `n` requires at least <code>N + &lceil;log<sub>2</sub> N&rceil; - 2</code> comparisons in the worst case.

:link:

* [Selection and order statistics](https://www.ics.uci.edu/~eppstein/161/960125.html) &ndash; ICS 161: [Design and analysis of algorithms](https://www.ics.uci.edu/~eppstein/161/) (1996)
* [Sample proofs involving selection problems](http://cs.slu.edu/~goldwasser/class/loyola/comp363/2003_Spring/handouts/selectionproofs.pdf) &ndash; COMP 363: Design and analysis of computer algorithms (2003)
* [Lower bounds and optimality](https://www.cse.unsw.edu.au/~cs2011/lect/2711_Adversary.pdf) &ndash; COMP 2011/2711: Data organisation (2006)

:movie_camera:

* [*Order statistics, median*](https://www.youtube.com/watch?v=mR_RUjsJnV8) &ndash; MIT OCW 6.046J/18.410J: Introduction to algorithms (2005)
* [Lectures 6-10: *Finding the smallest and second smallest elements*](https://www.youtube.com/watch?v=lWSYE-hRw0s&list=PLHxtyCq_WDLXryyw91lahwdtpZsmo4BGD) &ndash; Alexander Stepanov: Efficient programming with components (2013)

:book:

* Ch. 9: *Medians and order statistics* &ndash; T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)
* Sec. 6.5.2: *Finding the k<sup>th</sup> smallest element*, Sec. 6.11.2: *Finding the two largest elements in a set* &ndash; U.Manber. *Introduction to algorithms: A creative approach* (1989)
* Sec. 3.6: *Order statistics*, Sec. 3.7: *Expected time for order statistics* &ndash; A.V.Aho, J.E.Hopcroft, J.D.Ullman. *The design and analysis of computer algorithms* (1974)

:page_facing_up:

* S.S.Kislitsyn. [*On the selection of the k<sup>th</sup> element of an ordered set by pairwise comparison*](https://gdz.sub.uni-goettingen.de/id/PPN394039319_0005?tify={%22pages%22:[559]}) (in russian) &ndash; Sibirsky Matematichesky Zhurnal **5**, 557 (1964)

---

## Linear-time sorting

:movie_camera:

* [*Counting sort and radix sort*](https://www.youtube.com/watch?v=Nz1KZXbghj8&t=1966) &ndash; MIT OCW 6.006: Introduction to algorithms (2011)

### Count sort

### Radix sort

:link:

* [*Radix sort*](https://en.wikipedia.org/wiki/Radix_sort) &ndash; Wikipedia
* [*American flag sort*](https://en.wikipedia.org/wiki/American_flag_sort) &ndash; Wikipedia

:movie_camera:

* M.Skarupke. [*Sorting in less than `O(n log n)`: Generalizing and optimizing radix sort*](https://www.youtube.com/watch?v=zqs87a_7zxw) &ndash; C++ Now (2017)

---

## Other algorithms

### Pancake sorting

:memo:

* The problem of finding the shortest sequence of flips for a given stack of pancakes is NP-hard (L.Bulteau, G.Fertin, I.Rusu, 2011)

:link:

* [*Pancake sorting*](https://en.wikipedia.org/wiki/Pancake_sorting) &ndash; Wikipedia

### Spreadsort

:link:

* [*Spreadsort*](https://en.wikipedia.org/wiki/Spreadsort) &ndash; Wikipedia
* [*Spreadsort*](https://www.boost.org/doc/libs/1_71_0/libs/sort/doc/html/sort/single_thread/spreadsort.html) &ndash; Boost.Sort library
