# Graphs

## Table of contents

* [Data structures](#data-structures)
* [Traversal](#traversal)
	* [Breadth-first search (BFS)](#breadth-first-search-bfs)
	* [Depth-first search (DFS)](#depth-first-search-dfs)
	* [Cycle detection](#cycle-detection)
	* [Topological sorting](#topological-sorting)
* Shortest paths
	* Single-source shortest paths
	* All-pairs shortest paths
	* Travelling salesman problem

---

## Data structures

## Traversal

### Breadth-first search (BFS)

> Breadth-first search is an algorithm for traversing or searching a graph that explores all of the neighbour nodes at the present depth prior to moving on to the nodes at the next depth level.

:link: *Webpages*

* [Breadth-first search &ndash; Wikipedia](https://en.wikipedia.org/wiki/Breadth-first_search)

:movie_camera: *Videos*

* MIT OCW 6.006 Introduction to algorithms (2011) &ndash; *Breadth-First Search*\
[Watch at YouTube](https://www.youtube.com/watch?v=s-CYnVz-uh4) | [Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:book: *Books*

* T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009 &ndash; Sec. 22.2: *Breadth-first search*\
[Full text](https://labs.xjtudlc.com/labs/wldmt/reading%20list/books/Algorithms%20and%20optimization/Introduction%20to%20Algorithms.pdf) | [Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
* S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008 &ndash; Sec. 5.6: *Breadth-first search*\
[Full text](http://mimoza.marmara.edu.tr/~msakalli/cse706_12/SkienaTheAlgorithmDesignManual.pdf) | [Book website](http://www.algorist.com/)
* S.Halim, F.Halim. *Competitive Programming.* 3<sup>rd</sup> ed., 2013 &ndash; Sec. 4.2.2: *Breadth first search*

<!-- :memo: *Notes*

* Applications:
	* Connected components
	* Two-colouring -->

### Depth-first search (DFS)

> Depth-first search is an algorithm for traversing or searching a graph that explores as far as possible along each branch before backtracking.

:movie_camera: *Videos*

* MIT OCW 6.006 Introduction to algorithms (2011) &ndash; *Depth-First Search (DFS)*\
[Watch at YouTube](https://www.youtube.com/watch?v=AfSk24UTFS8) | [Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:book: *Books*

* T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009 &ndash; Sec. 22.3: *Depth-first search*\
[Full text](https://labs.xjtudlc.com/labs/wldmt/reading%20list/books/Algorithms%20and%20optimization/Introduction%20to%20Algorithms.pdf) | [Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
* S.S.Skiena. *The algorithm design manual*. Springer, 2<sup>nd</sup> ed., 2008 &ndash; Sec. 5.8: *Depth-first search*, Sec. 5.10: *Depth-first search on directed graphs*\
[Full text](http://mimoza.marmara.edu.tr/~msakalli/cse706_12/SkienaTheAlgorithmDesignManual.pdf) | [Book website](http://www.algorist.com/)
* S.Halim, F.Halim. *Competitive Programming.* 3<sup>rd</sup> ed., 2013 &ndash; Sec. 4.2.1: *Depth first search*

:memo: *Notes*

* Applications:
 	* [Cycle detection](#cycle-detection)
	* [Topological sort](#topological-sort)

### Cycle detection

:movie_camera: *Videos*

* MIT OCW 6.006 Introduction to algorithms (2011) &ndash; *Depth-First Search (DFS)*\
[Watch at YouTube](https://www.youtube.com/AfSk24UTFS8?t=1093) (from 18:13) | [Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

### Topological sorting

#### DFS-based topological sorting

:movie_camera: *Videos*

* MIT OCW 6.006 Introduction to algorithms (2011) &ndash; *Topological Sort*\
[Watch at YouTube](https://www.youtube.com/watch?v=AfSk24UTFS8&t=2515) (from 41:55) | [Course website](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

:book: *Books*

* T.H.Cormen, C.E.Leiserson, R.L.Rivest, C.Stein. *Introduction to algorithms*. The MIT Press, 3<sup>rd</sup> ed., 2009 &ndash; Sec. 22.4: *Topological sort*\
[Full text](https://labs.xjtudlc.com/labs/wldmt/reading%20list/books/Algorithms%20and%20optimization/Introduction%20to%20Algorithms.pdf) | [Book website](https://mitpress.mit.edu/books/introduction-algorithms-third-edition)
* S.Halim, F.Halim. *Competitive Programming.* 3<sup>rd</sup> ed., 2013 &ndash; Sec. 4.2.5: *Topological Sort*

#### Khan's algorithm

:book: *Books*

* S.Halim, F.Halim. *Competitive Programming.* 3<sup>rd</sup> ed., 2013 &ndash; Sec. 4.2.5: *Topological Sort*
