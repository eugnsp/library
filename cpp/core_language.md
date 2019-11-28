# Core language <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
	- [`main()`](#main)
- [ABI](#abi)
	- [Itanium C++ ABI](#itanium-c-abi)
- [Attributes](#attributes)
	- [`[[nodiscard]]`](#nodiscard)
	- [`[[trivially_relocatable]]`](#trivially_relocatable)
- [Declarations](#declarations)
	- [`const` and `mutable`](#const-and-mutable)
	- [`constexpr`](#constexpr)
	- [`friend`](#friend)
		- [Friend function templates](#friend-function-templates)
		- [Hidden friends](#hidden-friends)
	- [`inline`](#inline)
	- [Storage class specifiers](#storage-class-specifiers)
- [Exceptions](#exceptions)
- [Expressions](#expressions)
	- [Operators](#operators)
	- [Order of evaluation](#order-of-evaluation)
	- [Type conversions](#type-conversions)
		- [`dynamic_cast`](#dynamic_cast)
	- [Type punning](#type-punning)
- [Functions](#functions)
	- [Argument-dependent lookup](#argument-dependent-lookup)
	- [Function wrappers](#function-wrappers)
		- [`std::function`](#stdfunction)
	- [Lambda expressions](#lambda-expressions)
- [Standards](#standards)
	- [C++17](#c17)
- [Structured bindings](#structured-bindings)
- [Tricks and subtleties](#tricks-and-subtleties)
	- [Accessing private and protected members](#accessing-private-and-protected-members)
	- [Embedding binary data](#embedding-binary-data)
- [Types](#types)
	- [Aggregate, trivial and POD types](#aggregate-trivial-and-pod-types)
	- [Floating-point types](#floating-point-types)
		- [`__float128`](#__float128)
	- [Function types](#function-types)
	- [Integral types](#integral-types)
	- [Opaque typedefs](#opaque-typedefs)
	- [References](#references)
		- [Lifetime of a temporary](#lifetime-of-a-temporary)
		- [Rvalue references and move semantics](#rvalue-references-and-move-semantics)

---

## Introduction and overview

:link:

- [*The definitive C++ book guide and list*](https://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list) &ndash; Stack Overflow

:anchor:

- [*Standard C++*](https://isocpp.org/)
- [*The C++ standards committee*](http://www.open-std.org/jtc1/sc22/wg21/)
- [*C++ standards committee papers*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/)

### `main()`

:movie_camera:

- M.Godbolt. [*The bits between the bits: How we get to `main()`*](https://www.youtube.com/watch?v=dOfucXtyEsU) &ndash; CppCon (2018)

:anchor:

- [Main function](https://en.cppreference.com/w/cpp/language/main_function) &ndash; C++ reference

---

## ABI

:link:

- [*Binary compatibility issues with C++*](https://community.kde.org/Policies/Binary_Compatibility_Issues_With_C%2B%2B) &ndash; KDE wiki
- [*ABI stability*](https://source.android.com/devices/architecture/vndk/abi-stability) &ndash; Android Open Source Project

:movie_camera:

- L.Dionne. [*The C++ ABI from the ground up*](https://www.youtube.com/watch?v=DZ93lP1I7wU) &ndash; CppCon (2019)

:anchor:

- [*The ABI generic analysis and instrumentation library*](https://sourceware.org/libabigail/)
- L.Dionne. [*Controlling the instantiation of vtables and RTTI*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1263r0.pdf) &ndash; WG21/P1263R0 (2018)

### Itanium C++ ABI

> The Itanium C++ ABI is an ABI for C++. As an ABI, it gives precise rules for implementing the language, ensuring that separately-compiled parts of a program can successfully interoperate. It is not platform-specific and can be layered portably on top of an arbitrary C ABI. It is used as the standard C++ ABI for many major operating systems on all major architectures, and is implemented in many major C++ compilers, including GCC and Clang.

:link:

- [*Itanium C++ ABI*](https://itanium-cxx-abi.github.io/cxx-abi/abi.html)

---

## Attributes

:movie_camera:

- B.Saks. [*Better code with C++ attributes*](https://www.youtube.com/watch?v=teUA5U6eYQY) &ndash; CppCon (2019)

### `[[nodiscard]]`

> This attribute encourages the compiler to issue a warning if the return value is discarded.

:memo:

- Conservative approach suggested by N.Josuttis:
	- Should be added:
		- *existing APIs*: not using the return value always is a “huge mistake”; not using the return value is a source of trouble and easily can happen;
		- *new APIs*: not using the return value is usually an error.
	- Should not be added:
		- *existing APIs*: not using the return value is a possible/common way of programming at least for some input; not using the return value makes no sense but doesn’t hurt.

:link:

- [*What's the reason for not using C++17’s `[[nodiscard]]` almost everywhere in new code?*](https://softwareengineering.stackexchange.com/questions/363169/whats-the-reason-for-not-using-c17s-nodiscard-almost-everywhere-in-new-c) &ndash; Software Engineering

:anchor:

- N.Josuttis. [*`[[nodiscard]]` in the library*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r0.pdf) &ndash; WG21/P0600R0 (2017)

### `[[trivially_relocatable]]`

> This attribute specifies that the relocation operation for an object is trivial: moving the object and then immediately destroying the original is equivalent to `memcpy`. This attribute is not yet in the standard.

See [Relocation &ndash; Memory &ndash; Optimization and hardware](optimization_and_hardware.md#relocation).

---

## Declarations

### `const` and `mutable`

:memo:

- In C++98: `const` means “logically `const`”, in C++11 `const` means “thread safe” (bitwise `const` or internally synchronized).
- In C++98: `mutable` means “not observably non-`const`”, in C++11 `mutable` means “thread safe” (bitwise `const` or internally synchronized).

:link:

- [*Const correctness*](https://isocpp.org/wiki/faq/const-correctness) &ndash; C++ FAQ
- H.Sutter. [GotW #6: *Const-correctness*](http://www.gotw.ca/gotw/006.htm) &ndash; Guru of the Week (2009)
- S.Meyers. [*Appearing and disappearing `const`s in C++*](https://aristeia.com/Papers/appearing%20and%20disappearing%20consts.pdf) (2011)
- [*Use of `const` for function parameters*](https://stackoverflow.com/questions/117293/use-of-const-for-function-parameters) &ndash; Stack Overflow
- [*C++ `const` keyword &ndash; use liberally?*](https://stackoverflow.com/questions/1554750/c-const-keyword-use-liberally) &ndash; Stack Overflow

:movie_camera:

- H.Sutter. [*You don’t know `const` and `mutable`*](https://channel9.msdn.com/posts/C-and-Beyond-2012-Herb-Sutter-You-dont-know-blank-and-blank) &ndash; C++ and Beyond (2012)

:anchor:

- [ES.28: *Use lambdas for complex initialization, especially of `const` variables*](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Res-lambda-init) &ndash; C++ Core Guidelines

### `constexpr`

:link:

- [*Why is a `constexpr` function on a reference not `constexpr`?*](https://stackoverflow.com/questions/54124899/why-is-a-constexpr-function-on-a-reference-not-constexpr) &ndash; Stack Overflow

:movie_camera:

- S.Schurr. *`constexpr`:* [*Introduction*](https://www.youtube.com/watch?v=fZjYCQ8dzTc), [*Applications*](https://www.youtube.com/watch?v=qO-9yiAOQqc) &ndash; CppCon (2015)

### `friend`

#### Friend function templates

See [*Friend function templates* &ndash; Function templates &ndash; Templates](templates.md#friend-function-templates).

#### Hidden friends

:link:

- A.Williams. [*The power of hidden friends in C++*](https://www.justsoftwaresolutions.co.uk/cplusplus/hidden-friends.html) (2019)

:anchor:

- [*Recommendations for specifying “hidden friends”*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1601r0.pdf) &ndash; WG21/P1601R0 (2019)

### `inline`

:link:

- [*One Definition Rule &ndash; multiple definition of `inline` functions*](https://stackoverflow.com/questions/39652884/one-definition-rule-multiple-definition-of-inline-functions) &ndash; Stack Overflow
- [*Does it make any sense to use `inline` keyword with templates?*](https://stackoverflow.com/questions/10535667/does-it-make-any-sense-to-use-inline-keyword-with-templates) &ndash; Stack Overflow

:anchor:

- [*`inline` specifier*](https://en.cppreference.com/w/cpp/language/inline) &ndash; C++ reference

### Storage class specifiers

:link:

- [*What is external linkage and internal linkage?*](https://stackoverflow.com/questions/1358400/what-is-external-linkage-and-internal-linkage) &ndash; Stack Overflow
- P.Goldsborough. [*Internal and external linkage in C++*](http://www.goldsborough.me/c/c++/linker/2016/03/30/19-34-25-internal_and_external_linkage_in_c++/) (2016)

:anchor:

- [*Storage class specifiers*](https://en.cppreference.com/w/cpp/language/storage_duration) &ndash; C++ reference

---

## Exceptions

:link:

- [*Exceptions*](https://en.cppreference.com/w/cpp/language/exceptions) &ndash; C++ reference
- H.Sutter. [*When and how to use exceptions*](http://www.drdobbs.com/when-and-how-to-use-exceptions/184401836) &ndash; Dr.Dobb’s Journal (2004)
- [*When should I really use `noexcept`?*](https://stackoverflow.com/questions/10787766/when-should-i-really-use-noexcept) &ndash; Stack Overflow

---

## Expressions

### Operators

:link:

- [*What are the basic rules and idioms for operator overloading?*](https://stackoverflow.com/questions/4421706/what-are-the-basic-rules-and-idioms-for-operator-overloading) &ndash; Stack Overflow

:anchor:

- [*`operator` overloading*](https://en.cppreference.com/w/cpp/language/operators) &ndash; C++ reference
- [*Canonical implementations*](https://en.cppreference.com/w/cpp/language/operators#Canonical_implementations) &ndash; C++ reference

### Order of evaluation

:link:

- [*Undefined behavior and sequence points*](https://stackoverflow.com/questions/4176328/undefined-behavior-and-sequence-points) &ndash; Stack Overflow

:anchor:

- [*Order of evaluation*](https://en.cppreference.com/w/cpp/language/eval_order) &ndash; C++ reference

### Type conversions

#### `dynamic_cast`

:movie_camera:

- A.O’Dwyer. [*`dynamic_cast` from scratch*](https://www.youtube.com/watch?v=QzJL-8WbpuU) &ndash; CppCon (2017)

:anchor:

- [*`dynamic_cast` conversion*](https://en.cppreference.com/w/cpp/language/dynamic_cast) &ndash; C++ reference

### Type punning

:memo:

- Since C++20, some of type punning can be done using `std::bit_cast`, see [*`std::bit_cast`* &ndash; The standard library and Boost](#std_library.md#stdbit_cast).

:link:

- [*Type punning*](https://en.wikipedia.org/wiki/Type_punning) &ndash; Wikipedia
- L.Torvalds. [*... What’s the **real** reason for avoiding union aliasing?*](https://lkml.org/lkml/2018/6/5/769) &ndash; Linux kernel mailing list (2018)
- S.Yaghmour. [*What is the strict aliasing rule and why do we care?*](https://gist.github.com/shafik/848ae25ee209f698763cffee272a58f8) (2018)
- M.Acton. [*Understanding strict aliasing*](https://cellperformance.beyond3d.com/articles/2006/06/understanding-strict-aliasing.html) (2006)
- [*What is the strict aliasing rule?*](https://stackoverflow.com/questions/98650/what-is-the-strict-aliasing-rule) &ndash; Stack Overflow
- [*Gcc, strict-aliasing, and casting through a union*](https://stackoverflow.com/questions/2906365/gcc-strict-aliasing-and-casting-through-a-union) &ndash; Stack Overflow
- [*Can I safely convert struct of floats into float array in C++?*](https://stackoverflow.com/questions/45898184/can-i-safely-convert-struct-of-floats-into-float-array-in-c) &ndash; Stack Overflow
- [*Reinterpret struct with members of the same type as an array in a standard compliant way*](https://stackoverflow.com/questions/41419164/reinterpret-struct-with-members-of-the-same-type-as-an-array-in-a-standard-compl) &ndash; Stack Overflow

:movie_camera:

- T.Doumler. [*(How not to do) Type punning in modern C++*](https://www.youtube.com/watch?v=_qzMpk-22cc) &ndash; CppCon (2019)

:anchor:

- [Options that control optimization: Type punning](https://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html#Type-punning) &ndash; GCC documentation

---

## Functions

### Argument-dependent lookup

:link:

- [*What is “argument-dependent lookup” (aka ADL, or “Koenig lookup”)?*](https://stackoverflow.com/questions/8111677/what-is-argument-dependent-lookup-aka-adl-or-koenig-lookup) &ndash; Stack Overflow
- A.O’Dwyer. [*What is ADL?*](https://quuxplusone.github.io/blog/2019/04/26/what-is-adl/) (2019)
- A.O’Dwyer. [*ADL insanity*](https://quuxplusone.github.io/blog/2019/04/08/adl-insanity/) (2019)
- A.O’Dwyer. [*How `hana::type<T>` “disables ADL”*](https://quuxplusone.github.io/blog/2019/04/09/adl-insanity-round-2/) (2019)
- [*Why doesn’t ADL find function templates?*](https://stackoverflow.com/questions/2953684/why-doesnt-adl-find-function-templates) &ndash; Stack Overflow

:movie:

- J.Turner. [Episode 160: *Argument dependent lookup*](https://www.youtube.com/watch?v=agS-h_eaLj8) &ndash; C++ Weekly

:anchor:

- [*Argument-dependent lookup*](https://en.cppreference.com/w/cpp/language/adl) &ndash; C++ reference
- J.Spicer. [*ADL and function templates that are not visible*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0846r0.html) &ndash; WG21/P0846R0 (2017)

### Function wrappers

#### `std::function`

:link:

- [*Move-only version of `std::function`*](https://stackoverflow.com/questions/25330716/move-only-version-of-stdfunction) &ndash; Stack Overflow
- [*How to create an `std::function` from a move-capturing lambda expression?*](https://stackoverflow.com/questions/25421346/how-to-create-an-stdfunction-from-a-move-capturing-lambda-expression) &ndash; Stack Overflow

:anchor:

- [*`std::function`*](https://en.cppreference.com/w/cpp/utility/functional/function) &ndash; C++ reference

### Lambda expressions

:link:

- R.Chen. [*Non-capturing C++ lambdas can be converted to a pointer to function, but what about the calling convention?*](https://devblogs.microsoft.com/oldnewthing/20150220-00/?p=44623) (2015)
- A.Allain. [*Lambda functions in C++11 &ndash; the definitive guide*](https://www.cprogramming.com/c++11/c++11-lambda-closures.html) (2011)
- [*What is a lambda expression in C++11?*](https://stackoverflow.com/questions/7627098/what-is-a-lambda-expression-in-c11) &ndash; Stack Overflow
- [*Why are lambda expressions not allowed in an unevaluated operands but allowed in the unevaluated portions of constant expressions?*](https://stackoverflow.com/questions/22232164/why-are-lambda-expressions-not-allowed-in-an-unevaluated-operands-but-allowed-in) &ndash; Stack Overflow
- [*Can we get the type of a lambda argument?*](https://stackoverflow.com/questions/6512019/can-we-get-the-type-of-a-lambda-argument) &ndash; Stack Overflow

:movie_camera:

- A.O’Dwyer. [*Back to basics: Lambdas from scratch*](https://www.youtube.com/watch?v=3jCOwajNch0) &ndash; CppCon (2019)

:anchor:

- L.Dionne, H.Tong. [*Wording for lambdas in unevaluated contexts*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0315r4.pdf) &ndash; WG21/P0315R4 (2017)

---

## Standards

### C++17

:movie_camera:

- A.Meredith. *C++17 in breadth (not depth).* [Part I](https://www.youtube.com/watch?v=22jIHfvelZk), [Part II](https://www.youtube.com/watch?v=-rIixnNJM4k) &ndash; CppCon (2016)

:anchor:

- [*C++17 compiler support*](https://en.cppreference.com/w/cpp/compiler_support#cpp17) &ndash; C++ reference

###	C++2a

:movie_camera:

- A.Meredith. [*How C++20 can simplify `std::tuple`*](https://www.youtube.com/watch?v=SvxBvSK4i4k) &ndash; ACCU (2019)

:anchor:

- [*C++2a compiler support*](https://en.cppreference.com/w/cpp/compiler_support#cpp2a) &ndash; C++ reference

---

## Structured bindings

:link:

- [*Structured bindings and tuple of references*](https://stackoverflow.com/questions/49628401/structured-bindings-and-tuple-of-references) &ndash; Stack Overflow

---

## Tricks and subtleties

:link:

- [*Hidden features of C++?*](https://stackoverflow.com/questions/75538/hidden-features-of-c) &ndash; Stack Overflow
- [*Why compilers test the least significant bit in an address?*](https://stackoverflow.com/questions/53421279/why-compilers-test-the-least-significant-bit-in-an-address) &ndash; Stack Overflow
- [*Why does the size of class in C++ depend on the `public`/`private` status of data members?*](https://stackoverflow.com/questions/58960303/why-does-the-size-of-class-in-c-depend-on-the-public-private-status-of-data-me#58960555) &ndash; Stack Overflow

:movie_camera:

- M.Kruse. [*`v.~uint32_t();`*](https://www.youtube.com/watch?v=Pf8gDb-j4wQ) &ndash; CppCon (2019)

### Accessing private and protected members

:link:

- [*Accessing private members*](https://stackoverflow.com/questions/726096/accessing-private-members) &ndash; Stack Overflow
- J.Schaub. [*Access to private members. That’s easy!*](https://bloglitb.blogspot.com/2010/07/access-to-private-members-thats-easy.html) (2010))

### Embedding binary data

:link:

- D.Weiler. [incbin &ndash; Include binary files in C/C++](https://github.com/graphitemaster/incbin)
- H.Landau. [*Embedding of binary data into programs*](https://www.devever.net/~hl/incbin)
- [*Embedding resources in executable using GCC*](https://stackoverflow.com/questions/4158900/embedding-resources-in-executable-using-gcc) &ndash; Stack Overflow

:anchor:

- J. Meneide. [`std::embed`](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p1040r0.html) &ndash; WG21/P1040R0 (2018)

---

## Types

### Aggregate, trivial and POD types

:link:

- [*Trivial, standard-layout, POD, and literal types*](https://docs.microsoft.com/en-us/cpp/cpp/trivial-standard-layout-and-pod-types?view=vs-2019) &ndash; Visual C++ language reference (2018)
- [*What are aggregates and PODs and how/why are they special?*](https://stackoverflow.com/questions/4178175/what-are-aggregates-and-pods-and-how-why-are-they-special) &ndash; Stack Overflow
- [*Trivial vs. standard layout vs. POD*](https://stackoverflow.com/questions/6496545/trivial-vs-standard-layout-vs-pod) &ndash; Stack Overflow

### Floating-point types

See also [*Floating-point arithmetic* &ndash; Numeric data structures and algorithms](../data_structures_and_algorithms/numeric.md#floating-point-arithmetic).

:link:

- D.Howard. [*Byte swapping floating point types*](https://web.archive.org/web/20100125081223/http://www.dmh2000.com/cpp/dswap.shtml) (2007)

#### `__float128`

:link:

- [*`long double` (GCC specific) and `__float128`*](https://stackoverflow.com/questions/13516476/long-double-gcc-specific-and-float128) &ndash; Stack Overflow
- [*How to use GCC 4.6.0 libquadmath and `__float128` on x86 and x86_64*](https://stackoverflow.com/questions/6457385/how-to-use-gcc-4-6-0-libquadmath-and-float128-on-x86-and-x86-64) &ndash; Stack Overflow

:anchor:

- [*Additional floating types*](https://gcc.gnu.org/onlinedocs/gcc/Floating-Types.html) &ndash; GCC documentation

### Function types

:anchor:

- A.Meredith. [*Abominable function types*](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2015/p0172r0.html) &ndash; WG21/P0172R0 (2015)

### Integral types

:link:

- W.Dietz et al. [*Understanding integer overflow in C/C++*](https://www.cs.utah.edu/~regehr/papers/overflow12.pdf) &ndash; Proc. ICSE (2012)
- [*Rule 04. Integers*](https://wiki.sei.cmu.edu/confluence/pages/viewpage.action?pageId=87152052) &ndash; SEI CERT C coding standard
- [*Why does integer overflow on x86 with GCC cause an infinite loop?*](https://stackoverflow.com/questions/7682477/why-does-integer-overflow-on-x86-with-gcc-cause-an-infinite-loop) &ndash; Stack Overflow
- [*Why does this loop produce “warning: iteration 3u invokes undefined behavior” and output more than 4 lines?*](https://stackoverflow.com/questions/24296571/why-does-this-loop-produce-warning-iteration-3u-invokes-undefined-behavior-an) &ndash; Stack Overflow

:movie_camera:

- J.Bastien. [*Signed integers are two’s complement*](https://www.youtube.com/watch?v=JhUxIVf1qok) &ndash; CppCon (2018)

:anchor:

- J.Bastien. [*Signed integers are two’s complement*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0907r1.html) &ndash; WG21/P0907R1 (2018)

### Opaque typedefs

> An opaque type is a new type that is distinct from and distinguishable from its underlying type, yet retaining layout compatibility with its underlying type. The intent is to allow programmer control (1) over substitutability between an opaque alias and its underlying type, and (2) over overloading based on any parameter whose type is or involves an opaque alias.

:memo:

- > Nobody seemed to know, so I wrote a mail to the author, Walter E. Brown, and asked him. He told me that Bjarne doesn’t like that feature (anymore), so it is very unlikely that it will come anytime soon. Apparently C++ won’t get strong typedefs as core language feature. [[J.M&uuml;ller]](https://foonathan.net/blog/2016/10/19/strong-typedefs.html)
- See [*Opaque typedefs* &ndash; Patterns and idioms](patterns_and_idioms.md#opaque-typedefs) for implementations at the library level.

:anchor:

- W.E.Brown. [*Toward opaque typedefs for C++1Y, v2*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3741.pdf) &ndash; WG21/N3741 (2013)

### References

:link:

- [*Is null reference possible?*](https://stackoverflow.com/questions/4364536/is-null-reference-possible) &ndash; Stack Overflow

#### Lifetime of a temporary

:link:

- [*Does a `const` reference class member prolong the life of a temporary?*](https://stackoverflow.com/questions/2784262/does-a-const-reference-class-member-prolong-the-life-of-a-temporary) &ndash; Stack Overflow

:anchor:

- [*Lifetime of a temporary*](https://en.cppreference.com/w/cpp/language/reference_initialization#Lifetime_of_a_temporary) &ndash; C++ reference

#### Rvalue references and move semantics

:link:

- H.E.Hinnant et al. [*A brief introduction to rvalue references*](https://www.artima.com/cppsource/rvalue.html) (2008)
- T.Becker. [*C++ rvalue references explained*](http://thbecker.net/articles/rvalue_references/section_01.html) (2013)
- [*Rvalue reference declarator: `&&`*](https://docs.microsoft.com/en-us/cpp/cpp/rvalue-reference-declarator-amp-amp) &ndash; Microsoft Visual C++ (2016)
- S.Meyers. [*Universal references in C++11*](https://isocpp.org/blog/2012/11/universal-references-in-c11-scott-meyers) &ndash; [Overload **111**](https://accu.org/index.php/journals/c314/), 8 (2012)
- [*What is move semantics?*](https://stackoverflow.com/questions/3106110/what-is-move-semantics) &ndash; Stack Overflow
- [*Rvalues, lvalues and formal definitions*](https://stackoverflow.com/questions/56716647/rvalues-lvalues-and-formal-definitions) &ndash; Stack Overflow
- [*Pass by value vs pass by rvalue reference*](https://stackoverflow.com/questions/37935393/pass-by-value-vs-pass-by-rvalue-reference) &ndash; Stack Overflow
- [*Advantages of using `forward`*](https://stackoverflow.com/questions/3582001/advantages-of-using-forward) &ndash; Stack Overflow

:movie_camera:

- N.Josuttis. [*The nightmare of move semantics for trivial classes*](https://www.youtube.com/watch?v=PNRju6_yn3o) &ndash; CppCon (2017)

<!-- P1839R0 -->

<!-- https://stackoverflow.com/questions/1613341/what-do-the-following-phrases-mean-in-c-zero-default-and-value-initializat

https://stackoverflow.com/questions/37618213/when-is-a-private-constructor-not-a-private-constructor
-->


<!-- https://medium.com/@barryrevzin/value-categories-in-c-17-f56ae54bccbe
http://www.stroustrup.com/terminology.pdf
https://stackoverflow.com/questions/20717180/in-c-what-categories-lvalue-rvalue-xvalue-etc-can-expressions-that-prod
-->
