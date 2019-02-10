# Trees

## Binary trees

<!--
## Binary search trees

A binary search tree is a rooted binary tree that satisfies the binary search property: the value in each node must be greater than or equal to any value stored in the left subtree, and less than or equal to any value stored in the right subtree.
-->

## Self-balancing binary search trees

A self-balancing binary search tree is a binary search tree that automatically keeps its height small during insertions and deletions.

* https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree

### AVL (Adelson-Velskii&ndash;Landis) trees

An AVL tree is a self-balancing binary search tree in which is no node has subtrees differing in height by more than one.

#### Descriptions and implementations

* https://en.wikipedia.org/wiki/AVL_tree
* https://www.codeproject.com/Articles/2839/C-AVL-Tree-Template
* https://www.bradapp.com/ftp/src/libs/C++/AvlTrees.html
* http://somethingk.com/main/?p=1127
* https://gist.github.com/harish-r/097688ac7f48bcbadfa5

#### Papers

* G.M.Adelson-Velskii, E.M.Landis. *An algorithm for organization of information*. Doklady Akademii Nauk SSSR **146**, 263 (1962)\
[Full text](http://professor.ufabc.edu.br/~jesus.mena/courses/mc3305-2q-2015/AED2-10-avl-paper.pdf) | [Full text (russian)](http://www.mathnet.ru/links/29d35467640f7ae44d5d347a765fc559/dan26964.pdf)

#### Videos

* [MIT OCW 6.006 Introduction to algorithms (2011) &ndash; Lecture 6: *AVL Trees, AVL Sort*](https://www.youtube.com/watch?v=FNeL18KsWPc)

#### Visualizations

* https://www.cs.usfca.edu/~galles/visualization/AVLtree.html

### Binary indexed trees = Fenwick trees

A binary indexed tree is a data structure that can efficiently update elements and calculate prefix sums.

#### Descriptions and implementations

* https://en.wikipedia.org/wiki/Fenwick_tree

#### Papers

* P.M.Fenwick. *A new data structure for cumulative frequency tables*. Software: Practice and Experience **24**, [327](https://dx.doi.org/10.1002/spe.4380240306) (1994)\
[Full text](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.14.8917&rep=rep1&type=pdf)

#### Books

* S.Halim, F.Halim. *Competitive Programming*. 3rd ed., 2013 &ndash; Sec. 2.4.4
 *Binary Indexed (Fenwick) Tree*

#### Videos

* [Algorithms Live!: *Fenwick Trees*](https://www.youtube.com/watch?v=kPaJfAUwViY)
