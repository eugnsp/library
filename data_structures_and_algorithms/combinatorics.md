# Combinatorial algorithms

## Table of contents

* [Permutations](#permutations)
	* [Generating permutations](#generating-permutations)
		* [Algorithm L](#algorithm-l)
		* [Heap's algorithm](#heaps-algorithm)
	* [Generating random permutations](#generating-random-permutations)
		* [Fisher&ndash;Yates algorithm](#fisheryates-algoritm)

---

## Permutations

https://stackoverflow.com/questions/31773203/is-it-possible-to-invert-an-array-with-constant-extra-space

### Generating permutations

#### Algorithm L

> Algorithm L for the given sequence of `n` initially sorted elements <code>{a<sub>0</sub> &leq; a<sub>1</sub> &leq; ... &leq; a<sub>n-1</sub>}</code>, generates all permutations visiting them in the lexicographic order. Gist of the algorithm: for the current permutation, find the longest descreasing subsequence on the right, <code>{...a<sub>p</sub> &leq; a<sub>i</sub> &gt; a<sub>j</sub> &gt; ... &gt; a<sub>k</sub>}</code>, find the next front element <code>a<sub>f</sub> &gt; a<sub>p</sub></code> with the largest possible `f` in the range `[i, k]`, swap <code>a<sub>f</sub></code> and <code>a<sub>p</sub></code>, and then put the remaining elements in the ascending order, i.e. reverse the subsequence <code>{a<sub>i</sub>...a<sub>p</sub>...a<sub>k</sub>}</code>.

:memo:

* This algorithm is used in some implementations of `std::next_permutation` in the standard library.

:link:

* [*`std::next_permutation` implementation explanation* &ndash; Stack Overflow](https://stackoverflow.com/questions/11483060/stdnext-permutation-implementation-explanation)

:book:

* Sec. 7.2.1.2: *Generating all permutations* &ndash; D.E.Knuth. *The art of computer programming. Vol. 4A: Combinatorial algorithms, Part 1*. Addison-Wesley (2011)\
[Book website](https://www-cs-faculty.stanford.edu/~knuth/taocp.html)

#### Heap's algorithm

> Heap's algorithm generates all possible permutations of `n` objects. The algorithm minimizes movement: it generates each permutation from the previous one by interchanging a single pair of elements; the other `n - 2` elements are not disturbed.

:link:

* [*Heap's algorithm* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Heap%27s_algorithm)
* [*Heap algorithm for permutations* &ndash; Stack Overflow](https://stackoverflow.com/questions/31425531/heap-algorithm-for-permutations)

### Generating random permutations

#### Fisher&ndash;Yates algorithm

:memo:

* This algorithm is also known as the Knuth shuffle algorithm or algorithm P.

:link:

* [*Fisher&ndash;Yates shuffle* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle)
* [*Knuth shuffle* &ndash; Rosetta Code](https://www.rosettacode.org/wiki/Knuth_shuffle)
