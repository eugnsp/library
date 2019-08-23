# Concurrency and parallelism

## Table of contents

* [Introduction and overview](#introduction-and-overview)
* [GPU computing](#gpu-computing)
* [Multithreading](#multithreading)
	* [Lock-based](#lock)
		* [Spin locks](#spin-locks)
	* [Lock-free](#lock-free)
		* [Hazard pointers](#hazard-pointers)
		* [Read-copy-update (RCU)](#read-copy-update-rcu)
	* [Concurrency and the standard library](#concurrency-and-the-standard-library)
		* [`std::atomic_shared_ptr`](#stdatomic_shared_ptr)
		* [`std::promise`](#stdpromise)
	<!-- * [Patterns and idioms](#patterns-and-idioms)
		* [Execute-around pointer](#execute-around pointer) -->
	* [POSIX threads](#posix-threads)
---

## Introduction and overview

:link:

* [*Introduction to parallel computing* &ndash; B.Barney](https://computing.llnl.gov/tutorials/parallel_comp/)

## GPU computing

:movie_camera:

* [*C++ on GPUs done right?* &ndash; P.Steinbach @ Meeting C++ (2015)](https://www.youtube.com/watch?v=z43l_LaOqnM)

## Multithreading

:movie_camera:

* *Multithreading is the answer. What is the question?* &ndash; A.Sermersheim @ CppCon (2017)
	* [Part I](https://www.youtube.com/watch?v=GNw3RXr-VJk)
	* [Part II](https://www.youtube.com/watch?v=sDLQWivf1-I)
* [*C++11 multithreading done right?* &ndash; R.Grimm @ Meeting C++ (2014)](https://www.youtube.com/watch?v=paK38WAq8WY)
* [*The continuing future of C++ concurrency* &ndash; A.Williams @ CppCon (2016)](https://www.youtube.com/watch?v=FaHJOkOrfNo)

:book:

* [P.E.McKenney. *Is parallel programming hard, and, if so, what can you do about it?* (2018)](https://mirrors.edge.kernel.org/pub/linux/kernel/people/paulmck/perfbook/perfbook.html)
* [A.Williams. *C++ concurrency in action: Practical multithreading.* Manning, 2<sup>nd</sup> ed. (2019)](https://www.manning.com/books/c-plus-plus-concurrency-in-action-second-edition)
* Ch. 9: *Parallelism and concurrency* &ndash; J.Galowicz. *C++17 STL cookbook: Discover the latest enhancements to functional programming and lambda expressions.* Packt Publishing (2017)\
[Book website](https://www.packtpub.com/application-development/c17-stl-cookbook)
* Ch. 18: *Concurrency* &ndash; N.M.Josuttis. *The C++ standard library: A tutorial and reference.* Addison-Wesley, 2<sup>nd</sup> ed. (2012)\
[Book website](http://www.cppstdlib.com/)

:page_facing_up:

* [*Memory barriers: a hardware view for software hackers* &ndash; P.E.McKenney (2010)](http://www.rdrop.com/~paulmck/scalability/paper/whymb.2010.06.07c.pdf)


### Lock-based

#### Spin locks

:memo:

* Spin locks are typically slower if the number of threads is larger than the number of cores.

:link:

* [*When should one use a spinlock instead of mutex?* &ndash; Stack Overflow](https://stackoverflow.com/questions/5869825/when-should-one-use-a-spinlock-instead-of-mutex)
* [*Spinlock versus semaphore* &ndash; Stack Overflow](https://stackoverflow.com/questions/195853/spinlock-versus-semaphore)

### Lock-free

> Lock-free programming is a set of techniques for writing concurrent programs without using
explicit locks.

:movie_camera:

* [*C++ atomics, from basic to advanced: What do they really do?* &ndash; F.Pikus @ CppCon (2017)](https://www.youtube.com/watch?v=ZQFzMfHIxng)
* *Live lock-free or deadlock (practical lock-free programming)* &ndash; F.Pikus @ CppCon (2015)
	* [Part I](https://www.youtube.com/watch?v=lVBvHbJsg5Y)
	* [Part II](https://www.youtube.com/watch?v=1obZeHnAwz4)
* *`atomic<>` weapons* &ndash; H.Sutter @ C++ and Beyond (2012)
	* [Part I](https://www.youtube.com/watch?v=A8eCGOqgvH4)
	* [Part II](https://www.youtube.com/watch?v=KeLBd2EJLOU)

#### Hazard pointers

:link:

* [*Hazard pointer* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Hazard_pointer)
* [*Lock-free data structures with hazard pointers* &ndash; A.Alexandrescu, M.Michael @ Dr.Dobb's Journal (2004)](http://www.drdobbs.com/lock-free-data-structures-with-hazard-po/184401890)

#### Read-copy-update (RCU)

:link:

* [*Read-copy-update* &ndash; Wikipedia](https://en.wikipedia.org/wiki/Read-copy-update)
* [*Introduction to RCU* &ndash; P.E.McKenney](http://www2.rdrop.com/users/paulmck/RCU/)

:movie_camera:

* [*Read, copy, update, then what? RCU for non-kernel programmers* &ndash; F.Pikus @ CppCon (2017)](https://www.youtube.com/watch?v=rxQ5K9lo034)
* [*A lock-free concurrency toolkit for deferred reclamation and optimistic speculation* &ndash; P.E.McKenney @ CppCon (2016)](https://www.youtube.com/watch?v=uhgrD_B1RhQ&t=2289)

:anchor:

* [WG21/P0461R1: *Proposed RCU C++ API* (2017)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0461r1.pdf)
* [WG21/P0279R1: *Read-copy update (RCU) for C++* (2016)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0279r1.pdf)

### Concurrency and the standard library

:link:

* [*C++11 standard library extensions: Concurrency* &ndash; Standard C++ Foundation](https://isocpp.org/wiki/faq/cpp11-library-concurrency)

#### `std::atomic_shared_ptr`

:link:

* [*Why do we need `atomic_shared_ptr`?* &ndash; A.Williams (2015)](https://www.justsoftwaresolutions.co.uk/threading/why-do-we-need-atomic_shared_ptr.html)
* [*What is the difference between `std::shared_ptr` and `std::experimental::atomic_shared_ptr`?* &ndash; Stack Overflow](https://stackoverflow.com/questions/40223599/what-is-the-difference-between-stdshared-ptr-and-stdexperimentalatomic-sha)

#### `std::promise`

:link:

* [*What is `std::promise`?* &ndash; Stack Overflow](https://stackoverflow.com/questions/11004273/what-is-stdpromise)

### POSIX threads

:link:

* [*POSIX threads programming* &ndash; B.Barney](https://computing.llnl.gov/tutorials/pthreads/)

<!--

https://see.stanford.edu/materials/icsppcs107/23-Concurrency-Examples.pdf
https://stackoverflow.com/questions/5002046/atomicity-in-c-myth-or-reality

http://www.drdobbs.com/parallel/volatile-vs-volatile/212701484
-->
