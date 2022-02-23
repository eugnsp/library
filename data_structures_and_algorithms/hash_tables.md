# Hash tables and hashing <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
- [Hash functions](#hash-functions)
	- [Fowler–Noll–Vo hash function](#fowlernollvo-hash-function)
	- [Cryptographic hash functions](#cryptographic-hash-functions)
	- [Custom hash functions](#custom-hash-functions)
- [Hash tables](#hash-tables)
	- [Bloom filter](#bloom-filter)
	- [Extendible hashing](#extendible-hashing)
- [Consistent hashing](#consistent-hashing)
- [Implementations](#implementations)

---

## Introduction and overview

:link:

- R.L.Burk. [*Hashing: From good to perfect*](https://github.com/eugnsp/CUJ/blob/master/10.02/burk/burk.md) – C/C++ Users Journal **10** (1992)

## Hash functions

> A hash function is a function that maps data of arbitrary size to fixed-size values. A good hash function satisfies two basic properties: it should be very fast to compute and it should minimize duplication of output values (collisions). Hashing in the C++ standard library is implemented via `std::hash<T>` function object type.

:link:

- [*Hash function*](https://en.wikipedia.org/wiki/Hash_function) – Wikipedia

:grey_question:

- [*Why is XOR the default way to combine hashes?*](https://stackoverflow.com/q/5889238) – Stack Overflow
- [*Why does Java’s `hashCode()` in `String` use 31 as a multiplier?*](https://stackoverflow.com/q/299304) – Stack Overflow

:movie_camera:

- D.K&uuml;hl. [*#Hashing*](https://www.youtube.com/watch?v=CJsQSIp7-Ig) – ACCU (2019)

### Fowler–Noll–Vo hash function

> The FNV hashing algorithm is used in the `std::hash` implementation in the Microsoft standard library.

### Cryptographic hash functions

See [*Hashing* – Cryptographic algorithms](cryptographic.md#hashing).

### Custom hash functions

:link:

- [*xxHash – Extremely fast hash algorithm*](https://github.com/Cyan4973/xxHash)

## Hash tables

> A hash table is a data structure that implements an associative array abstract data type, a structure that can map keys to values. A hash table uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found. Hash tables in the C++ standard library go by the names of `std::unordered_[multi]set` and `std::unordered_[multi]map`. See [*Unordered containers* – The standard library](../cpp/std_library.md#unordered-containers).

:link:

- [*Hash table*](https://en.wikipedia.org/wiki/Hash_table) – Wikipedia
- [*Hashtable benchmarks*](https://github.com/google/hashtable-benchmarks)

:grey_question:

- [*Why should hash functions use a prime number modulus?*](https://stackoverflow.com/q/1145217) – Stack Overflow
- [*Does making array size a prime number help in hash table implementation? Why?*](https://www.quora.com/Does-making-array-size-a-prime-number-help-in-hash-table-implementation-Why) – Quora

:movie_camera:

- M.Kulukundis. [*Designing a fast, efficient, cache-friendly hash table, step by step*](https://www.youtube.com/watch?v=CJsQSIp7-Ig) – CppCon (2017)

### Bloom filter

> Bloom filter is a space-efficient probabilistic data structure that is used to test whether an element is a member of a set. False positive matches are possible, but false negatives are not.

:link:

- [*Bloom filter*](https://en.wikipedia.org/wiki/Bloom_filter) – Wikipedia
- [*Bloom filter calculator*](https://hur.st/bloomfilter/)
- M.Majkowski. [*When Bloom filters don’t bloom*](https://blog.cloudflare.com/when-bloom-filters-dont-bloom/) (2020)
- J.Talbot. [*What are Bloom filters?*](https://blog.medium.com/what-are-bloom-filters-1ec2a50c68ff) (2015)

:movie_camera:

- A.Deutsch. [*Esoteric data structures and where to find them: Bloom filter*](https://www.youtube.com/watch?v=-8UZhDjgeZU&t=603) – CppCon (2017)
- R.Edwards. [*Bloom filters*](https://www.youtube.com/watch?v=heEDL9usFgs)
- N.L.Gowda. [*Bloom filter for system design*](https://www.youtube.com/watch?v=Bay3X9PAX5k)

:page_facing_up:

- A.Broder, M.Mitzenmacher. [*Network applications of Bloom filters: A survey*](https://www.cs.princeton.edu/courses/archive/spring05/cos598E/bib/broder-survey.pdf) – [Internet Mathematics **1**, 485](https://doi.org/10.1080/15427951.2004.10129096) (2004)
- B.H.Bloom. [*Space/time trade-offs in hash coding with allowable errors*](https://www.cs.princeton.edu/courses/archive/spring05/cos598E/bib/p422-bloom.pdf) – [Communications of the ACM **13**, 422](https://doi.org/10.1145/362686.362692) (1970)

:book:

- Sec. 12.5: *Bloom filters: The basics*, Sec. 12.6: *Bloom filters: Heuristic analysis* – Roughgarden T. [*Algorithms illuminated (Part 2): Graph algorithms and data structures*](http://timroughgarden.org/books.html) – Soundlikeyourself Publishing (2018)

:dizzy:

- J.Davies. [*Bloom filters*](https://www.jasondavies.com/bloomfilter/)

### Extendible hashing

> Extendible hashing is a type of hash system that treats a hash as a bit string and uses a trie for bucket lookup.

:link:

- [*Extendible hashing*](https://en.wikipedia.org/wiki/Extendible_hashing) – Wikipedia


## Consistent hashing

:link:

- [*Consistent hashing*](https://en.wikipedia.org/wiki/Consistent_hashing) – Wikipedia
- M.Nielsen. [*Consistent hashing*](http://michaelnielsen.org/blog/consistent-hashing/) (2009)

## Implementations

:grey_question:

- [*Super high performance C/C++ hash map (table, dictionary)*](https://stackoverflow.com/q/3300525) – Stack Overflow

<!--

https://cs.uwaterloo.ca/research/tr/1986/CS-86-14.pdf
http://codecapsule.com/2013/11/11/robin-hood-hashing/
https://arxiv.org/pdf/1809.04339.pdf

-->

