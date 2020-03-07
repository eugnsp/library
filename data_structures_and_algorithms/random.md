# Randomized algorithms and probabilistic data structures <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Random numbers generation](#random-numbers-generation)
	- [Pseudorandom numbers generation](#pseudorandom-numbers-generation)
- [Random sampling](#random-sampling)
	- [Selection sampling](#selection-sampling)
	- [Reservoir sampling](#reservoir-sampling)
- [Random shuffling](#random-shuffling)
	- [Fisher–Yates algorithm](#fisheryates-algorithm)
- [Probabilistic datastructures](#probabilistic-datastructures)
	- [Bloom filter](#bloom-filter)

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

:dizzy:

- J.Davies. [*Bloom filters*](https://www.jasondavies.com/bloomfilter/)
