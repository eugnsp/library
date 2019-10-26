# String algorithms <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Lexicographically minimal string rotation](#lexicographically-minimal-string-rotation)
	- [Duval’s based algorithm](#duvals-based-algorithm)
- [Lyndon factorization](#lyndon-factorization)
	- [Duval’s algorithm](#duvals-algorithm)
- [String searching](#string-searching)
	- [Knuth&ndash;Morris&ndash;Pratt algorithm](#knuthndashmorrisndashpratt-algorithm)

---

## Lexicographically minimal string rotation

> Lexicographically minimal rotation if the rotation of a string possessing the lowest lexicographical order of all its rotations.

:link:

- [*Lexicographically minimal string rotation*](https://en.wikipedia.org/wiki/Lexicographically_minimal_string_rotation) &ndash; Wikipedia

### Duval’s based algorithm

:memo:

- This algorithm is also known as the Zhou Yuan’s minimal expression algorithm.

:link:

- [*Lyndon factorization*](https://cp-algorithms.com/string/lyndon_factorization.html) &ndash; CP-Algorithms
- [*How does the minimum expression algorithm by Zhou Yuan work?*](https://www.quora.com/How-does-the-minimum-expression-algorithm-by-Zhou-Yuan-work) &ndash; Quora

---

## Lyndon factorization

> Lyndon word is a (non-empty) string that is strictly smaller in lexicographic order than all of its rotations. Lyndon factorization is a decomposition of a string `s` into Lyndon words, <code>s = w<sub>1</sub>w<sub>2</sub>...w<sub>n</sub></code>, such that <code>w<sub>1</sub> &ge; w<sub>i</sub> &ge; ... &ge; w<sub>n</sub></code>.

:memo:

- [Lexicographically minimal string rotation](#lexicographically-minimal-string-rotation)
	- [Duval’s based algorithm](#duvals-based-algorithm)
- [Lyndon factorization](#lyndon-factorization)
	- [Duval’s algorithm](#duvals-algorithm)
- [String searching](#string-searching)
	- [Knuth&ndash;Morris&ndash;Pratt algorithm](#knuthndashmorrisndashpratt-algorithm)

:link:

- [*Lyndon word*](https://en.wikipedia.org/wiki/Lyndon_word) &ndash; Wikipedia

### Duval’s algorithm

:link:

- [*Lyndon factorization*](https://cp-algorithms.com/string/lyndon_factorization.html) &ndash; CP-Algorithms

:page_facing_up:

- J.P.Duval. *Factorizing words over an ordered alphabet* &ndash; [Journal of algorithms **8**, 363](https://dx.doi.org/10.1016/0196-6774(83)90017-2) (1983)
- S.S.Ghuman, E.Giaquinta, J.Tarhio. [*Alternative algorithms for Lyndon factorization*](https://arxiv.org/abs/1405.4892) &ndash; arXiv preprint (2014)

---

## String searching

### Knuth&ndash;Morris&ndash;Pratt algorithm

:link:

- [*Knuth&ndash;Morris&ndash;Pratt algorithm*](https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm) &ndash; Wikipedia

:movie_camera:

- W.Brinkman. [*KMP searching algorithm*](https://www.youtube.com/watch?v=y2b94AxPlF8) (2017)
