# Combinatorial algorithms <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Permutations](#permutations)
	- [Algorithm L](#algorithm-l)
	- [Heap’s algorithm](#heaps-algorithm)
	- [Random permutations](#random-permutations)

---

## Permutations

<!-- https://stackoverflow.com/questions/31773203/is-it-possible-to-invert-an-array-with-constant-extra-space -->

### Algorithm L

> Algorithm L for the given sequence of `n` initially sorted elements <code>{a<sub>0</sub> &leq; a<sub>1</sub> &leq; ... &leq; a<sub>n-1</sub>}</code>, generates all permutations visiting them in the lexicographic order. Gist of the algorithm: for the current permutation, find the longest decreasing subsequence on the right, <code>{...a<sub>p</sub> &leq; a<sub>i</sub> &gt; a<sub>j</sub> &gt; ... &gt; a<sub>k</sub>}</code>, find the next front element <code>a<sub>f</sub> &gt; a<sub>p</sub></code> with the largest possible `f` in the range `[i, k]`, swap <code>a<sub>f</sub></code> and <code>a<sub>p</sub></code>, and then put the remaining elements in the ascending order, i.e. reverse the subsequence <code>{a<sub>i</sub>...a<sub>p</sub>...a<sub>k</sub>}</code>.

:memo:

- This algorithm is used in some implementations of `std::next_permutation` in the standard library.

:link:

- [*`std::next_permutation` implementation explanation* – Stack Overflow](https://stackoverflow.com/q/11483060)

:book:

- Sec. 7.2.1.2: *Generating all permutations* – D.E.Knuth. [*The art of computer programming.*](https://www-cs-faculty.stanford.edu/~knuth/taocp.html) *Vol. 4A: Combinatorial algorithms, Part 1* (2011)

### Heap’s algorithm

> Heap’s algorithm generates all possible permutations of `n` objects. The algorithm minimizes movement: it generates each permutation from the previous one by interchanging a single pair of elements; the other `n - 2` elements are not disturbed.

:link:

- [*Heap’s algorithm*](https://en.wikipedia.org/wiki/Heap%27s_algorithm) – Wikipedia
- [*Heap algorithm for permutations*](https://stackoverflow.com/q/31425531) – Stack Overflow

### Random permutations

See [*Shuffling* – Randomized algorithms](random.md#shuffling).
