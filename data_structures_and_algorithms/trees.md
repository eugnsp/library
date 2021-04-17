# Trees <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Binary trees](#binary-trees)
	- [Binary search trees](#binary-search-trees)
	- [Self-balancing binary search trees](#self-balancing-binary-search-trees)
		- [AVL (Adelson-Velskiĭ–Landis) trees](#avl-adelson-velskiĭlandis-trees)
	- [Other binary trees](#other-binary-trees)
		- [Binary indexed trees (Fenwick trees)](#binary-indexed-trees-fenwick-trees)
	- [Generation of binary trees](#generation-of-binary-trees)
		- [Random binary trees](#random-binary-trees)
	- [Optimization of binary trees](#optimization-of-binary-trees)
- [B/B+-trees](#bb-trees)
	- [2-3 trees](#2-3-trees)
	- [Range trees](#range-trees)
- [Tries](#tries)
- [Traversal](#traversal)
- [Volumetric trees](#volumetric-trees)
	- [OpenVDB](#openvdb)

---

## Binary trees

> A binary tree is a tree in which no node can have more than two children. The total number of binary trees with `N` different keys is given by `N! C(N)`, where `C(N)` is the `N`<sup>th</sup> Catalan number. Asymptotically <code>C(N) &sim; 4<sup>N</sup> / [N<sup>3/2</sup> sqrt &pi;]</code>.

:grey_question:

- [*Why does a complete binary tree of `n` leaves have `2n−1` nodes?*](https://math.stackexchange.com/q/180005) – Mathematics

### Binary search trees

> A binary search tree is a binary tree that satisfies the binary search property: the key in each node must be greater than or equal to any key stored in the left subtree, and less than or equal to any key stored in the right subtree. The total number of binary search trees with `N` different keys is given by the `N`<sup>th</sup> Catalan number `C(N)`. Asymptotically <code>C(N) &sim; 4<sup>N</sup> / [N<sup>3/2</sup> sqrt &pi;]</code>. The average height of a randomly built binary search tree wuth `N` nodes is `O(log N)`.

:movie_camera:

- [*Binary search trees*](https://www.youtube.com/watch?v=9Jry5-82I68) – MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

:book:

- Sec. 2.3.1: *Binary search trees*, Sec: *Selection sort* – E.Horowitz, S.Sahni, S.Rajasekaran. *Computer algorithms* – W.H.Freeman (1997)
- Sec. 13.3: *Binary search trees* – J.Bentley. [*Programming pearls*](https://www.oreilly.com/library/view/programming-pearls-second/9780134498058/) (1999)

### Self-balancing binary search trees

> A self-balancing binary search tree is a binary search tree that automatically keeps its height small during arbitrary insertions and deletions.

:memo:

- For a self-balancing binary search tree containing `N` nodes, lookup, insertion, and removal of an item takes `O(log N)` worst-case time, and ordered enumeration of all nodes takes `O(N)` time.
- Self-balancing binary search trees can be used to implement sorted associative containers. For example, `std::set` and `std::map` are typically implemented using red-black trees.
- Self-balancing binary search can be used to count the number of inversions in an array and the number of smaller/larger elements on the right/left side of each element in an array.

:link:

- [Self-balancing binary search tree](https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree) – Wikipedia

#### AVL (Adelson-Velskiĭ–Landis) trees

> An AVL tree is a self-balancing binary search tree in which for every node the height of the left and right subtrees can differ by at most one.

:memo:

- The height of an AVL tree with `N` nodes lies between <code>log<sub>2</sub>(N + 1)</code> and <code>1.4404 log<sub>2</sub>(N + 2) - 0.3277</code>.
- For insertions, one rotation always suffices. For deletions, `O(log N)` rotations may be required. Non-recursive insertions and deletions are generally faster, but harded to code and read.
- Double rotations can be made more efficient if performed as a single step and not as two single rotations.
- Balance factors, i.e. differences in heights, can be stored instead of heights. This results in faster but more complicated code. If a balance factor is stored as a separate data member, there is no profit in the amount of space used due to data alignment.
- AVL trees require at most 45% more comparisons than optimal binary search trees.

:link:

- [AVL tree](https://en.wikipedia.org/wiki/AVL_tree) – Wikipedia
- [C++ AVL tree template](https://www.codeproject.com/Articles/2839/C-AVL-Tree-Template)
- [AVL trees: Tutorial and C++ implementation](https://www.bradapp.com/ftp/src/libs/C++/AvlTrees.html)
- [Simple AVL tree in C++](http://somethingk.com/main/?p=1127)
- [AVL tree implementation in C++](https://gist.github.com/harish-r/097688ac7f48bcbadfa5)

:book:

- Sec. 6.2.3: *Balanced trees* – D.E.Knuth. [*The art of computer programming.*](https://www-cs-faculty.stanford.edu/~knuth/taocp.html) *Vol. 3: Sorting and searching* (1998)
- Sec. 4.4: *AVL trees* – M.A.Weiss. [*Data structures and algorithm analysis in C++*](https://www.pearson.com/us/higher-education/program/Weiss-Data-Structures-and-Algorithm-Analysis-in-C-4th-Edition/PGM148299.html) (2014)
- Sec. 4.3.4: *AVL trees* – U.Manber. *Introduction to algorithms: A creative approach* (1989)

:page_facing_up:

- G.M.Adelson-Velskiĭ, E.M.Landis. *An algorithm for organization of information.* [In english](https://zhjwpku.com/assets/pdf/AED2-10-avl-paper.pdf), [In russian](http://mi.mathnet.ru/rus/dan/v146/i2/p263) – Doklady Akademii Nauk SSSR **146**, 263 (1962)

:movie_camera:

- [*AVL trees, AVL sort*](https://www.youtube.com/watch?v=FNeL18KsWPc) – MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

:dizzy: **Visualizations**

- [AVL tree visualization](https://www.cs.usfca.edu/~galles/visualization/AVLtree.html)

### Other binary trees

#### Binary indexed trees (Fenwick trees)

> A binary indexed tree (Fenwick tree) is a data structure that can efficiently update elements and calculate prefix sums. A Fenwick tree can be built for any cancellative semigroup (e.g. for the set of integers under addition or multiplication); if the cancellation property doesn't hold (e.g. for <code>min(&bullet;, &bullet;)</code>), a segment tree can be used. Both `0`-based and `1`-based indexing can be used in equally elegant ways. Applications: arithmetic coding, Monte–Carlo simulations.

 <!-- TODO : add links -->

:link:

- [*Fenwick tree*](https://en.wikipedia.org/wiki/Fenwick_tree) – Wikipedia
- [*Binary indexed trees*](https://www.topcoder.com/community/competitive-programming/tutorials/binary-indexed-trees/) – Topcoder
- [*Fenwick tree*](https://brilliant.org/wiki/fenwick-tree/) – Brilliant
- [*A JavaScript implementation of binary indexed tree*](https://github.com/Microsoft/fast-binary-indexed-tree-js) – Microsoft @ GitHub

:grey_question:

- [What are the advantage of binary indexed tree (BIT or Fenwick tree) over segment tree?](https://www.quora.com/What-are-the-advantage-of-binary-indexed-tree-BIT-or-fenwick-tree-over-segment-tree) – Quora

:movie_camera:

- [*Fenwick trees*](https://www.youtube.com/watch?v=kPaJfAUwViY) – Algorithms Live!
- W.Fiset. [*Fenwick tree/Binary indexed tree*](https://www.youtube.com/playlist?list=PLDV1Zeh2NRsCvoyP-bztk6uXAYoyZg_U9)

:book:

- Sec. 2.4.4: *Binary indexed (Fenwick) tree* – S.Halim, F.Halim. [*Competitive programming*](https://cpbook.net/) (2013)

:page_facing_up:

- P.M.Fenwick. [*A new data structure for cumulative frequency tables*](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.14.8917&rep=rep1&type=pdf) – [Software: Practice and Experience **24**, 327](https://dx.doi.org/10.1002/spe.4380240306) (1994)

### Generation of binary trees

- Sec. 7.2.1.6: [*Generating all trees*](http://www.cs.utsa.edu/~wagner/knuth/fasc4a.pdf) – D.E.Knuth. [*The art of computer programming.*](https://www-cs-faculty.stanford.edu/~knuth/taocp.html) *Vol. 4A: Combinatorial algorithms, Part 1* (2011)

#### Random binary trees

:link:

- E.M&auml;kinen [*Generating random binary trees – a survey*](https://www.sis.uta.fi/cs/reports/pdf/A-1998-3.pdf) (1998)

### Optimization of binary trees

- D.W.Schwartz. [*An efficient method for optimizing binary trees*](https://github.com/eugnsp/CUJ/blob/master/11.02/schwartz/schwartz.md) – C/C++ Users Journal **11** (1993)

---

## B/B+-trees

:grey_question:

- [*Advantage of B+ trees over BSTs?*](https://stackoverflow.com/q/15485220) – Stack Overflow

:movie_camera:

- [*2-3 Trees and B-Trees*](https://www.youtube.com/watch?v=TOb1tuEZ2X4) – MIT OCW 6.046J: [Design and analysis of algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-design-and-analysis-of-algorithms-spring-2015/index.htm) (2015)

:book:

- Ch. 18: *B-trees* – T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)

### 2-3 trees

### Range trees

:movie_camera:

- E.Demaine. [*Augmentation: Range trees*](https://www.youtube.com/watch?v=xVka6z1hu-I&t=3553) – MIT OCW 6.046J: [Design and analysis of algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-design-and-analysis-of-algorithms-spring-2015/index.htm) (2015)

---

## Tries

:link:

- J.W.M.Stevens. [*Lexical analysis using search tries*](https://github.com/eugnsp/CUJ/blob/master/10.04/jstevens/jstevens.md) – C/C++ Users Journal **10** (1992)

---

## Traversal

See also: [Graphs – Traversal](graphs.md#traversal)

:link:

- [*Tree traversal*](https://en.wikipedia.org/wiki/Tree_traversal) – Wikipedia

---

## Volumetric trees

### OpenVDB

:link:

- [OpenVDB](https://www.openvdb.org/)
- K.Museth. [*OpenVDB: An open source data structure and toolkit for high-resolution volumes*](https://www.youtube.com/watch?v=7hUH92xwODg) – BIDS (2015)
<!-- http://www.museth.org/Ken/Publications_files/Nielsen-Museth_JSC05.pdf -->
