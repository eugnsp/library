# Graphs <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Data structures](#data-structures)
- [Traversal](#traversal)
	- [Breadth-first search (BFS)](#breadth-first-search-bfs)
	- [Depth-first search (DFS)](#depth-first-search-dfs)
		- [Morris traversal](#morris-traversal)
	- [Cycle detection](#cycle-detection)
	- [Topological sorting](#topological-sorting)
		- [DFS-based topological sorting](#dfs-based-topological-sorting)
		- [Kahn’s algorithm](#kahns-algorithm)
- [Connectivity](#connectivity)
	- [Biconnectivity](#biconnectivity)
		- [Articulation points and bridges](#articulation-points-and-bridges)
		- [Biconnected components](#biconnected-components)
- [Shortest path](#shortest-path)
	- [Single source shortest paths](#single-source-shortest-paths)
		- [Dijsktra’s algorithm](#dijsktras-algorithm)
		- [Bellman–Ford’s algorithm](#bellmanfords-algorithm)
		- [A\* algorithm](#a-algorithm)
	- [All pairs shortest paths](#all-pairs-shortest-paths)
		- [Floyd–Warshall’s algorithm](#floydwarshalls-algorithm)
- [Minimum spanning tree](#minimum-spanning-tree)
	- [Kruskal’s algorithm](#kruskals-algorithm)

---

## Data structures

:book:

- Sec. 5.2: *Data structures for graphs* – S.S.Skiena. *The algorithm design manual* – Springer (2008)

---

## Traversal

:book:

- Sec. 6.4: *Tree traversal* – Drozdek A. *Data structures and algorithms in C++* – Cengage Learning (2012)

### Breadth-first search (BFS)

> Breadth-first search is an algorithm for traversing or searching a graph that explores all of the neighbour nodes at the present depth prior to moving on to the nodes at the next depth level.

:link:

- [*Breadth-first search* – Wikipedia](https://en.wikipedia.org/wiki/Breadth-first_search)

:movie_camera:

- [*Breadth-first search*](https://www.youtube.com/watch?v=s-CYnVz-uh4) – MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

:book:

- Sec. 22.2: *Breadth-first search* – T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)
- Sec. 5.6: *Breadth-first search* – S.S.Skiena. [*The algorithm design manual*](http://www.algorist.com/) (2008)
- Sec. 4.2.2: *Breadth first search* – S.Halim, F.Halim. [*Competitive programming*](https://cpbook.net/) (2013)

<!-- :memo:

- Applications:
	* Connected components
	* Two-colouring -->

### Depth-first search (DFS)

> Depth-first search is an algorithm for traversing or searching a graph that explores as far as possible along each branch before backtracking. It can be used for [cycle detection](#cycle-detection), [topological sorting](#dfs-based-topological-sorting), finding [articulation points and bridges](#articulation-points-and-bridges), finding [biconnected components](#biconnected-components).

:movie_camera:

- [*Depth-first search (DFS)*](https://www.youtube.com/watch?v=AfSk24UTFS8) – MIT OCW 6.006 [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

:book:

- Sec. 22.3: *Depth-first search* – T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)
- Sec. 5.8: *Depth-first search*, Sec. 5.10: *Depth-first search on directed graphs* – S.S.Skiena. [*The algorithm design manual*](http://www.algorist.com/) (2008)
- Sec. 4.2.1: *Depth first search* – S.Halim, F.Halim. [*Competitive programming*](https://cpbook.net/) (2013)

#### Morris traversal

:link:

- [*Morris in-order traversal using threading*](https://en.wikipedia.org/wiki/Tree_traversal#Morris_in-order_traversal_using_threading) – Wikipedia

:grey_question:

- [*Explain Morris inorder tree traversal without using stacks or recursion*](https://stackoverflow.com/q/5502916) – Stack Overflow

:movie_camera:

- N.Ormrod. [*Fantastic algorithms and where to find them: Morris traversal*](https://www.youtube.com/watch?v=YA-nB2wjVcI&t=703) – CppCon (2017)

:page_facing_up:

- P.Mateti, R.Manghirmalani. *Morris’ tree traversal algorithm reconsidered* – [Science of Computer Programming **11**, 29](https://doi.org/10.1016/0167-6423%2888%2990063-9) (1988)
- J.M.Morris. *Traversing binary trees simply and cheaply* – [Information Processing Letters **9**, 197](https://doi.org/10.1016/0020-0190%2879%2990068-1) (1979)

### Cycle detection

:movie_camera:

- [*Depth-first search (DFS)*](https://www.youtube.com/AfSk24UTFS8?t=1093) – MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

### Topological sorting

> Topological sorting of a directed acyclic graph (DAG) is a linear ordering of its vertices such that for every directed edge <code>(u &rarr; v)</code>, vertex `u` comes before vertex `v` in the ordering.

:link:

- [*Topological sorting*](https://en.wikipedia.org/wiki/Topological_sorting) – Wikipedia
- [*Topological sorting*](http://www3.cs.stonybrook.edu/~algorith/files/topological-sorting.shtml) – SB Algorithm Repository

:book:

- Sec. 4.2.5: *Topological sort* – S.Halim, F.Halim. [*Competitive programming*](https://cpbook.net/) (2013)
- Sec. 3.6: *Directed acyclic graphs and topological ordering* – J.Kleinberg, É.Tardos. [*Algorithm design*](https://www.cs.cornell.edu/home/kleinber/) – [Pearson](https://www.pearson.com/us/higher-education/program/Kleinberg-Algorithm-Design/PGM319216.html) (2005)

:memo:

- Applications: job scheduling

<!--
	* Shortest path finding  TODO : add link
	 applications of this type arise in instruction scheduling, ordering of formula cell evaluation when recomputing formula values in spreadsheets, logic synthesis, determining the order of compilation tasks to perform in makefiles, data serialization, and resolving symbol dependencies in linkers. It is also used to decide in which order to load tables with foreign keys in databases.
-->

#### DFS-based topological sorting

:movie_camera:

- [*Topological sort*](https://www.youtube.com/watch?v=AfSk24UTFS8&t=2515) – MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

:book:

- Sec. 22.4: *Topological sort* – T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. [*Introduction to algorithms*](https://mitpress.mit.edu/books/introduction-algorithms-third-edition) (2009)
- Sec. 5.10.1: *Topological sorting* – S.S.Skiena. [*The algorithm design manual*](http://www.algorist.com/) (2008)

#### Kahn’s algorithm

:link:

- M.Kettenis. [*`tsort.c` source code*](http://agentzh.org/misc/code/coreutils/tsort.c.html)

:book:

- Sec. 2.2.3: *Linked allocation* – D.E.Knuth. [*The art of computer programming.*](https://www-cs-faculty.stanford.edu/~knuth/taocp.html) *Vol. 1: Fundamental algorithms* (1997)

:page_facing_up:

- A.B.Kahn. *Topological sorting of large networks* – [Communications of the ACM **5**, 558](https://dx.doi.org/10.1145/368996.369025) (1962)

<!--
:memo: *Notes*

- Applications:
	* Coffman–Graham algorithm
	* Layered graph drawing
-->

---

## Connectivity

:link:

- [*Graph connectivity* – AlgoWiki](https://algowiki-project.org/en/Graph_connectivity)

:page_facing_up:

- J.Hopcroft, R.Tarjan. [*Algorithm 447: Efficient algorithms for graph manipulation*](http://akira.ruc.dk/~keld/teaching/algoritmedesign_f03/Artikler/06/Hopcroft73.pdf) – [Communications of the ACM **16**, 372](https://doi.org/10.1145/362248.362272) (1973)

### Biconnectivity

:book:

- Ch. 30: *Connectivity*, Sec.: *Biconnectivity* – R.Sedgewick. *Algorithms* (1983)
- Sec. 6.4: *Biconnected components and DFS* – E.Horowitz, S.Sahni, S.Rajasekaran. *Computer algorithms* (1997)

#### Articulation points and bridges

> An articulation point (cut vertex) is a vertex which, if deleted, would increase the number connected components. A bridge (cut adge) is an edge which, if deleted, would increase the number of connected components.

:movie_camera:

- W.Fiset. [*Bridges and articulation points algorithm*](https://www.youtube.com/watch?v=aZXi1unBdJA)

#### Biconnected components

> A biconnected component is a set of vertices mutually accessible via two distinct paths.

:link:

- [*Biconnected component*](https://en.wikipedia.org/wiki/Biconnected_component) – Wikipedia

---

## Shortest path

### Single source shortest paths

:movie_camera:

- S.Devadas. [*Single-source shortest paths problem*](https://www.youtube.com/watch?v=Aa2sqUhIn-E) – MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

#### Dijsktra’s algorithm

:link:

- [*Dijkstra’s algorithm*](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm) – Wikipedia

:grey_question:

- [*Why does Dijkstra’s algorithm use decrease-key?*](https://stackoverflow.com/q/9255620) – Stack Overflow
- [*How to implement `O(log n)` decrease-key operation for min-heap-based priority queue?*](https://stackoverflow.com/q/17009056) – Stack Overflow

:movie_camera:

- S.Devadas. [*SSSP on DAGs and Dijkstra’s algorithm*](https://www.youtube.com/watch?v=2E7MmKv0Y24), [*Speeding up Dijkstra*](https://www.youtube.com/watch?v=CHvQ3q_gJ7E) – MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)
- M.Pound. [*Dijkstra’s algorithm*](https://www.youtube.com/watch?v=GazC3A4OQTE) – Computerphile

:book:

- Ch. 9: *Dijkstra’s shortest-path algorithm* – Roughgarden T. [*Algorithms illuminated (Part 2): Graph algorithms and data structures*](http://timroughgarden.org/books.html) – Soundlikeyourself Publishing (2018)
- Sec. 4.4: *Shortest paths in a graph* – J.Kleinberg, É.Tardos. [*Algorithm design*](https://www.cs.cornell.edu/home/kleinber/) – [Addison-Wesley](https://www.pearson.com/us/higher-education/program/Kleinberg-Algorithm-Design/PGM319216.html) (2005)
- Sec. 6.3: *The single source shortest paths problem* – A.V.Aho, J.E.Hopcroft, J.D.Ullman. *Data structures and algorithms* – Addison-Wesley (1983)

#### Bellman–Ford’s algorithm

:movie_camera:

- S.Devadas. [*SSSP on DAGs and Dijkstra’s algorithm*](https://www.youtube.com/watch?v=2E7MmKv0Y24) – MIT OCW 6.006: [Introduction to algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm) (2011)

#### A\* algorithm

:movie_camera:

- M.Pound. [*A\* search algorithm*](https://www.youtube.com/watch?v=ySN5Wnu88nE) – Computerphile

### All pairs shortest paths

#### Floyd–Warshall’s algorithm

:book:

- Sec. 4.5: *All-pairs shortest paths* – S.Halim, F.Halim. [*Competitive programming*](https://cpbook.net/) (2013)

---

## Minimum spanning tree

> A minimum spanning tree is a subset of the edges of a connected, edge-weighted undirected graph that connects all the vertices together, without any cycles and with the minimum possible total edge weight.

:link:

- [*Minimum spanning tree*](https://en.wikipedia.org/wiki/Minimum_spanning_tree) – Wikipedia

:book:

- Sec. 4.5: *The minimum spanning tree problem* – J.Kleinberg, É.Tardos. [*Algorithm design*](https://www.cs.cornell.edu/home/kleinber/) – [Pearson](https://www.pearson.com/us/higher-education/program/Kleinberg-Algorithm-Design/PGM319216.html) (2005)

### Kruskal’s algorithm

:book:

- Sec. 4.6: *Implementing Kruskal’s algorithm: The union-find data structure* – J.Kleinberg, É.Tardos. [*Algorithm design*](https://www.cs.cornell.edu/home/kleinber/) – [Pearson](https://www.pearson.com/us/higher-education/program/Kleinberg-Algorithm-Design/PGM319216.html) (2005)
