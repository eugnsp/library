# Core language

## Table of contents

* [ABI](#abi)
	* [Itanium C++ ABI](#itanium-c-abi)
* [Attributes](#attributes)
	* [`[[nodiscard]]`](#nodiscard)
* [Exceptions](#exceptions)
	* [Exceptions in destructors](#exceptions-in-destructors)
* [Floating-point types](#floating-point-types)
* [Friend declaration](#friend-declaration)
* [Memory access](#memory-access)
	* [Strict aliasing rule](#strict-aliasing-rule)
* [References](#references)
	* [Lifetime of a temporary](#lifetime-of-a-temporary)
	* [Rvalue references](#rvalue-references)
* [Structured bindings](#structured-bindings)
* [Templates](#templates)
* [Tricks](#tricks)
	* [Accessing private and protected members](#accessing-private-and-protected-members)

---

## ABI

### Itanium C++ ABI

> The Itanium C++ ABI is an ABI for C++. As an ABI, it gives precise rules for implementing the language, ensuring that separately-compiled parts of a program can successfully interoperate. It is not platform-specific and can be layered portably on top of an arbitrary C ABI. It is used as the standard C++ ABI for many major operating systems on all major architectures, and is implemented in many major C++ compilers, including GCC and Clang.

:link: **Webpages**

* [Itanium C++ ABI](https://itanium-cxx-abi.github.io/cxx-abi/abi.html)

---

## Attributes

### `[[nodiscard]]`

> This attribute encourages the compiler to issue a warning if the return value is discarded.

:memo: **Notes**

* Conservative approach suggested by N.Josuttis:
	* Should be added:
		* *existing APIs*: not using the return value always is a "huge mistake"; not using the return value is a source of trouble and easily can happen;
		* *new APIs*: not using the return value is usually an error.
	* Should not be added:
		* *existing APIs*: not using the return value is a possible/common way of programming at least for some input; not using the return value makes no sense but doesn't hurt.

:link: **Webpages**

* [What's the reason for not using C++17's `[[nodiscard]]` almost everywhere in new code? &ndash; Software Engineering](https://softwareengineering.stackexchange.com/questions/363169/whats-the-reason-for-not-using-c17s-nodiscard-almost-everywhere-in-new-c)

:anchor: **Standards and technical reports**

* [`[[nodiscard]]` in the Library](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r0.pdf)

---

## Exceptions

:link: **Webpages**

* [When and how to use exceptions &ndash; H.Sutter, Dr.Dobb's Journal (2004)](http://www.drdobbs.com/when-and-how-to-use-exceptions/184401836)
* [Exceptions &ndash; C++ reference](https://en.cppreference.com/w/cpp/language/exceptions)

### Exceptions in destructors

:link: **Webpages**

* [Destructors that throw &ndash; A.Krzemie&nacute;ski C++ blog (2011)](https://akrzemi1.wordpress.com/2011/09/21/destructors-that-throw/)
* [Throwing destructors &ndash; B.Kolpackov (2004)](https://www.kolpackov.net/projects/c++/eh/dtor-1.xhtml)

---

## Floating-point types

:link: **Webpages**

* [Byte swapping floating point types &ndash; D.Howard](https://web.archive.org/web/20100125081223/http://www.dmh2000.com/cpp/dswap.shtml)

---

## Friend declaration

### Hidden friends

:link: **Webpages**

* [The power of hidden friends in C++ &ndash; A.Williams (2019)](https://www.justsoftwaresolutions.co.uk/cplusplus/hidden-friends.html)

:anchor: **Standards and technical reports**

* [WG21/P1601R0: Recommendations for specifying "hidden friends" (2019)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1601r0.pdf)

---

## Memory access

### Strict aliasing rule

:memo: **Notes**

* See also: [The standard library &ndash; `std::launder`](std_library.md#stdlaunder)

:link: **Webpages**

* [What is the strict aliasing rule? &ndash; Stack Overflow](https://stackoverflow.com/questions/98650/what-is-the-strict-aliasing-rule)

---

## References

:link: **Webpages**

* [Is null reference possible? &ndash; Stack Overflow](https://stackoverflow.com/questions/4364536/is-null-reference-possible)

### Lifetime of a temporary

:link: **Webpages**

* [Does a `const` reference class member prolong the life of a temporary? &ndash; Stack Overflow](https://stackoverflow.com/questions/2784262/does-a-const-reference-class-member-prolong-the-life-of-a-temporary)
* [Lifetime of a temporary &ndash; C++ reference](https://en.cppreference.com/w/cpp/language/reference_initialization#Lifetime_of_a_temporary)

### Rvalue references

:link: **Webpages**

* [A brief introduction to rvalue references &ndash; H.E.Hinnant, B.Stroustrup, B.Kozicki (2008)](https://www.artima.com/cppsource/rvalue.html)
* [C++ rvalue references explained &ndash; T.Becker (2013)](http://thbecker.net/articles/rvalue_references/section_01.html)
* [What is move semantics? &ndash; Stack Overflow](https://stackoverflow.com/questions/3106110/what-is-move-semantics)
* [Rvalues, lvalues and formal definitions &ndash; Stack Overflow](https://stackoverflow.com/questions/56716647/rvalues-lvalues-and-formal-definitions)
* [Pass by value vs pass by rvalue reference &ndash; Stack Overflow](https://stackoverflow.com/questions/37935393/pass-by-value-vs-pass-by-rvalue-reference)

:movie_camera: *Videos*

* *The nightmare of move semantics for trivial classes* &ndash; N.Josuttis @ CppCon (2017)\
[Watch at YouTube](https://www.youtube.com/watch?v=PNRju6_yn3o)

---

## Structured bindings

:link: **Webpages**

* [Structured bindings and tuple of references &ndash; Stack Overflow](https://stackoverflow.com/questions/49628401/structured-bindings-and-tuple-of-references)

## Templates

See [Templates](templates.md).

---

## Tricks

### Accessing private and protected members

:link: **Webpages**

* [Accessing private members &ndash; Stack Overflow](https://stackoverflow.com/questions/726096/accessing-private-members)
* [Access to private members. That's easy! &ndash; Johannes Schaub, litb's Blog](https://bloglitb.blogspot.com/2010/07/access-to-private-members-thats-easy.html)
