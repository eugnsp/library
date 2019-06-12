# The standard library

## Table of contents

* [General information](#general-information)
* [Algorithms](#algorithms)
* [Containers](#containers)
	* [`std::vector<bool>`](#stdvectorbool)
* [Regular expressions]($regular-expressions)
* [Smart pointers](#smart-pointers)
* [Strings](#strings)
* [Utilities](#utilities)
	* [Function objects](#function-objects)
	* [Pairs and tuples](#pairs-and-tuples)
	* [`std::launder`](#std-launder)
* [Tricks and subtleties](#tricks-and-subtleties)
* [Proposals](#proposals)
	* [`std::expected`](#stdexpected)

---

## General information

:book: **Books**

* *C++17 STL cookbook: Discover the latest enhancements to functional programming and lambda expressions.* &ndash; J.Galowicz. Packt Publishing, 2017\
[Book website](https://www.packtpub.com/application-development/c17-stl-cookbook)
* Ch. 18: *Concurrency* in *The C++ standard library: A tutorial and reference* &ndash; N.M.Josuttis. Addison-Wesley, 2<sup>nd</sup> ed., 2012\
[Book website](http://www.cppstdlib.com/)

## Algorithms

:movie_camera: **Videos**

* *STL algorithms: How to use them and how to write your own* &ndash; M.Clow @ ACCU (2016)\
[Watch at YouTube](https://www.youtube.com/watch?v=3nXLxMYXgWs)

## Containers

:movie_camera: **Videos**

* *If I had my 'druthers: A proposal for improving the containers in C++2x* &ndash; B.Steagall @ C++Now (2018)\
[Watch at YouTube](https://www.youtube.com/watch?v=bAE0qteS4Rk)

### `std::vector<bool>`

:link: **Webpages**

* [On `vector<bool>` &ndash; H.E.Hinnant (2012)](https://howardhinnant.github.io/onvectorbool.html)

## Regular expressions

:link: **Webpages**

* [Regular expressions library &ndash; C++ reference](https://en.cppreference.com/w/cpp/regex)

:movie_camera: **Videos**

* *Regular expressions in C++, present and future* &ndash; T.Shen @ CppCon (2016)\
[Watch at YouTube](https://www.youtube.com/watch?v=N_rkHzhXueo)

## Smart pointers

:link: **Webpages**

* [Why is `shared_ptr<void>` legal, while `unique_ptr<void>` is ill-formed? &ndash; Stack Overflow](https://stackoverflow.com/questions/39288891/why-is-shared-ptrvoid-legal-while-unique-ptrvoid-is-ill-formed)
* [What to use `std::optional` or `std::unique_ptr`? &ndash; Stack Overflow](https://stackoverflow.com/questions/44856701/what-to-use-stdoptional-or-stdunique-ptr?rq=1)

## Strings

:link: **Webpages**

* [Meaning of acronym SSO in the context of `std::string` &ndash; Stack Overflow](https://stackoverflow.com/questions/10315041/meaning-of-acronym-sso-in-the-context-of-stdstring)

## Utilities

:link: **Webpages**

* [Utility library &ndash; C++ reference](https://en.cppreference.com/w/cpp/utility)

### Function objects

:link: **Webpages**

* [Function objects &ndash; C++ reference](https://en.cppreference.com/w/cpp/utility/functional)

:movie_camera: **Videos**

* *`<functional>`: What's new, and proper usage* &ndash; S.T.Lavavej @ CppCon (2015)\
[Watch at YouTube](https://www.youtube.com/watch?v=zt7ThwVfap0)

### Pairs and tuples

:movie_camera: **Videos**

* *`tuple<>`: What's new and how it works* &ndash; S.T.Lavavej @ CppCon (2016)\
[Watch at YouTube](https://www.youtube.com/watch?v=JhgWFYfdIho)

### `std::launder`

:memo: **Notes**

* See also: [Core language &ndash; Strict aliasing rule](core_language.md#strict-aliasing-rule)

:link: **Webpages**

* [What is the purpose of `std::launder?` &ndash; Stack Overflow](https://stackoverflow.com/questions/39382501/what-is-the-purpose-of-stdlaunder)
* [Where can I find what `std::launder` really does? &ndash; Stack Overflow](https://stackoverflow.com/questions/53268089/where-can-i-find-what-stdlaunder-really-does)
* [`std::launder` &ndash; C++ reference](https://en.cppreference.com/w/cpp/utility/launder)

# Tricks and subtleties

:link: **Webpages**

* [In `std::exchange`, why is the second template parameter defaulted? &ndash; Stack Overflow](https://stackoverflow.com/questions/34876969/in-stdexchange-why-is-the-second-template-parameter-defaulted)

# Proposals

## `std::expected`

:link: **Webpages**

* [Proposal P0323R7: `std::expected` &ndash; V.Botet, J.F.Bastien (2018)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0323r7.html)
* [A proposal to add a utility class to represent expected monad &ndash; V.Botet, P.Talbot (2014)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4109.pdf)
