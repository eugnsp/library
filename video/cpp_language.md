# Core language and standard library design and development
## A visions for C++20 and `std2`

*Alisdair Meredith* @ C++Now (2017)

> C++17 is about to ship, and one of the subtle additions is the reservation of a family of namespaces for a future standard library. As our attention turns to C++20 and beyond, Alisdair Meredith will explore how language evolution could (and should) affect the design of this future library, and just what kind of a new library do we want anyway? This presentation breaks down into three parts. <b>I.</b> The first session lays down a vision of delivering all the language features likely to impact a library design in C++20. The obvious candidates are modules, concepts, and contracts, but what else? We will look at a variety of language features, assessing what they offer, or how they impact, a library designer. <b>II.</b> The second session looks into constraints and opportunities when designing a new C++ standard library. How compatible must we be with the old library? How ambitious should the new design be? What should our basic vocabulary types be? And how do we cope with language dependencies on `std` types like `type_info`? <b>III.</b> The final session is a planned workshop, to gain feedback from the attendees of C++Now &mdash; an invaluable resource of world class library designers. Have I highlighted the correct questions? What should the priorities be? What is an appropriate schedule for developing and standardizing such a new library? How can those of us without access to committee meetings still help with the process? The results of this workshop will be written up in an informational paper for the next ISO mailing.

Watch at YouTube: [Part I](https://www.youtube.com/watch?v=hizGxfDdc7M) [Part II](https://www.youtube.com/watch?v=fjtwfauk7a8) [Part III](https://www.youtube.com/watch?v=iAAAYNKU5g0) 

[See more details](https://cppnow2017.sched.com/event/A8Ia/a-vision-for-c20-and-std2-part-1-of-3)

## Meta: Thoughts on generative C++

*Herb Sutter* @ CppCon (2017)

> Two years ago, I started to focus on exploring ways that we might evolve the C++ language itself to make C++ programming both more powerful and simpler. The only way to accomplish both of those goals at the same time is by adding abstractions that let programmers directly express their intent &mdash; to elevate comments and documentation to testable code, and elevate coding patterns and idioms into compiler-checkable declarations. The work came up with several potential candidate features where judiciously adding some power to the language could simplify code dramatically, while staying true to C++'s core values of efficient abstraction, closeness to hardware, and the zero-overhead principle. The first two potential candidate features from that work to be further developed and proposed for ISO C++ are the `<=>` unified comparison operator (minor) and what I've provisionally called "metaclasses" as a way to generatively write C++ types (major). This talk is about the latter, and includes design motivation, current progress, and some live online compiler demos using the prototype Clang-based compiler built by Andrew Sutton and hosted at [godbolt.org](https://godbolt.org).

[Watch at YouTube](https://www.youtube.com/watch?v=4AfRAVcThyA)

[See more details](https://cppcon2017.sched.com/event/BguH/meta-thoughts-on-generative-c)

