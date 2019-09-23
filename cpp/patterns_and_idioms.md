# Patterns, idioms, and design principles

## Table of contents

* [Introduction](#introduction)
* [Adapter](#adapter)
* [Bridge and pimpl](#bridge-and-pimpl)
* [Curiously recurring template](#curiously-recurring-template)
* [Double-checked locking](#double-checked-locking)
* [Execute-around](#execute-around)
	* [Execute-around object](execute-around-object)
	* [Execute-around proxy](execute-around-proxy)
	* [Execute-around pointer](execute-around-pointer)
	* [Execute-around function](execute-around-function)
* [Opaque typedefs](#opaque-typedefs)
* [Passkey](#passkey)
* [Whole value](#whole-value)
* [Design principles](#design-principles)
	* [Class design](#class-design)

---

## Introduction

:link:

* [*Design patterns*](https://en.wikipedia.org/wiki/Design_Patterns) &ndash; Wikipedia

---

## Adapter

:link:

* [*Adapter pattern*](https://en.wikipedia.org/wiki/Adapter_pattern) &ndash; Wikipedia

:movie_camera:

* [*Adapter design pattern*](https://www.youtube.com/watch?v=9jIgSsIfh_8) &ndash; D.Banas

---

## Bridge and pimpl

:link:

* [*Bridge pattern*](https://en.wikipedia.org/wiki/Bridge_pattern) &ndash; Wikipedia

:movie_camera:

* D.Schmidt. [*The composite and bridge patterns*](https://www.youtube.com/watch?v=iM4W5hFqaEA&t=730)
* D.Banas. [*Bridge design pattern*](https://www.youtube.com/watch?v=qG286LQM6BU)

---

## Curiously recurring template

:link:

* [*Curiously recurring template pattern*](https://en.wikipedia.org/wiki/Curiously_recurring_template_pattern) &ndash; Wikipedia
* J.Coplien. [*Curiously recurring template patterns*](https://sites.google.com/a/gertrudandcope.com/info/Publications/InheritedTemplate.pdf) &ndash; C++ Report (1995)

---

## Double-checked locking

:memo:

* See also [Multithreading &ndash; Concurrency and parallelism](concurrency_and_parallelism.md#multithreading).

:link:

* [*Double-checked locking*](https://en.wikipedia.org/wiki/Double-checked_locking) &ndash; Wikipedia

:movie_camera:

* F.Pikus. [*Live lock-free or deadlock (practical lock-free programming), Part I*](https://www.youtube.com/watch?v=lVBvHbJsg5Y) &ndash; CppCon (2015)

---

## Execute-around

:link:

* K.Henney. [*C++ patterns: Executing around sequences*](https://hillside.net/europlop/HillsideEurope/Papers/EuroPLoP2000/2000_Henney_ExecutingAroundSequences.pdf) &ndash; EuroPLoP (2000)

### Execute-around object

> Execute-around object idiom abstracts the execution of a pair of actions that surround a sequence of statements, or a single action that follows a sequence.

:memo:

* This idiom is also known by the name of Resource acquisition is initialization (RAII).
* An example of this idiom is provided by smart pointers, e.g. by `std::unique_ptr`. See [The standard library &ndash; Smart pointers](std_library.md#smart-pointers).

:link:

* [*Resource acquisition is initialization*](https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization) &ndash; Wikipedia
* [*RAII*](https://en.cppreference.com/w/cpp/language/raii) &ndash; C++ reference
* [*What is meant by Resource acquisition is initialization (RAII)?*](https://stackoverflow.com/questions/2321511/what-is-meant-by-resource-acquisition-is-initialization-raii) &ndash; Stack Overflow

<!-- https://www.codeproject.com/Articles/10141/RAII-Dynamic-Objects-and-Factories-in-C -->

### Execute-around proxy

> Execute-around proxy idiom applies execute-around object idiom for individual calls on an object.

### Execute-around pointer

> Execute-around pointer idiom defines an execute-around proxy idiom when the actions performed on a target object are the same for all functions.

:memo:

* This idiom can be used to "convert" a non-thread-safe class into a thread-safe one by automatically locking and unlocking a mutex when member functions are called.

:link:

* [*Execute-around pointer*](https://en.wikibooks.org/wiki/More_C%2B%2B_Idioms/Execute-Around_Pointer) &ndash; WikiBooks
* [*We make any object thread-safe*](https://www.codeproject.com/Articles/1183379/We-make-any-object-thread-safe) &ndash; CodeProject (2018)

### Execute-around function

> Execute-around function idiom safely groups and executes a sequence of statements that must be enclosed by a pair of actions, or followed by a single action.

---

## Opaque typedefs

:memo:

* See also [*Opaque typedefs* &ndash; Core language](core-language.md#opaque-typedefs).

:link:

* L.B&ouml;ger. [*Empty scoped enums as strong aliases for integral types*](https://accu.org/index.php/journals/2683) &ndash; Overload **152**, 9 (2019)
* J.Müller. [*Tutorial: Emulating strong/opaque typedefs in C++*](https://foonathan.net/blog/2016/10/19/strong-typedefs.html) &ndash; foonathan::blog() (2016)

---

## Passkey

:link:

<!-- https://stackoverflow.com/questions/3217390/clean-c-granular-friend-equivalent-answer-attorney-client-idiom/3218920#3218920-->

https://stackoverflow.com/questions/3324248/how-to-name-this-key-oriented-access-protection-pattern

* [*Is this key-oriented access-protection pattern a known idiom?*](https://stackoverflow.com/questions/3220009/is-this-key-oriented-access-protection-pattern-a-known-idiom) &ndash; Stack Overflow

---

## Whole value

> ```cpp
> class Whole_value {
> public:
>     explicit Whole_value(int v) : v_(v) {}
>     explicit operator int() const { return v_; }
> private:
>     int v_;
> };
> ```

:movie_camera:

* H.Matthews. [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScst=975) &ndash; ACCU (2017)

---

## Design principles

:link:

* R.C.Martin. [*The principles of OOD*](http://www.butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod) &ndash; Uncle Bob (2004)

### Class design

> The five principles of class design [R.C.Martin]:
>
> 1. Single responsibility principle: a class should have one, and only one, reason to change.
> 2. Open-closed principle: you should be able to extend a class behavior, without modifying it.
> 3. Liskov substitution principle: derived classes must be substitutable for their base classes.
> 4. Interface segregation principle: make fine grained interfaces that are client specific.
> 5. Dependency inversion principle: depend on abstractions, not on concretions.

:link:

* [*SOLID*](https://en.wikipedia.org/wiki/SOLID) &ndash; Wikipedia
* R.C.Martin. [*Design principles and design patterns*](http://www.cvc.uab.es/shared/teach/a21291/temes/object_oriented_design/materials_adicionals/principles_and_patterns.pdf)
* R.C.Martin. [*Single responsibility principle*](https://web.archive.org/web/20150202200348/http://www.objectmentor.com/resources/articles/srp.pdf)
* R.C.Martin. [*Open-closed principle*](https://web.archive.org/web/20150905081105/http://www.objectmentor.com/resources/articles/ocp.pdf)
* R.C.Martin. [*Liskov substitution principle*](https://web.archive.org/web/20150905081111/http://www.objectmentor.com/resources/articles/lsp.pdf)
* R.C.Martin. [*Interface segregation principle*](https://web.archive.org/web/20150905081110/http://www.objectmentor.com/resources/articles/isp.pdf)
* R.C.Martin. [*Dependency inversion principle*](https://web.archive.org/web/20150905081103/http://www.objectmentor.com/resources/articles/dip.pdf)
