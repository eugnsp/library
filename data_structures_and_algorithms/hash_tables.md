# Hash tables <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [General information](#general-information)
- [Consistent hashing](#consistent-hashing)
- [Bloom filter](#bloom-filter)

---

## General information

> A hash table is a data structure that implements an associative array abstract data type, a structure that can map keys to values. A hash table uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found. Hash tables in the C++ standard library go by the names of `std::unordered_[multi]set` and `std::unordered_[multi]map`. See [The standard library – Unordered containers](../cpp/std_library.md#unordered-containers).

:link:

- [*Hash table*](https://en.wikipedia.org/wiki/Hash_table) – Wikipedia

:grey_question:

- [*Why is XOR the default way to combine hashes?*](https://stackoverflow.com/q/5889238) – Stack Overflow

:movie_camera:

- D.K&uuml;hl. [*#Hashing*](https://www.youtube.com/watch?v=CJsQSIp7-Ig) – ACCU (2019)
- M.Kulukundis. [*Designing a fast, efficient, cache-friendly hash table, step by step*](https://www.youtube.com/watch?v=CJsQSIp7-Ig) – CppCon (2017)

## Consistent hashing

:link:

- [*Consistent hashing*](https://en.wikipedia.org/wiki/Consistent_hashing) – Wikipedia
- M.Nielsen. [*Consistent hashing*](http://michaelnielsen.org/blog/consistent-hashing/) (2009)

<!--

https://cs.uwaterloo.ca/research/tr/1986/CS-86-14.pdf
http://codecapsule.com/2013/11/11/robin-hood-hashing/
https://arxiv.org/pdf/1809.04339.pdf

-->

## Bloom filter

See [*Bloom filter* – Randomized algorithms and probabilistic datastructures](random.md#bloom-filter)
