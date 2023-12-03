# Assembly, low-level programming, and OS internals <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
- [CPU](#cpu)
  - [CPU word size](#cpu-word-size)
  - [Endianness and NUXI problem](#endianness-and-nuxi-problem)
  - [x87](#x87)
  - [Tricks](#tricks)
- [Memory](#memory)
  - [Memory addressing](#memory-addressing)
- [Operating systems](#operating-systems)
  - [Libraries](#libraries)
    - [Linux](#linux)
    - [Windows](#windows)
  - [Device drivers](#device-drivers)

---

## Introduction and overview

:movie_camera:

- D.Sankel. [*Under the hood: Assembly, system calls, and hardware*](https://www.youtube.com/watch?v=0iXRRCnurvo) – C++Now (2023)

<!-- https://web.archive.org/web/20080107035604/http://www.cellperformance.com/mike_acton/2006/05/demystifying_the_restrict_keyw.html -->
<!-- - O.Mutlu. [Lec. 20: *Virtual memory*](https://www.youtube.com/watch?v=2RhGMpY18zw) – - Comp. Arch. 2015 -->

---

## CPU

:link:

- B.Wagstaff. [*A journey through the CPU pipeline*](https://www.gamedev.net/articles/programming/general-and-gameplay-programming/a-journey-through-the-cpu-pipeline-r3115/) (2013)

### CPU word size

:link:

- S.Ignatchenko. [*Size matters*](https://accu.org/journals/overload/22/120/ignatchenko_1895/) – [Overload **120**](https://accu.org/journals/overload/overload120) (2014)
- E.Musayev. [*A brief history of the road to 64 bits*](https://web.archive.org/web/20191222085303/http://www.eldar.com/node/262) (in Russian, 2009)

:page_facing_up:

- J.Mashey. [*The long road to 64 bits*](https://cacm.acm.org/magazines/2009/1/15667-the-long-road-to-64-bits/fulltext) – [Communications of the ACM **52**, 45-53](https://doi.org/10.1145/1435417.1435431) (2009)

### Endianness and NUXI problem

:link:

- [*Endianness*](https://en.wikipedia.org/wiki/Endianness) – Wikipedia

:book:

- Essay 1: *You must be joking* – P.J.Plauger. [*Programming on purpose III: Essays on software technology*](https://www.pearson.com/us/higher-education/program/Plauger-Programming-on-Purpose-III-Essays-on-Software-Technology/PGM133229.html) (1994)

### x87

See also [*Numeric data structures and algorithms*](../data_structures_and_algorithms/numeric.md).

:link:

- [*Pentium `FDIV` bug*](https://en.wikipedia.org/wiki/Pentium_FDIV_bug#cite_note-halfhill-199503-3) – Wikipedia
- B.Dawson. [*Intel underestimates error bounds by 1.3 quintillion](https://randomascii.wordpress.com/2014/10/09/intel-underestimates-error-bounds-by-1-3-quintillion/) (2014)
- S.Duplichan. [*Intel overstates FPU accuracy*](http://notabs.org/fpuaccuracy/index.htm) (2013)
- T.R.Halfhill. [*The truth behind the Pentium bug*](https://web.archive.org/web/20060209005434/http://www.byte.com/art/9503/sec13/art1.htm) – BYTE.com (1995)

:grey_question:

- [*Extended (80-bit) double floating point in x87, not SSE2 – we don’t miss it?*](https://stackoverflow.com/q/3206101) – Stack Overflow
- [*Did any compiler fully use Intel x87 80-bit floating point?*](https://retrocomputing.stackexchange.com/q/9751) – Retrocomputing

:anchor:

- [*Programming with the x87 floating-point unit*](http://www.infophysics.net/x87.pdf) – Intel

### Tricks

:movie_camera:

- C.Domas. [*The M/o/Vfuscator – Turning `mov` into a soul-crushing RE nightmare*](https://www.youtube.com/watch?v=R7EEoWg6Ekk) – Derbycon (2015)

:page_facing_up:

- S.Dolan. [*`mov` is Turing-complete*](https://drwho.virtadpt.net/files/mov.pdf) (2013)

---

## Memory

:link:

- E.Martin. [*Some things I’ve learned about memory*](http://neugierig.org/software/blog/2011/05/memory.html) (2011)
- U.Drepper. [*What every programmer should know about memory*](https://people.freebsd.org/~lstewart/articles/cpumemory.pdf) (2007)
- [*Simple benchmark for memory throughput and latency*](https://github.com/ssvb/tinymembench)
- L.Maranget, S.Sarkar, P.Sewell. [*A tutorial introduction to the ARM and POWER relaxed memory models*](https://www.cl.cam.ac.uk/~pes20/ppc-supplemental/test7.pdf) (2012)


:movie_camera:

- U.Drepper. [*C++ and memory: Between correctness and performance*](https://www.youtube.com/watch?v=LXfSXzxDY_M) – code::dive (2018)

### Memory addressing

:link:

- D.A.Rusling. [Ch. 3: *Memory management*](http://www.tldp.org/LDP/tlk/mm/memory.html) – [The Linux kernel](http://www.tldp.org/LDP/tlk/tlk-title.html)
- C.Santili. [*x86 paging tutorial*](https://cirosantilli.com/x86-paging)
- [*How does x86 paging work?*](https://stackoverflow.com/q/18431261) – Stack Overflow
- [*What are near, far and huge pointers?*](https://stackoverflow.com/q/3575592) – Stack Overflow

:movie_camera:

- JF Bastien. [*`*(char*)0 = 0;`*](https://www.youtube.com/watch?v=dFIqNZ8VbRY) – C++ on Sea (2023)
- C.Terman. *Virtual memory.* [Part I](https://www.youtube.com/watch?v=3akTtCu_F_k), [Part II](https://www.youtube.com/watch?v=DelO8tZFMrc) – MIT 6.004: Computation structures (2013)

:book:

- Essay 1: *You must be joking* – P.J.Plauger. [*Programming on purpose III: Essays on software technology*](https://www.pearson.com/us/higher-education/program/Plauger-Programming-on-Purpose-III-Essays-on-Software-Technology/PGM133229.html) (1994)

<!-- https://web.archive.org/web/20080107035604/http://www.cellperformance.com/mike_acton/2006/05/demystifying_the_restrict_keyw.html -->

<!-- https://www.airs.com/blog/archives/120
https://www.agner.org/optimize/optimizing_cpp.pdf
https://www.agner.org/optimize/
http://www.reedbeta.com/blog/data-oriented-hash-table/
 -->

---

## Operating systems

### Libraries

:movie_camera:

- O.Shilon. [*Shared libraries in Windows and Linux*](https://www.youtube.com/watch?v=6TrJc06IekE) – C++ on Sea (2023)

#### Linux

:link:

- I.Wienand. [*Position independent code and x86-64 libraries*](https://www.technovelty.org/c/position-independent-code-and-x86-64-libraries.html) (2013)
- E.Bendersky. [*Library order in static linking*](https://eli.thegreenplace.net/2013/07/09/library-order-in-static-linking) (2013)
- E.Bendersky. [*Load-time relocation of shared libraries*](https://eli.thegreenplace.net/2011/08/25/load-time-relocation-of-shared-libraries) (2011)
- E.Bendersky. [*Position independent code (PIC) in shared libraries*](https://eli.thegreenplace.net/2011/11/03/position-independent-code-pic-in-shared-libraries) (2011)
- E.Bendersky. [*Position independent code (PIC) in shared libraries on x64*](https://eli.thegreenplace.net/2011/11/11/position-independent-code-pic-in-shared-libraries-on-x64) (2011)

#### Windows

:link:

- S.Ignatchenko. [*To DLL or not to DLL*](https://accu.org/journals/overload/18/99/ignatchenko_1704/) – [Overload **163**](https://accu.org/journals/overload/overload99) (2010)

:movie_camera:

- J.McNellis. [*Everything you ever wanted to know about DLLs*](https://www.youtube.com/watch?v=JPQWQfDhICA) – CppCon (2017)

### Device drivers

:movie_camera:

- D.Saks. [*Memory-mapped devices as objects*](https://www.youtube.com/watch?v=uwzuAGtAEFk) – CppCon (2020)

---

