# The standard library

## Table of contents

* [General information](#general-information)
* [Algorithms](#algorithms)
* [Containers](#containers)
	* [Associative containers](#associative-containers)
	* [Sequence containers](#sequence-containers)
	* [`std::vector<bool>`](#stdvectorbool)
	* [Unordered containers](#unordered-containers)
* [Random number generation](#random-number-generation)
* [Regular expressions](#regular-expressions)
* [Smart pointers](#smart-pointers)
	* [`std::shared_ptr`](#stdshared_ptr)
	* [`std::unique_ptr`](#stdunique_ptr)
* [Strings](#strings)
* [Utilities](#utilities)
	* [Function objects](#function-objects)
	* [Pairs and tuples](#pairs-and-tuples)
	* [`std::launder`](#std-launder)
* [Tricks and subtleties](#tricks-and-subtleties)
	* [SFINAE](#sfinae)
* [Proposals](#proposals)
	* [`std::expected`](#stdexpected)

---

## General information

:book:

* [*C++17 STL cookbook: Discover the latest enhancements to functional programming and lambda expressions.*](https://www.packtpub.com/application-development/c17-stl-cookbook) &ndash; J.Galowicz. Packt Publishing (2017)
* Ch. 18: *Concurrency* in [*The C++ standard library: A tutorial and reference*](http://www.cppstdlib.com/) &ndash; N.M.Josuttis. Addison-Wesley, 2<sup>nd</sup> ed. (2012)

---

## Algorithms

:movie_camera:

* [*105 STL algorithms in less than an hour*](https://www.youtube.com/watch?v=bXkWuUe9V2I) &ndash; J.Boccara @ ACCU (2018)
* [*STL algorithms: How to use them and how to write your own*](https://www.youtube.com/watch?v=3nXLxMYXgWs) &ndash; M.Clow @ ACCU (2016)
* [*STL algorithms in action*](https://www.youtube.com/watch?v=eidEEmGLQcU) &ndash; M.VanLoon @ CppCon (2015)

---

## Containers

:movie_camera:

* [*If I had my 'druthers: A proposal for improving the containers in C++2x*](https://www.youtube.com/watch?v=bAE0qteS4Rk) &ndash; B.Steagall @ C++Now (2018)

### Associative containers

> Associative containers are: `std::set` (collection of unique keys, sorted by keys), `std::map` (collection of key-value pairs, sorted by keys, keys are unique), `std::multiset` (collection of keys, sorted by keys), and `std::multimap` (collection of key-value pairs, sorted by keys).

:link:

* [*`insert` vs `emplace` vs `operator[]` in C++ `std::map`*](https://stackoverflow.com/questions/17172080/insert-vs-emplace-vs-operator-in-c-map) &ndash; Stack Overflow

### Sequence containers

> Sequence containers are: `std::array` (static contiguous array), `std::vector` (dynamic contiguous array), `std::deque` (double-ended queue), `std::forward_list` (singly-linked list), and `std::list` (doubly-linked list).

#### `std::vector<bool>`

:link:

* [*On `vector<bool>`*](https://howardhinnant.github.io/onvectorbool.html) &ndash; H.E.Hinnant (2012)

### Unordered containers

> Unordered containers are: `std::unordered_set` (collection of unique keys, hashed by keys), `std::unordered_map` (collection of key-value pairs, hashed by keys, keys are unique), `std::unordered_multiset` (collection of keys, hashed by keys), and `std::unordered_multimap` (collection of key-value pairs, hashed by keys).

:link:

* [*Why is there no `std::is_transparent` equivalent for unordered containers?*](https://stackoverflow.com/questions/33373228/why-is-there-no-stdis-transparent-equivalent-for-unordered-containers) &ndash; Stack Overflow
* [*Why is `unordered_map` "`find` + `insert`" faster than "`insert` + check for success"?*](https://stackoverflow.com/questions/31804025/why-is-unordered-map-find-insert-faster-than-insert-check-for-success) &ndash; Stack Overflow
* [*Performance of `emplace` is worse than check followed by `emplace`*](https://stackoverflow.com/questions/24209592/performance-of-emplace-is-worse-than-check-followed-by-emplace) &ndash; Stack Overflow

:movie_camera:

* D.K&uuml;hl. [*#Hashing*](https://www.youtube.com/watch?v=CJsQSIp7-Ig) &ndash; ACCU (2019)
* M.Skarupke. [*You can do better than `std::unordered_map`: New improvements to hash table performance*](https://www.youtube.com/watch?v=M2fKMP47slQ) &ndash; C++ Now (2018)

:anchor:

* WG21/P0919R3: [*Heterogeneous lookup for unordered containers*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0919r3.html) &ndash; M.Pusz (2018)

---

## Random number generation

:link:

* M.E.O'Neill. [*Everything you never wanted to know about C++'s `random_device`*](http://www.pcg-random.org/posts/cpps-random_device.html) &ndash; PCG (2015)
* [*Why not just use `random_device`?*](https://stackoverflow.com/questions/39288595/why-not-just-use-random-device) &ndash; Stack Overflow

---

## Regular expressions

:link:

* [*Regular expressions library*](https://en.cppreference.com/w/cpp/regex) &ndash; C++ reference

:movie_camera:

* T.Shen. [*Regular expressions in C++, present and future*](https://www.youtube.com/watch?v=N_rkHzhXueo) &ndash; CppCon (2016)

---

## Smart pointers

:link:

* H.Sutter. [GotW #91: *Smart pointer parameters*](https://herbsutter.com/2013/06/05/gotw-91-solution-smart-pointer-parameters/) (2013)
* [*Why is `shared_ptr<void>` legal, while `unique_ptr<void>` is ill-formed?*](https://stackoverflow.com/questions/39288891/why-is-shared-ptrvoid-legal-while-unique-ptrvoid-is-ill-formed) &ndash; Stack Overflow

### `std::shared_ptr`

:link:

* [*`std::shared_ptr` thread safety*](https://stackoverflow.com/questions/14482830/stdshared-ptr-thread-safety) &ndash; Stack Overflow
* A.Williams. [*`std::shared_ptr`'s secret constructor*](https://www.justsoftwaresolutions.co.uk/cplusplus/shared-ptr-secret-constructor.html)

### `std::unique_ptr`

:link:

* [*What to use `std::optional` or `std::unique_ptr`?*](https://stackoverflow.com/questions/44856701/what-to-use-stdoptional-or-stdunique-ptr?rq=1) &ndash; Stack Overflow
* [*Should I assign or reset a `unique_ptr`?*](https://stackoverflow.com/questions/16061407/should-i-assign-or-reset-a-unique-ptr) &ndash; Stack Overflow

---

## Strings

:link:

* [*Meaning of acronym SSO in the context of `std::string`*](https://stackoverflow.com/questions/10315041/meaning-of-acronym-sso-in-the-context-of-stdstring) &ndash; Stack Overflow

---

## Utilities

:link:

* [*Utility library*](https://en.cppreference.com/w/cpp/utility) &ndash; C++ reference

### Function objects

:link:

* [*Function objects*](https://en.cppreference.com/w/cpp/utility/functional) &ndash; C++ reference

:movie_camera:

* S.T.Lavavej. [*`<functional>`: What's new, and proper usage*](https://www.youtube.com/watch?v=zt7ThwVfap0) &ndash; CppCon (2015)

### Pairs and tuples

:movie_camera:

* A.Meredith. [*How C++20 can simplify `std::tuple`*](https://www.youtube.com/watch?v=SvxBvSK4i4k) &ndash; ACCU (2019)
* S.T.Lavavej. [*`tuple<>`: What's new and how it works*](https://www.youtube.com/watch?v=JhgWFYfdIho) &ndash; CppCon (2016)

### `std::launder`

:memo:

* See also: [Core language &ndash; Strict aliasing rule](core_language.md#strict-aliasing-rule)

:link:

* [*`std::launder`*](https://en.cppreference.com/w/cpp/utility/launder) &ndash; C++ reference
* [*What is the purpose of `std::launder?`*](https://stackoverflow.com/questions/39382501/what-is-the-purpose-of-stdlaunder) &ndash; Stack Overflow
* [*Where can I find what `std::launder` really does?*](https://stackoverflow.com/questions/53268089/where-can-i-find-what-stdlaunder-really-does) &ndash; Stack Overflow

---

## Tricks and subtleties

:link:

* [*In `std::exchange`, why is the second template parameter defaulted?*](https://stackoverflow.com/questions/34876969/in-stdexchange-why-is-the-second-template-parameter-defaulted) &ndash; Stack Overflow

---

## SFINAE

* [*Making `std::get` play nice with SFINAE*](https://stackoverflow.com/questions/41708491/making-stdget-play-nice-with-sfinae) &ndash; Stack Overflow

---

## Proposals

### `std::expected`

:anchor:

* V.Botet, J.F.Bastien. [*`std::expected`*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0323r7.html) &ndash; WG21/P0323R7 (2018)
* V.Botet, P.Talbot. [*A proposal to add a utility class to represent expected monad*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4109.pdf) &ndash; WG21/N4109 (2014)

<!-- https://stackoverflow.com/questions/38779985/why-cant-stdtupleint-be-trivially-copyable -->
