# Data structures and algorithms: Trees

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

> A self-balancing binary search tree is a binary search tree that automatically keeps its height small during insertions and deletions.

:link: *Web pages*

* [Self-balancing binary search tree &ndash; Wikipedia](https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree) <!-- TODO : link -->

:memo: *Notes*

* Applications:
	* Implementation of sorted associative containers (e.g., `std::set` and `std::map`).

#### AVL (Adelson-Velskiĭ&ndash;Landis) trees

> An AVL tree is a self-balancing binary search tree in which for every node the height of the left and right subtrees can differ by at most one.

:link: *Web pages*

* [AVL tree &ndash; Wikipedia](https://en.wikipedia.org/wiki/AVL_tree)
* [C++ AVL tree template](https://www.codeproject.com/Articles/2839/C-AVL-Tree-Template)
* [AVL trees: Tutorial and C++ implementation](https://www.bradapp.com/ftp/src/libs/C++/AvlTrees.html)
* [Simple AVL tree in C++](http://somethingk.com/main/?p=1127)
* [AVL tree implementation in C++](https://gist.github.com/harish-r/097688ac7f48bcbadfa5)

:book: *Books*

* M.A.Weiss. *Data structures and algorithm analysis in C++*. Pearson, 4<sup>th</sup> ed., 2014 &ndash; Sec. 4.4: *AVL trees*

:page_facing_up: *Papers*

* G.M.Adelson-Velskiĭ, E.M.Landis. *An algorithm for organization of information*. Doklady Akademii Nauk SSSR **146**, 263 (1962)\
[Full text](http://professor.ufabc.edu.br/~jesus.mena/courses/mc3305-2q-2015/AED2-10-avl-paper.pdf) | [Full text (russian)](http://www.mathnet.ru/links/29d35467640f7ae44d5d347a765fc559/dan26964.pdf)

:movie_camera: *Videos*

* MIT OCW 6.006 Introduction to algorithms (2011) &ndash; *AVL Trees, AVL Sort*\
[Watch at YouTube](https://www.youtube.com/watch?v=FNeL18KsWPc) | [Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:dizzy: *Visualizations*

* [AVL tree visualzation](https://www.cs.usfca.edu/~galles/visualization/AVLtree.html)

:memo: *Notes*

* Maximum height of an AVL tree with *N* nodes is ~1.44 log<sub>2</sub>*N*.
* One rotation always suffices. Non-recursive insertions and deletions are generally faster, but harded to code and read.
* Balance factors (differences in heights) can be stored instead of heights. This results in faster but more complicated code. If a balance factor is stored as a separate data member, there is no profit in the amount of space used due to data alignment.
* Double rotations can be made more efficient if performed as a single step and not as two single rotations.

### Other binary trees

#### Binary indexed trees (Fenwick trees)

> A binary indexed tree is a data structure that can efficiently update elements and calculate prefix sums.

:link: *Webpages*

* [Fenwick tree &ndash; Wikipedia](https://en.wikipedia.org/wiki/Fenwick_tree)
* [Fenwick tree](https://brilliant.org/wiki/fenwick-tree/)
* [Binary indexed trees](https://www.topcoder.com/community/competitive-programming/tutorials/binary-indexed-trees/)
* [A JavaScript implementation of Binary Indexed](https://github.com/Microsoft/fast-binary-indexed-tree-js)

:movie_camera: *Videos*

* Algorithms Live! &ndash; *Fenwick trees*\
[Watch at YouTube](https://www.youtube.com/watch?v=kPaJfAUwViY)

:book: *Books*

* S.Halim, F.Halim. *Competitive programming.* 3<sup>rd</sup> ed., 2013 &ndash; Sec. 2.4.4: *Binary indexed (Fenwick) tree*

:page_facing_up: *Papers*

* P.M.Fenwick. *A new data structure for cumulative frequency tables.* Software: Practice and Experience **24**, [327](https://dx.doi.org/10.1002/spe.4380240306) (1994)\
[Full text](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.14.8917&rep=rep1&type=pdf)

:memo: *Notes*

* Both `0`-based and `1`-based indexing can be used in equally elegant ways.

## Traversal

:link: *Webpages*

[Tree traversal &ndash; Wikipedia](https://en.wikipedia.org/wiki/Tree_traversal)

:memo: *Notes*

* See also: [Graphs &ndash; Traversal](graphs.md#traversal)
