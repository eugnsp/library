# Graphs

## Table of contents

* [Data structures](#data-structures)
* [Traversal](#traversal)
	* [Breadth-first search (BFS)](#breadth-first-search-bfs)
	* [Depth-first search (DFS)](#depth-first-search-dfs)
	* [Cycle detection](#cycle-detection)
	* [Topological sorting](#topological-sorting)
		* [DFS-based topological sorting](#dfs-based-topological-sorting)
		* [Kahn's algorithm](#kahns-algorithm)
* Shortest paths
	* Single-source shortest paths
	* All-pairs shortest paths
	* Travelling salesman problem

---

## Data structures

## Traversal

### Breadth-first search (BFS)

> Breadth-first search is an algorithm for traversing or searching a graph that explores all of the neighbour nodes at the present depth prior to moving on to the nodes at the next depth level.

:link: **Webpages**

* [Breadth-first search &ndash; Wikipedia](https://en.wikipedia.org/wiki/Breadth-first_search)

:movie_camera: **Videos**

* MIT OCW 6.006 Introduction to algorithms (2011) &ndash; *Breadth-First Search*\
[Watch at YouTube](https://www.youtube.com/watch?v=s-CYnVz-uh4) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:book: **Books**

* T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009 &ndash; Sec. 22.2: *Breadth-first search*\
[Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
* S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008 &ndash; Sec. 5.6: *Breadth-first search*\
[Book website](http://www.algorist.com/)
* S.Halim, F.Halim. *Competitive Programming.* 3<sup>rd</sup> ed., 2013 &ndash; Sec. 4.2.2: *Breadth first search*\
[Book website](https://cpbook.net/)

<!-- :memo: **Notes**

* Applications:
	* Connected components
	* Two-colouring -->

### Depth-first search (DFS)

> Depth-first search is an algorithm for traversing or searching a graph that explores as far as possible along each branch before backtracking.

:wrench: **Applications**

* [Cycle detection](#cycle-detection)
* [DFS-based topological sorting](#dfs-based-topological-sorting)

:movie_camera: **Videos**

* MIT OCW 6.006 Introduction to algorithms (2011) &ndash; *Depth-First Search (DFS)*\
[Watch at YouTube](https://www.youtube.com/watch?v=AfSk24UTFS8) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:book: **Books**

* T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009 &ndash; Sec. 22.3: *Depth-first search*\
[Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
* S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008 &ndash; Sec. 5.8: *Depth-first search*, Sec. 5.10: *Depth-first search on directed graphs*\
[Book website](http://www.algorist.com/)
* S.Halim, F.Halim. *Competitive Programming*. 3<sup>rd</sup> ed., 2013 &ndash; Sec. 4.2.1: *Depth first search*\
[Book website](https://cpbook.net/)

### Cycle detection

:movie_camera: **Videos**

* MIT OCW 6.006 Introduction to algorithms (2011) &ndash; *Depth-First Search (DFS)*\
[Watch at YouTube](https://www.youtube.com/AfSk24UTFS8?t=1093) (from 18:13) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

### Topological sorting

> Topological sorting of a directed acyclic graph (DAG) is a linear ordering of its vertices such that for every directed edge `(u → v)`, vertex `u` comes before vertex `v` in the ordering.

:link: **Webpages**

* [Topological sorting &ndash; Wikipedia](https://en.wikipedia.org/wiki/Topological_sorting)
* [Topological sorting &ndash; SB Algorithm Repository](http://www3.cs.stonybrook.edu/~algorith/files/topological-sorting.shtml)

:book: **Books**

* S.Halim, F.Halim. *Competitive programming*. 3<sup>rd</sup> ed., 2013 &ndash; Sec. 4.2.5: *Topological Sort*\
[Book website](https://cpbook.net/)

:memo: **Notes**

* Applications:
	* Job scheduling

<!--
	* Shortest path finding  TODO : add link
	 applications of this type arise in instruction scheduling, ordering of formula cell evaluation when recomputing formula values in spreadsheets, logic synthesis, determining the order of compilation tasks to perform in makefiles, data serialization, and resolving symbol dependencies in linkers. It is also used to decide in which order to load tables with foreign keys in databases.
-->

#### DFS-based topological sorting

:movie_camera: **Videos**

* MIT OCW 6.006 Introduction to algorithms (2011) &ndash; *Topological Sort*\
[Watch at YouTube](https://www.youtube.com/watch?v=AfSk24UTFS8&t=2515) (from 41:55) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:book: **Books**

* T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009 &ndash; Sec. 22.4: *Topological sort*\
[Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
* S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008 &ndash; Sec. 5.10.1: *Topological sorting*\
[Book website](http://www.algorist.com/)


#### Kahn's algorithm

:link: **Webpages**

[`tsort.c` by Mark Kettenis](http://agentzh.org/misc/code/coreutils/tsort.c.html)

:book: **Books**

* D.E.Knuth. *The Art of Computer Programming, Vol. 1: Fundamental Algorithms*. Addison-Wesley, 3<sup>rd</sup> ed., 1997 &ndash; Sec. 2.2.3: *Linked allocation*\
[Book website](https://www-cs-faculty.stanford.edu/~knuth/taocp.html)

:page_facing_up: **Papers**

* A.B.Kahn. *Topological sorting of large networks*. Communications of the ACM **5**, [558](https://dx.doi.org/10.1145/368996.369025) (1962)

<!--
:memo: *Notes*

* Applications:
	* Coffman&ndash;Graham algorithm
	* Layered graph drawing
-->
