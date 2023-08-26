# The standard library, Boost, and proposals <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [General information](#general-information)
	- [The standard library](#the-standard-library)
		- [Implementations](#implementations)
	- [Boost](#boost)
- [Design principles](#design-principles)
	- [Customization point objects](#customization-point-objects)
- [Algorithms](#algorithms)
	- [`std::iota`](#stdiota)
	- [`std::midpoint`](#stdmidpoint)
	- [`std::next_permutation` / `std::prev_permutation` / `std::is_permutation`](#stdnext_permutation--stdprev_permutation--stdis_permutation)
	- [`std::[stable_]sort` / `std::is_sorted`](#stdstable_sort--stdis_sorted)
	- [`std::[stable_]partition`](#stdstable_partition)
	- [`std::[transform_]exclusive_scan` / `std::[transform_]inclusive_scan`](#stdtransform_exclusive_scan--stdtransform_inclusive_scan)
- [Concepts](#concepts)
- [Containers](#containers)
	- [Associative containers](#associative-containers)
		- [`std::set`](#stdset)
		- [`std::map`](#stdmap)
	- [Sequence containers](#sequence-containers)
		- [`std::array`](#stdarray)
		- [`std::deque`](#stddeque)
		- [`std::forward_list`](#stdforward_list)
		- [`std::list`](#stdlist)
		- [`std::vector`](#stdvector)
		- [`std::vector<bool>`](#stdvectorbool)
	- [Strings](#strings)
		- [Short string optimization](#short-string-optimization)
		- [`std::string_view`](#stdstring_view)
		- [C-strings](#c-strings)
	- [Unordered containers](#unordered-containers)
		- [`std::hash`](#stdhash)
	- [Container adaptors](#container-adaptors)
		- [`std::stack`](#stdstack)
		- [`std::queue`](#stdqueue)
		- [`std::priority_queue`](#stdpriority_queue)
	- [Container views](#container-views)
		- [`std::span`](#stdspan)
	- [Transparent comparators](#transparent-comparators)
	- [Erasing from containers](#erasing-from-containers)
	- [Signedness vs unsignedness of size](#signedness-vs-unsignedness-of-size)
	- [Non-standard containers](#non-standard-containers)
- [Exceptions](#exceptions)
	- [`noexcept` specifier](#noexcept-specifier)
	- [`std::bad_alloc`](#stdbad_alloc)
- [Input/output](#inputoutput)
	- [Input/output manipulators](#inputoutput-manipulators)
		- [`std::endl`](#stdendl)
	- [Output formatting](#output-formatting)
		- [Standard formatting library](#standard-formatting-library)
	- [`std::stringstream`](#stdstringstream)
	- [`std::ios_base::Init`](#stdios_baseinit)
- [Iterators](#iterators)
	- [Reverse iterators](#reverse-iterators)
- [Ranges](#ranges)
	- [Views](#views)
- [Memory](#memory)
	- [`std::malloc` / `std::calloc` / `std::free`](#stdmalloc--stdcalloc--stdfree)
	- [Allocators](#allocators)
	- [Smart pointers](#smart-pointers)
		- [`std::unique_ptr`](#stdunique_ptr)
		- [`std::shared_ptr`](#stdshared_ptr)
		- [`std::enable_shared_from_this`](#stdenable_shared_from_this)
		- [`std::weak_ptr`](#stdweak_ptr)
		- [`std::auto_ptr`](#stdauto_ptr)
		- [`std::observer_ptr`](#stdobserver_ptr)
		- [`boost::intrusive_ptr`](#boostintrusive_ptr)
		- [`std::out_ptr` and `std::inout_ptr` adaptors](#stdout_ptr-and-stdinout_ptr-adaptors)
- [Numerics](#numerics)
	- [Bit manipulation functions](#bit-manipulation-functions)
	- [`std::bit_cast`](#stdbit_cast)
	- [Linear algebra support](#linear-algebra-support)
	- [Random numbers](#random-numbers)
- [Regular expressions](#regular-expressions)
- [Type support](#type-support)
	- [`std::type_info`](#stdtype_info)
	- [Additional basic types](#additional-basic-types)
		- [`std::nullptr_t`](#stdnullptr_t)
	- [Fixed-width integer types](#fixed-width-integer-types)
	- [Uninitialized storage](#uninitialized-storage)
	- [`std::byte`](#stdbyte)
	- [Type traits](#type-traits)
		- [`std::is_class`](#stdis_class)
		- [`std::is_base_of`](#stdis_base_of)
		- [`std::is_trivial*`](#stdis_trivial)
- [Utilities](#utilities)
	- [Integer comparison functions](#integer-comparison-functions)
	- [Function objects](#function-objects)
		- [`std::reference_wrapper`](#stdreference_wrapper)
	- [`std::initializer_list`](#stdinitializer_list)
	- [Algebraic data types](#algebraic-data-types)
		- [Pairs and tuples](#pairs-and-tuples)
		- [`std::optional`](#stdoptional)
		- [`std::variant`](#stdvariant)
		- [`std::any`](#stdany)
		- [`(std::)expected`](#stdexpected)
	- [`std::launder`](#stdlaunder)
	- [`std::source_location`](#stdsource_location)
- [Date and time utilities](#date-and-time-utilities)
- [Filesystem](#filesystem)
- [Tricks and subtleties](#tricks-and-subtleties)
	- [Self-assignment](#self-assignment)
	- [C standard library](#c-standard-library)
- [The Standard Template Library (STL)](#the-standard-template-library-stl)

---

## General information

### The standard library

:link:

- S.Love. [*Are you afraid of the dark? – Making sense of the STL*](https://accu.org/journals/overload/9/43/love_443/) – [Overload **43**](https://accu.org/journals/overload/overload43) (2001)

:movie_camera:

- S.Dargo. [*Undefined behaviour in the STL*](https://www.youtube.com/watch?v=BEmAo6Fdg-Q) – C++ on Sea (2020)

:book:

- J.Galowicz. [*C++17 STL cookbook: Discover the latest enhancements to functional programming and lambda expressions*](https://www.packtpub.com/application-development/c17-stl-cookbook) (2017)
- N.M.Josuttis. [*The C++ standard library: A tutorial and reference*](http://www.cppstdlib.com/) (2012)

:anchor:

- B.Revzin. [*The mothership has landed: Adding `<=>` to the library*](https://wg21.link/p1614) – WG21/P1614 <!-- move -->

#### Implementations

:link:

- [*libstdc++*](https://github.com/gcc-mirror/gcc/tree/master/libstdc%2B%2B-v3)
- [*libc++*](https://github.com/llvm-mirror/libcxx)
- [*Microsoft*](https://github.com/microsoft/STL)

### Boost

:link:

- [Boost library incubator](http://blincubator.com/)

## Design principles

:movie_camera:

- A.Stepanov. [*STL and its design principles*](https://www.youtube.com/watch?v=COuHLky7E2Q) (2002)
- B.Steagall. [*Back to basics: Classic STL*](https://www.youtube.com/watch?v=0itiHQVWq4M) – CppCon (2021)

### Customization point objects

:link:

- [*Customization point design in C++11 and beyond*](https://ericniebler.com/2014/10/21/customization-point-design-in-c11-and-beyond/) (2014)

:grey_question:

- [*What are customization point objects and how to use them?*](https://stackoverflow.com/q/53495848) – Stack Overflow

---

## Algorithms

:link:

- S.Dargo. [*The big STL algorithms tutorial: wrapping up*](https://www.sandordargo.com/blog/2022/02/23/stl-alogorithms-tutorial-part-31-wrap-up) (2022)
- S.Dargo. [*The big STL algorithms tutorial: the memory header*](https://www.sandordargo.com/blog/2022/02/02/stl-alogorithms-tutorial-part-30-memory-header) (2022)
- S.Dargo. [*The big STL algorithms tutorial: more numeric algorithms*](https://www.sandordargo.com/blog/2022/01/05/stl-alogorithms-tutorial-part-28-more_numeric) (2022)
- S.Dargo. [*The big STL algorithms tutorial: Introduction*](https://www.sandordargo.com/blog/2019/01/30/stl-algos-intro) (2019)

:movie_camera:

- C.Hoekstra. *Algorithm intuition.* [Part I](https://www.youtube.com/watch?v=pUEnO6SvAMo), [Part II](https://www.youtube.com/watch?v=sEvYmb3eKsw) – CppCon (2019)
- J.Boccara. [*105 STL algorithms in less than an hour*](https://www.youtube.com/watch?v=bXkWuUe9V2I) – ACCU (2018)
- J.Boccara. [*105 STL algorithms in less than an hour*](https://www.youtube.com/watch?v=2olsGf6JIkU) – CppCon (2018)
- M.Clow. [*STL algorithms: How to use them and how to write your own*](https://www.youtube.com/watch?v=3nXLxMYXgWs) – ACCU (2016)
- M.Clow. [*STL algorithms: Why you should use them, and how to write your own*](https://www.youtube.com/watch?v=h4Jl1fk3MkQ) – CppCon (2016)
- M.VanLoon. [*STL algorithms in action*](https://www.youtube.com/watch?v=eidEEmGLQcU) – CppCon (2015)

<!-- ### `std::accumulate`

 -->

### `std::iota`

:link:

- S.Parent. [*#iotashaming*](https://sean-parent.stlab.cc/2019/01/04/iota.html) (2019)

:grey_question:

- [*What does iota of `std::iota` stand for?*](https://stackoverflow.com/q/9244879) – Stack Overflow

### `std::midpoint`

:movie_camera:

- M.Clow. [*`std::midpoint`? How hard could it be?*](https://www.youtube.com/watch?v=sBtAGxBh-XI) – CppCon (2019)

:anchor:

- S.D.Herring. [*Well-behaved interpolation for numbers and pointers*](https://wg21.link/p0811) – WG21/P0811

### `std::next_permutation` / `std::prev_permutation` / `std::is_permutation`

:grey_question:

- [*How to create a permutation using STL for number of places lower than the total length?*](https://stackoverflow.com/q/61392431) – Stack Overflow

:anchor:

- [*`std::next_permutation`*](https://en.cppreference.com/w/cpp/algorithm/next_permutation) – C++ reference
- [*`std::prev_permutation`*](https://en.cppreference.com/w/cpp/algorithm/prev_permutation) – C++ reference
- [*`std::is_permutation`*](https://en.cppreference.com/w/cpp/algorithm/is_permutation) – C++ reference

### `std::[stable_]sort` / `std::is_sorted`

:link:

- A.Demin. [*How sorting is implemented in the standard library*](http://demin.ws/blog/russian/2009/06/18/sort-implementation-in-stl/) (in Russian, 2009)

:grey_question:

- [*How can I sort two vectors in the same way, with criteria that uses only one of the vectors?*](https://stackoverflow.com/q/17074324) – Stack Overflow

### `std::[stable_]partition`

:link:

- A.A.Stepanov, M.A.Marcus. [Sec. 3: *Partition algorithms*](http://stepanovpapers.com/PAM3-partition_notes.pdf) – Notes for the Foundations of programming course (2004–2005)

:grey_question:

- [*`stable_partition` on forward iterators*](https://stackoverflow.com/q/59642958) – Stack Overflow
- [*How is `stable_partition` an adaptive algorithm?*](https://stackoverflow.com/q/21554635) – Stack Overflow

### `std::[transform_]exclusive_scan` / `std::[transform_]inclusive_scan`

:link:

- S.Dargo. [*The big STL algorithms tutorial: numeric scans*](https://www.sandordargo.com/blog/2022/01/19/stl-alogorithms-tutorial-part-29-numeric-scans) (2022)

:anchor:

- [*`std::exclusive_scan`*](https://en.cppreference.com/w/cpp/algorithm/exclusive_scan) – C++ reference
- [*`std::transform_exclusive_scan`*](https://en.cppreference.com/w/cpp/algorithm/transform_exclusive_scan) – C++ reference
- [*`std::inclusive_scan`*](https://en.cppreference.com/w/cpp/algorithm/inclusive_scan) – C++ reference
- [*`std::transform_inclusive_scan`*](https://en.cppreference.com/w/cpp/algorithm/transform_inclusive_scan) – C++ reference

---

## Concepts

See also [*Concepts* – Templates](templates.md#concepts).

:grey_question:

[*Why does `same_as` concept check type equality twice?*](https://stackoverflow.com/q/58509147) – Stack Overflow

---

## Containers

:grey_question:

- [*Nesting `std::` containers of movable objects*](https://stackoverflow.com/q/61269785) – Stack Overflow
- [*Does C++11 allow `vector<const T>`?*](https://stackoverflow.com/q/6954906) – Stack Overflow
- [*What’s the best way to iterate over two or more containers simultaneously*](https://stackoverflow.com/q/12552277) – Stack Overflow

:movie_camera:

- B.Steagall. [*If I had my ’druthers: A proposal for improving the containers in C++2x*](https://www.youtube.com/watch?v=bAE0qteS4Rk) – C++Now (2018)
- D.Higgins. [*Using STL containers efficiently*](https://www.youtube.com/watch?v=oBbGC-sUYVA) – CppCon (2016)
- M.Clow. [*Customizing the standard containers*](https://www.youtube.com/watch?v=NyivAC3WE6g) – CppCon (2016)
- B.Stroustrup. [*Why you should avoid linked lists*](https://www.youtube.com/watch?v=YQs6IC-vgmo) – Going Native (2012)

### Associative containers

> Associative containers are: `std::set` (collection of unique keys, sorted by keys), `std::map` (collection of key-value pairs, sorted by keys, keys are unique), `std::multiset` (collection of keys, sorted by keys), and `std::multimap` (collection of key-value pairs, sorted by keys).

:link:

- P.J.Plauger. [*Standard C/C++: Implementing associative containers*](https://github.com/eugnsp/CUJ/blob/master/15.05/plauger/plauger.md) – C/C++ Users Journal **15** (1997)

#### `std::set`

:link:

- A.O’Dwyer. [*Implementation divergence with a moved-from `set` comparator*](https://quuxplusone.github.io/blog/2023/05/10/lwg-2227/) (2023)
- K.Kreft, A.Langer. [*Effective standard C++ library: Are `set` iterators mutable or immutable*](https://github.com/eugnsp/CUJ/blob/master/18.10/kreft/kreft.md) – C/C++ Users Journal **18** (2000)
- M.Austern. [*Why you shouldn’t use `set` – and what you should use instead*](http://lafstern.org/matt/col1.pdf) – C++ Report (2000)

#### `std::map`

:grey_question:

- [*`insert` vs `emplace` vs `operator[]` in C++ `std::map`*](https://stackoverflow.com/q/17172080) – Stack Overflow
- [*Is there any reason to use `std::map::emplace()` instead of `try_emplace()` in C++1z?*](https://stackoverflow.com/q/46046828) – Stack Overflow

### Sequence containers

> Sequence containers are: `std::array` (static contiguous array), `std::vector` (dynamic contiguous array), `std::deque` (double-ended queue), `std::forward_list` (singly-linked list), and `std::list` (doubly-linked list).

See also [*Arrays and vectors* – Sequence data structures and algorithms](../data_structures_and_algorithms/sequence.md#arrays-and-vectors).

:link:

- A.O’Dwyer. [*The “array size constant” antipattern*](https://quuxplusone.github.io/blog/2020/08/06/array-size/) (2020)

#### `std::array`

:grey_question:

- [*Create `N`-element `constexpr` array in C++11*](https://stackoverflow.com/q/19019252) – Stack Overflow
- [*Why isn’t `std::array::size` static?*](https://stackoverflow.com/q/21936507) – Stack Overflow

#### `std::deque`

:grey_question:

- [*What really is a deque in STL?*](https://stackoverflow.com/q/6292332) – Stack Overflow
- [*Why is an STL deque not implemented as just a circular vector?*](https://stackoverflow.com/q/39324192) – Stack Overflow
- [*How can references be valid while iterators become invalidated in a deque*](https://stackoverflow.com/q/32800138) – Stack Overflow
- [*STL deque accessing by index is `O(1)`?*](https://stackoverflow.com/q/2297164) – Stack Overflow

#### `std::forward_list`

> Before this container was standardized, some Standard library implementations provided `std::slist` container as an extention.

:link:

- P.J.Plauger. [*Standard C/C++: A singly linked list*](https://github.com/eugnsp/CUJ/blob/master/18.02/plauger/plauger.md) – C/C++ Users Journal **18** (2000)

#### `std::list`

:link:

- H.Hinnant. [*On `std::list::size`*](https://howardhinnant.github.io/On_list_size.html)
- P.J.Plauger. [*Standard C/C++: A better list*](https://github.com/eugnsp/CUJ/blob/master/17.08/plauger/plauger.md) – C/C++ Users Journal **17** (1999)

:grey_question:

- [*Is `list::size()` really `O(n)`?*](https://stackoverflow.com/q/228908) – Stack Overflow
- [*Why is `std::list` bigger on C++11?*](https://stackoverflow.com/q/10065055) – Stack Overflow
- [*Why does `std::list::reverse` have `O(n)` complexity?*](https://stackoverflow.com/q/35612220) – Stack Overflow
- [*Why does `std::list` have `remove` and `remove_if` functions*](https://stackoverflow.com/q/56571235) – Stack Overflow

:anchor:

- [*`std::list`*](https://en.cppreference.com/w/cpp/container/list) – C++ reference
- [*`std::list`*](https://www.boost.org/sgi/stl/List.html) – SGI STL

#### `std::vector`

:link:

- A.O’Dwyer. [*What is the “vector pessimization”?*](https://quuxplusone.github.io/blog/2022/08/26/vector-pessimization/) (2022)
- G.Romer. [TotW #112: *`emplace` vs. `push_back`*`](https://abseil.io/tips/112) – Abseil C++ Tips
- R.Getov. [*Persistent vector iterators*](https://github.com/eugnsp/CUJ/blob/master/17.01/getov/getov.md) – C/C++ Users Journal **17** (1999)
- [*`folly::fbvector`*](https://github.com/facebook/folly/blob/master/folly/docs/FBVector.md)

:grey_question:

- [*How to enforce move semantics when a vector grows?*](https://stackoverflow.com/q/8001823) – Stack Overflow
- [*Making `std::vector` allocate aligned memory*](https://stackoverflow.com/q/12942548) – Stack Overflow
- [*What is the ideal growth rate for a dynamically allocated array?*](https://stackoverflow.com/q/1100311) – Stack Overflow
- [*Why would I ever use `push_back` instead of `emplace_back`?*](https://stackoverflow.com/q/10890653) – Stack Overflow
- [*Can `std::vector` `emplace_back` copy construct from an element of the vector itself?*](https://stackoverflow.com/q/24908718) – Stack Overflow
- [*Is inserting an element of a `std::vector` into the same vector allowed?*](https://stackoverflow.com/q/29300408) – Stack Overflow

:book:

- B.Stroustrup. *Making a `vector` fit for a standard* – S.B.Lippman. [*C++ gems: Programming pearls from The C++ report*](https://www.cambridge.org/ru/academic/subjects/computer-science/software-engineering-and-development/c-gems-programming-pearls-c-report) (1997)
- T.Cargill. *A dynamic vector is harder than it looks* – S.B.Lippman. [*C++ gems: Programming pearls from The C++ report*](https://www.cambridge.org/ru/academic/subjects/computer-science/software-engineering-and-development/c-gems-programming-pearls-c-report) (1997)

#### `std::vector<bool>`

:link:

- H.Hinnant. [*On `vector<bool>`*](https://howardhinnant.github.io/onvectorbool.html) (2012)

:grey_question:

- [*Why is `vector<bool>` not an STL container?*](https://stackoverflow.com/q/17794569) – Stack Overflow

### Strings

> The class template `std::basic_string` stores and manipulates sequences of `char`-like objects, which are non-array objects of trivial standard-layout type.

:memo:

- `std::basic_string<T, ...>` is the only container in the standard library that requires `T` to be a trivial standard-layout type.

:link:

- A.Mertz. [*`std::string` is not a container for raw data*](https://arne-mertz.de/2018/11/string-not-for-raw-data/) (2018)
- O.Betts. [*Empty strings in C++*](https://survex.com/~olly/blog/coding/empty-strings-in-c%2B%2B.html) (2013)
- H.Sutter. [GotW #29: *Strings*](http://www.gotw.ca/gotw/029.htm) – Guru of the Week (2009)
- P.Becker. [*Questions & Answers: The complex evolution of `<string>`*](https://github.com/eugnsp/CUJ/blob/master/16.01/becker/becker.md#conditional-operator) – C/C++ Users Journal **16** (1998)
- P.J.Plauger. [*Standard C/C++: The header `<string>`*](https://github.com/eugnsp/CUJ/blob/master/13.07/plauger/plauger.md) – C/C++ Users Journal **13** (1995)

:grey_question:

- [*Why `std::string` does not have `const char*` cast*](https://stackoverflow.com/q/59076004) – Stack Overflow
- [*Why doesn’t `std::string` provide implicit conversion to `char*`?*](https://stackoverflow.com/q/492061) – Stack Overflow
- [*Is it safe to append `std::string` to itself?*](https://stackoverflow.com/q/37074905) – Stack Overflow
- [*How do I check if a C++ `std::string` starts with a certain string, and convert a substring to an `int`?*](https://stackoverflow.com/q/1878001) – Stack Overflow
- [*Most optimized way of concatenation in strings*](https://stackoverflow.com/q/18892281) – Stack Overflow
- [*Why are there so many string classes in the face of `std::string`?*](https://softwareengineering.stackexchange.com/q/151619) – Software Engineering

:movie_camera:

- B.Ruth. [*`std::basic_string`: For more than just text*](https://www.youtube.com/watch?v=SDJImePyftY) – CppCon (2018)

:anchor:

- [*`std::basic_string`*](https://en.cppreference.com/w/cpp/string/basic_string) – C++ reference

#### Short string optimization

See also [*Local buffer optimization* – Patterns, idioms, and design principles](patterns_and_idioms.md#local-buffer-optimization).

:grey_question:

- [*Meaning of acronym SSO in the context of `std::string`*](https://stackoverflow.com/q/10315041) – Stack Overflow

#### `std::string_view`

> The class template `std::basic_string_view` describes an object that can refer to a constant contiguous sequence of `char`-like objects.

:link:

- A.O’Dwyer. [*Three reasons to pass `std::string_view` by value*](https://quuxplusone.github.io/blog/2021/11/09/pass-string-view-by-value/) (2021)
- J.Miller. [*C++ `std::string_view` for better performance: An example use case*](https://www.nextptr.com/tutorial/ta1217154594/cplusplus-stdstring_view-for-better-performance-an-example-use-case) (2019)
- A.O’Dwyer. [*`std::string_view` is a borrow type*](https://quuxplusone.github.io/blog/2018/03/27/string-view-is-a-borrow-type/) (2018)
- J.M&uuml;ller. [*`std::string_view` accepting temporaries: good idea or horrible pitfall?*](https://www.foonathan.net/2017/03/string_view-temporary/) (2017)
- M.Chastain. [TotW #1: *`string_view`*](https://abseil.io/tips/1) – Abseil C++ Tips

:grey_question:

- [*How exactly is `std::string_view` faster than `const std::string&`?*](https://stackoverflow.com/q/40127965) – Stack Overflow
- [*Is a `std::string_view` literal guaranteed to be null-terminated?*](https://stackoverflow.com/q/40127965) – Stack Overflow

:movie_camera:

- V.Ciura [*Enough `string_view` to hang ourselves*](https://www.youtube.com/watch?v=xwP4YCP_0q0) – CppCon (2018)
- M.Clow. [*`string_view`: When to use it and when not*](https://www.youtube.com/watch?v=H9gAaNRoon4) – CppCon (2015)
- N.MacIntosh. [*Evolving `array_view` and `string_view` for safe C++ code*](https://www.youtube.com/watch?v=C4Z3c4Sv52U) – CppCon (2015)

#### C-strings

:grey_question:

- [*Is it guaranteed to be safe to perform `memcpy(0, 0, 0)`?*](https://stackoverflow.com/q/5243012) – Stack Overflow

### Unordered containers

> Unordered containers are: `std::unordered_set` (collection of unique keys, hashed by keys), `std::unordered_map` (collection of key-value pairs, hashed by keys, keys are unique), `std::unordered_multiset` (collection of keys, hashed by keys), and `std::unordered_multimap` (collection of key-value pairs, hashed by keys).

:link:

- A.O’Dwyer. [*`unordered_multiset`’s API affects its big-O*](https://quuxplusone.github.io/blog/2022/06/23/unordered-multiset-equal-range/) (2022)
- J.M.L&oacute;pez Mu&ntilde;oz. [*Advancing the state of the art for `std::unordered_map` implementations*](https://accu.org/journals/overload/27/149/sharpe_2619/) – [Overload **170**](https://accu.org/journals/overload/overload170) (2022)
- J.M.L&oacute;pez Mu&ntilde;oz. [*Advancing the state of the art for `std::unordered_map` implementations*](https://bannalia.blogspot.com/2022/06/advancing-state-of-art-for.html) (2022)
- P.Trettner. [*Measuring `std::unordered_map` badness*](https://artificial-mind.net/blog/2021/10/09/unordered-map-badness) (2021)
- N.Wu. [*Blowing up `unordered_map`, and how to stop getting hacked on it*](https://codeforces.com/blog/entry/62393) (2018)
- P.J.Plauger. [*Standard C/C++: Hash tables*](https://github.com/eugnsp/CUJ/blob/master/16.11/plauger/plauger.md) – C/C++ Users Journal **16** (1998)

:grey_question:

- [*How `std::unordered_map` is implemented*](https://stackoverflow.com/q/31112852) – Stack Overflow
- [*How does C++ STL `unordered_map` resolve collisions?*](https://stackoverflow.com/q/21518704) – Stack Overflow
- [*Why is `unordered_map` “`find` + `insert`” faster than “`insert` + check for success”?*](https://stackoverflow.com/q/31804025) – Stack Overflow
- [*Performance of `emplace` is worse than check followed by `emplace`*](https://stackoverflow.com/q/24209592) – Stack Overflow

:movie_camera:

- D.K&uuml;hl. [*#Hashing*](https://www.youtube.com/watch?v=CJsQSIp7-Ig) – ACCU (2019)
- M.Skarupke. [*You can do better than `std::unordered_map`: New improvements to hash table performance*](https://www.youtube.com/watch?v=M2fKMP47slQ) – C++Now (2018)

:anchor:

- M.Austern. [*A proposal to add hash tables to the standard library*](https://wg21.link/n1456) – WG21/N1456
- J.M.L&oacute;pez Mu&ntilde;oz. [*`erase(iterator)` for unordered containers should not return an iterator*](https://wg21.link/n2023) – WG21/N2023
- M.Pusz. [*Heterogeneous lookup for unordered containers*](https://wg21.link/p0919) – WG21/P0919
- A.Tavory, V.Dreizin, B.Kosnik. [*Hash table design*](https://gcc.gnu.org/onlinedocs/libstdc++/ext/pb_ds/hash_based_containers.html) – [Policy-based data structures](https://gcc.gnu.org/onlinedocs/libstdc++/ext/pb_ds/)

#### `std::hash`

:grey_question:

- [*Does `std::hash` guarantee equal hashes for ”equal” floating point numbers?*](https://stackoverflow.com/questions/14943817) – Stack Overflow

:anchor:

- [*`std::hash`*](https://en.cppreference.com/w/cpp/utility/hash) – C++ reference
- [*C++ named requirements: Hash*](https://en.cppreference.com/w/cpp/named_req/Hash) – C++ reference
- W.E.Brown. [*Adjuncts to `std::hash`*](https://wg21.link/p0549) – WG21/P0549

### Container adaptors

#### `std::stack`

:grey_question:

- [*`std::stack` implementation on different containers - What is the actual difference?*](https://stackoverflow.com/questions/63043291) – Stack Overflow

:anchor:

- [*`std::stack`*](https://en.cppreference.com/w/cpp/container/stack) – C++ reference
- [*`std::stack`*](https://www.boost.org/sgi/stl/stack.html) – SGI STL

#### `std::queue`

:grey_question:

- [*Why doesn’t `std::queue::pop` return value?*](https://stackoverflow.com/q/25035691) – Stack Overflow

:anchor:

- [*std::queue*](https://en.cppreference.com/w/cpp/container/queue) – C++ reference

#### `std::priority_queue`

:grey_question:

- [*Priority queue clear method*](https://stackoverflow.com/q/2852140) – Stack Overflow

:anchor:

- [*std::priority_queue*](https://en.cppreference.com/w/cpp/container/priority_queue) – C++ reference

### Container views

#### `std::span`

> The class template `std::span` describes an object that can refer to a contiguous sequence of objects with the first element of the sequence at position zero. A span can either have a static extent or a dynamic extent.

:link:

- A.O’Dwyer. [*`std::span` should have a converting constructor from `initializer_list`*](https://quuxplusone.github.io/blog/2021/10/03/p2447-span-from-initializer-list/) (2021)
- B.Revzin. [*`span`: the best span*](https://brevzin.github.io/c++/2018/12/03/span-best-span/) (2018)
- B.Revzin. [*Should span be regular?*](https://medium.com/@barryrevzin/should-span-be-regular-6d7e828dd44) (2018)

:grey_question:

- [*What is a `span` and when should I use one?*](https://stackoverflow.com/q/45723819) – Stack Overflow
- [*Why does `std::span` lack `cbegin` and `cend` methods?*](https://stackoverflow.com/q/62757700) – Stack Overflow

:movie_camera:

- V.Ciura. [*A short life `span<>` for a regular mess*](https://www.youtube.com/watch?v=J02S50z5zEo) – CppCon (2019)

:anchor:

- [*`std::span`*](https://en.cppreference.com/w/cpp/container/span) – C++ reference
- N.MacIntosh, S.T.Lavavej. [*`span`: bounds-safe views for sequences of objects*](https://wg21.link/p0122) – WG21/P0122
- C.Jabot, C.Carter. [*Range constructor for `std::span`*](https://wg21.link/p1394) – WG21/P1394
- T.Van Eerd. [*Should `span` be regular?*](https://wg21.link/p1085) – WG21/P1085
- T.Brindle. [*Usability enhancements for `std::span`*](https://wg21.link/p1024) – WG21/P1024
- J.Brown. [*Signed `ssize()` functions, unsigned `size()` functions*](https://wg21.link/p1227) – WG21/P1227
- R.Douglas, N.Liber, M.Clow. [*Sizes should only `​span​` unsigned*](https://wg21.link/p1089) – WG21/P1089

### Transparent comparators

> Transparent comparators make it possible to avoid constructing an object of the type `key_type` to do the lookup using member functions like `find`, `lower_bound`, etc.

:grey_question:

- [*What are transparent comparators?*](https://stackoverflow.com/q/20317413) – Stack Overflow
- [*Why is there no `std::is_transparent` equivalent for unordered containers?*](https://stackoverflow.com/q/33373228) – Stack Overflow

:anchor:

- J.Wakely, S.T.Lavavej, J.M.L&oacute;pez Mu&ntilde;oz. [*Adding heterogeneous comparison lookup to associative containers*](https://wg21.link/n3657) – WG21/N3657

### Erasing from containers

:link:

- A.O’Dwyer. [*How to erase from an STL container*](https://quuxplusone.github.io/blog/2020/07/08/erase-if/) (2020)

:grey_question:

- [*Is stability of `std::remove` and `std::remove_if` design fail?*](https://stackoverflow.com/q/13818369) – Stack Overflow

:anchor:

- B.Friedman. [*Unstable remove algorithms*](https://wg21.link/p0041) – WG21/P0041

### Signedness vs unsignedness of size

:link:

- [*unsigned integers*](https://blog.libtorrent.org/2016/05/unsigned-integers/) – libtorrent blog (2016)
- D.Crocker. [*Danger – unsigned types used here!*](https://critical.eschertech.com/2010/04/07/danger-unsigned-types-used-here/) (2010)

:grey_question:

- [*Why is `std::ssize()` introduced in C++20?*](https://stackoverflow.com/q/56217283) – Stack Overflow
- [*Why are unsigned integers error prone?*](https://stackoverflow.com/q/30395205) – Stack Overflow

:movie_camera:

- J.Kalb. [*`unsigned`: A guideline for better code*](https://www.youtube.com/watch?v=wvtFGa6XJDU) – CppCon (2016)

:anchor:

- J.Brown. [*Signed `ssize()` functions, unsigned `size()` functions*](https://wg21.link/p1227) – WG21/P1227
- R.Douglas, N.Liber, M.Clow. [*Sizes should only `​span`​ unsigned*](https://wg21.link/p1089) – WG21/P1089

### Non-standard containers

:link:

- [*Amadeus containers (amc)*](https://github.com/AmadeusITGroup/amc)

---

## Exceptions

See also [*Exceptions* – Core language](core_language.md#exceptions) and [*Exceptions* – Patterns, idioms, and design principles](patterns_and_idioms.md#exceptions).

:link:

- A.O’Dwyer. [*What is the “vector pessimization”?*](https://quuxplusone.github.io/blog/2022/08/26/vector-pessimization/) (2022)
- A.O’Dwyer. [*A “pick two” triangle for `std::vector`*](https://quuxplusone.github.io/blog/2022/09/30/vector-pessimization-pick-two/) (2022)

### `noexcept` specifier

:grey_question:

- [*Why those two `std::string::find()` functions are declared as `noexcept`?*](https://stackoverflow.com/q/66603543) – Stack Overflow
- [*Why vector access operators are not specified as `noexcept`?*](https://stackoverflow.com/q/20517259) – Stack Overflow

:anchor:

- A.Berg&eacute;. [*“Throws: Nothing” should be `noexcept`*](https://wg21.link/p1656) – WG21/P1656

### `std::bad_alloc`

:anchor:

- A.Krzemie&nacute;ski, T.Kami&nacute;ski. [*`bad_alloc` is not out-of-memory!*](https://wg21.link/p1404) – WG21/P1404

---

## Input/output

:grey_question:

- [*`tellg()` function give wrong size of file?*](https://stackoverflow.com/q/22984956) – Stack Overflow
- [*Why does `std::getline()` skip input after a formatted extraction?*](https://stackoverflow.com/q/21567291) – Stack Overflow
- [*Why is `iostream::eof` inside a loop condition (i.e. `while (!stream.eof())`) considered wrong?*](https://stackoverflow.com/q/5605125) – Stack Overflow
- [*Who architected/designed C++’s IO Streams, and would it still be considered well-designed by today’s standards?*](https://stackoverflow.com/q/2753060) – Stack Overflow

:anchor:

- [*Input/output via `<iostream>` and `<cstdio>`*](https://isocpp.org/wiki/faq/input-output) – C++ FAQ
- [*Input/output library*](https://en.cppreference.com/w/cpp/io) – C++ reference

### Input/output manipulators

#### `std::endl`

:link:

- C.Sharpe. [*Don’t use `std::endl`*](https://accu.org/journals/overload/27/149/sharpe_2619/) – [Overload **149**](https://accu.org/journals/overload/overload149) (2019)
- D.K&uuml;hl. [*Stop excessive use of `std::endl`*](https://kuhllib.com/2012/01/14/stop-excessive-use-of-stdendl/) (2012)

:anchor:

- [*`std::endl`*](https://en.cppreference.com/w/cpp/io/manip/endl) – C++ reference

### Output formatting

:link:

- [*{fmt}: a modern formatting library*](https://github.com/fmtlib/fmt)
- S.Ignatchenko. [*5 Reasons **not** to use `std::ostream` for human-readable output*](https://accu.org/journals/overload/26/144/ignatchenko_2486/) – [Overload **143**](https://accu.org/journals/overload/overload143) (2018)
- D.Epp. [*IOStream is hopelessly broken*](https://www.moria.us/articles/iostream-is-hopelessly-broken/) (2017)
- H.Sutter. [*The string formatters of manor farm*](http://www.gotw.ca/publications/mill19.htm) (2001)

:grey_question:

- [*`std::printf` vs. `std::cout`*](https://stackoverflow.com/q/2872543) – Stack Overflow
- [*Is `std::cout` synchronized/thread-safe?*](https://stackoverflow.com/q/6374264) – Stack Overflow

#### Standard formatting library

:link:

- S.Collyer. [*C++20 text formatting: An introduction*](https://accu.org/journals/overload/29/166/collyer/) – [Overload **166**](https://accu.org/journals/overload/overload166) (2021)

:grey_question:

- [*How can I use C++20 `std::format`?*](https://stackoverflow.com/q/59024390) – Stack Overflow

:anchor:

- V.Zverovich, L.Howes. [*Text formatting*](https://wg21.link/p0645) – WG21/P0645

### `std::stringstream`

:grey_question:

- [*`stringstream <<` “overwriting”*](https://stackoverflow.com/q/10388032) – Stack Overflow

### `std::ios_base::Init`

> The class `std::ios_base::Init` is used to ensure that the default C++ streams (`std::cin`, `std::cout`, etc.) are properly initialized and destructed; the class tracks how many instances of it are created and initializes the C++ streams when the first instance is constructed as well as flushes the output streams when the last instance is destructed. [The nifty counter idiom](patterns_and_idioms.md#nifty-counter) is typically used in implementations.

---

## Iterators

See also [*Iterator* – Patterns, idioms, and design principles](patterns_and_idioms.md#iterator).

:link:

- S.Dargo. [*C++ basics: Pointers vs iterators*](https://www.sandordargo.com/blog/2022/03/16/iterators-vs-pointers) (2022)
- S.Meyers. [*Three guidelines for effective iterator usage*](https://www.drdobbs.com/cpp/three-guidelines-for-effective-iterator/184401406) – Dr.Dobb’s Journal (2001)
- K.Kreft, A.Langer. [*Iterators in the Standard C++ library*](https://web.archive.org/web/20050308162147/http://www.langer.camelot.de/Articles/C++Report/IteratorsInStdlib/IteratorsInStdlib.html) – C++ Report (1996)

:grey_question:

- [*`const_iterator` and constness of `const_iterator::value_type`*](https://stackoverflow.com/q/12819405) – Stack Overflow
- [*Why use iterators instead of array indices?*](https://stackoverflow.com/q/131241) – Stack Overflow
- [*Iterator loop vs index loop*](https://stackoverflow.com/q/14373934) – Stack Overflow
- [*Why is `std::iterator` deprecated?*](https://stackoverflow.com/q/43268146) – Stack Overflow

:movie_camera:

- C.Carter. [*Iterator haiku*](https://www.youtube.com/watch?v=rZs9ndzGB_8) – CppCon (2016)

:anchor:

- [*Boost.Iterator: The iterator library*](https://www.boost.org/doc/libs/release/libs/iterator/)

### Reverse iterators

:grey_question:

- [*Iterator vs reverse iterator*](https://stackoverflow.com/q/889262) – Stack Overflow

---

## Ranges

:link:

- T.Brindle. [*Rvalue ranges and views in C++20*](https://tristanbrindle.com/posts/rvalue-ranges-and-views) (2020)

:movie_camera:

- T.Brindle. [*An overview of standard ranges*](https://www.youtube.com/watch?v=d9qDEEJFwNc) – ACCU (2021)
- T.Brindle. [*C++20 ranges in practice*](https://www.youtube.com/watch?v=d_E-VLyUnzc) – CppCon (2020)
- T.Brindle. [*An overview of standard ranges*](https://www.youtube.com/watch?v=SYLgG7Q5Zws) – CppCon (2019)
- A.Schödl. [*Why iterators got it all wrong and what we should use instead*](https://www.youtube.com/watch?v=srp9Tie5BYk) – CodeNode (2017)
- A.Schödl. [*From iterators to ranges: The upcoming evolution of the STL*](https://www.youtube.com/watch?v=vrCtS6FDay8) – Meeting C++ (2015)

### Views

:grey_question:

- [*Ranges `filter_view::iterator` element modification results in UB*](https://stackoverflow.com/q/75456524) – Stack Overflow

:movie_camera:

- N.Josuttis. [*C++ views*](https://www.youtube.com/watch?v=qv29fo9sUjY) – ACCU (2023)

---

## Memory

See also [*Memory* – Optimization and hardware](optimization_and_hardware.md#memory).

### `std::malloc` / `std::calloc` / `std::free`

:grey_question:

- [*How is `malloc()` implemented internally?*](https://stackoverflow.com/q/3479330) – Stack Overflow
- [*Difference between `malloc` and `calloc`?*](https://stackoverflow.com/q/1538420) – Stack Overflow

:anchor:

- [R.10: *Avoid `malloc()` and `free()`*](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Rr-mallocfree) – C++ core guidelines

:book:

- Ch. 3: *Memory ownership* – F.G.Pikus. [*Hands-on design patterns with C++*](https://www.packtpub.com/application-development/hands-design-patterns-c) (2019)

### Allocators

:grey_question:

- [*What does (template) `rebind<>` do?*](https://stackoverflow.com/q/14148756) – Stack Overflow
- [*Why is `allocator::rebind` necessary when we have template template parameters?*](https://stackoverflow.com/q/12362363) – Stack Overflow
- [*Why is `std::allocator` a template?*](https://stackoverflow.com/q/45267275) – Stack Overflow

:movie_camera:

- P.Halpern. [*Allocators: The good parts*](https://www.youtube.com/watch?v=v3dz-AKOVL8) – CppCon (2017)
- B.Steagall. [*How to write a custom allocator*](https://www.youtube.com/watch?v=kSWfushlvB8) – CppCon (2017)

:anchor:

- [*`std::allocator`*](https://en.cppreference.com/w/cpp/memory/allocator) – C++ reference

### Smart pointers

> A smart pointer is a class that simulates a raw C++ pointer, and provides automatic exception-safe object lifetime management.

:link:

- R.Chen. [*Making sure that people use `make_unique` and `make_shared` to make your object*](https://devblogs.microsoft.com/oldnewthing/20220721-00/?p=106879) (2022)
- S.Dargo. [*Smart pointers and their deleters*](https://www.sandordargo.com/blog/2022/06/08/smart-pointers-and-deleters) (2022)
- A.O’Dwyer. [*In praise of `make_unique`*](https://quuxplusone.github.io/blog/2018/05/26/the-versatile-make-unique/) (2018)
- H.Sutter. [GotW #91: *Smart pointer parameters*](https://herbsutter.com/2013/06/05/gotw-91-solution-smart-pointer-parameters/) – Guru of the Week (2013)
- Y.Sharon. [*Smart pointers: What, why, which?*](http://ootips.org/yonat/4dev/smart-pointers.html) (1999)

:grey_question:

- [*What is a smart pointer and when should I use one?*](https://stackoverflow.com/q/106508) – Stack Overflow
- [*Why is `shared_ptr<void>` legal, while `unique_ptr<void>` is ill-formed?*](https://stackoverflow.com/q/39288891) – Stack Overflow
- [*Does `unique_ptr` and `shared_ptr` able to convert to each other’s type?*](https://stackoverflow.com/q/37884728) – Stack Overflow

:movie_camera:

- R.Grimm. [*Back to basics: Smart pointers*](https://www.youtube.com/watch?v=sQCSX7vmmKY) – CppCon (2020)
- A.O’Dwyer. [*Back to basics: Smart pointers*](https://www.youtube.com/watch?v=xGDLkt-jBJ4) – CppCon (2019)
- M.Fleming. [*The smart pointers I wish I had*](https://www.youtube.com/watch?v=CKCR5eFVrmc) – CppCon (2019)
- U.Drepper. [*C++ and memory: Between correctness and performance*](https://www.youtube.com/watch?v=LXfSXzxDY_M&t=1924) – code::dive (2018)

:anchor:

- [*Smart pointer*](https://en.wikipedia.org/wiki/Smart_pointer) – Wikipedia
- [*Boost.SmartPtr: The smart pointer library*](https://www.boost.org/doc/libs/release/libs/smart_ptr/)

#### `std::unique_ptr`

> The `std::unique_ptr` class is a smart pointer with unique ownership. `std::unique_ptr<T>` is *almost* as cheap as a raw pointer `T*`. For the Itanium ABI, any type with a destructor that is passed by value must be passed in memory: the address held in the `std::unique_ptr​` must be written out to memory, rather than passed in registers as it would be for a raw ​`T*`​.

:link:

- M.Clow. [*Simplifying code and achieving exception safety using `unique_ptr`*](https://cplusplusmusings.wordpress.com/2015/03/09/simplifying-code-and-achieving-exception-safety-using-unique_ptr/) (2015)
- E.Bendersky. [*Using `unique_ptr` with standard library containers*](https://eli.thegreenplace.net/2012/06/20/c11-using-unique_ptr-with-standard-library-containers) (2012)
- A.Soffer. [TotW #187: *`std::unique_ptr` must be moved*`](https://abseil.io/tips/187) – Abseil C++ Tips
- Y.Mandelbaum. [TotW #134: *`make_unique` and private constructors*`](https://abseil.io/tips/134) – Abseil C++ Tips
- J.Dennett. [TotW #126: *`make_unique` is the new `new`*`](https://abseil.io/tips/126) – Abseil C++ Tips

:grey_question:

- [*What to use `std::optional` or `std::unique_ptr`?*](https://stackoverflow.com/q/44856701) – Stack Overflow
- [*Should I assign or reset a `unique_ptr`?*](https://stackoverflow.com/q/16061407) – Stack Overflow
- [*`make_unique` with brace initialization*](https://stackoverflow.com/q/55141594) – Stack Overflow
- [*How do I pass a `unique_ptr` argument to a constructor or a function?*](https://stackoverflow.com/q/8114276) – Stack Overflow
- [*Why can a `T*` be passed in register, but a `unique_ptr<T>` cannot?*](https://stackoverflow.com/q/58339165) – Stack Overflow

:anchor:

- [*`std::unique_ptr`*](https://en.cppreference.com/w/cpp/memory/unique_ptr) – C++ reference
- S.T.Lavavej. [*`make_unique`*](https://wg21.link/n3588) – WG21/N3588

#### `std::shared_ptr`

> The `std::unique_ptr` class is a smart pointer with shared ownership.

:link:

- A.Williams. [*`std::shared_ptr`’s secret constructor*](https://www.justsoftwaresolutions.co.uk/cplusplus/shared-ptr-secret-constructor.html) (2015)
- H.Kumar. [*`shared_ptr` initialized with `nullptr` is null or empty?*](https://www.nextptr.com/question/qa1372136808/shared_ptr-initialized-with-nullptr-is-null-or-empty) (2020)

:grey_question:

- [*`std::shared_ptr` exception safety*](https://stackoverflow.com/q/20053504) – Stack Overflow
- [*`std::shared_ptr` thread safety*](https://stackoverflow.com/q/14482830) – Stack Overflow
- [*`shared_ptr` magic*](https://stackoverflow.com/q/3899790) – Stack Overflow
- [*How do I call `std::make_shared` on a class with only protected or private constructors?*](https://stackoverflow.com/q/8147027) – Stack Overflow
- [*What is the difference between an empty and a null `std::shared_ptr` in C++?*](https://stackoverflow.com/q/25920681) – Stack Overflow

:anchor:

- [*`std::shared_ptr`*](https://en.cppreference.com/w/cpp/memory/shared_ptr) – C++ reference

#### `std::enable_shared_from_this`

> `std::enable_shared_from_this` allows a member function of an object that is currently managed by a `std::shared_ptr` to extend the lifetime of that object dynamically by generating additional `std::shared_ptr` instances.

:link:

- R.Chen. [*Inside STL: The `shared_ptr` constructor and `enable_shared_from_this`*](https://devblogs.microsoft.com/oldnewthing/20230816-00/?p=108608) (2023)

:grey_question:

- [*What is the usefulness of `enable_shared_from_this`?*](https://stackoverflow.com/q/712279) – Stack Overflow

:anchor:

- [*`std::enable_shared_from_this`*](https://en.cppreference.com/w/cpp/memory/enable_shared_from_this) – C++ reference

#### `std::weak_ptr`

:grey_question:

- [*When is `std::weak_ptr` useful?*](https://stackoverflow.com/q/12030650) – Stack Overflow

:anchor:

- [*`std::weak_ptr`*](https://en.cppreference.com/w/cpp/memory/weak_ptr) – C++ reference

#### `std::auto_ptr`

> `std::auto_ptr` is a smart pointer with unique ownership that had been designed before rvalue references and move semantics were introduced into the language. It was deprecated in C++11 and removed in C++17.

:link:

- H.Sutter. [GotW #25: *`auto_ptr`*](http://www.gotw.ca/gotw/025.htm) – Guru of the Week (2009)

:anchor:

- [*`std::auto_ptr`*](https://en.cppreference.com/w/cpp/memory/auto_ptr) – C++ reference

#### `std::observer_ptr`

> `std::observer_ptr` is a smart pointer that takes no ownership responsibility for its pointees (non-owning pointer).

:anchor:

- [*`std::experimental::observer_ptr`*](https://en.cppreference.com/w/cpp/experimental/observer_ptr) – C++ reference
- B.Stroustrup. [*Abandon `observer_ptr`*](https://wg21.link/p1408) – WG21/P1408
- W.E.Brown. [*A proposal for the world’s dumbest smart pointer*](https://wg21.link/n4282) – WG21/N4282

#### `boost::intrusive_ptr`

> The `boost::intrusive_ptr` class is a smart pointer that stores a pointer to an object with an embedded reference count, which is managed somewhere outside the smart pointer.

:link:

- B.Wicht. [*Boost `intrusive_ptr`: Faster shared pointer*](https://baptiste-wicht.com/posts/2011/11/boost-intrusive_ptr.html) (2011)

:grey_question:

- [*Boost intrusive pointer*](https://stackoverflow.com/q/40137660) – Stack Overflow

:anchor:

- [*`intrusive_ptr`*](https://www.boost.org/doc/libs/release/libs/smart_ptr/smart_ptr.htm#intrusive_ptr) – Boost.SmartPtr
- I.Muerte. [*An intrusive smart pointer*](https://wg21.link/p0468) – WG21/P0468

#### `std::out_ptr` and `std::inout_ptr` adaptors

> `std::out_ptr` and `std::inout_ptr` are a thing convertible to a `T**` that updates (with a `reset()` call or semantically equivalent behavior) the smart pointer it is created with when it goes out of scope.

:link:

- S.Dargo. [*C++23: `std::out_ptr` and `std::inout_ptr`*](https://www.sandordargo.com/blog/2022/12/07/inout_ptr-and-out_ptr) (2022)

:grey_question:

- [*Understanding `std::inout_ptr` and `std::out_ptr` in C++23*](https://stackoverflow.com/q/68918312) – Stack Overflow

:anchor:

- [*`std::out_ptr_t`*](https://en.cppreference.com/w/cpp/memory/out_ptr_t) – C++ reference
- [*`std::inout_ptr_t`*](https://en.cppreference.com/w/cpp/memory/inout_ptr_t) – C++ reference
- J.Meneide, T.Buyukliev, I.Muerte. [*`out_ptr` – a scalable output pointer abstraction*](https://wg21.link/p1132) – WG21/P1132

---

## Numerics

### Bit manipulation functions

:anchor:

- [*Standard library header `<bit>`*](https://en.cppreference.com/w/cpp/header/bit) – C++ reference
- V.Reverdy. [*On the names of low-level bit manipulation functions*](https://wg21.link/p1956) – WG21/P1956

### `std::bit_cast`

:anchor:

- [`std::bit_cast`](https://en.cppreference.com/w/cpp/numeric/bit_cast) – C++ reference
- J.Bastien. [*Bit-casting object representations*](https://wg21.link/p0476) – WG21/P0476

### Linear algebra support

:link:

- V.Reverdy. [*On vectors, tensors, matrices, and hypermatrices*](https://wg21.link/p1770) – WG21/P1770
- M.Hoemmen et al. [*Historical lessons for C++ linear algebra library standardization*](https://wg21.link/p1417) – WG21/P1417

:movie_camera:

- G.Davidson. [*A linear algebra library for C++23*](https://www.youtube.com/watch?v=RzO7s-RbLwk) – C++ on Sea (2019)
- G.Davidson. [*Standardizing a linear algebra library*](https://www.youtube.com/watch?v=cIPmhIiY68U) – Meeting C++ (2018)

:anchor:

- G.Davidson, ​B.Steagall. [*A proposal to add linear algebra support to the C++ standard library*](https://wg21.link/p1385) – WG21/P1385
- G.Davidson, ​B.Steagall. [*What do we need from a linear algebra library?*](https://wg21.link/p1166) – WG21/P1166

### Random numbers

:link:

- M.E.O’Neill. [*Everything you never wanted to know about C++’s `random_device`*](http://www.pcg-random.org/posts/cpps-random_device.html) – PCG (2015)
- M.E.O’Neill. [*C++ seeding surprises*](https://www.pcg-random.org/posts/cpp-seeding-surprises.html) – PCG (2015)

:grey_question:

- [*Why is the new random library better than `std::rand()`?*](https://stackoverflow.com/q/53040940) – Stack Overflow
- [*Why not just use `random_device`?*](https://stackoverflow.com/q/39288595) – Stack Overflow
- [*Random engine differences*](https://stackoverflow.com/q/16536617) – Stack Overflow
- [*How to succinctly, portably, and thoroughly seed the `mt19937` PRNG?*](https://stackoverflow.com/q/45069219) – Stack Overflow
- [*If we seed `mt19937` as the same on different machines, will we get the same sequence of random numbers?*](https://stackoverflow.com/q/48730363) – Stack Overflow

:movie_camera:

- A.Weis. [*Random numbers are hard*](https://www.youtube.com/watch?v=WDScnjQwEK8) – Meeting C++ (2019)
- W.E.Brown. [*What C++ programmers need to know about header `<random>`*](https://www.youtube.com/watch?v=6DPkyvkMkk8) – CppCon (2016)
- C.Marks. [*I just wanted a random integer!*](https://www.youtube.com/watch?v=4_QO1nm7uJs) – CppCon (2016)
- S.T.Lavavej. [*`rand()` considered harmful*](https://www.youtube.com/watch?v=LDPMpc-ENqY) – GoingNative (2013)

:anchor:

- M.Klammler. [*Efficient seeding of random number engines*](https://wg21.link/p0205) – WG21/P0205
- M.Paterno. [*On random-number distributions for C++0x*](https://wg21.link/n1588) – WG21/N1588
<!-- http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2003/n1452.html -->

---

## Regular expressions

:link:

- [*Regular expressions library*](https://en.cppreference.com/w/cpp/regex) – C++ reference

:movie_camera:

- T.Shen. [*Regular expressions in C++, present and future*](https://www.youtube.com/watch?v=N_rkHzhXueo) – CppCon (2016)

---

## Type support

### `std::type_info`

> This class holds implementation-specific information about a type, including the name of the type and means to compare two types for equality or collating order. This is the class returned by the `typeid` operator.

:grey_question:

- [*Unmangling the result of `std::type_info::name`*](https://stackoverflow.com/q/281818) – Stack Overflow

:anchor:

- [*`std::type_info`*](https://en.cppreference.com/w/cpp/types/type_info) – C++ reference

### Additional basic types

#### `std::nullptr_t`

> `std::nullptr_t` is the type of the null pointer literal `nullptr`. It is a distinct type that is not itself a pointer type or a pointer to member type. An object of this type can be converted to any pointer or pointer-to-member type by a standard conversion.

:link:

- [*`nullptr`*](https://en.wikibooks.org/wiki/More_C%2B%2B_Idioms/nullptr) – WikiBooks

:grey_question:

- [*How does `nullptr` implementation work?*](https://stackoverflow.com/q/61283569) – Stack Overflow
- [*Why is `nullptr` a part of the core language, but `nullptr_t` is a part of STL?*](https://stackoverflow.com/q/57628496) – Stack Overflow
- [*Is `nullptr` falsy?*](https://stackoverflow.com/q/57527189) – Stack Overflow

:anchor:

- [*`std::nullptr_t`*](https://en.cppreference.com/w/cpp/types/nullptr_t) – C++ reference
- H.Sutter, B.Stroustrup. [*A name for the null pointer: `nullptr`*](https://wg21.link/n2431) – WG21/N2431

### Fixed-width integer types

> `std::int8_t`, `std::int16_t`, `std::int32_t`, and `std::int64_t` are guaranteed to use 2’s complement to represent negative values. They are provided only if the implementation directly supports the type.

:link:

- S.Ignatchenko. [*C++: On using `int*_t` as overload and template parameters*](http://ithare.com/c-on-using-int_t-as-overload-and-template-parameters/) (2018)

:grey_question:

- [*When is `uint8_t` ≠ `unsigned char`?*](https://stackoverflow.com/q/16138237) – Stack Overflow
- [*`size_t` vs `uintptr_t`*](https://stackoverflow.com/questions/1464174) – Stack Overflow
- [*Is `intmax_t` the same as `long long int`?*](https://stackoverflow.com/q/20459513) – Stack Overflow

### Uninitialized storage

> `std::aligned_storage` defines the type suitable for use as uninitialized storage for types of given size, `aligned_union` defines the type suitable for use as uninitialized storage for all given types.

:grey_question:

- [*What is the purpose of `std::aligned_storage`?*](https://stackoverflow.com/q/50271304) – Stack Overflow
- [*Placement new in `std::aligned_storage`?*](https://stackoverflow.com/q/28187732) – Stack Overflow

:anchor:

- C.J.Johnson. [*Deprecate `std::aligned_storage` and `std::aligned_union`*](https://wg21.link/p1413) – WG21/P1413

### `std::byte`

:anchor:

- [*`std::byte`*](https://en.cppreference.com/w/cpp/types/byte) – C++ reference
- N.MacIntosh. [*A byte type for increased type safety*](https://wg21.link/p0257) – WG21/P0257

### Type traits

See also [*Type traits* – Templates](templates.md#type-traits).

:memo:

- There 14 [primary type categories](https://en.cppreference.com/w/cpp/header/type_traits#Primary_type_categories): `is_void`, `is_null_pointer`, `is_integral`, `is_floating_point`, `is_array`, `is_enum`, `is_union`, `is_class`, `is_function`, `is_pointer`, `is_lvalue_reference`, `is_rvalue_reference`, `is_member_object_pointer`, `is_null_pointer`. Each type belongs to exactly one of them.

:movie_camera:

- M.Clow. [*Type traits: What are they and why should I use them?*](https://www.youtube.com/watch?v=VvbTP_k_Df4) – CppCon (2015)

:anchor:

- [*Standard library header `<type_traits>`*](https://en.cppreference.com/w/cpp/header/type_traits) – C++ reference

#### `std::is_class`

:grey_question:

- [*How does this implementation of `std::is_class` work?*](https://stackoverflow.com/questions/35213658/how-does-this-implementation-of-stdis-class-work) – Stack Overflow

#### `std::is_base_of`

:grey_question:

- [*How does `is_base_of` work?*](https://stackoverflow.com/q/2910979) – Stack Overflow

#### `std::is_trivial*`

:movie_camera:

- J.Turner. [*Great C++ `is_trivial`*](https://www.youtube.com/watch?v=ZxWjii99yao) – CppCon (2019)

---

## Utilities

:link:

- [*Utility library*](https://en.cppreference.com/w/cpp/utility) – C++ reference

### Integer comparison functions

Integer comparison functions `std::cmp_equal`, `std::cmp_not_equal`, `std::cmp_less`, `std::cmp_greater`, `std::cmp_less_equal`, `std::cmp_greater_equal` compare the values of two integers; unlike builtin comparison operators, negative signed integers always compare *less than* (and not *equal to*) unsigned integers: the comparison is safe against lossy integer conversion.

:anchor:

- [*Integer comparison functions*](https://en.cppreference.com/w/cpp/utility/intcmp) – C++ reference
- F.Kircheis. [*Safe integral comparisons*](https://wg21.link/p0586) – WG21/P0586

### Function objects

:link:

- [*Function objects*](https://en.cppreference.com/w/cpp/utility/functional) – C++ reference

:movie_camera:

- S.T.Lavavej. [*`<functional>`: What’s new, and proper usage*](https://www.youtube.com/watch?v=zt7ThwVfap0) – CppCon (2015)

#### `std::reference_wrapper`

`std::reference_wrapper` is a class template that wraps a reference in a copyable, assignable object; it can be used as a mechanism to store references inside standard containers, which cannot normally hold references.

:movie_camera:

- Z.Yuan. [*The many shades of `reference_wrapper`*](https://www.youtube.com/watch?v=EKJMZCL00Ak) - CppCon (2020)

:anchor:

- [*`std::reference_wrapper`*](https://en.cppreference.com/w/cpp/utility/functional/reference_wrapper) – C++ reference

### `std::initializer_list`

> An object of type `std::initializer_list<T>` is a lightweight proxy object that provides access to an array of objects of type `const T`.

:grey_question:

- [*`initializer_list` and template type deduction*](https://stackoverflow.com/q/12431495) – Stack Overflow
- [*`std::initializer_list` and move semantics*](https://stackoverflow.com/q/8193102) – Stack Overflow

:anchor:

- [*`std::initializer_list`*](https://en.cppreference.com/w/cpp/utility/initializer_list) – C++ reference

### Algebraic data types

:movie_camera:

- A.O’Dwyer. [*Back to basics: Algebraic data types*](https://www.youtube.com/watch?v=OJzmWqCCZaM) – CppCon (2020)

#### Pairs and tuples

:grey_question:

- [*Why can’t `std::tuple<int>` be trivially copyable?*](https://stackoverflow.com/q/38779985) – Stack Overflow
- [*Replace `N`-th element of a `std::tuple`*](https://stackoverflow.com/q/59670539) – Stack Overflow
- [*How does `std::tie` work?*](https://stackoverflow.com/q/43762651) – Stack Overflow

:movie_camera:

- A.Meredith. [*How C++20 can simplify `std::tuple`*](https://www.youtube.com/watch?v=SvxBvSK4i4k) – ACCU (2019)
- S.T.Lavavej. [*`tuple<>`: What’s new and how it works*](https://www.youtube.com/watch?v=JhgWFYfdIho) – CppCon (2016)

#### `std::optional`

> The class template `std::optional<T>` is a type that may or may not store a value of type `T` in its storage space. It is recommended to be used in situations where there is exactly one and clear reason for having no value of type `T`, and where the lack of value is as natural as having any regular value of `T`. It is not recommended to use optional to indicate that we were not able to compute a value because of a failure.

:link:

- A.Krzemieński. [*A moved-from optional*](https://akrzemi1.wordpress.com/2022/09/06/a-moved-from-optional/) (2022)
- B.Filipek. [*Using C++17 `std::optional`*](https://www.bfilipek.com/2018/05/using-optional.html) (2018)
- B.Filipek. [*Error handling and `std::optional`*](https://www.bfilipek.com/2018/05/errors-and-optional.html) (2018)
- B.Filipek. [*In-place construction for `std::any`, `std::variant` and `std::optional`*](https://www.bfilipek.com/2018/07/in-place-cpp17.html) (2018)
- B.Revzin. [*Implementing the spaceship operator for `optional`*](https://accu.org/journals/overload/26/147/revzin_2563/) – [Overload **147**](https://accu.org/journals/overload/overload147) (2018)
- S.Brand. [*Functional error-handling with optional and expected*](https://accu.org/journals/overload/26/143/brand_2462/) – [Overload **143**](https://accu.org/journals/overload/overload143) (2018)
- S.Brand. [*Functional exceptionless error-handling with optional and expected*](https://blog.tartanllama.xyz/optional-expected/) (2017)
- S.Brand. [*Implementation with functional-style extensions and reference support*](https://github.com/TartanLlama/optional)
- A.Krzemieński. [*Efficient optional values*](https://akrzemi1.wordpress.com/2015/07/15/efficient-optional-values/) (2015)
- A.Krzemieński. [*A gotcha with Optional*](https://akrzemi1.wordpress.com/2014/12/02/a-gotcha-with-optional/) (2014)

:grey_question:

- [*What to use: `std::optional` or `std::unique_ptr`?*](https://stackoverflow.com/q/44856701) – Stack Overflow
- [*Implementing `operator<=>` for `optional<T>`*](https://stackoverflow.com/q/47315539) – Stack Overflow
- [*Difference between Boost.Optional and `std::experimental::optional` assignment*](https://stackoverflow.com/q/40391244) – Stack Overflow

:anchor:

- [*`std::optional`*](https://en.cppreference.com/w/cpp/utility/optional) – C++ reference
- [*Boost.Optional: The optional wrapper library*](https://www.boost.org/doc/libs/release/libs/optional/)
- F.Cacciola, A.Krzemieński. [*A proposal to add a utility class to represent optional objects*](https://wg21.link/n3793) – WG21/N3793
- M.Mutz. [*More flexible `optional::value or()`*](https://wg21.link/p2218) – WG21/P2218
- A.Krzemieński. [*N3793 reference implementation*](https://github.com/akrzemi1/Optional/)

#### `std::variant`

:link:

- J.M&uuml;ller. [*Technique: Recursive variants and boxes*](https://www.foonathan.net/2022/05/recursive-variant-box/) (2022)
- A.Williams. [*Standardizing `variant`: Difficult decisions*](https://www.justsoftwaresolutions.co.uk/cplusplus/standardizing-variant.html) (2015)

:grey_question:

- [*How do I move the value of a `variant<Ts...>` into a `variant<T, Ts...>`?*](https://stackoverflow.com/q/61290807) – Stack Overflow

:movie_camera:

- R.Barkan. [*Variations on variants*](https://www.youtube.com/watch?v=YBXRiPKa_bc) – C++Now (2021)
- N.Liber. [*The many variants of `std::variant`*](https://www.youtube.com/watch?v=JUxhwf7gYLg) – C++Now (2019)
- M.Pusz. [*Effective replacement of dynamic polymorphism with `std::variant`*](https://www.youtube.com/watch?v=JGYxOieiZnY) – ACCU (2019)
- M.Pusz. [*Effective replacement of dynamic polymorphism with `std::variant`*](https://www.youtube.com/watch?v=gKbORJtnVu8) – CppCon (2018)
- D.Sankel. [*Variants: Past, present, and future*](https://www.youtube.com/watch?v=k3O4EKX4z1c) – CppCon (2016)

:anchor:

- [*`std::variant`*](https://en.cppreference.com/w/cpp/utility/variant) – C++ reference
- A.Naumann. [*Variant: a type-safe union*](https://wg21.link/n4542) – WG21/N4542
- Y.Zhihao. [*A sane `variant` converting constructor*](https://wg21.link/p0608) – WG21/P0608

#### `std::any`

See also [*Type erasure* – Patterns, idioms, and design principles](patterns_and_idioms.md#type-erasure).

:link:

- C.Carter. [*`std::any`: How, when, and why*](https://devblogs.microsoft.com/cppblog/stdany-how-when-and-why/) (2018)

:anchor:

- [*`std::any`*](https://en.cppreference.com/w/cpp/utility/any) – C++ reference

#### `(std::)expected`

> A proposed utility class to represent expected monad.

:link:

- S.Brand. [*Functional error-handling with optional and expected*](https://accu.org/journals/overload/26/143/brand_2462/) – [Overload **143**](https://accu.org/journals/overload/overload143) (2018)
- S.Brand. [*C++11/14/17 `std::expected` with functional-style extensions*](https://github.com/TartanLlama/expected)

:movie_camera:

- N.Douglas. [*Introduction to proposed `std::expected`*](https://www.youtube.com/watch?v=JfMBLx7qE0I) – Meeting C++ (2017)

:anchor:

- V.Botet, J.Bastien. [*`std::expected`*](https://wg21.link/p0323) – WG21/P0323
- N.Douglas. [*Concerns about `expected<T, E>` from the Boost.Outcome peer review*](https://wg21.link/p0762) – WG21/P0762
- V.Botet, P.Talbot. [*A proposal to add a utility class to represent expected monad*](https://wg21.link/n4109) – WG21/N4109

### `std::launder`

:grey_question:

- [*What is the purpose of `std::launder?`*](https://stackoverflow.com/q/39382501) – Stack Overflow
- [*Where can I find what `std::launder` really does?*](https://stackoverflow.com/q/53268089) – Stack Overflow

:anchor:

- [*`std::launder`*](https://en.cppreference.com/w/cpp/utility/launder) – C++ reference

### `std::source_location`

:grey_question:

- [*`std::experimental::source_location` at compile time*](https://stackoverflow.com/q/52977593) – Stack Overflow
- [*How to use source_location in a variadic template function?*](https://stackoverflow.com/q/57547273) – Stack Overflow

:anchor:

- [*`std::source_location`*](https://en.cppreference.com/w/cpp/utility/source_location) – C++ reference
- R.Douglas, C.Jabot, D.Kr&uuml;gler, P.Sommerlad. [*Adopt `source_location` for C++20*](https://wg21.link/p1208) – WG21/P1208

---

## Date and time utilities

:link:

- A.Krzemieński. [*Using `std::chrono`*](https://akrzemi1.wordpress.com/2022/04/11/using-stdchrono/) (2022)
- A.Krzemieński. [*Local time*](https://akrzemi1.wordpress.com/2022/04/24/local-time/) (2022)

:grey_question:

- [*Accepting `std::chrono::duration` of any representation/period*](https://stackoverflow.com/q/22362717) – Stack Overflow
- [*What are the uses of `std::chrono::high_resolution_clock`?*](https://stackoverflow.com/q/37426832) – Stack Overflow

:movie_camera:

- H.Hinnant. [*A `<chrono>` tutorial*](https://www.youtube.com/watch?v=P32hvk8b13M) – CppCon (2016)
- H.Hinnant. [*A C++14 approach to dates and times*](https://www.youtube.com/watch?v=tzyGjOm8AKo) – CppCon (2015)

:anchor:

- [*Date and time utilities*](https://en.cppreference.com/w/cpp/chrono) – C++ reference
- H.E.Hinnant, W.E.Brown, J.Garland, M.Paterno. [*A foundation to sleep on: Clocks, points in time, and time durations*](https://wg21.link/n2661) – WG21/N2661

---

## Filesystem

:grey_question:

- [*Native path separator bug in C++17 `std::filesystem::path`?*](https://stackoverflow.com/q/51886072) – Stack Overflow
- [*What is the C++17 equivalent to `boost::filesystem::unique_path()`?*](https://stackoverflow.com/q/43316527) – Stack Overflow

:anchor:

- [*Filesystem library*](https://en.cppreference.com/w/cpp/filesystem) – C++ reference

---

## Tricks and subtleties

:link:

- A.O’Dwyer. [*Don’t inherit from standard types*](https://quuxplusone.github.io/blog/2018/12/11/dont-inherit-from-std-types/) (2018)

:grey_question:

- [*In `std::exchange`, why is the second template parameter defaulted?*](https://stackoverflow.com/q/34876969) – Stack Overflow
- [*Why does the C++ standard algorithm `count` return a `difference_type` instead of `size_t`?*](https://stackoverflow.com/q/7505083) – Stack Overflow
- [*Why standard container iterators don’t overload `->*`?*](https://stackoverflow.com/q/48626039) – Stack Overflow
- [*Why does `numeric_limits` work on types it does not know?*](https://stackoverflow.com/q/47520847) – Stack Overflow
- [*Why is swap called by `std::sort` only if my container has more than 32 elements?*](https://stackoverflow.com/q/59473178) – Stack Overflow

:movie_camera:

- J.Brown. [*This one weird trick: `std::integral_constant`*](https://www.youtube.com/watch?v=MKes-sG3zAU) – CppCon (2019)

### Self-assignment

:link:

- E.Niebler. [*Post-conditions on self-move](https://ericniebler.com/2017/03/31/post-conditions-on-self-move/) (2017)

:grey_question:

- [*What does the standard library guarantee about self move assignment?*](https://stackoverflow.com/q/13127455) – Stack Overflow
- [*What is the rationale for self-assignment-unsafe move assignment operators in the standard library?*](https://stackoverflow.com/q/39852013) – Stack Overflow

### C standard library

:link:

- D.Levin. [*glibc: The C library in GNU/Linux system*](https://www.youtube.com/watch?v=qntaaVf5oUg) – OS Day (in Russian, 2018)
- J.Wakely. [*Why `<cstdlib>` is more complicated than you might think*](https://developers.redhat.com/blog/2016/02/29/why-cstdlib-is-more-complicated-than-you-might-think/) (2016)

:anchor:

- W.E.Brown. [*Deprecate certain declarations in the global namespace*](https://wg21.link/p0657) – WG21/P0657

---

## The Standard Template Library (STL)

:link:

- [*Standard Template Library*](https://en.wikipedia.org/wiki/Standard_Template_Library) – Wikipedia
- [*History of the Standard Template Library*](https://en.wikipedia.org/wiki/History_of_the_Standard_Template_Library) – Wikipedia

:grey_question:

- [*What’s the difference between “STL” and “C++ standard library”?*](https://stackoverflow.com/q/5205491) – Stack Overflow

:book:

- M.J.Vilot. *Standard template library* – S.B.Lippman. [*C++ gems: Programming pearls from The C++ report*](https://www.cambridge.org/ru/academic/subjects/computer-science/software-engineering-and-development/c-gems-programming-pearls-c-report) (1997)

:page_facing_up:

- D.R.Musser, A.A.Stepanov. [*A library of generic algorithms in Ada*](http://stepanovpapers.com/p216-musser.pdf) – [Proceedings of ACM SIGAda, 216](https://doi.org/10.1145/317500.317529) (1987)

:movie_camera:


:anchor:

- [*SGI STL: Programmer’s guide*](https://www.boost.org/sgi/stl/)

<!-- ## SFINAE

<!-- move into Templates
- [*Making `std::get` play nice with SFINAE*](https://stackoverflow.com/q/41708491) – Stack Overflow -->


