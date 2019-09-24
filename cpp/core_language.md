# Core language

## Table of contents

* [ABI](#abi)
	* [Itanium C++ ABI](#itanium-c-abi)
* [Attributes](#attributes)
	* [`[[nodiscard]]`](#nodiscard)
	* [`[[trivially_relocatable]]`](#triviallyrelocatable)
* [Exceptions](#exceptions)
	* [Exceptions in destructors](#exceptions-in-destructors)
* [Functions](#functions)
	* [Argument-dependent lookup](#argument-dependent-lookup)
* [Keywords](#keywords)
	* [`const` and `mutable`](const-and-mutable)
	* [`friend`](#friend)
* [Memory access](#memory-access)
	* [Strict aliasing rule](#strict-aliasing-rule)
* [Standards](#standards)
	* [C++20](#c20)
* [Structured bindings](#structured-bindings)
* [Templates](#templates)
* [Tricks](#tricks)
	* [Accessing private and protected members](#accessing-private-and-protected-members)
* [Types](#types)
	* [Floating-point types](#floating-point-types)
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

### Exceptions in destructors

:link:

* A.Krzemie&nacute;ski. [*Destructors that throw*](https://akrzemi1.wordpress.com/2011/09/21/destructors-that-throw/) (2011)
* B.Kolpackov. [*Throwing destructors*](https://www.kolpackov.net/projects/c++/eh/dtor-1.xhtml) (2004)

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

## Memory access

### Strict aliasing rule

:memo:

* See also: [*`std::launder`* &ndash; The standard library](std_library.md#stdlaunder)

:link:

* [*What is the strict aliasing rule?*](https://stackoverflow.com/questions/98650/what-is-the-strict-aliasing-rule) &ndash; Stack Overflow

---

## Standards

###	C++20

:movie_camera:

* A.Meredith. [*How C++20 can simplify `std::tuple`*](https://www.youtube.com/watch?v=SvxBvSK4i4k) &ndash; ACCU (2019)

---

## Structured bindings

:link:

* [*Structured bindings and tuple of references*](https://stackoverflow.com/questions/49628401/structured-bindings-and-tuple-of-references) &ndash; Stack Overflow

## Templates

See [Templates](templates.md).

---

## Tricks

### Accessing private and protected members

:link:

* [*Accessing private members*](https://stackoverflow.com/questions/726096/accessing-private-members) &ndash; Stack Overflow
* J.Schaub. [*Access to private members. That's easy!*](https://bloglitb.blogspot.com/2010/07/access-to-private-members-thats-easy.html) &ndash; litb's Blog

---

## Types

### Floating-point types

:memo:

* See also [*Floating-point numbers* &ndash; Numeric data structures and algorithms](../data_structures_and_algorithms/numeric.md).

:link:

* D.Howard. [*Byte swapping floating point types*](https://web.archive.org/web/20100125081223/http://www.dmh2000.com/cpp/dswap.shtml)

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

