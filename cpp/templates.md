# Templates

## Table of contents

* [Introduction and overview](#introduction-and-overview)
* [Function templates](#function-templates)
* [Parsing](#parsing)
	* [Keywords `template` and `typename` as disambiguators](#keywords-template-and-typename-as-disambiguators)
	* [Two-phase lookup](#two-phase-lookup)
* [Policies](#policies)
* [Type traits](#type-traits)

---

## Introduction and overview

:movie_camera:

* [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScs) &ndash; H.Matthews @ ACCU (2017)
* *Modern template metaprogramming: A compendium* &ndash; W.E.Brown @ CppCon (2014)
	* [Part I](https://www.youtube.com/watch?v=Am2is2QCvxY)
	* [Part II](https://www.youtube.com/watch?v=a0FliKwcwXE)

:book: *Books*

* [*C++ templates: The complete guide*](http://www.tmplbook.com/) &ndash; D.Vandevoorde, N.M.Josuttis, D.Gregor. Addison-Wesley, 2<sup>nd</sup> ed. (2017)

---

## Policies

---

## Function templates

:link:

* [*Necessity of forward-declaring template functions*](https://stackoverflow.com/questions/7255281/necessity-of-forward-declaring-template-functions) &ndash; Stack Overflow
* [*Why not specialize function templates?*](http://www.gotw.ca/publications/mill17.htm) &ndash; H.Sutter

---

## Parsing

### Keywords `template` and `typename` as disambiguators

:link:

* [*Where and why do I have to put the `template` and `typename` keywords?*](https://stackoverflow.com/a/613132/1625187) &ndash; Stack Overflow
* [GotW #35: *Typename*](http://www.gotw.ca/gotw/035.htm) &ndash; H.Sutter (2009)

:movie_camera:

* [*Efficient programming with components* (part of lecture 12)](https://www.youtube.com/watch?v=revYKQKg-eo&t=138) &ndash; A.Stepanov, A9 (2013)

### Two-phase lookup

:link:

* [*Two-phase name lookup support comes to MSVC* &ndash; T.Gani, et al. @ C++ team blog](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/)
* [*Two-phase lookup in C++ templates*](https://www.gonwan.com/2014/12/12/two-phase-lookup-in-c-templates/)

---

## Policies

:movie_camera:

* [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScs&t=2387) &ndash; H.Matthews @ ACCU (2017)

---

## Type traits

:link:

* [*Type support*](https://en.cppreference.com/w/cpp/types) &ndash; C++ reference
* [*C++ type traits*](http://www.drdobbs.com/cpp/c-type-traits/184404270) &ndash; J.Maddock, S.Cleary @ Dr. Dobb's Journal
* [*An introduction to C++ traits*](https://accu.org/index.php/journals/442) &ndash; T.Frogley @ ACCU

:movie_camera:

* [*The best type traits that C++ doesn't have*](https://www.youtube.com/watch?v=MWBfmmg8-Yo) &ndash; A.O'Dwyer @ C++Now (2018)
* [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScs&t=2028) &ndash; H.Matthews @ ACCU (2017)
* [*Type traits: what are they and why should I use them?*](https://www.youtube.com/watch?v=VvbTP_k_Df4) &ndash; M.Clow @ CppCon (2015)


<!--
http://www.gotw.ca/publications/mxc++-item-4.htm

https://stackoverflow.com/questions/281725/template-specialization-based-on-inherit-class

https://www.codeproject.com/Articles/268849/An-Idiots-Guide-to-Cplusplus-Templates-Part-2
https://www.hackcraft.net/cpp/templateinheritance/

https://stackoverflow.com/questions/55396786/check-if-class-is-a-template-specialization/55398444#55398444
 -->
