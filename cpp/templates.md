# Templates <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
- [Argument deduction](#argument-deduction)
- [Function templates](#function-templates)
- [Parsing and compilation](#parsing-and-compilation)
	- [Keywords `template` and `typename` as disambiguators](#keywords-template-and-typename-as-disambiguators)
	- [Optimization](#optimization)
	- [Two-phase lookup](#two-phase-lookup)
- [Policies](#policies)
- [Tuples](#tuples)
- [Type lists](#type-lists)
- [Type traits](#type-traits)

---

## Introduction and overview

:movie_camera:

- H.Matthews. [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScs) &ndash; ACCU (2017)
- W.E.Brown. *Modern template metaprogramming: A compendium.* [Part I](https://www.youtube.com/watch?v=Am2is2QCvxY), [Part II](https://www.youtube.com/watch?v=a0FliKwcwXE) &ndash; CppCon (2014)
- A.Modell. [*C++ advanced topics in templates*](https://www.youtube.com/watch?v=X30OwlsMWak) &ndash; Tech Talk (2014)
- M.Caisse. *Introduction to modern C++ techniques.* [Part I](https://www.youtube.com/watch?v=9TFV2JxX7L0), [Part II](https://www.youtube.com/watch?v=urshrBatNo4) &ndash; C++Now (2012)

:book:

- D.Vandevoorde, N.M.Josuttis, D.Gregor. [*C++ templates: The complete guide*](http://www.tmplbook.com/) &ndash; [Addison-Wesley Professional](https://www.informit.com/store/c-plus-plus-templates-the-complete-guide-9780321714121) (2017)
- A.Alexandrescu. [*Modern C++ design: Generic programming and design patterns applied*](http://erdani.com/index.php/books/modern-c-design/) &ndash; [Addison-Wesley Professional](https://www.informit.com/store/modern-c-plus-plus-design-generic-programming-and-design-9780201704310) (2001)

---

## Argument deduction

:link:

- [*Template argument deduction*](https://en.cppreference.com/w/cpp/language/template_argument_deduction) &ndash; C++ reference

:movie_camera:

- S.Meyers. [*Type deduction and why you care*](https://www.youtube.com/watch?v=wQxj20X-tIU) &ndash; CppCon (2014)

---

## Concepts

:link:

* [*How will concepts lite interact with universal references?*](https://stackoverflow.com/questions/29182279/how-will-concepts-lite-interact-with-universal-references) &ndash; Stack Overflow

:movie_camera:

* B.Stroustrup. [*Concepts: The future of generic programming (the future is here)*](https://www.youtube.com/watch?v=HddFGPTAmtU) &ndash; CppCon (2018)

:anchor:

* W.E.Brown. [*`enable_if` vs.`requires`: A case study*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0552r0.pdf) &ndash; WG21/P0552R0 (2017)

---

## Function templates

:link:

- [*Necessity of forward-declaring template functions*](https://stackoverflow.com/questions/7255281/necessity-of-forward-declaring-template-functions) &ndash; Stack Overflow
- H.Sutter. [*Why not specialize function templates?*](http://www.gotw.ca/publications/mill17.htm)

---

## Parsing and compilation

### Keywords `template` and `typename` as disambiguators

> ```cpp
> struct S { template<typename T> using type = T; };
> template<class T> void foo() { typename T::template type<int> x; }
>
> foo<S>();
> ```

:link:

- [*Where and why do I have to put the `template` and `typename` keywords?*](https://stackoverflow.com/a/613132/1625187) &ndash; Stack Overflow
- H.Sutter. [GotW #35: *Typename*](http://www.gotw.ca/gotw/035.htm) &ndash; Guru of the Week (2009)

:movie_camera:

- A.Stepanov. [*Efficient programming with components* (part of Lec. 12)](https://www.youtube.com/watch?v=revYKQKg-eo&t=138) &ndash; A9 (2013)

### Optimization

:link:

- L.Dionne. [*Efficient parameter pack indexing*](https://ldionne.com/2015/11/29/efficient-parameter-pack-indexing/) (2015)
- A.Berg&eacute;. [*True story: Efficient packing*](http://talesofcpp.fusionfenix.com/post-22/true-story-efficient-packing) (2015)

:movie_camera:

- J.Brown. [*Reducing template compilation overhead, using C++11, 14, 17, and 20*](https://www.youtube.com/watch?v=TyiiNVA1syk) &ndash; CppCon (2019)

### Two-phase lookup

> Names are resolved in two steps: first, non-dependent names are resolved at the time of template definition and, second, dependent names are resolved at the time of template instantiation.

:link:

- T.Gani et al. [*Two-phase name lookup support comes to MSVC*](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/) &ndash; Microsoft C++ team blog (2017)
- [*Two-phase lookup in C++ templates*](https://www.gonwan.com/2014/12/12/two-phase-lookup-in-c-templates/) (2014)
- E.Bendersky. [*Dependent name lookup for C++ templates*](https://eli.thegreenplace.net/2012/02/06/dependent-name-lookup-for-c-templates) (2012)

---

## Policies

:movie_camera:

- H.Matthews. [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScs&t=2387) &ndash; ACCU (2017)

:book:

- Ch. 1: *Policy-based class design* &ndash; A.Alexandrescu. [*Modern C++ design: Generic programming and design patterns applied*](http://erdani.com/index.php/books/modern-c-design/) &ndash; [Addison-Wesley Professional](https://www.informit.com/store/modern-c-plus-plus-design-generic-programming-and-design-9780201704310) (2001)

---

## Tuples

:link:

- N.Deppe. [*Template metaprogramming. Part 3: Tuple iteration with recursion*](https://nilsdeppe.com/posts/tmpl-part3) (2017)
- N.Deppe. [*Template metaprogramming. Part 4: Recursion free tuple iteration*](https://nilsdeppe.com/posts/tmpl-part4) (2017)

:movie_camera:

- J.Brown. [*Reducing template compilation overhead, using C++11, 14, 17, and 20*](https://www.youtube.com/watch?v=TyiiNVA1syk&t=872) &ndash; CppCon (2019)
- A.Modell. [*C++ advanced topics in templates*](https://www.youtube.com/watch?v=X30OwlsMWak&t=2112) &ndash; Tech Talk (2014)

## Type lists

:link:

- N.Deppe. [*Template metaprogramming. Part 2: Typelist*](https://nilsdeppe.com/posts/tmpl-part2) (2017)
- J.Galowicz. [*Type lists*](https://blog.galowicz.de/2016/05/08/compile_time_type_lists/) (2016)
- J.Galowicz. [*Type list compile time performance*](https://blog.galowicz.de/2016/06/25/cpp_template_type_list_performance/) (2016)
- J.Galowicz. [*Transformations between user input/output and type lists*](https://blog.galowicz.de/2016/05/14/converting_between_c_strings_and_type_lists/) (2016)

:book:

- Ch. 3: *Typelists* &ndash; A.Alexandrescu. [*Modern C++ design: Generic programming and design patterns applied*](http://erdani.com/index.php/books/modern-c-design/) &ndash; [Addison-Wesley Professional](https://www.informit.com/store/modern-c-plus-plus-design-generic-programming-and-design-9780201704310) (2001)

## Type traits

See also [*Type traits* &ndash; The standard library and Boost](std_library.md#type-traits).

:link:

- J.Maddock, S.Cleary. [*C++ type traits*](https://www.boost.org/doc/libs/1_31_0/libs/type_traits/c++_type_traits.htm) &ndash; Dr. Dobb’s Journal (2000)
- T.Frogley. [*An introduction to C++ traits*](https://accu.org/index.php/journals/442) &ndash; ACCU (2001)
- N.Deppe. [*Template metaprogramming. Part 1*](https://nilsdeppe.com/posts/tmpl-part1) (2017)

:movie_camera:

- A.O’Dwyer. [*The best type traits that C++ doesn’t have*](https://www.youtube.com/watch?v=MWBfmmg8-Yo) &ndash; C++Now (2018)
- H.Matthews. [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScs&t=2028) &ndash; ACCU (2017)

<!--
http://www.gotw.ca/publications/mxc++-item-4.htm

https://stackoverflow.com/questions/281725/template-specialization-based-on-inherit-class

https://www.codeproject.com/Articles/268849/An-Idiots-Guide-to-Cplusplus-Templates-Part-2
https://www.hackcraft.net/cpp/templateinheritance/

https://stackoverflow.com/questions/55396786/check-if-class-is-a-template-specialization/55398444#55398444
 -->
