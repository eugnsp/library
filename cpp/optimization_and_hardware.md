# Optimization and hardware <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
- [Compiler optimizations](#compiler-optimizations)
	- [Heap allocation](#heap-allocation)
	- [Integeral division](#integeral-division)
	- [Return value optimization and copy elision](#return-value-optimization-and-copy-elision)
	- [Undefined behavior](#undefined-behavior)
		- [Strict aliasing rule](#strict-aliasing-rule)
- [CPU](#cpu)
	- [Memory and cache](#memory-and-cache)
		- [Allocation](#allocation)
		- [Relocation](#relocation)

---

## Introduction and overview

:link:

- [*Optimizing C++*](https://en.wikibooks.org/wiki/Optimizing_C%2B%2B) &ndash; WikiBooks

:movie_camera:

- H.Matthews. [*Optimising a small real-world C++ application*](https://www.youtube.com/watch?v=fDlE93hs_-U) &ndash; ACCU (2019)
- A.Alexandrescu. [*Speed is found in the minds of people*](https://www.youtube.com/watch?v=FJJTYQYB1JQ) &ndash; CppCon (2019)
- F.Pikus. [*Design for performance*](https://www.youtube.com/watch?v=m25p3EtBua4) &ndash; CppCon (2018)
- H.Matthews. [*Optimising a small real-world C++ application*](https://www.youtube.com/watch?v=IGFBCvroXJ8) &ndash; NDC (2018)
- H.Matthews. [*C++ performance and optimisation*](https://www.youtube.com/watch?v=eICYHA-eyXM) &ndash; NDC (2017)
- C.Cook. [*The speed game: Automated trading systems in C++*](https://www.youtube.com/watch?v=ulOLGX3HNCI) &ndash; Meeting C++ (2016)
- A.Alexandrescu. [*Optimization tips*](https://www.youtube.com/watch?v=Qq_WaiwzOtI) &ndash; CppCon (2014)

---

## Compiler optimizations

:link

- A.O’Dwyer. [*`[[trivial_abi]]` 101*](https://quuxplusone.github.io/blog/2018/05/02/trivial-abi-101/)
- [*Why does this loop produce “warning: iteration 3u invokes undefined behavior” and output more than 4 lines?*](https://stackoverflow.com/questions/24296571/why-does-this-loop-produce-warning-iteration-3u-invokes-undefined-behavior-an) &ndash; Stack Overflow

:movie_camera:

- C.Carruth. [*Understanding compiler optimization*](https://www.youtube.com/watch?v=haQ2cijhvhE) &ndash; code::dive (2016)

### Heap allocation

- [*Is the compiler allowed to optimize out heap memory allocations?*](https://stackoverflow.com/questions/31873616/is-the-compiler-allowed-to-optimize-out-heap-memory-allocations) &ndash; Stack Overflow

### Integeral division

:link:

- [*Why does GCC use multiplication by a strange number in implementing integer division?*](https://stackoverflow.com/questions/41183935/why-does-gcc-use-multiplication-by-a-strange-number-in-implementing-integer-divi) &ndash; Stack Overflow
- D.W.Jones. [*Reciprocal multiplication, a tutorial*](https://homepage.divms.uiowa.edu/~jones/bcd/divide.html) (1999)
- T.Granlund, P.L.Montgomery. [*Division by invariant integers using multiplication*](https://gmplib.org/~tege/divcnst-pldi94.pdf) (1994)

### Return value optimization and copy elision

:camera:

- J.Kalb. [*Copy elision*](https://www.youtube.com/watch?v=fSB57PiXpRw) &ndash; C++Now (2018)

:anchor:

- [*Copy elision*](https://en.cppreference.com/w/cpp/language/copy_elision) &ndash; C++ reference

### Undefined behavior

:link

- K.Walfridsson. [*How undefined signed overflow enables optimizations in GCC*](https://kristerw.blogspot.com/2016/02/how-undefined-signed-overflow-enables.html) (2016)
- J.Regehr. [*Finding undefined behavior bugs by finding dead code*](https://blog.regehr.org/archives/970) (2013)
- C.Lattner. *What every C programmer should know about undefined behavior.* [Part I](http://blog.llvm.org/2011/05/what-every-c-programmer-should-know.html), [Part II](http://blog.llvm.org/2011/05/what-every-c-programmer-should-know_14.html), [Part III](http://blog.llvm.org/2011/05/what-every-c-programmer-should-know_21.html) &ndash; LLVM project (2013)

<!-- http://blog.regehr.org/archives/213 -->

:movie_camera:

- J.Regehr. [*Undefined behavior and compiler optimizations*](https://www.youtube.com/watch?v=AeEwxtEOgH0) &ndash; C++Now (2018)

#### Strict aliasing rule

See [*Type-punning* &ndash; Core language](core_language.md#type-punning).

---

## CPU

:movie_camera:

- C.Bay. [*The CPU cache: Instruction re-ordering made obvious*](https://www.youtube.com/watch?v=tNkVUIv2gEE) &ndash; C++Now (2016)
- M.Godbolt. [*x86 internals for fun & profit*](https://www.youtube.com/watch?v=hgcNM-6wr34) &ndash; GOTO (2014)

### Memory and cache

:link:

- U.Drepper. [*What every programmer should know about memory*](https://people.freebsd.org/~lstewart/articles/cpumemory.pdf) (2007)

<!-- https://web.archive.org/web/20080107035604/http://www.cellperformance.com/mike_acton/2006/05/demystifying_the_restrict_keyw.html -->

:movie_camera:

- T.Doumler. [*Want fast C++? Know your hardware!*](https://www.youtube.com/watch?v=BP6NxVxDQIs) &ndash; CppCon (2016)
- S.Meyers. [*CPU caches and why you care*](https://www.youtube.com/watch?v=WDIkqP4JbkE) &ndash; code::dive (2014)

#### Allocation

:link:

- N.Fitzgerald. [*Always bump downwards*](https://fitzgeraldnick.com/2019/11/01/always-bump-downwards.html) (2019)

:movie_camera:

- A.Alexandrescu [`std::allocator` is to allocation what `std::vector` is to vexation](https://www.youtube.com/watch?v=LIb3L4vKZ7U) &ndash; CppCon (2015)

#### Relocation

:link:

- A.O’Dwyer. [Announcing “trivially relocatable”](https://quuxplusone.github.io/blog/2018/07/18/announcing-trivially-relocatable/) (2018)

:movie_camera:

- A.O’Dwyer. [Trivially relocatable](https://www.youtube.com/watch?v=SGdfPextuAU) &ndash; C++Now (2019)

:anchor:

- A.O’Dwyer. [Object relocation in terms of move plus destroy](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1144r2.html) &ndash; WG21/P1144R2 (2019)

<!-- https://web.archive.org/web/20080107035604/http://www.cellperformance.com/mike_acton/2006/05/demystifying_the_restrict_keyw.html -->

<!-- https://www.airs.com/blog/archives/120
https://www.agner.org/optimize/optimizing_cpp.pdf
http://www.reedbeta.com/blog/data-oriented-hash-table/
 -->
