# Patterns, idioms, and design principles

## Table of contents

* [Introduction](#introduction)
* [Adapter](#adapter)
* [Bridge and pimpl](#bridge-and-pimpl)
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

* [*Design patterns* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Design_Patterns)

---

## Adapter

:link:

* [*Adapter pattern* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Adapter_pattern)

:movie_camera:

* [*Adapter design pattern* &ndash; D.Banas](https://www.youtube.com/watch?v=9jIgSsIfh_8)

---

## Bridge and pimpl

:link:

* [*Bridge pattern* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Bridge_pattern)

:movie_camera:

* [*The composite and bridge patterns* &ndash; D.Schmidt](https://www.youtube.com/watch?v=iM4W5hFqaEA&t=730)
* [*Bridge design pattern* &ndash; D.Banas](https://www.youtube.com/watch?v=qG286LQM6BU)

---

## Double-checked locking

:memo:

* See also [Multithreading &ndash; Concurrency and parallelism](concurrency_and_parallelism.md#multithreading).

:link:

* [*Double-checked locking* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Double-checked_locking)

:movie_camera:

* [*Live lock-free or deadlock (practical lock-free programming), Part I* &ndash; F.Pikus @ CppCon (2015)](https://www.youtube.com/watch?v=lVBvHbJsg5Y)

---

## Execute-around

:link:

* [*C++ patterns: Executing around sequences* &ndash; K.Henney, EuroPLoP (2000)](https://hillside.net/europlop/HillsideEurope/Papers/EuroPLoP2000/2000_Henney_ExecutingAroundSequences.pdf)

### Execute-around object

> Execute-around object idiom abstracts the execution of a pair of actions that surround a sequence of statements, or a single action that follows a sequence.

:memo:

* This idiom is also known by the name of Resource acquisition is initialization (RAII).
* An example of this idiom is provided by smart pointers, e.g. by `std::unique_ptr`. See [The standard library &ndash; Smart pointers](std_library.md#smart-pointers).

:link:

* [*Resource acquisition is initialization* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization)
* [*RAII* &ndash; C++ reference](https://en.cppreference.com/w/cpp/language/raii)
* [*What is meant by Resource acquisition is initialization (RAII)?* &ndash; Stack Overflow](https://stackoverflow.com/questions/2321511/what-is-meant-by-resource-acquisition-is-initialization-raii)

<!-- https://www.codeproject.com/Articles/10141/RAII-Dynamic-Objects-and-Factories-in-C -->

### Execute-around proxy

> Execute-around proxy idiom applies execute-around object idiom for individual calls on an object.

### Execute-around pointer

> Execute-around pointer idiom defines an execute-around proxy idiom when the actions performed on a target object are the same for all functions.

:memo:

* This idiom can be used to "convert" a non-thread-safe class into a thread-safe one by automatically locking and unlocking a mutex when member functions are called.

:link:

* [*Execute-around pointer* &ndash; WikiBooks](https://en.wikibooks.org/wiki/More_C%2B%2B_Idioms/Execute-Around_Pointer)
* [*We make any object thread-safe* &ndash; AlexeyAB, CodeProject (2018)](https://www.codeproject.com/Articles/1183379/We-make-any-object-thread-safe)

### Execute-around function

> Execute-around function idiom safely groups and executes a sequence of statements that must be enclosed by a pair of actions, or followed by a single action.

---

## Opaque typedefs

:memo:

* See also [*Opaque typedefs* &ndash; Core language](core-language.md#opaque-typedefs).

:link:

* [*Empty Scoped Enums as Strong Aliases for Integral Types* &ndash; L.B&ouml;ger, Overload **152**, 9 (2019)](https://accu.org/index.php/journals/2683)
* [*Tutorial: Emulating strong/opaque typedefs in C++* &ndash; J.Müller, foonathan::blog() (2016)](https://foonathan.net/blog/2016/10/19/strong-typedefs.html)

---

## Passkey

:link:

<!-- https://stackoverflow.com/questions/3217390/clean-c-granular-friend-equivalent-answer-attorney-client-idiom/3218920#3218920-->

https://stackoverflow.com/questions/3324248/how-to-name-this-key-oriented-access-protection-pattern

* [*Is this key-oriented access-protection pattern a known idiom?* &ndash; Stack Overflow](https://stackoverflow.com/questions/3220009/is-this-key-oriented-access-protection-pattern-a-known-idiom)

---

## Whole value

> A minimal example of the *"whole value"* pattern:
> ```cpp
> class Value {
> public:
>     explicit Value(int v) : v_(v) {}
>     operator int() const { return v_; }
> private:
>     int v_;
> };
> ```

---

## Design principles

:link:

* [*The principles of OOD* &ndash; R.C.Martin (2004)](http://www.butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod)

### Class design

> The five principles of class design [R.C.Martin]:
>
> 1. Single responsibility principle: a class should have one, and only one, reason to change.
> 2. Open-closed principle: you should be able to extend a class behavior, without modifying it.
> 3. Liskov substitution principle: derived classes must be substitutable for their base classes.
> 4. Interface segregation principle: make fine grained interfaces that are client specific.
> 5. Dependency inversion principle: depend on abstractions, not on concretions.

:link:

* [*SOLID* &ndash; Wikipedia](https://en.wikipedia.org/wiki/SOLID)
* [*Design principles and design patterns* &ndash; R.C.Martin (2000)](http://www.cvc.uab.es/shared/teach/a21291/temes/object_oriented_design/materials_adicionals/principles_and_patterns.pdf)
* [*Single responsibility principle* &ndash; R.C.Martin](https://web.archive.org/web/20150202200348/http://www.objectmentor.com/resources/articles/srp.pdf)
* [*Open-closed principle* &ndash; R.C.Martin](https://web.archive.org/web/20150905081105/http://www.objectmentor.com/resources/articles/ocp.pdf)
* [*Liskov substitution principle* &ndash; R.C.Martin](https://web.archive.org/web/20150905081111/http://www.objectmentor.com/resources/articles/lsp.pdf)
* [*Interface segregation principle* &ndash; R.C.Martin](https://web.archive.org/web/20150905081110/http://www.objectmentor.com/resources/articles/isp.pdf)
* [*Dependency inversion principle* &ndash; R.C.Martin](https://web.archive.org/web/20150905081103/http://www.objectmentor.com/resources/articles/dip.pdf)
