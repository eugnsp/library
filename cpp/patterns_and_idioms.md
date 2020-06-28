# Patterns, idioms, and design principles <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Design principles](#design-principles)
	- [Style and guidelines](#style-and-guidelines)
	- [Class design](#class-design)
		- [Liskov substitution principle](#liskov-substitution-principle)
	- [Interface design](#interface-design)
		- [Destructors](#destructors)
		- [Rule of zero/three/five](#rule-of-zerothreefive)
	- [Error handling](#error-handling)
		- [Exceptions](#exceptions)
- [Patterns and idioms](#patterns-and-idioms)
	- [Abstract factory](#abstract-factory)
	- [Adapter](#adapter)
	- [Barton–Nackman trick](#bartonnackman-trick)
	- [Bridge and pimpl](#bridge-and-pimpl)
	- [Builder](#builder)
	- [Chain-of-responsibility](#chain-of-responsibility)
	- [Copy-and-swap / Move-and-swap](#copy-and-swap--move-and-swap)
	- [Curiously recurring template](#curiously-recurring-template)
	- [Double-checked locking](#double-checked-locking)
	- [Execute-around](#execute-around)
		- [Execute-around object (RAII)](#execute-around-object-raii)
		- [Execute-around proxy](#execute-around-proxy)
		- [Execute-around pointer](#execute-around-pointer)
		- [Execute-around function](#execute-around-function)
	- [Flyweight](#flyweight)
	- [In-place factory, typed in-place factory](#in-place-factory-typed-in-place-factory)
	- [Infinite loop](#infinite-loop)
	- [Observer](#observer)
	- [Opaque typedef (whole value)](#opaque-typedef-whole-value)
	- [Passkey](#passkey)
	- [Singleton](#singleton)
	- [Strategy / Policy](#strategy--policy)
	- [Type erasure](#type-erasure)
	- [Visitor](#visitor)
- [Antipatterns](#antipatterns)

---

## Design principles

:link:

- [*The architecture of open source applications*](https://www.aosabook.org/en/index.html)

:grey_question:

- [*What is a magic number, and why is it bad?*](https://stackoverflow.com/q/47882) – Stack Overflow
- [*Are global variables bad?*](https://stackoverflow.com/q/484635) – Stack Overflow

:movie_camera:

- F.Pikus. [*Design for performance*](https://www.youtube.com/watch?v=m25p3EtBua4) – CppCon (2018)

### Style and guidelines

:link:

- [*Standard library guidelines*](https://github.com/cplusplus/LEWG/blob/master/library-design-guidelines.md)
- [*Google C++ style guide*](https://google.github.io/styleguide/cppguide.html)
- D.Kieras. [*C++ header file guidelines*](http://www.umich.edu/~eecs381/handouts/CppHeaderFileGuidelines.pdf)
- M.Wilson. [*QM bites: Order your includes (twice over)*](https://accu.org/index.php/journals/2249) – [Overload **133**](https://accu.org/index.php/journals/c362/) (2016)
- M.Wilson. [*QM bites: The two sides of boolean parameters*](https://accu.org/index.php/journals/2183) – [Overload **130**](https://accu.org/index.php/journals/c356/) (2015)
- S.Ignatchenko. [*Best practices vs witch hunts*](https://accu.org/index.php/journals/2066) – [Overload **125**](https://accu.org/index.php/journals/c346/) (2015)
- B.Schmidt. [*I like whitespace*](https://accu.org/index.php/journals/2063) – [Overload **125**](https://accu.org/index.php/journals/c346/) (2015)
- J.Wakely. [*Stop the constant shouting*](https://accu.org/index.php/journals/1923) – [Overload **121**](https://accu.org/index.php/journals/c338/) (2014)

:grey_question:

- [*Does `auto` make C++ code harder to understand?*](https://softwareengineering.stackexchange.com/q/180216) – Software Engineering

:movie_camera:

- B.Stroustrup. [*Writing good C++14*](https://www.youtube.com/watch?v=1OEu9C51K2A) – CppCon (2015)
- H.Sutter. [*Back to the basics! Essentials of modern C++ style*](https://www.youtube.com/watch?v=xnqTKD8uD64) – CppCon (2014)

:anchor:

- [*C++ core guidelines*](https://github.com/isocpp/CppCoreGuidelines)
- [*Linux kernel coding style*](https://www.kernel.org/doc/html/latest/process/coding-style.html)

### Class design

<!-- > SOLID are the five principles of class design:
>
> - single responsibility principle: a class should have one, and only one, reason to change;
> - open-closed principle: you should be able to extend a class behavior, without modifying it;
> - interface segregation principle: make fine grained interfaces that are client specific;
> - dependency inversion principle: depend on abstractions, not on concretions. -->

:link:

- [*SOLID*](https://en.wikipedia.org/wiki/SOLID) – Wikipedia
- R.C.Martin. [*Design principles and design patterns*](http://www.cvc.uab.es/shared/teach/a21291/temes/object_oriented_design/materials_adicionals/principles_and_patterns.pdf)
- R.C.Martin. SOLID: [*Single responsibility principle*](https://web.archive.org/web/20150202200348/http://www.objectmentor.com/resources/articles/srp.pdf), [*Open-closed principle*](https://web.archive.org/web/20150905081105/http://www.objectmentor.com/resources/articles/ocp.pdf), [*Interface segregation principle*](https://web.archive.org/web/20150905081110/http://www.objectmentor.com/resources/articles/isp.pdf), [*Dependency inversion principle*](https://web.archive.org/web/20150905081103/http://www.objectmentor.com/resources/articles/dip.pdf)
- C.Oldwood. [*KISSing SOLID goodbye*](https://accu.org/index.php/journals/1957) – [Overload **122*](https://accu.org/index.php/journals/c340/) (2014)
- R.C.Martin. [*The principles of OOD*](http://www.butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod) – Uncle Bob (2004)
- H.Sutter. [*What’s in a class? The interface principle*](http://www.gotw.ca/publications/mill02.htm) (1998)

:movie_camera:

- J.Kalb. [*Back to basics: Object-oriented programming*](https://www.youtube.com/watch?v=32tDTD9UJCE) – CppCon (2018)
- K.Henney. [*The SOLID design principles deconstructed*](https://www.youtube.com/watch?v=tMW08JkFrBA) – YOW! (2013)

:book:

- Sec.: *Class design and inheritance* – H.Sutter, A.Alexandrescu. [*C++ coding standards: 101 rules, guidelines, and best practices*](http://www.gotw.ca/publications/c++cs.htm) – [Addison-Wesley](https://www.pearson.com/us/higher-education/program/Sutter-C-Coding-Standards-101-Rules-Guidelines-and-Best-Practices/PGM147301.html) (2004)

#### Liskov substitution principle

> Liskov substitution principle states that, in a computer program, if `S` is a subtype of `T`, then objects of type `T` may be replaced with objects of type `S` (i.e. an object of type `T` may be substituted with any object of a subtype `S`) without altering any of the desirable properties of the program (correctness, task performed, etc.).

:link:

- [*Liskov substitution principle*](https://en.wikipedia.org/wiki/Liskov_substitution_principle) – Wikipedia
- R.C.Martin. [*Liskov substitution principle*](https://web.archive.org/web/20150905081111/http://www.objectmentor.com/resources/articles/lsp.pdf)

:grey_question:

- [*What is an example of the Liskov substitution principle?*](https://stackoverflow.com/q/56860) – Stack Overflow

### Interface design

:grey_question:

- [*Pass by value vs pass by rvalue reference*](https://stackoverflow.com/q/37935393) – Stack Overflow
- [*Is it better to pass by value or pass by constant reference?*](https://stackoverflow.com/q/270408) – Stack Overflow

:anchor:

- [F.16: *For “in” parameters, pass cheaply-copied types by value and others by reference to `const`*](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#Rf-in) – C++ core guidelines

#### Destructors

:link:

- A.Krzemie&nacute;ski. [*Destructors that throw*](https://akrzemi1.wordpress.com/2011/09/21/destructors-that-throw/) (2011)
- B.Kolpackov. [*Throwing destructors*](https://www.kolpackov.net/projects/c++/eh/dtor-1.xhtml) (2004)

:grey_question:

- [*Throwing exceptions out of a destructor*](https://stackoverflow.com/q/130117) – Stack Overflow

:movie_camera:

- P.Isensee. [*Destructor case studies: Best practices for safe and efficient teardown*](https://www.youtube.com/watch?v=XvWyLAW_U0Q) – CppCon (2019)

#### Rule of zero/three/five

> *The rule of zero*: if a class requires no user-defined constructors, no user-defined assignment operators and no user-defined destructor, avoid defining them. *The rule of three/five*: if a class requires a user-defined destructor, a user-defined copy (and move) constructor, or a user-defined copy (and move) assignment operator, it almost certainly requires all three (five).

:link:

- [*Rule of three*](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) – Wikipedia
- S.Meyers. [*A concern about the rule of zero*](https://scottmeyers.blogspot.com/2014/03/a-concern-about-rule-of-zero.html) (2014)
- J.Alday. [*Enforcing the rule of zero*](https://accu.org/index.php/journals/1896) – [Overload **120**](https://accu.org/index.php/journals/c336/) (2014)
- R.M.Fernandes. [*Rule of zero*](https://web.archive.org/web/20121127171954/http://rmartinho.github.com/cxx11/2012/08/15/rule-of-zero.html) (2012)

:anchor:

- [*The rule of three/five/zero*](https://en.cppreference.com/w/cpp/language/rule_of_three) – C++ reference
- W.E.Brown. [*Proposing the rule of five, v2*](http://open-std.org/JTC1/SC22/WG21/docs/papers/2014/n3839.pdf) – WG21/N3839 (2014)

### Error handling

:link:

- J.M&uuml;ller. [*Exceptions vs expected: Let’s find a compromise*](https://foonathan.net/2017/12/exceptions-vs-expected/) (2017)
- J.M&uuml;ller. [*How to handle errors in constructors without exceptions?*](https://foonathan.net/2017/01/exceptions-constructor/) (2017) <!-- which pattern is this? -->
- V.Romeo. [*Why choose sum types over exceptions?*](https://vittorioromeo.info/index/blog/adts_over_exceptions.html) (2017)

:movie_camera:

- A.Schödl. [*A practical approach to error handling](https://www.youtube.com/watch?v=CFwwBMcuG6U) – Meeting C++ (2014)

<!-- * A.Alexandrescu. [*Systematic error handling in C++*](https://www.youtube.com/watch?v=kaI4R0Ng4E8&t=570) – C++ and Beyond (2012) -->

:anchor:

- L.Crowl. [*Handling disappointment in C++*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0157r0.html) – WG21/P0157R0 (2015)

:anchor:

- [*Error handling*](https://en.cppreference.com/w/cpp/error) – C++ reference

#### Exceptions

> Levels of exception guarantee:
> - *nothrow exception guarantee*: the function never throws exceptions;
> - *strong exception guarantee*: if the function throws an exception, the state of the program is rolled back to the state just before the function call (commit-or-rollback semantics);
> - *basic exception guarantee*: if the function throws an exception, the program is in a valid state, no resources are leaked, and all objects’ invariants are intact;
> - *no exception guarantee*: if the function throws an exception, the program may not be in a valid state, resource leaks, memory corruption, or other invariant-destroying errors may have occurred.

For exceptions in destructors, see [*Destructors*](#destructors).

:link:

- R.McArdell. [*C++11 (and beyond) exception support*](https://accu.org/index.php/journals/2422) – [Overload **141**](https://accu.org/index.php/journals/c378/), 24 (2017)
- H.Sutter. [GotW #102: *Exception-safe function calls*](https://herbsutter.com/gotw/_102/) (2012)
- H.Sutter. [GotW #56: *Exception-safe function calls*](http://www.gotw.ca/gotw/056.htm)
- H.Sutter. [*When and how to use exceptions*](http://www.drdobbs.com/when-and-how-to-use-exceptions/184401836) – Dr.Dobb’s Journal (2004)
- H.Sutter. [*Exception-safe generic containers*](http://ptgmedia.pearsoncmg.com/imprint_downloads/informit/aw/meyerscddemo/DEMO/MAGAZINE/SU_FRAME.HTM) (1997)
- T.Cargill. [*Exception handling: A false sense of security*](http://ptgmedia.pearsoncmg.com/images/020163371x/supplements/Exception_Handling_Article.html) (1994)

:grey_question:

- B.Stroustrup. [*Why doesn’t C++ provide a `finally` construct?*](http://www.stroustrup.com/bs_faq2.html#finally) – C++ style and technique FAQ
- [*When should I really use `noexcept`?*](https://stackoverflow.com/q/10787766) – Stack Overflow
- [*Is there any difference between `noexcept` and empty throw specification for an lambda expression?*](https://stackoverflow.com/q/37433371) – Stack Overflow
- [*Why vector access operators are not specified as `noexcept`?*](https://stackoverflow.com/q/20517259) – Stack Overflow

:anchor:

- [*Exceptions*](https://en.cppreference.com/w/cpp/language/exceptions) – C++ reference
- [*`std::move_if_noexcept`*](https://en.cppreference.com/w/cpp/utility/move_if_noexcept) – C++ reference

---

## Patterns and idioms

> A design pattern is a general technique used to solve a class of related problems.

:link:

- [*Design patterns*](https://en.wikipedia.org/wiki/Design_Patterns) – Wikipedia
- S.Ignatchenko. [*“No Bugs” top five C++ cooking recipes*](https://accu.org/index.php/journals/1874) – [Overload **113**](https://accu.org/index.php/journals/c320/) (2013)

:movie_camera:

* F.Pikus. [*C++ design patterns: From C++03 to C++17*](https://www.youtube.com/watch?v=MdtYi0vvct0) – CppCon (2019)

### Abstract factory

> The abstract factory pattern provides a way to encapsulate a group of individual factories without specifying their concrete classes. The client software creates a concrete implementation of the abstract factory and then uses the generic interface of the factory to create the concrete objects.

:book:

- App. sec. *Abstract factory* – A.Holub. [*Holub on patterns: Learning design patterns by looking at code*](https://holub.com/patterns/book.pdf) (2004)

### Adapter

:link:

- [*Adapter pattern*](https://en.wikipedia.org/wiki/Adapter_pattern) – Wikipedia

:movie_camera:

- [*Adapter design pattern*](https://www.youtube.com/watch?v=9jIgSsIfh_8) – D.Banas

### Barton–Nackman trick

:link:

- [*Barton–Nackman trick*](https://en.wikipedia.org/wiki/Barton%E2%80%93Nackman_trick) – Wikipedia
- [*Barton–Nackman trick*](https://en.wikibooks.org/wiki/More_C%2B%2B_Idioms/Barton-Nackman_trick) – WikiBooks

:book:

- Sec. 21.2.1: *The Barton–Nackman trick* – D.Vandevoorde, N.M.Josuttis, D.Gregor. [*C++ templates: The complete guide*](http://www.tmplbook.com/) (2017)

### Bridge and pimpl

:link:

- [*Bridge pattern*](https://en.wikipedia.org/wiki/Bridge_pattern) – Wikipedia

:movie_camera:

- D.Schmidt. [*The composite and bridge patterns*](https://www.youtube.com/watch?v=iM4W5hFqaEA&t=730)
- D.Banas. [*Bridge design pattern*](https://www.youtube.com/watch?v=qG286LQM6BU)

### Builder

> The builder pattern separates the creation of an object from its representation. It is used to create complex objects that are built in multiple stages:
> ```cpp
> struct Builder {
>     Builder(...);
>     Builder& add(...) { ...; return *this; }
>     operator Product() const;
> };
>
> Product pr = Builder(...).add(...).add(...).add(...);

:link:

- [*Builder pattern*](https://en.wikipedia.org/wiki/Builder_pattern) – Wikipedia

### Chain-of-responsibility

> The chain-of-responsibility is a design pattern consisting of a source of command objects and a series of processing objects. Each processing object contains logic that defines the types of command objects that it can handle; the rest are passed to the next processing object in the chain.

:link:

- [*Chain-of-responsibility pattern*](https://en.wikipedia.org/wiki/Chain-of-responsibility_pattern) – Wikipedia

### Copy-and-swap / Move-and-swap

> The copy-and-swap idiom allows an assignment operator to be implemented elegantly with strong exception safety. However, it is often harmful to performance when a strong exception safety guarantee of the copy assignment operator is not needed.
> ```cpp
> class Object {
> public:
>     Object(const Object&);
>     Object(Object&&);
>
>     Object& operator=(const Object& obj) {
>         Object{obj}.swap(*this);
>         return *this;
>     }
>
>     Object& operator=(Object&& obj) {
>         Object{std::move(obj)}.swap(*this);
>         return *this;
>     }
> };
> ```

:grey_question:

- [*What is the copy-and-swap idiom?*](https://stackoverflow.com/q/3279543) – Stack Overflow
- [*Using `swap` to implement move assignment*](https://stackoverflow.com/q/32234623) – Stack Overflow

:book:

- Ch. 5: *A comprehensive look at RAII* – F.G.Pikus. [*Hands-on design patterns with C++*](https://www.packtpub.com/application-development/hands-design-patterns-c) (2019)

### Curiously recurring template

> The curiously recurring template pattern (CRTP) is an idiom in which a class `X` derives from a class template using `X` itself as template parameter:
> ```cpp
> template<class Derived>
> class Base {
>   private:
>     friend Derived;
>     Base();
>   public:
>     void foo() { static_cast<Derived*>(this)->foo(); }
> };
>
> class X : public Base<X> {
>   public:
>     void foo();
> }
> ```

:link:

- [*Curiously recurring template pattern*](https://en.wikipedia.org/wiki/Curiously_recurring_template_pattern) – Wikipedia
- A.Nasonov. [*Better encapsulation for the curiously recurring template pattern*](https://accu.org/index.php/journals/296) – [Overload **70**](https://accu.org/index.php/journals/c142/) (2005)
- J.Coplien. [*Curiously recurring template patterns*](https://sites.google.com/a/gertrudandcope.com/info/Publications/InheritedTemplate.pdf) – C++ Report (1995)

:grey_question:

- [*What is the curiously recurring template pattern?*](https://stackoverflow.com/q/4173254) – Stack Overflow
- [*CRTP with protected derived member*](https://stackoverflow.com/q/8523762) – Stack Overflow

:book:

- Ch. 8: *The curiously recurring template pattern* – F.G.Pikus. [*Hands-on design patterns with C++*](https://www.packtpub.com/application-development/hands-design-patterns-c) (2019)

### Double-checked locking

See also [*Multithreading* – Concurrency and parallelism](concurrency_and_parallelism.md#multithreading).

:link:

- [*Double-checked locking*](https://en.wikipedia.org/wiki/Double-checked_locking) – Wikipedia

:movie_camera:

- F.Pikus. [*Live lock-free or deadlock (practical lock-free programming). Part I*](https://www.youtube.com/watch?v=lVBvHbJsg5Y) – CppCon (2015)

### Execute-around

:link:

- K.Henney. [*C++ patterns: Executing around sequences*](https://hillside.net/europlop/HillsideEurope/Papers/EuroPLoP2000/2000_Henney_ExecutingAroundSequences.pdf) – EuroPLoP (2000)

#### Execute-around object (RAII)

> Execute-around object idiom abstracts the execution of a pair of actions that surround a sequence of statements, or a single action that follows a sequence. This idiom is also known by the name of scope guard and resource acquisition is initialization (RAII). An example of this idiom is provided by standard library [smart pointers](std_library.md#smart-pointers), e.g. by `std::unique_ptr`.

:link:

- [*Resource acquisition is initialization*](https://en.wikipedia.org/wiki/Resource_acquisition_is_initialization) – Wikipedia
- P.Grenyer. [*RAII is not garbage*](https://accu.org/index.php/journals/1945) – [Overload **106**](https://accu.org/index.php/journals/c303/) (2011)

:grey_question:

- [*What is meant by Resource acquisition is initialization (RAII)?*](https://stackoverflow.com/q/2321511) – Stack Overflow

:book:

- Ch. 5: *A comprehensive look at RAII* – F.G.Pikus. [*Hands-on design patterns with C++*](https://www.packtpub.com/application-development/hands-design-patterns-c) (2019)

:anchor:

- [*RAII*](https://en.cppreference.com/w/cpp/language/raii) – C++ reference

<!--Scoped Resource - Generic RAII Wrapper for theStandard Library  https://isocpp.org/files/papers/N3949.pdf -->
<!-- https://www.codeproject.com/Articles/10141/RAII-Dynamic-Objects-and-Factories-in-C -->

#### Execute-around proxy

> Execute-around proxy idiom applies execute-around object idiom for individual calls on an object.

#### Execute-around pointer

> Execute-around pointer idiom defines an execute-around proxy idiom when the actions performed on a target object are the same for all functions.

:memo:

- This idiom can be used to “convert” a non-thread-safe class into a thread-safe one by automatically locking and unlocking a mutex when member functions are called.

:link:

- [*Execute-around pointer*](https://en.wikibooks.org/wiki/More_C%2B%2B_Idioms/Execute-Around_Pointer) – WikiBooks
- [*We make any object thread-safe*](https://www.codeproject.com/Articles/1183379/We-make-any-object-thread-safe) – CodeProject (2018)

#### Execute-around function

> Execute-around function idiom safely groups and executes a sequence of statements that must be enclosed by a pair of actions, or followed by a single action.

### Flyweight

:link:

- [*Boost.Flyweight: Small-sized handle classes granting constant access to shared common data*](https://www.boost.org/doc/libs/release/libs/flyweight/doc/index.html)

### In-place factory, typed in-place factory

:link:

- [*Boost.Optional: In-place factories*](https://www.boost.org/doc/libs/1_72_0/libs/optional/doc/html/boost_optional/tutorial/in_place_factories.html)

### Infinite loop

> ```cpp
> for (;;) { ... }
> while (true) { ... }
> do { ... } while (true);
> ```

:link:

- M.Wilson. [*QM bites: Looping for-ever*](https://accu.org/index.php/journals/2227) – [Overload **132**](https://accu.org/index.php/journals/c360/) (2016)
- [*Endless loop in C/C++*](https://stackoverflow.com/q/20186809) – Stack Overflow

### Observer

:link:

- M.Wilson. [*QM bites: Looping for-ever*](https://accu.org/index.php/journals/2227) – [Overload **132**](https://accu.org/index.php/journals/c360/) (2016)

### Opaque typedef (whole value)

> An opaque type is a new type that is distinct from and distinguishable from its underlying type, yet retaining layout compatibility with its underlying type. The intent is to allow programmer control (1) over substitutability between an opaque alias and its underlying type, and (2) over overloading based on any parameter whose type is or involves an opaque alias.
> ```cpp
> template<class T> class Whole_value {
> public:
>     Whole_value(T v) : v_(v) {}
>     operator T() const { return v_; }
> private:
>     T v_;
> };
> ```

:memo:

- > Nobody seemed to know, so I wrote a mail to the author, Walter E. Brown, and asked him. He told me that Bjarne doesn’t like that feature (anymore), so it is very unlikely that it will come anytime soon. Apparently C++ won’t get strong typedefs as core language feature. [[J.M&uuml;ller]](https://foonathan.net/blog/2016/10/19/strong-typedefs.html)

:link:

- L.B&ouml;ger. [*Empty scoped enums as strong aliases for integral types*](https://accu.org/index.php/journals/2683) – [Overload **152**](https://accu.org/index.php/journals/c401/) (2019)
- J.M&uuml;ller. [*Tutorial: Emulating strong/opaque typedefs in C++*](https://foonathan.net/2016/10/strong-typedefs/) (2016)

:movie_camera:

- H.Matthews. [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScst=975) – ACCU (2017)

:anchor:

- W.E.Brown. [*Toward opaque typedefs for C++1Y, v2*](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3741.pdf) – WG21/N3741 (2013)
- [*`BOOST_STRONG_TYPEDEF`*](https://www.boost.org/doc/libs/1_71_0/libs/serialization/doc/strong_typedef.html) – Boost.Serialization

### Passkey

:grey_question:

<!-- https://stackoverflow.com/questions/3217390/clean-c-granular-friend-equivalent-answer-attorney-client-idiom/3218920#3218920-->

<!-- https://stackoverflow.com/questions/3324248/how-to-name-this-key-oriented-access-protection-pattern -->

- [*Is this key-oriented access-protection pattern a known idiom?*](https://stackoverflow.com/q/3220009) – Stack Overflow

### Singleton

> The singleton pattern ensures that a class has one instance and provides a global point of access to that instance. It is useful when exactly one object is needed to coordinate actions across the system.
> ```cpp
> class Singleton {
> public:
>     static Singleton& instance() {
>         static Singleton inst;
>         return inst;
>     }
>
> private:  // protected:
>     Singleton();
>     Singleton(const Singleton&) = delete;
>     Singleton& operator=(const Singleton&) = delete;
>     ~Singleton() = default;
> };

:link:

- [*Singleton*](https://en.wikipedia.org/wiki/Singleton_pattern) – Wikipedia
- F.Glassborow. *Exploring patterns: Part 1* – [Overload **26**](https://accu.org/index.php/journals/c288/) (1998)
- R.Nystrom. [*Singleton*](https://gameprogrammingpatterns.com/singleton.html) – Game programming patterns
<!-- https://wiki.c2.com/?SingletonPattern -->

:grey_question:

- [*Is Meyers’ implementation of the Singleton pattern thread safe?*](https://stackoverflow.com/q/1661529) – Stack Overflow

:book:

- Ch. 15: *Singleton – A classic OOP pattern* – F.G.Pikus. [*Hands-on design patterns with C++*](https://www.packtpub.com/application-development/hands-design-patterns-c) (2019)
- Ch. 6: *Implementing singletons*  – A.Alexandrescu. [*Modern C++ design: Generic programming and design patterns applied*](http://erdani.com/index.php/books/modern-c-design/) (2001)
- Item 26: *Limiting the number of objects of a class* – S.Meyers. [*More effective C++: 35 new ways to improve your programs and designs*](https://www.informit.com/store/more-effective-c-plus-plus-35-new-ways-to-improve-your-9780201633719) (1996)

### Strategy / Policy

> The strategy pattern enables run- or compile-time selection of an algorithm for a particular behaviour. This pattern is also known by the name of policy pattern.

:movie_camera:

- H.Matthews. [*The C++ type system is your friend*](https://www.youtube.com/watch?v=MCiVdu7gScs&t=2387) – ACCU (2017)

:book:

- Ch. 16: *Policy-based design* – F.G.Pikus. [*Hands-on design patterns with C++*](https://www.packtpub.com/application-development/hands-design-patterns-c) (2019)
- Ch. 1: *Policy-based class design* – A.Alexandrescu. [*Modern C++ design: Generic programming and design patterns applied*](http://erdani.com/index.php/books/modern-c-design/) – [Addison-Wesley](https://www.informit.com/store/modern-c-plus-plus-design-generic-programming-and-design-9780201704310) (2001)

### Type erasure



### Visitor

> The visitor pattern separates an algorithm from an object structure, which is the data for this algorithm. It lets one define a new operation without changing the classes of the elements on which it operates.
> ```cpp
> class Visitor {
> public:
>     void visit(A&);
>     void visit(B&);
> };
>
> class A {
> public:
>     void accept(Visitor& v) { v.visit(*this); }
> };
>
> class B {
> public:
>     void accept(Visitor& v) { v.visit(*this); }
> };
> ```

:link:

- [*Visitor pattern*](https://en.wikipedia.org/wiki/Visitor_pattern) – Wikipedia
- F.Glassborow. [*Exploring patterns: Part 2*](https://accu.org/index.php/journals/593) – [Overload **27**](https://accu.org/index.php/journals/c176/) (1998)

:grey_question:

- [*When should I use the Visitor design pattern?*](https://stackoverflow.com/q/255214) – Stack Overflow

:movie_camera:

- B.Kannan. [*Generalised double dispatch*](https://www.youtube.com/watch?v=nNqiBasCab4) – CppCon (2019)

<!-- https://stackoverflow.com/questions/44447292/when-should-i-return-by-value-as-opposed-to-returning-a-unique-pointer -->
<!-- https://stackoverflow.com/questions/1691007/whats-the-right-way-to-overload-operator-for-a-class-hierarchy -->

---

## Antipatterns

:link:

- J.Wakely. [*C++ antipatterns*](https://accu.org/index.php/journals/2271) – [Overload **134**](https://accu.org/index.php/journals/c364/) (2016)

:movie_camera:

- L.Brandy. [*Curiously recurring C++ bugs at Facebook*](https://www.youtube.com/watch?v=lkgszkPnV8g) – CppCon (2017)
- B.Kernighan. [*Elements of programming style*](https://www.youtube.com/watch?v=8SUkrR7ZfTA) – Princeton University (2009)

