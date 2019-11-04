# Patterns, idioms, and design principles <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction](#introduction)
- [Design principles](#design-principles)
	- [Class design](#class-design)
		- [Destructors](#destructors)
		- [Rule of zero/three/five](#rule-of-zerothreefive)
		- [SOLID principles](#solid-principles)
	- [Guidelines](#guidelines)
- [Patterns and idioms](#patterns-and-idioms)
	- [Adapter](#adapter)
	- [Bridge and pimpl](#bridge-and-pimpl)
	- [Builder](#builder)
	- [Copy-and-swap](#copy-and-swap)
	- [Curiously recurring template](#curiously-recurring-template)
	- [Double-checked locking](#double-checked-locking)
	- [Execute-around](#execute-around)
		- [Execute-around object](#execute-around-object)
		- [Execute-around proxy](#execute-around-proxy)
		- [Execute-around pointer](#execute-around-pointer)
		- [Execute-around function](#execute-around-function)
	- [Opaque typedef (whole value)](#opaque-typedef-whole-value)
	- [Passkey](#passkey)
	- [Strategy](#strategy)
	- [Visitor](#visitor)

---

## Introduction

:link:

- [*Design patterns*](https://en.wikipedia.org/wiki/Design_Patterns) &ndash; Wikipedia

## Design principles

:movie_camera:

- F.Pikus. [*Design for performance*](https://www.youtube.com/watch?v=m25p3EtBua4) &ndash; CppCon (2018)

### Class design

:link:

- R.C.Martin. [*The principles of OOD*](http://www.butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod) &ndash; Uncle Bob (2004)

:movie_camera:

- J.Kalb. [*Back to basics: Object-oriented programming*](https://www.youtube.com/watch?v=32tDTD9UJCE) &ndash; CppCon (2018)

:book:

- Sec.: *Class design and inheritance* &ndash; H.Sutter, A.Alexandrescu. [*C++ coding standards: 101 rules, guidelines, and best practices*](http://www.gotw.ca/publications/c++cs.htm) &ndash; [Addison-Wesley Professional](https://www.pearson.com/us/higher-education/program/Sutter-C-Coding-Standards-101-Rules-Guidelines-and-Best-Practices/PGM147301.html) (2004)

#### Destructors

:link:

- A.Krzemie&nacute;ski. [*Destructors that throw*](https://akrzemi1.wordpress.com/2011/09/21/destructors-that-throw/) (2011)
- B.Kolpackov. [*Throwing destructors*](https://www.kolpackov.net/projects/c++/eh/dtor-1.xhtml) (2004)

:movie_camera:

- P.Isensee. [*Destructor case studies: Best practices for safe and efficient teardown*](https://www.youtube.com/watch?v=XvWyLAW_U0Q) &ndash; CppCon (2019)

#### Rule of zero/three/five

> The rule of zero: if a class requires no user-defined constructors, no user-defined assignment operators and no user-defined destructor, avoid defining them.\
> The rule of three/five: if a class requires a user-defined destructor, a user-defined copy (and move) constructor, or a user-defined copy (and move) assignment operator, it almost certainly requires all three (five).

:link:

- [*Rule of three*](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) &ndash; Wikipedia
- S.Meyers. [*A concern about the rule of zero*](https://scottmeyers.blogspot.com/2014/03/a-concern-about-rule-of-zero.html) (2014)
- R.M.Fernandes. [*Rule of zero*](https://web.archive.org/web/20121127171954/http://rmartinho.github.com/cxx11/2012/08/15/rule-of-zero.html) (2012)

:anchor:

- [*The rule of three/five/zero*](https://en.cppreference.com/w/cpp/language/rule_of_three) &ndash; C++ reference

#### SOLID principles

> SOLID are the five principles of class design:
>
> 1. Single responsibility principle: a class should have one, and only one, reason to change.
> 2. Open-closed principle: you should be able to extend a class behavior, without modifying it.
> 3. Liskov substitution principle: derived classes must be substitutable for their base classes.
> 4. Interface segregation principle: make fine grained interfaces that are client specific.
> 5. Dependency inversion principle: depend on abstractions, not on concretions.

:link:

- [*SOLID*](https://en.wikipedia.org/wiki/SOLID) &ndash; Wikipedia
- R.C.Martin. [*Design principles and design patterns*](http://www.cvc.uab.es/shared/teach/a21291/temes/object_oriented_design/materials_adicionals/principles_and_patterns.pdf)
- R.C.Martin. SOLID: [*Single responsibility principle*](https://web.archive.org/web/20150202200348/http://www.objectmentor.com/resources/articles/srp.pdf), [*Open-closed principle*](https://web.archive.org/web/20150905081105/http://www.objectmentor.com/resources/articles/ocp.pdf), [*Liskov substitution principle*](https://web.archive.org/web/20150905081111/http://www.objectmentor.com/resources/articles/lsp.pdf), [*Interface segregation principle*](https://web.archive.org/web/20150905081110/http://www.objectmentor.com/resources/articles/isp.pdf), [*Dependency inversion principle*](https://web.archive.org/web/20150905081103/http://www.objectmentor.com/resources/articles/dip.pdf)

### Guidelines

- [*C++ core guidelines*](https://github.com/isocpp/CppCoreGuidelines)
- [*Standard library guidelines*](https://github.com/cplusplus/LEWG/blob/master/library-design-guidelines.md)
- [*Google C++ style guide*](https://google.github.io/styleguide/cppguide.html)

:movie_camera:

- B.Stroustrup. [*Writing good C++14*](https://www.youtube.com/watch?v=1OEu9C51K2A) &ndash; CppCon (2015)
- H.Sutter. [*Back to the basics! Essentials of modern C++ style*](https://www.youtube.com/watch?v=xnqTKD8uD64) &ndash; CppCon (2014)

---

## Patterns and idioms

> A design pattern is a general technique used to solve a class of related problems.

:movie_camera:

* F.Pikus. [*C++ design patterns: From C++03 to C++17*](https://www.youtube.com/watch?v=MdtYi0vvct0) &ndash; CppCon (2019)

### Adapter

:link:

- [*Adapter pattern*](https://en.wikipedia.org/wiki/Adapter_pattern) &ndash; Wikipedia

:movie_camera:

- [*Adapter design pattern*](https://www.youtube.com/watch?v=9jIgSsIfh_8) &ndash; D.Banas

### Bridge and pimpl

:link:

- [*Bridge pattern*](https://en.wikipedia.org/wiki/Bridge_pattern) &ndash; Wikipedia

:movie_camera:

- D.Schmidt. [*The composite and bridge patterns*](https://www.youtube.com/watch?v=iM4W5hFqaEA&t=730)
- D.Banas. [*Bridge design pattern*](https://www.youtube.com/watch?v=qG286LQM6BU)

### Builder

> The builder pattern separates the creation of an object from its representation. It is used to create complex objects that are built in multiple stages:
> ```cpp
> struct Builder {
>     Builder(...);
>     Builder& add(...) { ...; return *this; }
>     operator Product() const;
> };
>
> Product pr = Builder(...).add(...).add(...).add(...);

:link:

- [*Builder pattern*](https://en.wikipedia.org/wiki/Builder_pattern) &ndash; Wikipedia

### Copy-and-swap

:link:

- [*What is the copy-and-swap idiom?*](https://stackoverflow.com/questions/3279543/what-is-the-copy-and-swap-idiom) &ndash; Stack Overflow

### Curiously recurring template

> The curiously recurring template pattern (CRTP) is an idiom in which a class `X` derives from a class template using `X` itself as template parameter:
> ```cpp
> template<class Derived> struct Base {
>     void foo() { static_cast<Derived*>(this)->foo(); }
> };
>
> struct X : Base<X> {
>     void foo();
> }
> ```

:link:

- [*Curiously recurring template pattern*](https://en.wikipedia.org/wiki/Curiously_recurring_template_pattern) &ndash; Wikipedia
- J.Coplien. [*Curiously recurring template patterns*](https://sites.google.com/a/gertrudandcope.com/info/Publications/InheritedTemplate.pdf) &ndash; C++ Report (1995)
- [*What is the curiously recurring template pattern?*](https://stackoverflow.com/questions/4173254/what-is-the-curiously-recurring-template-pattern-crtp) &ndash; Stack Overflow

### Double-checked locking

See also [*Multithreading* &ndash; Concurrency and parallelism](concurrency_and_parallelism.md#multithreading).

:link:

- [*Double-checked locking*](https://en.wikipedia.org/wiki/Double-checked_locking) &ndash; Wikipedia

:movie_camera:

- F.Pikus. [*Live lock-free or deadlock (practical lock-free programming). Part I*](https://www.youtube.com/watch?v=lVBvHbJsg5Y) &ndash; CppCon (2015)

### Execute-around

:link:

- K.Henney. [*C++ patterns: Executing around sequences*](https://hillside.net/europlop/HillsideEurope/Papers/EuroPLoP2000/2000_Henney_ExecutingAroundSequences.pdf) &ndash; EuroPLoP (2000)

#### Execute-around object

> Execute-around object idiom abstracts the execution of a pair of actions that surround a sequence of statements, or a single action that follows a sequence. This idiom is also known by the name of scope guard and resource acquisition is initialization (RAII).

:memo:

- An example of this idiom is provided by smart pointers, e.g. by `std::unique_ptr`. See [The standard library &ndash; Smart pointers](std_library.md#smart-pointers).

:link:

- [*Resource acquisition is initialization*](https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization) &ndash; Wikipedia
- [*RAII*](https://en.cppreference.com/w/cpp/language/raii) &ndash; C++ reference
- [*What is meant by Resource acquisition is initialization (RAII)?*](https://stackoverflow.com/questions/2321511/what-is-meant-by-resource-acquisition-is-initialization-raii) &ndash; Stack Overflow

<!-- https://www.codeproject.com/Articles/10141/RAII-Dynamic-Objects-and-Factories-in-C -->

#### Execute-around proxy

> Execute-around proxy idiom applies execute-around object idiom for individual calls on an object.

#### Execute-around pointer

> Execute-around pointer idiom defines an execute-around proxy idiom when the actions performed on a target object are the same for all functions.

:memo:

- This idiom can be used to “convert” a non-thread-safe class into a thread-safe one by automatically locking and unlocking a mutex when member functions are called.

:link:

- [*Execute-around pointer*](https://en.wikibooks.org/wiki/More_C%2B%2B_Idioms/Execute-Around_Pointer) &ndash; WikiBooks
- [*We make any object thread-safe*](https://www.codeproject.com/Articles/1183379/We-make-any-object-thread-safe) &ndash; CodeProject (2018)

#### Execute-around function

> Execute-around function idiom safely groups and executes a sequence of statements that must be enclosed by a pair of actions, or followed by a single action.

### Opaque typedef (whole value)

> ```cpp
> class Whole_value {
> public:
>     Whole_value(int v) : v_(v) {}
>     operator int() const { return v_; }
> private:
>     int v_;
> };
> ```

See also [*Opaque typedefs* &ndash; Core language](core-language.md#opaque-typedefs).

:link:

- L.B&ouml;ger. [*Empty scoped enums as strong aliases for integral types*](https://accu.org/index.php/journals/2683) &ndash; Overload **152**, 9 (2019)
- J.M&uuml;ller. [*Tutorial: Emulating strong/opaque typedefs in C++*](https://foonathan.net/2016/10/strong-typedefs/) (2016)

:movie_camera:

- H.Matthews. [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScst=975) &ndash; ACCU (2017)

### Passkey

:link:

<!-- https://stackoverflow.com/questions/3217390/clean-c-granular-friend-equivalent-answer-attorney-client-idiom/3218920#3218920-->

<!-- https://stackoverflow.com/questions/3324248/how-to-name-this-key-oriented-access-protection-pattern -->

- [*Is this key-oriented access-protection pattern a known idiom?*](https://stackoverflow.com/questions/3220009/is-this-key-oriented-access-protection-pattern-a-known-idiom) &ndash; Stack Overflow

### Strategy

> The strategy pattern enables run-time selection of an algorithm for a particular behaviour. This pattern is also known by the name of policy pattern.

### Visitor

> The visitor pattern separates an algorithm from an object structure, which is the data for this algorithm.

:link:

- [*Visitor pattern*](https://en.wikipedia.org/wiki/Visitor_pattern) &ndash; Wikipedia
- [*When should I use the Visitor design pattern?*](https://stackoverflow.com/questions/255214/when-should-i-use-the-visitor-design-pattern) &ndash; Stack Overflow

:movie_camera:

- B.Kannan. [*Generalised double dispatch*](https://www.youtube.com/watch?v=nNqiBasCab4) &ndash; CppCon (2019)
