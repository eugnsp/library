# Core language

## Table of contents

* [Attributes](#attributes)
	* [`[[nodiscard]]`](#nodiscard)
* [Exceptions](#exceptions)
	* [Exceptions in destructors](#exceptions-in-destructors)
* [Move semantics](#move-semantics)
* [Tricks](#tricks)
	* [Accessing private and protected members](#accessing-private-and-protected-members)

---

## Attributes

### `[[[nodiscard]]`

> This attribute encourages the compiler to issue a warning if the return value is discarded.

:memo: **Notes**

* Conservative approach suggested by N.Josuttis:
	* Should be added:
		* *existing APIs*: not using the return value always is a "huge mistake"; not using the return value is a source of trouble and easily can happen;
		* *new APIs*: not using the return value is usually an error.
	* Should not be added:
		* *existing APIs*: not using the return value is a possible/common way of programming at least for some input; not using the return value makes no sense but doesn't hurt.

:anchor: **Standards and technical reports**

* [`[[nodiscard]]` in the Library](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r0.pdf)

## Exceptions

### Exceptions in destructors

:link: **Webpages**

* [Destructors that throw &ndash; A.Krzemie&nacute;ski C++ blog (2011)](https://akrzemi1.wordpress.com/2011/09/21/destructors-that-throw/)
* [Throwing destructors &ndash; B.Kolpackov (2004)](https://www.kolpackov.net/projects/c++/eh/dtor-1.xhtml)

## Move semantics

:movie_camera: *Videos*

* N.Josuttis @ CppCon (2017) &ndash; *The nightmare of move semantics for trivial classes*\
[Watch at YouTube](https://www.youtube.com/watch?v=PNRju6_yn3o)

## Tricks

### Accessing private and protected members

:link: **Webpages**

* [Accessing private members &ndash; Stack Overflow](https://stackoverflow.com/questions/726096/accessing-private-members)
* [Access to private members. That's easy! &ndash; Johannes Schaub, litb's Blog](https://bloglitb.blogspot.com/2010/07/access-to-private-members-thats-easy.html)
