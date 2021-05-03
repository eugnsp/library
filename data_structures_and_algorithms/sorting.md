# Sorting and searching algorithms <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
- [Comparison sorting](#comparison-sorting)
	- [Insertion sort](#insertion-sort)
	- [Selection sort](#selection-sort)
	- [Heap sort](#heap-sort)
	- [Merge sort](#merge-sort)
		- [Inversions counting](#inversions-counting)
	- [Quick sort](#quick-sort)
		- [Lomuto partition](#lomuto-partition)
		- [Hoare partition](#hoare-partition)
		- [“Fat pivot” partition / Dutch national flag problem](#fat-pivot-partition--dutch-national-flag-problem)
	- [Order statistics and quick select](#order-statistics-and-quick-select)
- [Linear-time sorting](#linear-time-sorting)
	- [Count sort](#count-sort)
	- [Radix sort](#radix-sort)
	- [Sorting by swapping](#sorting-by-swapping)
		- [Adjacent swaps](#adjacent-swaps)
		- [Arbitrary swaps](#arbitrary-swaps)
- [Other algorithms](#other-algorithms)
	- [Pancake sorting](#pancake-sorting)
	- [Spreadsort](#spreadsort)

---

## Introduction and overview

:anchor:

- [*Boost.Sort: The sorting library*](https://www.boost.org/doc/libs/release/libs/sort/)

---

## Comparison sorting

> In comparison sorting one may compare two element (checking whether <code>a<sub>i</sub> &lt; a<sub>j</sub></code>). Other operations on element (e.g., using them as indices) are not allowed. Any comparison-based algorithm of sorting an array of size `N` requires <code>&Omega;(N log N)</code> comparisons in the worst case. Determining the exact number of comparisons is a computationally hard problem even for small `N`. No simple formula for the solution is known. For practical applications one should always consider constant factors hidden in the big-`O` notation. Typically, <code>O(N<sup>2</sup>)</code> algorithms (e.g., insertion sort) are faster than `O(N log N)` ones (e.g., quick sort) for small inputs. For example, `std::sort` implementation in `libstdc++` resorts to the insertion sort if the input size doesn’t exceed `16` elements, and Microsoft’s implementation uses the value `32`.

:link:

- [*Comparison sort*](https://en.wikipedia.org/wiki/Comparison_sort) – Wikipedia
- [*Minimal number of comparisons needed to sort `n` elements*](https://oeis.org/A036604) – The OEIS

:grey_question:

- [*What is stability in sorting algorithms and why is it important?*](https://stackoverflow.com/q/1517793) – Stack Overflow

:movie_camera:

- [*Lower bounds for sorting*](https://www.youtube.com/watch?v=Nz1KZXbghj8) – MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/) (2011)

:book:

- Col. 11: *Sorting* – J.Bentley. [*Programming pearls*](https://www.oreilly.com/library/view/programming-pearls-second/9780134498058/) (1999)
- Sec. 5.6: *Sorting requires <code>&Omega;(n log n)</code> comparisons* – Roughgarden T. [*Algorithms illuminated (Part 1): The basics*](http://timroughgarden.org/books.html) – Soundlikeyourself Publishing (2017)

:page_facing_up:

- J.L.Bentley, M.D.McIlroy. [*Engineering a sort function*](https://cs.fit.edu/~pkc/classes/writing/samples/bentley93engineering.pdf) – [Software: Practice and experience **23**, 1249](https://doi.org/10.1002/spe.4380231105) (1993)

:dizzy:

- [*Comparison sorting algorithms visualization*](https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html)

### Insertion sort

> Insertion sort iterates, consuming one input element each repetition, and growing a sorted output range. At each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted range, and inserts it there. It repeats until no input elements remain. Insertion sort is commonly used to sort a small number of elements. It is employed in many `std::sort` implementations as a final step of recursion when a sub-range is small enough.
> ```cpp
> template<class Bidir_it>
> void linear_insert(Bidir_it first, Bidir_it last) {
>     auto value = std::move(*last);
>     for (auto curr = std::prev(last); value < *curr; --curr) {
>         *last = std::move(*curr);
>         if ((last = curr) == first)
>             break;
>     }
>     *last = std::move(value);
> }
>
> template<class Bidir_it>
> void insertion_sort(Bidir_it first, Bidir_it last) {
>     if (first == last)
>         return;
>     for (auto next = std::next(first); next != last; ++next)
>         linear_insert(first, next);
> }
> ```

:link:

- B.B.Cindric. [*When the “best” algorithm isn’t*](https://github.com/eugnsp/CUJ/blob/master/13.03/cindric/cindric.md) – C/C++ Users Journal **13** (1995)

:book:

- Ch. 9: *Medians and order statistics* – T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)
- Ch. 8: *Elementary sorting methods*, Sec.: *Insertion sort* – R.Sedgewick. *Algorithms* (1983)

### Selection sort

> Selection sort divides the input range into two parts: a sorted sub-range of items which is built up from left to right at the front of the range and a sub-range of the remaining unsorted items that occupy the rest of the range. The algorithm proceeds by finding the smallest element in the unsorted sub-range, swapping it with the leftmost unsorted element (putting it in sorted order), and moving the sub-range boundaries one element to the right. Selection sort makes only `O(N)` writes in the average and the worst cases, and is useful when writes are significantly more expensive than reads, e.g. when elements have small keys and very large associated data or when elements are stored in flash memory.
> ```cpp
> template<class Forward_it>
> Forward_it min_element(Forward_it first, Forward_it last) {
>     auto min = first++;
>     for (; first != last; ++first)
>         if (*first < *min)
>             min = first;
>     return min;
> }
>
> template<class Forward_it>
> void selection_sort(Forward_it first, Forward_it last) {
>     for (; first != last; ++first)
>         std::iter_swap(first, min_element(first, last));
> }
> ```

:link:

- [*Selection sort* – Wikipedia](https://en.wikipedia.org/wiki/Selection_sort)
- N.A.Alechina. [*Selection sort: Loop invariants*](http://www.cs.nott.ac.uk/~psznza/G5BADS04/ans3.html) – Algorithms and data structures (2004)
- R.Jenke. [*Supplemental handout on selection sort*](http://pages.cs.wisc.edu/~dieter/Courses/2011s-CS240/scribes/selectsort.pdf) – [CS 240: Intro to discrete mathematics](http://pages.cs.wisc.edu/~dieter/Courses/2011s-CS240/) (2011)

:book:

- Ch. 8: *Elementary sorting methods*, Sec: *Selection sort* – R.Sedgewick. *Algorithms* (1983)

### Heap sort

:wrench:

- Implementation of `std::partial_sort` that rearranges a given range such that `k` smallest elements become the first `k` elements of the range, in sorted order.

### Merge sort

:memo:

- Merge sort is useful for sorting linked lists and for external sorting of data that doesn’t fit into main memory.

:link:

- [Merge sort – Wikipedia](https://en.wikipedia.org/wiki/Merge_sort)

:book:

- Sec. 5.1.: *A first recurrence: The mergesort algorithm* – J.Kleinberg, É.Tardos. [*Algorithm design*](https://www.cs.cornell.edu/home/kleinber/) – [Pearson](https://www.pearson.com/us/higher-education/program/Kleinberg-Algorithm-Design/PGM319216.html) (2005)

#### Inversions counting

> Problem: count the number of inversions in a permutation <code>P = (a<sub>1</sub>, ..., a<sub>N</sub>)</code>, i.e. the number of pairs <code>(a<sub>i</sub></code>, <code>a<sub>j</sub>)</code> with `i < j` and <code>a<sub>i</sub> &gt; a<sub>j</sub></code>.

:link:

- [*Counting inversions in a permutation*](https://web.cs.ucdavis.edu/~gusfield/cs122/inversioncount.pdf) – CS 122A: [Algorithm design and analysis](https://web.cs.ucdavis.edu/~gusfield/cs122f10/) (2010)

:movie_camera:

- [*Counting the number of inversions in a permutation*](https://www.youtube.com/watch?v=Vj5IOD7A6f8) – CS 122A: [Algorithm design and analysis](https://web.cs.ucdavis.edu/~gusfield/cs122f10/) (2010)

:book:

- Sec. 5.3: *Counting inversions* – J.Kleinberg, É.Tardos. [*Algorithm design*](https://www.cs.cornell.edu/home/kleinber/) – [Pearson](https://www.pearson.com/us/higher-education/program/Kleinberg-Algorithm-Design/PGM319216.html) (2005)

<!--* The minimum number of adjacent swaps required to sort a permutation `P` (i.e. convert into the identity one) is equal to the number of inversions in `P`. The minimum number of swaps, not necessarily adjacent, is equal to the size of `P` minus the number of cycles in `P`.-->

### Quick sort

> Gist of the algorithm: choose the `pivot` value; partition the range into two sub-ranges, according to whether they are `< pivot`, `== pivot` or `> pivot`, then sort sub-ranges recursively.
> ```cpp
> template<class Rand_it>
> void quicksort(Rand_it first, Rand_it last) {
>     if (last - first <= 1)
>         return;
>     const auto part = partition_hoare(first, last);
>     quicksort(first, part);
>     quicksort(part, last);
> }
> ```

:link:

- [*Quicksort*](https://en.wikipedia.org/wiki/Quicksort) – Wikipedia

:grey_question:

- [*Why is quicksort better than other sorting algorithms in practice?*](https://cs.stackexchange.com/q/3) – Computer Science

:book:

- Ch. 7: *Quicksort* – T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)
- Ch. 5: *QuickSort* – Roughgarden T. [*Algorithms illuminated (Part 1): The basics*](http://timroughgarden.org/books.html) – Soundlikeyourself Publishing (2017)

:page_facing_up:

- M.D.McIlroy. [*A killer adversary for quicksort*](https://www.cs.dartmouth.edu/~doug/mdmspe.pdf) – [Software: Practice and experience **29**, 341](https://doi.org/10.1002/(SICI)1097-024X(19990410)29:4%3C341::AID-SPE237%3E3.0.CO;2-R) (1999)
- Sec. *Algorithm datasheets: Sort a range by partitioning (quicksort)* – D.R.Musser, A.A.Stepanov. [*Algorithm-oriented generic libraries*](http://stepanovpapers.com/HPL-94-13.pdf)
- [HP Laboratories technical report 94-13](https://www.hpl.hp.com/techreports/94/HPL-94-13.html) (1994)

:dizzy:

- [*Quick-sort with Hungarian folk dance*](https://www.youtube.com/watch?v=ywWBy6J5gz8)

#### Lomuto partition

> Lomuto partition scheme permutes the range `[first, last)` into `{{< pivot}, pivot, {>= pivot}}`, where `pivot` is the value of some pivotal element.
> ```cpp
> template<class Bidir_it>
> Bidir_it partition_lomuto(Bidir_it first, Bidir_it last) {
>     const auto& pivot = *--last;
>     auto part = first;
>     for (; first != last; ++first)
>         if (*first < pivot)
>             std::iter_swap(part++, first);
>     std::iter_swap(part, last);
>     return part;
> }
> ```

:link:

- [*Quicksort: Lomuto partition scheme*](https://en.wikipedia.org/wiki/Quicksort#Lomuto_partition_scheme) – Wikipedia

:book:

- Sec. 7.1: *Description of quicksort* – T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)
- Sec. 11.2: *A simple Quicksort* – J.Bentley. [*Programming pearls*](https://www.oreilly.com/library/view/programming-pearls-second/9780134498058/) (1999)

#### Hoare partition

> Hoare partition scheme permutes the range `[first, last)` into `{{<= pivot}, {>= pivot}}`, where `pivot` is the value of some pivotal element. Hoare partition does three times fewer swaps on average than Lomuto’s partition, and it creates efficient partitions even when all values are equal. This partition scheme is used to implement `std::sort` in `libstdc++`.
> ```cpp
> template<class Rand_it>
> Rand_it partition_hoare(Rand_it first, Rand_it last) {
>    const auto pivot = *(first + (last - first) / 2);
>    while (true) {
>        while (*first < pivot)
>            ++first;
>        --last;
>        while (pivot < *last)
>            --last;
>        if (!(first < last))
>            return first;
>        std::iter_swap(first++, last);
>    }
> }
> ```

:link:

- [*Quicksort: Hoare partition scheme*](https://en.wikipedia.org/wiki/Quicksort#Hoare_partition_scheme) – Wikipedia

:book:

- Sec. 11.3: *Better Quicksort* – J.Bentley. [*Programming pearls*](https://www.oreilly.com/library/view/programming-pearls-second/9780134498058/) (1999)

:page_facing_up:

- Sec. *Algorithm datasheets: Partition a range* – D.R.Musser, A.A.Stepanov. [*Algorithm-oriented generic libraries*](http://stepanovpapers.com/HPL-94-13.pdf) – [HP Laboratories technical report 94-13](https://www.hpl.hp.com/techreports/94/HPL-94-13.html) (1994)

#### “Fat pivot” partition / Dutch national flag problem

> “Fat pivot” partition scheme permutes the range `[first, last)` into `{{< pivot}, {= pivot}, {> pivot}}`, where `pivot` is the value of some pivotal element.
> ```cpp
> template<class Rand_it>
> std::pair<Rand_it, Rand_it> partition_fat_pivot(Rand_it first, Rand_it last) {
>     const auto& pivot = *--last;
>     auto part1 = first, part2 = last;
>     while (first != part2)
>         if (*first < pivot)
>             std::iter_swap(first++, part1++);
>         else if (pivot < *first)
>             std::iter_swap(first, --part2);
>         else
>             ++first;
>      std::iter_swap(part2++, last);
>      return {part1, part2};
> }
> ```

:link:

- [*Dutch national flag problem*](https://en.wikipedia.org/wiki/Dutch_national_flag_problem) – Wikipedia

:book:

- Ch. 14: *The problem of the Dutch national flag* – E.W.Dijkstra. [*A discipline of programming*](https://seriouscomputerist.atariverse.com/media/pdf/book/Discipline%20of%20Programming.pdf) (1976)

:page_facing_up:

- E.W.Dijkstra. [*Sequencing primitives revisited*](https://www.cs.utexas.edu/users/EWD/ewd03xx/EWD398.PDF) – EWD398 (1973)

### Order statistics and quick select

> The `K`<sup>th</sup> order statistic of an array is its `K`<sup>th</sup> smallest element. Any comparison-based algorithm of finding the smallest element in an array of size `N` requires at least `N - 1` comparisons in the worst case. Any comparison-based algorithm of finding both the smallest and the largest elements in an array of size `N` requires at least `⌈3N / 2⌉ - 1` comparisons in the worst case. Any comparison-based algorithm of finding both the smallest and the second smallest element in an array of size `N` requires at least <code>N + &lceil;log<sub>2</sub> N&rceil; - 2</code> comparisons in the worst case.

:link:

- [Selection and order statistics](https://www.ics.uci.edu/~eppstein/161/960125.html) – ICS 161: [Design and analysis of algorithms](https://www.ics.uci.edu/~eppstein/161/) (1996)
- [Sample proofs involving selection problems](http://cs.slu.edu/~goldwasser/class/loyola/comp363/2003_Spring/handouts/selectionproofs.pdf) – COMP 363: Design and analysis of computer algorithms (2003)
- [Lower bounds and optimality](https://www.cse.unsw.edu.au/~cs2011/lect/2711_Adversary.pdf) – COMP 2011/2711: Data organisation (2006)

:movie_camera:

- [*Order statistics, median*](https://www.youtube.com/watch?v=mR_RUjsJnV8) – MIT OCW 6.046J/18.410J: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-introduction-to-algorithms-sma-5503-fall-2005/) (2005)
- [Lectures 6-10: *Finding the smallest and second smallest elements*](https://www.youtube.com/watch?v=lWSYE-hRw0s&list=PLHxtyCq_WDLXryyw91lahwdtpZsmo4BGD) – Alexander Stepanov: Efficient programming with components (2013)

:book:

- Ch. 6: *Linear-time selection* – Roughgarden T. [*Algorithms illuminated (Part 1): The basics*](http://timroughgarden.org/books.html) – Soundlikeyourself Publishing (2017)
- Ch. 9: *Medians and order statistics* – T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)
- Sec. 6.5.2: *Finding the k<sup>th</sup> smallest element*, Sec. 6.11.2: *Finding the two largest elements in a set* – U.Manber. *Introduction to algorithms: A creative approach* (1989)
- Sec. 3.6: *Order statistics*, Sec. 3.7: *Expected time for order statistics* – A.V.Aho, J.E.Hopcroft, J.D.Ullman. *The design and analysis of computer algorithms* (1974)

:page_facing_up:

- K.Chen, A.Dumitrescu. [*Selection algorithms with small groups*](https://arxiv.org/abs/1409.3600) (2019)
- S.S.Kislitsyn. [*On the selection of the k<sup>th</sup> element of an ordered set by pairwise comparison*](https://gdz.sub.uni-goettingen.de/id/PPN394039319_0005?tify={%22pages%22:[559]}) – Sibirsky Matematichesky Zhurnal **5**, 557 (in Russian, 1964)

---

## Linear-time sorting

:movie_camera:

- [*Counting sort and radix sort*](https://www.youtube.com/watch?v=Nz1KZXbghj8&t=1966) – MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/) (2011)

### Count sort

### Radix sort

:link:

- [*Radix sort*](https://en.wikipedia.org/wiki/Radix_sort) – Wikipedia
- [*American flag sort*](https://en.wikipedia.org/wiki/American_flag_sort) – Wikipedia

:movie_camera:

- M.Skarupke. [*Sorting in less than `O(n log n)`: Generalizing and optimizing radix sort*](https://www.youtube.com/watch?v=zqs87a_7zxw) – C++Now (2017)

### Sorting by swapping

#### Adjacent swaps

> The minimum number of adjacent swaps required to sort a permutation `P` (i.e. convert it into the identity one) is equal to the number of inversions in `P`.

#### Arbitrary swaps

> The minimum number of arbitrary swaps required to sort a permutation `P` (i.e. convert it into the identity one) is equal to the size of `P` minus the number of cycles in `P`.

:link:

- [*Compute the minimal number of swaps to order a sequence*](https://stackoverflow.com/q/15152322) – Stack Overflow

---

## Other sorting algorithms

### Pancake sorting

:memo:

- The problem of finding the shortest sequence of flips for a given stack of pancakes is NP-hard (L.Bulteau, G.Fertin, I.Rusu, 2011)

:link:

- [*Pancake sorting*](https://en.wikipedia.org/wiki/Pancake_sorting) – Wikipedia

### Spreadsort

:link:

- [*Spreadsort*](https://en.wikipedia.org/wiki/Spreadsort) – Wikipedia
- [*Spreadsort*](https://www.boost.org/doc/libs/1_71_0/libs/sort/doc/html/sort/single_thread/spreadsort.html) – Boost.Sort library

---

# Searching

:book:

- Col. 13: *Searching* – J.Bentley. [*Programming pearls*](https://www.oreilly.com/library/view/programming-pearls-second/9780134498058/) (1999)

## Binary search

See also [*Binary search* – Algorithm analysis](algorithm_analysis.md#binary-search).

:book:

- Col. 4: *Writing correct programs*, Sec. 9.4: *Major surgery – binary search* – J.Bentley. [*Programming pearls*](https://www.oreilly.com/library/view/programming-pearls-second/9780134498058/) (1999)

