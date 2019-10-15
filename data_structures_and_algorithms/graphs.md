# Graphs <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Data structures](#data-structures)
- [Traversal](#traversal)
	- [Breadth-first search (BFS)](#breadth-first-search-bfs)
	- [Depth-first search (DFS)](#depth-first-search-dfs)
	- [Cycle detection](#cycle-detection)
	- [Topological sorting](#topological-sorting)
		- [DFS-based topological sorting](#dfs-based-topological-sorting)
		- [Kahn's algorithm](#kahns-algorithm)
- [Connectivity](#connectivity)
	- [Biconnectivity](#biconnectivity)
		- [Articulation points and bridges](#articulation-points-and-bridges)
		- [Biconnected components](#biconnected-components)
---

## Data structures

:book:

- Sec. 5.2: *Data structures for graphs* &ndash; S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008.\
[Book website](http://www.algorist.com/)

---

## Traversal

### Breadth-first search (BFS)

> Breadth-first search is an algorithm for traversing or searching a graph that explores all of the neighbour nodes at the present depth prior to moving on to the nodes at the next depth level.

:link:

- [*Breadth-first search* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Breadth-first_search)

:movie_camera:

- [*Breadth-first search*](https://www.youtube.com/watch?v=s-CYnVz-uh4) &ndash; MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

:book:

- Sec. 22.2: *Breadth-first search* &ndash; T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)
- Sec. 5.6: *Breadth-first search* &ndash; S.S.Skiena. [*The algorithm design manual*](http://www.algorist.com/) (2008)
- Sec. 4.2.2: *Breadth first search* &ndash; S.Halim, F.Halim. [*Competitive programming*](https://cpbook.net/) (2013)

<!-- :memo:

- Applications:
	* Connected components
	* Two-colouring -->

### Depth-first search (DFS)

> Depth-first search is an algorithm for traversing or searching a graph that explores as far as possible along each branch before backtracking.

:memo:

- [Data structures](#data-structures)
- [Traversal](#traversal)
	- [Breadth-first search (BFS)](#breadth-first-search-bfs)
	- [Depth-first search (DFS)](#depth-first-search-dfs)
	- [Cycle detection](#cycle-detection)
	- [Topological sorting](#topological-sorting)
		- [DFS-based topological sorting](#dfs-based-topological-sorting)
		- [Kahn's algorithm](#kahns-algorithm)
- [Connectivity](#connectivity)
	- [Biconnectivity](#biconnectivity)
		- [Articulation points and bridges](#articulation-points-and-bridges)
		- [Biconnected components](#biconnected-components)

:movie_camera:

- [*Depth-first search (DFS)*](https://www.youtube.com/watch?v=AfSk24UTFS8) &ndash; MIT OCW 6.006 [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

:book:

- Sec. 22.3: *Depth-first search* &ndash; T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)
- Sec. 5.8: *Depth-first search*, Sec. 5.10: *Depth-first search on directed graphs* &ndash; S.S.Skiena. [*The algorithm design manual*](http://www.algorist.com/) (2008)
- Sec. 4.2.1: *Depth first search* &ndash; S.Halim, F.Halim. [*Competitive programming*](https://cpbook.net/) (2013)

### Cycle detection

:movie_camera:

- [*Depth-first search (DFS)*](https://www.youtube.com/AfSk24UTFS8?t=1093) &ndash; MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

### Topological sorting

> Topological sorting of a directed acyclic graph (DAG) is a linear ordering of its vertices such that for every directed edge <code>(u &rarr; v)</code>, vertex `u` comes before vertex `v` in the ordering.

:link:

- [*Topological sorting*](https://en.wikipedia.org/wiki/Topological_sorting) &ndash; Wikipedia
- [*Topological sorting*](http://www3.cs.stonybrook.edu/~algorith/files/topological-sorting.shtml) &ndash; SB Algorithm Repository

:book:

- Sec. 4.2.5: *Topological sort* &ndash; S.Halim, F.Halim. [*Competitive programming*](https://cpbook.net/) (2013)

:memo:

- Applications: job scheduling

<!--
	* Shortest path finding  TODO : add link
	 applications of this type arise in instruction scheduling, ordering of formula cell evaluation when recomputing formula values in spreadsheets, logic synthesis, determining the order of compilation tasks to perform in makefiles, data serialization, and resolving symbol dependencies in linkers. It is also used to decide in which order to load tables with foreign keys in databases.
-->

#### DFS-based topological sorting

:movie_camera:

- [*Topological sort*](https://www.youtube.com/watch?v=AfSk24UTFS8&t=2515) &ndash; MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

:book:

- Sec. 22.4: *Topological sort* &ndash; T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)
- Sec. 5.10.1: *Topological sorting* &ndash; S.S.Skiena. [*The algorithm design manual*](http://www.algorist.com/) (2008)

#### Kahn's algorithm

:link:

- M.Kettenis. [*`tsort.c` source code*](http://agentzh.org/misc/code/coreutils/tsort.c.html)

:book:

- Sec. 2.2.3: *Linked allocation* &ndash; D.E.Knuth. [*The art of computer programming.*](https://www-cs-faculty.stanford.edu/~knuth/taocp.html) *Vol. 1: Fundamental algorithms* (1997)

:page_facing_up:

- A.B.Kahn. *Topological sorting of large networks* &ndash; [Communications of the ACM **5**, 558](https://dx.doi.org/10.1145/368996.369025) (1962)

<!--
:memo: *Notes*

- Applications:
	* Coffman&ndash;Graham algorithm
	* Layered graph drawing
-->

---

## Connectivity

:link:

- [*Graph connectivity* &ndash; AlgoWiki](https://algowiki-project.org/en/Graph_connectivity)

:page_facing_up:

- J.Hopcroft, R.Tarjan. [*Algorithm 447: Efficient algorithms for graph manipulation*](http://akira.ruc.dk/~keld/teaching/algoritmedesign_f03/Artikler/06/Hopcroft73.pdf) &ndash; [Communications of the ACM **16**, 372](https://doi.org/10.1145/362248.362272) (1973)

### Biconnectivity

:book:


- Ch. 30: *Connectivity*, Sec.: *Biconnectivity* &ndash; R.Sedgewick. *Algorithms* (1983)
- Sec. 6.4: *Biconnected components and DFS* &ndash; E.Horowitz, S.Sahni, S.Rajasekaran. *Computer algorithms* (1997)

#### Articulation points and bridges

> An articulation point (cut vertex) is a vertex which, if deleted, would increase the number connected components. A bridge (cut adge) is an edge which, if deleted, would increase the number of connected components.

:movie_camera:

- W.Fiset. [*Bridges and articulation points algorithm*](https://www.youtube.com/watch?v=aZXi1unBdJA)

#### Biconnected components

> A biconnected component is a set of vertices mutually accessible via two distinct paths.

:link:

- [*Biconnected component*](https://en.wikipedia.org/wiki/Biconnected_component) &ndash; Wikipedia
