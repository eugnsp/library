# Concurrency and parallelism <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
- [GPU computing](#gpu-computing)
- [Multithreading](#multithreading)
	- [Concurrency and the standard library](#concurrency-and-the-standard-library)
		- [`std::atomic_shared_ptr`](#stdatomic_shared_ptr)
		- [`std::condition_variable`](#stdcondition_variable)
		- [`std::promise`](#stdpromise)
	- [Data races and race conditions](#data-races-and-race-conditions)
	- [Lock-based](#lock-based)
		- [Spin locks](#spin-locks)
	- [Lock-free](#lock-free)
		- [Hazard pointers](#hazard-pointers)
		- [Read-copy-update (RCU)](#read-copy-update-rcu)
	- [Memory model](#memory-model)
	- [POSIX threads](#posix-threads)

---

## Introduction and overview

:link:

- B.Barney. [*Introduction to parallel computing*](https://computing.llnl.gov/tutorials/parallel_comp/) – Lawrence Livermore National Laboratory

---

<!-- ## Algorithms

### Inclusive scan

--- -->

## GPU computing

:movie_camera:

- P.Steinbach. [*C++ on GPUs done right?*](https://www.youtube.com/watch?v=z43l_LaOqnM) – Meeting C++ (2015)

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

- [*C++11 standard library extensions: Concurrency*](https://isocpp.org/wiki/faq/cpp11-library-concurrency) – Standard C++ Foundation

#### `std::atomic_shared_ptr`

:link:

- A.Williams. [*Why do we need `atomic_shared_ptr`?*](https://www.justsoftwaresolutions.co.uk/threading/why-do-we-need-atomic_shared_ptr.html) (2015)
- [*What is the difference between `std::shared_ptr` and `std::experimental::atomic_shared_ptr`?*](https://stackoverflow.com/q/40223599) – Stack Overflow

#### `std::condition_variable`

> The `std::condition_variable` is a synchronization primitive that can be used to block a thread, or multiple threads at the same time, until another thread both modifies a shared variable (the condition), and notifies the `std::condition_variable`.

:memo:

- Even if the shared variable is atomic, it must be modified under the mutex in order to correctly publish the modification to the waiting thread.

:link:

- [`std::condition_variable`](https://en.cppreference.com/w/cpp/thread/condition_variable) – C++ reference

#### `std::promise`

> The `std::promise` provides a facility to store a value or an exception that is later acquired asynchronously via a `std::future` object created by the `std::promise` object.

:link:

- [`std::promise`](https://en.cppreference.com/w/cpp/thread/promise) – C++ reference
- [*What is `std::promise`?*](https://stackoverflow.com/q/11004273) – Stack Overflow

### Data races and race conditions

:link:

- [*Are “data races” and “race condition” actually the same thing in context of concurrent programming*](https://stackoverflow.com/q/11276259) – Stack Overflow

### Lock-based

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

<!--

https://see.stanford.edu/materials/icsppcs107/23-Concurrency-Examples.pdf
https://stackoverflow.com/questions/5002046/atomicity-in-c-myth-or-reality

http://www.drdobbs.com/parallel/volatile-vs-volatile/212701484
-->
