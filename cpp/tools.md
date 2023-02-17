# Tools <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Build automation](#build-automation)
	- [CMake](#cmake)
- [Version control](#version-control)
	- [Git](#git)
- [Compilation and compilers](#compilation-and-compilers)
	- [GCC](#gcc)
	- [Clang](#clang)
	- [MSVC](#msvc)
	- [Circle](#circle)
- [Linking and linkers](#linking-and-linkers)
	- [Linux](#linux)
	- [Windows](#windows)
		- [DLLs](#dlls)
- [IDE](#ide)
	- [Visual Studio Code](#visual-studio-code)
- [Code analysis and optimization tools](#code-analysis-and-optimization-tools)
	- [Online compilers](#online-compilers)
	- [Intel Architecture Code Analyzer (IACA)](#intel-architecture-code-analyzer-iaca)
	- [Valgrind](#valgrind)
- [Debugging](#debugging)
	- [GDB](#gdb)
		- [Pretty printers](#pretty-printers)
- [C++ tests and quizes](#c-tests-and-quizes)

---

## Build automation

### CMake

:link:

- [*Include Google Benchmark/Test in C++ project*](https://felixmoessbauer.com/blog-reader/include-google-benchmark-test-in-c-project.html) – Software Engineering Blog

:movie_camera:

- F.Castelli. [*Introduction to CMake*](https://www.youtube.com/watch?v=jt3meXdP-QI) – SwedenCpp (2018)
- D.Pfeifer. [*Effective CMake*](https://www.youtube.com/watch?v=bsXLMQ6WgIk) – C++Now (2017)
- M.Ropert. [*Using modern CMake patterns to enforce a good modular design*](https://www.youtube.com/watch?v=eC9-iRN2b04) – CppCon (2017)
- J.Turner. [Episode 78: *Intro to CMake*](https://www.youtube.com/watch?v=HPMvU64RUTY) – C++ Weekly (2017)

---

## Version control

### Git

:grey_question:

- [*How to make Git “forget” about a file that was tracked but is now in `.gitignore`?*](https://stackoverflow.com/q/1274057) – Stack Overflow
- [*When should I use `git pull --rebase`?*](https://stackoverflow.com/q/2472254) – Stack Overflow

:movie_camera:

- C.Schafer. [*Git tutorial for beginners*](https://www.youtube.com/playlist?list=PL-osiE80TeTuRUfjRe54Eea17-YfnOOAx)

---

## Compilation and compilers

:link:

- A.O’Dwyer. [*Always read the first error message first*](https://quuxplusone.github.io/blog/2023/01/21/did-you-mean-bool/) (2023)

:anchor:

- [*C++ compiler support*](https://en.cppreference.com/w/cpp/compiler_support) – C++ reference

### GCC

:link:

- M.Jones [*GCC hacks in the Linux kernel*](https://developer.ibm.com/tutorials/l-gcc-hacks/) (2008)
- M.Davis. [*An introduction to creating GCC plugins*](https://lwn.net/Articles/457543/) (2011)
- F.Aboukhadijeh. [*GCC Easter egg: C++ undefined defined behavior*](https://feross.org/gcc-ownage/) (2010)

:grey_question:

- [*Linux kernel’s `__is_constexpr` macro*](https://stackoverflow.com/q/49481217) – Stack Overflow
- [*What are the GCC predefined macros for the compiler’s version number?*](https://stackoverflow.com/q/1936719) – Stack Overflow

:sound:

- M.Deters. [Episode 61: *Internals of GCC*](http://www.se-radio.net/2007/07/episode-61-internals-of-gcc/) – Software Engineering Radio (2007)

:anchor:

- [*Semantics of floating point math in GCC*](https://gcc.gnu.org/wiki/FloatingPointMath) – GCC Wiki

### Clang

:link:

- E.Bendersky. [*Dumping a C++ object’s memory layout with Clang*](https://eli.thegreenplace.net/2012/12/17/dumping-a-c-objects-memory-layout-with-clang/) (2012)

### MSVC

:link:

- [*Compiler limits*](https://learn.microsoft.com/en-us/cpp/cpp/compiler-limits) (2021)

:anchor:

- [*Compiler options: `/fp` (specify floating-point behavior)](https://docs.microsoft.com/en-us/cpp/build/reference/fp-specify-floating-point-behavior) – Visual C++ documentation

### Circle

:link:

- [*Circle C++ compiler*](https://www.circle-lang.org/)

---

## Linking and linkers

:link:

- D.Drysdale. [*Beginner’s guide to linkers*](http://www.lurklurk.org/linkers/linkers.html) (2009)

:grey_question:

- [*What do linkers actually do with multiply-defined `inline` functions?*](https://stackoverflow.com/q/35233468) – Stack Overflow

:movie_camera:

- N.Friedman. [*What C++ developers should know about globals (and the linker)*](https://www.youtube.com/watch?v=xVT1y0xWgww) – CppCon (2017)

:book:

- J.R.Levine. [*Linkers and loaders*](https://linker.iecc.com/) – Morgan-Kauffman (1999)

### Linux

:link:

- I.Wienand. [*Position independent code and x86-64 libraries*](https://www.technovelty.org/c/position-independent-code-and-x86-64-libraries.html) (2013)
- E.Bendersky. [*Library order in static linking*](https://eli.thegreenplace.net/2013/07/09/library-order-in-static-linking) (2013)
- E.Bendersky. [*Load-time relocation of shared libraries*](https://eli.thegreenplace.net/2011/08/25/load-time-relocation-of-shared-libraries) (2011)
- E.Bendersky. [*Position independent code (PIC) in shared libraries*](https://eli.thegreenplace.net/2011/11/03/position-independent-code-pic-in-shared-libraries) (2011)
- E.Bendersky. [*Position independent code (PIC) in shared libraries on x64*](https://eli.thegreenplace.net/2011/11/11/position-independent-code-pic-in-shared-libraries-on-x64) (2011)

### Windows

#### DLLs

:link:

- S.Ignatchenko. [*To DLL or not to DLL*](https://accu.org/journals/overload/18/99/ignatchenko_1704/) – [Overload **163**](https://accu.org/journals/overload/overload99) (2010)

:movie_camera:

- J.McNellis. [*Everything you ever wanted to know about DLLs*](https://www.youtube.com/watch?v=JPQWQfDhICA) – CppCon (2017)

---

## IDE

### Visual Studio Code

:link:

- [*Visual Studio Code*](https://code.visualstudio.com/)
- [*Visual Studio Code: Getting started*](https://code.visualstudio.com/docs)
- [*C/C++ for Visual Studio Code*](https://code.visualstudio.com/docs/languages/cpp)

---

## Code analysis and optimization tools

:movie_camera:

- H.Matthews. [*Optimising a small real-world C++ application*](https://www.youtube.com/watch?v=fDlE93hs_-U) – ACCU (2019)

### Online compilers

:link:

- [*Compiler explorer*](https://godbolt.org/)

:movie_camera:

- M.Godbolt [*Compiler explorer: Behind the scenes*](https://www.youtube.com/watch?v=kIoZDUd5DKw) – CppCon (2019)

### Intel Architecture Code Analyzer (IACA)

- [*What is IACA and how do I use it?*](https://stackoverflow.com/q/26021337) – Stack Overflow

### Valgrind

:movie_camera:

- J.Turner. [Episode 86: *Valgrind compiler optimization*](https://www.youtube.com/watch?v=3l0BQs2ThTo) – C++ Weekly (2017)

---

## Debugging

:link:

- [*Debugging stack traces from crash dumps*](https://github.com/microsoft/WinObjC/wiki/Debugging-Stack-Traces-from-Crash-Dumps) – Microsoft

:grey_question:

- [*When and why will an OS initialise memory to `0xCD`, `0xDD`, etc. on `malloc`/`free`/`new`/`delete`?*](https://stackoverflow.com/q/370195) – Stack Overflow

:movie_camera:

- B.Steagall. [*Back to basics: Debugging techniques*](https://www.youtube.com/watch?v=M7fV-eQwxrY) – CppCon (2021)
- H.Matthews. [*Optimising a small real-world C++ application*](https://www.youtube.com/watch?v=fDlE93hs_-U) – ACCU (2019)
- G.Law. [*Debugging Linux C++*](https://www.youtube.com/watch?v=V1t6faOKjuQ) – CppCon (2018)
- [*Unusual memory bit patterns*](https://www.softwareverify.com/memory-bit-patterns.php)

### GDB

:link:

- [*Debugging with GDB*](https://sourceware.org/gdb/onlinedocs/gdb/Pretty-Printing.html)

:grey_question:

- [*Identify source file name for a symbol in gdb debugger*](https://stackoverflow.com/q/58826430) – Stack Overflow

#### Pretty printers

:link:

- [Sec. 10.9: *Pretty printing*](https://sourceware.org/gdb/onlinedocs/gdb/Pretty-Printing.html) – Debugging with GDB
- [Sec. 23.2.2: *Python API*](https://sourceware.org/gdb/onlinedocs/gdb/Python-API.html) – Debugging with GDB
- D.Haguenauer. [*Writing custom GDB pretty-printers*](http://www.kurokatta.org/grumble/2018/05/gdb-pretty) (2018)
- *Pretty printing.* [Part I](http://tromey.com/blog/?p=524), [Part II](http://tromey.com/blog/?p=546) (2008)
- [*Make debugging easier with custom pretty-printers*](https://rethinkdb.com/blog/make-debugging-easier-with-custom-pretty-printers) (2010)
- R.Sonderfeld. [*GDB pretty printers for Boost*](https://github.com/ruediger/Boost-Pretty-Printer)

---

## C++ tests and quizes

:link:

- A.S.Knatten. [*C++ quiz*](http://cppquiz.org/)
- J.Nieminen. [*Test your C++ knowledge*](http://warp.povusers.org/c++test/)
