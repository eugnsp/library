# Randomized algorithms and probabilistic data structures <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Probability theory](#probability-theory)
- [Random numbers generation](#random-numbers-generation)
	- [Pseudorandom numbers generation](#pseudorandom-numbers-generation)
- [Random sampling](#random-sampling)
	- [Selection sampling](#selection-sampling)
	- [Reservoir sampling](#reservoir-sampling)
- [Random shuffling](#random-shuffling)
	- [Fisher–Yates algorithm](#fisheryates-algorithm)
- [Probabilistic datastructures](#probabilistic-datastructures)
	- [Bloom filter](#bloom-filter)
	- [Skip lists](#skip-lists)
- [HyperLogLog](#hyperloglog)

---

## Probability theory

:movie_camera:

- E.Lawrence. *Why use measure theory for probability?* [Part I](https://www.youtube.com/watch?v=RjPXfUT7Odo), [Part II](https://www.youtube.com/watch?v=Q9KOeP-nrYQ), [Part III](https://www.youtube.com/watch?v=rAYA2Mu51bw) (2012)

---

## Random numbers generation

### Pseudorandom numbers generation

:link:

- [*Xorshift*](https://en.wikipedia.org/wiki/Xorshift) – Wikipedia

---

## Random sampling

:book:

- Sec. 3.4.2: *Random sampling and shuffling* – D.E.Knuth. [*The art of computer programming.*](https://www-cs-faculty.stanford.edu/~knuth/taocp.html) *Vol. 2: Seminumerical algorithms* (1997)

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

- N.Ormrod. [*Fantastic algorithms and where to find them*: Reservoir sampling](https://www.youtube.com/watch?v=YA-nB2wjVcI&t=1268) – CppCon (2017)

## Random shuffling

:link:

- J.Atwood. [*The danger of naïveté*](https://blog.codinghorror.com/the-danger-of-naivete/) (2007)

:book:

- Sec. 3.4.2: *Random sampling and shuffling* – D.E.Knuth. [*The art of computer programming.*](https://www-cs-faculty.stanford.edu/~knuth/taocp.html) *Vol. 2: Seminumerical algorithms* (1997)

### Fisher–Yates algorithm

:link:

- [*Fisher–Yates shuffle*](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle) – Wikipedia
- [*Knuth shuffle*](https://www.rosettacode.org/wiki/Knuth_shuffle) – Rosetta Code

---

## Probabilistic datastructures

### Bloom filter

> Bloom filter is a space-efficient probabilistic data structure that is used to test whether an element is a member of a set. False positive matches are possible, but false negatives are not.

:link:

- [*Bloom filter*](https://en.wikipedia.org/wiki/Bloom_filter) – Wikipedia
- [*Bloom filter calculator*](https://hur.st/bloomfilter/)
- M.Majkowski. [*When Bloom filters don’t bloom*](https://blog.cloudflare.com/when-bloom-filters-dont-bloom/) (2020)
- J.Talbot. [*What are Bloom filters?*](https://blog.medium.com/what-are-bloom-filters-1ec2a50c68ff) (2015)

:movie_camera:

- A.Deutsch. [*Esoteric data structures and where to find them*](https://www.youtube.com/watch?v=-8UZhDjgeZU&t=603) – CppCon (2017)
- R.Edwards. [*Bloom filters*](https://www.youtube.com/watch?v=heEDL9usFgs)
- N.L.Gowda. [*Bloom filter for system design*](https://www.youtube.com/watch?v=Bay3X9PAX5k)

:page_facing_up:

- A.Broder, M.Mitzenmacher. [*Network applications of Bloom filters: A survey*](https://www.cs.princeton.edu/courses/archive/spring05/cos598E/bib/broder-survey.pdf) – [Internet Mathematics **1**, 485](https://doi.org/10.1080/15427951.2004.10129096) (2004)
- B.H.Bloom. [*Space/time trade-offs in hash coding with allowable errors*](https://www.cs.princeton.edu/courses/archive/spring05/cos598E/bib/p422-bloom.pdf) – [Communications of the ACM **13**, 422](https://doi.org/10.1145/362686.362692) (1970)

:book:

- Sec. 12.5: *Bloom filters: The basics*, Sec. 12.6: *Bloom filters: Heuristic analysis* – Roughgarden T. [*Algorithms illuminated (Part 2): Graph algorithms and data structures*](http://timroughgarden.org/books.html) – Soundlikeyourself Publishing (2018)

:dizzy:

- J.Davies. [*Bloom filters*](https://www.jasondavies.com/bloomfilter/)

### Skip lists

:movie_camera:

- [*Randomization: Skip lists*](https://www.youtube.com/watch?v=2g9OSRKJuzM) – MIT OCW 6.046J/18.410J: [Design and analysis of algorithms](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-design-and-analysis-of-algorithms-spring-2015/) (2015)

:page_facing_up:

- W.Pugh. [*A skip list cookbook*](http://cglab.ca/~morin/teaching/5408/refs/p90b.pdf) – Tech. Rep. UMIACS-TR-89-72.1 (1990)

---

## HyperLogLog

:link:

- [*HyperLogLog*](https://en.wikipedia.org/wiki/HyperLogLog) – Wikipedia

:movie_camera:

- N.Ormrod. [*Fantastic algorithms and where to find them*: HyperLogLog](https://www.youtube.com/watch?v=YA-nB2wjVcI&t=1653) – CppCon (2017)
