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

:movie_camera:

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

- A.Williams. [*Multi-threading in C++0x*](https://accu.org/index.php/journals/1584) – [Overload **93**](https://accu.org/index.php/journals/c257/) (2009)
- [*C++11 standard library extensions: Concurrency*](https://isocpp.org/wiki/faq/cpp11-library-concurrency) – Standard C++ Foundation

#### `std::atomic`

:grey_question:

- [*Does `std::atomic::operator++` really return by value?*](https://stackoverflow.com/q/13231048) – Stack Overflow

#### `std::atomic_shared_ptr`

:link:

- A.Williams. [*Why do we need `atomic_shared_ptr`?*](https://www.justsoftwaresolutions.co.uk/threading/why-do-we-need-atomic_shared_ptr.html) (2015)

:grey_question:

- [*What is the difference between `std::shared_ptr` and `std::experimental::atomic_shared_ptr`?*](https://stackoverflow.com/q/40223599) – Stack Overflow

#### `std::condition_variable`

> The `std::condition_variable` is a synchronization primitive that can be used to block a thread, or multiple threads at the same time, until another thread both modifies a shared variable (the condition), and notifies the `std::condition_variable`.

:memo:

- Even if the shared variable is atomic, it must be modified under the mutex in order to correctly publish the modification to the waiting thread.

:link:

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

:grey_question:

- [*`std::async` won’t spawn a new thread when return value is not stored*](https://stackoverflow.com/q/9490405) – Stack Overflow

:anchor:

- H.Sutter. [*`async` and `~future`*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3451.pdf) – WG21/N3451 (2012)

### Data races and race conditions

- [*Are “data races” and “race condition” actually the same thing in context of concurrent programming*](https://stackoverflow.com/q/11276259) – Stack Overflow

### Lock-based

#### Mutex locks

:link:

- S.Ignatchenko. [*5 big fat reasons why mutexes suck big time*](https://accu.org/index.php/journals/2623) – [Overload **149**](https://accu.org/index.php/journals/c395/) (2019)

#### Spin locks

:memo:

- Spin locks are typically slower if the number of threads is larger than the number of cores.

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

- [*Proposed RCU C++ API* (2017)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0461r1.pdf) – WG21/P0461R1
- [*Read-copy update (RCU) for C++* (2016)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0279r1.pdf) – WG21/P0279R1

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
-->

### Coroutines

:movie_camera:

- J.McNellis. [*Introduction to C++ coroutines*](https://www.youtube.com/watch?v=ZTqHjjm86Bw) – CppCon (2016)

---

## GPU computing

:movie_camera:

- P.Steinbach. [*C++ on GPUs done right?*](https://www.youtube.com/watch?v=z43l_LaOqnM) – Meeting C++ (2015)
