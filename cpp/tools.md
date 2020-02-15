# Tools <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Build automation](#build-automation)
	- [CMake](#cmake)
- [Code analysis and optimization tools](#code-analysis-and-optimization-tools)
	- [Online compilers](#online-compilers)
	- [Intel Architecture Code Analyzer (IACA)](#intel-architecture-code-analyzer-iaca)
	- [Valgrind](#valgrind)
- [Compilers](#compilers)
	- [GCC](#gcc)
- [Debugging](#debugging)
	- [GDB](#gdb)
		- [Pretty printers](#pretty-printers)
- [IDE](#ide)
	- [Visual Studio Code](#visual-studio-code)
- [Version-control system](#version-control-system)
	- [Git](#git)

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

## Code analysis and optimization tools

:movie_camera:

- H.Matthews. [*Optimising a small real-world C++ application*](https://www.youtube.com/watch?v=fDlE93hs_-U) – ACCU (2019)

### Online compilers

:link:

- [*Compiler explorer*](https://godbolt.org/)

### Intel Architecture Code Analyzer (IACA)

- [*What is IACA and how do I use it?*](https://stackoverflow.com/q/26021337) – Stack Overflow

### Valgrind

:movie_camera:

- J.Turner. [Episode 86: *Valgrind compiler optimization*](https://www.youtube.com/watch?v=3l0BQs2ThTo) – C++ Weekly (2017)

---

## Compilers

:link:

- [*C++ compiler support*](https://en.cppreference.com/w/cpp/compiler_support) – C++ reference

### GCC

:link:

- M.Jones [*GCC hacks in the Linux kernel*](https://developer.ibm.com/tutorials/l-gcc-hacks/) (2008)

:grey_question:

- [*Linux kernel’s `__is_constexpr` macro*](https://stackoverflow.com/q/49481217) – Stack Overflow
- [*What are the GCC predefined macros for the compiler’s version number?*](https://stackoverflow.com/q/1936719) – Stack Overflow

:sound:

- M.Deters. [Episode 61: *Internals of GCC*](http://www.se-radio.net/2007/07/episode-61-internals-of-gcc/) – Software Engineering Radio (2007)

:anchor:

- [*Semantics of floating point math in GCC*](https://gcc.gnu.org/wiki/FloatingPointMath) – GCC Wiki

## MSVC

:anchor:

- [*Compiler options: `/fp` (specify floating-point behavior)](https://docs.microsoft.com/en-us/cpp/build/reference/fp-specify-floating-point-behavior) – Visual C++ documentation

---

## Linkers

:link:

- E.Bendersky. [*Library order in static linking*](https://eli.thegreenplace.net/2013/07/09/library-order-in-static-linking) (2013)

---

## Debugging

:link:

- [*Debugging stack traces from crash dumps*](https://github.com/microsoft/WinObjC/wiki/Debugging-Stack-Traces-from-Crash-Dumps) – Microsoft

:grey_question:

- [*When and why will an OS initialise memory to `0xCD`, `0xDD`, etc. on `malloc`/`free`/`new`/`delete`?*](https://stackoverflow.com/q/370195) – Stack Overflow

:movie_camera:

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

## IDE

### Visual Studio Code

:link:

- [*Visual Studio Code*](https://code.visualstudio.com/)
- [*Visual Studio Code: Getting started*](https://code.visualstudio.com/docs)
- [*C/C++ for Visual Studio Code*](https://code.visualstudio.com/docs/languages/cpp)

---

## Version-control system

### Git

:grey_question:

- [*How to make Git “forget” about a file that was tracked but is now in `.gitignore`?*](https://stackoverflow.com/q/1274057) – Stack Overflow

:movie_camera:

- C.Schafer. [*Git tutorial for beginners*](https://www.youtube.com/playlist?list=PL-osiE80TeTuRUfjRe54Eea17-YfnOOAx)
