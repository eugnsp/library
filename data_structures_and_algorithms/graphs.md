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
* [Connectivity](#connectivity)
	* [Biconnectivity](#biconnectivity)
		* [Articulation points and bridges](#articulation-points-and-bridges)
		* [Biconnected components](#biconnected-components)
* Shortest paths
	* Single-source shortest paths
	* All-pairs shortest paths
	* Travelling salesman problem
---

## Data structures

:book:

* Sec. 5.2: *Data structures for graphs* &ndash; S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008.\
[Book website](http://www.algorist.com/)

---

## Traversal

### Breadth-first search (BFS)

> Breadth-first search is an algorithm for traversing or searching a graph that explores all of the neighbour nodes at the present depth prior to moving on to the nodes at the next depth level.

:link:

* [*Breadth-first search* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Breadth-first_search)

:movie_camera:

* *Breadth-first search* &ndash; MIT OCW 6.006: Introduction to algorithms (2011).\
[Watch at YouTube](https://www.youtube.com/watch?v=s-CYnVz-uh4) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:book:

* Sec. 22.2: *Breadth-first search* &ndash; T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009.\
[Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
* Sec. 5.6: *Breadth-first search* &ndash; S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008.\
[Book website](http://www.algorist.com/)
* Sec. 4.2.2: *Breadth first search* &ndash; S.Halim, F.Halim. *Competitive programming.* 3<sup>rd</sup> ed., 2013.\
[Book website](https://cpbook.net/)

<!-- :memo:

* Applications:
	* Connected components
	* Two-colouring -->

### Depth-first search (DFS)

> Depth-first search is an algorithm for traversing or searching a graph that explores as far as possible along each branch before backtracking.

:memo:

* DFS can be used for [cycle detection](#cycle-detection), [topological sorting](#dfs-based-topological-sorting), finding [articulation points and bridges](#articulation-points-and-bridges), fiding [biconnected components](#biconnected-components).

:movie_camera:

* *Depth-first search (DFS)* &ndash; MIT OCW 6.006 Introduction to algorithms (2011).\
[Watch at YouTube](https://www.youtube.com/watch?v=AfSk24UTFS8) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:book:

* Sec. 22.3: *Depth-first search* &ndash; T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009.\
[Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
* Sec. 5.8: *Depth-first search*, Sec. 5.10: *Depth-first search on directed graphs* &ndash; S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008.\
[Book website](http://www.algorist.com/)
* Sec. 4.2.1: *Depth first search* &ndash; S.Halim, F.Halim. *Competitive programming*. 3<sup>rd</sup> ed., 2013.\
[Book website](https://cpbook.net/)

### Cycle detection

:movie_camera:

* *Depth-first search (DFS)* &ndash; MIT OCW 6.006: Introduction to algorithms (2011).\
[Watch at YouTube](https://www.youtube.com/AfSk24UTFS8?t=1093) (from 18:13) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

### Topological sorting

> Topological sorting of a directed acyclic graph (DAG) is a linear ordering of its vertices such that for every directed edge <code>(u &rarr; v)</code>, vertex `u` comes before vertex `v` in the ordering.

:link:

* [*Topological sorting* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Topological_sorting)
* [*Topological sorting* &ndash; SB Algorithm Repository](http://www3.cs.stonybrook.edu/~algorith/files/topological-sorting.shtml)

:book:

* Sec. 4.2.5: *Topological sort* &ndash; S.Halim, F.Halim. *Competitive programming*. 3<sup>rd</sup> ed., 2013.\
[Book website](https://cpbook.net/)

:memo:

* Applications:
	* Job scheduling

<!--
	* Shortest path finding  TODO : add link
	 applications of this type arise in instruction scheduling, ordering of formula cell evaluation when recomputing formula values in spreadsheets, logic synthesis, determining the order of compilation tasks to perform in makefiles, data serialization, and resolving symbol dependencies in linkers. It is also used to decide in which order to load tables with foreign keys in databases.
-->

#### DFS-based topological sorting

:movie_camera:

* *Topological Sort* &ndash; MIT OCW 6.006: Introduction to algorithms (2011).\
[Watch at YouTube](https://www.youtube.com/watch?v=AfSk24UTFS8&t=2515) (from 41:55) |
[Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:book:

* Sec. 22.4: *Topological sort* &ndash; T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009.\
[Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
* Sec. 5.10.1: *Topological sorting* &ndash; S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008.\
[Book website](http://www.algorist.com/)

#### Kahn's algorithm

:link:

[*`tsort.c` source code* &ndash; M.Kettenis](http://agentzh.org/misc/code/coreutils/tsort.c.html)

:book:

* Sec. 2.2.3: *Linked allocation* &ndash; D.E.Knuth. *The art of computer programming. Vol. 1: Fundamental algorithms*. Addison-Wesley, 3<sup>rd</sup> ed., 1997.\
[Book website](https://www-cs-faculty.stanford.edu/~knuth/taocp.html)

:page_facing_up:

* A.B.Kahn. *Topological sorting of large networks*. Communications of the ACM **5**, [558](https://dx.doi.org/10.1145/368996.369025) (1962).

<!--
:memo: *Notes*

* Applications:
	* Coffman&ndash;Graham algorithm
	* Layered graph drawing
-->

---

## Connectivity

:link:

* [Graph connectivity &ndash; AlgoWiki](https://algowiki-project.org/en/Graph_connectivity)

:page_facing_up:

* *Algorithm 447: Efficient algorithms for graph manipulation* &ndash; J.Hopcroft, R.Tarjan. Communications of the ACM **16**, [372](https://doi.org/10.1145/362248.362272) (1973).\
[Full text](http://akira.ruc.dk/~keld/teaching/algoritmedesign_f03/Artikler/06/Hopcroft73.pdf)

### Biconnectivity

:book:

* Ch. 30: *Connectivity*, Sec.: *Biconnectivity* &ndash; R.Sedgewick. *Algorithms*. Addison-Wesley, 1983.
* Sec. 6.4: *Biconnected components and DFS* &ndash; E.Horowitz, S.Sahni, S.Rajasekaran. *Computer algorithms*. W.H.Freeman, 1997.

#### Articulation points and bridges

> An articulation point (cut vertex) is a vertex which, if deleted, would increase the number connected components. A bridge (cut adge) is an edge which, if deleted, would increase the number of connected components.

:movie_camera:

* *Bridges and articulation points algorithm* &ndash;William Fiset\
[Watch at YouTube](https://www.youtube.com/watch?v=aZXi1unBdJA)

#### Biconnected components

> A biconnected component is a set of vertices mutually accessible via two distinct paths.

:link:

* [Biconnected component &ndash; Wikipedia](https://en.wikipedia.org/wiki/Biconnected_component)
