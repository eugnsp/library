# Libraries and applications <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Dimensional analysis](#dimensional-analysis)
  - [Boost.Units](#boostunits)
  - [mp-units](#mp-units)
- [Space industry](#space-industry)
- [Boost](#boost)
  - [Boost.Iterator](#boostiterator)
  - [Boost.SmartPtr](#boostsmartptr)
    - [`boost::intrusive_ptr`](#boostintrusive_ptr)

---

## Dimensional analysis

### Boost.Units

> The Boost.Units library is an implementation of dimensional analysis in a general and extensible manner, treating it as a generic compile-time metaprogramming problem. Support for units and quantities (defined as a unit and associated value) for arbitrary unit system models and arbitrary value types is provided, as is a fine-grained general facility for unit conversions.

### mp-units

:link:

- [*`mp-units` – A physical quantities and units library for C++*](https://github.com/mpusz/mp-units)

:movie_camera:

- M.Pusz. [*`mp-units`: Lessons learned and a new C++ library design*](https://www.youtube.com/watch?v=l0rXdJfXLZc) – ACCU (2023)

---

## Space industry

:movie_camera:

- P.Nyman. [*C++ in space*](https://www.youtube.com/watch?v=VxNVGVW9nyI) – Sweden C++ (2023)
- J.Arrieta. [*Traveling the Solar system with C++: Programming rocket science*](https://www.youtube.com/watch?v=YXs3DFrZZL4) – CppCon (2017)

---

## Boost

:link:

- [Boost library incubator](http://blincubator.com/)

### Boost.Iterator

:anchor:

- [*Boost.Iterator: The iterator library*](https://www.boost.org/doc/libs/release/libs/iterator/)

### Boost.SmartPtr

:anchor:

- [*Boost.SmartPtr: The smart pointer library*](https://www.boost.org/doc/libs/release/libs/smart_ptr/)

#### `boost::intrusive_ptr`

> The `boost::intrusive_ptr` class is a smart pointer that stores a pointer to an object with an embedded reference count, which is managed somewhere outside the smart pointer.

:link:

- B.Wicht. [*Boost `intrusive_ptr`: Faster shared pointer*](https://baptiste-wicht.com/posts/2011/11/boost-intrusive_ptr.html) (2011)

:grey_question:

- [*Boost intrusive pointer*](https://stackoverflow.com/q/40137660) – Stack Overflow

:anchor:

- [*`intrusive_ptr`*](https://www.boost.org/doc/libs/release/libs/smart_ptr/smart_ptr.htm#intrusive_ptr) – Boost.SmartPtr
- I.Muerte. [*An intrusive smart pointer*](https://wg21.link/p0468) – WG21/P0468
