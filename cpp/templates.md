# Templates <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
	- [Applications](#applications)
- [Template arguments](#template-arguments)
	- [Argument deduction](#argument-deduction)
		- [Class template argument deduction (CTAD)](#class-template-argument-deduction-ctad)
		- [Deduction guides](#deduction-guides)
- [Concepts](#concepts)
	- [Standard concepts](#standard-concepts)
	- [Applications](#applications-1)
- [Function templates](#function-templates)
	- [Friend function templates](#friend-function-templates)
- [Parsing and compilation](#parsing-and-compilation)
	- [Optimization](#optimization)
		- [`extern template`](#extern-template)
	- [Two-phase lookup](#two-phase-lookup)
		- [Keywords `template` and `typename` as disambiguators](#keywords-template-and-typename-as-disambiguators)
- [SFINAE](#sfinae)
	- [SFINAE-friendliness](#sfinae-friendliness)
	- [Detection idiom](#detection-idiom)
- [Specialization](#specialization)
- [Explicit instantiation](#explicit-instantiation)
- [Tuples](#tuples)
- [Type traits](#type-traits)
- [Variadic templates](#variadic-templates)
	- [Type lists](#type-lists)
	- [Fold expressions](#fold-expressions)

---

## Introduction and overview

:link:

- S.Golodetz. [*Functional programming using C++ templates (Part I)*](https://accu.org/journals/overload/15/81/golodetz_1422/) – [Overload **81**](https://accu.org/journals/overload/overload81) (2007)
- S.Golodetz. [*Functional programming using C++ templates (Part II)*](https://members.accu.org/index.php/journals/1616) – [Overload **82**](https://accu.org/journals/overload/overload82) (2007)

:grey_question:

- [*Templates*](https://isocpp.org/wiki/faq/templates) – C++ FAQ

:movie_camera:

- J.Hagins. [*Template metaprogramming: Practical application*](https://www.youtube.com/watch?v=4YC6_77-iEY) – CppCon (2021)
- H.Matthews. [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScs) – ACCU (2017)
- W.E.Brown. *Modern template metaprogramming: A compendium.* [Part I](https://www.youtube.com/watch?v=Am2is2QCvxY), [Part II](https://www.youtube.com/watch?v=a0FliKwcwXE) – CppCon (2014)
- A.Modell. [*C++ advanced topics in templates*](https://www.youtube.com/watch?v=X30OwlsMWak) – Tech Talk (2014)
- M.Caisse. *Introduction to modern C++ techniques.* [Part I](https://www.youtube.com/watch?v=9TFV2JxX7L0), [Part II](https://www.youtube.com/watch?v=urshrBatNo4) – C++Now (2012)

:page_facing_up:

- B.Stroustrup. [*Parameterized types for C++*](https://www.usenix.org/legacy/publications/compsystems/1989/win_stroustrup.pdf) – Computing System **2**, 55 (1989)

:book:

- D.Vandevoorde, N.M.Josuttis, D.Gregor. [*C++ templates: The complete guide*](http://www.tmplbook.com/) – [Addison-Wesley](https://www.informit.com/store/c-plus-plus-templates-the-complete-guide-9780321714121) (2017)
- A.Alexandrescu. [*Modern C++ design: Generic programming and design patterns applied*](http://erdani.com/index.php/books/modern-c-design/) – [Addison-Wesley](https://www.informit.com/store/modern-c-plus-plus-design-generic-programming-and-design-9780201704310) (2001)

### Applications

:movie_camera:

- J.Gopel. [*Using modern C++ to eliminate virtual functions*](https://www.youtube.com/watch?v=gTNJXVmuRRA) – CppCon (2022)

---

## Template arguments

:link:

- J.M&uuml;ller. [*Tricks with default template arguments*](https://foonathan.net/2020/10/tricks-default-template-argument/) (2020)

### Argument deduction

:grey_question:

- [*What is a nondeduced context?*](https://stackoverflow.com/q/25245453) – Stack Overflow

:movie_camera:

- S.Meyers. [*Type deduction and why you care*](https://www.youtube.com/watch?v=wQxj20X-tIU) – CppCon (2014)

:anchor:

- [*Template argument deduction*](https://en.cppreference.com/w/cpp/language/template_argument_deduction) – C++ reference

#### Class template argument deduction (CTAD)

:link:

- A.O’Dwyer. [*Beware CTAD on `reverse_iterator`*](https://quuxplusone.github.io/blog/2022/08/02/reverse-iterator-ctad/) (2022)
- A.O’Dwyer. [*Thoughts on `-Wctad-maybe-unsupported`*](https://quuxplusone.github.io/blog/2022/10/07/wctad-maybe-unsupported/) (2022)
- R.Orr. [*CTAD – What is this new acronym all about?*](https://accu.org/journals/overload/26/143/orr_2465/) – [Overload **143**](https://accu.org/journals/overload/overload143) (2019)

:grey_question:

- [*Is `std::make_move_iterator` redundant since C++17’s class template argument deduction?*](https://stackoverflow.com/q/57762121) – Stack Overflow

:movie_camera:

- M.Clow. [*Class template argument deduction: History, how to ise it, and how to enable it for your classes*](https://www.youtube.com/watch?v=EPfPMW-rOtc) – CppCon (2022)
- T.Doumler. [*Class template argument deduction in C++17*](https://www.youtube.com/watch?v=UDs90b0yjjQ) – CppCon (2018)
- T.Doumler. [*Class template argument deduction in C++17*](https://www.youtube.com/watch?v=STJExxBU54M) – ACCU (2018)
- S.T.Lavavej. [*Class template argument deduction for everyone*](https://www.youtube.com/watch?v=-H-ut6j1BYU) – CppCon (2018)
- Z.Yuan. [*Class template argument deduction: A new abstraction*](https://www.youtube.com/watch?v=4X8gXzi8bx8) – CppCon (2017)

:anchor:

- M.Spertus, F.Vali, R.Smith. [*Template argument deduction for class templates*](https://wg21.link/p0091) – WG21/P0091

#### Deduction guides

:grey_question:

- [*What are template deduction guides and when should we use them?*](https://stackoverflow.com/q/40951697) – Stack Overflow

:anchor:

- [*Deduction for class templates*](https://en.cppreference.com/w/cpp/language/class_template_argument_deduction#Deduction_for_class_templates) – C++ reference

---

## Concepts

See also [*Concepts* – The standard library and proposals](core_language.md#concepts).

:link:

- A.Krzemieński. [*Concepts – case studies*](https://akrzemi1.wordpress.com/2021/09/16/concepts-case-studies/) (2021)
- A.Krzemieński. [*Semantic requirements in concepts*](https://akrzemi1.wordpress.com/2020/10/26/semantic-requirements-in-concepts/) (2020)
- A.Sutton. [*Defining concepts*](https://accu.org/journals/overload/24/131/sutton_2198/) – [Overload **131**](https://accu.org/journals/overload/overload131) (2016)
- A.Sutton. [*Introducing concepts*](https://accu.org/journals/overload/23/129/sutton_2157/) – [Overload **129**](https://accu.org/journals/overload/overload129) (2015)

:grey_question:

- [*How will concepts lite interact with universal references?*](https://stackoverflow.com/q/29182279) – Stack Overflow
- [*Why does `same_as` concept check type equality twice?*](https://stackoverflow.com/q/58509147) – Stack Overflow

:movie_camera:

- J.Garland. *Using concepts: C++ design in a concept world.* [Part I](https://www.youtube.com/watch?v=Ffu9C1BZ4-c), [Part II](https://www.youtube.com/watch?v=IXbf5lxGtr0) – C++Now (2021)
- R.Barkan. [*Semantic sugar: Tips for effective template library APIs*](https://www.youtube.com/watch?v=u0rvEMV8Qq4) – C++Now (2021)
- H.Matthews. [*C++ concepts for developers*](https://www.youtube.com/watch?v=ut40iShzqEY) – NDC (2019)
- R.Grimm. [*Concepts in C++20: Revolution or evolution*](https://www.youtube.com/watch?v=BXBnAmqZvpo) – CppCon (2019)
- B.Stroustrup. [*Concepts: The future of generic programming (the future is here)*](https://www.youtube.com/watch?v=HddFGPTAmtU) – CppCon (2018)

:anchor:

- W.E.Brown. [*`enable_if` vs.`requires`: A case study*](https://wg21.link/p0552) – WG21/P0552

### Standard concepts

:grey_question:

- [*Why is the `std::derived_from` concept implemented with an additional convertibility test that adds cv-qualifiers?*](https://stackoverflow.com/q/65915059) – Stack Overflow

### Applications

:link:

- A.Fertig. [*C++20 concepts applied – Safe bitmasks using scoped enums*](https://andreasfertig.blog/2024/01/cpp20-concepts-applied/) (2024)

---

## Function templates

:link:

- R.Chen. [*Function overloading is more flexible (and more convenient) than template function specialization*](https://devblogs.microsoft.com/oldnewthing/20250410-00/?p=111063) (2025)
- H.Sutter. [*Why not specialize function templates?*](http://www.gotw.ca/publications/mill17.htm)

:grey_question:

- [*Necessity of forward-declaring template functions*](https://stackoverflow.com/q/7255281) – Stack Overflow

:movie_camera:

- B.Saks. [*Back to basics: Function call resolution in C++*](https://www.youtube.com/watch?v=ab_RzvGAS1Q) – CppCon (2024)
- W.E.Brown. [*C++ function templates: How do they really work?*](https://www.youtube.com/watch?v=nfIX8yWlByY) – C++ on Sea (2019)
- W.E.Brown. [*C++ function templates: How do they really work?*](https://www.youtube.com/watch?v=NIDEjY5ywqU) – CppCon (2018)

### Friend function templates

:grey_question:

- [*Why do I get linker errors when I use template friends?*](https://isocpp.org/wiki/faq/templates#template-friends) – C++ FAQ
- [*Correct syntax for friend template function*](https://stackoverflow.com/q/42692050) – Stack Overflow

:movie_camera:

- D.Saks. [*Making new friends*](https://www.youtube.com/watch?v=POa_V15je8Y&t=1854s) – CppCon (2018)

---

## Parsing and compilation

:link:

- [*C++ keyword of the day: `export`*](https://blogs.msmvps.com/vandooren/2008/09/24/c-keyword-of-the-day-export/) (2008)

:grey_question:

- [*Why do templates use the angle bracket syntax?*](https://stackoverflow.com/q/43254027) – Stack Overflow
- [*How do compilers eliminate the need to write white spaces between closing angle brackets, when using template classes since C++ 11 standard?*](https://www.quora.com/How-do-C++-compilers-eliminate-the-need-to-write-white-spaces-between-closing-angle-brackets-when-using-template-classes-since-C++-11-standard) – Quora

:anchor:

- D.Vandevoorde. [*Right angle brackets*](https://wg21.link/n1757) – WG21/N1757

### Optimization

:link:

- C.DaCamara. [*Improving the state of debug performance in C++*](https://devblogs.microsoft.com/cppblog/improving-the-state-of-debug-performance-in-c/) (2022)
- A.O’Dwyer. [*Benchmarking Clang’s `-fbuiltin-std-forward`*](https://quuxplusone.github.io/blog/2022/12/24/builtin-std-forward/) (2022)
- D.Pallastrelli. [*Reduce compilation times with `extern template`*](https://arne-mertz.de/2019/02/extern-template-reduce-compile-times/) (2019)
- L.Dionne. [*Efficient parameter pack indexing*](https://ldionne.com/2015/11/29/efficient-parameter-pack-indexing/) (2015)
- A.Berg&eacute;. [*True story: Efficient packing*](http://talesofcpp.fusionfenix.com/post-22/true-story-efficient-packing) (2015)

:movie_camera:

- J.Brown. [*Reducing template compilation overhead, using C++11, 14, 17, and 20*](https://www.youtube.com/watch?v=TyiiNVA1syk) – CppCon (2019)

#### `extern template`

:grey_question:

- [*Using `extern template` with third-party header-only library*](https://stackoverflow.com/q/61477486) – Stack Overflow

### Two-phase lookup

> Names are resolved in two steps: first, non-dependent names are resolved at the time of template definition and, second, dependent names are resolved at the time of template instantiation.

:link:

- T.Gani et al. [*Two-phase name lookup support comes to MSVC*](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/) – Microsoft C++ team blog (2017)
- [*Two-phase lookup in C++ templates*](https://www.gonwan.com/2014/12/12/two-phase-lookup-in-c-templates/) (2014)
- E.Bendersky. [*Dependent name lookup for C++ templates*](https://eli.thegreenplace.net/2012/02/06/dependent-name-lookup-for-c-templates) (2012)

:grey_question:

- [*Why do I have to access template base class members through the `this` pointer?*](https://stackoverflow.com/q/4643074) – Stack Overflow

:anchor:

- J.Wilkinson, J.Dehnert, M.Austern. [*A proposed new template compilation model*](http://www.open-std.org/JTC1/SC22/WG21/docs/papers/1996/N0906.pdf) – WG21/N0906

#### Keywords `template` and `typename` as disambiguators

> ```cpp
> struct S { template<typename T> using type = T; };
> template<class T> void foo() { typename T::template type<int> x; }
>
> foo<S>();
> ```

:link:

- H.Sutter. [GotW #35: *Typename*](http://www.gotw.ca/gotw/035.htm)

:grey_question:

- [*Why don’t I need to specify `typename` before a dependent type in C++20?*](https://stackoverflow.com/q/61990971) – Stack Overflow
- [*Where and why do I have to put the `template` and `typename` keywords?*](https://stackoverflow.com/q/610245) – Stack Overflow

:movie_camera:

- A.Stepanov. [*Efficient programming with components* (part of Lec. 12)](https://www.youtube.com/watch?v=revYKQKg-eo&t=138) – A9 (2013)

---

## SFINAE

> "Substitution Failure Is Not An Error" – when substituting the explicitly specified or deduced type for the template parameter fails, the specialization is discarded from the overload set instead of causing a compile error.

:link:

- [*Substitution failure is not an error*](http://blog.olivierlanglois.net/index.php/2007/09/01/what_is_the_c_sfinae_principle) – Wikipedia

:grey_question:

- [*What exactly is the “immediate context” mentioned in the C++11 Standard for which SFINAE applies?*](https://stackoverflow.com/q/15260685) – Stack Overflow
- [*How does `std::void_t` work*](https://stackoverflow.com/q/27687389) – Stack Overflow
- [*SFINAE and partial class template specializations*](https://stackoverflow.com/q/30676839) – Stack Overflow
- [*SFINAE examples?*](https://stackoverflow.com/q/982808) – Stack Overflow

:anchor:

- [*SFINAE*](https://en.cppreference.com/w/cpp/language/sfinae) – C++ reference

### SFINAE-friendliness

:link:

- B.Ganetsky. [*A single-function SFINAE-friendly `std::apply`*](https://blog.ganets.ky/SfinaeApply/) (2024)

:grey_question:

- [*What is “Expression SFINAE”?*](https://stackoverflow.com/q/12654067) – Stack Overflow

### Detection idiom

- P.Barber. [*Unit testing compilation failure*](https://accu.org/journals/overload/20/108/barber_1928/) – [Overload **108**](https://accu.org/journals/overload/overload108) (2012)

---

## Specialization

:link:

- A.O’Dwyer. [*Don’t reopen namespace `std`*](https://quuxplusone.github.io/blog/2021/10/27/dont-reopen-namespace-std/) (2021)
- O.Wigley. [*Alternatives for partial template function specialisation*](https://accu.org/journals/overload/10/50/wigley_385/) – [Overload **50**](https://accu.org/journals/overload/overload50) (2002)

:grey_question:

- [*Partial specialization of template class copy constructor*](https://stackoverflow.com/q/16575257) – Stack Overflow

---

## Explicit instantiation

- A.O’Dwyer. [*Don’t explicitly instantiate `std` templates*](https://quuxplusone.github.io/blog/2021/08/06/dont-explicitly-instantiate-std-templates/) (2021)

---

## Tuples

:link:

- N.Deppe. [*Template metaprogramming. Part 3: Tuple iteration with recursion*](https://nilsdeppe.com/posts/tmpl-part3) (2017)
- N.Deppe. [*Template metaprogramming. Part 4: Recursion free tuple iteration*](https://nilsdeppe.com/posts/tmpl-part4) (2017)

:movie_camera:

- J.Brown. [*Reducing template compilation overhead, using C++11, 14, 17, and 20*](https://www.youtube.com/watch?v=TyiiNVA1syk&t=872) – CppCon (2019)
- A.Modell. [*C++ advanced topics in templates*](https://www.youtube.com/watch?v=X30OwlsMWak&t=2112) – Tech Talk (2014)

---

## Type traits

See also [*Type traits* – The standard library and Boost](std_library.md#type-traits).

:link:

- J.M&uuml;ller. [*Trivially copyable does not mean trivially copy constructible*](https://www.foonathan.net/2021/03/trivially-copyable/) (2021)
- J.M&uuml;ller. [*Technique: Immediately-invoked function expression for metaprogramming*](https://www.foonathan.net/2020/10/iife-metaprogramming/) (2020)
- N.Deppe. [*Template metaprogramming. Part 1*](https://nilsdeppe.com/posts/tmpl-part1) (2017)
- T.Frogley. [*An introduction to C++ traits*](https://accu.org/journals/overload/9/43/frogley_442/) – ACCU (2001)
- J.Maddock, S.Cleary. [*C++ type traits*](https://www.boost.org/doc/libs/1_31_0/libs/type_traits/c++_type_traits.htm) ([mirror](https://www.drdobbs.com/cpp/c-type-traits/184404270)) – Dr. Dobb’s Journal (2000)

:grey_question:

- [*What are the 15 classifications of types in C++?*](https://stackoverflow.com/q/27032790) – Stack Overflow

:movie_camera:

- J.Hagins. *Template Metaprogramming: Type Traits.* [*Part 1*](https://www.youtube.com/watch?v=tiAVWcjIF6o), [*Part 2*](https://www.youtube.com/watch?v=dLZcocFOb5Q) – CppCon (2020)
- A.O’Dwyer. [*The best type traits that C++ doesn’t have*](https://www.youtube.com/watch?v=MWBfmmg8-Yo) – C++Now (2018)
- H.Matthews. [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScs&t=2028) – ACCU (2017)

:anchor:

- [*C++ named requirements: `UnaryTypeTrait`*](https://en.cppreference.com/w/cpp/named_req/UnaryTypeTrait) – C++ reference
- [*C++ named requirements: `BinaryTypeTrait`*](https://en.cppreference.com/w/cpp/named_req/BinaryTypeTrait) – C++ reference
- [*C++ named requirements: `TransformationTrait`*](https://en.cppreference.com/w/cpp/named_req/TransformationTrait) – C++ reference

---

## Variadic templates

:link:

- E.Bendersky. [*Variadic templates in C++*](https://eli.thegreenplace.net/2014/variadic-templates-in-c/) (2014)

:grey_question:

- [*Variadic template pack expansion*](https://stackoverflow.com/q/25680461) – Stack Overflow

:movie_camera:

- M.Dominiak. [*“Variadic expansion in examples*](https://www.youtube.com/watch?v=Os5YLB5D2BU) – CppCon (2016)

:anchor:

- B.Seymour, S.T.Lavavej. [*Searching for types in parameter packs*](https://wg21.link/n4115) – WG21/N4115

### Type lists

:link:

- N.Deppe. [*Template metaprogramming. Part 2: Typelist*](https://nilsdeppe.com/posts/tmpl-part2) (2017)
- J.Galowicz. [*Type lists*](https://blog.galowicz.de/2016/05/08/compile_time_type_lists/) (2016)
- J.Galowicz. [*Type list compile time performance*](https://blog.galowicz.de/2016/06/25/cpp_template_type_list_performance/) (2016)
- J.Galowicz. [*Transformations between user input/output and type lists*](https://blog.galowicz.de/2016/05/14/converting_between_c_strings_and_type_lists/) (2016)

:book:

- Ch. 3: *Typelists* – A.Alexandrescu. [*Modern C++ design: Generic programming and design patterns applied*](http://erdani.com/index.php/books/modern-c-design/) (2001)

### Fold expressions

:link:

- J.M&uuml;ller. [*Nifty fold expression tricks*](https://www.foonathan.net/2020/05/fold-tricks/) (2020)
- A.O’Dwyer. [*Folding over `operator=`*](https://quuxplusone.github.io/blog/2020/05/07/assignment-operator-fold-expression/) (2020)

:anchor:

- [*Fold expression*](https://en.cppreference.com/w/cpp/language/fold) – C++ reference

<!--
http://www.gotw.ca/publications/mxc++-item-4.htm

https://stackoverflow.com/questions/281725/template-specialization-based-on-inherit-class

https://www.codeproject.com/Articles/268849/An-Idiots-Guide-to-Cplusplus-Templates-Part-2
https://www.hackcraft.net/cpp/templateinheritance/

https://stackoverflow.com/questions/55396786/check-if-class-is-a-template-specialization/55398444#55398444
 -->

<!-- https://stackoverflow.com/questions/59252363/why-is-my-class-non-default-constructible -->
