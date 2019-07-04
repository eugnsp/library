# Trees

## Table of contents

* [Binary trees](#binary-trees)
	* [Self-balancing binary search trees](#self-balancing-binary-search-trees)
		* [AVL (Adelson-Velskiĭ&ndash;Landis) trees](#avl-adelson-velskiĭlandis-trees)
	* [Other binary trees](#other-binary-trees)
		* [Binary indexed trees (Fenwick trees)](#binary-indexed-trees-fenwick-trees)
* [B-trees](#b-trees)
	* [2-3 trees](#2-3-trees)
* [Traversal](#traversal)

---

## Binary trees

> A binary tree is a tree in which no node can have more than two children.

:memo: **Notes**

* The total number of binary trees with `N` different keys is given by `N! C(N)`, where `C(N)` is the `N`<sup>th</sup> Catalan number. Asymptotically <code>C(N) &sim; 4<sup>N</sup> / [N<sup>3/2</sup> sqrt &pi;]</code>.
* The average height of a randomly built binary search tree is `O(log n)`.

### Binary search trees

> A binary search tree is a binary tree that satisfies the binary search property: the key in each node must be greater than or equal to any key stored in the left subtree, and less than or equal to any key stored in the right subtree.

:memo: **Notes**

* The total number of binary search trees with `N` different keys is given by the `N`<sup>th</sup> Catalan number `C(N)`. Asymptotically <code>C(N) &sim; 4<sup>N</sup> / [N<sup>3/2</sup> sqrt &pi;]</code>.

:movie_camera: **Videos**

* *Binary search trees* &ndash; MIT OCW 6.006: Introduction to algorithms (2011).\
[Watch at YouTube](https://www.youtube.com/watch?v=9Jry5-82I68) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

### Self-balancing binary search trees

> A self-balancing binary search tree is a binary search tree that automatically keeps its height small during arbitrary insertions and deletions.

:memo: **Notes**

* For a self-balancing binary search tree containing `N` nodes, lookup, insertion, and removal of an item takes `O(log N)` worst-case time, and ordered enumeration of all nodes takes `O(N)` time.
* Self-balancing binary search trees can be used to implement sorted associative containers. For example, `std::set` and `std::map` are typically implemented using red-black trees.
* Self-balancing binary search can be used to count the number of inversions in an array and the number of smaller/larger elements on the right/left side of each element in an array.

:link: **Webpages**

* [Self-balancing binary search tree &ndash; Wikipedia](https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree)

#### AVL (Adelson-Velskiĭ&ndash;Landis) trees

> An AVL tree is a self-balancing binary search tree in which for every node the height of the left and right subtrees can differ by at most one.

:memo: **Notes**

* The height of an AVL tree with `N` nodes lies between <code>log<sub>2</sub>(N + 1)</code> and <code>1.4404 log<sub>2</sub>(N + 2) - 0.3277</code>.
* For insertions, one rotation always suffices. For deletions, `O(log N)` rotations may be required. Non-recursive insertions and deletions are generally faster, but harded to code and read.
* Double rotations can be made more efficient if performed as a single step and not as two single rotations.
* Balance factors, i.e. differences in heights, can be stored instead of heights. This results in faster but more complicated code. If a balance factor is stored as a separate data member, there is no profit in the amount of space used due to data alignment.
* AVL trees require at most 45% more comparisons than optimal binary search trees.

:link: **Webpages**

* [AVL tree &ndash; Wikipedia](https://en.wikipedia.org/wiki/AVL_tree)
* [C++ AVL tree template](https://www.codeproject.com/Articles/2839/C-AVL-Tree-Template)
* [AVL trees: Tutorial and C++ implementation](https://www.bradapp.com/ftp/src/libs/C++/AvlTrees.html)
* [Simple AVL tree in C++](http://somethingk.com/main/?p=1127)
* [AVL tree implementation in C++](https://gist.github.com/harish-r/097688ac7f48bcbadfa5)

:book: **Books**

* Sec. 6.2.3: *Balanced trees* &ndash; D.E.Knuth. *The art of computer programming. Vol. 3: Sorting and searching*. Addison-Wesley, 2<sup>nd</sup> ed., 1998. \
[Book website](https://www-cs-faculty.stanford.edu/~knuth/taocp.html)
* Sec. 4.4: *AVL trees* &ndash; M.A.Weiss. *Data structures and algorithm analysis in C++*. Pearson, 4<sup>th</sup> ed., 2014.\
[Book website](https://www.pearson.com/us/higher-education/program/Weiss-Data-Structures-and-Algorithm-Analysis-in-C-4th-Edition/PGM148299.html)
* Sec. 4.3.4: *AVL trees* &ndash; U.Manber. *Introduction to algorithms: A creative approach.* Addison-Wesley, 1<sup>st</sup> ed., 1989.

:page_facing_up: **Papers**

* G.M.Adelson-Velskiĭ, E.M.Landis. *An algorithm for organization of information*. Doklady Akademii Nauk SSSR **146**, 263 (1962).\
[Full text](http://professor.ufabc.edu.br/~jesus.mena/courses/mc3305-2q-2015/AED2-10-avl-paper.pdf) |
[Full text (russian)](http://www.mathnet.ru/links/29d35467640f7ae44d5d347a765fc559/dan26964.pdf)

:movie_camera: **Videos**

* *AVL trees, AVL sort* &ndash; MIT OCW 6.006: Introduction to algorithms (2011).\
[Watch at YouTube](https://www.youtube.com/watch?v=FNeL18KsWPc) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:dizzy: **Visualizations**

* [AVL tree visualization](https://www.cs.usfca.edu/~galles/visualization/AVLtree.html)

### Other binary trees

#### Binary indexed trees (Fenwick trees)

> A binary indexed tree is a data structure that can efficiently update elements and calculate prefix sums.

:memo: **Notes**

* Both `0`-based and `1`-based indexing can be used in equally elegant ways.
* A Fenwick tree can be built for any cancellative semigroup (e.g. for the set of integers under addition or multiplication); if the cancellation property doesn't hold (e.g. for <code>min(&bullet;, &bullet;)</code>), a segment tree can be used.

:wrench: **Applications**

* Arithmetic coding
* Monte-Carlo simulations

 <!-- TODO : add links -->

:link: **Webpages**

* [Fenwick tree &ndash; Wikipedia](https://en.wikipedia.org/wiki/Fenwick_tree)
* [Binary indexed trees &ndash; Topcoder](https://www.topcoder.com/community/competitive-programming/tutorials/binary-indexed-trees/)
* [Fenwick tree &ndash; Brilliant](https://brilliant.org/wiki/fenwick-tree/)
* [A JavaScript implementation of binary indexed tree &ndash; Github](https://github.com/Microsoft/fast-binary-indexed-tree-js)

:movie_camera: **Videos**

* *Fenwick trees* &ndash; Algorithms Live!\
[Watch at YouTube](https://www.youtube.com/watch?v=kPaJfAUwViY)
* *Fenwick tree/Binary indexed tree* &ndash; William Fiset.\
[Watch at YouTube](https://www.youtube.com/playlist?list=PLDV1Zeh2NRsCvoyP-bztk6uXAYoyZg_U9)

:book: **Books**

* Sec. 2.4.4: *Binary indexed (Fenwick) tree* &ndash; S.Halim, F.Halim. *Competitive programming*. 3<sup>rd</sup> ed., 2013.\
[Book website](https://cpbook.net/)

:page_facing_up: **Papers**

* P.M.Fenwick. *A new data structure for cumulative frequency tables*. Software: Practice and Experience **24**, [327](https://dx.doi.org/10.1002/spe.4380240306) (1994).\
[Full text](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.14.8917&rep=rep1&type=pdf)

---

## B-trees

:movie_camera: **Videos**

* *2-3 Trees and B-Trees* &ndash; MIT OCW 6.046J: Design and analysis of algorithms (2015).\
[Watch at YouTube](https://www.youtube.com/watch?v=TOb1tuEZ2X4) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-design-and-analysis-of-algorithms-spring-2015/index.htm)

:book: **Books**

* Ch. 18: *B-trees* &ndash; T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009.\
[Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)

### 2-3 trees

---

## Traversal

:link: **Webpages**

[Tree traversal &ndash; Wikipedia](https://en.wikipedia.org/wiki/Tree_traversal)

:memo: **Notes**

* See also: [Graphs &ndash; Traversal](graphs.md#traversal)
