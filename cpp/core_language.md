# Core language <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
- [ABI and implementation](#abi-and-implementation)
	- [Itanium C++ ABI](#itanium-c-abi)
	- [Inheritance](#inheritance)
- [Attributes](#attributes)
	- [`[[likely]]` / `[[unlikely]]`](#likely--unlikely)
	- [`[[nodiscard]]`](#nodiscard)
	- [`[[noreturn]]`](#noreturn)
	- [`[[trivially_relocatable]]`](#trivially_relocatable)
- [Declarations](#declarations)
	- [Alignment](#alignment)
	- [`const` and `mutable`](#const-and-mutable)
	- [`constexpr`](#constexpr)
	- [Elaborated type specifier](#elaborated-type-specifier)
	- [`friend`](#friend)
		- [Friend function templates](#friend-function-templates)
		- [Hidden friends](#hidden-friends)
	- [`inline`](#inline)
	- [`static`](#static)
	- [Flexible array member](#flexible-array-member)
	- [Most vexing parse](#most-vexing-parse)
	- [Namespaces](#namespaces)
	- [Storage class specifiers](#storage-class-specifiers)
	- [Structured binding](#structured-binding)
- [Initialization](#initialization)
- [Dynamic memory](#dynamic-memory)
	- [Alignment](#alignment-1)
- [Exceptions](#exceptions)
- [Expressions](#expressions)
	- [Compound literals](#compound-literals)
	- [Order of evaluation](#order-of-evaluation)
	- [Type conversions](#type-conversions)
		- [`dynamic_cast`](#dynamic_cast)
	- [Type punning](#type-punning)
- [Functions and functional objects](#functions-and-functional-objects)
	- [Overload resolution](#overload-resolution)
	- [Argument-dependent lookup](#argument-dependent-lookup)
	- [Function wrappers](#function-wrappers)
		- [`std::function`](#stdfunction)
	- [Lambda expressions](#lambda-expressions)
		- [Recursive lambdas](#recursive-lambdas)
	- [Member functions](#member-functions)
		- [Member function poiners](#member-function-poiners)
	- [`main()`](#main)
- [Operators](#operators)
	- [Comparisons](#comparisons)
		- [Pointer comparisons](#pointer-comparisons)
	- [`sizeof`](#sizeof)
- [Tricks and subtleties](#tricks-and-subtleties)
	- [Accessing private and protected members](#accessing-private-and-protected-members)
	- [Embedding binary data](#embedding-binary-data)
- [Types](#types)
	- [Aggregate, trivial and POD types](#aggregate-trivial-and-pod-types)
	- [Floating-point types](#floating-point-types)
		- [`__float128`](#__float128)
	- [Integral types](#integral-types)
	- [Class types](#class-types)
		- [Inheritance](#inheritance-1)
	- [Function types](#function-types)
	- [References](#references)
		- [Lifetime of a temporary](#lifetime-of-a-temporary)
		- [Rvalue references and move semantics](#rvalue-references-and-move-semantics)
	- [Opaque typedefs](#opaque-typedefs)
- [Standards](#standards)
	- [C++17](#c17)
- [C vs C++](#c-vs-c)

---

## Introduction and overview

:grey_question:

- [*The definitive C++ book guide and list*](https://stackoverflow.com/q/388242) – Stack Overflow

:anchor:

- [*Standard C++*](https://isocpp.org/)
- [*The C++ standards committee*](http://www.open-std.org/jtc1/sc22/wg21/)
- [*C++ standards committee papers*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/)
- [*C++ standard core language closed issues*](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html)
- [*C++ standard draft sources*](https://github.com/cplusplus/draft)

---

## ABI and implementation

:link:

- [*Binary compatibility issues with C++*](https://community.kde.org/Policies/Binary_Compatibility_Issues_With_C%2B%2B) – KDE wiki
- [*ABI stability*](https://source.android.com/devices/architecture/vndk/abi-stability) – Android Open Source Project

:movie_camera:

- L.Dionne. [*The C++ ABI from the ground up*](https://www.youtube.com/watch?v=DZ93lP1I7wU) – CppCon (2019)

:anchor:

- [*The ABI generic analysis and instrumentation library*](https://sourceware.org/libabigail/)
- L.Dionne. *Controlling the instantiation of vtables and RTTI.* [P1263R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1263r0.pdf) (2018)

### Itanium C++ ABI

> The Itanium C++ ABI is an ABI for C++. As an ABI, it gives precise rules for implementing the language, ensuring that separately-compiled parts of a program can successfully interoperate. It is not platform-specific and can be layered portably on top of an arbitrary C ABI. It is used as the standard C++ ABI for many major operating systems on all major architectures, and is implemented in many major C++ compilers, including GCC and Clang.

:link:

- [*Itanium C++ ABI*](https://itanium-cxx-abi.github.io/cxx-abi/abi.html)

### Inheritance

:grey_question:

- [*Virtual table layout of multiple inheritance*](https://stackoverflow.com/q/15921372) – Stack Overflow

:book:

- Ch. 1: *Inheritance*, Sec.: *Inheritance implementation*; Ch. 2: *Multiple inheritance*, Sec.: *Multiple inheritance implementation* – N.Llopis. *C++ for game programmers* – Charles River Media (2003)

---

## Attributes

:movie_camera:

- B.Saks. [*Better code with C++ attributes*](https://www.youtube.com/watch?v=teUA5U6eYQY) – CppCon (2019)

### `[[likely]]` / `[[unlikely]]`

> These attributes allow the compiler to optimize for the case where paths of execution are more or less likely than any alternative path of execution.

:grey_question:

- [*How to use C++20’s `likely`/`unlikely` attributes in `if-else` statement*](https://stackoverflow.com/q/51797959) – Stack Overflow

:anchor:

- [*C++ attribute: `likely`, `unlikely`*](https://en.cppreference.com/w/cpp/language/attributes/likely) – C++ reference

### `[[nodiscard]]`

> This attribute encourages the compiler to issue a warning if the return value is discarded. Conservative approach suggested by N.Josuttis:
>
> - Should be added:
>	* *existing APIs*: not using the return value always is a “huge mistake”; not using the return value is a source of trouble and easily can happen;
>	* *new APIs*: not using the return value is usually an error.
> - Should not be added:
>   * *existing APIs*: not using the return value is a possible/common way of programming at least for some input; not using the return value makes no sense but doesn’t hurt.

:link:

- [*What’s the reason for not using C++17’s `[[nodiscard]]` almost everywhere in new code?*](https://softwareengineering.stackexchange.com/questions/363169/whats-the-reason-for-not-using-c17s-nodiscard-almost-everywhere-in-new-c) – Software Engineering

:anchor:

- N.Josuttis. *`[[nodiscard]]` in the library.* [P0600R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r0.pdf) (2017)

### `[[noreturn]]`

> This attribute indicates that the function does not return.

:grey_question:

- [*What is the point of `[[noreturn]]`?*](https://stackoverflow.com/q/10538291) – Stack Overflow

:anchor:

- [*C++ attribute: `noreturn`*](https://en.cppreference.com/w/cpp/language/attributes/noreturn) – C++ reference

### `[[trivially_relocatable]]`

> This attribute specifies that the relocation operation for an object is trivial: moving the object and then immediately destroying the original is equivalent to `memcpy`. This attribute is not yet in the standard.

See [*Relocation* – Memory – Optimization and hardware](optimization_and_hardware.md#relocation).

---

## Declarations

:link:

- D.Anderson. [*The “clockwise/spiral rule”*](http://c-faq.com/decl/spiral.anderson.html)

:movie_camera:

- H.Hinnant. [*How to initialize `x` from expression `y`*](https://www.youtube.com/watch?v=hobFOAehwio) – Meeting C++ (2019)

### Alignment

:link:

- E.S.Raymond. [*The lost art of structure packing*](http://www.catb.org/esr/structure-packing/)

:grey_question:

- [*Structure padding and packing*](https://stackoverflow.com/q/4306186) – Stack Overflow

:anchor:

- [*`alignas` specifier*](https://en.cppreference.com/w/cpp/language/alignas) – C++ reference

### `const` and `mutable`

:memo:

- In C++98: `const` means “logically `const`”, in C++11 `const` means “thread safe” (bitwise `const` or internally synchronized).
- In C++98: `mutable` means “not observably non-`const`”, in C++11 `mutable` means “thread safe” (bitwise `const` or internally synchronized).

:link:

- [*Const correctness*](https://isocpp.org/wiki/faq/const-correctness) – C++ FAQ
- H.Sutter. [GotW #6: *Const-correctness*](http://www.gotw.ca/gotw/006.htm)
- S.Meyers. [*Appearing and disappearing `const`s in C++*](https://aristeia.com/Papers/appearing%20and%20disappearing%20consts.pdf) (2011)

:grey_question:

- [*Use of `const` for function parameters*](https://stackoverflow.com/q/117293) – Stack Overflow
- [*C++ `const` keyword – use liberally?*](https://stackoverflow.com/q/1554750) – Stack Overflow

:movie_camera:

- H.Sutter. [*You don’t know `const` and `mutable`*](https://channel9.msdn.com/posts/C-and-Beyond-2012-Herb-Sutter-You-dont-know-blank-and-blank) – C++ and Beyond (2012)

:anchor:

- [ES.28: *Use lambdas for complex initialization, especially of `const` variables*](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Res-lambda-init) – C++ Core Guidelines

### `constexpr`

:grey_question:

- [*Why is a `constexpr` function on a reference not `constexpr`?*](https://stackoverflow.com/q/54124899) – Stack Overflow
- [*Why do we need to mark functions as `constexpr`?*](https://stackoverflow.com/q/14472359) – Stack Overflow

:movie_camera:

- S.Schurr. *`constexpr`:* [*Introduction*](https://www.youtube.com/watch?v=fZjYCQ8dzTc), [*Applications*](https://www.youtube.com/watch?v=qO-9yiAOQqc) – CppCon (2015)

### Elaborated type specifier

:anchor:

- [*Elaborated type specifier*](https://en.cppreference.com/w/cpp/language/elaborated_type_specifier) – C++ reference

### `friend`

#### Friend function templates

See [*Friend function templates* – Function templates – Templates](templates.md#friend-function-templates).

#### Hidden friends

:link:

- A.Williams. [*The power of hidden friends in C++*](https://www.justsoftwaresolutions.co.uk/cplusplus/hidden-friends.html) (2019)

:anchor:

- [*Recommendations for specifying “hidden friends”*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1601r0.pdf) – WG21/P1601R0 (2019)

### `inline`

:grey_question:

- [*One Definition Rule – multiple definition of `inline` functions*](https://stackoverflow.com/q/39652884) – Stack Overflow
- [*Does it make any sense to use `inline` keyword with templates?*](https://stackoverflow.com/q/10535667) – Stack Overflow

:anchor:

- [*`inline` specifier*](https://en.cppreference.com/w/cpp/language/inline) – C++ reference

### `static`

:grey_question:

- [*Static variables in an inlined function*](https://stackoverflow.com/q/185624) – Stack Overflow

### Flexible array member

:link:

- [*Flexible array member*](https://en.wikipedia.org/wiki/Flexible_array_member) – Wikipedia

:grey_question:

- [*Are flexible array members valid in C++?*](https://stackoverflow.com/q/4412749) – Stack Overflow
- [*Is using flexible array members in C bad practice?*](https://stackoverflow.com/q/246977) – Stack Overflow

### Most vexing parse

> There is an ambiguity in the grammar involving *expression-statements* and *declarations*: An *expression-statement* with a function-style explicit type conversion as its leftmost subexpression can be indistinguishable from a *declaration* where the first *declarator* starts with a `(`. In those cases the *statement* is a *declaration*.

:link:

- H.Sutter. [GotW #75: *Istream initialization?*](http://www.gotw.ca/gotw/006.htm)
- D.Kalev. [*Overcoming the “most vexing parse” problem*](http://www.devx.com/cplus/10MinuteSolution/43032/0/page/2) (2009)

:book:

- Item 6: *Be alert for C++’s most vexing parse* – S.Meyers. *Effective STL: 50 Specific ways to improve your use of the standard template library* – [Addison-Wesley Professional](https://www.informit.com/store/effective-stl-50-specific-ways-to-improve-your-use-9780201749625) (2001)

:anchor:

- [[stmt.ambig] *Statements: Ambiguity resolution*](http://eel.is/c++draft/stmt.ambig) – C++ standard draft

### Namespaces

:grey_question:

- [*Wherefore inline unnamed namespaces?*](https://stackoverflow.com/q/20208591) – Stack Overflow

:anchor:

- [*Namespaces*](https://en.cppreference.com/w/cpp/language/namespace) – C++ reference

### Storage class specifiers

:link:

- [*What is external linkage and internal linkage?*](https://stackoverflow.com/q/1358400) – Stack Overflow
- P.Goldsborough. [*Internal and external linkage in C++*](http://www.goldsborough.me/c/c++/linker/2016/03/30/19-34-25-internal_and_external_linkage_in_c++/) (2016)

:anchor:

- [*Storage class specifiers*](https://en.cppreference.com/w/cpp/language/storage_duration) – C++ reference

### Structured binding

:link:

- S.Brand. [*Adding C++17 structured bindings support to your classes*](https://blog.tartanllama.xyz/structured-bindings/) (2016)

:grey_question:

- [*Structured bindings and tuple of references*](https://stackoverflow.com/q/49628401) – Stack Overflow

:anchor:

- [*Structured binding declaration*](https://en.cppreference.com/w/cpp/language/structured_binding) – C++ reference
- B.Revzin, J.Wakely. *Structured bindings can introduce a pack.* [P1061R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1061r1.html) (2019)
- N.Lesser. *Extending structured bindings to be more like variable declarations.* [P1091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1091r3.html) (2019)

---

## Initialization

:link:

- C.McClure. [*C++ object initialization*](https://daemons.net/programming/c++/initialization.html)
- B.Filipek. [*What happens to your static variables at the start of the program?*](https://www.bfilipek.com/2018/02/staticvars.html) (2018)
- S.Brand. [*Initialization in C++ is bonkers*](https://accu.org/index.php/journals/2379) – [Overload **139**](https://accu.org/index.php/journals/c374/), 9 (2017)
- E.Martin. [*Static initializers*](http://neugierig.org/software/chromium/notes/2011/08/static-initializers.html) (2011)
- A.Demin. [*The difference between `new T()` and `new T`* (in Russian)](http://demin.ws/blog/russian/2009/02/20/difference-between-new-and-new-with-brackets/) (2009)

:anchor:

- [*Initialization*](https://en.cppreference.com/w/cpp/language/initialization) – C++ reference

---

## Dynamic memory

:link:

- [R.10: *Avoid `malloc()` and `free()`*](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Rr-mallocfree) – C++ Core Guidelines
- [R.11: *Avoid calling `new` and `delete` explicitly*](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Rr-newdelete) – C++ Core Guidelines
- [*How do compilers use “over-allocation” to remember the number of elements in an allocated array?*](https://isocpp.org/wiki/faq/compiler-dependencies#num-elems-in-new-array-overalloc) – C++ FAQ
- [*How do compilers use an “associative array” to remember the number of elements in an allocated array?*](https://isocpp.org/wiki/faq/compiler-dependencies#num-elems-in-new-array-assocarray) – C++ FAQ

:grey_question:

- [*Treating memory returned by operator `new(sizeof(T) * N)` as an array*](https://stackoverflow.com/q/53451770/1625187) – Stack Overflow
- [*Difference between `new` and `operator new`?*](https://stackoverflow.com/q/1885849) – Stack Overflow

:book:

- Sec. 19.2.5: *Allocation and deallocation* – B.Stroustrup. [*The C++ programming language*](http://www.stroustrup.com/4th.html) – [Addison-Wesley Professional](https://www.pearson.com/us/higher-education/program/Stroustrup-C-Programming-Language-The-4th-Edition/PGM326200.html) (2013)
- Item 8: *Understand the different meanings of `new` and `delete`* – S.Meyers. *More effective C++: 35 new ways to improve your programs and designs* – [*Addison-Wesley Professional*](https://www.informit.com/store/more-effective-c-plus-plus-35-new-ways-to-improve-your-9780201633719) (1996)
- Ch. 10: *Memory management* – B.Stroustrup. [*The design and evolution of C++*](http://www.stroustrup.com/dne.html) – [Addison-Wesley Professional](https://www.pearson.com/us/higher-education/program/Stroustrup-Design-and-Evolution-of-C-The/PGM287667.html) (1994)

:anchor:

- [*Low level memory management*](https://en.cppreference.com/w/cpp/memory/new) – C++ reference

### Alignment

:link:

- B.Filipek. [*New `new()`: The C++17’s alignment parameter for `operator new()`*](https://www.bfilipek.com/2019/08/newnew-align.html) (2019)

:anchor:

- C.Nelson. *Dynamic memory allocation for over-aligned data.* [P0035R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html) (2016)

---

## Exceptions

See [*Exceptions* – Patterns, idioms, and design principles](patterns_and_idioms.md#exceptions).

---

## Expressions

### Compound literals

:link:

- R.Meyers. [*The new C: Compound literals*](https://www.drdobbs.com/the-new-c-compound-literals/184401404) – Dr.Dobb’s Journal (2001)

:grey_question:

- [*Are compound literals standard C++?*](https://stackoverflow.com/q/28116467) – Stack Overflow

:anchor:

[*Compound literals*](https://en.cppreference.com/w/c/language/compound_literal) – C++ reference

### Order of evaluation

:grey_question:

- [*Undefined behavior and sequence points*](https://stackoverflow.com/q/4176328) – Stack Overflow

:anchor:

- [*Order of evaluation*](https://en.cppreference.com/w/cpp/language/eval_order) – C++ reference

### Type conversions

:book:

- Item 2: *Prefer C++-style casts* – S.Meyers. *More effective C++: 35 new ways to improve your programs and designs* – [*Addison-Wesley Professional*](https://www.informit.com/store/more-effective-c-plus-plus-35-new-ways-to-improve-your-9780201633719) (1996)

#### `dynamic_cast`

:movie_camera:

- A.O’Dwyer. [*`dynamic_cast` from scratch*](https://www.youtube.com/watch?v=QzJL-8WbpuU) – CppCon (2017)

:anchor:

- [*`dynamic_cast` conversion*](https://en.cppreference.com/w/cpp/language/dynamic_cast) – C++ reference

### Type punning

:memo:

- Since C++20, some of type punning can be done using `std::bit_cast`, see [*`std::bit_cast`* – The standard library and Boost](#std_library.md#stdbit_cast).

:link:

- [*Type punning*](https://en.wikipedia.org/wiki/Type_punning) – Wikipedia
- L.Torvalds. [*... What’s the **real** reason for avoiding union aliasing?*](https://lkml.org/lkml/2018/6/5/769) – Linux kernel mailing list (2018)
- S.Yaghmour. [*What is the strict aliasing rule and why do we care?*](https://gist.github.com/shafik/848ae25ee209f698763cffee272a58f8) (2018)
- M.Acton. [*Understanding strict aliasing*](https://cellperformance.beyond3d.com/articles/2006/06/understanding-strict-aliasing.html) (2006)

:grey_question:

- [*What is the strict aliasing rule?*](https://stackoverflow.com/q/98650) – Stack Overflow
- [*Gcc, strict-aliasing, and casting through a union*](https://stackoverflow.com/q/2906365) – Stack Overflow
- [*Can I safely convert struct of floats into float array in C++?*](https://stackoverflow.com/q/45898184) – Stack Overflow
- [*Reinterpret struct with members of the same type as an array in a standard compliant way*](https://stackoverflow.com/q/41419164) – Stack Overflow

:movie_camera:

- T.Doumler. [*(How not to do) Type punning in modern C++*](https://www.youtube.com/watch?v=_qzMpk-22cc) – CppCon (2019)

:anchor:

- [Options that control optimization: Type punning](https://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html#Type-punning) – GCC documentation

---

## Functions and functional objects

### Overload resolution

:link:

- [*Overload resolution between object, rvalue reference, const reference*](https://stackoverflow.com/q/17961719) – Stack Overflow

### Argument-dependent lookup

:link:

- [*What is “argument-dependent lookup” (aka ADL, or “Koenig lookup”)?*](https://stackoverflow.com/q/8111677) – Stack Overflow
- A.O’Dwyer. [*What is ADL?*](https://quuxplusone.github.io/blog/2019/04/26/what-is-adl/) (2019)
- A.O’Dwyer. [*ADL insanity*](https://quuxplusone.github.io/blog/2019/04/08/adl-insanity/) (2019)
- A.O’Dwyer. [*How `hana::type<T>` “disables ADL”*](https://quuxplusone.github.io/blog/2019/04/09/adl-insanity-round-2/) (2019)

:grey_question:

- [*Why doesn’t ADL find function templates?*](https://stackoverflow.com/q/2953684) – Stack Overflow

:movie_camera:

- J.Turner. [Episode 160: *Argument dependent lookup*](https://www.youtube.com/watch?v=agS-h_eaLj8) – C++ Weekly

:anchor:

- [*Argument-dependent lookup*](https://en.cppreference.com/w/cpp/language/adl) – C++ reference
- J.Spicer. *ADL and function templates that are not visible.* [P0846R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0846r0.html) (2017)

### Function wrappers

#### `std::function`

:grey_question:

- [*Move-only version of `std::function`*](https://stackoverflow.com/q/25330716) – Stack Overflow
- [*How to create an `std::function` from a move-capturing lambda expression?*](https://stackoverflow.com/q/25421346) – Stack Overflow

:anchor:

- [*`std::function`*](https://en.cppreference.com/w/cpp/utility/functional/function) – C++ reference

### Lambda expressions

:link:

- R.Chen. [*Non-capturing C++ lambdas can be converted to a pointer to function, but what about the calling convention?*](https://devblogs.microsoft.com/oldnewthing/20150220-00/?p=44623) (2015)
- A.Allain. [*Lambda functions in C++11 – the definitive guide*](https://www.cprogramming.com/c++11/c++11-lambda-closures.html) (2011)

:grey_question:

- [*What is a lambda expression in C++11?*](https://stackoverflow.com/q/7627098) – Stack Overflow
- [*Why are lambda expressions not allowed in an unevaluated operands but allowed in the unevaluated portions of constant expressions?*](https://stackoverflow.com/q/22232164) – Stack Overflow
- [*Can we get the type of a lambda argument?*](https://stackoverflow.com/q/6512019) – Stack Overflow

:movie_camera:

- A.O’Dwyer. [*Back to basics: Lambdas from scratch*](https://www.youtube.com/watch?v=3jCOwajNch0) – CppCon (2019)

:anchor:

- L.Dionne, H.Tong. *Wording for lambdas in unevaluated contexts.* [P0315R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0315r4.pdf) (2017)

#### Recursive lambdas

:link:

- P.Melendez. [*Recursive lambdas in C++(14)*](http://pedromelendez.com/blog/2015/07/16/recursive-lambdas-in-c14/) (2015)

:grey_question:

- [*Recursive lambda functions in C++11*](https://stackoverflow.com/q/2067988) – Stack Overflow

### Member functions

#### Member function poiners

:link:

- V.Lazarenko. [*Why C++ member function pointers are 16 bytes wide*](http://lazarenko.me/wide-pointers/) (2013)
- R.Chen. [*Pointers to member functions are very strange animals*](https://devblogs.microsoft.com/oldnewthing/?p=40713) (2004)

:anchor:

- [*Pointers to member functions*](https://isocpp.org/wiki/faq/pointers-to-members) – C++ FAQ

### `main()`

:link:

- E.Bendersky. [*How statically linked programs run on Linux*](https://eli.thegreenplace.net/2012/08/13/how-statically-linked-programs-run-on-linux) (2012)

:movie_camera:

- M.Godbolt. [*The bits between the bits: How we get to `main()`*](https://www.youtube.com/watch?v=dOfucXtyEsU) – CppCon (2018)

:anchor:

- [Main function](https://en.cppreference.com/w/cpp/language/main_function) – C++ reference

---

## Operators

:grey_question:

- [*What are the basic rules and idioms for operator overloading?*](https://stackoverflow.com/q/4421706) – Stack Overflow

:anchor:

- [*`operator` overloading*](https://en.cppreference.com/w/cpp/language/operators) – C++ reference
- [*Canonical implementations*](https://en.cppreference.com/w/cpp/language/operators#Canonical_implementations) – C++ reference

### Comparisons

:link:

- B.Revzin. [*Implementing the spaceship operator for `optional`*](https://accu.org/index.php/journals/2563) – [Overload **147**](https://accu.org/index.php/journals/c391/), 10 (2018)

:anchor:

- [*Comparison operators*](https://en.cppreference.com/w/cpp/language/operator_comparison) – C++ reference
- [*Default comparisons*](https://en.cppreference.com/w/cpp/language/default_comparisons) – C++ reference

#### Pointer comparisons

:link:

- A.O’Dwyer. [*Pointer comparisons with `std::less<void>`: a horror story*](https://quuxplusone.github.io/blog/2019/01/20/std-less-nightmare/) (2019)
- K.Walfridsson. [*C pointers are not hardware pointers*](https://kristerw.blogspot.com/2016/03/c-pointers-are-not-hardware-pointers.html) (2016)

:anchor:

- [*Pointer comparison operators*](https://en.cppreference.com/w/cpp/language/operator_comparison#Pointer_comparison_operators) – C++ reference

### `sizeof`

> The `sizeof` operator yields the size in bytes of the object or type. When applied to a class type, the result is the size of an object of that class plus any additional padding required to place such object in an array.

:anchor:

[*`sizeof` operator*](https://en.cppreference.com/w/cpp/language/sizeof) – C++ reference

---

## Tricks and subtleties

:grey_question:

- [*Hidden features of C++?*](https://stackoverflow.com/q/75538) – Stack Overflow
- [*Why compilers test the least significant bit in an address?*](https://stackoverflow.com/q/53421279) – Stack Overflow
- [*Why does the size of class in C++ depend on the `public`/`private` status of data members?*](https://stackoverflow.com/q/58960303) – Stack Overflow

:movie_camera:

- M.Kruse. [*`v.~uint32_t();`*](https://www.youtube.com/watch?v=Pf8gDb-j4wQ) – CppCon (2019)

### Accessing private and protected members

:link:

- J.Schaub. [*Access to private members. That’s easy!*](https://bloglitb.blogspot.com/2010/07/access-to-private-members-thats-easy.html) (2010))

:grey_question:

- [*Accessing private members*](https://stackoverflow.com/q/726096) – Stack Overflow

### Embedding binary data

:link:

- D.Weiler. [incbin – Include binary files in C/C++](https://github.com/graphitemaster/incbin)
- H.Landau. [*Embedding of binary data into programs*](https://www.devever.net/~hl/incbin)

:grey_question:

- [*Embedding resources in executable using GCC*](https://stackoverflow.com/q/4158900) – Stack Overflow

:anchor:

- J. Meneide. *`std::embed`.* [P1040R0](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p1040r0.html) (2018)

---

## Types

### Aggregate, trivial and POD types

:link:

- [*Trivial, standard-layout, POD, and literal types*](https://docs.microsoft.com/en-us/cpp/cpp/trivial-standard-layout-and-pod-types?view=vs-2019) – Visual C++ language reference (2018)
- [*What are aggregates and PODs and how/why are they special?*](https://stackoverflow.com/q/4178175) – Stack Overflow
- [*Trivial vs. standard layout vs. POD*](https://stackoverflow.com/q/6496545) – Stack Overflow

### Floating-point types

> There are three floating point types: `float`, `double`, and `long double`. The type `double` provides at least as much precision as `float`, and the type `long double` provides at least as much precision as `double`. The set of values of the type `float` is a subset of the set of values of the type `double`; the set of values of the type `double` is a subset of the set of values of the type `long double`. The value representation of floating-point types is implementation-defined.

See also [*Floating-point arithmetic* – Numeric data structures and algorithms](../data_structures_and_algorithms/numeric.md#floating-point-arithmetic).

:link:

- D.Howard. [*Byte swapping floating point types*](https://web.archive.org/web/20100125081223/http://www.dmh2000.com/cpp/dswap.shtml) (2007)
- [*Semantics of floating point math in GCC*](https://gcc.gnu.org/wiki/FloatingPointMath) – GCC Wiki
- [*Compiler options: `/fp` (specify floating-point behavior)](https://docs.microsoft.com/en-us/cpp/build/reference/fp-specify-floating-point-behavior) – Visual C++ documentation
- [*Handling overflow when casting doubles to integers in C*](https://stackoverflow.com/q/526070) – Stack Overflow

:anchor:

- P.A.Bristow, C.Kormanyos, J.Maddock. *Floating-point typedefs having specified widths.* [N1703](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1703.pdf), [N3626](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3626.pdf) (2013)

#### `__float128`

:link:

- [*`long double` (GCC specific) and `__float128`*](https://stackoverflow.com/q/13516476) – Stack Overflow
- [*How to use GCC 4.6.0 libquadmath and `__float128` on x86 and x86_64*](https://stackoverflow.com/q/6457385) – Stack Overflow

:anchor:

- [*Additional floating types*](https://gcc.gnu.org/onlinedocs/gcc/Floating-Types.html) – GCC documentation

### Integral types

:link:

- W.Dietz et al. [*Understanding integer overflow in C/C++*](https://www.cs.utah.edu/~regehr/papers/overflow12.pdf) – Proc. ICSE (2012)
- [*Rule 04. Integers*](https://wiki.sei.cmu.edu/confluence/pages/viewpage.action?pageId=87152052) – SEI CERT C coding standard
- [*Why does integer overflow on x86 with GCC cause an infinite loop?*](https://stackoverflow.com/q/7682477) – Stack Overflow
- [*Why does this loop produce “warning: iteration 3u invokes undefined behavior” and output more than 4 lines?*](https://stackoverflow.com/q/24296571) – Stack Overflow

:movie_camera:

- J.Bastien. [*Signed integers are two’s complement*](https://www.youtube.com/watch?v=JhUxIVf1qok) – CppCon (2018)

:anchor:

- J.Bastien. [*Signed integers are two’s complement*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0907r1.html) – WG21/P0907R1 (2018)

### Class types

:link:

- [*Is C++ allowed to increase the derived class size if there are no new member variables compared to the base class?*](https://stackoverflow.com/q/19949737) – Stack Overflow

:anchor:

- [*Class declaration*](https://en.cppreference.com/w/cpp/language/class) – C++ reference

#### Inheritance

:book:

- Ch. 1: *Inheritance*, Ch. 2: *Multiple inheritance* – N.Llopis. *C++ for game programmers* – Charles River Media (2003)

### Function types

:anchor:

- A.Meredith. *Abominable function types.* [P0172R0](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/2015/p0172r0.html) (2015)

### References

:link:

- [*Is null reference possible?*](https://stackoverflow.com/q/4364536) – Stack Overflow

#### Lifetime of a temporary

:link:

- [*Does a `const` reference class member prolong the life of a temporary?*](https://stackoverflow.com/q/2784262) – Stack Overflow

:anchor:

- [*Lifetime of a temporary*](https://en.cppreference.com/w/cpp/language/reference_initialization#Lifetime_of_a_temporary) – C++ reference

#### Rvalue references and move semantics

:link:

- H.E.Hinnant et al. [*A brief introduction to rvalue references*](https://www.artima.com/cppsource/rvalue.html) (2008)
- T.Becker. [*C++ rvalue references explained*](http://thbecker.net/articles/rvalue_references/section_01.html) (2013)
- [*Rvalue reference declarator: `&&`*](https://docs.microsoft.com/en-us/cpp/cpp/rvalue-reference-declarator-amp-amp) – Microsoft Visual C++ (2016)
- S.Meyers. [*Universal references in C++11*](https://accu.org/index.php/journals/1887) ([mirror](https://isocpp.org/blog/2012/11/universal-references-in-c11-scott-meyers)) – [Overload **111**](https://accu.org/index.php/journals/c314/), 8 (2012)
- [*What is move semantics?*](https://stackoverflow.com/q/3106110) – Stack Overflow
- [*Rvalues, lvalues and formal definitions*](https://stackoverflow.com/q/56716647) – Stack Overflow
- [*Pass by value vs pass by rvalue reference*](https://stackoverflow.com/q/37935393) – Stack Overflow
- [*Advantages of using `forward`*](https://stackoverflow.com/q/3582001) – Stack Overflow
- [*Do rvalue references to `const` have any use?*](https://stackoverflow.com/q/4938875) – Stack Overflow

:movie_camera:

- K.Iglberger. *Back to basics: Move semantics.* [Part I](https://www.youtube.com/watch?v=St0MNEU5b0o), [Part II](https://www.youtube.com/watch?v=pIzaZbKUw2s) – CppCon (2019)
- N.Josuttis. [*The nightmare of move semantics for trivial classes*](https://www.youtube.com/watch?v=PNRju6_yn3o) – CppCon (2017)

:anchor:

- B.Stroustrup. [*“New” value terminology*](http://www.stroustrup.com/terminology.pdf)

### Opaque typedefs

See [*Opaque typedef* – Patterns, idioms, and design principles](patterns_and_idioms.md#opaque-typedef-whole-value).

---

## Standards

### C++17

:movie_camera:

- A.Meredith. *C++17 in breadth (not depth).* [Part I](https://www.youtube.com/watch?v=22jIHfvelZk), [Part II](https://www.youtube.com/watch?v=-rIixnNJM4k) – CppCon (2016)

:anchor:

- [*C++17 compiler support*](https://en.cppreference.com/w/cpp/compiler_support#cpp17) – C++ reference

###	C++2a

:movie_camera:

- A.Meredith. [*How C++20 can simplify `std::tuple`*](https://www.youtube.com/watch?v=SvxBvSK4i4k) – ACCU (2019)

:anchor:

- [*C++2a compiler support*](https://en.cppreference.com/w/cpp/compiler_support#cpp2a) – C++ reference

---

## C vs C++

:link:

- D.R.Tribble. [*Incompatibilities between ISO C and ISO C++*](http://david.tribble.com/text/cdiffs.htm) (2001)
- [*Size of character (`'a'`) in C/C++*](https://stackoverflow.com/q/2172943)


<!-- https://sites.google.com/site/grprakash2/confusion -->

<!-- P1839R0 -->

<!-- https://stackoverflow.com/questions/1613341/what-do-the-following-phrases-mean-in-c-zero-default-and-value-initializat

https://stackoverflow.com/questions/37618213/when-is-a-private-constructor-not-a-private-constructor
-->


<!-- https://medium.com/@barryrevzin/value-categories-in-c-17-f56ae54bccbe
http://www.stroustrup.com/terminology.pdf
https://stackoverflow.com/questions/20717180/in-c-what-categories-lvalue-rvalue-xvalue-etc-can-expressions-that-prod
-->

<!-- https://stackoverflow.com/questions/81870/is-it-possible-to-print-a-variables-type-in-standard-c/56766138#56766138 -->
