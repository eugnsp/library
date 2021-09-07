# Randomized algorithms and probabilistic data structures <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Probability theory](#probability-theory)
- [Random numbers generation](#random-numbers-generation)
- [Distributions](#distributions)
	- [Uniform distribution](#uniform-distribution)
- [Sampling](#sampling)
	- [Selection sampling](#selection-sampling)
	- [Reservoir sampling](#reservoir-sampling)
- [Shuffling](#shuffling)
	- [Fisher–Yates algorithm](#fisheryates-algorithm)
- [Probabilistic data structures](#probabilistic-data-structures)
	- [Skip lists](#skip-lists)
- [HyperLogLog](#hyperloglog)

---

## Probability theory

:movie_camera:

- E.Lawrence. *Why use measure theory for probability?* [Part I](https://www.youtube.com/watch?v=RjPXfUT7Odo), [Part II](https://www.youtube.com/watch?v=Q9KOeP-nrYQ), [Part III](https://www.youtube.com/watch?v=rAYA2Mu51bw) (2012)

---

## Random numbers generation

For cryptographically secure random number generation see [*Random numbers generation* – Cryptographic algorithms and data structures](cryptographic.md#random-numbers-generation).

:link:

- [*Xorshift*](https://en.wikipedia.org/wiki/Xorshift) – Wikipedia
- M.Marini. [*A class hierarchy for random number generation*](https://github.com/eugnsp/CUJ/blob/master/14.10/marini/marini.md) – C/C++ Users Journal **14** (1996)

---

## Distributions

### Uniform distribution

- D.Lemire. [*Nearly divisionless random integer generation on various systems*](https://lemire.me/blog/2019/06/06/nearly-divisionless-random-integer-generation-on-various-systems/) (2019)

---

## Sampling

:book:

- Sec. 3.4.2: *Random sampling and shuffling* – D.E.Knuth. [*The art of computer programming.*](https://www-cs-faculty.stanford.edu/~knuth/taocp.html) *Vol. 2: Seminumerical algorithms* (1997)
- Col. 12: *A sample problem* – J.Bentley. [*Programming pearls*](https://www.oreilly.com/library/view/programming-pearls-second/9780134498058/) (1999)

### Selection sampling

:link:

- [*Knuth’s algorithm S*](https://rosettacode.org/wiki/Knuth%27s_algorithm_S) – Rosetta Code
- B.Rieck. [*A technique for selection sampling (sampling without replacement)*](http://bastian.rieck.me/blog/posts/2017/selection_sampling/)

:page_facing_up:

- J.S.Vitter. [*An efficient algorithm for sequential random sampling*](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.94.1689&rep=rep1&type=pdf) – [ACM Transactions on Mathematical Software **13**, 58](https://doi.org/10.1145/23002.23003) (1987)

### Reservoir sampling

:link:

- [*Reservoir sampling*](https://en.wikipedia.org/wiki/Reservoir_sampling) – Wikipedia

:movie_camera:

- N.Ormrod. [*Fantastic algorithms and where to find them: Reservoir sampling*](https://www.youtube.com/watch?v=YA-nB2wjVcI&t=1268) – CppCon (2017)

---

## Shuffling

:link:

- J.Atwood. [*The danger of naïveté*](https://blog.codinghorror.com/the-danger-of-naivete/) (2007)

:book:

- Sec. 3.4.2: *Random sampling and shuffling* – D.E.Knuth. [*The art of computer programming.*](https://www-cs-faculty.stanford.edu/~knuth/taocp.html) *Vol. 2: Seminumerical algorithms* (1997)

### Fisher–Yates algorithm

:link:

- [*Fisher–Yates shuffle*](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle) – Wikipedia
- [*Knuth shuffle*](https://www.rosettacode.org/wiki/Knuth_shuffle) – Rosetta Code

---

## Probabilistic data structures

### Skip lists

:grey_question:

- [*How does a skip list work?*](https://softwareengineering.stackexchange.com/q/287254) – Software Engineering

:movie_camera:

- [*Randomization: Skip lists*](https://www.youtube.com/watch?v=2g9OSRKJuzM) – MIT OCW 6.046J/18.410J: [Design and analysis of algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-design-and-analysis-of-algorithms-spring-2015/) (2015)

:book:

- Sec. 3.4: *Skip lists* – Drozdek A. *Data structures and algorithms in C++* – Cengage Learning (2012)

:page_facing_up:

- W.Pugh. [*A skip list cookbook*](http://cglab.ca/~morin/teaching/5408/refs/p90b.pdf) – Tech. Rep. UMIACS-TR-89-72.1 (1990)

---

## HyperLogLog

:link:

- [*HyperLogLog*](https://en.wikipedia.org/wiki/HyperLogLog) – Wikipedia

:movie_camera:

- N.Ormrod. [*Fantastic algorithms and where to find them: HyperLogLog*](https://www.youtube.com/watch?v=YA-nB2wjVcI&t=1653) – CppCon (2017)
