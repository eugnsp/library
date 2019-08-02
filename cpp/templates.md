# Templates

## Table of contents

* [Introduction and overview](#introduction-and-overview)
* [Function templates](#function-templates)
* [Syntax](#syntax)
	* [Keywords `template` and `typename` as disambiguators](#keywords-template-and-typename-as-disambiguators)
* [Two-phase lookup](#two-phase-lookup)
* [Type traits](#type-traits)

---

## Introduction and overview

:movie_camera:

* *Modern template metaprogramming: A compendium* &ndash; W.E.Brown @ CppCon (2014)\
Watch at YouTube: [Part I](https://www.youtube.com/watch?v=Am2is2QCvxY), [Part II](https://www.youtube.com/watch?v=a0FliKwcwXE)

:book: *Books*

* D.Vandevoorde, N.M.Josuttis, D.Gregor. *C++ templates: The complete guide.* Addison-Wesley, 2<sup>nd</sup> ed. (2017)\
[Book website](http://www.tmplbook.com/)

## Function templates

:link:

* [Necessity of forward-declaring template functions &ndash; Stack Overflow](https://stackoverflow.com/questions/7255281/necessity-of-forward-declaring-template-functions)
* [Why not specialize function templates? &ndash; Herb Sutter](http://www.gotw.ca/publications/mill17.htm)

## Syntax

### Keywords `template` and `typename` as disambiguators

:link:

* [Where and why do I have to put the `template` and `typename` keywords? &ndash; Stack Overflow](https://stackoverflow.com/a/613132/1625187)
* [GotW #35: Typename &ndash; H.Sutter (2009)](http://www.gotw.ca/gotw/035.htm)

:movie_camera:

* *Efficient programming with components* (part of lecture 12) &ndash; Alexander Stepanov, A9 (2013)\
[Watch at YouTube](https://www.youtube.com/watch?v=revYKQKg-eo&t=138) (from 2:18)

## Two-phase lookup

:link:

* [Two-phase name lookup support comes to MSVC &ndash; T.Gani, S.T.Lavavej, A.Marino, G.D.Reis, A.Pardoe, C++ team blog](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/)
* [Two-phase lookup in C++ templates](https://www.gonwan.com/2014/12/12/two-phase-lookup-in-c-templates/)

## Type traits

:link:

* [C++ type traits &ndash; J.Maddock, S.Cleary, Dr. Dobb's Journal](http://www.drdobbs.com/cpp/c-type-traits/184404270)
* [An introduction to C++ traits &ndash; T.Frogley, ACCU](https://accu.org/index.php/journals/442)
* [Type support &ndash; C++ reference](https://en.cppreference.com/w/cpp/types)

:movie_camera:

* *The best type traits that C++ doesn't have* &ndash; A.O'Dwyer @ C++Now (2018)\
[Watch at YouTube](https://www.youtube.com/watch?v=MWBfmmg8-Yo)
* *Type traits: what are they and why should I use them?* &ndash; M.Clow @ CppCon (2015)\
[Watch at YouTube](https://www.youtube.com/watch?v=VvbTP_k_Df4)

<!--
http://www.gotw.ca/publications/mxc++-item-4.htm

https://stackoverflow.com/questions/281725/template-specialization-based-on-inherit-class

https://www.codeproject.com/Articles/268849/An-Idiots-Guide-to-Cplusplus-Templates-Part-2
https://www.hackcraft.net/cpp/templateinheritance/

https://stackoverflow.com/questions/55396786/check-if-class-is-a-template-specialization/55398444#55398444
 -->
