# The standard library, Boost and proposals <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [General information](#general-information)
	- [Implementations](#implementations)
- [Algorithms](#algorithms)
	- [`std::iota`](#stdiota)
	- [`std::midpoint`](#stdmidpoint)
- [Containers](#containers)
	- [Associative containers](#associative-containers)
	- [Sequence containers](#sequence-containers)
		- [`std::array`](#stdarray)
		- [`std::deque`](#stddeque)
		- [`std::vector`](#stdvector)
		- [`std::vector<bool>`](#stdvectorbool)
	- [Unordered containers](#unordered-containers)
- [Input/output](#inputoutput)
- [Iterators](#iterators)
- [Memory](#memory)
	- [Allocators](#allocators)
- [Numerics](#numerics)
	- [`std::bit_cast`](#stdbit_cast)
	- [Linear algebra support](#linear-algebra-support)
	- [Random numbers](#random-numbers)
- [Regular expressions](#regular-expressions)
- [Smart pointers](#smart-pointers)
	- [`std::unique_ptr`](#stdunique_ptr)
	- [`std::shared_ptr`](#stdshared_ptr)
		- [`std::enable_shared_from_this`](#stdenable_shared_from_this)
	- [`std::weak_ptr`](#stdweak_ptr)
	- [`std::auto_ptr`](#stdauto_ptr)
	- [`std::observer_ptr`](#stdobserver_ptr)
	- [`boost::intrusive_ptr`](#boostintrusive_ptr)
- [Strings](#strings)
	- [Short string optimization](#short-string-optimization)
	- [`std::string_view`](#stdstring_view)
- [Type support](#type-support)
	- [Fixed-width integer types](#fixed-width-integer-types)
	- [Type traits](#type-traits)
	- [`std::is_trivial*`](#stdis_trivial)
- [Utilities](#utilities)
	- [Function objects](#function-objects)
	- [Pairs and tuples](#pairs-and-tuples)
	- [Sum types](#sum-types)
		- [`std::variant`](#stdvariant)
		- [`(std::)expected`](#stdexpected)
	- [`std::launder`](#stdlaunder)
- [Tricks and subtleties](#tricks-and-subtleties)
- [The Standard Template Library (STL)](#the-standard-template-library-stl)

---

## General information

:book:

- J.Galowicz. [*C++17 STL cookbook: Discover the latest enhancements to functional programming and lambda expressions*](https://www.packtpub.com/application-development/c17-stl-cookbook) (2017)
- Ch. 18: *Concurrency* &ndash; N.M.Josuttis. [*The C++ standard library: A tutorial and reference*](http://www.cppstdlib.com/) (2012)

### Implementations

:link:

- [*libstdc++*](https://github.com/gcc-mirror/gcc/tree/master/libstdc%2B%2B-v3)
- [*libc++*](https://github.com/llvm-mirror/libcxx)
- [*Microsoft*](https://github.com/microsoft/STL)

---

## Algorithms

:movie_camera:

- C.Hoekstra. *Algorithm intuition.* [Part I](https://www.youtube.com/watch?v=pUEnO6SvAMo), [Part II](https://www.youtube.com/watch?v=sEvYmb3eKsw) &ndash; CppCon (2019)
- J.Boccara. [*105 STL algorithms in less than an hour*](https://www.youtube.com/watch?v=bXkWuUe9V2I) &ndash; ACCU (2018)
- M.Clow. [*STL algorithms: How to use them and how to write your own*](https://www.youtube.com/watch?v=3nXLxMYXgWs) &ndash; ACCU (2016)
- M.VanLoon. [*STL algorithms in action*](https://www.youtube.com/watch?v=eidEEmGLQcU) &ndash; CppCon (2015)

### `std::iota`

:link:

- S.Parent. [*#iotashaming*](https://sean-parent.stlab.cc/2019/01/04/iota.html) (2019)
- [*What does iota of `std::iota` stand for?*](https://stackoverflow.com/questions/9244879/what-does-iota-of-stdiota-stand-for) &ndash; Stack Overflow

### `std::midpoint`

:movie_camera:

- M.Clow. [*`std::midpoint`? How hard could it be?*](https://www.youtube.com/watch?v=sBtAGxBh-XI) &ndash; CppCon (2019)

:anchor:

- S.D.Herring. [*Well-behaved interpolation for numbers and pointers*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p0811r3.html) &ndash; WG21/P0811R3 (2019)

---

## Containers

:movie_camera:

- B.Steagall. [*If I had my ’druthers: A proposal for improving the containers in C++2x*](https://www.youtube.com/watch?v=bAE0qteS4Rk) &ndash; C++Now (2018)

### Associative containers

> Associative containers are: `std::set` (collection of unique keys, sorted by keys), `std::map` (collection of key-value pairs, sorted by keys, keys are unique), `std::multiset` (collection of keys, sorted by keys), and `std::multimap` (collection of key-value pairs, sorted by keys).

:link:

- [*`insert` vs `emplace` vs `operator[]` in C++ `std::map`*](https://stackoverflow.com/questions/17172080/insert-vs-emplace-vs-operator-in-c-map) &ndash; Stack Overflow

### Sequence containers

> Sequence containers are: `std::array` (static contiguous array), `std::vector` (dynamic contiguous array), `std::deque` (double-ended queue), `std::forward_list` (singly-linked list), and `std::list` (doubly-linked list).

#### `std::array`

:link:

- [*Create `N`-element `constexpr` array in C++11*](https://stackoverflow.com/questions/19019252/create-n-element-constexpr-array-in-c11) &ndash; Stack Overflow
- [*Why isn’t `std::array::size` static?*](https://stackoverflow.com/questions/21936507/why-isnt-stdarraysize-static) &ndash; Stack Overflow

#### `std::deque`

:link:

- [*What really is a deque in STL?*](https://stackoverflow.com/questions/6292332/what-really-is-a-deque-in-stl) &ndash; Stack Overflow

#### `std::vector`

:link:

- [*How to enforce move semantics when a vector grows?*](https://stackoverflow.com/questions/8001823/how-to-enforce-move-semantics-when-a-vector-grows) &ndash; Stack Overflow

#### `std::vector<bool>`

:link:

- H.E.Hinnant. [*On `vector<bool>`*](https://howardhinnant.github.io/onvectorbool.html) (2012)
- [*Why is `vector<bool>` not an STL container?*](https://stackoverflow.com/questions/17794569/why-is-vectorbool-not-a-stl-container) &ndash; Stack Overflow

### Unordered containers

> Unordered containers are: `std::unordered_set` (collection of unique keys, hashed by keys), `std::unordered_map` (collection of key-value pairs, hashed by keys, keys are unique), `std::unordered_multiset` (collection of keys, hashed by keys), and `std::unordered_multimap` (collection of key-value pairs, hashed by keys).

:link:

- [*Why is there no `std::is_transparent` equivalent for unordered containers?*](https://stackoverflow.com/questions/33373228/why-is-there-no-stdis-transparent-equivalent-for-unordered-containers) &ndash; Stack Overflow
- [*Why is `unordered_map` “`find` + `insert`” faster than “`insert` + check for success”?*](https://stackoverflow.com/questions/31804025/why-is-unordered-map-find-insert-faster-than-insert-check-for-success) &ndash; Stack Overflow
- [*Performance of `emplace` is worse than check followed by `emplace`*](https://stackoverflow.com/questions/24209592/performance-of-emplace-is-worse-than-check-followed-by-emplace) &ndash; Stack Overflow

:movie_camera:

- D.K&uuml;hl. [*#Hashing*](https://www.youtube.com/watch?v=CJsQSIp7-Ig) &ndash; ACCU (2019)
- M.Skarupke. [*You can do better than `std::unordered_map`: New improvements to hash table performance*](https://www.youtube.com/watch?v=M2fKMP47slQ) &ndash; C++Now (2018)

:anchor:

- M.Pusz. [*Heterogeneous lookup for unordered containers*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0919r3.html) &ndash; WG21/P0919R3 (2018)

---

## Input/output

:link:

* [`tellg()` function give wrong size of file?](https://stackoverflow.com/questions/22984956/tellg-function-give-wrong-size-of-file) &ndash; Stack Overflow

:anchor:

* [*Input/output library*](https://en.cppreference.com/w/cpp/io) &ndash; C++ reference

---

## Iterators

:link:

- [*Why use iterators instead of array indices?*](https://stackoverflow.com/questions/131241/why-use-iterators-instead-of-array-indices) &ndash; Stack Overflow
- [*Iterator loop vs index loop*](https://stackoverflow.com/questions/14373934/iterator-loop-vs-index-loop) &ndash; Stack Overflow

:movie_camera:

- C.Carter. [*Iterator haiku*](https://www.youtube.com/watch?v=rZs9ndzGB_8) &ndash; CppCon (2016)

---

## Memory

See also [*Memory and cache* &ndash; Optimization and hardware](optimization_and_hardware.md#memory-and-cache).

### Allocators

- [*What does (template) `rebind<>` do?*](https://stackoverflow.com/questions/14148756/what-does-template-rebind-do) &ndash; Stack Overflow
- [*Why is `allocator::rebind` necessary when we have template template parameters?*](https://stackoverflow.com/questions/12362363/why-is-allocatorrebind-necessary-when-we-have-template-template-parameters) &ndash; Stack Overflow

:anchor:

- [`std::allocator`](https://en.cppreference.com/w/cpp/memory/allocator) &ndash; C++ reference

---

## Numerics

### `std::bit_cast`

:anchor:

- [`std::bit_cast`](https://en.cppreference.com/w/cpp/numeric/bit_cast) &ndash; C++ reference
- J.Bastien. [*Bit-casting object representations*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0476r2.html) &ndash; WG21/P0476R2 (2017)

### Linear algebra support

:link:

V.Reverdy. [*On vectors, tensors, matrices, and hypermatrices*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1770r0.pdf)

:movie_camera:

- G.Davidson. [*Standardizing a linear algebra library*](https://www.youtube.com/watch?v=cIPmhIiY68U) &ndash; Meeting C++ (2018)

:anchor:

- M.Hoemmen et al. [*Historical lessons for C++ linear algebra library standardization*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1417r0.pdf) &ndash; WG21/P1417R0 (2019)
- G.Davidson, ​B.Steagall. [*A proposal to add linear algebra support to the C++ standard library*](http://open-std.org/JTC1/SC22/WG21/docs/papers/2019/p1385r3.pdf) &ndash; WG21/P1385R3 (2019)
- G.Davidson, ​B.Steagall. [*What do we need from a linear algebra library?*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1166r0.pdf) &ndash; WG21/P1166R0 (2019)

### Random numbers

:link:

- M.E.O’Neill. [*Everything you never wanted to know about C++’s `random_device`*](http://www.pcg-random.org/posts/cpps-random_device.html) &ndash; PCG (2015)
- [*Why is the new random library better than `std::rand()`?*](https://stackoverflow.com/questions/53040940/why-is-the-new-random-library-better-than-stdrand) &ndash; Stack Overflow
- [*Why not just use `random_device`?*](https://stackoverflow.com/questions/39288595/why-not-just-use-random-device) &ndash; Stack Overflow

:movie_camera:

- A.Weis. [*Random numbers are hard*](https://www.youtube.com/watch?v=WDScnjQwEK8) &ndash; Meeting C++ (2019)

---

## Regular expressions

:link:

- [*Regular expressions library*](https://en.cppreference.com/w/cpp/regex) &ndash; C++ reference

:movie_camera:

- T.Shen. [*Regular expressions in C++, present and future*](https://www.youtube.com/watch?v=N_rkHzhXueo) &ndash; CppCon (2016)

---

## Smart pointers

> A smart pointer is a class that simulates a raw C++ pointer, and provides automatic exception-safe object lifetime management.

:link:

- [*Smart pointer*](https://en.wikipedia.org/wiki/Smart_pointer) &ndash; Wikipedia
- [*Boost.SmartPtr: The smart pointer library*](https://www.boost.org/doc/libs/release/libs/smart_ptr/smart_ptr.htm)
- H.Sutter. [GotW #91: *Smart pointer parameters*](https://herbsutter.com/2013/06/05/gotw-91-solution-smart-pointer-parameters/) &ndash; Guru of the Week (2013)
- Y.Sharon. [*Smart pointers: What, why, which?*](http://ootips.org/yonat/4dev/smart-pointers.html) (1999)
- [*What is a smart pointer and when should I use one?*](https://stackoverflow.com/questions/106508/what-is-a-smart-pointer-and-when-should-i-use-one) &ndash; Stack Overflow
- [*Why is `shared_ptr<void>` legal, while `unique_ptr<void>` is ill-formed?*](https://stackoverflow.com/questions/39288891/why-is-shared-ptrvoid-legal-while-unique-ptrvoid-is-ill-formed) &ndash; Stack Overflow

:movie_camera:

- A.O’Dwyer. [*Back to basics: Smart pointers*](https://www.youtube.com/watch?v=xGDLkt-jBJ4) &ndash; CppCon (2019)
- M.Fleming. [*The smart pointers I wish I had*](https://www.youtube.com/watch?v=CKCR5eFVrmc) &ndash; CppCon (2019)

### `std::unique_ptr`

> The `std::unique_ptr` class is a smart pointer with unique ownership.

:link:

- [*What to use `std::optional` or `std::unique_ptr`?*](https://stackoverflow.com/questions/44856701/what-to-use-stdoptional-or-stdunique-ptr?rq=1) &ndash; Stack Overflow
- [*Should I assign or reset a `unique_ptr`?*](https://stackoverflow.com/questions/16061407/should-i-assign-or-reset-a-unique-ptr) &ndash; Stack Overflow
- [*`make_unique` with brace initialization*](https://stackoverflow.com/questions/55141594/make-unique-with-brace-initialization) &ndash; Stack Overflow
- [*How do I pass a `unique_ptr` argument to a constructor or a function?*](https://stackoverflow.com/questions/8114276/how-do-i-pass-a-unique-ptr-argument-to-a-constructor-or-a-function) &ndash; Stack Overflow

:anchor:

- [`std::unique_ptr`](https://en.cppreference.com/w/cpp/memory/unique_ptr) &ndash; C++ reference
- S.T.Lavavej. [`make_unique`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3588.htm) &ndash; WG21/N3588 (2013)

### `std::shared_ptr`

> The `std::unique_ptr` class is a smart pointer with shared ownership.

:link:

- [*`std::shared_ptr` thread safety*](https://stackoverflow.com/questions/14482830/stdshared-ptr-thread-safety) &ndash; Stack Overflow
- A.Williams. [*`std::shared_ptr`’s secret constructor*](https://www.justsoftwaresolutions.co.uk/cplusplus/shared-ptr-secret-constructor.html)

:anchor:

- [`std::shared_ptr`](https://en.cppreference.com/w/cpp/memory/shared_ptr) &ndash; C++ reference

#### `std::enable_shared_from_this`

> `std::enable_shared_from_this` allows a member function of an object that is currently managed by a `std::shared_ptr` to extend the lifetime of that object dynamically by generating additional `std::shared_ptr` instances.

:link:

- [*What is the usefulness of `enable_shared_from_this`?*](https://stackoverflow.com/questions/712279/what-is-the-usefulness-of-enable-shared-from-this) &ndash; Stack Overflow

:anchor:

- [`std::enable_shared_from_this`](https://en.cppreference.com/w/cpp/memory/enable_shared_from_this) &ndash; C++ reference

### `std::weak_ptr`

:link:

- [*When is `std::weak_ptr` useful?*](https://stackoverflow.com/questions/12030650/when-is-stdweak-ptr-useful) &ndash; Stack Overflow

:anchor:

- [`std::weak_ptr`](https://en.cppreference.com/w/cpp/memory/weak_ptr) &ndash; C++ reference

### `std::auto_ptr`

> `std::auto_ptr` is a smart pointer with unique ownership that had been designed before rvalue references and move semantics were introduced into the language. It was deprecated in C++11 and removed in C++17.

:link:

- H.Sutter. [GotW #25: *`auto_ptr`*](http://www.gotw.ca/gotw/025.htm) &ndash; Guru of the Week (2009)

:anchor:

- [`std::auto_ptr`](https://en.cppreference.com/w/cpp/memory/auto_ptr) &ndash; C++ reference

### `std::observer_ptr`

> `std::observer_ptr` is a smart pointer that takes no ownership responsibility for its pointees (non-owning pointer).

:anchor:

- [`std::experimental::observer_ptr`](https://en.cppreference.com/w/cpp/experimental/observer_ptr) &ndash; C++ reference
- B.Stroustrup. [Abandon `observer_ptr`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1408r0.pdf) &ndash; WG21/P1408R0 (2018)
- W.E.Brown. [A proposal for the world’s dumbest smart pointer](http://open-std.org/JTC1/SC22/WG21/docs/papers/2014/n4282.pdf) &ndash; WG21/N4282 (2014)

### `boost::intrusive_ptr`

> The `boost::intrusive_ptr` class is a smart pointer that stores a pointer to an object with an embedded reference count, which is managed somewhere outside the smart pointer.

:link:

- B.Wicht. [*Boost `intrusive_ptr`: Faster shared pointer*](https://baptiste-wicht.com/posts/2011/11/boost-intrusive_ptr.html) (2011)
- [*Boost intrusive pointer*](https://stackoverflow.com/questions/40137660/boost-intrusive-pointer) &ndash; Stack Overflow

:anchor:

- [*`intrusive_ptr`*](https://www.boost.org/doc/libs/release/libs/smart_ptr/smart_ptr.htm#intrusive_ptr) &ndash; Boost.SmartPtr
- I.Muerte. [*An intrusive smart pointer*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0468r1.html) &ndash; WG21/P0468R1 (2018)

---

## Strings

:memo:

- `std::basic_string<T, ...>` is the only container in the standard library that requires `T` to be a trivial standard-layout type.

:link:

- H.Sutter. [GotW #29: *Strings*](http://www.gotw.ca/gotw/029.htm) &ndash; Guru of the Week (2009)
- [*Why `std::string` does not have `const char*` cast*](https://stackoverflow.com/questions/59076004/why-stdstring-does-not-have-const-char-cast) &ndash; Stack Overflow
- [*Why doesn’t `std::string` provide implicit conversion to `char*`?*](https://stackoverflow.com/questions/492061/why-doesnt-stdstring-provide-implicit-conversion-to-char) &ndash; Stack Overflow

:anchor:

- [*`std::basic_string`*](https://en.cppreference.com/w/cpp/string/basic_string) &ndash; C++ reference

### Short string optimization

:link:

- [*Meaning of acronym SSO in the context of `std::string`*](https://stackoverflow.com/questions/10315041/meaning-of-acronym-sso-in-the-context-of-stdstring) &ndash; Stack Overflow

### `std::string_view`

:link:

- J.Miller. [C++ `std::string_view` for better performance: An example use case](https://www.nextptr.com/tutorial/ta1217154594/cplusplus-stdstring_view-for-better-performance-an-example-use-case) (2019)

:movie_camera:

- M.Clow. [*`string_view`: When to use it and when not*](https://www.youtube.com/watch?v=H9gAaNRoon4) &ndash; CppCon (2015)
- N.MacIntosh. [*Evolving `array_view` and `string_view` for safe C++ code*](https://www.youtube.com/watch?v=C4Z3c4Sv52U) &ndash; CppCon (2015)

---

## Type support

### Fixed-width integer types

:memo:

- `std::int8_t`, `std::int16_t`, `std::int32_t`, and `std::int64_t` are guaranteed to use 2’s complement to represent negative values.

:link:

- [*When is `uint8_t` ≠ `unsigned char`?*](https://stackoverflow.com/questions/16138237/when-is-uint8-t-%E2%89%A0-unsigned-char) &ndash; Stack Overflow

### Type traits

See also [*Type traits* &ndash; Templates](templates.md#type-traits).

:movie_camera:

- M.Clow. [*Type traits: What are they and why should I use them?*](https://www.youtube.com/watch?v=VvbTP_k_Df4) &ndash; CppCon (2015)

:anchor:

- [*Standard library header `<type_traits>`*](https://en.cppreference.com/w/cpp/header/type_traits) &ndash; C++ reference

### `std::is_trivial*`

:movie_camera:

- J.Turner. [*Great C++ `is_trivial`*](https://www.youtube.com/watch?v=ZxWjii99yao) &ndash; CppCon (2019)

---

## Utilities

:link:

- [*Utility library*](https://en.cppreference.com/w/cpp/utility) &ndash; C++ reference

### Function objects

:link:

- [*Function objects*](https://en.cppreference.com/w/cpp/utility/functional) &ndash; C++ reference

:movie_camera:

- S.T.Lavavej. [*`<functional>`: What’s new, and proper usage*](https://www.youtube.com/watch?v=zt7ThwVfap0) &ndash; CppCon (2015)

### Pairs and tuples

:link:

- [Why can’t `std::tuple<int>` be trivially copyable?](https://stackoverflow.com/questions/38779985/why-cant-stdtupleint-be-trivially-copyable) &ndash; Stack Overflow

:movie_camera:

- A.Meredith. [*How C++20 can simplify `std::tuple`*](https://www.youtube.com/watch?v=SvxBvSK4i4k) &ndash; ACCU (2019)
- S.T.Lavavej. [*`tuple<>`: What’s new and how it works*](https://www.youtube.com/watch?v=JhgWFYfdIho) &ndash; CppCon (2016)

### Sum types

#### `std::variant`

:movie_camera:

- N.Liber. [*The many variants of `std::variant`*](https://www.youtube.com/watch?v=JUxhwf7gYLg) &ndash; C++Now (2019)

:anchor:

- [`std::variant`](https://en.cppreference.com/w/cpp/utility/variant) &ndash; C++ reference

#### `(std::)expected`

> A proposed utility class to represent expected monad.

:link:

- S.Brand. [C++11/14/17 `std::expected` with functional-style extensions](https://github.com/TartanLlama/expected)

:anchor:

- V.Botet, J.F.Bastien. [*`std::expected`*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0323r7.html) &ndash; WG21/P0323R7 (2018)
- V.Botet, P.Talbot. [*A proposal to add a utility class to represent expected monad*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4109.pdf) &ndash; WG21/N4109 (2014)

### `std::launder`

:link:

- [*What is the purpose of `std::launder?`*](https://stackoverflow.com/questions/39382501/what-is-the-purpose-of-stdlaunder) &ndash; Stack Overflow
- [*Where can I find what `std::launder` really does?*](https://stackoverflow.com/questions/53268089/where-can-i-find-what-stdlaunder-really-does) &ndash; Stack Overflow

:anchor:

- [*`std::launder`*](https://en.cppreference.com/w/cpp/utility/launder) &ndash; C++ reference

---

## Tricks and subtleties

:link:

- A.O’Dwyer. [*Don’t inherit from standard types*](https://quuxplusone.github.io/blog/2018/12/11/dont-inherit-from-std-types/) (2018)
- [*In `std::exchange`, why is the second template parameter defaulted?*](https://stackoverflow.com/questions/34876969/in-stdexchange-why-is-the-second-template-parameter-defaulted) &ndash; Stack Overflow
- [*Why does the C++ standard algorithm `count` return a `difference_type` instead of `size_t`?*](https://stackoverflow.com/questions/7505083/why-does-the-c-standard-algorithm-count-return-a-difference-type-instead-of) &ndash; Stack Overflow
- [*Why standard container iterators don’t overload `->*`?*](https://stackoverflow.com/questions/48626039/why-standard-container-iterators-dont-overload) &ndash; Stack Overflow
- [*Why does `numeric_limits` work on types it does not know?*](https://stackoverflow.com/questions/47520847/c-why-does-numeric-limits-work-on-types-it-does-not-know) &ndash; Stack Overflow

:movie_camera:

- J.Brown. [*This one weird trick: `std::integral_constant`*](https://www.youtube.com/watch?v=MKes-sG3zAU) &ndash; CppCon (2019)

---

## The Standard Template Library (STL)

:link:

- [*Standard Template Library*](https://en.wikipedia.org/wiki/Standard_Template_Library) &ndash; Wikipedia
- [*History of the Standard Template Library*](https://en.wikipedia.org/wiki/History_of_the_Standard_Template_Library) &ndash; Wikipedia
- A.Stevens [*An interview with Alex Stepanov*](http://stepanovpapers.com/drdobbs-interview.html) &ndash; Dr.Dobb's Journal (1995)
- [*What’s the difference between “STL” and “C++ standard library”?*](https://stackoverflow.com/questions/5205491/whats-the-difference-between-stl-and-c-standard-library) &ndash; Stack Overflow

:page_facing_up:

- D.R.Musser, A.A.Stepanov. [*A library of generic algorithms in Ada*](http://stepanovpapers.com/p216-musser.pdf) &ndash; [Proceedings of ACM SIGAda, 216](https://doi.org/10.1145/317500.317529) (1987)

:movie_camera:

- A.Stepanov. [*STL and its design principles*](https://www.youtube.com/watch?v=COuHLky7E2Q) (2002)

:anchor:

- A.Stepanov et al. [*SGI STL: Source code and documentation*](https://web.archive.org/web/20171202101253/http://www.sgi.com:80/tech/stl/)

<!-- ## SFINAE

<!-- move into Templates
- [*Making `std::get` play nice with SFINAE*](https://stackoverflow.com/questions/41708491/making-stdget-play-nice-with-sfinae) &ndash; Stack Overflow -->

<!-- * A.Alexandrescu. [*Systematic error handling in C++*](https://www.youtube.com/watch?v=kaI4R0Ng4E8&t=570) &ndash; C++ and Beyond (2012) -->
