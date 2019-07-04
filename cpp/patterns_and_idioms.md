# Patterns and idioms

## Table of contents

* [Introduction](#introduction)
* [Adapter](#adapter)
* [Double-checked locking](#double-checked-locking)
* [Passkey](#passkey)

---

## Introduction

:link: **Webpages**

* [Design patterns &ndash; Wikipedia](https://en.wikipedia.org/wiki/Design_Patterns)

---

## Adapter

:link: **Webpages**

* [Adapter pattern &ndash; Wikipedia](https://en.wikipedia.org/wiki/Adapter_pattern)

:movie_camera: **Videos**

* *Adapter design pattern* &ndash; D.Banas\
[Watch at YouTube](https://www.youtube.com/watch?v=qG286LQM6BU)

---

## Double-checked locking

:memo: **Notes**

* See also [Concurrency and parallelism - Multithreading](concurrency_and_parallelism.md#multithreading).

:link: **Webpages**

* [Double-checked locking &ndash; Wikipedia](https://en.wikipedia.org/wiki/Double-checked_locking)

:movie_camera: **Videos**

* *Live lock-free or deadlock (practical lock-free programming), Part I* &ndash; F.Pikus @ CppCon (2015).\
[Watch at YouTube](https://www.youtube.com/watch?v=lVBvHbJsg5Y)

---

## Passkey

:link: **Webpages**

<!-- https://stackoverflow.com/questions/3217390/clean-c-granular-friend-equivalent-answer-attorney-client-idiom/3218920#3218920-->

https://stackoverflow.com/questions/3324248/how-to-name-this-key-oriented-access-protection-pattern

* [Is this key-oriented access-protection pattern a known idiom? &ndash; Stack Overflow](https://stackoverflow.com/questions/3220009/is-this-key-oriented-access-protection-pattern-a-known-idiom)

:anchor: **Standards and technical reports**

* [`[[nodiscard]]` in the Library](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r0.pdf)

---

## Exceptions

### Exceptions in destructors

:link: **Webpages**

* [Destructors that throw &ndash; A.Krzemie&nacute;ski C++ blog (2011)](https://akrzemi1.wordpress.com/2011/09/21/destructors-that-throw/)
* [Throwing destructors &ndash; B.Kolpackov (2004)](https://www.kolpackov.net/projects/c++/eh/dtor-1.xhtml)

---

## Memory access

### Strict aliasing rule

:memo: **Notes**

* See also: [The standard library &ndash; `std::launder`](std_library.md#stdlaunder)

:link: **Webpages**

* [What is the strict aliasing rule? &ndash; Stack Overflow](https://stackoverflow.com/questions/98650/what-is-the-strict-aliasing-rule)

---

## Move semantics

:movie_camera: *Videos*

* *The nightmare of move semantics for trivial classes* &ndash; N.Josuttis @ CppCon (2017)\
[Watch at YouTube](https://www.youtube.com/watch?v=PNRju6_yn3o)

---

## References

### Lifetime of a temporary

:link: **Webpages**

* [Does a `const` reference class member prolong the life of a temporary? &ndash; Stack Overflow](https://stackoverflow.com/questions/2784262/does-a-const-reference-class-member-prolong-the-life-of-a-temporary)
* [Lifetime of a temporary &ndash; C++ reference](https://en.cppreference.com/w/cpp/language/reference_initialization#Lifetime_of_a_temporary)

---

## Structured bindings

:link: **Webpages**

* [Structured bindings and tuple of references &ndash; Stack Overflow](https://stackoverflow.com/questions/49628401/structured-bindings-and-tuple-of-references)

---

## Tricks

### Accessing private and protected members

:link: **Webpages**

* [Accessing private members &ndash; Stack Overflow](https://stackoverflow.com/questions/726096/accessing-private-members)
* [Access to private members. That's easy! &ndash; Johannes Schaub, litb's Blog](https://bloglitb.blogspot.com/2010/07/access-to-private-members-thats-easy.html)
