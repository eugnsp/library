# Trees

## Table of contents

* [Binary trees](#binary-trees)
	* [Self-balancing binary search trees](#self-balancing-binary-search-trees)
		* [AVL (Adelson-Velskiĭ&ndash;Landis) trees](#avl-adelson-velskiĭlandis-trees)
	* [Other binary trees](#other-binary-trees)
		* [Binary indexed trees (Fenwick trees)](#binary-indexed-trees-fenwick-trees)
* [Traversal](#traversal)

---

## Binary trees

<!--
### Binary search trees

A binary search tree is a rooted binary tree that satisfies the binary search property: the value in each node must be greater than or equal to any value stored in the left subtree, and less than or equal to any value stored in the right subtree.-->

### Self-balancing binary search trees

> A self-balancing binary search tree is a binary search tree that automatically keeps its height small during arbitrary insertions and deletions.

:link: *Web pages*

* [Self-balancing binary search tree &ndash; Wikipedia](https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree) <!-- TODO : link -->

:memo: *Notes*

* For a self-balancing BST containing `N` nodes, lookup, insertion, and removal of an item takes `O(log N)` worst-case time, and ordered enumeration of all nodes takes `O(N)` time.
* Applications:
	* Implementation of sorted associative containers (e.g., `std::set` and `std::map`).
	* Counting inversions in an array

#### AVL (Adelson-Velskiĭ&ndash;Landis) trees

> An AVL tree is a self-balancing binary search tree in which for every node the height of the left and right subtrees can differ by at most one.

:link: *Web pages*

* [AVL tree &ndash; Wikipedia](https://en.wikipedia.org/wiki/AVL_tree)
* [C++ AVL tree template](https://www.codeproject.com/Articles/2839/C-AVL-Tree-Template)
* [AVL trees: Tutorial and C++ implementation](https://www.bradapp.com/ftp/src/libs/C++/AvlTrees.html)
* [Simple AVL tree in C++](http://somethingk.com/main/?p=1127)
* [AVL tree implementation in C++](https://gist.github.com/harish-r/097688ac7f48bcbadfa5)

:book: **Books**

* M.A.Weiss. *Data structures and algorithm analysis in C++*. Pearson, 4<sup>th</sup> ed., 2014 &ndash; Sec. 4.4: *AVL trees*\
[Book website](https://www.pearson.com/us/higher-education/program/Weiss-Data-Structures-and-Algorithm-Analysis-in-C-4th-Edition/PGM148299.html)
* U.Manber. *Introduction to algorithms: A creative approach.* Addison-Wesley, 1<sup>st</sup> ed., 1989 &ndash; Sec. 4.3.4: *AVL trees*

:page_facing_up: **Papers**

* G.M.Adelson-Velskiĭ, E.M.Landis. *An algorithm for organization of information*. Doklady Akademii Nauk SSSR **146**, 263 (1962)\
[Full text](http://professor.ufabc.edu.br/~jesus.mena/courses/mc3305-2q-2015/AED2-10-avl-paper.pdf) | [Full text (russian)](http://www.mathnet.ru/links/29d35467640f7ae44d5d347a765fc559/dan26964.pdf)

:movie_camera: **Videos**

* MIT OCW 6.006 Introduction to algorithms (2011) &ndash; *AVL Trees, AVL Sort*\
[Watch at YouTube](https://www.youtube.com/watch?v=FNeL18KsWPc) | [Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:dizzy: **Visualizations**

* [AVL tree visualization](https://www.cs.usfca.edu/~galles/visualization/AVLtree.html)

:memo: **Notes**

* Maximum height of an AVL tree with *N* nodes is `~1.44 log₂N`.
* For insertions, one rotation always suffices. For deletions, `O(log N)` rotations may be required. Non-recursive insertions and deletions are generally faster, but harded to code and read.
* Double rotations can be made more efficient if performed as a single step and not as two single rotations.
* Balance factors (differences in heights) can be stored instead of heights. This results in faster but more complicated code. If a balance factor is stored as a separate data member, there is no profit in the amount of space used due to data alignment.
* AVL trees require at most 45% more comparisons than optimal binary search trees.

### Other binary trees

#### Binary indexed trees (Fenwick trees)

> A binary indexed tree is a data structure that can efficiently update elements and calculate prefix sums.

:link: **Webpages**

* [Fenwick tree &ndash; Wikipedia](https://en.wikipedia.org/wiki/Fenwick_tree)
* [Binary indexed trees &ndash; Topcoder](https://www.topcoder.com/community/competitive-programming/tutorials/binary-indexed-trees/)
* [Fenwick tree &ndash; Brilliant](https://brilliant.org/wiki/fenwick-tree/)
* [A JavaScript implementation of binary indexed tree &ndash; Github](https://github.com/Microsoft/fast-binary-indexed-tree-js)

:movie_camera: **Videos**

* Algorithms Live! &ndash; *Fenwick trees*\
[Watch at YouTube](https://www.youtube.com/watch?v=kPaJfAUwViY)
* William Fiset &ndash; *Fenwick tree/Binary indexed tree*\
[Watch at YouTube](https://www.youtube.com/playlist?list=PLDV1Zeh2NRsCvoyP-bztk6uXAYoyZg_U9)

:book: **Books**

* S.Halim, F.Halim. *Competitive programming.* 3<sup>rd</sup> ed., 2013 &ndash; Sec. 2.4.4: *Binary indexed (Fenwick) tree*\
[Book website](https://cpbook.net/)

:page_facing_up: **Papers**

* P.M.Fenwick. *A new data structure for cumulative frequency tables.* Software: Practice and Experience **24**, [327](https://dx.doi.org/10.1002/spe.4380240306) (1994)\
[Full text](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.14.8917&rep=rep1&type=pdf)

:memo: **Notes**

* Both `0`-based and `1`-based indexing can be used in equally elegant ways.
* A Fenwick tree can be built for any cancellative semigroup (e.g. for the set of integers under addition or multiplication); if the cancellation property doesn't hold (e.g. for `min(•, •)`), a segment tree enters the stage.
* Applications:
	* Arithmetic coding
	* Monte-Carlo simulations

 <!-- TODO : add links -->

## Traversal

:link: **Webpages**

[Tree traversal &ndash; Wikipedia](https://en.wikipedia.org/wiki/Tree_traversal)

:memo: **Notes**

* See also: [Graphs &ndash; Traversal](graphs.md#traversal)
