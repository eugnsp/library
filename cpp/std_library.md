# The standard library, Boost and proposals <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [General information](#general-information)
	- [Implementations](#implementations)
- [Algorithms](#algorithms)
	- [std::iota](#stdiota)
	- [std::midpoint](#stdmidpoint)
	- [std::*sort](#stdsort)
	- [std::[stable_]partition](#stdstable_partition)
- [Concepts](#concepts)
- [Containers](#containers)
	- [Associative containers](#associative-containers)
	- [Sequence containers](#sequence-containers)
		- [std::array](#stdarray)
		- [std::deque](#stddeque)
		- [std::list](#stdlist)
		- [std::vector](#stdvector)
		- [std::vector&lt;bool&gt;](#stdvectorltboolgt)
	- [Unordered containers](#unordered-containers)
	- [Transparent comparators](#transparent-comparators)
- [Exceptions](#exceptions)
- [Input/output](#inputoutput)
	- [Input/output manipulators](#inputoutput-manipulators)
		- [std::endl](#stdendl)
	- [Output formatting](#output-formatting)
- [Iterators](#iterators)
- [Memory](#memory)
	- [Allocators](#allocators)
- [Numerics](#numerics)
	- [std::bit_cast](#stdbit_cast)
	- [Linear algebra support](#linear-algebra-support)
	- [Random numbers](#random-numbers)
- [Regular expressions](#regular-expressions)
- [Smart pointers](#smart-pointers)
	- [std::unique_ptr](#stdunique_ptr)
	- [std::shared_ptr](#stdshared_ptr)
		- [std::enable_shared_from_this](#stdenable_shared_from_this)
	- [std::weak_ptr](#stdweak_ptr)
	- [std::auto_ptr](#stdauto_ptr)
	- [std::observer_ptr](#stdobserver_ptr)
	- [boost::intrusive_ptr](#boostintrusive_ptr)
- [Strings](#strings)
	- [Short string optimization](#short-string-optimization)
	- [std::string_view](#stdstring_view)
- [Type support](#type-support)
	- [Fixed-width integer types](#fixed-width-integer-types)
	- [Type traits](#type-traits)
		- [std::is_base_of](#stdis_base_of)
		- [std::is_trivial*](#stdis_trivial)
- [Utilities](#utilities)
	- [Function objects](#function-objects)
	- [std::initializer_list](#stdinitializer_list)
	- [Pairs and tuples](#pairs-and-tuples)
	- [Sum types](#sum-types)
		- [std::optional](#stdoptional)
		- [std::variant](#stdvariant)
		- [(std::)expected](#stdexpected)
	- [std::launder](#stdlaunder)
- [Tricks and subtleties](#tricks-and-subtleties)
- [The Standard Template Library (STL)](#the-standard-template-library-stl)

---

## General information

:link:

- S.Love. [*Are you afraid of the dark? – Making ense of the STL*](https://accu.org/index.php/journals/443) – [Overload **43**](https://accu.org/index.php/journals/c161/) (2001)

:book:

- J.Galowicz. [*C++17 STL cookbook: Discover the latest enhancements to functional programming and lambda expressions*](https://www.packtpub.com/application-development/c17-stl-cookbook) (2017)
- N.M.Josuttis. [*The C++ standard library: A tutorial and reference*](http://www.cppstdlib.com/) (2012)

:anchor:

- B.Revzin. [*The mothership has landed: Adding `<=>` to the library*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1614r2.html) – WG21/P1614R2 (2019)

### Implementations

:link:

- [*libstdc++*](https://github.com/gcc-mirror/gcc/tree/master/libstdc%2B%2B-v3)
- [*libc++*](https://github.com/llvm-mirror/libcxx)
- [*Microsoft*](https://github.com/microsoft/STL)

---

## Algorithms

:movie_camera:

- C.Hoekstra. *Algorithm intuition.* [Part I](https://www.youtube.com/watch?v=pUEnO6SvAMo), [Part II](https://www.youtube.com/watch?v=sEvYmb3eKsw) – CppCon (2019)
- J.Boccara. [*105 STL algorithms in less than an hour*](https://www.youtube.com/watch?v=bXkWuUe9V2I) – ACCU (2018)
- M.Clow. [*STL algorithms: How to use them and how to write your own*](https://www.youtube.com/watch?v=3nXLxMYXgWs) – ACCU (2016)
- M.VanLoon. [*STL algorithms in action*](https://www.youtube.com/watch?v=eidEEmGLQcU) – CppCon (2015)

### `std::iota`

:link:

- S.Parent. [*#iotashaming*](https://sean-parent.stlab.cc/2019/01/04/iota.html) (2019)
- [*What does iota of `std::iota` stand for?*](https://stackoverflow.com/q/9244879) – Stack Overflow

### `std::midpoint`

:movie_camera:

- M.Clow. [*`std::midpoint`? How hard could it be?*](https://www.youtube.com/watch?v=sBtAGxBh-XI) – CppCon (2019)

:anchor:

- S.D.Herring. [*Well-behaved interpolation for numbers and pointers*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p0811r3.html) – WG21/P0811R3 (2019)

### `std::[stable_]sort`

:link:

- A.Demin. [*How sorting is implemented in the standard library* (in Russian)](http://demin.ws/blog/russian/2009/06/18/sort-implementation-in-stl/) (2009)

### `std::[stable_]partition`

:link:

- A.A.Stepanov, M.A.Marcus. [Sec. 3: *Partition algorithms*](http://stepanovpapers.com/PAM3-partition_notes.pdf) – Notes for the Foundations of programming course (2004–2005)
- [*`stable_partition` on forward iterators*](https://stackoverflow.com/q/59642958) – Stack Overflow
- [*How is `stable_partition` an adaptive algorithm?*](https://stackoverflow.com/q/21554635) – Stack Overflow

---

## Concepts

See also [*Concepts* – Templates](templates.md#concepts).

:link:

[*Why does `same_as` concept check type equality twice?*](https://stackoverflow.com/q/58509147) – Stack Overflow

---

## Containers

:movie_camera:

- B.Steagall. [*If I had my ’druthers: A proposal for improving the containers in C++2x*](https://www.youtube.com/watch?v=bAE0qteS4Rk) – C++Now (2018)
- B.Stroustrup. [*Why you should avoid linked lists*](https://www.youtube.com/watch?v=YQs6IC-vgmo) – Going Native (2012)

### Associative containers

> Associative containers are: `std::set` (collection of unique keys, sorted by keys), `std::map` (collection of key-value pairs, sorted by keys, keys are unique), `std::multiset` (collection of keys, sorted by keys), and `std::multimap` (collection of key-value pairs, sorted by keys).

:link:

- [*`insert` vs `emplace` vs `operator[]` in C++ `std::map`*](https://stackoverflow.com/q/17172080) – Stack Overflow

### Sequence containers

> Sequence containers are: `std::array` (static contiguous array), `std::vector` (dynamic contiguous array), `std::deque` (double-ended queue), `std::forward_list` (singly-linked list), and `std::list` (doubly-linked list).

#### `std::array`

:link:

- [*Create `N`-element `constexpr` array in C++11*](https://stackoverflow.com/q/19019252) – Stack Overflow
- [*Why isn’t `std::array::size` static?*](https://stackoverflow.com/q/21936507) – Stack Overflow

#### `std::deque`

:link:

- [*What really is a deque in STL?*](https://stackoverflow.com/q/6292332) – Stack Overflow
- [*How can references be valid while iterators become invalidated in a deque*](https://stackoverflow.com/q/32800138) – Stack Overflow

#### `std::list`

:link:

- H.Hinnant. [*On `std::list::size`*](https://howardhinnant.github.io/On_list_size.html)
- [*Is `list::size()` really `O(n)`?*](https://stackoverflow.com/q/228908) – Stack Overflow
- [*Why is `std::list` bigger on C++11?*](https://stackoverflow.com/q/10065055) – Stack Overflow

:anchor:

- [*`std::list`*](https://en.cppreference.com/w/cpp/container/list) – C++ reference
- [*`std::list`*](https://web.archive.org/web/20171122174457/http://www.sgi.com/tech/stl/List.html) – SGI STL

#### `std::vector`

:link:

- [*How to enforce move semantics when a vector grows?*](https://stackoverflow.com/q/8001823) – Stack Overflow

#### `std::vector<bool>`

:link:

- H.Hinnant. [*On `vector<bool>`*](https://howardhinnant.github.io/onvectorbool.html) (2012)
- [*Why is `vector<bool>` not an STL container?*](https://stackoverflow.com/q/17794569) – Stack Overflow

### Unordered containers

> Unordered containers are: `std::unordered_set` (collection of unique keys, hashed by keys), `std::unordered_map` (collection of key-value pairs, hashed by keys, keys are unique), `std::unordered_multiset` (collection of keys, hashed by keys), and `std::unordered_multimap` (collection of key-value pairs, hashed by keys).

:link:

- [*Why is `unordered_map` “`find` + `insert`” faster than “`insert` + check for success”?*](https://stackoverflow.com/q/31804025) – Stack Overflow
- [*Performance of `emplace` is worse than check followed by `emplace`*](https://stackoverflow.com/q/24209592) – Stack Overflow

:movie_camera:

- D.K&uuml;hl. [*#Hashing*](https://www.youtube.com/watch?v=CJsQSIp7-Ig) – ACCU (2019)
- M.Skarupke. [*You can do better than `std::unordered_map`: New improvements to hash table performance*](https://www.youtube.com/watch?v=M2fKMP47slQ) – C++Now (2018)

:anchor:

- M.Pusz. [*Heterogeneous lookup for unordered containers*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0919r3.html) – WG21/P0919R3 (2018)

### Transparent comparators

> Transparent comparators make it possible to avoid constructing an object of the type `key_type` to do the lookup using member functions like `find`, `lower_bound`, etc.

:link:

- [*What are transparent comparators?*](https://stackoverflow.com/q/20317413) – Stack Overflow
- [*Why is there no `std::is_transparent` equivalent for unordered containers?*](https://stackoverflow.com/q/33373228) – Stack Overflow

:anchor:

- J.Wakely, S.T.Lavavej, J.M.L&oacute;pez Mu&ntilde;oz. [*Adding heterogeneous comparison lookup to associative containers*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm) – WG21/N3657 (2013)

---

## Exceptions

See [*Exceptions* – Patterns, idioms, and design principles](patterns_and_idioms.md#exceptions).

---

## Input/output

:link:

- [`tellg()` function give wrong size of file?](https://stackoverflow.com/q/22984956) – Stack Overflow

:anchor:

- [*Input/output via `<iostream>` and `<cstdio>`*](https://isocpp.org/wiki/faq/input-output) – C++ FAQ
- [*Input/output library*](https://en.cppreference.com/w/cpp/io) – C++ reference

### Input/output manipulators

#### `std::endl`

:link:

- C.Sharpe. [*Don’t use `std::endl`*](https://accu.org/index.php/journals/2619) – [Overload **149**](https://accu.org/index.php/journals/c395/), 34 (2019)
- D.K&uuml;hl. [*Stop excessive use of `std::endl`*](https://kuhllib.com/2012/01/14/stop-excessive-use-of-stdendl/) (2012)

:anchor:

- [*std::endl*](https://en.cppreference.com/w/cpp/io/manip/endl) – C++ reference

### Output formatting

:link:

- S.Ignatchenko. [*5 Reasons **not** to use `std::ostream` for human-readable output*](https://accu.org/index.php/journals/2486) – [Overload **143**](https://accu.org/index.php/journals/c384/), 16 (2018)
- D.Epp. [*IOStream is hopelessly broken*](https://www.moria.us/articles/iostream-is-hopelessly-broken/) (2017)
- [{fmt}: a modern formatting library](https://github.com/fmtlib/fmt)
- [*`std::printf` vs. `std::cout`*](https://stackoverflow.com/q/2872543) – Stack Overflow
- [*Is `std::cout` synchronized/thread-safe?*](https://stackoverflow.com/q/6374264) – Stack Overflow
- [*How can I use C++20 `std::format`?*](https://stackoverflow.com/q/59024390) – Stack Overflow

:anchor:

- V.Zverovich, L.Howes. [*Text formatting*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0645r1.html) – WG21/P0645R1

---

## Iterators

:link:

- [*Why use iterators instead of array indices?*](https://stackoverflow.com/q/131241) – Stack Overflow
- [*Iterator loop vs index loop*](https://stackoverflow.com/q/14373934) – Stack Overflow
- [*Why is `std::iterator` deprecated?*](https://stackoverflow.com/q/43268146) – Stack Overflow

:movie_camera:

- C.Carter. [*Iterator haiku*](https://www.youtube.com/watch?v=rZs9ndzGB_8) – CppCon (2016)

---

## Memory

See also [*Memory and cache* – Optimization and hardware](optimization_and_hardware.md#memory-and-cache).

### Allocators

- [*What does (template) `rebind<>` do?*](https://stackoverflow.com/q/14148756) – Stack Overflow
- [*Why is `allocator::rebind` necessary when we have template template parameters?*](https://stackoverflow.com/q/12362363) – Stack Overflow
- [*Why is `std::allocator` a template?*](https://stackoverflow.com/q/45267275) – Stack Overflow

:anchor:

- [`std::allocator`](https://en.cppreference.com/w/cpp/memory/allocator) – C++ reference

---

## Numerics

### `std::bit_cast`

:anchor:

- [`std::bit_cast`](https://en.cppreference.com/w/cpp/numeric/bit_cast) – C++ reference
- J.Bastien. [*Bit-casting object representations*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0476r2.html) – WG21/P0476R2 (2017)

### Linear algebra support

:link:

- M.Hoemmen et al. [*Historical lessons for C++ linear algebra library standardization*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1417r0.pdf) (2019)
- V.Reverdy. [*On vectors, tensors, matrices, and hypermatrices*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1770r0.pdf) (2019)

:movie_camera:

- G.Davidson. [*Standardizing a linear algebra library*](https://www.youtube.com/watch?v=cIPmhIiY68U) – Meeting C++ (2018)

:anchor:

- G.Davidson, ​B.Steagall. [*A proposal to add linear algebra support to the C++ standard library*](http://open-std.org/JTC1/SC22/WG21/docs/papers/2019/p1385r3.pdf) – WG21/P1385R3 (2019)
- G.Davidson, ​B.Steagall. [*What do we need from a linear algebra library?*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1166r0.pdf) – WG21/P1166R0 (2019)

### Random numbers

:link:

- M.E.O’Neill. [*Everything you never wanted to know about C++’s `random_device`*](http://www.pcg-random.org/posts/cpps-random_device.html) – PCG (2015)
- [*Why is the new random library better than `std::rand()`?*](https://stackoverflow.com/q/53040940) – Stack Overflow
- [*Why not just use `random_device`?*](https://stackoverflow.com/q/39288595) – Stack Overflow

:movie_camera:

- A.Weis. [*Random numbers are hard*](https://www.youtube.com/watch?v=WDScnjQwEK8) – Meeting C++ (2019)

---

## Regular expressions

:link:

- [*Regular expressions library*](https://en.cppreference.com/w/cpp/regex) – C++ reference

:movie_camera:

- T.Shen. [*Regular expressions in C++, present and future*](https://www.youtube.com/watch?v=N_rkHzhXueo) – CppCon (2016)

---

## Smart pointers

> A smart pointer is a class that simulates a raw C++ pointer, and provides automatic exception-safe object lifetime management.

:link:

- [*Smart pointer*](https://en.wikipedia.org/wiki/Smart_pointer) – Wikipedia
- H.Sutter. [GotW #91: *Smart pointer parameters*](https://herbsutter.com/2013/06/05/gotw-91-solution-smart-pointer-parameters/) – Guru of the Week (2013)
- Y.Sharon. [*Smart pointers: What, why, which?*](http://ootips.org/yonat/4dev/smart-pointers.html) (1999)
- [*What is a smart pointer and when should I use one?*](https://stackoverflow.com/q/106508) – Stack Overflow
- [*Why is `shared_ptr<void>` legal, while `unique_ptr<void>` is ill-formed?*](https://stackoverflow.com/q/39288891) – Stack Overflow

:movie_camera:

- A.O’Dwyer. [*Back to basics: Smart pointers*](https://www.youtube.com/watch?v=xGDLkt-jBJ4) – CppCon (2019)
- M.Fleming. [*The smart pointers I wish I had*](https://www.youtube.com/watch?v=CKCR5eFVrmc) – CppCon (2019)

:anchor:

- [*Boost.SmartPtr: The smart pointer library*](https://www.boost.org/doc/libs/release/libs/smart_ptr/smart_ptr.htm)

### `std::unique_ptr`

> The `std::unique_ptr` class is a smart pointer with unique ownership.

:link:

- [*What to use `std::optional` or `std::unique_ptr`?*](https://stackoverflow.com/q/44856701) – Stack Overflow
- [*Should I assign or reset a `unique_ptr`?*](https://stackoverflow.com/q/16061407) – Stack Overflow
- [*`make_unique` with brace initialization*](https://stackoverflow.com/q/55141594) – Stack Overflow
- [*How do I pass a `unique_ptr` argument to a constructor or a function?*](https://stackoverflow.com/q/8114276) – Stack Overflow

:anchor:

- [*`std::unique_ptr`*](https://en.cppreference.com/w/cpp/memory/unique_ptr) – C++ reference
- S.T.Lavavej. [*`make_unique`*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3588.htm) – WG21/N3588 (2013)

### `std::shared_ptr`

> The `std::unique_ptr` class is a smart pointer with shared ownership.

:link:

- [*`std::shared_ptr` thread safety*](https://stackoverflow.com/q/14482830) – Stack Overflow
- A.Williams. [*`std::shared_ptr`’s secret constructor*](https://www.justsoftwaresolutions.co.uk/cplusplus/shared-ptr-secret-constructor.html)
- [*`shared_ptr` magic*](https://stackoverflow.com/q/3899790) – Stack Overflow

:anchor:

- [*`std::shared_ptr`*](https://en.cppreference.com/w/cpp/memory/shared_ptr) – C++ reference

#### `std::enable_shared_from_this`

> `std::enable_shared_from_this` allows a member function of an object that is currently managed by a `std::shared_ptr` to extend the lifetime of that object dynamically by generating additional `std::shared_ptr` instances.

:link:

- [*What is the usefulness of `enable_shared_from_this`?*](https://stackoverflow.com/q/712279) – Stack Overflow

:anchor:

- [`std::enable_shared_from_this`](https://en.cppreference.com/w/cpp/memory/enable_shared_from_this) – C++ reference

### `std::weak_ptr`

:link:

- [*When is `std::weak_ptr` useful?*](https://stackoverflow.com/q/12030650) – Stack Overflow

:anchor:

- [*`std::weak_ptr`*](https://en.cppreference.com/w/cpp/memory/weak_ptr) – C++ reference

### `std::auto_ptr`

> `std::auto_ptr` is a smart pointer with unique ownership that had been designed before rvalue references and move semantics were introduced into the language. It was deprecated in C++11 and removed in C++17.

:link:

- H.Sutter. [GotW #25: *`auto_ptr`*](http://www.gotw.ca/gotw/025.htm) – Guru of the Week (2009)

:anchor:

- [`std::auto_ptr`](https://en.cppreference.com/w/cpp/memory/auto_ptr) – C++ reference

### `std::observer_ptr`

> `std::observer_ptr` is a smart pointer that takes no ownership responsibility for its pointees (non-owning pointer).

:anchor:

- [*`std::experimental::observer_ptr`*](https://en.cppreference.com/w/cpp/experimental/observer_ptr) – C++ reference
- B.Stroustrup. [*Abandon `observer_ptr`*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1408r0.pdf) – WG21/P1408R0 (2018)
- W.E.Brown. [*A proposal for the world’s dumbest smart pointer*](http://open-std.org/JTC1/SC22/WG21/docs/papers/2014/n4282.pdf) – WG21/N4282 (2014)

### `boost::intrusive_ptr`

> The `boost::intrusive_ptr` class is a smart pointer that stores a pointer to an object with an embedded reference count, which is managed somewhere outside the smart pointer.

:link:

- B.Wicht. [*Boost `intrusive_ptr`: Faster shared pointer*](https://baptiste-wicht.com/posts/2011/11/boost-intrusive_ptr.html) (2011)
- [*Boost intrusive pointer*](https://stackoverflow.com/q/40137660) – Stack Overflow

:anchor:

- [*`intrusive_ptr`*](https://www.boost.org/doc/libs/release/libs/smart_ptr/smart_ptr.htm#intrusive_ptr) – Boost.SmartPtr
- I.Muerte. [*An intrusive smart pointer*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0468r1.html) – WG21/P0468R1 (2018)

---

## Strings

:memo:

- `std::basic_string<T, ...>` is the only container in the standard library that requires `T` to be a trivial standard-layout type.

:link:

- H.Sutter. [GotW #29: *Strings*](http://www.gotw.ca/gotw/029.htm) – Guru of the Week (2009)
- [*Why `std::string` does not have `const char*` cast*](https://stackoverflow.com/q/59076004) – Stack Overflow
- [*Why doesn’t `std::string` provide implicit conversion to `char*`?*](https://stackoverflow.com/q/492061) – Stack Overflow

:anchor:

- [*`std::basic_string`*](https://en.cppreference.com/w/cpp/string/basic_string) – C++ reference

### Short string optimization

:link:

- [*Meaning of acronym SSO in the context of `std::string`*](https://stackoverflow.com/q/10315041) – Stack Overflow

### `std::string_view`

:link:

- J.Miller. [C++ `std::string_view` for better performance: An example use case](https://www.nextptr.com/tutorial/ta1217154594/cplusplus-stdstring_view-for-better-performance-an-example-use-case) (2019)

:movie_camera:

- M.Clow. [*`string_view`: When to use it and when not*](https://www.youtube.com/watch?v=H9gAaNRoon4) – CppCon (2015)
- N.MacIntosh. [*Evolving `array_view` and `string_view` for safe C++ code*](https://www.youtube.com/watch?v=C4Z3c4Sv52U) – CppCon (2015)

---

## Type support

### Fixed-width integer types

:memo:

- `std::int8_t`, `std::int16_t`, `std::int32_t`, and `std::int64_t` are guaranteed to use 2’s complement to represent negative values.

:link:

- [*When is `uint8_t` ≠ `unsigned char`?*](https://stackoverflow.com/q/16138237) – Stack Overflow

### Type traits

See also [*Type traits* – Templates](templates.md#type-traits).

:movie_camera:

- M.Clow. [*Type traits: What are they and why should I use them?*](https://www.youtube.com/watch?v=VvbTP_k_Df4) – CppCon (2015)

:anchor:

- [*Standard library header `<type_traits>`*](https://en.cppreference.com/w/cpp/header/type_traits) – C++ reference

#### `std::is_base_of`

:link:

- [*How does `is_base_of` work?*](https://stackoverflow.com/q/2910979) – Stack Overflow

#### `std::is_trivial*`

:movie_camera:

- J.Turner. [*Great C++ `is_trivial`*](https://www.youtube.com/watch?v=ZxWjii99yao) – CppCon (2019)

---

## Utilities

:link:

- [*Utility library*](https://en.cppreference.com/w/cpp/utility) – C++ reference

### Function objects

:link:

- [*Function objects*](https://en.cppreference.com/w/cpp/utility/functional) – C++ reference

:movie_camera:

- S.T.Lavavej. [*`<functional>`: What’s new, and proper usage*](https://www.youtube.com/watch?v=zt7ThwVfap0) – CppCon (2015)

### `std::initializer_list`

> An object of type `std::initializer_list<T>` is a lightweight proxy object that provides access to an array of objects of type `const T`.

:link:

- [*`std::initializer_list` and move semantics*](https://stackoverflow.com/q/8193102) – Stack Overflow

:anchor:

- [*`std::initializer_list`*](https://en.cppreference.com/w/cpp/utility/initializer_list) – C++ reference

### Pairs and tuples

:link:

- [*Why can’t `std::tuple<int>` be trivially copyable?*](https://stackoverflow.com/q/38779985) – Stack Overflow
- [*Replace `N`-th element of a `std::tuple`*](https://stackoverflow.com/q/59670539) – Stack Overflow

:movie_camera:

- A.Meredith. [*How C++20 can simplify `std::tuple`*](https://www.youtube.com/watch?v=SvxBvSK4i4k) – ACCU (2019)
- S.T.Lavavej. [*`tuple<>`: What’s new and how it works*](https://www.youtube.com/watch?v=JhgWFYfdIho) – CppCon (2016)

### Sum types

#### `std::optional`

> The class template `std::optional<T>` is a type that may or may not store a value of type `T` in its storage space. It is recommended to be used in situations where there is exactly one and clear reason for having no value of type `T`, and where the lack of value is as natural as having any regular value of `T`. It is not recommended to use optional to indicate that we were not able to compute a value because of a failure.

:link:

- B.Filipek. [*Using C++17 `std::optional`*](https://www.bfilipek.com/2018/05/using-optional.html) (2018)
- B.Filipek. [*Error handling and `std::optional`*](https://www.bfilipek.com/2018/05/errors-and-optional.html) (2018)
- B.Filipek. [*In-place construction for `std::any`, `std::variant` and `std::optional`*](https://www.bfilipek.com/2018/07/in-place-cpp17.html) (2018)
- B.Revzin. [*Implementing the spaceship operator for `optional`*](https://accu.org/index.php/journals/2563) – [Overload **147**](https://accu.org/index.php/journals/c391/), 10 (2018)
- S.Brand. [*Functional error-handling with optional and expected*](https://accu.org/index.php/journals/2462) – [Overload **143**](https://accu.org/index.php/journals/c382/), 21 (2018)
- S.Brand. [*Functional exceptionless error-handling with optional and expected*](https://blog.tartanllama.xyz/optional-expected/) (2017)
- S.Brand. [*Implementation with functional-style extensions and reference support*](https://github.com/TartanLlama/optional)
- A.Krzemieński. [*A gotcha with Optional*](https://akrzemi1.wordpress.com/2014/12/02/a-gotcha-with-optional/) (2014)
- A.Krzemieński. [*Efficient optional values*](https://akrzemi1.wordpress.com/2015/07/15/efficient-optional-values/) (2015)
- [*What to use `std::optional` or `std::unique_ptr`?*](https://stackoverflow.com/q/44856701) – Stack Overflow
- [*Implementing `operator<=>` for `optional<T>`*](https://stackoverflow.com/q/47315539) – Stack Overflow

:anchor:

- [*`std::optional`*](https://en.cppreference.com/w/cpp/utility/optional) – C++ reference
- [*Boost.Optional: The optional wrapper library*](https://www.boost.org/doc/libs/release/libs/optional/doc/html/index.html)
- F.Cacciola, A.Krzemieński. [*A proposal to add a utility class to represent optional objects*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3793.html) – WG21/N3793 (2013)
- [* libstdc++’s implementation*](https://github.com/gcc-mirror/gcc/blob/master/libstdc%2B%2B-v3/include/std/optional)
- A.Krzemieński. [*N3793 reference implementation*](https://github.com/akrzemi1/Optional/)

#### `std::variant`

:movie_camera:

- N.Liber. [*The many variants of `std::variant`*](https://www.youtube.com/watch?v=JUxhwf7gYLg) – C++Now (2019)

:anchor:

- [`std::variant`](https://en.cppreference.com/w/cpp/utility/variant) – C++ reference

#### `(std::)expected`

> A proposed utility class to represent expected monad.

:link:

- S.Brand. [*Functional error-handling with optional and expected*](https://accu.org/index.php/journals/2462) – [Overload **143**](https://accu.org/index.php/journals/c382/), 21 (2018)
- S.Brand. [C++11/14/17 `std::expected` with functional-style extensions](https://github.com/TartanLlama/expected)

:movie_camera:

- N.Douglas. [*Introduction to proposed `std::expected`*](https://www.youtube.com/watch?v=JfMBLx7qE0I) – Meeting C++ (2017)

:anchor:

- V.Botet, J.Bastien. *`std::expected`*. [R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0323r7.html) (2017), [R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0323r4.html) (2018) – WG21/P0323
- N.Douglas. [*Concerns about `expected<T, E>` from the Boost.Outcome peer review*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0762r0.pdf) – WG21/P0762R0 (2017)
- V.Botet, P.Talbot. [*A proposal to add a utility class to represent expected monad*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4109.pdf) – WG21/N4109 (2014)

### `std::launder`

:link:

- [*What is the purpose of `std::launder?`*](https://stackoverflow.com/q/39382501) – Stack Overflow
- [*Where can I find what `std::launder` really does?*](https://stackoverflow.com/q/53268089) – Stack Overflow

:anchor:

- [*`std::launder`*](https://en.cppreference.com/w/cpp/utility/launder) – C++ reference

---

## Tricks and subtleties

:link:

- A.O’Dwyer. [*Don’t inherit from standard types*](https://quuxplusone.github.io/blog/2018/12/11/dont-inherit-from-std-types/) (2018)
- [*In `std::exchange`, why is the second template parameter defaulted?*](https://stackoverflow.com/q/34876969) – Stack Overflow
- [*Why does the C++ standard algorithm `count` return a `difference_type` instead of `size_t`?*](https://stackoverflow.com/q/7505083) – Stack Overflow
- [*Why standard container iterators don’t overload `->*`?*](https://stackoverflow.com/q/48626039) – Stack Overflow
- [*Why does `numeric_limits` work on types it does not know?*](https://stackoverflow.com/q/47520847) – Stack Overflow
- [*Why is swap called by `std::sort` only if my container has more than 32 elements?*](https://stackoverflow.com/q/59473178) – Stack Overflow

:movie_camera:

- J.Brown. [*This one weird trick: `std::integral_constant`*](https://www.youtube.com/watch?v=MKes-sG3zAU) – CppCon (2019)

---

## The Standard Template Library (STL)

:link:

- [*Standard Template Library*](https://en.wikipedia.org/wiki/Standard_Template_Library) – Wikipedia
- [*History of the Standard Template Library*](https://en.wikipedia.org/wiki/History_of_the_Standard_Template_Library) – Wikipedia
- [*What’s the difference between “STL” and “C++ standard library”?*](https://stackoverflow.com/q/5205491) – Stack Overflow

:page_facing_up:

- D.R.Musser, A.A.Stepanov. [*A library of generic algorithms in Ada*](http://stepanovpapers.com/p216-musser.pdf) – [Proceedings of ACM SIGAda, 216](https://doi.org/10.1145/317500.317529) (1987)

:movie_camera:

- A.Stepanov. [*STL and its design principles*](https://www.youtube.com/watch?v=COuHLky7E2Q) (2002)

:anchor:

- [*SGI STL: Programmer’s guide*](https://www.boost.org/sgi/stl/)

<!-- ## SFINAE

<!-- move into Templates
- [*Making `std::get` play nice with SFINAE*](https://stackoverflow.com/q/41708491) – Stack Overflow -->


