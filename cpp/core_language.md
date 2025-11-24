# Core language <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
	- [Abstract machine](#abstract-machine)
- [ABI and implementation](#abi-and-implementation)
	- [Itanium C++ ABI](#itanium-c-abi)
	- [Calling conventions](#calling-conventions)
	- [Implementation of inheritance and virtual functions](#implementation-of-inheritance-and-virtual-functions)
	- [Implementation of exceptions](#implementation-of-exceptions)
- [Keywords](#keywords)
- [Attributes](#attributes)
	- [`[[maybe_unused]]`](#maybe_unused)
	- [`[[likely]]` / `[[unlikely]]`](#likely--unlikely)
	- [`[[nodiscard]]`](#nodiscard)
	- [`[[noreturn]]`](#noreturn)
	- [`[[trivially_relocatable]]`](#trivially_relocatable)
- [Declarations](#declarations)
	- [`alignas` and alignment](#alignas-and-alignment)
	- [`auto`](#auto)
	- [`const` and `mutable`](#const-and-mutable)
	- [`volatile`](#volatile)
	- [`constexpr`](#constexpr)
		- [`constexpr` and dynamic allocations](#constexpr-and-dynamic-allocations)
	- [`consteval`](#consteval)
	- [`decltype` and `std::declval()`](#decltype-and-stddeclval)
	- [`enum`, `enum class`](#enum-enum-class)
	- [`friend`](#friend)
		- [Friend function templates](#friend-function-templates)
		- [Hidden friends](#hidden-friends)
	- [`inline`](#inline)
	- [`static`](#static)
	- [`static_assert`](#static_assert)
	- [`using`](#using)
		- [`using enum`](#using-enum)
	- [Elaborated type specifier](#elaborated-type-specifier)
	- [Flexible array member](#flexible-array-member)
	- [Most vexing parse](#most-vexing-parse)
	- [Namespaces](#namespaces)
	- [Storage class specifiers](#storage-class-specifiers)
	- [Structured binding](#structured-binding)
- [Initialization](#initialization)
	- [Aggregate initialization](#aggregate-initialization)
	- [Uniform initialization](#uniform-initialization)
	- [`constinit`](#constinit)
- [Dynamic memory](#dynamic-memory)
	- [Alignment](#alignment)
	- [Object creation and placement `new`](#object-creation-and-placement-new)
	- [Global replacement of `operator new` and `operator delete`](#global-replacement-of-operator-new-and-operator-delete)
- [Exceptions](#exceptions)
	- [`noexcept` specifier](#noexcept-specifier)
- [Expressions](#expressions)
	- [`nullptr`](#nullptr)
	- [Compound literals](#compound-literals)
	- [User-defined literals](#user-defined-literals)
	- [Operator precedence and associativity](#operator-precedence-and-associativity)
	- [Order of evaluation](#order-of-evaluation)
	- [Type conversions](#type-conversions)
		- [`dynamic_cast`](#dynamic_cast)
	- [Type punning](#type-punning)
	- [Value categories](#value-categories)
- [Flow control](#flow-control)
	- [Range-based `for` loop](#range-based-for-loop)
	- [`if`](#if)
		- [`if constexpr`](#if-constexpr)
	- [`switch`](#switch)
- [Functions and function objects](#functions-and-function-objects)
	- [Overload resolution](#overload-resolution)
	- [Argument-dependent lookup](#argument-dependent-lookup)
	- [Function wrappers](#function-wrappers)
		- [`std::function`](#stdfunction)
	- [Lambda expressions](#lambda-expressions)
	- [Member functions](#member-functions)
		- [Member function pointers](#member-function-pointers)
		- [Special member functions](#special-member-functions)
		- [Explicit object parameter / deducing `this`](#explicit-object-parameter--deducing-this)
	- [Deleted functions (`= delete;`)](#deleted-functions--delete)
	- [`main()`](#main)
- [Operators](#operators)
	- [Comparisons](#comparisons)
		- [Three-ways comparisons](#three-ways-comparisons)
		- [Pointer comparisons](#pointer-comparisons)
	- [Conditional operator `?:`](#conditional-operator-)
	- [Logical operators](#logical-operators)
		- [Implication](#implication)
	- [`sizeof` / `alignof`](#sizeof--alignof)
- [Types](#types)
	- [`void`](#void)
	- [Integral types](#integral-types)
		- [Integral promotion](#integral-promotion)
		- [`wchar_t`](#wchar_t)
	- [Floating-point types](#floating-point-types)
		- [`__float128`](#__float128)
	- [Numeric limits](#numeric-limits)
		- [`CHAR_BIT`](#char_bit)
	- [Trivial and POD types](#trivial-and-pod-types)
	- [Pointer and array types](#pointer-and-array-types)
		- [Null pointers](#null-pointers)
	- [Class types](#class-types)
		- [Destructors](#destructors)
		- [Layout](#layout)
		- [Member functions](#member-functions-1)
		- [Polymorphism and inheritance](#polymorphism-and-inheritance)
	- [Union types](#union-types)
	- [Function types](#function-types)
	- [References](#references)
		- [Lifetime of a temporary](#lifetime-of-a-temporary)
		- [Rvalue references, universal references, and move semantics](#rvalue-references-universal-references-and-move-semantics)
	- [Opaque typedefs](#opaque-typedefs)
- [Standards](#standards)
	- [C++11](#c11)
	- [C++14](#c14)
	- [C++17](#c17)
	- [C++20](#c20)
	- [C++23](#c23)
- [Tricks and subtleties](#tricks-and-subtleties)
	- [Accessing private and protected members](#accessing-private-and-protected-members)
	- [Embedding binary data](#embedding-binary-data)
- [C, C vs C++](#c-c-vs-c)
	- [Arrays](#arrays)
	- [Functions](#functions)
	- [Static variables](#static-variables)
	- [Conditional operator](#conditional-operator)

---

## Introduction and overview

:link:

- K.Henney. [*C++ – an invisible foundation of everything*](https://accu.org/journals/overload/29/161/stroustrup/) – [Overload **161**](https://accu.org/journals/overload/overload161) (2021)

:grey_question:

- [*The definitive C++ book guide and list*](https://stackoverflow.com/q/388242) – Stack Overflow

:movie_camera:

- W.E.Brown. [*What I think when I think about C++*](https://www.youtube.com/watch?v=bgyY3x8y4PE) – Core C++ (2022)
- V.Ciura. [*C++ mythbusters*](https://www.youtube.com/watch?v=Ue836lVgPtk) – Meeting C++ (2022)
- H.Sutter. [*Quantifying accidental complexity: An empirical look at teaching and using C++*](https://www.youtube.com/watch?v=6lurOCdaj0Y) – CppCon (2020)
- C.Carruth, T.Winters. [*What is C++*](https://www.youtube.com/watch?v=LJh5QCV4wDg) – CppCon (2019)

:anchor:

- [*Standard C++*](https://isocpp.org/)
- [*The C++ standards committee*](http://www.open-std.org/jtc1/sc22/wg21/)
- [*C++ standards committee papers*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/)
- [*C++ standard core language closed issues*](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html)
- [*C++ standard draft sources*](https://github.com/cplusplus/draft)
- C.Carruth et al. [*Goals and priorities for C++*](https://wg21.link/p2137) – WG21/P2137

### Abstract machine

:grey_question:

- [*Undefined, unspecified and implementation-defined behavior*](https://stackoverflow.com/q/2397984) – Stack Overflow

:movie_camera:

- B.A.Lelbach. [*The C++ execution model*](https://www.youtube.com/watch?v=6zq5ZmCvldU) – ACCU (2025)
- B.Steagall. [*Back to basics: The abstract machine*](https://www.youtube.com/watch?v=ZAji7PkXaKY) – CppCon (2020)

---

## ABI and implementation

:link:

- [*Binary compatibility issues with C++*](https://community.kde.org/Policies/Binary_Compatibility_Issues_With_C%2B%2B) – KDE wiki
- [*ABI stability*](https://source.android.com/devices/architecture/vndk/abi-stability) – Android Open Source Project
- [*The ABI generic analysis and instrumentation library*](https://sourceware.org/libabigail/)

:movie_camera:

- M.Clow. [*What is an ABI, and why is breaking it a problem?*](https://www.youtube.com/watch?v=-XjUiLgJE2Y) – C++Now (2021)
- M.Clow. [*What is an ABI, and why is breaking it bad?*](https://www.youtube.com/watch?v=7RoTDjLLXJQ) – CppCon (2020)
- L.Dionne. [*The C++ ABI from the ground up*](https://www.youtube.com/watch?v=DZ93lP1I7wU) – CppCon (2019)

:anchor:

- T.Winters. [*What is ABI, and what should WG21 do about it?*](https://wg21.link/p2028) – WG21/P2028
- T.Winters. [*ABI – Now or never*](https://wg21.link/p1863) – WG21/P1863
- L.Dionne. [*Controlling the instantiation of vtables and RTTI*](https://wg21.link/p1263) – WG21/P1263

### Itanium C++ ABI

> The Itanium C++ ABI is an ABI for C++. As an ABI, it gives precise rules for implementing the language, ensuring that separately-compiled parts of a program can successfully interoperate. It is not platform-specific and can be layered portably on top of an arbitrary C ABI. It is used as the standard C++ ABI for many major operating systems on all major architectures, and is implemented in many major C++ compilers, including GCC and Clang.

:link:

- [*Itanium C++ ABI*](https://itanium-cxx-abi.github.io/cxx-abi/abi.html)

### Calling conventions

:link:

- R.Orr. [*Windows 64-bit calling conventions*](https://accu.org/journals/overload/22/120/orr_1897/) – [Overload **120**](https://accu.org/journals/overload/overload120) (2014)

### Implementation of inheritance and virtual functions

:link:

- D.Saks. [*Stepping up to C++: How virtual functions work*](https://github.com/eugnsp/CUJ/blob/master/12.01/saks/saks.md) – C/C++ Users Journal **12** (1994)

:grey_question:

- [*Virtual table layout of multiple inheritance*](https://stackoverflow.com/q/15921372) – Stack Overflow

:movie_camera:

- C.Ryan. [*C++ under the hood: Internal class mechanisms*](https://www.youtube.com/watch?v=gWinNE5rd6Q) – CppCon (2024)

:book:

- Ch. 1: *Inheritance*, Sec.: *Inheritance implementation*; Ch. 2: *Multiple inheritance*, Sec.: *Multiple inheritance implementation* – N.Llopis. *C++ for game programmers* – Charles River Media (2003)

### Implementation of exceptions

See also [*Exceptions* – Patterns, idioms, and design principles](patterns_and_idioms.md#exceptions).

:link:

- V.Kochhar. [*How a C++ compiler implements exception handling*](https://www.codeproject.com/Articles/2126/How-a-C-compiler-implements-exception-handling) (2002)

:movie_camera:

- A.Weis. [*Exceptions demystified*](https://www.youtube.com/watch?v=kO0KVB-XIeE) – C++Now (2019)
- J.McNellis. [*Unwinding the stack: Exploring how C++ exceptions work on windows*](https://www.youtube.com/watch?v=COEv2kq_Ht8) – CppCon (2018)
- D.Watson. [*C++ exceptions and stack unwinding*](https://www.youtube.com/watch?v=_Ivd3qzgT7U) – CppCon (2017)

:anchor:

- [*Exception handling*](https://itanium-cxx-abi.github.io/cxx-abi/abi-eh.html) – [Itanium C++ ABI](https://itanium-cxx-abi.github.io/cxx-abi/abi.html)

---

## Keywords

:link:

- H.Sutter. [*Keywords that aren’t (or, comments by another name)*](https://www.drdobbs.com/keywords-that-arent-or-comments-by-anoth/184403859) – Dr.Dobb’s Journal (2003)

---

## Attributes

:grey_question:

- [*In a lambda, what does the second list of attributes do?*](https://stackoverflow.com/q/77704109) – Stack Overflow

:movie_camera:

- B.Saks. [*Better code with C++ attributes*](https://www.youtube.com/watch?v=teUA5U6eYQY) – CppCon (2019)

### `[[maybe_unused]]`

See also [*Unused variables and return values* – Patterns, idioms, and design principles](./patterns_and_idioms.md#unused-variables-and-return-values).

### `[[likely]]` / `[[unlikely]]`

> These attributes allow the compiler to optimize for the case where paths of execution are more or less likely than any alternative path of execution.

See [*`[[likely]]` / `[[unlikely]]` attributes* – Hardware, optimization, and OS internals](optimization_and_hardware.md#likely--unlikely-attributes).

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

- N.Josuttis. [*`[[nodiscard]]` in the library*](https://wg21.link/p0600) – WG21/P0600

### `[[noreturn]]`

> This attribute indicates that the function does not return.

:link:

- A.O’Dwyer. [*`void` versus `[[noreturn]]`*](https://quuxplusone.github.io/blog/2022/06/29/that-undiscovered-country/) (2022)

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

- D.Saks. [*The column that needs a name: Understanding C++ declarations*](https://github.com/eugnsp/CUJ/blob/master/14.01/saks/saks.md) – C/C++ Users Journal **14** (1996)
- D.Anderson. [*The “clockwise/spiral rule”*](http://c-faq.com/decl/spiral.anderson.html)
- T.Parr. [*How to read C declarations*](https://parrt.cs.usfca.edu/doc/how-to-read-C-declarations.html)
- [C gibberish <-> English](https://cdecl.org/)

:movie_camera:

- W.E.Brown. [*A medley of C++*](https://www.youtube.com/watch?v=dRClYjASTvA): [*The principle behind C++ declaration syntax*](https://www.youtube.com/watch?v=dRClYjASTvA&t=1535s) – C++ on Sea (2022)
- H.Hinnant. [*How to initialize `x` from expression `y`*](https://www.youtube.com/watch?v=hobFOAehwio) – Meeting C++ (2019)
- D.Saks. [*East `const` but `constexpr` West*](https://www.youtube.com/watch?v=z6s6bacI424) – code::dive (2018)

### `alignas` and alignment

See also [*Layout* – Class types](#layout).

:anchor:

- [*`alignas` specifier*](https://en.cppreference.com/w/cpp/language/alignas) – C++ reference

### `auto`

> For variables, specifies that the type of the variable will be automatically deduced from its initializer. For functions, specifies that the return type will be deduced from its `return` statements. For non-type template parameters, specifies that the type will be deduced from the argument.

:link:

- H.Sutter. [GotW #92: *`auto` variables, Part 1*](https://herbsutter.com/2013/06/07/gotw-92-solution-auto-variables-part-1/) (2013)
- H.Sutter. [GotW #93: *`auto` variables, Part 2*](https://herbsutter.com/2013/06/13/gotw-93-solution-auto-variables-part-2/) (2013)
- H.Sutter. [GotW #94: *AAA style (almost always `auto`)*](https://herbsutter.com/2013/08/12/gotw-94-solution-aaa-style-almost-always-auto/) (2013)
- R.Orr. [*`auto` – A necessary evil?* (Part II)](https://accu.org/journals/overload/21/116/orr_1840/) – [Overload **116**](https://accu.org/journals/overload/overload116) (2013)
- R.Orr. [*`auto` – A necessary evil?*](https://accu.org/journals/overload/21/115/orr_1859/) – [Overload **115**](https://accu.org/journals/overload/overload115) (2013)

:grey_question:

- [*C++11 – declaring non-static data members as `auto`*](https://stackoverflow.com/q/11302981) – Stack Overflow
- [*Does `auto` make C++ code harder to understand?*](https://softwareengineering.stackexchange.com/q/180216) – Software Engineering

### `const` and `mutable`

> In C++98: `const` means “logically `const`”, in C++11 `const` means “thread safe” (bitwise `const` or internally synchronized). In C++98: `mutable` means “not observably non-`const`”, in C++11 `mutable` means “thread safe” (bitwise `const` or internally synchronized).

:link:

- [*Const correctness*](https://isocpp.org/wiki/faq/const-correctness) – C++ FAQ
- H.Sutter. [GotW #6: *Const-correctness*](http://www.gotw.ca/gotw/006.htm)
- A.O’Dwyer. [*`const` is a contract*](https://quuxplusone.github.io/blog/2019/01/03/const-is-a-contract/) (2019)
- S.Meyers. [*Appearing and disappearing `const`s in C++*](https://aristeia.com/Papers/appearing%20and%20disappearing%20consts.pdf) (2011)
- D.Saks. [*Stepping up to C++: Mutable class members*](https://github.com/eugnsp/CUJ/blob/master/13.04/saks/saks.md) – C/C++ Users Journal **13** (1995)

:grey_question:

- [*Use of `const` for function parameters*](https://stackoverflow.com/q/117293) – Stack Overflow
- [*C++ `const` keyword – use liberally?*](https://stackoverflow.com/q/1554750) – Stack Overflow

:movie_camera:

- H.Sutter. [*You don’t know `const` and `mutable`*](https://channel9.msdn.com/posts/C-and-Beyond-2012-Herb-Sutter-You-dont-know-blank-and-blank) – C++ and Beyond (2012)

:anchor:

- [ES.28: *Use lambdas for complex initialization, especially of `const` variables*](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Res-lambda-init) – C++ core guidelines

### `volatile`

:movie_camera:

- B.Saks. [*What `volatile` means (and doesn’t mean)*](https://www.youtube.com/watch?v=GeblxEQIPFM) – CppCon (2024)

### `constexpr`

:link:

- J.M&uuml;ller. [*`constexpr` is a platform*](https://www.foonathan.net/2020/10/constexpr-platform/) (2020)
- B.Revzin. [*The `constexpr` array size problem*](https://brevzin.github.io/c++/2020/02/05/constexpr-array-size/) (2020)
- A.Krzemie&nacute;ski. [`constexpr` function is not `const`](https://akrzemi1.wordpress.com/2013/06/20/constexpr-function-is-not-const/) (2013)

:grey_question:

- [*Why is a `constexpr` function on a reference not `constexpr`?*](https://stackoverflow.com/q/54124899) – Stack Overflow
- [*Why do we need to mark functions as `constexpr`?*](https://stackoverflow.com/q/14472359) – Stack Overflow
- [*Detecting `constexpr` with SFINAE*](https://stackoverflow.com/q/15232758) – Stack Overflow
- [*Should I mark a compiler-generated constructor as `constexpr`?*](https://stackoverflow.com/q/20810378) – Stack Overflow
- [*Why disallow `goto` in `constexpr` functions?*](https://stackoverflow.com/q/45266577) – Stack Overflow
- [*The value of a `const` variable is or is not usable in a constant expression, depending on the variable type*](https://stackoverflow.com/q/45593044) – Stack Overflow
- [*Can you call a `static constexpr` member function at compile time?*](https://stackoverflow.com/q/78742160) – Stack Overflow

:movie_camera:

- S.Schurr. *`constexpr`:* [*Introduction*](https://www.youtube.com/watch?v=fZjYCQ8dzTc), [*Applications*](https://www.youtube.com/watch?v=qO-9yiAOQqc) – CppCon (2015)

:anchor:

- B.Revzin. [*Using unknown pointers and references in constant expressions*](https://wg21.link/p2280) – WG21/P2280

#### `constexpr` and dynamic allocations

:grey_question:

- [*C++20 `constexpr` `vector` and `string` not working*](https://stackoverflow.com/q/69498115) – Stack Overflow

### `consteval`

:grey_question:

- [*Will `consteval` functions allow template parameters dependent on function arguments?*](https://stackoverflow.com/q/56130792) – Stack Overflow

### `decltype` and `std::declval()`

> The `decltype` specifier inspects the declared type of an entity or the type and value category of an expression. `std::declval` converts any type `T` to a reference type, making it possible to use member functions in the operand of the decltype specifier without the need to go through constructors.

:link:

- A.O’Dwyer. [*`decltype` of a non-static member*](https://quuxplusone.github.io/blog/2021/02/10/decltype-of-member/) (2021)

:grey_question:

- [*Why does `std::declval` add a reference?*](https://stackoverflow.com/q/25707441) – Stack Overflow

:anchor:

- [*`decltype` specifier*](https://en.cppreference.com/w/cpp/language/decltype) – C++ reference

### `enum`, `enum class`

:link:

- S.Dargo. [*Bitwise enumerations*](https://www.sandordargo.com/blog/2022/06/22/bitwise-enums) (2022)
- A.Williams. [*Using `enum class`es as bitfields*](https://www.justsoftwaresolutions.co.uk/cplusplus/using-enum-classes-as-bitfields.html) (2015)

:grey_question:

- [*Is it safe to `reinterpret_cast` an `enum class` variable to a reference of the underlying type?*](https://stackoverflow.com/q/19476818) – Stack Overflow
- [*Using `reinterpret_cast` on an enum class – valid or undefined behavior?*](https://stackoverflow.com/q/29066335) – Stack Overflow
- [*Are C++ enums signed or unsigned?*](https://stackoverflow.com/q/159034) – Stack Overflow

:anchor:

- [*Enumeration declaration*](https://en.cppreference.com/w/cpp/language/enum) – C++ reference
- [*What is the type of an enumeration such as `enum Color`? Is it of type `int`?*](https://isocpp.org/wiki/faq/newbie#enumeration-is-its-own-type) – C++ FAQ
- [*If an enumeration type is distinct from any other type, what good is it? What can you do with it?*](https://isocpp.org/wiki/faq/newbie#enumeration-type-ops) – C++ FAQ

### `friend`

:movie_camera:

- D.Saks. [*Making new friends*](https://www.youtube.com/watch?v=POa_V15je8Y) – CppCon (2018)

#### Friend function templates

See [*Friend function templates* – Function templates – Templates](templates.md#friend-function-templates).

#### Hidden friends

:link:

- A.Williams. [*The power of hidden friends in C++*](https://www.justsoftwaresolutions.co.uk/cplusplus/hidden-friends.html) (2019)

:movie_camera:

- P.Bindels. [*Crouching tiger, hidden friend*](https://www.youtube.com/watch?v=H5TEUiEplY0) – ACCU (2023)

:anchor:

- W.E.Brown, D.Sunderland. [*Recommendations for specifying “hidden friends”*](https://wg21.link/p1601) – WG21/P1601

### `inline`

:link:

- P.Arias. [*Inline variables and functions*](https://pabloariasal.github.io/2019/02/28/cpp-inlining/) (2019)

:grey_question:

- [*One Definition Rule – multiple definition of `inline` functions*](https://stackoverflow.com/q/39652884) – Stack Overflow
- [*Does it make any sense to use `inline` keyword with templates?*](https://stackoverflow.com/q/10535667) – Stack Overflow

:anchor:

- [*`inline` specifier*](https://en.cppreference.com/w/cpp/language/inline) – C++ reference

### `static`

:grey_question:

- [*Static variables in an inlined function*](https://stackoverflow.com/q/185624) – Stack Overflow
- [*What is a `static` function in C?*](https://stackoverflow.com/q/558122) – Stack Overflow

### `static_assert`

:anchor:

- [*`static_assert` declaration*](https://en.cppreference.com/w/cpp/language/static_assert) – C++ reference
- B.Revzin. [*Allowing `static_assert(false)`*](https://wg21.link/p2593) – WG21/P2593

### `using`

:link:

- S.Dargo. [*The 4 use of `using` in C++*](https://www.sandordargo.com/blog/2022/04/27/the-4-use-of-using-in-cpp) (2022)

:grey_question:

- [*A `using` statement compiles with g++, fails compilation with clang*](https://stackoverflow.com/q/27954940) – Stack Overflow
- [*About the ambiguity of `using` a name vs `using` a namespace when doing unqualified calls*](https://stackoverflow.com/q/71690024) – Stack Overflow

#### `using enum`

:anchor:

- [*Using-enum-declaration*](https://en.cppreference.com/w/cpp/language/enum#Using-enum-declaration) – C++ reference
- G.A&zcaron;man, J.M&uuml;ller. [*Using enum*](https://wg21.link/p1099) – WG21/P1099

### Elaborated type specifier

:anchor:

- [*Elaborated type specifier*](https://en.cppreference.com/w/cpp/language/elaborated_type_specifier) – C++ reference

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

- Item 6: *Be alert for C++’s most vexing parse* – S.Meyers. *Effective STL: 50 Specific ways to improve your use of the standard template library* – [Addison-Wesley](https://www.informit.com/store/effective-stl-50-specific-ways-to-improve-your-use-9780201749625) (2001)

:anchor:

- [[stmt.ambig] *Statements: Ambiguity resolution*](http://eel.is/c++draft/stmt.ambig) – C++ standard draft

### Namespaces

:link:

- A.Fertig. [*`static`, `inline`, or an unnamed namespace what’s the difference*](https://andreasfertig.blog/2023/03/static-inline-or-an-unnamed-namespace-whats-the-difference/) (2023)

:grey_question:

- [*Wherefore inline unnamed namespaces?*](https://stackoverflow.com/q/20208591) – Stack Overflow

:anchor:

- [*Namespaces*](https://en.cppreference.com/w/cpp/language/namespace) – C++ reference

### Storage class specifiers

:link:

- A.Fertig. [*`static`, `inline`, or an unnamed namespace what’s the difference*](https://andreasfertig.blog/2023/03/static-inline-or-an-unnamed-namespace-whats-the-difference/) (2023)
- [*What is external linkage and internal linkage?*](https://stackoverflow.com/q/1358400) – Stack Overflow
- P.Goldsborough. [*Internal and external linkage in C++*](http://www.goldsborough.me/c/c++/linker/2016/03/30/19-34-25-internal_and_external_linkage_in_c++/) (2016)
- J.Schilling. [*Extern inlines by default*](https://web.archive.org/web/20060509150105/glenmccl.com/ansi_015.htm) (2001)

:movie_camera:

- D.Saks. [*Storage duration and linkage in C and C++*](https://www.youtube.com/watch?v=0kgTuWkyorc) – NDC TechTown (2019)

:anchor:

- [*Storage class specifiers*](https://en.cppreference.com/w/cpp/language/storage_duration) – C++ reference

### Structured binding

:link:

- S.Brand. [*Adding C++17 structured bindings support to your classes*](https://blog.tartanllama.xyz/structured-bindings/) (2016)

:grey_question:

- [*Understand structured binding in C++17 by analogy*](https://stackoverflow.com/q/49795131) – Stack Overflow
- [*Why are structured bindings defined in terms of a uniquely named variable?*](https://stackoverflow.com/q/49797286) – Stack Overflow
- [*Structured bindings and tuple of references*](https://stackoverflow.com/q/49628401) – Stack Overflow

:anchor:

- [*Structured binding declaration*](https://en.cppreference.com/w/cpp/language/structured_binding) – C++ reference
- B.Revzin, J.Wakely. [*Structured bindings can introduce a pack*](https://wg21.link/p1061) – WG21/P1061
- N.Lesser. [*Extending structured bindings to be more like variable declarations*](https://wg21.link/p1091) – WG21/P1091

---

## Initialization

:link:

- A.O’Dwyer. [*PSA: Value-initialization is not merely default-construction*](https://quuxplusone.github.io/blog/2023/06/22/psa-value-initialization/) (2023)
- P.Arias. [*Initialization of static variables*](https://pabloariasal.github.io/2020/01/02/static-variable-initialization/) (2020)
- C.McClure. [*C++ object initialization*](https://daemons.net/programming/c++/initialization.html)
- B.Filipek. [*What happens to your static variables at the start of the program?*](https://www.bfilipek.com/2018/02/staticvars.html) (2018)
- S.Brand. [*Initialization in C++ is bonkers*](https://accu.org/journals/overload/25/139/brand_2379/) – [Overload **139**](https://accu.org/journals/overload/overload139), 9 (2017)
- E.Martin. [*Static initializers*](http://neugierig.org/software/chromium/notes/2011/08/static-initializers.html) (2011)
- A.Demin. [*The difference between `new T()` and `new T`*](http://demin.ws/blog/russian/2009/02/20/difference-between-new-and-new-with-brackets/) (in Russian, 2009)

:grey_question:

- [*Is C++11 uniform initialization a replacement for the old style syntax?*](https://softwareengineering.stackexchange.com/q/133688) – Software Engineering
- [*Can `T t = {};` and `T t{};` produce different results?*](https://stackoverflow.com/q/62008160) – Stack Overflow

:anchor:

- [*Initialization*](https://en.cppreference.com/w/cpp/language/initialization) – C++ reference

### Aggregate initialization

:link:

- A.Fertig. [*Aggregates: C++17 vs. C++20*](https://andreasfertig.blog/2024/02/aggregates-cpp17-vs-cpp20/) (2024)

:grey_question:

- [*What are aggregates and PODs and how/why are they special?*](https://stackoverflow.com/q/4178175) – Stack Overflow

:anchor:

- [*Aggregate initialization*](https://en.cppreference.com/w/cpp/language/aggregate_initialization) – C++ reference

### Uniform initialization

:link:

- A.Fertig. [*Evaluation order in C++ and uniform initialization*](https://andreasfertig.blog/2023/05/evaluation-order-in-cpp-and-uniform-initialization/) (2023)

### `constinit`

:grey_question:

- [*What is `constinit` in C++20?*](https://stackoverflow.com/q/57845131) – Stack Overflow

---

## Dynamic memory

:link:

- D.Saks. [*C++ theory and practice: `new` and `delete`*](https://github.com/eugnsp/CUJ/blob/master/15.01/saks/saks.md) – C/C++ Users Journal **15** (1997)

:grey_question:

- [*How do compilers use “over-allocation” to remember the number of elements in an allocated array?*](https://isocpp.org/wiki/faq/compiler-dependencies#num-elems-in-new-array-overalloc) – C++ FAQ
- [*How do compilers use an “associative array” to remember the number of elements in an allocated array?*](https://isocpp.org/wiki/faq/compiler-dependencies#num-elems-in-new-array-assocarray) – C++ FAQ
- [*Treating memory returned by operator `new(sizeof(T) * N)` as an array*](https://stackoverflow.com/q/53451770) – Stack Overflow
- [*Why should C++ programmers minimize use of `new`?*](https://stackoverflow.com/q/6500313) – Stack Overflow
- [*Difference between `new` and `operator new`?*](https://stackoverflow.com/q/1885849) – Stack Overflow

:book:

- Sec. 19.2.5: *Allocation and deallocation* – B.Stroustrup. [*The C++ programming language*](http://www.stroustrup.com/4th.html) – [Addison-Wesley](https://www.pearson.com/us/higher-education/program/Stroustrup-C-Programming-Language-The-4th-Edition/PGM326200.html) (2013)
- Item 8: *Understand the different meanings of `new` and `delete`* – S.Meyers. *More effective C++: 35 new ways to improve your programs and designs* – [Addison-Wesley](https://www.informit.com/store/more-effective-c-plus-plus-35-new-ways-to-improve-your-9780201633719) (1996)
- Ch. 10: *Memory management* – B.Stroustrup. [*The design and evolution of C++*](http://www.stroustrup.com/dne.html) – [Addison-Wesley](https://www.pearson.com/us/higher-education/program/Stroustrup-Design-and-Evolution-of-C-The/PGM287667.html) (1994)

:anchor:

- [*Low level memory management*](https://en.cppreference.com/w/cpp/memory/new) – C++ reference
- [R.10: *Avoid `malloc()` and `free()`*](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Rr-mallocfree) – C++ core guidelines
- [R.11: *Avoid calling `new` and `delete` explicitly*](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Rr-newdelete) – C++ core guidelines

### Alignment

:link:

- B.Filipek. [*New `new()`: The C++17’s alignment parameter for `operator new()`*](https://www.bfilipek.com/2019/08/newnew-align.html) (2019)

:anchor:

- C.Nelson. [*Dynamic memory allocation for over-aligned data*](https://wg21.link/p0035) – WG21/P0035

### Object creation and placement `new`

See also [*Uninitialized storage* – The standard library and proposals](std_library.md#uninitialized-storage).

:grey_question:

- [*Array placement-new requires unspecified overhead in the buffer?*](https://stackoverflow.com/q/8720425) – Stack Overflow
- [*Is using `malloc` for `int` undefined behavior until C++20*](https://stackoverflow.com/q/63379066) – Stack Overflow

:movie_camera:

- C.J.Johnson. [*How to hold a `T`*](https://www.youtube.com/watch?v=WX8FsrUbLjc) – CppCon (2019)

:anchor:

- R.Smith. [*Implicit creation of objects for low-level object manipulation*](https://wg21.link/p0593) – WG21/P0593
- B.Hutchings. [*Determining the buffer size for placement new*](https://wg21.link/cwg476) – WG21/CWG issue 476 (2004)
- T.Koeppe. [*C++ DR about global placement array new*](https://wg21.link/ewg68) – WG21/EWG issue 68 (2013)

### Global replacement of `operator new` and `operator delete`

:grey_question:

- [*How to properly replace global `new` and `delete` operators*](https://stackoverflow.com/q/8186018) – Stack Overflow
- [*Is it possible to replace the global `operator new` everywhere?*](https://stackoverflow.com/q/2104459) – Stack Overflow

:anchor:

- [*`operator new`, `operator new[]`: Global_replacements*](https://en.cppreference.com/w/cpp/memory/new/operator_new#Global_replacements) – C++ reference

---

## Exceptions

See also [*Exceptions* – Patterns, idioms, and design principles](patterns_and_idioms.md#exceptions) and [*Exceptions* – The standard library and proposals](std_library.md#exceptions).

:link:

- R.McArdell. [*C++11 (and beyond) exception support*](https://accu.org/journals/overload/25/141/mcardell_2422/) – [Overload **141**](https://accu.org/journals/overload/overload141) (2017)

:grey_question:

- B.Stroustrup. [*Why doesn’t C++ provide a `finally` construct?*](http://www.stroustrup.com/bs_faq2.html#finally) – C++ style and technique FAQ
- [*Is there any difference between `noexcept` and empty throw specification for an lambda expression?*](https://stackoverflow.com/q/37433371) – Stack Overflow
- [*Losing exception type when rethrowing an exception from a `catch` block*](https://stackoverflow.com/q/12548022) – Stack Overflow

### `noexcept` specifier

> Specifies whether a function could throw exceptions.

:anchor:

- [*`noexcept` specifier*](https://en.cppreference.com/w/cpp/language/noexcept_spec) – C++ reference

---

## Expressions

### `nullptr`

> The keyword `nullptr` denotes the pointer literal. It is a prvalue of type `std::nullptr_t`.

See [*`std::nullptr_t`* – The standard library and proposals](std_library.md#stdnullptr_t).

### Compound literals

> A compound literal constructs an unnamed object of specified type in-place: `( type ) { initializer-list }`.

:link:

- R.Meyers. [*The new C: Compound literals*](https://www.drdobbs.com/the-new-c-compound-literals/184401404) – Dr.Dobb’s Journal (2001)

:grey_question:

- [*Are compound literals standard C++?*](https://stackoverflow.com/q/28116467) – Stack Overflow

:anchor:

- [*Compound literals*](https://en.cppreference.com/w/c/language/compound_literal) – C++ reference

### User-defined literals

> A user-defined literal (UDL) allows integer, floating-point, character, and string literals to produce objects of user-defined type by defining a user-defined suffix.

:link:

- A.O’Dwyer. [*Namespaces for UDLs*](https://quuxplusone.github.io/blog/2018/03/21/namespaces-for-udls/) (2018)

:anchor:

- [*User-defined literals*](https://en.cppreference.com/w/cpp/language/user_literal) – C++ reference

### Operator precedence and associativity

:grey_question:

- [*Who defines C operator precedence and associativity, and how does it relate to order of evaluation?*](https://stackoverflow.com/q/20767745) – Stack Overflow
- [*What is the relation between operator precedence and order of evaluation?*](https://stackoverflow.com/q/5473107) – Stack Overflow

:anchor:

- [*C++ operator precedence*](https://en.cppreference.com/w/cpp/language/operator_precedence) – C++ reference

### Order of evaluation

:link:

- E.Lippert. [*Precedence vs associativity vs order*](https://ericlippert.com/2008/05/23/precedence-vs-associativity-vs-order/) (2008)
- P.Becker. [*Questions & Answers*](https://github.com/eugnsp/CUJ/blob/master/16.01/becker/becker.md#order-of-evaluation) – C/C++ Users Journal **16** (1998)

:grey_question:

- [*What is the relation between operator precedence and order of evaluation?*](https://stackoverflow.com/q/5473107) – Stack Overflow
- [*Who defines C operator precedence and associativity, and how does it relate to order of evaluation?*](https://stackoverflow.com/q/20767745) – Stack Overflow
- [*Undefined behavior and sequence points*](https://stackoverflow.com/q/4176328) – Stack Overflow

:book:

- T.Cargill. *A dynamic vector is harder than it looks* – S.B.Lippman. [*C++ gems: Programming pearls from The C++ report*](https://www.cambridge.org/ru/academic/subjects/computer-science/software-engineering-and-development/c-gems-programming-pearls-c-report) (1997)

:anchor:

- [*Order of evaluation*](https://en.cppreference.com/w/cpp/language/eval_order) – C++ reference

### Type conversions

:grey_question:

- [*When should `static_cast`, `dynamic_cast`, `const_cast`, and `reinterpret_cast` be used?*](https://stackoverflow.com/q/332030) – Stack Overflow

:book:

- Item 2: *Prefer C++-style casts* – S.Meyers. *More effective C++: 35 new ways to improve your programs and designs* – [Addison-Wesley](https://www.informit.com/store/more-effective-c-plus-plus-35-new-ways-to-improve-your-9780201633719) (1996)

#### `dynamic_cast`

:link:

- A.O’Dwyer. [*Classically polymorphic visit replaces some uses of `dynamic_cast`*](https://quuxplusone.github.io/blog/2020/09/29/oop-visit/) (2020)

:grey_question:

- [*C++ equivalent of Java’s `instanceof`*](https://stackoverflow.com/q/500493) – Stack Overflow
- [*`dynamic_cast` with RTTI disabled*](https://stackoverflow.com/q/7687041) – Stack Overflow

:movie_camera:

- A.O’Dwyer. [*`dynamic_cast` from scratch*](https://www.youtube.com/watch?v=QzJL-8WbpuU) – CppCon (2017)

:anchor:

- [*`dynamic_cast` conversion*](https://en.cppreference.com/w/cpp/language/dynamic_cast) – C++ reference

### Type punning

:memo:

- Since C++20, some of type punning can be done using `std::bit_cast`, see [*`std::bit_cast`* – The standard library and Boost](#std_library.md#stdbit_cast).

:link:

- M.Sebor. *The joys and perils of C and C++ aliasing.* [Part 1](https://developers.redhat.com/blog/2020/06/02/the-joys-and-perils-of-c-and-c-aliasing-part-1), [Part II](https://developers.redhat.com/blog/2020/06/03/the-joys-and-perils-of-aliasing-in-c-and-c-part-2) (2020)
- L.Torvalds. [*... What’s the **real** reason for avoiding union aliasing?*](https://lkml.org/lkml/2018/6/5/769) – Linux kernel mailing list (2018)
- S.Yaghmour. [*What is the strict aliasing rule and why do we care?*](https://gist.github.com/shafik/848ae25ee209f698763cffee272a58f8) (2018)
- M.Acton. [*Understanding strict aliasing*](https://cellperformance.beyond3d.com/articles/2006/06/understanding-strict-aliasing.html) (2006)

:grey_question:

- [*gcc, strict-aliasing, and horror stories*](https://stackoverflow.com/q/2958633) – Stack Overflow
- [*What is the strict aliasing rule?*](https://stackoverflow.com/q/98650) – Stack Overflow
- [*Performance benefits of strict aliasing*](https://stackoverflow.com/q/754929) – Stack Overflow
- [*Gcc, strict-aliasing, and casting through a union*](https://stackoverflow.com/q/2906365) – Stack Overflow
- [*Can I safely convert struct of floats into float array in C++?*](https://stackoverflow.com/q/45898184) – Stack Overflow
- [*Reinterpret struct with members of the same type as an array in a standard compliant way*](https://stackoverflow.com/q/41419164) – Stack Overflow

:movie_camera:

- T.Doumler. [*(How not to do) Type punning in modern C++*](https://www.youtube.com/watch?v=_qzMpk-22cc) – CppCon (2019)

:anchor:

- [*Type punning*](https://en.wikipedia.org/wiki/Type_punning) – Wikipedia
- [Options that control optimization: Type punning](https://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html#Type-punning) – GCC documentation

### Value categories

:link:

- A.S.Knatten. [*lvalues, rvalues, glvalues, prvalues, xvalues, help!*](https://accu.org/journals/overload/27/150/knatten_2641/) – [Overload **150**](https://accu.org/journals/overload/overload150) (2019)
- B.Revzin. [*Value categories in C++17*](https://medium.com/@barryrevzin/value-categories-in-c-17-f56ae54bccbe) (2017)

:grey_question:

- [*What categories (lvalue, rvalue, xvalue, etc.) can expressions that produce temporaries of class type fall into?*](https://stackoverflow.com/q/20717180) – Stack Overflow
- [*Rvalues, lvalues and formal definitions*](https://stackoverflow.com/q/56716647) – Stack Overflow

:movie_camera:

- W.E.Brown. [*A medley of C++*](https://www.youtube.com/watch?v=dRClYjASTvA): [*Exploring C++ value categories and the expression category taxonomy*](https://www.youtube.com/watch?v=dRClYjASTvA&t=5078s) – C++ on Sea (2022)

:anchor:

- [*Value categories*](https://en.cppreference.com/w/cpp/language/value_category) – C++ reference
- B.Stroustrup. [*“New” value terminology*](http://www.stroustrup.com/terminology.pdf)

---

## Flow control

### Range-based `for` loop

:link:

- S.Dargo. [*The infamous bug of range-based for loops*](https://www.sandordargo.com/blog/2022/04/20/range-base-p2012) (2022)
- M.Clow. [*Range based for loops and pairs of iterators*](https://cplusplusmusings.wordpress.com/2013/04/14/range-based-for-loops-and-pairs-of-iterators/) (2013)

:movie_camera:

- D.K&uuml;hl. [*Range `for`*](https://www.youtube.com/watch?v=hGu9XWsOgWQ) – CppCon (2016)

### `if`

:anchor:

- [`if` statement](https://en.cppreference.com/w/cpp/language/if) – C++ reference

#### `if constexpr`

:grey_question:

- [*Difference between `if constexpr()` vs `if()`*](https://stackoverflow.com/q/43434491) – Stack Overflow

### `switch`

> Transfers control to one of several statements, depending on the value of a condition.

:movie_camera:

- H.Wennborg. [*C++ `switch` statements under the hood in LLVM*](https://www.youtube.com/watch?v=nfy51jenN3M) – StockholmCpp (2024)

:anchor:

- [*`switch` statement*](https://en.cppreference.com/w/cpp/language/switch) - C++ reference

---

## Functions and function objects

:grey_question:

- [*Simplest way to determine return type of function*](https://stackoverflow.com/q/53673442) – Stack Overflow
- [*C++ `decltype` deducing current function returned type*](https://stackoverflow.com/q/21412144) – Stack Overflow

:movie_camera:

- B.Saks. [*Back to basics: Function call resolution in C++*](https://www.youtube.com/watch?v=ab_RzvGAS1Q) – CppCon (2024)
- M.Shah. [*Back to basics: Functions in C++*](https://www.youtube.com/watch?v=CpHX1Du5R0Q) – CppCon (2023)

### Overload resolution

:link:

- [*Overload resolution between object, rvalue reference, const reference*](https://stackoverflow.com/q/17961719) – Stack Overflow

### Argument-dependent lookup

:link:

- [*What is “argument-dependent lookup” (aka ADL, or “Koenig lookup”)?*](https://stackoverflow.com/q/8111677) – Stack Overflow
- A.O’Dwyer. [*What is ADL?*](https://quuxplusone.github.io/blog/2019/04/26/what-is-adl/) (2019)
- A.O’Dwyer. [*ADL insanity*](https://quuxplusone.github.io/blog/2019/04/08/adl-insanity/) (2019)
- A.O’Dwyer. [*How `hana::type<T>` “disables ADL”*](https://quuxplusone.github.io/blog/2019/04/09/adl-insanity-round-2/) (2019)
- A.O’Dwyer. [*Avoid ADL calls to functions with common names*](https://quuxplusone.github.io/blog/2018/06/17/std-size/) (2018)
- A.O’Dwyer. [*WG21: Avoid creating ADL situations on functions with semi-common names*](https://quuxplusone.github.io/blog/2018/11/04/std-hash-value/) (2018)

:grey_question:

- [*Why doesn’t ADL find function templates?*](https://stackoverflow.com/q/2953684) – Stack Overflow

:movie_camera:

- J.Turner. [Episode 160: *Argument dependent lookup*](https://www.youtube.com/watch?v=agS-h_eaLj8) – C++ Weekly

:anchor:

- [*Argument-dependent lookup*](https://en.cppreference.com/w/cpp/language/adl) – C++ reference
- J.Spicer. [*ADL and function templates that are not visible*](https://wg21.link/p0846) – WG21/P0846

### Function wrappers

#### `std::function`

:grey_question:

- [*Move-only version of `std::function`*](https://stackoverflow.com/q/25330716) – Stack Overflow
- [*How to create an `std::function` from a move-capturing lambda expression?*](https://stackoverflow.com/q/25421346) – Stack Overflow

:anchor:

- [*`std::function`*](https://en.cppreference.com/w/cpp/utility/functional/function) – C++ reference

### Lambda expressions

See also [*Lambda expression idioms* – Patterns, idioms, and design principles](./patterns_and_idioms.md#lambda-expression-idioms).

:link:

- R.Chen. [*Non-capturing C++ lambdas can be converted to a pointer to function, but what about the calling convention?*](https://devblogs.microsoft.com/oldnewthing/20150220-00/?p=44623) (2015)
- S.Meyers. [*C++14 lambdas and perfect forwarding*](https://scottmeyers.blogspot.com/2013/05/c14-lambdas-and-perfect-forwarding.html) (2013)
- S.Meyers. [*Lambdas vs. closures*](https://scottmeyers.blogspot.com/2013/05/lambdas-vs-closures.html) (2013)
- A.Allain. [*Lambda functions in C++11 – the definitive guide*](https://www.cprogramming.com/c++11/c++11-lambda-closures.html) (2011)

:grey_question:

- [*What is the need of template lambda introduced in C++20 when C++14 already has generic lambda?*](https://stackoverflow.com/q/54126204) – Stack Overflow
- [*What is a lambda expression in C++11?*](https://stackoverflow.com/q/7627098) – Stack Overflow
- [*Why are lambda expressions not allowed in an unevaluated operands but allowed in the unevaluated portions of constant expressions?*](https://stackoverflow.com/q/22232164) – Stack Overflow
- [*Can we get the type of a lambda argument?*](https://stackoverflow.com/q/6512019) – Stack Overflow
- [*Why is a `const` variable sometimes not required to be captured in a lambda?*](https://stackoverflow.com/q/43467095) – Stack Overflow
- [*In a lambda, what does the second list of attributes do?*](https://stackoverflow.com/q/77704109) – Stack Overflow

:movie_camera:

- W.E.Brown. [*A medley of C++*](https://www.youtube.com/watch?v=dRClYjASTvA): [*Why are they named lambdas?*](https://www.youtube.com/watch?v=dRClYjASTvA&t=2696s) – C++ on Sea (2022)
- R.Orr. [*Let’s look at lambdas*](https://www.youtube.com/watch?v=NAuFNXIsbtw) – ACCU (2021)
- B.Geller, A.Sermersheim. [*Back to basics: Lambda expressions*](https://www.youtube.com/watch?v=ZIPNFcw6V9o) – CppCon (2020)
- B.Deane. [*C++20 lambdas: Familiar template syntax*](https://www.youtube.com/watch?v=uOc6RPu9-CA) – CppCon (2020)
- A.O’Dwyer. [*Back to basics: Lambdas from scratch*](https://www.youtube.com/watch?v=3jCOwajNch0) – CppCon (2019)

:anchor:

- L.Dionne, H.Tong. [*Wording for lambdas in unevaluated contexts*](https://wg21.link/p0315) – WG21/P0315
- L.Dionne. [*Familiar template syntax for generic lambdas*](https://wg21.link/p0428) – WG21/P0428

### Member functions

#### Member function pointers

:link:

- A.Fertig. [*Calling a C++ member function with a null object*](https://andreasfertig.blog/2024/06/calling-a-cpp-member-function-with-a-null-object/) (2024)
- A.Fertig. [*The power of ref-qualifiers*](https://andreasfertig.blog/2022/07/the-power-of-ref-qualifiers/) (2022)
- V.Lazarenko. [*Why C++ member function pointers are 16 bytes wide*](http://lazarenko.me/wide-pointers/) (2013)
- R.Chen. [*Pointers to member functions are very strange animals*](https://devblogs.microsoft.com/oldnewthing/?p=40713) (2004)
- C.Skelly. [*Powerful pointers to member functions*](https://github.com/eugnsp/CUJ/blob/master/12.10/skelly/skelly.md) – C/C++ Users Journal **12** (1994)

:movie_camera:

- C.Ryan. [*C++ under the hood: Internal class mechanisms*](https://www.youtube.com/watch?v=gWinNE5rd6Q) – CppCon (2024)

:anchor:

- [*Pointers to member functions*](https://isocpp.org/wiki/faq/pointers-to-members) – C++ FAQ

#### Special member functions

:movie_camera:

- K.van Rens. [*Special member functions in C++*](https://www.youtube.com/watch?v=ajRTADPXEko) – C++ on Sea (2023)

#### Explicit object parameter / deducing `this`

:link:

- S.Brand. [*C++23’s deducing `this`: what it is, why it is, how to use it*](https://devblogs.microsoft.com/cppblog/cpp23-deducing-this/)

### Deleted functions (`= delete;`)

> If, instead of a function body, the special syntax `= delete;` is used, the function is defined as deleted. Any use of a deleted function is ill-formed (the program will not compile).

:link:

- A.O’Dwyer. [*Refactoring with `=delete`*](https://quuxplusone.github.io/blog/2022/11/11/refactoring-with-delete/) (2022)
- A.O’Dwyer. [*What `=delete` means*](https://quuxplusone.github.io/blog/2021/10/17/equals-delete-means/) (2021)
- A.Knatten. [*No move vs deleted move constructors*](https://accu.org/journals/overload/29/166/knatten/) – [Overload **166**](https://accu.org/journals/overload/overload166) (2021)
- A.Knatten. [*The difference between no move constructor and a deleted move constructor*](https://blog.knatten.org/2021/10/15/the-difference-between-no-move-constructor-and-a-deleted-move-constructor/) (2021)


:anchor:

- [*Deleted functions*](https://en.cppreference.com/w/cpp/language/function#Deleted_functions) – C++ reference

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

:movie_camera:

- B.Deane. [*Operator overloading: History, principles and practice*](https://www.youtube.com/watch?v=zh4EgO13Etg) – CppCon (2018)

:anchor:

- [*`operator` overloading*](https://en.cppreference.com/w/cpp/language/operators) – C++ reference
- [*Canonical implementations*](https://en.cppreference.com/w/cpp/language/operators#Canonical_implementations) – C++ reference

### Comparisons

:link:

- J.M&uuml;ller. [*Mathematics behind comparison*](https://foonathan.net/2018/06/equivalence-relations/) (2018)
- B.Stroustrup. [*A bit of background for the default comparison proposal*](https://isocpp.org/blog/2016/02/a-bit-of-background-for-the-default-comparison-proposal-bjarne-stroustrup) (2016)

:anchor:

- [*Comparison operators*](https://en.cppreference.com/w/cpp/language/operator_comparison) – C++ reference
- B.Stroustrup. [*Default comparisons*](https://wg21.link/n4175) – WG21/N4175

#### Three-ways comparisons

:link:

- J.Boccara. [*How to define comparison operators by default in C++*](https://www.fluentcpp.com/2021/08/23/how-to-define-comparison-operators-by-default-in-c/) (2021)
- B.Revzin. [*Implementing the spaceship operator for `optional`*](https://accu.org/journals/overload/26/147/revzin_2563/) (2018)
 – [Overload **147**](https://accu.org/journals/overload/overload147) (2018)

:movie_camera:

- L.de Cock. [*Space invaders: The C++20 spaceship operator is upon us*](https://www.youtube.com/watch?v=_dFnSfFMuPw) – ACCU (2023)
- W.E.Brown. [*A C++20 preview: `operator<=>`*](https://www.youtube.com/watch?v=_PKpyD6Ba1s) – CppCon (2017)

:anchor:

- [*Default comparisons*](https://en.cppreference.com/w/cpp/language/default_comparisons) – C++ reference
- D.Stone. [*I did not order this! Why is it on my bill?*](https://wg21.link/p1190) – WG21/P1190 <!-- see refs inside! -->

#### Pointer comparisons

:link:

- A.O’Dwyer. [*Pointer comparisons with `std::less<void>`: a horror story*](https://quuxplusone.github.io/blog/2019/01/20/std-less-nightmare/) (2019)
- K.Walfridsson. [*C pointers are not hardware pointers*](https://kristerw.blogspot.com/2016/03/c-pointers-are-not-hardware-pointers.html) (2016)

:anchor:

- [*Pointer comparison operators*](https://en.cppreference.com/w/cpp/language/operator_comparison#Pointer_comparison_operators) – C++ reference

### Conditional operator `?:`

:link:

- K.Pugh. [*Using the conditional operator `?:`*](https://github.com/eugnsp/CUJ/blob/master/10.02/pugh/pugh.md#conditional_operator) – C/C++ Users Journal **10** (1992)

### Logical operators

#### Implication

:link:

- [*In support of implication for C++*](https://www.elbeno.com/blog/?p=1725) (2023)

:anchor:

- W.E.Brown. [*Implication for C++*](https://wg21.link/p2971) – WG21/P2971

### `sizeof` / `alignof`

> The `sizeof` operator yields the size in bytes of the object or type. When applied to a class type, the result is the size of an object of that class plus any additional padding required to place such object in an array. The `alignof` operator returns the alignment required for any instance of a type.

:grey_question:

- [*Is it always the case that `sizeof(T) >= alignof(T)` for all object types `T`?*](https://stackoverflow.com/questions/46457449) – Stack Overflow

:anchor:

- [*`sizeof` operator*](https://en.cppreference.com/w/cpp/language/sizeof) – C++ reference
- [*`alignof` operator*](https://en.cppreference.com/w/cpp/language/alignof) – C++ reference

---

## Types

:grey_question:

- [*What are the 15 classifications of types in C++?*](https://stackoverflow.com/q/27032790) – Stack Overflow

:movie_camera:

- W.E.Brown. [*A medley of C++*](https://www.youtube.com/watch?v=dRClYjASTvA): [*The universe of C++ types*](https://www.youtube.com/watch?v=dRClYjASTvA&t=170s) – C++ on Sea (2022)
- B.Milewski. [*Why algebraic data types are important*](https://www.youtube.com/watch?v=LkqTLJK2API) – code::dive (2018)

### `void`

:grey_question:

- [*How much existing C++ code would break if `void` was actually defined as `struct void {};`*](https://stackoverflow.com/questions/53197340) – Stack Overflow

:anchor:

- [Void type](https://en.cppreference.com/w/cpp/language/types#Void_type) – C++ reference

### Integral types

:link:

- J.M&uuml;ller. [*New integer types I’d like to see*](https://www.foonathan.net/2022/09/new-integer-types/) (2022)
- W.Dietz et al. [*Understanding integer overflow in C/C++*](https://www.cs.utah.edu/~regehr/papers/overflow12.pdf) – Proc. ICSE (2012)
- [*Rule 04. Integers*](https://wiki.sei.cmu.edu/confluence/pages/viewpage.action?pageId=87152052) – SEI CERT C coding standard

:grey_question:

- [*Compiler optimizations may cause integer overflow. Is that okay?*](https://stackoverflow.com/q/74102654) – Stack Overflow
- [*Why does integer overflow on x86 with GCC cause an infinite loop?*](https://stackoverflow.com/q/7682477) – Stack Overflow
- [*Why does this loop produce “warning: iteration `3u` invokes undefined behavior” and output more than 4 lines?*](https://stackoverflow.com/q/24296571) – Stack Overflow
- [*Does a `long` ban make sense?*](https://softwareengineering.stackexchange.com/q/317670) – Software Engineering

:movie_camera:

- R.Seacord. [*Integer type selection in C++ in safe, secure and correct code*](https://www.youtube.com/watch?v=82jVpEmAEV4) – C++ Now (2023)
- J.Bastien. [*Signed integers are two’s complement*](https://www.youtube.com/watch?v=JhUxIVf1qok) – CppCon (2018)
- D.Saks. [*Choosing the right integer types in C and C++*](https://www.youtube.com/watch?v=IJaa58cfvOw) – code::dive (2018)

:anchor:

- J.Bastien. [*Signed integers are two’s complement*](https://wg21.link/p0907) – WG21/P0907

#### Integral promotion

:grey_question:

- [*Implicit type conversion rules in C++ operators*](https://stackoverflow.com/q/5563000) – Stack Overflow
- [*Why do unsigned “small” integers promote to `signed int`?*](https://stackoverflow.com/q/56604299) – Stack Overflow

:movie_camera:

- S.Shemesh. [*C++ integer promotion is completely broken*](https://www.youtube.com/watch?v=b0VjS0OKTmQ) – Core C++ (2021)

:anchor:

- [*Integral promotion*](https://en.cppreference.com/w/cpp/language/implicit_conversion#Integral_promotion) – C++ reference

#### `wchar_t`

:link:

- [*`wchar_t` is a historical accident*](https://www.moria.us/articles/wchar-is-a-historical-accident/) (2017)

### Floating-point types

> There are three floating point types: `float`, `double`, and `long double`. The type `double` provides at least as much precision as `float`, and the type `long double` provides at least as much precision as `double`. The set of values of the type `float` is a subset of the set of values of the type `double`; the set of values of the type `double` is a subset of the set of values of the type `long double`. The value representation of floating-point types is implementation-defined.

See also [*Floating-point arithmetic* – Numeric data structures and algorithms](../data_structures_and_algorithms/numeric.md#floating-point-arithmetic).

:link:

- D.Howard. [*Byte swapping floating point types*](https://web.archive.org/web/20100125081223/http://www.dmh2000.com/cpp/dswap.shtml) (2007)
- [*Semantics of floating point math in GCC*](https://gcc.gnu.org/wiki/FloatingPointMath) – GCC Wiki
- [*Compiler options: `/fp` (specify floating-point behavior)](https://docs.microsoft.com/en-us/cpp/build/reference/fp-specify-floating-point-behavior) – Visual C++ documentation
- [*Handling overflow when casting doubles to integers in C*](https://stackoverflow.com/q/526070) – Stack Overflow

:grey_question:

- [*When do you use `float` and when do you use `double`*](https://softwareengineering.stackexchange.com/q/188721) – Software Engineering

:anchor:

- P.A.Bristow, C.Kormanyos, J.Maddock. [*Floating-point typedefs having specified widths*](https://wg14.link/n1703) – WG14/N1703
- P.A.Bristow, C.Kormanyos, J.Maddock. [*Floating-point typedefs having specified widths*](https://wg21.link/n3626) – WG21/N3626

#### `__float128`

:link:

- [*`long double` (GCC specific) and `__float128`*](https://stackoverflow.com/q/13516476) – Stack Overflow
- [*How to use GCC 4.6.0 libquadmath and `__float128` on x86 and x86_64*](https://stackoverflow.com/q/6457385) – Stack Overflow

:anchor:

- [*Additional floating types*](https://gcc.gnu.org/onlinedocs/gcc/Floating-Types.html) – GCC documentation

### Numeric limits

> The `std::numeric_limits` class template provides a standardized way to query various properties of arithmetic types.

:anchor:

- [*`std::numeric_limits`*](https://en.cppreference.com/w/cpp/types/numeric_limits) – C++ reference

#### `CHAR_BIT`

> Bit width of a byte.

:anchor:

- J.Bastien. [*There are exactly 8 bits in a byte*](https://wg21.link/p3477) – WG21/P3477

### Trivial and POD types

:link:

- [*Trivial, standard-layout, POD, and literal types*](https://docs.microsoft.com/en-us/cpp/cpp/trivial-standard-layout-and-pod-types?view=vs-2019) – Visual C++ language reference (2018)
- [*Trivial vs. standard layout vs. POD*](https://stackoverflow.com/q/6496545) – Stack Overflow

### Pointer and array types

:grey_question:

- [*Can C arrays contain padding in between elements?*](https://stackoverflow.com/q/1066681) – Stack Overflow
- [*One-dimensional access to a multidimensional array: is it well-defined behaviour?*](https://stackoverflow.com/q/6290956) – Stack Overflow

:movie_camera:

- M.Shah. [*Back to basics: Pointers*](https://www.youtube.com/watch?v=0zd8eznWv4k) – CppCon (2021)
- B.Saks. [*Back to basics: Pointers and memory*](https://www.youtube.com/watch?v=rqVWj0aVSxg) – CppCon (2020)

#### Null pointers

:anchor:

- [*Null pointers*](https://c-faq.com/null/) – C programming FAQs

### Class types

:grey_question:

- [*Is C++ allowed to increase the derived class size if there are no new member variables compared to the base class?*](https://stackoverflow.com/q/19949737) – Stack Overflow

:movie_camera:

- R.Powell. [*Intro to the C++ object model*](https://www.youtube.com/watch?v=iLiDezv_Frk) – CppCon (2015)

:anchor:

- [*Class declaration*](https://en.cppreference.com/w/cpp/language/class) – C++ reference

#### Destructors

:link:

- A.Fertig. [*When an empty destructor is required*](https://andreasfertig.blog/2023/12/when-an-empty-destructor-is-required/) (2023)
- A.Fertig. [*Why you shouldn’t provide an empty destructor*](https://andreasfertig.blog/2023/11/why-you-shouldnt-provide-an-empty-destructor/) (2023)

:grey_question:

- [*Significance of trivial destruction*](https://stackoverflow.com/q/41897418) – Stack Overflow

:anchor:

- [*Destructors*](https://en.cppreference.com/w/cpp/language/destructor) – C++ reference

#### Layout

:link:

- S.Dargo. [*Make declaration order layout mandated*](https://www.sandordargo.com/blog/2022/05/04/cpp23-P1847R4-Make-declaration-order-mandated) (2022)
- E.S.Raymond. [*The lost art of structure packing*](http://www.catb.org/esr/structure-packing/)
- E.Bendersky. [*Dumping a C++ object’s memory layout with Clang*](https://eli.thegreenplace.net/2012/12/17/dumping-a-c-objects-memory-layout-with-clang/) (2012)

:grey_question:

- [*Structure padding and packing*](https://stackoverflow.com/q/4306186) – Stack Overflow
- [*Passing reference of packed `struct` member to template – GCC bug?*](https://stackoverflow.com/q/29340160) – Stack Overflow

:movie_camera:

- S.Dewhurst. [*Back to basics: Class layout*](https://www.youtube.com/watch?v=SShSV_iV1Ko) – CppCon (2020)

:anchor:

- [*C++ named requirements: `StandardLayoutType`*](https://en.cppreference.com/w/cpp/named_req/StandardLayoutType) – C++ reference
- [*`std::is_standard_layout`*](https://en.cppreference.com/w/cpp/types/is_standard_layout) – C++ reference
- [*`std::has_unique_object_representations`*](https://en.cppreference.com/w/cpp/types/has_unique_object_representations) – C++ reference
- P.Balog. [*Make declaration order layout mandated*](https://wg21.link/p1847) – WG21/P1847

#### Member functions

See [Functions and function objects – *Member functions*](#member-functions).

#### Polymorphism and inheritance

See also [*Implementation of inheritance* – ABI and implementation](#implementation-of-inheritance).

:link:

- S.Pamudurthy. [*Polymorphism in C++ – A type compatibility view*](https://accu.org/journals/overload/26/148/james_2586/) – [Overload **141**](https://accu.org/journals/overload/overload141) (2017)
- E.de Vries. [*Memory layout for multiple and virtual inheritance*](https://web.archive.org/web/20160413064252/http://www.phpcompiler.org/articles/virtualinheritance.html) (2006)

:grey_question:

- [*Inheritance — Multiple and virtual inheritance*](https://isocpp.org/wiki/faq/multiple-inheritance) – C++ FAQ

:movie_camera

- I.Bogosavljevic. [*The hidden performance price of C++ virtual functions*](https://www.youtube.com/watch?v=n6PvvE_tEPk) – CppCon (2022)

:book:

- Ch. 1: *Inheritance*, Ch. 2: *Multiple inheritance* – N.Llopis. *C++ for game programmers* – Charles River Media (2003)

### Union types

:grey_question:

- B.Stroustrup. [*unions (generalized)*](https://www.stroustrup.com/C++11FAQ.html#unions) – C++11 - the new ISO C++ standard

:anchor:

- [*Union declaration*](https://en.cppreference.com/w/cpp/language/union) – C++ reference

### Function types

:anchor:

- A.Meredith. [*Abominable function types*](https://wg21.link/p0172) – WG21/P0172

### References

:grey_question:

- [*Is null reference possible?*](https://stackoverflow.com/q/4364536) – Stack Overflow

#### Lifetime of a temporary

:link:

- T.Winters. [TotW #107: *Reference lifetime extension*`](https://abseil.io/tips/107) – Abseil C++ Tips (2015)

:grey_question:

- [*Does a `const` reference class member prolong the life of a temporary?*](https://stackoverflow.com/q/2784262) – Stack Overflow

:movie_camera

- A.Schödl. [*The C++ rvalue lifetime disaster*](https://www.youtube.com/watch?v=s9vBk5CxFyY) – CoreHard (2019)

:anchor:

- [*Lifetime of a temporary*](https://en.cppreference.com/w/cpp/language/reference_initialization#Lifetime_of_a_temporary) – C++ reference

#### Rvalue references, universal references, and move semantics

See also [*Move semantics* – Patterns, idioms, and design principles](patterns_and_idioms.md#move-semantics).

:link:

- R.Chen. [*On harmful overuse of `std::move`*](https://devblogs.microsoft.com/oldnewthing/20231124-00/?p=109059) (2023)
- A.O’Dwyer. [*Don’t `forward things` that aren’t forwarding references*](https://quuxplusone.github.io/blog/2023/05/27/dont-forward-non-forwarding-references/) (2023)
- C.DaCamara. [*Improving the state of debug performance in C++*](https://devblogs.microsoft.com/cppblog/improving-the-state-of-debug-performance-in-c/) (2022)
- J.M&uuml;ller. [*Implementation сhallenge: Replacing `std::move` and `std::forward`*](https://www.foonathan.net/2020/09/move-forward/) (2020)
- H.E.Hinnant et al. [*A brief introduction to rvalue references*](https://www.artima.com/cppsource/rvalue.html) (2008)
- [*Rvalue reference declarator: `&&`*](https://docs.microsoft.com/en-us/cpp/cpp/rvalue-reference-declarator-amp-amp) – Microsoft Visual C++ (2016)
- T.Becker. [*C++ rvalue references explained*](http://thbecker.net/articles/rvalue_references/section_01.html) (2013)
- S.Meyers. [*C++14 lambdas and perfect forwarding*](https://scottmeyers.blogspot.com/2013/05/c14-lambdas-and-perfect-forwarding.html) (2013)
- S.Meyers. [*Universal references in C++11*](https://accu.org/journals/overload/20/111/meyers_1887/) ([mirror](https://isocpp.org/blog/2012/11/universal-references-in-c11-scott-meyers)) – [Overload **111**](https://accu.org/journals/overload/overload111), 8 (2012)
- E.Bendersky. [*Understanding lvalues and rvalues in C and C++*](https://eli.thegreenplace.net/2011/12/15/understanding-lvalues-and-rvalues-in-c-and-c/) (2011)

:grey_question:

- [*What is move semantics?*](https://stackoverflow.com/q/3106110) – Stack Overflow
- [*Rvalues, lvalues and formal definitions*](https://stackoverflow.com/q/56716647) – Stack Overflow
- [*Pass by value vs pass by rvalue reference*](https://stackoverflow.com/q/37935393) – Stack Overflow
- [*Rvalues and move semantics with `return` statement*](https://stackoverflow.com/q/4986673) – Stack Overflow
- [*The implementation of `std::forward`*](https://stackoverflow.com/q/27501400) – Stack Overflow
- [*Advantages of using `forward`*](https://stackoverflow.com/q/3582001) – Stack Overflow
- [*Do rvalue references to `const` have any use?*](https://stackoverflow.com/q/4938875) – Stack Overflow
- [*What does `auto&&` tell us?*](https://stackoverflow.com/q/13230480/) – Stack Overflow

:movie_camera:

- A.Kirsh. [*To move or not to move: An interactive analysis*](https://www.youtube.com/watch?v=PuCWH5DXDBc) – CppNorth (2023)
- A.Fertig. [*Back to basics: Move semantics*](https://www.youtube.com/watch?v=knEaMpytRMA) – CppCon (2022)
- N.Josuttis. [*Back to basics: Move semantics*](https://www.youtube.com/watch?v=Bt3zcJZIalk) – CppCon (2021)
- N.Josuttis. [*The hidden secrets of move semantics*](https://www.youtube.com/watch?v=TFMKjL38xAI) – CppCon (2020)
- D.Olsen. [*Back to basics: Move semantics*](https://www.youtube.com/watch?v=ZG59Bqo7qX4) – CppCon (2020)
- K.Iglberger. *Back to basics: Move semantics.* [Part I](https://www.youtube.com/watch?v=St0MNEU5b0o), [Part II](https://www.youtube.com/watch?v=pIzaZbKUw2s) – CppCon (2019)
- A.Schödl. [*The C++ rvalue lifetime disaster*](https://www.youtube.com/watch?v=s9vBk5CxFyY) – CoreHard (2019)
- N.Josuttis. [*The nightmare of move semantics for trivial classes*](https://www.youtube.com/watch?v=PNRju6_yn3o) – CppCon (2017)

:anchor:

- B.Stroustrup. [*“New” value terminology*](http://www.stroustrup.com/terminology.pdf)

### Opaque typedefs

See [*Opaque typedef* – Patterns, idioms, and design principles](patterns_and_idioms.md#opaque-typedef-whole-value).

---

## Standards

### C++11

:grey_question:

- B.Stroustrup. [*C++11 - the new ISO C++ standard*](https://www.stroustrup.com/C++11FAQ.html)

### C++14

:link:

- M.Nelson. [*The C++14 standard: What you need to know*](https://www.drdobbs.com/cpp/the-c14-standard-what-you-need-to-know/240169034) – Dr.Dobb’s Journal (2014)
- A.Krzemie&nacute;ski. [`constexpr` function is not `const`](https://akrzemi1.wordpress.com/2013/06/20/constexpr-function-is-not-const/) (2013)

### C++17

:movie_camera:

- N.Josuttis. [*C++17 : The biggest traps*](https://www.youtube.com/watch?v=mAZyaAo3M70) – C++ on Sea (2019)
- N.Josuttis. [*C++17 – The best features*](https://www.youtube.com/watch?v=e2ZQyYr0Oi0) - ACCU (2018)
- B.A.Lelbach. *C++17 features.* [Part I](https://www.youtube.com/watch?v=fI2xiUqqH3Q), [Part II](https://www.youtube.com/watch?v=qjxBKINAWk0) – CppCon (2017)
- A.Meredith. *C++17 in breadth (not depth).* [Part I](https://www.youtube.com/watch?v=22jIHfvelZk), [Part II](https://www.youtube.com/watch?v=-rIixnNJM4k) – CppCon (2016)

:anchor:

- [*C++17 compiler support*](https://en.cppreference.com/w/cpp/compiler_support#cpp17) – C++ reference

### C++20

:link:

- S.Dargo. [*My first work experience with C++20*](https://www.sandordargo.com/blog/2022/04/13/first-company-project-experience-with-cpp20) (2022)

:movie_camera:

- A.Williams. [*An introduction to multithreading in C++20*](https://www.youtube.com/watch?v=A7sVFJLJM-A) – CppCon (2022)
- N.Josuttis. [*C++20: My favourite code examples*](https://www.youtube.com/watch?v=UCIKbUvEKfI) – ACCU (2022)
- N.Josuttis. [*C++20: My favourite code examples*](https://www.youtube.com/watch?v=ey4pTOfdi9k) – Meeting C++ (2021)
- B.Deane. [*C++20 lambdas: Familiar template syntax*](https://www.youtube.com/watch?v=uOc6RPu9-CA) – CppCon (2020)
- F.Cooper. [*C++20: All the small things*](https://www.youtube.com/watch?v=LL_NrM7MY44) – C++ on Sea (2020)
- B.Stroustrup. [*C++20: C++ at 40*](https://www.youtube.com/watch?v=u_ij0YNkFUs) – CppCon (2019)
- A.Meredith. [*How C++20 can simplify `std::tuple`*](https://www.youtube.com/watch?v=SvxBvSK4i4k) – ACCU (2019)

:anchor:

- [*Compiler support for C++20*](https://en.cppreference.com/w/cpp/compiler_support/20) – C++ reference

### C++23

:movie_camera:

- M.Gregoire. [*C++23: An overview of almost all new and updated features*](https://www.youtube.com/watch?v=Cttb8vMuq-Y) – CppCon (2023)

:anchor:

- [*Compiler support for C++23*](https://en.cppreference.com/w/cpp/compiler_support/23) – C++ reference

---

## Tricks and subtleties

:link:

- A.O’Dwyer. [*Hidden `reinterpret_cast`s*](https://quuxplusone.github.io/blog/2020/01/22/expression-list-in-functional-cast/) (2020)

:grey_question:

- [*Hidden features of C++*](https://stackoverflow.com/q/75538) – Stack Overflow
- [*Why compilers test the least significant bit in an address?*](https://stackoverflow.com/q/53421279) – Stack Overflow
- [*Why does the size of class in C++ depend on the `public`/`private` status of data members?*](https://stackoverflow.com/q/58960303) – Stack Overflow
- [*Difference between `struct` and `typedef struct` in C++?*](https://stackoverflow.com/q/612328) – Stack Overflow
- [*What are “extern char condition tricks”?*](https://stackoverflow.com/q/70818988) – Stack Overflow
- [*Why can I use scalar type as the return type of `operator->`?*](https://stackoverflow.com/q/70773154/) – Stack Overflow
- [*What is the worst real-world macros/pre-processor abuse you’ve ever come across?*](https://stackoverflow.com/q/652788/) – Stack Overflow

:movie_camera:

- J.Bastien. [*`*(char*)0 = 0;`*](https://www.youtube.com/watch?v=dFIqNZ8VbRY) – C++ on Sea (2023)
- J.M&uuml;ller . [*C++ features you might not know*](https://www.youtube.com/watch?v=zGWj7Qo_POY) – C++ on Sea (2023)
- M.Kruse. [*`v.~uint32_t();`*](https://www.youtube.com/watch?v=Pf8gDb-j4wQ) – CppCon (2019)
- J.Wakely, M.Clow. [*These 10 tricks that only library implementors know!*](https://www.youtube.com/watch?v=wYd2V4nPn0E) – ACCU (2018)

### Accessing private and protected members

:link:

- J.Schaub. [*Access to private members. That’s easy!*](https://bloglitb.blogspot.com/2010/07/access-to-private-members-thats-easy.html) (2010))

:grey_question:

- [*Accessing private members*](https://stackoverflow.com/q/726096) – Stack Overflow

### Embedding binary data

:link:

- D.Weiler. [*incbin – Include binary files in C/C++*](https://github.com/graphitemaster/incbin)
- H.Landau. [*Embedding of binary data into programs*](https://www.devever.net/~hl/incbin)

:grey_question:

- [*Embedding resources in executable using GCC*](https://stackoverflow.com/q/4158900) – Stack Overflow

:anchor:

- J. Meneide. [*`std::embed`*](https://wg21.link/p1040) – WG21/P1040

---

## C, C vs C++

:link:

- A.Weissflog. [*Modern C for C++ peeps*](https://floooh.github.io/2019/09/27/modern-c-for-cpp-peeps.html) (2019)
- [*Linus Torvalds on C++*](http://harmful.cat-v.org/software/c++/linus) (2007)
- J.Nieminen. [*A response to Linus Torvalds on C++*](http://warp.povusers.org/OpenLetters/ResponseToTorvalds.html) (2007)
- D.R.Tribble. [*Incompatibilities between ISO C and ISO C++*](http://david.tribble.com/text/cdiffs.htm) (2001)

:grey_question:

- [*What are the fundamental differences between C and C++?*](https://softwareengineering.stackexchange.com/q/16390) – Software Engineering
- [*Why should we `typedef` a `struct` so often in C?*](https://stackoverflow.com/q/252780) – Stack Overflow
- [*Size of character (`'a'`) in C/C++*](https://stackoverflow.com/q/2172943)
- [*Is there any reason to use C++ instead of C, Perl, Python, etc.?*](https://softwareengineering.stackexchange.com/q/29109) – Software Engineering
- [*When to use C over C++, and C++ over C?*](https://softwareengineering.stackexchange.com/q/113295) – Software Engineering
- [*Is the C programming language still used?*](https://softwareengineering.stackexchange.com/q/103897) – Software Engineering

:movie_camera:

- D.Zalewski. [*C is great, long live C! Programming in modern C with a sneak peek into C23*](https://www.youtube.com/watch?v=lLv1s7rKeCM) – ACCU (2023)
- L.Sas. [*Modern C and what we can learn from it*](https://www.youtube.com/watch?v=QpAhX-gsHMs) – ACCU (2021)

:anchor:

- [*C programming FAQs*](https://c-faq.com/)

### Arrays

:book:

- Essay 1: *You must be joking* – P.J.Plauger. [*Programming on purpose III: Essays on software technology*](https://www.pearson.com/us/higher-education/program/Plauger-Programming-on-Purpose-III-Essays-on-Software-Technology/PGM133229.html) (1994)

### Functions

:link:

- A.Mertz. [*Calling C code from C++ with `extern “C”`*](https://arne-mertz.de/2018/10/calling-cpp-code-from-c-with-extern-c/) (2018)

:grey_question:

- [*Call a C function from C++ code*](https://stackoverflow.com/q/16850992) – Stack Overflow
- [*What kinds of C++ functions can be placed in a C function pointer?*](https://stackoverflow.com/q/36941866) – Stack Overflow
- [*Passing lambdas as callbacks to C functions*](https://stackoverflow.com/questions/55395717) – Stack Overflow
- [*How to make a function with C-linkage from template?*](https://stackoverflow.com/q/26174510) – Stack Overflow
- [*What is the difference between `function()` and `function(void)`?*](https://softwareengineering.stackexchange.com/q/286490) – Software Engineering

### Static variables

:grey_question:

- [*Difference between initialization of static variables in C and C++*](https://stackoverflow.com/q/5921920) – Stack Overflow

### Conditional operator

:link:

- P.Becker. [*Questions & Answers*](https://github.com/eugnsp/CUJ/blob/master/16.01/becker/becker.md#conditional-operator) – C/C++ Users Journal **16** (1998)

:grey_question:

- [*Conditional operator differences between C and C++*](https://stackoverflow.com/q/1082655) – Stack Overflow

<!-- https://sites.google.com/site/grprakash2/confusion -->

<!-- P1839R0 -->

<!-- https://stackoverflow.com/questions/1613341/what-do-the-following-phrases-mean-in-c-zero-default-and-value-initializat

https://stackoverflow.com/questions/37618213/when-is-a-private-constructor-not-a-private-constructor
-->



<!-- https://stackoverflow.com/questions/81870/is-it-possible-to-print-a-variables-type-in-standard-c/56766138#56766138 -->
