# Concurrency and parallelism <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
- [SIMD](#simd)
	- [SIMD within a register (SWAR)](#simd-within-a-register-swar)
- [Multithreading](#multithreading)
	- [Concurrency and the standard library](#concurrency-and-the-standard-library)
		- [`std::atomic`](#stdatomic)
		- [`std::atomic_shared_ptr`](#stdatomic_shared_ptr)
		- [`std::condition_variable`](#stdcondition_variable)
		- [`std::mutex`](#stdmutex)
		- [`std::promise` / `std::future`](#stdpromise--stdfuture)
		- [`std::async`](#stdasync)
		- [`std::thread`](#stdthread)
		- [`std::lock_guard`](#stdlock_guard)
	- [Data races and race conditions](#data-races-and-race-conditions)
	- [Lock-based](#lock-based)
		- [Mutex locks](#mutex-locks)
		- [Spin locks](#spin-locks)
	- [Lock-free](#lock-free)
		- [Hazard pointers](#hazard-pointers)
		- [Read-copy-update (RCU)](#read-copy-update-rcu)
	- [Memory model](#memory-model)
	- [POSIX threads](#posix-threads)
	- [Coroutines](#coroutines)
	- [Concurrency patterns](#concurrency-patterns)
- [GPU computing](#gpu-computing)

---

## Introduction and overview

:link:

- B.Barney. [*Introduction to parallel computing*](https://computing.llnl.gov/tutorials/parallel_comp/) – Lawrence Livermore National Laboratory

---

<!-- ## Algorithms

### Inclusive scan

--- -->

---

## SIMD

:movie_camera:

- B.Steagall. [*Adventures in SIMD-thinking*](https://www.youtube.com/watch?v=1FPobiebZLE) – CppNow (2021)
- B.Steagall. *Adventures in SIMD-thinking* [Part I](https://www.youtube.com/watch?v=qejTqnxQRcw), [Part II](https://www.youtube.com/watch?v=qXleSwCCEvY) – CppCon (2020)

### SIMD within a register (SWAR)

:link:

- [*SWAR*](https://en.wikipedia.org/wiki/SWAR) – Wikipedia
- H.Dietz. [Ch. 4: *SIMD within a register (e.g., using MMX)*](https://www.tldp.org/HOWTO/Parallel-Processing-HOWTO-4.html) – Linux parallel processing HOWTO
- [*SIMD and SWAR techniques*](https://www.chessprogramming.org/SIMD_and_SWAR_Techniques) – Chess Programming Wiki

:grey_question:

- [*Is `reinterpret_cast`ing between hardware SIMD vector pointer and the corresponding type an undefined behavior?*](https://stackoverflow.com/q/52112605) – Stack Overflow
- [*Is casting to simd-type undefined behaviour in C++?*](https://stackoverflow.com/questions/58910969) – Stack Overflow

---

## Multithreading

:link:

- E.Bendersky. [*C++11 threads, affinity and hyperthreading*](https://eli.thegreenplace.net/2016/c11-threads-affinity-and-hyperthreading/) (2016)

:movie_camera:

- A.Williams. [*An introduction to multithreading in C++20*](https://www.youtube.com/watch?v=A7sVFJLJM-A) – CppCon (2022)
- F.Petriconi. [*An adventure in race conditions*](https://www.youtube.com/watch?v=asgO4P2fhTw) – ACCU (2019)
- A.Sermersheim. *Multithreading is the answer. What is the question?* [Part I](https://www.youtube.com/watch?v=GNw3RXr-VJk), [Part II](https://www.youtube.com/watch?v=sDLQWivf1-I) – CppCon (2017)
- R.Grimm. [*C++11 multithreading done right?*](https://www.youtube.com/watch?v=paK38WAq8WY) – Meeting C++ (2014)
- A.Williams. [*The continuing future of C++ concurrency*](https://www.youtube.com/watch?v=FaHJOkOrfNo) – CppCon (2016)

:book:

- P.E.McKenney. [*Is parallel programming hard, and, if so, what can you do about it?*](https://mirrors.edge.kernel.org/pub/linux/kernel/people/paulmck/perfbook/perfbook.html) (2018)
- A.Williams. [*C++ concurrency in action: Practical multithreading*](https://www.manning.com/books/c-plus-plus-concurrency-in-action-second-edition) (2019)
- Ch. 9: *Parallelism and concurrency* – J.Galowicz. [*C++17 STL cookbook: Discover the latest enhancements to functional programming and lambda expressions*](https://www.packtpub.com/application-development/c17-stl-cookbook) (2017)
- Ch. 18: *Concurrency* – N.M.Josuttis. [*The C++ standard library: A tutorial and reference*](http://www.cppstdlib.com/) (2012)

:page_facing_up:

- P.E.McKenney. [*Memory barriers: A hardware view for software hackers*](http://www.rdrop.com/~paulmck/scalability/paper/whymb.2010.06.07c.pdf) (2010)

### Concurrency and the standard library

:link:

- L.R.Teodorescu. [*A case against blind use of C++ parallel algorithms*](https://accu.org/journals/overload/29/161/teodorescu/) – [Overload **161**](https://accu.org/journals/overload/overload161) (2021)
- A.Williams. [*Multi-threading in C++0x*](https://accu.org/journals/overload/17/93/williams_1584/) – [Overload **93**](https://accu.org/journals/overload/overload93) (2009)
- [*C++11 standard library extensions: Concurrency*](https://isocpp.org/wiki/faq/cpp11-library-concurrency) – Standard C++ Foundation

:movie_camera:

- J.Machutov&aacute;. [*Memory Model: Get your shared data under control*](https://www.youtube.com/watch?v=L5RCGDAan2Y) – C++ Meeting (2023)
- A.Williams. [*An introduction to multithreading in C++20*](https://www.youtube.com/watch?v=A7sVFJLJM-A) – CppCon (2022)
- M.Shah. [*Back to basics: Concurrency*](https://www.youtube.com/watch?v=pfIC-kle4b0) – CppCon (2021)
- A.O’Dwyer. [*Back to basics: Concurrency*](https://www.youtube.com/watch?v=F6Ipn7gCOsY) – CppCon (2020)
- B.A.Lelbach. [*The C++17 parallel algorithms library and beyond*](https://www.youtube.com/watch?v=Vck6kzWjY88) – CppCon (2016)
- D.K&uuml;hl. [*C++17 parallel algorithms*](https://www.youtube.com/watch?v=Ve8cHE9LNfk) – CppCon (2017)

#### `std::atomic`

:grey_question:

- [*Does `std::atomic::operator++` really return by value?*](https://stackoverflow.com/q/13231048) – Stack Overflow

:movie_camera:

- H.-J.Boehm. [*Using weakly ordered C++ atomics correctly*](https://www.youtube.com/watch?v=M15UKpNlpeM) – CppCon (2016)

#### `std::atomic_shared_ptr`

:link:

- A.Williams. [*Why do we need `atomic_shared_ptr`?*](https://www.justsoftwaresolutions.co.uk/threading/why-do-we-need-atomic_shared_ptr.html) (2015)

:grey_question:

- [*What is the difference between `std::shared_ptr` and `std::experimental::atomic_shared_ptr`?*](https://stackoverflow.com/q/40223599) – Stack Overflow

#### `std::condition_variable`

> The `std::condition_variable` is a synchronization primitive that can be used to block a thread, or multiple threads at the same time, until another thread both modifies a shared variable (the condition), and notifies the `std::condition_variable`.

:grey_question:

- [*Shared atomic variable is not properly published if it is not modified under mutex*](https://stackoverflow.com/q/38147825) – Stack Overflow

:anchor:

- [`std::condition_variable`](https://en.cppreference.com/w/cpp/thread/condition_variable) – C++ reference

#### `std::mutex`

> The `std::mutex` class is a synchronization primitive that can be used to protect shared data from being simultaneously accessed by multiple threads.

:grey_question:

- [*Move constructor for `std::mutex`*](https://stackoverflow.com/q/7557179) – Stack Overflow
- [*Why is `std::mutex::unlock()` not `noexcept`*](https://stackoverflow.com/q/38450189) – Stack Overflow

:anchor:

- [*`std::mutex`*](https://en.cppreference.com/w/cpp/thread/mutex) – C++ reference

#### `std::promise` / `std::future`

> The `std::promise` provides a facility to store a value or an exception that is later acquired asynchronously via a `std::future` object created by the `std::promise` object.

:grey_question:

- [*What is `std::promise`?*](https://stackoverflow.com/q/11004273) – Stack Overflow
- [*Futures vs. promises*](https://stackoverflow.com/q/12620186) – Stack Overflow
- [*Why we need both `std::promise` and `std::future`?*](https://stackoverflow.com/q/34169602) – Stack Overflow

:anchor:

- [`std::promise`](https://en.cppreference.com/w/cpp/thread/promise) – C++ reference

#### `std::async`

:link:

- E.Bendersky. [*The promises and challenges of `std::async` task-based parallelism in C++11 *](https://eli.thegreenplace.net/2016/the-promises-and-challenges-of-stdasync-task-based-parallelism-in-c11/) (2016)
- M.Nelson. [*C++11’s `async` template*](https://www.drdobbs.com/cpp/c11s-async-template/240001196) – Dr.Dobb’s Journal (2012)

:grey_question:

- [*`std::async` won’t spawn a new thread when return value is not stored*](https://stackoverflow.com/q/9490405) – Stack Overflow

:anchor:

- N.Josuttis. [*Why deprecating `async()` is the worst of all options*](https://wg21.link/n3780) – WG21/N3780
- H.-J.Boehm. [*`async()` future destructors must wait*](https://wg21.link/n3679) – WG21/N3679
- H.Sutter. [*`async` and `~future`*](https://wg21.link/n3451) – WG21/N3451

#### `std::thread`

:anchor:

- H.-J.Boehm. [*A plea to reconsider detach-on-destruction for thread objects*](https://wg21.link/n2802) – WG21/N2802

#### `std::lock_guard`

:grey_question:

- [*Why is `std::lock_guard` not movable?*](https://stackoverflow.com/q/22502606) – Stack Overflow

:anchor:

- [*`std::lock_guard`*](https://en.cppreference.com/w/cpp/thread/lock_guard) – C++ reference

### Data races and race conditions

:grey_question:

- [*Are “data races” and “race condition” actually the same thing in context of concurrent programming*](https://stackoverflow.com/q/11276259) – Stack Overflow

### Lock-based

#### Mutex locks

:link:

- S.Ignatchenko. [*5 big fat reasons why mutexes suck big time*](https://accu.org/journals/overload/27/149/ignatchenko_2623/) – [Overload **149**](https://accu.org/journals/overload/overload149) (2019)
- M.Spertus. [*Thread-safe copy and move constructors*](https://www.justsoftwaresolutions.co.uk/threading/thread-safe-copy-constructors.html) (2011)

#### Spin locks

<!-- - Spin locks are typically slower if the number of threads is larger than the number of cores. -->

:link:

- [*When should one use a spinlock instead of mutex?*](https://stackoverflow.com/q/5869825) – Stack Overflow
- [*Spinlock versus semaphore*](https://stackoverflow.com/q/195853) – Stack Overflow

### Lock-free

> Lock-free programming is a set of techniques for writing concurrent programs without using explicit locks.

:movie_camera:

- F.Pikus. [*C++ atomics, from basic to advanced: What do they really do?*](https://www.youtube.com/watch?v=ZQFzMfHIxng) – CppCon (2017)
- F.Pikus. *Live lock-free or deadlock (practical lock-free programming).* [Part I](https://www.youtube.com/watch?v=lVBvHbJsg5Y), [Part II](https://www.youtube.com/watch?v=1obZeHnAwz4) – CppCon (2015)
- H.Sutter. *`atomic<>` weapons:* [Part I](https://www.youtube.com/watch?v=A8eCGOqgvH4), [Part II](https://www.youtube.com/watch?v=KeLBd2EJLOU) – C++ and Beyond (2012)

#### Hazard pointers

:link:

- [*Hazard pointer* – Wikipedia](https://en.wikipedia.org/wiki/Hazard_pointer)
- A.Alexandrescu, M.Michael. [*Lock-free data structures with hazard pointers*](http://www.drdobbs.com/lock-free-data-structures-with-hazard-po/184401890) – Dr.Dobb’s Journal (2004)

#### Read-copy-update (RCU)

:link:

- [*Read-copy-update*](https://en.wikipedia.org/wiki/Read-copy-update) – Wikipedia
- P.E.McKenney. [*Introduction to RCU*](http://www2.rdrop.com/users/paulmck/RCU/)

:movie_camera:

- F.Pikus. [*Read, copy, update, then what? RCU for non-kernel programmers*](https://www.youtube.com/watch?v=rxQ5K9lo034) – CppCon (2017)
- P.E.McKenney. [*A lock-free concurrency toolkit for deferred reclamation and optimistic speculation*](https://www.youtube.com/watch?v=uhgrD_B1RhQ&t=2289) – CppCon (2016)

:anchor:

- P.E.McKenney et al. [*Proposed RCU C++ API*](https://wg21.link/p0461) – WG21/P0461
- P.E.McKenney. [*Read-copy update (RCU) for C++*](https://wg21.link/p0279) – WG21/P0279

### Memory model

:link:

- [*C++11 introduced a standardized memory model. What does it mean? And how is it going to affect C++ programming?*](https://stackoverflow.com/q/6319146) – Stack Overflow

:anchor:

- [*Memory model*](https://en.cppreference.com/w/cpp/language/memory_model) – C++ reference

### POSIX threads

:link:

- B.Barney. [*POSIX threads programming*](https://computing.llnl.gov/tutorials/pthreads/)

:grey_question:

- [*When to use `pthread_exit()` and when to use `pthread_join()` in Linux?*](https://stackoverflow.com/q/20824229) – Stack Overflow

<!--

https://see.stanford.edu/materials/icsppcs107/23-Concurrency-Examples.pdf
https://stackoverflow.com/questions/5002046/atomicity-in-c-myth-or-reality

http://www.drdobbs.com/parallel/volatile-vs-volatile/212701484

https://www.hpl.hp.com/techreports/2004/HPL-2004-209.pdf
-->

### Coroutines

:movie_camera:

- R.Barkan. [*Coroutine intuition in C++*](https://www.youtube.com/watch?v=2jzuuOeUDQI) – C++ on Sea (2023)
- J.McNellis. [*Introduction to C++ coroutines*](https://www.youtube.com/watch?v=ZTqHjjm86Bw) – CppCon (2016)

### Concurrency patterns

See [*Concurrency patterns* – Patterns, idioms, and design principles](patterns_and_idioms.md#concurrency-patterns).

---

## GPU computing

:movie_camera:

- P.Steinbach. [*C++ on GPUs done right?*](https://www.youtube.com/watch?v=z43l_LaOqnM) – Meeting C++ (2015)
