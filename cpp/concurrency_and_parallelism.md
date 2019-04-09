# Concurrency and parallelism

## Table of contents

* [GPU computing](#gpu-computing)
* [Multithreading](#multithreading)
	* [Synchronization mechanisms](#lock-free-data-structures-and-design)
		* [Hazard pointers](#hazard-pointers)
		* [Read-copy-update (RCU)](#read-copy-update-rcu)
	* [Concurrency and the standard library](#concurrency-and-the-standard-library)
		* [`std::atomic_shared_ptr` class](#stdatomicsharedptr-class)
---

## GPU computing

:movie_camera: **Videos**

* P.Steinbach @ Meeting C++ (2015) &ndash; *C++ on GPUs done right?*\
[Watch at YouTube](https://www.youtube.com/watch?v=z43l_LaOqnM)

## Multithreading

:movie_camera: **Videos**

* *Multithreading is the answer. What is the question?* &ndash; A.Sermersheim @ CppCon (2017).\
Watch at YouTube: [Part I](https://www.youtube.com/watch?v=GNw3RXr-VJk), [Part II](https://www.youtube.com/watch?v=sDLQWivf1-I)
* *C++11 multithreading done right?* &ndash; R.Grimm @ Meeting C++ (2014).\
[Watch at YouTube](https://www.youtube.com/watch?v=paK38WAq8WY)
* *`atomic<>` weapons* &ndash; H.Sutter @ C++ and Beyond (2012).\
Watch at YouTube: [Part I](https://www.youtube.com/watch?v=A8eCGOqgvH4), [Part II](https://www.youtube.com/watch?v=KeLBd2EJLOU)

:book: **Books**

* A.Williams. *C++ concurrency in action: Practical multithreading.* Manning, 2<sup>nd</sup> ed., 2019.\
[Book website](https://www.manning.com/books/c-plus-plus-concurrency-in-action-second-edition)
* Ch. 9: *Parallelism and concurrency* &ndash; J.Galowicz. *C++17 STL cookbook: Discover the latest enhancements to functional programming and lambda expressions.* Packt Publishing, 2017.\
[Book website](https://www.packtpub.com/application-development/c17-stl-cookbook)
* Ch. 18: *Concurrency* &ndash; N.M.Josuttis. *The C++ standard library: A tutorial and reference.* Addison-Wesley, 2<sup>nd</sup> ed., 2012.\
[Book website](http://www.cppstdlib.com/)

### Synchronization mechanisms

#### Hazard pointers

:link: **Webpages**

* [Lock-free data structures with hazard pointers &ndash; Dr.Dobb's Journal](http://www.drdobbs.com/lock-free-data-structures-with-hazard-po/184401890)

#### Read-copy-update (RCU)

:link: **Webpages**

* [Read-copy-update](https://en.wikipedia.org/wiki/Read-copy-update)
* [Introduction to RCU &ndash; Paul E. McKenney](http://www2.rdrop.com/users/paulmck/RCU/)

:movie_camera: **Videos**

* *Read, copy, update, then what? RCU for non-kernel programmers* &ndash; F.Pikus @ CppCon (2017).\
[Watch at YouTube](https://www.youtube.com/watch?v=rxQ5K9lo034)
* *A lock-free concurrency toolkit for deferred reclamation and optimistic speculation* &ndash; P.E.McKenney @ CppCon (2016).\
[Watch at YouTube](https://www.youtube.com/watch?v=uhgrD_B1RhQ&t=2289) (from 38:09)

:orange_book: **Standards and technical reports**

* [WG21/P0461R1: Proposed RCU C++ API (2017)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0461r1.pdf)
* [WG21/P0279R1: Read-copy update (RCU) for C++ (2016)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0279r1.pdf)

### Concurrency and the standard library

:link: **Webpages**

* [C++11 standard library extensions: Concurrency &ndash; Standard C++ Foundation](https://isocpp.org/wiki/faq/cpp11-library-concurrency)

#### `std::atomic_shared_ptr` class

:link: **Webpages**

* [Why do we need `atomic_shared_ptr`? &ndash; Anthony Williams (2015)](https://www.justsoftwaresolutions.co.uk/threading/why-do-we-need-atomic_shared_ptr.html)
* [What is the difference between `std::shared_ptr` and `std::experimental::atomic_shared_ptr`? &ndash;Stack Overflow](https://stackoverflow.com/questions/40223599/what-is-the-difference-between-stdshared-ptr-and-stdexperimentalatomic-sha)
