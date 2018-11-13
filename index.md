# Algorithms
## Dynamic programming
### Introduction to algorithms: dynamic programming

*Erik Demaine* @ MIT OCW 6.006 (2011)

> <small><b>I.</b> This lecture introduces dynamic programming, in which careful exhaustive search can be used to design polynomial-time algorithms. The Fibonacci and shortest paths problems are used to introduce guessing, memoization, and reusing solutions to subproblems. <b>II.</b> This lecture starts with a five-step process for dynamic programming, and then covers text justification and perfect-information blackjack. The lecture also describes how parent pointers are used to recover the solution. <b>III.</b> This lecture starts with how to define useful subproblems for strings or sequences, and then looks at parenthesization, edit distance, and the knapsack problem. The lecture ends with a brief discussion of pseudopolynomial time. <b>IV.</b> This lecture introduces a second type of guessing, in which more subproblems are created so that more features of the solution can be found. This type of guessing is illustrated with piano/guitar fingering and the Tetris and Super Mario Brothers games.</small>

Watch at YouTube: [Part I](https://www.youtube.com/watch?v=OQ5jsbhAv_M) [Part II](https://www.youtube.com/watch?v=ENyox7kNKeY) [Part III](https://www.youtube.com/watch?v=ocZMDMZwhCY) [Part IV](https://www.youtube.com/watch?v=tp4_UXaVyx8) 

[See more details](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-006-introduction-to-algorithms-fall-2011/index.htm)

## Sorting algorithms
### Engineering a sort function

*Jon L. Bentley, M. Douglas McIlroy* @ Software: Practice and Experience <u>23</u>, 1249 (1993)

> We recount the history of a new `qsort` function for a C library. Our function is clearer, faster and more robust than existing sorts. It chooses partitioning elements by a new sampling scheme; it partitions by a novel solution to Dijkstra's Dutch National Flag problem; and it swaps efficiently. Its behavior was assessed with timing and debugging testbeds, and with a program to certify performance. The design techniques apply in domains beyond sorting.

DOI: [10.1002/spe.4380231105](https://doi.org/10.1002/spe.4380231105)

[Read](https://cs.fit.edu/~pkc/classes/writing/samples/bentley93engineering.pdf)

## Standard library algorithms
### STL algorithms: how to use them and how to write your own

*Marshall Clow* @ ACCU (2016)

> The STL contains a collection of containers, which everyone knows about, and a collection of algorithms, which are less well known. In this session, I will talk about the algorithms that are in the STL, how they are designed, and talk about writing your own algorithms that work in the same style as existing ones.

[Watch at YouTube](https://www.youtube.com/watch?v=3nXLxMYXgWs)

[See more details](https://accu.org/index.php/conferences/accu_conference_2016/accu2016_sessions#STL_Algorithms_%E2%80%93_How_to_Use_Them_and_How_to_Write_Your_Own)

## String algorithms
### Fast conversion from UTF-8 with C++, DFAs, and SSE intrinsics

*Bob Steagall* @ C++Now (2018)

> UTF-8 is taking on an increasingly important role in text processing. Many applications require the conversion of UTF-8 to UTF-16 or UTF-32, but typical conversion algorithms are sub-optimal. This talk will describe a fast, correct, DFA-based approach to UTF-8 conversion that requires only three simple lookup tables and a small amount of straightforward C++ code. We'll begin with a quick review UTF-8 and its relation to UTF-16 and UTF-32, as well as the concept of code units and code points. Next, we'll look at the layout of bits within a UTF-8 byte sequence, and from that, show a simple algorithm for converting from UTF-8 to UTF-32. Along the way will be a definition of overlong and invalid byte sequences. Following that will be a discussion of how to construct a DFA to perform the same operations as the simple algorithm. We'll then look at code for the DFA traversal underlying the basic conversion algorithm, and how to gain an additional performance boost by using SSE intrinsics. Finally, we'll compare the performance of this approach to several commonly-available implementations on Windows and Linux, and show how it's possible to do significantly faster conversions. 

[Watch at YouTube](https://www.youtube.com/watch?v=h5oczBeib_M)

[See more details](https://cppnow2018.sched.com/event/EC6x/fast-conversion-from-utf-8-with-c-dfas-and-sse-intrinsics)

### Regular expressions in C++, present and future

*Tim Shen* @ CppCon (2016)

> Regular expressions are widely used in application development and data processing, yet it is challenging to design and implement a regular expression library that is expressive, efficient and safe. In this talk, Tim Shen, the current maintainer of libstdc++'s `<regex>`, will introduce the basics of implementing regular expressions in C++, the status of existing implementations, and what is expected from the standardization process. For the implementation, several data structures and algorithms will be introduced, with pros and cons listed; we will show how several popular implementations (Boost.Regex, Boost.Xpressive, `<regex>` from standard library implementations, RE2, etc) pick their algorithms. Several popular features/patterns that hurt performance will be explained, with a "safe" regex usage suggested. Finally a wishlist of features will be presented, in order to deliver a more efficient and usable regex library. 

[Watch at YouTube](https://www.youtube.com/watch?v=N_rkHzhXueo)

[See more details](https://cppcon2016.sched.com/event/7nDI/regular-expressions-in-c-present-and-future)

# C++ language
## Core language and standard library design and development
### A visions for C++20 and `std2`

*Alisdair Meredith* @ C++Now (2017)

> C++17 is about to ship, and one of the subtle additions is the reservation of a family of namespaces for a future standard library. As our attention turns to C++20 and beyond, Alisdair Meredith will explore how language evolution could (and should) affect the design of this future library, and just what kind of a new library do we want anyway? This presentation breaks down into three parts. <b>I.</b> The first session lays down a vision of delivering all the language features likely to impact a library design in C++20. The obvious candidates are modules, concepts, and contracts, but what else? We will look at a variety of language features, assessing what they offer, or how they impact, a library designer. <b>II.</b> The second session looks into constraints and opportunities when designing a new C++ standard library. How compatible must we be with the old library? How ambitious should the new design be? What should our basic vocabulary types be? And how do we cope with language dependencies on `std` types like `type_info`? <b>III.</b> The final session is a planned workshop, to gain feedback from the attendees of C++Now &mdash; an invaluable resource of world class library designers. Have I highlighted the correct questions? What should the priorities be? What is an appropriate schedule for developing and standardizing such a new library? How can those of us without access to committee meetings still help with the process? The results of this workshop will be written up in an informational paper for the next ISO mailing.

Watch at YouTube: [Part I](https://www.youtube.com/watch?v=hizGxfDdc7M) [Part II](https://www.youtube.com/watch?v=fjtwfauk7a8) [Part III](https://www.youtube.com/watch?v=iAAAYNKU5g0) 

[See more details](https://cppnow2017.sched.com/event/A8Ia/a-vision-for-c20-and-std2-part-1-of-3)

### Meta: Thoughts on generative C++

*Herb Sutter* @ CppCon (2017)

> Two years ago, I started to focus on exploring ways that we might evolve the C++ language itself to make C++ programming both more powerful and simpler. The only way to accomplish both of those goals at the same time is by adding abstractions that let programmers directly express their intent &mdash; to elevate comments and documentation to testable code, and elevate coding patterns and idioms into compiler-checkable declarations. The work came up with several potential candidate features where judiciously adding some power to the language could simplify code dramatically, while staying true to C++'s core values of efficient abstraction, closeness to hardware, and the zero-overhead principle. The first two potential candidate features from that work to be further developed and proposed for ISO C++ are the `<=>` unified comparison operator (minor) and what I've provisionally called "metaclasses" as a way to generatively write C++ types (major). This talk is about the latter, and includes design motivation, current progress, and some live online compiler demos using the prototype Clang-based compiler built by Andrew Sutton and hosted at [godbolt.org](https://godbolt.org).

[Watch at YouTube](https://www.youtube.com/watch?v=4AfRAVcThyA)

[See more details](https://cppcon2017.sched.com/event/BguH/meta-thoughts-on-generative-c)

# Compilers
## Compiler optimization
### What else has my compiler done for me lately?

*Matt Godbolt* @ C++Now (2018)

> We've given Matt four day's notice to tell us what his compiler has done for him since his [CppCon 2017 Keynote](https://cppcon2017.sched.com/event/BguG/unbolting-the-compilers-lid-what-has-my-compiler-done-for-me-lately).

[Watch at YouTube](https://www.youtube.com/watch?v=nAbCKa0FzjQ)

[See more details](https://cppnow2018.sched.com/event/EilZ/what-else-has-my-compiler-done-for-me-lately)

### What has my compiler done for me lately? Unbolting the compiler's lid

*Matt Godbolt* @ CppCon (2017)

> In 2012, Matt and a colleague were arguing whether it was efficient to use the then-new-fangled range for. During the discussion a bash script was written to quickly compile C++ source and dump the assembly. Five years later and that script has grown into a website relied on by many to quickly see the code their compiler emits, to compare different compilers' code generation and behaviour, to quickly prototype and share code, and investigate the effect of optimization flags. In this talk Matt will not only show you how easy (and fun!) it is to understand the assembly code generated by your compiler, but also how important it can be. He'll explain how he uses Compiler Explorer in his day job programming low-latency trading systems, and show some real-world examples. He'll demystify assembly code and give you the tools to understand and appreciate how hard your compiler works for you. He'll also talk a little about how Compiler Explorer works behind the scenes, how it is maintained and deployed, and  share some stories about how it has changed over the years. By the end of this session you'll be itching to take your favourite code snippets and start exploring what your compiler does with them.

[Watch at YouTube](https://www.youtube.com/watch?v=bSkpMdDe4g4)

[See more details](https://cppcon2017.sched.com/event/BguG/unbolting-the-compilers-lid-what-has-my-compiler-done-for-me-lately)

### C++ costless abstractions: the compiler view

*Serge Guelton* @ CppCon (2016)

> One of the motto of C++ is "costless abstractions", a.k.a. you only pay for what you use. To achieve this goal, modern C++ puts a heavy burden on the compiler. But what does the compiler really does when it meets an exception? When it finds a nested lambda? When it encounters a structure that wraps a single scalar? During this talk, we'll go trough a set of innocent C++ sample that involves several data types and algorithms from the standard library, and verify that the costless abstraction principle holds, especially when looking at the difference between several optimization level, eventually digging into specific compiler optimization to understand what happens under the hood. This talk uses Clang++ as the reference compiler, and relies on its LLVM bitcode output to explain how the abstractions are lowered (or completely pruned) at the Intermediate Representation level.

[Watch at YouTube](https://www.youtube.com/watch?v=q0N9Tvf7Bz0)

[See more details](https://cppcon2016.sched.com/event/7nLK/c-costless-abstractions-the-compiler-view)

### Understanding compiler optimization

*Chandler Carruth* @ code::dive (2016)

> C++ is used in applications where resources are constrained and performance is critical. However, its power in this domain comes from the ability to build large, complex systems in C++. These systems leverage numerous C++ features in order to build and utilize abstractions that make reasoning about these complex systems possible. Abstractions are the very essence of how we scale software to solve ever larger and more complex problems.

[Watch at YouTube](https://www.youtube.com/watch?v=haQ2cijhvhE)

[See more details](http://codedive.pl/index/speaker/name/chandler-carruth/year/2016/)

# Data types and data structures
## Type deduction and why you care

*Scott Meyers* @ CppCon (2014)

> C++11 extends type deduction to include universal references, applies it to `auto` variables and lambda expressions, then throws in a special auto-only deduction rule. C++14 pushes the boundary further, adding two forms of function return type deduction (`auto` and `decltype(auto)`) for arbitrary functions and offering `auto` parameters for lambdas. The result is that what could be treated as a black box in C++98 has become a topic that practicing C++ developers really need to understand.

[Watch at YouTube](https://www.youtube.com/watch?v=wQxj20X-tIU)

[See more details](https://cppcon2014.sched.com/event/1qDJkx1/type-deduction-and-why-you-care)

## Floating point types
### Beyond floating point: next generation computer arithmetic

*John L. Gustafson* @ Stanford Computer Systems Colloquium (2017)

> A new data type called a "posit" is designed for direct drop-in replacement for IEEE Standard 754 floats. Unlike unum arithmetic, posits do not require interval-type mathematics or variable size operands, and they round if an answer is inexact, much the way floats do. However, they provide compelling advantages over floats, including simpler hardware implementation that scales from as few as two-bit operands to thousands of bits. For any bit width, they have a larger dynamic range, higher accuracy, better closure under arithmetic operations, and simpler exception-handling. For example, posits never overflow to infinity or underflow to zero, and there is no "Not-a-Number" (NaN) value. Posits should take up less space to implement in silicon than an IEEE float of the same size. With fewer gate delays per operation as well as lower silicon footprint, the posit operations per second (POPS) supported by a chip can be significantly higher than the FLOPs using similar hardware resources. GPU accelerators, in particular, could do more arithmetic per watt and per dollar yet deliver superior answer quality. A series of comprehensive benchmarks compares how many decimals of accuracy can be produced for a set number of bits-per-value, using various number formats. Low-precision posits provide a better solution than "approximate computing" methods that try to tolerate decreases in answer quality. High-precision posits provide better answers (more correct decimals) than floats of the same size, suggesting that in some cases, a 32-bit posit may do a better job than a 64-bit float. In other words, posits beat floats at their own game. 

[Watch at YouTube](https://www.youtube.com/watch?v=aP0Y1uAA-2Y)

[See more details](http://web.stanford.edu/class/ee380/Abstracts/170201.html)

### Demystifying floating point numbers

*John Farrier* @ CppCon (2015)

> Every day we develop software that relies on math while we often overlook the importance of understanding the implications of using our IEEE floats. From the often cited "floating point error" to unstable algorithms, this talk will explain the importance of floats, understanding their storage, the impact of the IEEE floats on math, and designing algorithms better. Finally, the talk will conclude with a quick case study of storing time for games and simulations.

[Watch at YouTube](https://www.youtube.com/watch?v=k12BJGSc2Nc)

[See more details](https://cppcon2015.sched.com/event/3vn4/demystifying-floating-point-numbers)

# Design and style
## Structured programming with `go to` statements

*Donald E. Knuth* @ ACM Computing Surveys <u>6</u>, 261 (1974)

> A consideration of several different examples sheds new light on the problem of creating reliable,  well-structured programs that behave efficiently. This study focuses largely on two issues: (a) improved syntax for iterations and error exits, making it possible to write a larger class of programs clearly and efficiently without go to statements; (b) a methodology of program design, beginning with readable and correct, but possibly inefficient programs that are systematically transformed if necessary into efficient and correct, but possibly less readable code. The discussion brings out opposing points of view about whether or not `go to` statements should be abolished; some merit is found on both sides of this  question. Finally, an attempt is made to define the true nature of structured programming, and to recommend  fruitful directions for further study.

DOI: [10.1145/356635.356640](https://doi.org/10.1145/356635.356640)

Read: [Source 1](http://oberon2005.oberoncore.ru/classics/dk1974b.pdf
) [Source 2](http://web.archive.org/web/20130731202547/http://pplab.snu.ac.kr/courses/adv_pl05/papers/p261-knuth.pdf)

## Rethinking pointers

*Jonathan M&uuml;ller* @ C++Now (2018)

> "Do not use owning raw pointers, use a smart pointer instead." &mdash; And yet it is common to use them when writing a linked list, for example. "Use a reference when a pointer is non-null." &mdash; But the standard library interfaces themselves don't follow this advice all the time. We're at a point where a simple question "I need to point to some other object" requires a complicated lecture about raw vs. smart pointers, references and the danger of putting references inside angle brackets. Clearly we can do better. Let's take a step back, and look at the bigger picture: What are the common pointer-like types? Which properties do they have in common, which are unique? What are the possible situations that require pointer-like types? Which properties do those situations require? This talk will answer those questions and so provide the definitive guide to choosing the correct pointer types. We'll be discussing whether or not `optional<T&>` or `std::observer_ptr` are necessary, talk about the difference in applications for `T&`, `gsl::non_null<T>` and `std::reference_wrapper<T>`, and look how the type system can help us catch lifetime issues.

[Watch at YouTube](https://www.youtube.com/watch?v=kYiEvVEh6Tw)

[See more details](https://cppnow2018.sched.com/event/EC7S/rethinking-pointers)

## Using types effectively

*Ben Deane* @ CppCon (2016)

> C++ has a pretty good type system, and modern C++ gives us a greater ability than ever before to use that type system for good: to make APIs easier to use and harder to misuse, to make our datatypes more closely express our intent, and generally to make code safer, more obvious in function and perhaps even faster. This is an interactive session &mdash; incorporating games played between presenter and audience, even &mdash; taking a look at choices available to us as datatype and API designers, and examining how a little knowledge about the algebra of algebraic datatypes can help. We'll see why `std::optional` and (hopefully soon) `std::variant` will quickly become an essential part of everyone's toolbox, and also explore how types can be used to express not just the structure of data, but also the behaviour of objects and functions.


[Watch at YouTube](https://www.youtube.com/watch?v=ojZbFIQSdl8)

[See more details](https://cppcon2016.sched.com/event/7nDJ/using-types-effectively)

## Writing good C++14

*Bjarne Stroustrup* @ CppCon (2015)

> How do we use C++14 to make our code better, rather than just different? How do we do so on a grand scale, rather than just for exceptional programmers? We need guidelines to help us progress from older styles, such as "C with Classes", C, "pure OO", etc. We need articulated rules to save us from each having to discover them for ourselves. Ideally, they should be machine-checkable, yet adjustable to serve specific needs. In this talk, I describe a style of guidelines that can be deployed to help most C++ programmers. There could not be a single complete set of rules for everybody, but we are developing a set of rules for most C++ use. This core can be augmented with rules for specific application domains such as embedded systems and systems with stringent security requirements. The rules are prescriptive rather than merely sets of prohibitions, and about much more than code layout. I describe what the rules currently cover (e.g., interfaces, functions, resource management, and pointers). I describe tools and a few simple classes that can be used to support the guidelines. The core guidelines and a guideline support library reference implementation will be open source projects freely available on all major platforms (initially, GCC, Clang, and Microsoft). 

[Watch at YouTube](https://www.youtube.com/watch?v=1OEu9C51K2A)

[See more details](https://cppcon2015.sched.com/event/3vVp/keynote-writing-good-c14)

## Interface design
### Modern C++ API design: from rvalue-references to type design

*Titus Winters* @ C++Now (2018)

> The old rules for C++API design are due for an update &mdash; we made ad hoc changes to design principles in the standard library, but haven't really written down the new ideas. Parameter passing and API design for free functions/member functions is due for a general update, particularly as a result of rvalue-references and reference qualification. How do we express "maybe move" APIs? When do we want reference-qualified overload sets? What does an rvalue-reference qualified non-overloaded method mean? How do we express call once semantics? This talk will focus on modern C++ design from small (choice of passing by value or reference) to large (regular types, reference types, move-only types, etc). We will also introduce a taxonomy of type properties as a means to discuss known-good type design families. 

[Watch at YouTube](https://www.youtube.com/watch?v=2UmDvg5xv1U)

[See more details](https://cppnow2018.sched.com/event/593e9796afdddded34505f1bc066a14e)

### Free your functions!

*Klaus Iglberger* @ CppCon (2017)

> You are devoted to minimize coupling and duplication? You are taking care to maximize cohesion, flexibility, extensibility, encapsulation, testability, and even performance in order to achieve the high goals of (object-oriented) programming? Awesome! But wait: You still favor member functions? Seriously? You have been deceived! You have been praying at the altar of false promises! Shed the shackles of Java philosophy! Free your functions! In this talk I will demonstrate why in C++ free functions should generally be preferred to member functions, and why free functions &mdash; not member functions! &mdash; provide you with all the aforementioned advantages you expect from object-oriented programming. Note, though, that this talk might fundamentally change your perception of C++ and object-oriented programming in general! 

[Watch at YouTube](https://www.youtube.com/watch?v=WLDT1lDOsb4)

[See more details](https://cppcon2017.sched.com/event/BgsL/free-your-functions)

# Exceptions and error handling
## Standard library exceptions and error handling
### Your own error code

*Andrzej Krzemie&nacute;ski* @  (2017)

> I was recently implementing the "classification of error conditions" in my application offered by the functionality behind `std::error_code`. In this post I want to share some of my experience and insight. C++11 comes with a quite sophisticated mechanism for classifying error conditions. You may have encountered names like "error code", "error condition", "error category", but figuring out what good they are, and how to use them is difficult. The only valuable source of information on the subject in the Internet is a series of blog posts by <em>Christopher Kohlhoff</em>, the author of Boost.Asio library. And this was a really good start for me. But still, I believe it would be beneficial to have more than one source of information, and more than one way of explaining the subject. So here we go&hellip;

[Read](https://akrzemi1.wordpress.com/2017/07/12/your-own-error-code/)

### System error support in C++0x

*Christopher Kohlhoff* @  (2010)

> Among the many new library features in C++0x is a little header called `&lt;system_error&gt;`. It provides a selection of utilities for managing, well, system errors. The principal components defined in the header are: `class error_category`, `class error_code`, `class error_condition`, `class system_error`, `enum class errc`. I had a hand in the design of this facility, so in this series of posts I will try to capture the rationale, history, and intended uses of the various components.

Read: [Part I](http://blog.think-async.com/2010/04/system-error-support-in-c0x-part-1.html
)[Part II](http://blog.think-async.com/2010/04/system-error-support-in-c0x-part-2.html
)[Part III](http://blog.think-async.com/2010/04/system-error-support-in-c0x-part-3.html
)[Part IV](http://blog.think-async.com/2010/04/system-error-support-in-c0x-part-4.html
)[Part V](http://blog.think-async.com/2010/04/system-error-support-in-c0x-part-5.html)

# Numerical methods
## Iterative solvers and preconditioners
### Krylov subspace solvers and preconditioners

*Kees Vuik* @ CEMRACS Summer school (2016)

> In these lecture notes an introduction to Krylov subspace solvers and preconditioners is presented. After a discretization of partial differential equations large, sparse systems of linear
equations has to be solved. Fast solution of these systems is very urgent nowadays. The size
of the problems can be 10<sup>13</sup> unknowns and 10<sup>13</sup> equations. Iterative solution methods are the
methods of choice for these large linear systems. We start with a short introduction of Basic
Iterative Methods. Thereafter preconditioned Krylov subspace methods, which are state of
the art, are described. A distinction is made between various classes of matrices.

[Watch at YouTube](https://www.youtube.com/watch?v=TbYgBL2lSM0)

[See more details](http://ta.twi.tudelft.nl/users/vuik/cemracs/)

# Optimization
## Moving faster: everyday efficiency in modern C++

*Alan Talbot* @ C++Now (2018)

> There seems to be a widely held belief among programmers today that efficiency no longer matters in most situations because processors are so fast and numerous and memory is so large. But from a user's perspective computers are often slower today than they were 30 years ago despite the enormous increase in measured performance of the hardware. How can this be? If this is true, what are we doing wrong and what can we do about it? Is efficiency an everyday concern for working programmers, or is it only needed for special cases written by specialists? In this talk we will explore these questions and consider the proposition that, contrary to popular belief, performance almost always matters and pervasive attention to efficiency is essential to ensure good performance. We will examine the efficiency tools modern C++ has to offer and discuss techniques for writing efficient code in an elegant, expressive and natural way. Topics will include tuning vs. optimizing, value semantics vs. reference semantics, unions and variants, move semantics, forwarding, container choice, in-place construction, and container node handling.

[Watch at YouTube](https://www.youtube.com/watch?v=J9yVA341zrw)

[See more details](https://cppnow2018.sched.com/event/bcbd5aab935fbc1e8f457175d6910de2)

## The nightmare of move semantics for trivial classes

*Nicolai Josuttis* @ CppCon (2017)

> Assume, we implement a very simple class having just multiple string members. Even ordinary application programmer prefer to make it simple and fast. You think you know how to do it? Well beware! It can become a lot harder than you initially might assume. So, let's look at a trivial class with multiple string members and use live coding to see the effect using different implementation approaches (using constructors passing by value, by reference, by perfect forwarding, or doing more sophisticated tricks). Sooner than later we will fall into the deep darkness of universal/forwarding references, `std::enable_if`, type traits, and concepts.

[Watch at YouTube](https://www.youtube.com/watch?v=PNRju6_yn3o)


## When a microsecond is an eternity: High performance trading systems in C++

*Carl Cook* @ CppCon (2017)

> Automated trading involves submitting electronic orders rapidly when opportunities arise. But it's harder than it seems: either your system is the fastest and you make the trade, or you get nothing. This is a considerable challenge for any C++ developer &mdash; the critical path is only a fraction of the total codebase, it is invoked infrequently and unpredictably, yet must execute quickly and without delay. Unfortunately we can't rely on the help of compilers, operating systems and standard hardware, as they typically aim for maximum throughput and fairness across all processes. This talk describes how successful low latency trading systems can be developed in C++, demonstrating common coding techniques used to reduce execution times. While automated trading is used as the motivation for this talk, the topics discussed are equally valid to other domains such as game development and soft real-time processing. 

[Watch at YouTube](https://www.youtube.com/watch?v=NH1Tta7purM)

[See more details](https://cppcon2017.sched.com/event/BgsH/when-a-microsecond-is-an-eternity-high-performance-trading-systems-in-c)

## Optimization tips

*Andrei Alexandrescu* @ CppCon (2014)

> Reasonably-written C++ code will be naturally fast. This is to C++'s excellent low-penalty abstractions and a memory model close to the machine. However, a large category of applications have no boundaries on desired speed, meaning there's no point of diminishing returns in making code faster. Better speed means less power consumed for the same work, more workload with the same data center expense, better features for the end user, more features for machine learning, better analytics, and more. Optimizing has always been an art, and in particular optimizing C++ on contemporary hardware has become a task of formidable complexity. This is because modern hardware has a few peculiarities about it that are not sufficiently understood and explored. This talk discusses a few such effects, and guides the attendee on how to navigate design and implementation options in search for better performance.

[Watch at YouTube](https://www.youtube.com/watch?v=Qq_WaiwzOtI)

[See more details](https://channel9.msdn.com/Events/CPP/C-PP-Con-2014/Optimization-Tips-Mo-Hustle-Mo-Problems)

## Memory and cache
### The CPU cache: instruction re-ordering made obvious

*Charles Bay* @ BoostCon (2016)

> This is an introductory discussion of the CPU cache, its anatomy, and its ever-growing role in hardware and software design. Modern performant systems are implemented with explicit knowledge of the CPU cache's structure and behavior. Discussion is made of CPU registers, CPU cache levels, the cache line, the data bus, the CPU instruction pipeline, the compiler's duty, and the tremendous hijinks performed by execution units within the processor core at runtime which leads to instruction re-ordering.

[Watch at YouTube](https://www.youtube.com/watch?v=tNkVUIv2gEE)


# Parallel compuing
## GPU computing
### C++ on GPUs done right?

*Peter Steinbach* @ Meeting C++ (2015)

> *No description is available.*

[Watch at YouTube](https://www.youtube.com/watch?v=z43l_LaOqnM)

[See more details](https://github.com/psteinb/meetingcpp2015)

## Multi-core computing
### `atomic<>` Weapons

*Herb Sutter* @ C++ and Beyond (2012)

> *The facts.* The C++11 memory model and what it requires you to do to make sure your code is correct and stays correct. We'll include clear answers to several FAQs: "how do the compiler and hardware cooperate to remember how to respect these rules?", "what is a race condition?", and the ageless one-hand-clapping question "how is a race condition like a debugger?" *The tools.* The deep interrelationships and fundamental tradeoffs among mutexes, atomics, and fences/barriers. I'll try to convince you why standalone memory barriers are bad, and why barriers should always be associated with a specific load or store. *The unspeakables.* I'll grudgingly and reluctantly talk about the Thing I Said I'd Never Teach That Programmers Should Never Need To Now: relaxed atomics. Don't use them! If you can avoid it. But here's what you need to know, even though it would be nice if you didn't need to know it. *The rapidly-changing hardware reality.* How locks and atomics map to hardware instructions on ARM and x86/x64, and throw in POWER and Itanium for good measure &mdash; and I'll cover how and why the answers are actually different last year and this year, and how they will likely be different again a few years from now. We'll cover how the latest CPU and GPU hardware memory models are rapidly evolving, and how this directly affects C++ programmers.

Watch at YouTube: [Part I](https://www.youtube.com/watch?v=A8eCGOqgvH4) [Part II](https://www.youtube.com/watch?v=KeLBd2EJLOU) 

[See more details](https://channel9.msdn.com/Shows/Going+Deep/Cpp-and-Beyond-2012-Herb-Sutter-atomic-Weapons-1-of-2)

# Standard library
## Iterator haiku

*Casey Carter* @ CppCon (2016)

> How five iterator categories blossomed into seven, and Sentinels trimmed them back to five again. Recently proposed changes to the ranges TS distill its seven iterator categories back to five without sacrificing any expressive power. Removing operations that are extraneous in the Sentinel world eliminates a potential source of programming errors.

[Watch at YouTube](https://www.youtube.com/watch?v=rZs9ndzGB_8)

[See more details](https://cppcon2016.sched.com/event/7nLy/iterator-haiku)

## `<functional>`: What's new, and proper usage

*Stephan T. Lavavej* @ CppCon (2015)

> `<functional>` gained lots of machinery in C++11, with further changes in C++14 and C++17. This talk will cover what's new in 11/14/17, focusing on how to use it properly. For example, you've probably used `std::function`, but do you know the criteria for activating the Small Functor Optimization? (It's not just being small!) We'll also look at `std::bind()`, `std::mem_fn`, C++17's `std::invoke()`, and more.

[Watch at YouTube](https://www.youtube.com/watch?v=zt7ThwVfap0)

[See more details](https://cppcon2015.sched.com/event/3vd1/ltfunctionalgt-whats-new-and-proper-usage)

## `string_view`: when to use it and when not

*Marshall Clow* @ CppCon (2015)

> The library fundamentals TS contains a new class `std::string_view`, which appears to be unlike anything else in the standard library. In this talk, we will explore the uses of `std::string_view`, when it is appropriate to use it, and when it is not. Along the way, I will discuss other possible `_view` classes, with an eye to the upcoming "ranges" proposal before the standards committee.

[Watch at YouTube](https://www.youtube.com/watch?v=H9gAaNRoon4)

[See more details](https://cppcon2015.sched.com/event/3vch/stringview-when-to-use-it-and-when-not)

## Evolving `array_view` and `string_view` for safe C++ code

*Neil MacIntosh* @ CppCon (2015)

> The Library Fundamentals TS already contains a `std::string_view` type, and possibly soon an `array_view` type. These are important and should be used pervasively as function parameters, especially instead of (pointer, length) pairs which are generally unsafe. They offer additional benefits in the form of decoupling: allowing functions to be specified in terms of high-level views rather than references to specific, concrete string and container types which bind both caller and callee to a specific implementation detail. As a specific example, using string_view in function signatures allows them to be called with any of the endless proliferation of string types that exist in codebases today (`std::string`, `CStringT`, `char*`, `BSTR`, `HSTRING`, `MyString` etc). We can and should evolve these types further as a key part of achieving memory safety for C++ code. This example-driven talk shares our experience with preventing defects in large-scale commercial C++ codebases by applying modestly evolved versions of the proposed `array_view` and `std::string_view` types, plus a small number of related types such as `not_null`. Adopting these types enables simpler and safer code that eliminates important classes of defects by construction. The types are carefully designed to have usually exactly zero space and time overhead over the current unsafe idioms they replace, so as to leave no valid performance reason against adopting them. Using these types enables high-quality static analysis, and is allowing Microsoft to fully replace non-standard and non-portable annotation systems for type and memory safety in our own code bases. We believe this approach is generally applicable to code at all levels, from application code down to the most performance-sensitive systems code.

[Watch at YouTube](https://www.youtube.com/watch?v=C4Z3c4Sv52U)

[See more details](https://cppcon2015.sched.com/event/3vbQ/a-few-good-types-evolving-arrayview-and-stringview-for-safe-c-code)

## Allocators
### An allocator is a handle to a heap

*Arthur O'Dwyer* @ C++Now (2018)

> C++17 introduced the `std::pmr` framework. In this framework, a `std::pmr::polymorphic_allocator<T>` holds a pointer to a `std::pmr::memory_resource`. The memory resource is in charge of managing and organizing the heap itself, and the allocator object is just a thin "handle" pointing to the memory resource. This is not just a convenient implementation strategy for `std::pmr`! Rather, this elucidates the true meaning of the Allocator concept which has existed, unchanged, since C++98. An Allocator <b>is</b> a handle to a MemoryResource. Even `std::allocator` can &ndash; and should &ndash; be viewed as a handle to a global singleton "heap", and not as a MemoryResource in its own right. From this core insight we derive many corollaries, such as the need for allocator types to be lightweight and efficiently copyable, the fundamental impossibility of implementing an "in-place" `std::vector` via stupid allocator tricks, and the philosophical underpinnings of "rebinding." We'll show at least two non-standard examples of types modeling Allocator that act as different kinds of handles to heaps: a `shmem_allocator` that holds a `shmem_ptr` to a memory resource, and a `shutdown_safe_allocator` that holds a `weak_ptr` to a memory resource. We'll discuss what we can expect from a "moved-from" allocator object, relate the notion of "handle" to neighboring notions such as "fa&ccedil;ade" and "adaptor", and suggest similarities between "allocator/heap" and "executor/execution-context".

[Watch at YouTube](https://www.youtube.com/watch?v=0MdSJsCTRkY)

[See more details](https://cppnow2018.sched.com/event/767e288589eae513fb3afff01fbca567)

## Containers
### If I had my 'druthers: a proposal for improving the containers in C++2x

*Bob Steagall* @ C++Now (2018)

> This talk will first review weaknesses in the current container library and discuss corresponding opportunities for improvement. We'll then list some tentative requirements, distinguishing between the needs of ordinary users and power users. We'll cover the need for meaningful names, and emphasize the distinction between low-level concrete containers, such as linked lists, and high-level adaptor containers, such as stacks. We'll then present a proposed high-level design for the container library and an idiom for container implementation that fulfills those requirements. We'll also cover changes to allocators and memory management facilities needed to support the proposed design. Along the way we'll look at example code for implementation and usage, and discuss ways to improve the containers' public APIs.


[Watch at YouTube](https://www.youtube.com/watch?v=bAE0qteS4Rk)

[See more details](https://cppnow2018.sched.com/event/ec102c7cabeea1c91c5629bd6d926ca4)

## Iterators
## Utilities
### Initializer lists are broken, let's fix them

*Jason Turner* @ C++Now (2018)

> C++11's `std::initializer_list` objects are flawed in ways that prevent them from being used in some contexts and used efficiently in other contexts. They allow you to create dangling references that most compilers and static analysis tools are unable to track. Specific examples, benchmarks, and quotes from the standard will illustrate these problems and how they are mandated. Will it be possible to address these issues with library changes or do we need to make a change to the standard? We will attempt to come to a consensus as a group. 

[Watch at YouTube](https://www.youtube.com/watch?v=sSlmmZMFsXQ)

[See more details](https://cppnow2018.sched.com/event/4058f00b8431f1610d3246f62066ac51)

### `tuple<>`: What's new and how it works

*Stephan T. Lavavej* @ CppCon (2016)

> `std::tuple` has been gaining new abilities, like get-by-type in C++14 and conditionally-explicit constructors in C++17. This talk will begin by briefly summarizing what you can do with tuples in C++11 and C++14. Next, we'll explore what's new in C++17, and how it can improve your code. We'll also delve into how this magic is implemented, with new metaprogramming tools like `std::conjunction`. Finally, we'll look at active issues in tuple's design, and what the Library Working Group is doing about them.

[Watch at YouTube](https://www.youtube.com/watch?v=JhgWFYfdIho)

[See more details](https://cppcon2016.sched.com/event/7nLk/tupleltgt-whats-new-and-how-it-works)

# Template metaprogramming
## Make classes great again! (Using concepts for customization points)

*Vinnie Falco* @ CppCon (2017)

> Learn new ways to think about class design, that you can apply to your own projects! In this talk we'll start with a simple class that models an HTTP message. We'll go over the limitations of the simple declaration, then walk through a series of guided improvements. We will explore ways to think about class models, create a concept as a customization point, perform type checking, and document a concept. The example class we will explore is based on the message container found in the Boost.Beast library. You do not need to know anything (or care) about network protocols. This is about building better classes.

[Watch at YouTube](https://www.youtube.com/watch?v=WsUnnYEKPnI)

[See more details](https://cppcon2017.sched.com/event/BgsE/make-classes-great-again-using-concepts-for-customization-points)

## Modern template metaprogramming: a compendium

*Walter E. Brown* @ CppCon (2014)

> Template metaprogramming has become an important part of a C++ programmer's toolkit. This talk will demonstrate state-of-the-art metaprogramming techniques, applying each to obtain representative implementations of selected standard library facilities. Along the way, we will look at `std::void_t`, a recently-proposed, extremely simple new new `<type_traits>` candidate whose use has been described by one expert as "highly advanced (and elegant), and surprising even to experienced template metaprogrammers."

Watch at YouTube: [Part I](https://www.youtube.com/watch?v=Am2is2QCvxY) [Part II](https://www.youtube.com/watch?v=a0FliKwcwXE) 

[See more details](https://cppcon2014.sched.com/event/1iGEgWF/modern-template-metaprogramming-a-compendium-part-i)

## Type traits
### The best type traits that C++ doesn't have

*Arthur O'Dwyer* @ C++Now (2018)

> I'll present three candidates for the best type trait that doesn't (yet!) exist in C++. The first trait, `is_trivially_relocatable_v<T>`, tells whether objects of type `T` can be "atomically move-constructed-and-destroyed" by `std::memcpy`. The canonical use-cases for this operation are vector resizing and hash-table rehashing. We'll look at benchmarks for resizing `std::vector<std::unique_ptr<T>>` with and without this type trait, and consider the curious case of **swapping** two trivially relocatable objects. The second trait, `is_trivially_equality_comparable_v<T>`, tells whether objects of type `T` can be compared by `std::memcmp`. The canonical use-case for this operation is compare-exchange on `std::atomic<T>`, which is already implemented in terms of `std::memcmp` but has undefined behavior for types that are not trivially comparable. (WG21 has begun to tackle this problem via papers N4130 and P0528.) With the introduction of "operator spaceship" in C++2a, the compiler now has enough information to determine the trivial comparability of every user-defined type; this could be exposed as a built-in type trait. We'll look at benchmarks for `std::vector<std::unique_ptr<T>>::operator==` with and without this type trait, and give a nod to `is_trivially_less_than_comparable_v<T>`. The third trait is actually a traits class: `tombstone_traits<T>`. This part of the talk will build on Mark Zeren's C++Now 2017 session "Rethinking Strings". Most object types have invalid or "spare" representations, for example the all-bits-zero representation of a `std::reference_wrapper<U>` or the `0x02` representation of a `bool`. By opting into a specialization of `tombstone_traits<T>`, the programmer can make these "spare" representations available to tombstone-aware library classes such as `std::optional<T>` and `cuckoo_hash<T>`. We'll show how `tombstone_traits<bool>` exposes the spare representations, how `tombstone_traits<std::optional<T>>` propagates them appropriately, and how the tombstone representations can be used in practice by a Robin Hood hash table.

[Watch at YouTube](https://www.youtube.com/watch?v=MWBfmmg8-Yo)

[See more details](https://cppnow2018.sched.com/event/ae35e6b500090e00c295aeeef68762c0)

### Type traits: what are they and why should I use them?

*Marshall Clow* @ CppCon (2015)

> In this talk, I will answer the questions, "What are type traits?" and "Why are type traits useful?", along with some examples of why when when they should be used.

[Watch at YouTube](https://www.youtube.com/watch?v=VvbTP_k_Df4)

[See more details](https://cppcon2015.sched.com/event/3vci/type-traits-what-are-they-and-why-should-i-use-them)

