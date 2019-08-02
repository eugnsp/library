# Combinatorial algorithms

## Table of contents

* [Permutations](#permutations)
	* [Generating permutations](#generating-permutations)
		* [Algorithm L](#algorithm-l)
		* [Heap's algorithm](#heaps-algorithm)

---

## Permutations

https://stackoverflow.com/questions/31773203/is-it-possible-to-invert-an-array-with-constant-extra-space

### Generating permutations

#### Algorithm L

> Algorithm L for the given sequence of `n` elements <code>(a<sub>0</sub>...a<sub>n-1</sub>)</code>, initially sorted so that <code>(a<sub>0</sub> &leq; a<sub>1</sub> &leq; ... &leq; a<sub>k-1</sub>)</code>, generates all permutations visiting them in the lexicographic order.

:memo:

* This algorithm is used in some implementations of `std::next_permutation` in the Standard library.

:link:

* [`std::next_permutation` implementation explanation &ndash; Stack Overflow](https://stackoverflow.com/questions/11483060/stdnext-permutation-implementation-explanation)

:book:

* Sec. 7.2.1.2: *Generating all permutations* &ndash; D.E.Knuth. *The art of computer programming. Vol. 4A: Combinatorial algorithms, Part 1*. Addison-Wesley (2011)\
[Book website](https://www-cs-faculty.stanford.edu/~knuth/taocp.html)

#### Heap's algorithm

> Heap's algorithm generates all possible permutations of `n` objects. The algorithm minimizes movement: it generates each permutation from the previous one by interchanging a single pair of elements; the other `n - 2` elements are not disturbed.

:link:

* [Heap's algorithm &ndash; Wikipedia](https://en.wikipedia.org/wiki/Heap%27s_algorithm)
* [Heap algorithm for permutations &ndash; Stack Overflow](https://stackoverflow.com/questions/31425531/heap-algorithm-for-permutations)

