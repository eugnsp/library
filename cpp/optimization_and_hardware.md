# Optimization and hardware

## Table of contents

* [Introduction and overview](#introduction-and-overview)
* [CPU](#cpu)
* [Memory and cache](#memory-and-cache)
	* [Allocation](#allocation
	* [Relocation](#relocation)

---

## Introduction and overview

:movie_camera:

* H.Matthews. [*Optimising a small real-world C++ application*](https://www.youtube.com/watch?v=fDlE93hs_-U) &ndash; ACCU (2019)
* A.Alexandrescu. [*Speed is found in the minds of people*](https://www.youtube.com/watch?v=FJJTYQYB1JQ) &ndash; CppCon (2019)
* J.Regehr. [*Undefined behavior and compiler optimizations*](https://www.youtube.com/watch?v=AeEwxtEOgH0) &ndash; C++ Now (2018)
* H.Matthews. [*Optimising a small real-world C++ application*](https://www.youtube.com/watch?v=IGFBCvroXJ8) &ndash; NDC (2018)
* H.Matthews. [*C++ performance and optimisation*](https://www.youtube.com/watch?v=eICYHA-eyXM) &ndash; NDC (2017)
* C.Cook. [*The speed game: Automated trading systems in C++*](https://www.youtube.com/watch?v=ulOLGX3HNCI) &ndash; Meeting C++ (2016)
* C.Carruth. [*Understanding compiler optimization*](https://www.youtube.com/watch?v=haQ2cijhvhE) &ndash; code::dive (2016)
* A.Alexandrescu. [*Optimization tips*](https://www.youtube.com/watch?v=Qq_WaiwzOtI) &ndash; CppCon (2014)

---

# CPU

:movie_camera:

* C.Bay. [*The CPU cache: Instruction re-ordering made obvious*](https://www.youtube.com/watch?v=tNkVUIv2gEE) &ndash; C++Now (2016)
* M.Godbolt. [*x86 internals for fun & profit*](https://www.youtube.com/watch?v=hgcNM-6wr34) &ndash; GOTO (2014)

## Memory and cache

:link:

* U.Drepper. [*What every programmer should know about memory*](https://people.freebsd.org/~lstewart/articles/cpumemory.pdf) (2007)

:movie_camera:

* T.Doumler. [*Want fast C++? Know your hardware!*](https://www.youtube.com/watch?v=BP6NxVxDQIs) &ndash; CppCon (2016)
* S.Meyers. [*CPU caches and why you care*](https://www.youtube.com/watch?v=WDIkqP4JbkE) &ndash; code::dive (2014)

---

## Optimization

:memo:

* For memory relocation see also [`[[trivially_relocatable]]` &ndash; Core language](core_language.md#triviallyrelocatable).

### Allocation

:movie_camera:

* A.Alexandrescu [`std::allocator` is to allocation what `std::vector` is to vexation](https://www.youtube.com/watch?v=LIb3L4vKZ7U) &ndash; CppCon (2015)

### Relocation

:link:

* A.O'Dwyer. [Announcing “trivially relocatable”](https://quuxplusone.github.io/blog/2018/07/18/announcing-trivially-relocatable/) (2018)

:movie_camera:

* A.O'Dwyer. [Trivially relocatable](https://www.youtube.com/watch?v=SGdfPextuAU) &ndash; C++Now (2019)

:anchor:

* A.O'Dwyer. [Object relocation in terms of move plus destroy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1144r2.html) &ndash; WG21/P1144R2 (2019)

<!-- https://www.airs.com/blog/archives/120
https://www.agner.org/optimize/optimizing_cpp.pdf
http://www.reedbeta.com/blog/data-oriented-hash-table/
 -->
