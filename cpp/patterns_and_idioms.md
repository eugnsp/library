# Patterns, idioms, and design principles

## Table of contents

* [Introduction](#introduction)
* [Adapter](#adapter)
* [Bridge and pimpl](#bridge-and-pimpl)
* [Double-checked locking](#double-checked-locking)
* [Opaque typedefs](#opaque-typedefs)
* [Passkey](#passkey)
* [Design principles](#design-principles)
	* [Class design](#class-design)

---

## Introduction

:link:

* [Design patterns &ndash; Wikipedia](https://en.wikipedia.org/wiki/Design_Patterns)

---

## Adapter

:link:

* [Adapter pattern &ndash; Wikipedia](https://en.wikipedia.org/wiki/Adapter_pattern)

:movie_camera:

* *Adapter design pattern* &ndash; D.Banas\
[Watch at YouTube](https://www.youtube.com/watch?v=9jIgSsIfh_8)

---

## Bridge and pimpl

:link:

* [Bridge pattern &ndash; Wikipedia](https://en.wikipedia.org/wiki/Bridge_pattern)

:movie_camera:

* *The composite and bridge patterns* &ndash; D.Schmidt\
[Watch at YouTube](https://www.youtube.com/watch?v=iM4W5hFqaEA&t=730) (from 12:11)
* *Bridge design pattern* &ndash; D.Banas\
[Watch at YouTube](https://www.youtube.com/watch?v=qG286LQM6BU)

---

## Double-checked locking

:memo:

* See also [*Concurrency and parallelism* &ndash; Multithreading](concurrency_and_parallelism.md#multithreading).

:link:

* [*Double-checked locking* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Double-checked_locking)

:movie_camera:

* *Live lock-free or deadlock (practical lock-free programming), Part I* &ndash; F.Pikus @ CppCon (2015).\
[Watch at YouTube](https://www.youtube.com/watch?v=lVBvHbJsg5Y)

---

## Opaque typedefs

:memo:

* See also [Core language &ndash; Opaque typedefs](core-language.md#opaque-typedefs).

:link:

* [*Tutorial: Emulating strong/opaque typedefs in C++* &ndash; J.Müller, foonathan::blog() (2016)](https://foonathan.net/blog/2016/10/19/strong-typedefs.html)

---

## Passkey

:link:

<!-- https://stackoverflow.com/questions/3217390/clean-c-granular-friend-equivalent-answer-attorney-client-idiom/3218920#3218920-->

https://stackoverflow.com/questions/3324248/how-to-name-this-key-oriented-access-protection-pattern

* [Is this key-oriented access-protection pattern a known idiom? &ndash; Stack Overflow](https://stackoverflow.com/questions/3220009/is-this-key-oriented-access-protection-pattern-a-known-idiom)

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
