# Core language

## Table of contents

* [ABI](#abi)
	* [Itanium C++ ABI](#itanium-c-abi)
* [Attributes](#attributes)
	* [`[[nodiscard]]`](#nodiscard)
	* [`[[trivially_relocatable]]`](#trivially_relocatable)
* [Exceptions](#exceptions)
* [Functions](#functions)
	* [Argument-dependent lookup](#argument-dependent-lookup)
* [Keywords](#keywords)
	* [`const` and `mutable`](const-and-mutable)
	* [`friend`](#friend)
* [Standards](#standards)
	* [C++17](#c17)
	* [C++2a](#c2a)
* [Structured bindings](#structured-bindings)
* [Tricks](#tricks)
	* [Accessing private and protected members](#accessing-private-and-protected-members)
* [Types](#types)
	* [Aggregate and POD types](#aggregate-and-pod-types)
	* [Const-correctness](#const-correctness)
	* [Floating-point types](#floating-point-types)
	* [Function types](#function-types)
	* [Integral types](#integral-types)
	* [Opaque typedefs](#opaque-typedefs)
	* [References](#references)
		* [Lifetime of a temporary](#lifetime-of-a-temporary)
		* [Rvalue references and move semantics](#rvalue-references-and-move-semantics)
	* [Type conversions](#type-conversions)
		* [`dynamic_cast`](dynamiccast)

---

## ABI

### Itanium C++ ABI

> The Itanium C++ ABI is an ABI for C++. As an ABI, it gives precise rules for implementing the language, ensuring that separately-compiled parts of a program can successfully interoperate. It is not platform-specific and can be layered portably on top of an arbitrary C ABI. It is used as the standard C++ ABI for many major operating systems on all major architectures, and is implemented in many major C++ compilers, including GCC and Clang.

:link:

* [*Itanium C++ ABI*](https://itanium-cxx-abi.github.io/cxx-abi/abi.html)

---

## Attributes

:movie_camera:

* B.Saks. [*Better code with C++ attributes*](https://www.youtube.com/watch?v=teUA5U6eYQY) &ndash; CppCon (2019)

### `[[nodiscard]]`

> This attribute encourages the compiler to issue a warning if the return value is discarded.

:memo:

* Conservative approach suggested by N.Josuttis:
	* Should be added:
		* *existing APIs*: not using the return value always is a "huge mistake"; not using the return value is a source of trouble and easily can happen;
		* *new APIs*: not using the return value is usually an error.
	* Should not be added:
		* *existing APIs*: not using the return value is a possible/common way of programming at least for some input; not using the return value makes no sense but doesn't hurt.

:link:

* [*What's the reason for not using C++17's `[[nodiscard]]` almost everywhere in new code?*](https://softwareengineering.stackexchange.com/questions/363169/whats-the-reason-for-not-using-c17s-nodiscard-almost-everywhere-in-new-c) &ndash; Software Engineering

:anchor:

* N.Josuttis. [*`[[nodiscard]]` in the Library*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r0.pdf) &ndash; WG21/P0600R0 (2017)

### `[[trivially_relocatable]]`

> This attribute specifies that the relocation operation for an object is trivial: moving the object and then immediately destroying the original is equivalent to `memcpy`. This attribute is not yet in the standard.

See [Relocation &ndash; Memory &ndash; Optimization and hardware](optimization_and_hardware.md#relocation).

---

## Exceptions

:link:

* [*Exceptions*](https://en.cppreference.com/w/cpp/language/exceptions) &ndash; C++ reference
* H.Sutter. [*When and how to use exceptions*](http://www.drdobbs.com/when-and-how-to-use-exceptions/184401836) &ndash; Dr.Dobb's Journal (2004)

---

## Functions

### Argument-dependent lookup

:link:

* [*Argument-dependent lookup*](https://en.cppreference.com/w/cpp/language/adl) &ndash; C++ reference
* [*What is “argument-dependent lookup” (aka ADL, or “Koenig Lookup”)?*](https://stackoverflow.com/questions/8111677/what-is-argument-dependent-lookup-aka-adl-or-koenig-lookup) &ndash; Stack Overflow
* A.O'Dwyer. [*What is ADL?*](https://quuxplusone.github.io/blog/2019/04/26/what-is-adl/) (2019)
* A.O'Dwyer. [*ADL insanity*](https://quuxplusone.github.io/blog/2019/04/08/adl-insanity/) (2019)
* A.O'Dwyer. [*How `hana::type<T>` “disables ADL”*](https://quuxplusone.github.io/blog/2019/04/09/adl-insanity-round-2/) (2019)

---

## Keywords

### `const` and `mutable`

:memo:

* In C++98: `const` means "logically `const`", in C++11 `const` means "thread safe" (bitwise `const` or internally synchronized).
* In C++98: `mutable` means "not observably non-`const`", in C++11 `mutable` means "thread safe" (bitwise `const` or internally synchronized).

:movie_camera:

* H.Sutter. [*You don't know `const` and `mutable`*](https://channel9.msdn.com/posts/C-and-Beyond-2012-Herb-Sutter-You-dont-know-blank-and-blank) &ndash; C++ and Beyond (2012)

### `friend`

#### Hidden friends

:link:

* A.Williams. [*The power of hidden friends in C++*](https://www.justsoftwaresolutions.co.uk/cplusplus/hidden-friends.html) (2019)

:anchor:

* [*Recommendations for specifying “hidden friends”*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1601r0.pdf) &ndash; WG21/P1601R0 (2019)

---

## Standards

### C++17

:movie_camera:

* A.Meredith. *C++17 in breadth (not depth).* [Part I](https://www.youtube.com/watch?v=22jIHfvelZk), [Part II](https://www.youtube.com/watch?v=-rIixnNJM4k) &ndash; CppCon (2016)

:anchor:

* [*C++17 compiler support*](https://en.cppreference.com/w/cpp/compiler_support#cpp17) &ndash; C++ reference

###	C++2a

:movie_camera:

* A.Meredith. [*How C++20 can simplify `std::tuple`*](https://www.youtube.com/watch?v=SvxBvSK4i4k) &ndash; ACCU (2019)

:anchor:

* [*C++2a compiler support*](https://en.cppreference.com/w/cpp/compiler_support#cpp2a) &ndash; C++ reference

---

## Structured bindings

:link:

* [*Structured bindings and tuple of references*](https://stackoverflow.com/questions/49628401/structured-bindings-and-tuple-of-references) &ndash; Stack Overflow

---

## Tricks

### Accessing private and protected members

:link:

* [*Accessing private members*](https://stackoverflow.com/questions/726096/accessing-private-members) &ndash; Stack Overflow
* J.Schaub. [*Access to private members. That's easy!*](https://bloglitb.blogspot.com/2010/07/access-to-private-members-thats-easy.html) &ndash; litb's Blog

---

## Types

### Aggregate, trivial and POD types

:link:

* [*Trivial, standard-layout, POD, and literal types*](https://docs.microsoft.com/en-us/cpp/cpp/trivial-standard-layout-and-pod-types?view=vs-2019) &ndash; Visual C++ language reference (2018)
* [*What are aggregates and PODs and how/why are they special?*](https://stackoverflow.com/questions/4178175/what-are-aggregates-and-pods-and-how-why-are-they-special) &ndash; Stack Overflow
* [*Trivial vs. standard layout vs. POD*](https://stackoverflow.com/questions/6496545/trivial-vs-standard-layout-vs-pod) &ndash; Stack Overflow

### Const-correctness

:link:

* [*Const correctness*](https://isocpp.org/wiki/faq/const-correctness) &ndash; C++ FAQ
* H.Sutter. [GotW #6: *Const-correctness*](http://www.gotw.ca/gotw/006.htm) &ndash; Guru of the Week (2009)
* [*Use of `const` for function parameters*](https://stackoverflow.com/questions/117293/use-of-const-for-function-parameters) &ndash; Stack Overflow
* [*C++ `const` keyword - use liberally?*](https://stackoverflow.com/questions/1554750/c-const-keyword-use-liberally) &ndash; Stack Overflow

### Floating-point types

See also [*Floating-point numbers* &ndash; Numeric data structures and algorithms](../data_structures_and_algorithms/numeric.md).

:link:

* D.Howard. [*Byte swapping floating point types*](https://web.archive.org/web/20100125081223/http://www.dmh2000.com/cpp/dswap.shtml)

### Function types

:anchor:

* A.Meredith. [*Abominable function types*](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2015/p0172r0.html) &ndash; WG21/P0172R0 (2015)

### Integral types

:link:

* [*Rule 04. Integers*](https://wiki.sei.cmu.edu/confluence/pages/viewpage.action?pageId=87152052) &ndash; SEI CERT C coding standard

### Opaque typedefs

> An opaque type is a new type that is distinct from and distinguishable from its underlying type, yet retaining layout compatibility with its underlying type. The intent is to allow programmer control (1) over substitutability between an opaque alias and its underlying type, and (2) over overloading based on any parameter whose type is or involves an opaque alias.

:memo:

* > Nobody seemed to know, so I wrote a mail to the author, Walter E. Brown, and asked him. He told me that Bjarne doesn’t like that feature (anymore), so it is very unlikely that it will come anytime soon. Apparently C++ won't get strong typedefs as core language feature. [[J.Müller]](https://foonathan.net/blog/2016/10/19/strong-typedefs.html)
* See [*Opaque typedefs* &ndash; Patterns and idioms](patterns_and_idioms.md#opaque-typedefs) for implementations at the library level.

:anchor:

* W.E.Brown. [*Toward opaque typedefs for C++1Y, v2*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3741.pdf) &ndash; WG21/N3741 (2013)

### References

:link:

* [*Is null reference possible?*](https://stackoverflow.com/questions/4364536/is-null-reference-possible) &ndash; Stack Overflow

#### Lifetime of a temporary

:link:

* [*Does a `const` reference class member prolong the life of a temporary?*](https://stackoverflow.com/questions/2784262/does-a-const-reference-class-member-prolong-the-life-of-a-temporary) &ndash; Stack Overflow
* [*Lifetime of a temporary*](https://en.cppreference.com/w/cpp/language/reference_initialization#Lifetime_of_a_temporary) &ndash; C++ reference

#### Rvalue references and move semantics

:link:

* [*A brief introduction to rvalue references*](https://www.artima.com/cppsource/rvalue.html) &ndash; H.E.Hinnant, B.Stroustrup, B.Kozicki (2008)
* [*C++ rvalue references explained*](http://thbecker.net/articles/rvalue_references/section_01.html) &ndash; T.Becker (2013)
* [*What is move semantics?*](https://stackoverflow.com/questions/3106110/what-is-move-semantics) &ndash; Stack Overflow
* [*Rvalues, lvalues and formal definitions*](https://stackoverflow.com/questions/56716647/rvalues-lvalues-and-formal-definitions) &ndash; Stack Overflow
* [*Pass by value vs pass by rvalue reference*](https://stackoverflow.com/questions/37935393/pass-by-value-vs-pass-by-rvalue-reference) &ndash; Stack Overflow

:movie_camera:

* N.Josuttis. [*The nightmare of move semantics for trivial classes*](https://www.youtube.com/watch?v=PNRju6_yn3o) &ndash; CppCon (2017)

### Type conversions

#### `dynamic_cast`

:link:

* [*`dynamic_cast` conversion*](https://en.cppreference.com/w/cpp/language/dynamic_cast) &ndash; C++ reference

:movie_camera:

* A.O'Dwyer. [*`dynamic_cast` from scratch*](https://www.youtube.com/watch?v=QzJL-8WbpuU) &ndash; CppCon (2017)


<!-- https://stackoverflow.com/questions/1613341/what-do-the-following-phrases-mean-in-c-zero-default-and-value-initializat

https://stackoverflow.com/questions/37618213/when-is-a-private-constructor-not-a-private-constructor
-->
