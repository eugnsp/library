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

* [*C++17 STL cookbook: Discover the latest enhancements to functional programming and lambda expressions.* &ndash; J.Galowicz. Packt Publishing (2017)](https://www.packtpub.com/application-development/c17-stl-cookbook)
* Ch. 18: *Concurrency* in [*The C++ standard library: A tutorial and reference* &ndash; N.M.Josuttis. Addison-Wesley, 2<sup>nd</sup> ed. (2012)](http://www.cppstdlib.com/)

---

## Algorithms

:movie_camera:

* [*105 STL algorithms in less than an hour* &ndash; J.Boccara @ ACCU (2018)](https://www.youtube.com/watch?v=bXkWuUe9V2I)
* [*STL algorithms: How to use them and how to write your own* &ndash; M.Clow @ ACCU (2016)](https://www.youtube.com/watch?v=3nXLxMYXgWs)
* [*STL algorithms in action* &ndash; M.VanLoon @ CppCon (2015)](https://www.youtube.com/watch?v=eidEEmGLQcU)

---

## Containers

:movie_camera:

* [*If I had my 'druthers: A proposal for improving the containers in C++2x* &ndash; B.Steagall @ C++Now (2018)](https://www.youtube.com/watch?v=bAE0qteS4Rk)

### Associative containers

> Associative containers are: `std::set` (collection of unique keys, sorted by keys), `std::map` (collection of key-value pairs, sorted by keys, keys are unique), `std::multiset` (collection of keys, sorted by keys), and `std::multimap` (collection of key-value pairs, sorted by keys).

:link:

* [*`insert` vs `emplace` vs `operator[]` in C++ `std::map`* &ndash; Stack Overflow](https://stackoverflow.com/questions/17172080/insert-vs-emplace-vs-operator-in-c-map)

### Sequence containers

> Sequence containers are: `std::array` (static contiguous array), `std::vector` (dynamic contiguous array), `std::deque` (double-ended queue), `std::forward_list` (singly-linked list), and `std::list` (doubly-linked list).

#### `std::vector<bool>`

:link:

* [*On `vector<bool>`* &ndash; H.E.Hinnant (2012)](https://howardhinnant.github.io/onvectorbool.html)

### Unordered containers

> Unordered containers are: `std::unordered_set` (collection of unique keys, hashed by keys), `std::unordered_map` (collection of key-value pairs, hashed by keys, keys are unique), `std::unordered_multiset` (collection of keys, hashed by keys), and `std::unordered_multimap` (collection of key-value pairs, hashed by keys).

:link:

* [*Why is there no `std::is_transparent` equivalent for unordered containers?* &ndash; Stack Overflow](https://stackoverflow.com/questions/33373228/why-is-there-no-stdis-transparent-equivalent-for-unordered-containers)
* [*Why is `unordered_map` "`find` + `insert`" faster than "`insert` + check for success"?* &ndash; Stack Overflow](https://stackoverflow.com/questions/31804025/why-is-unordered-map-find-insert-faster-than-insert-check-for-success)
* [*Performance of `emplace` is worse than check followed by `emplace`* &ndash; Stack Overflow](https://stackoverflow.com/questions/24209592/performance-of-emplace-is-worse-than-check-followed-by-emplace)

:movie_camera:

* [*#Hashing* - Dietmar K&uuml;hl @ ACCU (2019)](https://www.youtube.com/watch?v=CJsQSIp7-Ig)
* [*You can do better than `std::unordered_map`: New improvements to hash table performance* &ndash; M.Skarupke @ C++ Now (2018)](https://www.youtube.com/watch?v=M2fKMP47slQ)

:anchor:

* [WG21/P0919R3: *Heterogeneous lookup for unordered containers* &ndash; M.Pusz (2018)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0919r3.html)

---

## Random number generation

:link:

* [*Everything you never wanted to know about C++'s `random_device`* &ndash; M.E.O'Neill (2015)](http://www.pcg-random.org/posts/cpps-random_device.html)
* [*Why not just use `random_device`?* &ndash; Stack Overflow](https://stackoverflow.com/questions/39288595/why-not-just-use-random-device)

---

## Regular expressions

:link:

* [*Regular expressions library* &ndash; C++ reference](https://en.cppreference.com/w/cpp/regex)

:movie_camera:

* [*Regular expressions in C++, present and future* &ndash; T.Shen @ CppCon (2016)](https://www.youtube.com/watch?v=N_rkHzhXueo)

---

## Smart pointers

:link:

* [GotW #91: *Smart pointer parameters* &ndash; H.Sutter (2013)](https://herbsutter.com/2013/06/05/gotw-91-solution-smart-pointer-parameters/)
* [*Why is `shared_ptr<void>` legal, while `unique_ptr<void>` is ill-formed?* &ndash; Stack Overflow](https://stackoverflow.com/questions/39288891/why-is-shared-ptrvoid-legal-while-unique-ptrvoid-is-ill-formed)

### `std::shared_ptr`

:link:

* [*`std::shared_ptr` thread safety* &ndash; Stack Overflow](https://stackoverflow.com/questions/14482830/stdshared-ptr-thread-safety)
* [*`std::shared_ptr`'s secret constructor* &ndash; A.Williams](https://www.justsoftwaresolutions.co.uk/cplusplus/shared-ptr-secret-constructor.html)

### `std::unique_ptr`

:link:

* [*What to use `std::optional` or `std::unique_ptr`?* &ndash; Stack Overflow](https://stackoverflow.com/questions/44856701/what-to-use-stdoptional-or-stdunique-ptr?rq=1)
* [*Should I assign or reset a `unique_ptr`?* &ndash; Stack Overflow](https://stackoverflow.com/questions/16061407/should-i-assign-or-reset-a-unique-ptr)

---

## Strings

:link:

* [*Meaning of acronym SSO in the context of `std::string`* &ndash; Stack Overflow](https://stackoverflow.com/questions/10315041/meaning-of-acronym-sso-in-the-context-of-stdstring)

---

## Utilities

:link:

* [*Utility library* &ndash; C++ reference](https://en.cppreference.com/w/cpp/utility)

### Function objects

:link:

* [*Function objects* &ndash; C++ reference](https://en.cppreference.com/w/cpp/utility/functional)

:movie_camera:

* [*`<functional>`: What's new, and proper usage* &ndash; S.T.Lavavej @ CppCon (2015)](https://www.youtube.com/watch?v=zt7ThwVfap0)

### Pairs and tuples

:movie_camera:

* [*How C++20 can simplify `std::tuple`* &ndash; A.Meredith @ ACCU (2019)](https://www.youtube.com/watch?v=SvxBvSK4i4k)
* [*`tuple<>`: What's new and how it works* &ndash; S.T.Lavavej @ CppCon (2016)](https://www.youtube.com/watch?v=JhgWFYfdIho)

### `std::launder`

:memo:

* See also: [Core language &ndash; Strict aliasing rule](core_language.md#strict-aliasing-rule)

:link:

* [*What is the purpose of `std::launder?`* &ndash; Stack Overflow](https://stackoverflow.com/questions/39382501/what-is-the-purpose-of-stdlaunder)
* [*Where can I find what `std::launder` really does?* &ndash; Stack Overflow](https://stackoverflow.com/questions/53268089/where-can-i-find-what-stdlaunder-really-does)
* [*`std::launder`* &ndash; C++ reference](https://en.cppreference.com/w/cpp/utility/launder)

---

## Tricks and subtleties

:link:

* [*In `std::exchange`, why is the second template parameter defaulted?* &ndash; Stack Overflow](https://stackoverflow.com/questions/34876969/in-stdexchange-why-is-the-second-template-parameter-defaulted)

---

## SFINAE

* [*Making `std::get` play nice with SFINAE* &ndash; Stack Overflow](https://stackoverflow.com/questions/41708491/making-stdget-play-nice-with-sfinae)

---

## Proposals

### `std::expected`

:anchor:

* [WG21/P0323R7: *`std::expected`* &ndash; V.Botet, J.F.Bastien (2018)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0323r7.html)
* [WG21/N4109: *A proposal to add a utility class to represent expected monad* &ndash; V.Botet, P.Talbot (2014)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4109.pdf)

<!-- https://stackoverflow.com/questions/38779985/why-cant-stdtupleint-be-trivially-copyable -->
