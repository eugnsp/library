# Templates <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
- [Argument deduction](#argument-deduction)
- [Concepts](#concepts)
- [Function templates](#function-templates)
	- [Friend function templates](#friend-function-templates)
- [Parsing and compilation](#parsing-and-compilation)
	- [Optimization](#optimization)
	- [Two-phase lookup](#two-phase-lookup)
	- [Keywords template and typename as disambiguators](#keywords-template-and-typename-as-disambiguators)
- [Policies](#policies)
- [SFINAE](#sfinae)
- [Specialization](#specialization)
- [Tuples](#tuples)
- [Type lists](#type-lists)
- [Type traits](#type-traits)

---

## Introduction and overview

:grey_question:

- [*Templates*](https://isocpp.org/wiki/faq/templates) – C++ FAQ

:movie_camera:

- H.Matthews. [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScs) – ACCU (2017)
- W.E.Brown. *Modern template metaprogramming: A compendium.* [Part I](https://www.youtube.com/watch?v=Am2is2QCvxY), [Part II](https://www.youtube.com/watch?v=a0FliKwcwXE) – CppCon (2014)
- A.Modell. [*C++ advanced topics in templates*](https://www.youtube.com/watch?v=X30OwlsMWak) – Tech Talk (2014)
- M.Caisse. *Introduction to modern C++ techniques.* [Part I](https://www.youtube.com/watch?v=9TFV2JxX7L0), [Part II](https://www.youtube.com/watch?v=urshrBatNo4) – C++Now (2012)

:page_facing_up:

- B.Stroustrup. [*Parameterized types for C++*](https://www.usenix.org/legacy/publications/compsystems/1989/win_stroustrup.pdf) – Computing System **2**, 55 (1989)

:book:

- D.Vandevoorde, N.M.Josuttis, D.Gregor. [*C++ templates: The complete guide*](http://www.tmplbook.com/) – [Addison-Wesley Professional](https://www.informit.com/store/c-plus-plus-templates-the-complete-guide-9780321714121) (2017)
- A.Alexandrescu. [*Modern C++ design: Generic programming and design patterns applied*](http://erdani.com/index.php/books/modern-c-design/) – [Addison-Wesley Professional](https://www.informit.com/store/modern-c-plus-plus-design-generic-programming-and-design-9780201704310) (2001)

---

## Argument deduction

:link:

- R.Orr. [*CTAD – What is this new acronym all about?*](https://accu.org/index.php/journals/2465) – [Overload **143**](https://accu.org/index.php/journals/c382/), 13 (2019)

:movie_camera:

- S.Meyers. [*Type deduction and why you care*](https://www.youtube.com/watch?v=wQxj20X-tIU) – CppCon (2014)

:anchor:

- [*Template argument deduction*](https://en.cppreference.com/w/cpp/language/template_argument_deduction) – C++ reference
- M.Spertus, F.Vali, R.Smith. [*Template argument deduction for class templates*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html) – WG21/P0091R3 (2017)
- M.Spertus, F.Vali, R.Smith. [*Template argument deduction for class templates*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0091r4.html) – WG21/P0091R4 (2017)

---

## Concepts

See also [*Concepts* – The standard library, Boost and proposals](core_language.md#concepts).

:link:

- A.Sutton. [*Introducing concepts*](https://accu.org/index.php/journals/2157) – [Overload **129**](https://accu.org/index.php/journals/c354/) (2015)
- A.Sutton. [*Defining concepts*](https://accu.org/index.php/journals/2198) – [Overload **131**](https://accu.org/index.php/journals/c358/) (2016)

:grey_question:

- [*How will concepts lite interact with universal references?*](https://stackoverflow.com/q/29182279) – Stack Overflow

:movie_camera:

- H.Matthews. [*C++ concepts for developers*](https://www.youtube.com/watch?v=ut40iShzqEY) – NDC (2019)
- B.Stroustrup. [*Concepts: The future of generic programming (the future is here)*](https://www.youtube.com/watch?v=HddFGPTAmtU) – CppCon (2018)

:anchor:

- W.E.Brown. [*`enable_if` vs.`requires`: A case study*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0552r0.pdf) – WG21/P0552R0 (2017)

---

## Function templates

:link:

- H.Sutter. [*Why not specialize function templates?*](http://www.gotw.ca/publications/mill17.htm)

:grey_question:

- [*Necessity of forward-declaring template functions*](https://stackoverflow.com/q/7255281) – Stack Overflow

### Friend function templates

:grey_question:

- [*Why do I get linker errors when I use template friends?*](https://isocpp.org/wiki/faq/templates#template-friends) – C++ FAQ
- [*Correct syntax for friend template function*](https://stackoverflow.com/q/42692050) – Stack Overflow

---

## Parsing and compilation

:link:

- [*C++ keyword of the day: `export`*](https://blogs.msmvps.com/vandooren/2008/09/24/c-keyword-of-the-day-export/) (2008)
- [*Why do templates use the angle bracket syntax?*](https://stackoverflow.com/q/43254027) – Stack Overflow
- [*How do compilers eliminate the need to write white spaces between closing angle brackets, when using template classes since C++ 11 standard?*](https://www.quora.com/How-do-C++-compilers-eliminate-the-need-to-write-white-spaces-between-closing-angle-brackets-when-using-template-classes-since-C++-11-standard) – Quora

:anchor:

- D.Vandevoorde. [*Right angle brackets*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1757.html) – WG21/N1757 (2005)

### Optimization

:link:

- L.Dionne. [*Efficient parameter pack indexing*](https://ldionne.com/2015/11/29/efficient-parameter-pack-indexing/) (2015)
- A.Berg&eacute;. [*True story: Efficient packing*](http://talesofcpp.fusionfenix.com/post-22/true-story-efficient-packing) (2015)

:movie_camera:

- J.Brown. [*Reducing template compilation overhead, using C++11, 14, 17, and 20*](https://www.youtube.com/watch?v=TyiiNVA1syk) – CppCon (2019)

### Two-phase lookup

> Names are resolved in two steps: first, non-dependent names are resolved at the time of template definition and, second, dependent names are resolved at the time of template instantiation.

:link:

- T.Gani et al. [*Two-phase name lookup support comes to MSVC*](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/) – Microsoft C++ team blog (2017)
- [*Two-phase lookup in C++ templates*](https://www.gonwan.com/2014/12/12/two-phase-lookup-in-c-templates/) (2014)
- E.Bendersky. [*Dependent name lookup for C++ templates*](https://eli.thegreenplace.net/2012/02/06/dependent-name-lookup-for-c-templates) (2012)

:grey_question:

- [*Why do I have to access template base class members through the `this` pointer?*](https://stackoverflow.com/q/4643074) – Stack Overflow

### Keywords `template` and `typename` as disambiguators

> ```cpp
> struct S { template<typename T> using type = T; };
> template<class T> void foo() { typename T::template type<int> x; }
>
> foo<S>();
> ```

:link:

- [*Where and why do I have to put the `template` and `typename` keywords?*](https://stackoverflow.com/q/610245) – Stack Overflow
- H.Sutter. [GotW #35: *Typename*](http://www.gotw.ca/gotw/035.htm)

:movie_camera:

- A.Stepanov. [*Efficient programming with components* (part of Lec. 12)](https://www.youtube.com/watch?v=revYKQKg-eo&t=138) – A9 (2013)

---

## Policies

:movie_camera:

- H.Matthews. [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScs&t=2387) – ACCU (2017)

:book:

- Ch. 1: *Policy-based class design* – A.Alexandrescu. [*Modern C++ design: Generic programming and design patterns applied*](http://erdani.com/index.php/books/modern-c-design/) – [Addison-Wesley Professional](https://www.informit.com/store/modern-c-plus-plus-design-generic-programming-and-design-9780201704310) (2001)

---

## SFINAE

> "Substitution Failure Is Not An Error" – when substituting the explicitly specified or deduced type for the template parameter fails, the specialization is discarded from the overload set instead of causing a compile error.

:link:

- [*Substitution failure is not an error*](http://blog.olivierlanglois.net/index.php/2007/09/01/what_is_the_c_sfinae_principle) – Wikipedia

:grey_question:

- [*What is “Expression SFINAE”?*](https://stackoverflow.com/q/12654067) – Stack Overflow
- [*How does `std::void_t` work*](https://stackoverflow.com/q/27687389) – Stack Overflow
- [*SFINAE examples?*](https://stackoverflow.com/q/982808) – Stack Overflow

:anchor:

- [*SFINAE*](https://en.cppreference.com/w/cpp/language/sfinae) – C++ reference

---

## Specialization

:grey_question:

- [*Partial specialization of template class copy constructor*](https://stackoverflow.com/q/16575257) – Stack Overflow

---

## Tuples

:link:

- N.Deppe. [*Template metaprogramming. Part 3: Tuple iteration with recursion*](https://nilsdeppe.com/posts/tmpl-part3) (2017)
- N.Deppe. [*Template metaprogramming. Part 4: Recursion free tuple iteration*](https://nilsdeppe.com/posts/tmpl-part4) (2017)

:movie_camera:

- J.Brown. [*Reducing template compilation overhead, using C++11, 14, 17, and 20*](https://www.youtube.com/watch?v=TyiiNVA1syk&t=872) – CppCon (2019)
- A.Modell. [*C++ advanced topics in templates*](https://www.youtube.com/watch?v=X30OwlsMWak&t=2112) – Tech Talk (2014)

---

## Type lists

:link:

- N.Deppe. [*Template metaprogramming. Part 2: Typelist*](https://nilsdeppe.com/posts/tmpl-part2) (2017)
- J.Galowicz. [*Type lists*](https://blog.galowicz.de/2016/05/08/compile_time_type_lists/) (2016)
- J.Galowicz. [*Type list compile time performance*](https://blog.galowicz.de/2016/06/25/cpp_template_type_list_performance/) (2016)
- J.Galowicz. [*Transformations between user input/output and type lists*](https://blog.galowicz.de/2016/05/14/converting_between_c_strings_and_type_lists/) (2016)

:book:

- Ch. 3: *Typelists* – A.Alexandrescu. [*Modern C++ design: Generic programming and design patterns applied*](http://erdani.com/index.php/books/modern-c-design/) – [Addison-Wesley Professional](https://www.informit.com/store/modern-c-plus-plus-design-generic-programming-and-design-9780201704310) (2001)

---

## Type traits

See also [*Type traits* – The standard library and Boost](std_library.md#type-traits).

:link:

- J.Maddock, S.Cleary. [*C++ type traits*](https://www.boost.org/doc/libs/1_31_0/libs/type_traits/c++_type_traits.htm) – Dr. Dobb’s Journal (2000)
- T.Frogley. [*An introduction to C++ traits*](https://accu.org/index.php/journals/442) – ACCU (2001)
- N.Deppe. [*Template metaprogramming. Part 1*](https://nilsdeppe.com/posts/tmpl-part1) (2017)

:movie_camera:

- A.O’Dwyer. [*The best type traits that C++ doesn’t have*](https://www.youtube.com/watch?v=MWBfmmg8-Yo) – C++Now (2018)
- H.Matthews. [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScs&t=2028) – ACCU (2017)

<!--
http://www.gotw.ca/publications/mxc++-item-4.htm

https://stackoverflow.com/questions/281725/template-specialization-based-on-inherit-class

https://www.codeproject.com/Articles/268849/An-Idiots-Guide-to-Cplusplus-Templates-Part-2
https://www.hackcraft.net/cpp/templateinheritance/

https://stackoverflow.com/questions/55396786/check-if-class-is-a-template-specialization/55398444#55398444
 -->

<!-- https://stackoverflow.com/questions/59252363/why-is-my-class-non-default-constructible -->
